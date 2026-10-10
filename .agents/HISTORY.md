# AGENTS.md — HISTORY

State file. The one file that may reference the past — sparingly. Read when
relevant to the current task; long-term memory for decisions, not a log.
Routine history lives in git; only record what is costly to rediscover.

## Format

| Date | Decision | Rationale | Git ref |
| ---- | -------- | --------- | ------- |
| YYYY-MM-DD | [description] | [why] | [commit hash/tag] |

## Record

- High-level architectural decisions and breaking changes.
- Dependency, tooling, and platform choices — including the alternative that lost.
- False turns and rejected approaches, with the reason.

## Do not record

- Routine commits, refactor logs, session activity, release notes.
- Anything obvious from git, the code, or current AGENTS.md/state files.

## Guidance

- Keep entries brief — enough to reconstruct the reasoning.
- Link to the relevant commits or tags.
- If this file grows large, move older entries to `.agents/history/` and keep
  a pointer here.
- Completed implementation plans are archived as single files at
  `.agents/history/<YYYY-MM-DD-plan-name>.md` and linked from the decision
  entry they belong to.
