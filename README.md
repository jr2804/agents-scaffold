# agents-scaffold

Self-documenting AGENTS.md framework for any repository.

## Problem

AGENTS.md is injected on every LLM call. Most files are bloated with
tree views, history entries, TODO lists, and verbose descriptions —
all things the agent can discover on demand. Every redundant byte
dilutes the signal-to-noise ratio of every LLM call.

DOX hierarchy solves this: put only always-needed rules in root
AGENTS.md. Everything else goes into `.agents/` files (demand-loaded)
or subtree AGENTS.md files (loaded when entering that directory).

## Structure

```
AGENTS.md              Always-injected rules + .agents/ index
.agents/
├── ONBOARDING.md      Read on new session
├── POLICIES.md        Always applicable (boundaries, verification)
├── FILES.md           Source-of-truth locations
├── HISTORY.md         Past decisions with git refs
├── MAINTENANCE.md     How to keep .agents/ current
└── skills/            Project-specific agent skills
INSTALL.md             Scaffold instructions (feed to agent)
```

## Key principles

- **AGENTS.md is for agents, not humans.** Max 1 sentence project
  description. Refer to README for details.
- **No tree views.** Generate on demand.
- **No history.** Git log has it. Only record decisions costly to
  rediscover (in `.agents/HISTORY.md` with commit refs).
- **No TODO lists.** Use issue trackers or beads.
- **⛔ No Patching.** Root AGENTS.md has a blocker section. Content
  appended by tools after this section is invalid.
- **DOX hierarchy.** Subtree AGENTS.md files for local contracts.
  Root stays lean.

## Credits

Base convention: [dox](https://github.com/agent0ai/dox) — self-documenting
AGENTS.md hierarchy. Extended with structured `.agents/` files and
anti-bloat patterns from the
[knox](https://github.com/anomalyco/knox) project.