# Repository Maintenance Handoff

Last updated: 2026-08-07 22:12 CST (UTC+8)

This file is the current handoff for maintenance across the `zhangshujuan1314/*` repositories. It records only work that has been verified from repository state, pull requests, issues, or CI. Historical actions belong in `MAINTENANCE_LOG.md`.

## Operating rules

1. Security and data-loss risks before cosmetic cleanup.
2. Structural or destructive changes go through a branch + PR unless the change is metadata/documentation only.
3. Do not call a fix complete until there is repository/CI evidence when CI is available.
4. README claims are not test evidence.
5. Generated binaries/ZIPs belong in Releases or CI artifacts, not source history.
6. Secrets never belong in repository files, encrypted or otherwise, when the decryption key is also in the repository.
7. Keep Issues for unresolved work; close only when the actual external dependency is complete.
8. `MAINTENANCE_LOG.md` is append-only.

## Current priority queue

### P0 / P1

- **youdian-shouhuo** — credential rotation remains externally actionable. Repository-side encrypted env files/decrypt helper were removed, but old JWT/API/MongoDB/SMTP/etc. credentials must be revoked/rotated at their providers. Keep the rotation issue open until that is verified.
- **cyber-flower** — public JWT fallback has been removed and the production configuration now fails closed. Continue with duplicate nested repository cleanup, then restore ESLint/E2E gates and reduce dependency audit debt.
- **books** — review redistribution rights for committed commercial-book PDFs. Do not rewrite history or delete files until redistribution authorization is known.

### Reliability

- **frontier-radar** — workflow commit-step fix is merged. Verify a scheduled run that starts after the fix; do not use pre-fix scheduled failures as evidence against the fix.
- **cyber-flower** — unit-test gate is restored and verified. E2E and lint remain incomplete.
- **mybrain** — CI is established; clean runner verified 131 tests passing at time of setup.
- **quanttrader** — Argon2id password migration, production JWT-secret guard, Docker env corrections, and default-deny arbitrary strategy execution are merged and CI-verified. Custom Python execution must remain trusted-code-only until a real isolation boundary exists.

### Repository governance / presentation

- **cineweave-studio** — phase/status reports moved from repository root to `docs/archive/status-reports/`; treat them as historical snapshots, not current release truth.
- **roundtable** — source tree still contains `Roundtable-v1.0.0-Windows.zip`, while GitHub Releases was empty when checked. Create a real Release before removing the only downloadable package from source.
- **ai-zhihang** — generated ZIP artifacts removed from source and ignored going forward.
- **nuanxingzhe-ai** — marked Legacy; maintained successor is `nuanxingzhe-ai-next`.
- **pxpipe** — clarify upstream/original-project attribution before using it as an original flagship project.
- **cc-cockpit** — replace README screenshot/GIF placeholders with real product evidence before promoting it as a flagship release.

## Active work

### cyber-flower

- PR #6: remove stale nested `cyber-flower/` project copy. The branch is based on latest maintenance state and must pass CI before merge.
- Issue #2: restore real lint + E2E gates and address dependency audit findings.

## Recommended next actions

1. Finish and merge `cyber-flower` duplicate-tree cleanup only after CI confirms the maintained root tree still builds/tests.
2. Re-run dependency audit on the maintained `cyber-flower/server` after recent COS dependency cleanup; record exact remaining high/critical packages before changing major versions.
3. Restore non-mutating ESLint configuration and then E2E with an explicit Mongo test service or isolated test module.
4. Verify the next post-fix `frontier-radar` scheduled ingest.
5. Create/verify a real `roundtable` GitHub Release, then remove the ZIP from source in a separate PR.
6. Continue portfolio cleanup only after P0/P1 work is green.

## Handoff checklist

Before ending a maintenance session:

- Update this file if priority/status changed.
- Append actions and verification evidence to `MAINTENANCE_LOG.md`.
- Keep unresolved external actions open as Issues.
- Do not merge a security/build PR with pending or failed CI unless the repository has no executable CI and that limitation is explicitly recorded.
