# AGENTS.md — ONBOARDING

Read this when starting a new session. After first read, only revisit when
project structure or tooling changes significantly.

## Project

Copy-paste DOX convention for lean root instructions, conditionally read
`.agents/` state, and scoped subtree contracts. User-facing docs live in
`README.md` and `INSTALL.md`.

## Quick start

```bash
mise install
mise run check
mise run format-md
```

## Entry points (read these first)

| File | Why |
|------|-----|
| `AGENTS.md` | Root rail — rules + Child DOX Index |
| `.agents/POLICIES.md` | Boundaries, priorities, verification |
| `.agents/FILES.md` | Source-of-truth locations |
| `README.md` | Positioning, mechanism, and integration examples |
| `INSTALL.md` | Shipped install/update migration contract |

## Where to dig deeper

- `.agents/TOOLS.md` — tools, skills, runtimes, and project tasks
- `.agents/MAINTENANCE.md` — state-file ownership and update triggers
- `.agents/HISTORY.md` — durable decisions and plan archives
- `.github/workflows/release.yml` — CalVer release automation
- `assets/readme/` — README figures
- Subtree `AGENTS.md` files — local contracts for each area

## Available tools

Development tools, MCP servers, skills, and CLIs are inventoried in
`.agents/TOOLS.md`. Tool declarations and tasks live under `.config/mise/`.
