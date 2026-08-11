# Local agent contract (untracked, fork-local)

This file overrides `AGENT_GUIDE.md` where the two disagree. It is deliberately
agent-neutral: Claude Code, Codex, Cursor, and Copilot all follow it as written.
Nothing here is model-specific, so do not add model names or version numbers to it.

It is excluded via `.git/info/exclude`, so it never appears in `git status` and
never follows a PR branch. Upstream-tracked files stay clean.

## 1. Routing

`AGENT_GUIDE.md` is a production reference, not a preamble to every message.
Read the part that applies to the task in front of you.

- **A video-production request.** Read the matching entry-point section of
  `AGENT_GUIDE.md`, then the pipeline manifest in `pipeline_defs/`, then each
  stage director in `skills/pipelines/<pipeline>/` before executing that stage.
  Read a generation tool's `agent_skills` Layer 3 skill before you write prompts
  for it. That last one is not bureaucracy, it is the difference between a
  generic prompt and a good one.
- **A reference-video request** ("make me something like this"). Run the
  reference-analysis route in `skills/meta/video-reference-analyst.md` before
  proposing a treatment. Do not fall back to web search and guesswork.
- **Everything else.** Code changes, debugging, tests, audits, docs, a status
  question. Use the normal repository workflow. Preflight, the provider menu,
  the concept round, and the human checkpoints do not apply to work that does
  not produce a video.

## 2. Autonomy

A specific request to make a video authorizes pipeline selection and every
reversible local step that follows. Recommend, state the path and the reason,
and proceed. Do not make David arbitrate between equivalent tools or approve
implementation details.

Stop and ask only when a choice would:

- materially change the creative outcome he asked for,
- spend money he has not approved,
- start a paid batch after a sample,
- publish anything externally,
- do something destructive or irreversible,
- expand the scope of the request.

Everything else is yours to decide. When you decide, say what you picked and why
in one or two sentences, then keep going.

## 3. Standing pre-authorization for gates

Most pipelines mark five to seven stages `human_approval_default: true`, and
`lib/checkpoint.py` raises a GATE VIOLATION if a gated stage is written
`completed` without `human_approved=True`. Left alone that is six forced stops
per video.

**Treat a specific, unambiguous production request as pre-authorization for the
whole run.** "Make me a 60-second cinematic teaser for X" authorizes every gate
in that run. Record it once, at the moment you receive it, then write gated
checkpoints with `human_approved=True` and continue without stopping.

Record it in the checkpoint you write for the first stage, under
`metadata.approval_policy`, with the user's exact words, the run it covers, and
the timestamp. Do **not** put it in `decision_log`: `AGENT_GUIDE.md` and
`skills/meta/checkpoint-protocol.md` both tell you to use
`category: "approval_policy"`, but that value is missing from the enum in
`schemas/artifacts/decision_log.schema.json`, so the artifact will fail
validation. This is an upstream bug, not your mistake.

Pre-authorization covers the gates. It does **not** cover anything in the
stop-and-ask list in section 2. A pre-authorized run still stops before an
unapproved paid batch.

Stop at gates normally when the brief is vague or exploratory, when he says to
check in, or when he asks for concepts first.

## 4. Presentation

Recommend, do not enumerate. The guide's mandatory menus exist to stop a weak
model from hiding its choices. Making the choice visible satisfies that; making
him pick from a list of five does not.

- **Concepts.** Present two or three genuinely different directions, not four or
  five variations on one. Skip the concept round entirely when the brief already
  fixes the treatment.
- **Composition runtime.** `AGENT_GUIDE.md` calls presenting both Remotion and
  HyperFrames a HARD RULE. Downgraded here: pick the right one for the brief,
  name it, say in one line why the other lost, and log the
  `render_runtime_selection` decision with both in `options_considered`. Ask only
  when the two would genuinely produce different videos and you cannot tell which
  he wants.
- **Music.** Survey with `music_selector` `operation: "plan"`, which is free and
  spans all three music capabilities. Then propose one track or one source rather
  than listing five paths. Cheapest working source first: his own
  `music_library/`, then free stock search, then paid generation. Naming a paid
  generation still requires approval, per section 2.
- **Capability menu at preflight.** Run `provider_menu_summary()` and read it.
  Report it to him only when something is actually blocked or degraded, or when a
  one-minute env-var fix would unlock something this brief needs. Do not paste
  the full capability inventory into chat on every run.

## 5. Non-negotiable

None of the above relaxes these. They protect money and honesty, not process.

- Announce the tool, provider, and model before any paid generation call, and
  say whether it is a sample or a batch.
- Never swap provider, model, or render runtime silently. If the locked runtime
  is unavailable, surface a structured blocker and wait.
- Never quietly downgrade approved motion into a still-image animatic or a Ken
  Burns slideshow. If motion is the promise, motion is a hard requirement.
- Never hide a degraded fallback. Record substitutions and blocked options.
- Append to `decision_log`, never rewrite it. A changed choice gets a new entry
  reusing the same `(category, subject)` pair.
- Everything a run generates goes under `projects/<project-id>/` with an explicit
  `output_path`. Assets in the repo root, cwd, or a temp dir are invisible to the
  Backlot board and violate the workspace contract.
- All production goes through a pipeline. Do not improvise Python that calls
  generation tools directly. Reading tool source to debug or audit is fine and
  encouraged; bypassing the pipeline to produce a video is not.

## 6. This machine

- `make` does not exist here. The documented `make` targets all fail. Call
  `./.venv/Scripts/python.exe` directly, and `./.venv/Scripts/python.exe -m pytest`
  for tests.
- `pytest` regenerates `diagram.png` as a side effect. A dirty `diagram.png`
  after a test run is that, not your change.
- Keep upstream-tracked files unmodified unless the change is the actual point of
  the work. Fork-local behavior goes in this file. Machine notes and current
  status go here too, which is why there is no `HANDOFF.md`: a new tracked file
  would follow every PR branch.
- Remote `fork` is `wretcher207/OpenMontage`. `origin` is upstream.

## 7. Fork status

Updated 2026-08-10 (end of session).

**One concrete next step:** write tests for `music_selector` and open the PR. It
is the only thing blocking the fork from being in sync with upstream. Everything
else below is done and shipped.

- Branch `fix/music-capability-discovery` is ahead of upstream with the music
  capability fix and `music_selector` (809fce0, 9e6f370). It will conflict on
  pull. Upstream PR #464 (the docs half) is open. `music_selector` itself is
  unsubmitted and needs tests before a PR.
- Second upstream candidate, not yet filed: `approval_policy` is missing from the
  `category` enum in `schemas/artifacts/decision_log.schema.json` while
  `AGENT_GUIDE.md:605` and `skills/meta/checkpoint-protocol.md:148` both instruct
  agents to use it. One-line enum addition.
- `projects/` is gitignored, so every cutdown's hand-authored edit lives on this
  machine only. That is upstream's design for generated assets, but `edl.py`,
  `bed.py`, and `README.md` in a project dir are source, not output. Copy them
  beside the media on delivery.
- `projects/cab-rot-kimi-k3/` delivered 2026-08-10, 77m26s cut to 3:01, then
  **remastered twice the same day**, both times because David caught something
  every automated check had passed. First the music bed was inaudible
  (`mus_alone` -25 to -21; music-only passages went from -23 to -19 LUFS against
  a -14.4 program). Then the cards were not DPD at all: ffmpeg drawtext in
  Bahnschrift with an invented rust accent, ending on the wordmark set in the
  wrong typeface. Cards now render from `workspace/dpd-video-kit`
  (`SectionCard` / `EndCard`) via `cards.mjs` plus `"cards_dir"` and
  `"cards_cmd"` in `project.json`. Master, raw, and the edit sources are under
  `C:\media\video\cab-rot-kimi-k3\`. Its `README.md` carries the measurement
  behind every decision including both remasters.
- **`assets/dpd-Title Sequence.mp4` is untracked and must stay that way, and must
  not be deleted.** It is one of only two copies of the DPD title sequence, which
  has no source: `LogoSting` in `dpd-video-kit` is an earlier, plainer design and
  measures SSIM ~0.78 against this file. The other copy and nine reference stills
  are at `C:\media\video\dpd-title-sequence\`. The rebuild job (a `PhosphorCRT`
  wrapper so the cards inherit the ident's treatment) is written up in
  `workspace/dpd-video-kit/HANDOFF.md`. Until it lands, a DPD cut opens glowing
  and ends flat.
- `projects/fable5-dashboard/` (The Signal Room) delivered 2026-08-07. Its edit is
  still stranded in the gitignored dir; nothing was copied out.
- Both cutdowns were built with the `recording-cutdown` skill. Three silent-failure
  bugs in its `montage.py` were found and fixed during the Cab Rot run (uncropped
  timelapses, a snapper that could drop a phrase without flagging it, and
  synccheck failing on false positives). Both cuts predate those fixes, so re-read
  an old cut before trusting it.
