# Repository Maintenance Handoff

Last updated: 2026-08-07 23:24 CST (UTC+8)

This file is the current handoff for maintenance across the `zhangshujuan1314/*` repositories. It records only work verified from repository state, pull requests, issues, CI, or explicit external confirmation. Historical actions and failed experiments belong in `MAINTENANCE_LOG.md`.

## Operating rules

1. Security and data-loss risks before cosmetic cleanup.
2. Structural or destructive changes go through a branch + PR unless the change is metadata/documentation only.
3. Do not call a fix complete until there is repository/CI evidence when CI is available.
4. README claims are not test evidence.
5. Generated binaries/ZIPs belong in Releases or CI artifacts, not source history.
6. Secrets never belong in repository files, encrypted or otherwise, when the decryption key is also in the repository.
7. Keep Issues for unresolved work; close only when the actual dependency/action is complete.
8. `MAINTENANCE_LOG.md` is append-only. If a previous status becomes obsolete, append a correction instead of rewriting history.
9. Temporary maintenance workflows must stay off `main` and be removed after evidence collection.
10. When concurrent maintenance lands first, re-read `main`; close superseded PRs instead of overwriting newer work.

## Current priority queue

### P0 / P1 external actions

- **youdian-shouhuo** — repository-side secret cleanup is complete, but old JWT/API/MongoDB/SMTP/etc. credentials must still be revoked/rotated at their providers. Security Issue #1 must remain open until external rotation is verified.
- **books** — review redistribution rights for committed commercial-book PDFs. Do not delete files or rewrite Git history until redistribution authorization is known.

### Runtime verification

- **frontier-radar** — workflow commit-step fix is merged, but still needs the first scheduled run that *starts after the fix* for runtime verification. Ignore pre-fix scheduled failures.

### Publication / portfolio work

- **cc-cockpit** — engineering/install baseline is already CI-verified on Windows, including remote `npx github:...` startup and localhost-only behavior. Issue #1 remains open only for **real sanitized screenshots/GIF/video**; do not fabricate demo assets from mocks or private session data.
- **pxpipe** — attribution is now explicit in README: the repo is identified as an experimental derivative of `teamchong/pxpipe` (MIT), upstream remains the official project, and local experimental increments are enumerated. No further attribution rewrite is currently required.

## Verified engineering baselines

### cyber-flower — security/reliability baseline complete

- Public/default JWT fallback removed; production secret configuration fails closed.
- Stale nested full-project copy removed after full CI verification.
- Non-mutating TypeScript ESLint restored and tightened to **zero warnings**.
- Current CI requires production high/critical audit, build, **6/6 unit tests**, **5/5 E2E tests** with MongoDB, and Docker build.
- Coordinated Nest 10 -> 11 migration merged in PR #14 (`0ce4ae440e46e55f778227a75bbd5d2d77a86786`).
- Final migration candidate verified **0 npm vulnerabilities**, including production **0 high / 0 critical**.
- Permanent CI regression gate merged in PR #15 (`f362c11fc2115e1519a1ac605797f4c1fb4906cb`): `npm audit --omit=dev --audit-level=high` now blocks future production high/critical dependency regressions.
- Dependency-security Issue #2 is closed as completed.
- Remaining Node 20 warning concerns GitHub Action runtime/tooling versions, not the application production dependency graph; track separately if upgraded.

### mybrain

- GitHub pytest CI established.
- Clean runner verified **131 tests passed** at setup time after declaring `pytest-asyncio` explicitly.

### quanttrader

- Argon2id password migration with legacy salted-SHA256 login migration is merged and CI-verified.
- Production JWT secret fails closed; Docker `QT_*` configuration corrected.
- Arbitrary submitted Python strategy execution is default-denied; built-in templates remain enabled. Custom Python must remain trusted-code-only until a real isolation boundary exists.

### roundtable

- Real GitHub Release `v1.0.0` exists; Windows ZIP is a Release asset and no longer lives in the source tree.
- Normal CI is established on Python **3.10 and 3.12**; existing mocked suite verified **16 tests passed**.
- Temporary release-bootstrap workflow was removed after evidence collection.

## Repository governance completed

- **cineweave-studio** — eight phase/status reports moved from repository root to `docs/archive/status-reports/` as unchanged historical snapshots.
- **ai-zhihang** — generated ZIP artifacts removed from source and ignored going forward.
- **nuanxingzhe-ai** — marked Legacy; maintained successor is `nuanxingzhe-ai-next`.
- **landscape-scroll** — marked **Completed / Frozen showcase**; retained as a Canvas interaction/visual work rather than an active product.
- **life-timeline** — marked **Completed / Frozen**; retained as a single-file local-first interaction/information-visualization work.
- **shiguang-jiaonang** — marked **Completed concept prototype / Frozen** and explicitly documents that current AI organization is a front-end simulation, not a real LLM/backend capability.
- **profile repository** — focused profile README established so flagship work is not presented at equal weight with every experiment.

## Active work

1. **frontier-radar** — verify first post-fix scheduled ingest and record exact run ID/conclusion.
2. **youdian-shouhuo** — external provider-side credential rotation/revocation.
3. **books** — redistribution-rights decision before destructive cleanup.
4. **cc-cockpit** — capture real sanitized publication assets; Issue #1 contains the privacy checklist and verified runtime baseline.

## Recommended next actions

1. Check `frontier-radar` once a scheduled run has actually started after the workflow fix.
2. Complete `youdian-shouhuo` credential rotation; only then decide whether encrypted blobs should be purged from Git history.
3. Determine `books` redistribution authorization and either retain authorized materials or remove unauthorized PDFs/history.
4. Capture `cc-cockpit` screenshots/GIF from a real but sanitized local session; keep local paths, prompts, usernames, project names, tokens, and API keys out of assets.
5. After P0/P1 external work is resolved, continue lower-risk portfolio cleanup/archiving rather than opening new overlapping projects.

## Handoff checklist

Before ending a maintenance session:

- Update this file if priority/status changed.
- Append actions and verification evidence to `MAINTENANCE_LOG.md`.
- Keep unresolved external actions open as Issues.
- Do not merge security/build PRs with pending or failed CI unless the repository has no executable CI and that limitation is explicitly recorded.
- Remove temporary maintenance workflows after their evidence has been collected.
- Re-read default branches before writes when concurrent maintenance is active.
