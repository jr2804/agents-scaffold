# 2026-11-25 — Template separation and README reset

Implementation: `f89464e12038579b60e71655ed04b0fab9f30ffa`

## Problem

The shipped docs pointed users at this repository's live `.agents/*.md` files
as if they were blanks, copied `LICENSE` and `THIRD_PARTY_NOTICES.md` into user
projects, and buried setup behind a long agent-facing manual. The README also
included unrelated research and development sections.

## Decision

- Keep `.agents/*.md` here as this repository's live project context.
- Add six blank, copyable files under `templates/`.
- Point README and INSTALL at `templates/`, never at the live state files.
- Keep README and INSTALL short: manual copy, one agent URL, migration checklist.
- Do not tell users to copy the scaffold's license or upstream notices.

## Outcome

- `templates/` holds `ONBOARDING.md`, `POLICIES.md`, `FILES.md`, `TOOLS.md`,
  `HISTORY.md`, and `MAINTENANCE.md`.
- `README.md` and `INSTALL.md` were rewritten for users; knox, research tables,
  CLI plumbing, and development instructions were removed.
- Root rules and repository policies record the live-context/template split.
- `mise run check` and `git diff --check` passed before the implementation
  commit.
