# Repository Maintenance Handoff

Last updated: 2026-08-07 22:45 CST (UTC+8)

This file is the current handoff for maintenance across the `zhangshujuan1314/*` repositories. It records only work that has been verified from repository state, pull requests, issues, or CI. Historical actions belong in `MAINTENANCE_LOG.md`.

## Operating rules

1. Security and data-loss risks before cosmetic cleanup.
2. Structural or destructive changes go through a branch + PR unless the change is metadata/documentation only.
3. Do not call a fix complete until there is repository/CI evidence when CI is available.
4. README claims are not test evidence.
5. Generated binaries/ZIPs belong in Releases or CI artifacts, not source history.
6. Secrets never belong in repository files, encrypted or otherwise, when the decryption key is also in the repository.
7. Keep Issues for unresolved work; close only when the actual external dependency is complete.
8. `MAINTENANCE_LOG.md` is append-only. If a previous status becomes obsolete, append a correction rather than rewriting history.
9. Temporary maintenance workflows must stay off `main` and be removed from their branch after evidence is collected.
10. When concurrent maintenance lands first, re-read `main`; close superseded PRs instead of overwriting newer work.

## Current priority queue

### P0 / P1 external actions

- **youdian-shouhuo** — repository-side secret cleanup is complete, but old JWT/API/MongoDB/SMTP/etc. credentials must still be revoked/rotated at their providers. Security Issue #1 must remain open until external rotation is verified.
- **books** — review redistribution rights for committed commercial-book PDFs. Do not delete files or rewrite Git history until redistribution authorization is known.

### P1 engineering

- **cyber-flower** — no critical npm audit findings remain. Current clean audit: full tree **26 vulnerabilities (3 low, 15 moderate, 8 high, 0 critical)**; production-only **13 (9 moderate, 4 high, 0 critical)**. Production high chains are `@nestjs/platform-express -> multer` and `@nestjs/swagger -> js-yaml/lodash`. Issue #2 is open. First try a non-breaking `npm audit fix` on an isolated branch; if runtime highs remain, test a coordinated Nest 10 -> 11 migration rather than `--force` on main.
- **frontier-radar** — workflow commit-step fix is merged, but still needs a scheduled run that starts after the fix for runtime verification. Ignore failures that started on the pre-fix commit.

### Reliability baseline already established

- **cyber-flower** — public JWT fallback removed; stale nested full-project copy removed; non-mutating ESLint restored; previous 12 warnings removed; CI now requires **zero warnings**; build, **6/6 unit tests**, **5/5 E2E tests**, and Docker build are verified green.
- **mybrain** — CI is established; clean runner verified **131 tests passed** at setup time.
- **quanttrader** — Argon2id password migration, production JWT-secret guard, Docker env corrections, and default-deny arbitrary strategy execution are merged and CI-verified. Custom Python execution must remain trusted-code-only until a real isolation boundary exists.

### Repository governance / presentation

- **cineweave-studio** — eight phase/status reports moved from repository root to `docs/archive/status-reports/` as unchanged historical snapshots.
- **roundtable** — **completed:** real GitHub Release `v1.0.0` exists; the existing Windows ZIP was uploaded as the Release asset, README now points to Releases, and the ZIP was removed from the source tree in merged PR #3.
- **ai-zhihang** — generated ZIP artifacts removed from source and ignored going forward.
- **nuanxingzhe-ai** — marked Legacy; maintained successor is `nuanxingzhe-ai-next`.
- **pxpipe** — clarify upstream/original-project attribution before using it as an original flagship project.
- **cc-cockpit** — replace README screenshot/GIF placeholders with real product evidence before promoting it as a flagship release.

## Active work

### cyber-flower

- Issue #2: reduce remaining runtime dependency audit debt.
- A branch-only dependency audit separated production from development findings and has been cleaned of its temporary workflow after evidence collection.
- Next safe experiment: run non-breaking `npm audit fix` on an isolated branch, then require zero-warning lint + build + unit + E2E + Docker + production re-audit before merge.

### frontier-radar

- Verify the first scheduled ingest started after the workflow fix. Record the exact run ID/conclusion in `MAINTENANCE_LOG.md`.

### external/manual

- `youdian-shouhuo`: rotate/revoke provider-side credentials.
- `books`: determine redistribution authorization before destructive cleanup.

## Recommended next actions

1. Apply and verify non-breaking npm audit remediation for `cyber-flower`; do not use `--force` on main.
2. Re-audit `cyber-flower` production dependencies and decide whether a coordinated Nest 11 upgrade is justified.
3. Verify the next post-fix `frontier-radar` scheduled ingest.
4. Resolve `youdian-shouhuo` provider-side credential rotation and then decide whether Git history rewriting is warranted.
5. Review `books` redistribution rights.
6. Resume portfolio/presentation cleanup only after these P0/P1 items are either resolved or explicitly accepted/documented.

## Handoff checklist

Before ending a maintenance session:

- Update this file if priority/status changed.
- Append actions and verification evidence to `MAINTENANCE_LOG.md`.
- Keep unresolved external actions open as Issues.
- Do not merge a security/build PR with pending or failed CI unless the repository has no executable CI and that limitation is explicitly recorded.
- Remove temporary maintenance workflows after their evidence has been collected.
