# Bringing this fork up on a new machine

This branch (`fork-local`) is a backup, not a code branch. It carries the four
files that live outside git on the working machine: the agent contracts, the
Cursor rule, and a copy of the exclude list that hides them. It is never merged
and never becomes a PR.

Nothing here is secret. Keys are not in this branch and never should be.

## What this branch holds

| File | What it is |
|---|---|
| `AGENT_LOCAL.md` | The real agent contract. Overrides `AGENT_GUIDE.md` where they disagree. Agent-neutral on purpose: Claude Code, Codex, Cursor and Copilot all follow it as written. |
| `CLAUDE.local.md` | Claude Code's pointer into `AGENT_LOCAL.md`, plus the machine-specific gotchas. |
| `.cursor/rules/local.mdc` | Same contract, in the form Cursor loads automatically. |
| `git-info-exclude` | Copy of `.git/info/exclude`. A clone does not carry this, so you have to put it back by hand or all three files above show up as untracked. |

## Restoring on a fresh clone

```bash
git clone https://github.com/wretcher207/OpenMontage.git
cd OpenMontage
git remote add upstream https://github.com/calesthio/OpenMontage.git
git fetch origin fork-local
git checkout origin/fork-local -- AGENT_LOCAL.md CLAUDE.local.md .cursor/rules/local.mdc
git show origin/fork-local:git-info-exclude >> .git/info/exclude
```

The last line matters. Without it those three files sit untracked in every
`git status` and eventually follow a PR branch by accident, which is the exact
thing the exclude list exists to prevent. `SETUP-LOCAL.md` is in the exclude
list too, so pull it down separately if you want it on disk.

Note the remote naming. On the working machine `origin` is upstream
(`calesthio/OpenMontage`) and `fork` is the fork, because the repo was cloned
from upstream first. A fresh clone of the fork inverts that. Check
`git remote -v` before you push anything.

## What is NOT in this branch, and has to come from somewhere else

**`.env`.** Live API keys, gitignored (`.gitignore:44`), and it stays that way.
Source of truth is `workspace/api-keys.md`. The variables the repo actually
reads:

- `ELEVENLABS_API_KEY` — `elevenlabs_tts` narration and `music_gen`
- `FAL_KEY` and `FAL_AI_API_KEY` — flux, recraft, kling, minimax, seedance, veo
- `GEMINI_API_KEY` and `GOOGLE_API_KEY` — google_music (Lyria 3), google_tts,
  google_imagen, gemini_omni_video. Same value in both.
- `GOOGLE_CLOUD_PROJECT` — the project **ID**, not the number. Only
  `google_imagen` reads it, via `resolve_project_id` in
  `tools/google_credentials.py`. Lyria ignores it.

The direct MiniMax key has no consumer here. OpenMontage reaches MiniMax through
fal.ai, so `FAL_KEY` covers it.

**`.venv/`** and **`remotion-composer/node_modules/`.** Rebuildable, see below.

## Install

Built here on Python 3.14.6, Node 24.18.0. FFmpeg has to be on PATH separately.

`make` does not exist on the Windows box, so every `make setup` / `make preflight`
line in the repo docs fails outright. Run the steps directly:

```bash
python -m venv .venv
./.venv/Scripts/python.exe -m pip install -r requirements.txt   # Scripts/ on Windows, bin/ elsewhere
cd remotion-composer && npm install && cd ..
```

npm warns that esbuild's postinstall is blocked by `allow-scripts`. That is the
classic silent Remotion breaker, but esbuild 0.28.1 loads fine regardless,
verified on this machine. Do not go chasing it.

Preflight, the no-make way:

```bash
./.venv/Scripts/python.exe -c "from tools.tool_registry import registry; import json; registry.discover(); print(json.dumps(registry.provider_menu(), indent=2))"
```

Render engines should come back `{ffmpeg: True, remotion: True, hyperframes: True}`.
To prove the whole pipeline without spending anything, render a zero-key demo:
`./.venv/Scripts/python.exe render_demo.py world-in-numbers` produces a 1920x1080
h264+aac 30fps mp4. `render_demo.py --list` shows all three.

## Traps worth carrying over

- **`pytest tests/contracts/` rewrites `diagram.png`** as a side effect, via
  `tools/graphics/diagram_gen.py`. It shows up as a dirty binary file that is not
  your work. Revert it, do not commit it.
- **`fix/music-capability-discovery` will conflict on a pull from upstream.** It
  edits upstream-tracked files (`AGENT_GUIDE.md`, three director skills,
  `skills/INDEX.md`). That is why the clean cherry-pick
  `fix/music-plan-checks-all-capabilities` exists as the PR branch instead.
- **Machine-specific guidance goes in `AGENT_LOCAL.md` or `CLAUDE.local.md`,
  never in tracked files** including `CLAUDE.md`. Tracked files stay clean so
  PR branches stay clean.

## Branch map

- `main` — tracks `calesthio/OpenMontage`. Untouched.
- `fix/music-plan-checks-all-capabilities` — upstream PR #464, docs-only music
  capability fix, cherry-picked clean off upstream main.
- `fix/music-capability-discovery` — the same fix plus `music_selector`, the
  426-line tool registering under its own `music` capability. Deliberately not
  submitted upstream: CONTRIBUTING.md wants tests with behavior changes, and
  giving the selector its own capability is an architectural call a maintainer
  should weigh in on first.
- `fork-local` — this branch. Backup only.
