# 2026-11-26 — Remove publishing machinery and simplify docs

Implementation commit: `8637d61`

## Context

The issue report found that the scaffold had accumulated published artifacts,
duplicated rules, an extra policy directory, and a drifted copy of the DOX
core. The project is copied into other repositories; it does not need package
publishing automation.

## Decisions

- Keep no numbered artifacts. Remove all existing GitHub artifacts and local
  or remote references to them.
- Replace publishing automation with a read-only CI workflow on `push` and
  `pull_request`. It runs `mise run check`; it does not write to the repository.
- Install and migration docs fetch from the `main` branch, not a fixed
  reference.
- Keep a single `.agents/POLICIES.md`. Fold rule tiers, pointers, plans, figures,
  licensing, and workflow limits into it; remove the policy subdirectory.
- Restore the upstream DOX core from Core Contract through User Preferences.
  The remaining scaffold layer is the state table, project rules, and the
  No Patching section, within the 40-line limit.
- Document two intentional deviations: the Child DOX Index is `None`, and the
  upstream core is wrapped to the repository's 160-character Markdown limit.
- Rename every state-file heading to `# State file — <NAME>`, including the
  templates, so a root agent that loads several files never sees duplicate
  top-level `AGENTS.md` headings.
- Keep one canonical state table in root `AGENTS.md`; keep the live-context
  warning in `INSTALL.md`; keep the 120-line rule in `MAINTENANCE.md`; keep the
  no-tree/no-history/no-TODO rule in `README.md`; keep verification commands in
  `POLICIES.md`.

## Outcome

- `README.md` now states why the project exists and names the context tree.
- `INSTALL.md` is a short copy, fill, ignore, check, and migration guide.
- `.agents/` has six state files and no policy subdirectory.
- GitHub has no published artifacts, and CI is check-only.
- `mise run check` passes, including the stricter table line-length check.
- The publishing workflow and its write permission were removed.
