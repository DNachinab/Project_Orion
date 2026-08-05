# Commit Standards

BusinessOS follows [Conventional Commits](https://www.conventionalcommits.org/).

## Format

```
<type>(<scope>): <short summary>

[optional body]

[optional footer(s)]
```

- **type** — one of:
  - `feat` — new feature
  - `fix` — bug fix
  - `docs` — documentation only
  - `refactor` — code change that neither fixes a bug nor adds a feature
  - `test` — adding or correcting tests
  - `chore` — tooling, dependencies, build config
  - `perf` — performance improvement
- **scope** — the module or area affected, matching the repo structure where possible: `frontend`, `backend`, `mobile`, `infrastructure`, `procurement`, `inventory`, `accounting`, `sales`, `invoicing`, `hr`, `bi`, `ai-assistant`.
- **summary** — imperative mood, lowercase, no trailing period. E.g. `add`, not `added` or `adds`.

## Examples

```
feat(inventory): add reorder threshold alerts
fix(invoicing): correct tax rounding on recurring invoices
docs: add branching strategy
refactor(backend): extract purchase-order validation into shared service
chore(infrastructure): pin container base image versions
```

## Body & footers

- Use the body to explain *why*, not *what* (the diff already shows what).
- Reference issues with `Refs #123` or close them with `Closes #123`.
- Breaking changes: start a footer with `BREAKING CHANGE:` and describe the impact/migration.

## Granularity

- Each commit should be a coherent, working change — avoid "WIP" or "fix typo" commits landing on `main` (squash-merge from PRs handles this automatically; keep in-branch commits reasonably clean too).
