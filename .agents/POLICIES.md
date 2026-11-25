# AGENTS.md — POLICIES

Read for boundaries, priorities, verification, and DOX authoring rules.

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
- NEVER create temp files in project root. Use dedicated temp dirs.

## Change constraints

- Minimal, surgical edits. Preserve existing style.
- No new dependencies without explicit instruction.
- No unrelated refactoring while fixing a bug.

## Code quality

Universal defaults. Project-specific standards live in scoped contracts or
`.agents/policies/repository.md`.

- **SRP** — one reason to change per module/function.
- **DRY** — check before adding. Extract on third occurrence (Rule of Three).
- **Redundant code** — remove dead branches, unreachable conditions, unused
  params/imports before finishing.
- **Duplication vs. abstraction** — prefer duplication over wrong premature
  abstraction.
- No new code-quality tooling by default — opt in per project.

## Completion checklist

- Change solves the stated problem
- Relevant validation ran (or gaps stated)
- No unintended side effects or secrets exposed

## DOX rule index

- `.agents/policies/dox.md` — authoring tiers, plans, state subdirectories,
  documentation archives, and size budgets.
- `.agents/policies/repository.md` — GitHub releases, local tooling, README
  figures, and licensing.

## Verification

```bash
mise run check
mise run format-md
```

`check` is non-mutating. Run `format-md` only when formatting changes are
intended. Release automation is verified on GitHub with
`gh workflow view release` and `gh run list`; see
`.agents/policies/repository.md`.

## Response format

Concise and specific. No filler, intros, or restated requirements.
Answer direct questions directly.

For review/debugging/analysis: findings with references, conclusion,
approach. Mention caveats.
