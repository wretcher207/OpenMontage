# Machine-local notes (untracked)

**Read [`AGENT_LOCAL.md`](AGENT_LOCAL.md) first.** It is the fork's real agent
contract and it **overrides `CLAUDE.md` and `AGENT_GUIDE.md` where they disagree**,
including `CLAUDE.md`'s "read AGENT_GUIDE.md before responding to ANY user message"
line. `AGENT_GUIDE.md` is a reference to consult per task, not a preamble.

`AGENT_LOCAL.md` is agent-neutral on purpose: Codex, Cursor, and Copilot follow the
same file, so the fork behaves the same whichever agent is driving. Put nothing
Claude-specific in it, and put nothing fork-wide in here.

It carries: task routing, the autonomy contract, standing pre-authorization for
checkpoint gates, presentation rules, the non-negotiables, this machine's facts,
and current fork status.

## Claude Code only

- Nothing at present. Anything that would go here and also apply to Codex belongs
  in `AGENT_LOCAL.md` instead.
