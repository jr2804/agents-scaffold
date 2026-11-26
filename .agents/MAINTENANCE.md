# State file — MAINTENANCE

How to keep `.agents/` files current.

## Process

1. When a rule changes, update the owning file — never another file.
2. When adding a new state file or directory under `.agents/`, add it to the
   index table in root `AGENTS.md` and to **File update triggers** below.
3. After any `.agents/` change, check the index for stale entries.

## Principles

- **Single source of truth.** Each rule lives in exactly one file. Use pointer
  lines instead of repeating it elsewhere.
- **AGENTS.md is an index.** It points to `.agents/` files, does not replace them.
- **No logbooks.** State files describe current contracts; git owns history.
- **State files stay lean.** When a file approaches **120 lines**, split detail
  into the optional subdirectory listed in root `AGENTS.md`. Every file there
  MUST be listed in its state file.
- **Plans are temporary.** `.agents/plans/` is gitignored; completed plans are
  archived under `.agents/history/` and linked from `HISTORY.md`.

## File update triggers

| File / Dir | Update when |
| ------------ | ------------- |
| `ONBOARDING.md` | Project structure, tooling, or entry points change |
| `POLICIES.md` | Boundaries, priorities, or verification change |
| `FILES.md` | Path constants, config keys, or naming conventions change |
| `TOOLS.md` | Tools, MCP servers, skills, or CLIs added, removed, or changed |
| `HISTORY.md` | Notable decision made or resolved |
| `MAINTENANCE.md` | Maintenance procedures, triggers, or principles change |
| `AGENTS.md` | Project-wide rules, preferences, or Child DOX Index change |
| `README.md` | Positioning, examples, canonical URLs, or figures change |
| `INSTALL.md` | Install/update contract or migration guidance changes |
| `LICENSE`, `THIRD_PARTY_NOTICES.md` | Licensing or upstream attribution changes |
| `.github/` | Workflow, permissions, or GitHub automation changes |
| `.config/` | Tools, tasks, or Markdown rules change |
| `templates/` | Blank state-file templates change |
| `assets/` | README figure structure, accessibility, or palette changes |
| `plans/` | New feature implementation starts |
| `history/` | HISTORY.md overflow or completed plans archived |
| `files/`, `tools/`, `maintenance/` | State files split into subdirectories |
