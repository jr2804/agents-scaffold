# AGENTS.md — MAINTENANCE

How to keep `.agents/` files current.

## Process

1. When a rule changes, update its owning file only.
2. When adding a state file or detail file, add it to the owning state-file index.
3. After any `.agents/` change, check for stale entries.

## Principles

- One rule, one home. Other files use pointer lines.
- State files describe current contracts, not logs.
- Split detail into the matching `.agents/<topic>/` directory near 120 lines.
- Plans are gitignored; completed plans archive to `.agents/history/`.

## File update triggers

| File / Dir | Update when |
| ---------- | ----------- |
| `ONBOARDING.md` | Structure, tooling, or entry points change |
| `POLICIES.md` | Boundaries, priorities, or verification change |
| `FILES.md` | Source-of-truth locations change |
| `TOOLS.md` | Tools, skills, or CLIs change |
| `HISTORY.md` | A notable decision is made |
| `MAINTENANCE.md` | Maintenance process changes |
