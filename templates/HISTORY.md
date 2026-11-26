# State file — HISTORY

The one state file that may reference the past. Record decisions that are
costly to rediscover; leave routine history to Git.

## Format

| Date | Decision | Rationale | Git ref |
| ---- | -------- | --------- | ------- |
| YYYY-MM-DD | [decision] | [why] | [commit] |

## Record

- Architectural decisions and breaking changes.
- Tooling and platform choices, including the alternative that lost.
- Rejected approaches and the reason.

## Do not record

- Routine commits, session activity, or routine notes.
- Anything obvious from Git or current state files.

## Archiving

When work lands, consolidate its plan into
`.agents/history/<YYYY-MM-DD-plan-name>.md` and link it from the decision.
