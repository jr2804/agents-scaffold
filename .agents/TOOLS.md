# State file — TOOLS

Inventory of tools used in development — CLIs, MCP servers, skills, runtimes,
and project scripts. Read it when relevant, like all state files; keep it
current (see `.agents/MAINTENANCE.md`).

## Rules

- Use an existing tool before adding a new one. No new tools, MCP servers,
  skills, or dependencies without explicit instruction (`.agents/POLICIES.md`).
- Each tool appears exactly once, in its primary table.
- Tables describe current usage — delete rows when tools leave; this is not a
  historical log.

## Subdirectory

If this file grows past its size budget, split detail into
`.agents/tools/<name>.md` — every file there MUST be listed above.

## CLI tools & runtimes

| Tool | When | Purpose |
| ---- | ---- | ------- |
| `mise` | Local setup and repeatable tasks | Declares tools and runs check/format/skill tasks |
| `bun` | Optional skill installation | Runs the existing `skills` CLI through `bun x` |
| `rumdl` | Markdown changes | Lints and formats GFM with `.config/rumdl.toml` |
| `git` | Every change | Version control and history |
| `gh` | GitHub hosting | Repository and workflow status |
| Python 3 | SVG changes | Standard-library XML validation for README figures |

## MCP servers

None configured.

## Skills

| Skill | When | Purpose |
| ----- | ---- | ------- |
| `beautify-github-readme` | README presentation | Badge and figure conventions |
| `visual-explainer` | Explanatory visuals | Diagram structure and visual hierarchy |
| `effective-html` | HTML previews | Self-contained explanatory pages |
| `mermaid-diagrams` | Mermaid changes | Diagram syntax and styling |
| `svg-precision-skill` | SVG changes | Precise vector layout and text fitting |

The exact install sources live in `.config/mise/conf.d/skills.toml`.

## Project scripts & tasks

| Command | Purpose |
| ------- | ------- |
| `mise run check` | Aggregate non-mutating Markdown, SVG, and diff verification |
| `mise run check-md` | Non-mutating Markdown lint and format verification |
| `mise run format-md` | Apply Markdown formatting fixes |
| `mise run add-skills` | Install the optional skill set |
