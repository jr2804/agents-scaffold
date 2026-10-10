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
- `.agents/TOOLS.md` — tools, MCP servers, skills, CLIs in use
- `.agents/HISTORY.md` — past decisions and rationale
- Source-tree AGENTS.md files — local contracts for each area

## Available tools

Development tools, MCP servers, skills, and CLIs are inventoried in the
state file `.agents/TOOLS.md` — read it before assuming a tool, update it
when tooling changes.
