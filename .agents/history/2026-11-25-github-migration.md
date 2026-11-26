# 2026-11-25 — README, comparison, and GitHub migration

Implementation commit: `9a1c9ab3f769640e29b686c53ff9ccc347acb131`  
Canonical repository: <https://github.com/jr2804/agents-scaffold>

## Context

Codeberg announced restrictions on LLM-generated projects. The scaffold needed
a canonical GitHub home, clearer user-facing documentation, and figures that
remain legible in a README. The existing DOX state layout also needed an
evidence-based check against its two closest related projects.

## Comparison and decisions

Reviewed `agent0ai/dox` at
`765ae4ac02cc884eefcd41a3d0f71941721adb89` and `agentsmd/agents.md` at
`d001185d792eb6402a58e4cbef1c228b309ec25d` on 2026-11-25.

| Project | Role | Decision |
| ------- | ---- | -------- |
| `agent0ai/dox` | Copyable parent/child hierarchy | Keep the base; add state files, budgets, migration, checks |
| `agentsmd/agents.md` | Markdown convention and ecosystem | Keep format and precedence; not a scaffold/runtime |
| `anomalyco/knox` | Structured `.agents/` context and anti-bloat patterns | Keep attribution for the state-layer ideas |

Rejected unsupported performance claims, universal auto-loading language, and
child `AGENTS.md` files for small or hidden directories. Supporting agents must
read state files when their stated trigger applies; actual discovery and
injection remain client-dependent.

## Implemented changes

- Replaced placeholder DOX indexes and state files with current repository
  contracts.
- Made user instructions explicitly override repository instructions and
  narrowed No Patching to prohibit autonomous post-marker injection.
- Reworked the README, install/update contract, comparison table, hero SVG, and
  footer SVG; removed stale Codeberg setup URLs and the duplicate Codeberg skill
  source.
- Made updates fetch the full canonical file set from GitHub, failing closed
  instead of falling back to stale in-context content.
- Replaced Forgejo automation with a GitHub Actions workflow that pins actions
  and runs `mise run check`.
- Added MIT licensing and preserved DOX/AGENTS.md notices in
  `THIRD_PARTY_NOTICES.md`.
- Made GitHub the canonical remote while retaining the old Codeberg remote as
  `codeberg` until the source repository is archived or deleted.

## Verification

- `mise run check` passed Markdown lint and format checks for 12 files and XML
  validation for both README SVGs.
- `git diff --check` passed.
- Workflow YAML parsed successfully with the expected `push`/manual triggers,
  one job, and ordered checkout, install, and check steps.
- Repository metadata and live automation are verified after the first GitHub
  push.
