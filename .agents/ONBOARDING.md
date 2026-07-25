# AGENTS.md — ONBOARDING

Read this when starting a new session. After first read, only revisit when
project structure or tooling changes significantly.

## Project

One-line description. Full docs at `README.md` or `docs/`.

## Quick start

```bash
# build
# test
# lint
# typecheck
```

## Entry points (read these first)

| File | Why |
|------|-----|
| `AGENTS.md` | Root rail — rules + `.agents/` index |
| `.agents/POLICIES.md` | Boundaries, priorities, verification |
| `.agents/FILES.md` | Source-of-truth locations |

## Where to dig deeper

- `docs/` — user-facing documentation
- `.agents/HISTORY.md` — past decisions and rationale
- Source-tree AGENTS.md files — local contracts for each area

## Available tools

If MCP/CLI tools are available for this workspace:

- **codegraph** — symbol search, call graphs
- **grepai** — find code by intent
- **repowise** — architecture overview, risk, health
- Any project-specific tools
