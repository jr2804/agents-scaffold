# AGENTS.md — FILES

Single source of truth for paths, config keys, and naming conventions.
Kept compact — agents hallucinate less when they know where definitions live.

## Pattern

- One file owns each class of definition (paths, config defaults, enums).
- Import from that file. Never hard-code values in other modules.
- Variables that address files get `_file` suffix; directories get `_dir`.

## Project-specific sources of truth

| What | Where | Key names |
|------|-------|-----------|
| DOX root contract | `AGENTS.md` | Project rules, Child DOX Index, No Patching |
| State-file contracts | `.agents/*.md` | ONBOARDING, POLICIES, FILES, TOOLS, HISTORY, MAINTENANCE |
| Detailed DOX rules | `.agents/policies/dox.md` | Authoring, plans, archives, size budgets |
| Repository policies | `.agents/policies/repository.md` | Releases, tooling, figures, licensing |
| Install/update behavior | `INSTALL.md` | Modes, immutable source, fail-closed migration |
| Project license | `LICENSE` | MIT terms |
| Upstream notices | `THIRD_PARTY_NOTICES.md` | DOX and AGENTS.md attribution |
| Canonical repository URL | `README.md` | GitHub raw URL for `INSTALL.md` |
| Markdown rules | `.config/rumdl.toml` | `global.disable`, `line-length`, `flavor` |
| Tool declarations | `.config/mise/config.toml` | `tools.bun`, `tools.rumdl` |
| Project tasks | `.config/mise/conf.d/format.toml` | `check`, `check-md`, `format-md` |
| Optional skills | `.config/mise/conf.d/skills.toml` | `add-skills` |
| Release automation | `.github/workflows/release.yml` | CalVer tag, `GH_TOKEN`, generated notes |
| README figures | `assets/readme/*.svg` | `hero.svg`, `made-with-beautify.svg` |

## Subdirectory

If this file grows past its size budget, split detail into
`.agents/files/<name>.md` — every file there MUST be listed above.
