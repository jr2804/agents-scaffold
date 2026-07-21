# AGENTS.md — POLICIES

Always applicable. Boundaries, priorities, verification, checklist.

## Priorities

1. Correctness
2. Evidence
3. Safety
4. Minimal changes
5. Consistency
6. Performance

## Boundaries

- NEVER fabricate paths, commits, APIs, config keys, env vars, test results,
  or benchmark numbers. If you don't know, say so.
- NEVER guess at command names, flags, or paths. Read source or run `--help`.
- NEVER add secrets, API keys, or tokens to files. Use env vars.
- NEVER run destructive commands (`rm -rf`, `git reset --hard`,
  `git push --force`) without explicit confirmation.
- NEVER delete or move files without explicit instruction.
- NEVER create temp files in project root. Use dedicated temp dir.

## Change constraints

- Minimal, surgical edits. Preserve existing style.
- No new dependencies without explicit instruction.
- No unrelated refactoring while fixing a bug.
- When changing tests, update only directly affected tests.

## Completion checklist

- Change solves the stated problem
- Relevant validation ran (or gaps explicitly stated)
- No unintended side effects introduced
- No secrets added or exposed

## Content rules (keep AGENTS.md lean)

- **No tree views.** Generate on demand with `rg --files | tree-cli --fromfile`.
- **No history.** Git log has it. Only record decisions costly to rediscover
  (in `.agents/HISTORY.md` with commit refs).
- **No TODO lists.** Use issue trackers or beads.

## Verification

[Project-specific verification commands — lint, test, typecheck, etc.]

## Response format

Concise and specific. No filler, intros, or restated requirements.
Answer direct questions directly.

For review/debugging/analysis: findings with references, conclusion,
approach. Mention caveats.

## Closeout

1. Run verification
2. Report docs intentionally left unchanged and why