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

---

## Logging policy

- Never rewrite prior log entries to make outcomes look cleaner.
- If a prior statement becomes false, append a correction with evidence.
- Record CI/test evidence separately from README claims.
- Record destructive actions (deletions, history rewrites, secret rotation) explicitly.
- Do not place credentials, private tokens, decrypted secrets, or sensitive values in this log.
