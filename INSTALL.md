# INSTALL — Scaffold a project with AGENTS.md

Feed this file to your coding agent to set up the DOX hierarchy.

## Files to create

### Root `AGENTS.md`

Copy AGENTS.md from agents-scaffold. Fill sections 2–4:

**AGENTS.md §4 (Project rules):** 5-10 essential, frequently-broken rules that
must be injected on every LLM call. Examples: path conventions, import rules,
naming patterns, required config keys. Everything non-essential goes into
`.agents/` files.

### `.agents/ONBOARDING.md`

One-line project description. Entry points. Build/test commands. Reference
to tools (codegraph, grepai, repos, etc. if available).

### `.agents/POLICIES.md`

Keep the generic boundaries/priorities/verification template. Add
project-specific policies under the correct section.

### `.agents/FILES.md`

Map each category of definition to its source file. Example:

| What | Where |
|------|-------|
| Path constants | `src/project/paths.py` |
| Config defaults | `src/project/config.py` |

### `.agents/HISTORY.md`

Start empty. Add entries as decisions are made.

### `.agents/MAINTENANCE.md`

Keep generic template. Only change update triggers if project has unique needs.

## Migration instructions

### Review existing AGENTS.md

1. **Move project description →** `README.md` or `docs/`. Keep max 1 sentence
   in AGENTS.md.
2. **Delete tree views** — generate on demand with `rg --files | tree-cli --fromfile`.
3. **Delete history entries** — move important ones to `.agents/HISTORY.md`
   with git refs. Routine history stays in git log.
4. **Delete TODO lists** — use an issue tracker or beads.
5. **Move non-essential rules →** `.agents/POLICIES.md` or subtree AGENTS.md.
   Only inject what is needed on every LLM call.
6. **Move path/constant definitions →** `.agents/FILES.md`.
7. **Add ⛔ No Patching section** at end of root AGENTS.md.

### Check for tool patches

Search AGENTS.md for content inserted by tools (beads, linters, CI bots).
If found:
- Move legitimate rules to the correct `.agents/` file.
- Delete everything after the ⛔ No Patching block.

### Create subtree AGENTS.md files

For directories with dense local contracts:

```
src/api/AGENTS.md     → API-specific rules
tests/AGENTS.md       → Testing conventions
```

These are demand-loaded on entry and keep root AGENTS.md lean.