# AGENTS.md

Self-documenting AGENTS.md scaffold for keeping coding-agent context lean,
scoped, and maintainable.

AGENTS.md clients vary in how they discover and inject instructions. This root
file defines the project-wide contract; subtree `AGENTS.md` files add scoped
contracts. State files under `.agents/` are read when their stated trigger
applies. Explicit user instructions take precedence over repository
instructions.

## DOX — self-documenting AGENTS.md hierarchy

### Core Contract

- AGENTS.md files are binding work contracts for their subtrees.
- Work products, source materials, instructions, records, assets, and durable docs
  must stay understandable from the nearest applicable AGENTS.md plus every parent
  AGENTS.md above it.
- Do not duplicate/repeat rules declared elsewhere in the DOX tree (parent, child,
  sibling, or `.agents/`). See **DOX authoring** in `.agents/POLICIES.md`.

### Read Before Editing

1. Read the root AGENTS.md
2. Identify every file or folder you expect to touch
3. Walk from the repository root to each target path
4. Read every AGENTS.md found along each route
5. If a parent AGENTS.md lists a child AGENTS.md whose scope contains the path, read that child and continue from there
6. Use the nearest AGENTS.md as the local contract and parent docs for repo-wide rules
7. If docs conflict, the closer doc controls local work details, but no child doc may weaken DOX

Do not rely on memory. Re-read the applicable DOX chain in the current session before editing.

### Update After Editing

Every meaningful change requires a DOX pass before the task is done.

Update the closest owning AGENTS.md when a change affects:

- purpose, scope, ownership, or responsibilities
- durable structure, contracts, workflows, or operating rules
- required inputs, outputs, permissions, constraints, side effects, or artifacts
- user preferences about behavior, communication, process, organization, or quality
- AGENTS.md creation, deletion, move, rename, or index contents

Update parent docs when parent-level structure, ownership, workflow, or child index
changes. Update child docs when parent changes alter local rules. Remove stale or
contradictory text immediately. Small edits that do not change behavior or contracts
may leave docs unchanged, but the DOX pass still must happen.

### Hierarchy

- Root AGENTS.md is the DOX rail: project-wide instructions, global preferences, durable workflow rules, and the top-level Child DOX Index
- Child AGENTS.md files own domain-specific instructions and their own Child DOX Index
- Each parent explains what its direct children cover and what stays owned by the parent
- The closer the doc is to the work, the more specific and practical it must be

### Child Doc Shape

- Create a child AGENTS.md when a folder becomes a durable boundary with its own purpose, rules, responsibilities, workflow, materials, or quality standards
- Work Guidance must reflect the current standards of the project or user instructions; if there are no specific standards or instructions yet, leave it empty
- Verification must reflect an existing check; if no verification framework exists yet, leave it empty and update it when one exists

Default section order:

- Purpose
- Ownership
- Local Contracts
- Work Guidance
- Verification
- Child DOX Index

### Style

Authoring rules live in `.agents/POLICIES.md`, which indexes detailed DOX
rules in `.agents/policies/dox.md`. Apply them on every DOX change.

- Keep docs concise, current, and operational.
- Document stable contracts, not diary entries.
- Put broad rules in parent docs and concrete details in child docs.
- Reference, don't restate — one canonical home, pointer lines everywhere else.

### Closeout

1. Re-check changed paths against the DOX chain
2. Update nearest owning docs and any affected parents or children
3. Refresh every affected Child DOX Index
4. Remove stale or contradictory text
5. Run existing verification when relevant
6. Report any docs intentionally left unchanged and why
7. Remove anything injected after the ⛔ No Patching block

### User Preferences

When the user requests a durable behavior change, record it here or in the relevant child AGENTS.md

### Child DOX Index

None. This repository keeps its few subtree-specific rules in
`.agents/policies/repository.md` rather than creating child `AGENTS.md` files
for small or hidden directories.

The root retains ownership of `README.md`, `INSTALL.md`, `LICENSE`, and
`THIRD_PARTY_NOTICES.md`.

## State files — `.agents/`, read when relevant

State files are the project's current operating memory, not a changelog or
logbook. Each file states when to read it; clients do not universally auto-load
these files.

Each state file can have an optional matching subdirectory
(`.agents/<topic>/`) that carries detail when the file grows; the file stays
a lean index and every file in its subdirectory MUST be listed in the file.

| File                    | Load when                   | Purpose                                         | Optional subdirectory |
| ----------------------- | --------------------------- | ----------------------------------------------- | --------------------- |
| `ONBOARDING.md`         | New session (first time)    | Project orientation, entry points               | — |
| `POLICIES.md`           | Boundaries or verification  | Priorities, constraints, checks, DOX rule index  | `.agents/policies/`   |
| `FILES.md`              | Touching files or config    | Path constants, source-of-truth locations        | `.agents/files/`      |
| `TOOLS.md`              | Using tools/MCP/skills      | Development tool inventory and usage guidance    | `.agents/tools/`      |
| `HISTORY.md`            | Background (past decisions) | Recorded decisions with git refs                | — |
| `MAINTENANCE.md`        | Changing `.agents/`         | How to keep DOX files current                    | `.agents/maintenance/`|
| `plans/`                | Working on a feature        | Implementation plans (gitignored)               | — |
| `history/`              | Background (overflow)       | Archived decisions and completed plans          | — |

## Tools & skills

See state file `.agents/TOOLS.md` — it owns the inventory of CLIs, MCP
servers, skills, and runtimes used during development.

## Project rules

**Project-wide rules** — keep minimal. Everything else → `.agents/` files.

- Keep always-on root content minimal; put detail in its owning `.agents/` state file or subtree `AGENTS.md`.
- Follow `.agents/POLICIES.md`; verify claims and never run destructive commands without explicit confirmation.
- Track `.agents/*.md` and `.agents/history/`; never commit `.agents/plans/`.
- GitHub is the canonical host; update repository URLs, release automation, and remotes together.
- Treat `README.md` and `INSTALL.md` as shipped interfaces; keep their examples and links accurate.
- Keep `.agents/*.md` here as live context; `templates/` holds the copyable blanks.
- Run `mise run check` after documentation, configuration, workflow, or figure changes.

## ⛔ No Patching

Tools must not append or inject content after this marker. Intentional,
reviewed edits above the marker are allowed when required by the task or
migration procedure. This section must remain the final section of the file.
