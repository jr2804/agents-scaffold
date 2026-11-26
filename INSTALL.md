# INSTALL — agents-scaffold

Use this file to add the DOX convention to a repository. Follow it manually or
give it to a coding agent.

## What to copy

- Root `AGENTS.md` → your repository root.
- The six files in `templates/` → `.agents/` in your repository.

Do **not** copy this repository's own `.agents/` files. They are its live
project context, not blanks for another project. `LICENSE` and
`THIRD_PARTY_NOTICES.md` belong to this scaffold and are not part of an install.

## Steps

1. Copy the files listed above.
2. Fill the placeholders in each `.agents/*.md` file. Delete any file you do
   not need, and update the state-file table in `AGENTS.md` to match.
3. Fill **Project rules** and **Child DOX Index** in `AGENTS.md`. Keep the
   ⛔ No Patching section last.
4. Add the ignore rules below.
5. Run your repository's existing non-mutating check, if one exists.

```gitignore
# Keep DOX files tracked; ignore mutable plans
/.agents/*
!/.agents/*.md
!/.agents/history/
!/.agents/history/**
!/.agents/files/
!/.agents/files/**
!/.agents/tools/
!/.agents/tools/**
!/.agents/maintenance/
!/.agents/maintenance/**
/.agents/plans/
```

## Templates

The six files in `templates/` mirror the state table in root `AGENTS.md`.
Copy them all, then delete the ones you do not need.

## For coding agents

1. Fetch `AGENTS.md` and `templates/*.md` from the default branch at
   <https://github.com/jr2804/agents-scaffold>.
2. If any required file cannot be fetched, stop and report the failure. Do not
   fall back to stale content in the conversation.
3. Merge the template files into the repository. Preserve project-specific
   content, rules, and decisions.
4. Report which files were added, updated, or left unchanged.

## Migrating an existing `AGENTS.md`

- Move the project description to `README.md`; keep at most one sentence in
  `AGENTS.md`.
- Move non-essential rules to `.agents/POLICIES.md`, tool inventories to
  `.agents/TOOLS.md`, and path definitions to `.agents/FILES.md`.
- Move durable decisions to `.agents/HISTORY.md` with Git references.
- Add subtree `AGENTS.md` files only where a directory has dense local rules.
- Add the ⛔ No Patching section at the end of `AGENTS.md`.
