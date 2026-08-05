# Branching Strategy

BusinessOS uses **trunk-based development with short-lived feature branches**. This is recommended for a small/early-stage team building a modular platform: it avoids the merge overhead of long-lived branches (e.g. GitFlow's `develop`) while still gating everything through review.

## Branches

- **`main`** — always deployable. Protected: no direct pushes, requires a passing build and at least one approving review to merge.
- **`feature/<short-description>`** — one branch per unit of work, cut from `main`. Example: `feature/procurement-purchase-orders`.
- **`fix/<short-description>`** — bug fixes, same rules as feature branches. Example: `fix/invoice-tax-rounding`.
- **`release/<version>`** *(introduced once we have external customers / mobile app store cycles)* — stabilization branch cut from `main` for a release; only fixes get cherry-picked in.

## Workflow

1. Branch off `main`: `git checkout -b feature/xyz`
2. Commit small, working increments (see [COMMIT_STANDARDS.md](COMMIT_STANDARDS.md)).
3. Push and open a PR against `main` early (draft PR is fine) — see [CODE_REVIEW.md](CODE_REVIEW.md).
4. Keep the branch short-lived (days, not weeks). Rebase on `main` regularly to avoid drift.
5. Squash-merge into `main` once approved and CI passes. Delete the branch after merge.

## Rules

- Never commit directly to `main`.
- Never force-push to `main`.
- Keep feature branches scoped to one module/concern where possible — this repo's `frontend/`, `backend/`, `mobile/`, `infrastructure/` split means most changes should touch one top-level directory at a time.
- Tag releases on `main` (`v0.1.0`, etc.) once we have a real release cadence.
