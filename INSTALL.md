# INSTALL — Scaffold a project with AGENTS.md

Feed this file to your coding agent to set up the DOX hierarchy.

> **⚠ Note on `.agents/` directory**
> The `.agents/` subdirectory is a common convention — tools, skills, and
> agent runtimes may already create one in your project. It is also
> frequently listed in `.gitignore` patterns (especially when added by
> Copilot, Cursor, or similar tooling). **You must add git exclusion
> rules** in your project's `.gitignore` so that the DOX markdown files
> under `.agents/` are tracked by version control:
>
> ```gitignore
> # Keep .agents/ DOX .md files tracked (override any blanket ignore)
> /.agents/*
> !/.agents/*.md
> ```
>
> The second line is the essential one — it un-ignores `.md` files inside
> `.agents/`. The first line (`/.agents/*`) sets up the ignore rule that
> the second line then overrides.
>
> **If your project's `.gitignore` already has a blanket ignore for this
> directory** (e.g. `/.agents/`, `/.agents`, or just `.agents`), the
> first line is redundant — you only need the `!/.agents/*.md` line:
>
> ```gitignore
> # Keep .agents/ DOX .md files tracked (override existing ignore)
> !/.agents/*.md
> ```
>
> **Conversely, if your project already has explicit inclusion rules**
> for `.agents/` (e.g. `!.agents/` + `!.agents/**`, or a
> project-specific pattern that already covers `.md` files), then no
> gitignore change is needed at all — skip the whole block.
>
> In both cases, the goal is the same: only the five DOX `.md` files
> are tracked; anything else tools may drop in `.agents/` (configs,
> binaries, lock files) stays ignored.

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

| What            | Where                   |
| --------------- | ----------------------- |
| Path constants  | `src/project/paths.py`  |
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

```text
src/api/AGENTS.md     → API-specific rules
tests/AGENTS.md       → Testing conventions
```

These are demand-loaded on entry and keep root AGENTS.md lean.
