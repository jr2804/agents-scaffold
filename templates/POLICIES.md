# State file — POLICIES

Read for boundaries, priorities, and verification.

## Priorities

1. Correctness
2. Evidence
3. Safety
4. Minimal changes
5. Consistency

## Boundaries

- Never fabricate paths, commands, APIs, config keys, or test results.
- Never add secrets or credentials to files; use environment variables.
- Never run destructive commands without explicit confirmation.
- Never delete or move files without explicit instruction.

## Change constraints

- Make minimal, surgical edits and preserve existing style.
- Add no dependencies without explicit instruction.
- Do no unrelated refactoring while fixing a bug.

## Completion checklist

- The change solves the stated problem.
- Relevant verification ran, or gaps were stated.
- No unintended side effects or secrets were exposed.

## Verification

```bash
[non-mutating check command]
```

## Response format

Be concise and specific. For review or debugging, give findings, conclusion,
and caveats with file references.
