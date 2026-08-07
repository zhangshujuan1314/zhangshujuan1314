# Repository Maintenance Log

Append-only operational log for maintenance across `zhangshujuan1314/*` repositories.

Format: `timestamp | repository | action | verification | status / next action`.

---

## 2026-08-07

- **22:12 CST | global** — Established `MAINTENANCE_HANDOFF.md` and this append-only log as the maintenance source of truth. **Status:** active.
- **quanttrader** — Replaced new password storage with Argon2id while retaining legacy salted SHA-256 login compatibility and migration. Added Backend CI and migration tests. **Verification:** final Backend CI succeeded. **Status:** merged.
- **quanttrader** — Removed production reliance on public/default JWT signing secret; corrected `QT_*` Docker environment names and removed backend reload mode. **Verification:** Backend CI succeeded. **Status:** merged.
- **quanttrader** — Default-denied arbitrary submitted Python strategy execution while leaving built-in templates available; explicit trusted-code opt-in remains possible. **Verification:** Backend CI run succeeded with guard tests. **Status:** merged; do not call this a Python sandbox.
- **mybrain** — Added GitHub pytest CI and explicit async-test dependency. Initial clean run exposed missing `pytest-asyncio`; after correction, clean runner reported **131 passed, 2 warnings**. README test count updated to verified total. **Status:** merged.
- **youdian-shouhuo** — Removed committed encrypted env files and hard-coded decrypt helper; documentation/ignore policy updated. **Status:** repository-side cleanup merged. **External follow-up:** rotate/revoke every credential that may have existed in those files; keep security issue open until done.
- **frontier-radar** — Fixed ingest workflow commit step that unconditionally added nonexistent `pipeline/cache/`. **Status:** merged; next scheduled run that starts after the fix is required for runtime verification.
- **cyber-flower** — Restored a non-empty Jest unit-test gate without `--passWithNoTests`. **Verification:** CI executed `src/app.controller.spec.ts`, **2/2 tests passed**; build and Docker build also succeeded. **Status:** merged.
- **cyber-flower** — Removed public `cyber-bloom-secret-key` JWT fallback, centralized secret validation, and made production Docker Compose require a strong JWT secret. **Verification:** PR CI succeeded before merge. **Status:** merged.
- **cyber-flower** — Dependency audit during CI reported **37 vulnerabilities (3 low, 21 moderate, 10 high, 3 critical)** at that point. Subsequent repository activity began removing the unused COS SDK critical dependency chain. **Status:** re-audit required before quoting a current count.
- **cyber-flower** — Identified a stale nested full-project copy under `cyber-flower/`, including stale security code. Opened PR #6 to remove the duplicate tree while preserving history. Branch was refreshed onto the latest observed maintenance main before continuing validation. **Status:** open; merge only after CI.
- **cineweave-studio** — Moved eight phase/status reports from repository root into `docs/archive/status-reports/` without changing their blob contents; added archive explanation. **Status:** merged; cleanup issue completed.
- **ai-zhihang** — Removed generated deployment ZIP artifacts from source and added ZIP ignore rule. **Status:** merged.
- **nuanxingzhe-ai** — Marked the old static version Legacy and pointed maintenance to `nuanxingzhe-ai-next`. **Status:** completed; repository Archive toggle remains a UI/admin action if desired.
- **roundtable** — Verified GitHub Releases list was empty while `Roundtable-v1.0.0-Windows.zip` remained in source. **Status:** do not remove ZIP until a real Release exists.
- **books** — Identified redistribution/licensing risk for committed commercial-book PDFs. Repository Issues are disabled. **Status:** no destructive action taken; rights review required first.
- **global profile** — Added a focused GitHub Profile README to surface flagship work instead of presenting all repositories at equal weight. **Status:** completed.

### Later corrections and second-round work

- **22:20-22:30 CST | cyber-flower** — **Correction to the earlier duplicate-tree entry:** PR #6 completed full CI and was merged. **Verification:** maintained root tree passed build, **6/6 unit tests**, **5/5 E2E tests** with MongoDB, and Docker build. **Status:** stale nested `cyber-flower/` full-project copy removed from main.
- **22:25 CST | cyber-flower** — Concurrent maintenance landed the non-mutating TypeScript ESLint toolchain on `main` first. An independently prepared PR #11 was closed unmerged as superseded rather than downgrading/duplicating the newer implementation. **Verification:** landed main CI succeeded. **Status:** concurrent-write conflict handled without overwriting newer work.
- **22:40-22:44 CST | cyber-flower** — Removed all **12 existing lint warnings** with minimal dead-code/unused-binding cleanup and tightened CI from `--max-warnings=20` to **`--max-warnings=0`**. **Verification:** PR #13 CI run #25 passed zero-warning lint, build, unit, E2E, and Docker. **Status:** PR #13 merged as commit `38ef9c2ca4404ddf877591242e51518a394a347a`.
- **22:41-22:44 CST | cyber-flower** — Ran a temporary branch-only npm audit workflow and removed that workflow after evidence collection. **Verification:** full tree **26 vulnerabilities: 3 low, 15 moderate, 8 high, 0 critical**; production-only tree **13: 9 moderate, 4 high, 0 critical**. Production highs are concentrated in `@nestjs/platform-express -> multer` and `@nestjs/swagger -> js-yaml/lodash`; development-only highs are in the Nest CLI toolchain. **Status:** Issue #2 reopened and updated; next step is non-breaking `npm audit fix`, then coordinated major upgrade only if required.
- **22:26 CST | roundtable** — Created real GitHub Release `v1.0.0` from the existing source-tree Windows package. **Verification:** release workflow succeeded; Release asset `Roundtable-v1.0.0-Windows.zip` published at **18,104 bytes**, preserving the existing package content. **Status:** release published.
- **22:28 CST | roundtable** — Updated README to use the Release download, removed `Roundtable-v1.0.0-Windows.zip` from source, and relied on existing ignore rules to prevent reintroduction. **Verification:** PR #3 reviewed as README change + binary deletion only and merged. **Status:** binary migration complete.
- **22:45 CST | global** — Refreshed `MAINTENANCE_HANDOFF.md` to reflect verified current state and narrowed active work to unresolved P0/P1 items. **Status:** handoff current as of this entry.

---

## Logging policy

- Never rewrite prior log entries to make outcomes look cleaner.
- If a prior statement becomes false, append a correction with evidence.
- Record CI/test evidence separately from README claims.
- Record destructive actions (deletions, history rewrites, secret rotation) explicitly.
- Do not place credentials, private tokens, decrypted secrets, or sensitive values in this log.
