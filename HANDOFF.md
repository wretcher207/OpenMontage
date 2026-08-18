> status: active | one-liner: OSS agentic video platform, fork of calesthio/OpenMontage, with local contributions going upstream | next: David watches WGYC redux rev 5 (2:44, registration redacted in 3 shots); music_selector tests + upstream PR still pending

# HANDOFF - OpenMontage

Upstream clone plus local work. Contribute changes upstream rather than
diverging.

Created 2026-08-14.

## Agent contract

`WORKFLOW.md` (untracked, fork-local) is the whole contract and it is one page.
`AGENT_GUIDE.md`, `pipeline_defs/` and `skills/` are upstream reference, not
binding here. `PROJECTS-LOCAL.md` (untracked) holds delivery records and
per-project facts.

## Workflow reset, 2026-08-16

David's call. The fork had four stacked layers of video rules: upstream's
mandatory pipeline system, a fork-local file that existed mainly to cancel it,
the global cutting skill, and a set of per-video memory rules generalised from
single past jobs. The layers contradicted each other and the output showed it.

All of it collapsed into `WORKFLOW.md`: four non-negotiables covering money and
honesty, and otherwise the agent's judgment stated in a sentence per video. No
route table, no per-type rule sets, no forced gates.

**Shelved, deliberately, do not rebuild without asking:** the video-type router.
The previous plan was to split the cutdown path into named types (talking head,
craft b-roll, event coverage, performance, montage) each with its own selection
logic, audio contract, pacing and card rules. That is the exact "arbitrary rules
for different things" this reset removed. The underlying observation still
stands and is worth knowing: `~/.claude/skills/recording-cutdown/` is
transcript-driven end to end (filler removal, rambling removal, word-boundary
cut points, webcam PIP handling), so it fits a talking head and fits nothing
else well. Treat that as a known limitation to work around per job, not as a
spec to implement.

**Also ruled out 2026-08-16, do not re-propose:** integrating the third-party
`AgriciDaniel/claude-youtube` skill (14 YouTube strategy and packaging commands).
Evaluated and dropped.

## Open work

- `music_selector` needs tests, then an upstream PR. Branch
  `fix/music-capability-discovery` carries it (809fce0, 9e6f370) and will
  conflict on pull. Upstream PR #464 (the docs half) is open.
- WGYC camper-top build is in progress and blocked on the client sending usable
  finished-top media. Plan is `WGYC-BUILD-HANDOFF.md`; facts are in
  `PROJECTS-LOCAL.md`.
