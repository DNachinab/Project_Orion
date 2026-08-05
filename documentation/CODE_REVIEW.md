# Code Review Process

## Before opening a PR

- Keep the PR small and scoped to one concern — easier to review, easier to revert.
- Make sure it builds and passes tests/linting locally.
- Write a description covering **what** changed and **why** (link an issue/ticket if one exists).
- Self-review your own diff first.

## Opening the PR

- Target `main`.
- Use a clear title following the [commit standards](COMMIT_STANDARDS.md) format, e.g. `feat(inventory): add reorder threshold alerts`.
- Mark as **draft** if it's not ready for review yet.

## Review requirements

- At least **one approval** required before merge (raise to two once the team grows beyond ~4 engineers or for changes touching shared/core modules — e.g. `backend/` auth, database schema, or `infrastructure/`).
- CI (build + tests + lint) must pass before merge.
- Author cannot approve their own PR.
- Reviewer response target: within 1 business day for normal PRs; same-day for anything blocking.

## What reviewers check

- Correctness — does it do what it claims, including edge cases?
- Security — no injected secrets, no unvalidated input crossing a trust boundary (especially payments, auth, financial data).
- Consistency — matches existing patterns in that module rather than introducing a parallel convention.
- Scope — no unrelated changes bundled in.
- Tests — new behavior has coverage; bug fixes include a regression test.

## Merging

- Squash-merge to keep `main` history linear and readable.
- Delete the branch after merge.
- Author merges once approved (unless the reviewer requests to merge themselves).
