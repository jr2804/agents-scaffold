# DOX authoring and maintenance rules

Detailed rules indexed by `.agents/POLICIES.md`.

## Where a rule lives

A rule goes in the **highest (most general) tier that fully applies**:

- Applies to **all code in the project** → `.agents/POLICIES.md` (default).
- Meaningful **only inside one subtree** → that subtree's `AGENTS.md`.
- Just helps navigation → the parent's Child DOX Index, nothing else.

Do not create a child `AGENTS.md` for a small or hidden directory unless its
local contract is dense enough to justify separate discovery.

## Reference, don't restate

A rule appears in **exactly one file**. Other files use a pointer line:
`<topic> — see <file>`. Never copy the rule, rationale, or example.

## Rule first, rationale second, never third

A DOX line is the rule. If a rationale is costly to rediscover, add one short
clause. No multi-paragraph explanations or code pairs — those belong in a
skill or `docs/`, linked once.

## Content rules

- **No tree views.** Generate on demand with `rg --files | tree-cli --fromfile`.
- **No history in AGENTS.md files.** Record only decisions costly to rediscover
  in `.agents/HISTORY.md` or `.agents/history/`.
- **Lean state files.** Split detail into the matching `.agents/<topic>/`
  subdirectory when a state file approaches **120 lines**.
- **Lean subtree contracts.** Keep each subtree `AGENTS.md` at or below
  **250 lines**.
- **Index every detail file.** A file missing from its owning state-file index
  is dead content.
- **No TODO lists.** Use issue trackers or beads.
- Prefer direct bullets with explicit names.
- Trim obvious statements, repeated rules, and detail that no longer applies.

## Implementation plans

- Plans, refactoring plans, and design docs go in
  `.agents/plans/<YYYY-MM-DD>-<feature-name>/` — NOT under version control.
- Name phases with numeric prefixes so file order matches implementation order.
- NEVER commit plans to git. They are mutable working artifacts.
- Archive a plan when its work lands; do not wait for a maintenance pass.

## State file subdirectories

| State file | Optional subdirectory |
| ---------- | -------------------- |
| `FILES.md` | `.agents/files/` |
| `POLICIES.md` | `.agents/policies/` |
| `TOOLS.md` | `.agents/tools/` |
| `MAINTENANCE.md` | `.agents/maintenance/` |

Only create a subdirectory when its state file approaches its size budget.
Every file inside must be listed in the owning state file with a one-line
description. `ONBOARDING.md` and `HISTORY.md` have no matching subdirectories.

## Documentation and archives

- Shipped guides and references go in `docs/` and ARE committed.
- When `.agents/HISTORY.md` grows large, archive older entries to
  `.agents/history/` and leave a pointer.
- Consolidate a completed plan into
  `.agents/history/<YYYY-MM-DD-plan-name>.md`, remove the plan directory, and
  link the archive from `.agents/HISTORY.md` with the implementation commit.
- `.agents/history/` IS version-controlled.
- State files describe current contracts; never append session notes,
  iteration logs, or changelogs. `.agents/HISTORY.md` is the only exception.
