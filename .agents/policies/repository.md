# Repository-specific policies

Detailed rules indexed by `.agents/POLICIES.md`.

## GitHub releases

- A push to `main` or a manual dispatch creates the next unused
  `YYYY.M.PATCH` tag and GitHub Release.
- Run the non-mutating `mise run check` task before creating a tag.
- Use `github.token` through `GH_TOKEN`; never add a Forgejo token or endpoint.
- Grant `contents: write` only to the release job.
- Serialize release runs so concurrent pushes cannot select the same tag.
- Keep repository URLs, install examples, release automation, and Git remotes
  synchronized with the canonical GitHub repository.

## Local tooling

- Keep tool and task declarations under `.config/mise/`; reflect changes in
  `.agents/TOOLS.md` and `.agents/FILES.md`.
- Preserve the current `latest` tool-version policy unless the user requests
  pinning.
- `format-md` mutates files; `check` and `check-md` must remain non-mutating.
- Keep skill installation optional; it is not required for verification.

## README figures

- Keep SVGs self-contained: no external fonts, images, scripts, or network
  resources.
- Every figure needs `viewBox`, `role="img"`, and unique `aria-labelledby`
  targets.
- Preserve the slate-and-teal palette and system font stacks.
- Keep all text inside the canvas and legible at the width used in `README.md`.
- README alt text explains the figure's meaning, not its visible text.

## Licensing

- This project is MIT-licensed; see `LICENSE`.
- Preserve upstream attribution and permission notices in
  `THIRD_PARTY_NOTICES.md` when redistributing derived scaffold content.
- Do not replace upstream notices with a README credit link alone.
