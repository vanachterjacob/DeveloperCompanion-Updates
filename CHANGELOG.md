# Changelog

All notable changes to DeveloperCompanion will be documented in this file.

This changelog is generated from git tags and commit ranges, with per-commit scope and diff stats.

## [Unreleased]

## [0.2.6] - 2026-03-03

### Features

- feat(synergy): add archive retry — edit and re-push synced entries from the archive view, with failed entry badge and retry button in form view
- feat(devops): stream live CLI output during builds — Claude and Kimi engines now use `stream-json` output format for real-time progress (tool calls, file reads/writes, thinking phases) instead of showing "Initializing" until completion
- feat(devops): add build retention & purge — configurable retention period (1-365 days, default 30) in DevOps settings, "Purge old builds" and "Purge failed builds" buttons in the Build Dashboard, and a recency filter (All / 1D / 7D / 30D) for the build queue

### Improvements

- refactor(settings): move Activities and About into dedicated settings tabs — remove standalone modals/buttons from header, add separator + new sidebar items at bottom, update CommandPalette and guided tour references
- chore(cli): refresh static model lists for all CLI engines — add latest Cursor models (gpt-5.3-codex, composer-1.5, kimi-k2.5, etc.), remove defunct models (o4-mini, o3, gemini-2.0-flash), add `kimi` prefix validation
- test(cli): add `verify-cli-models.sh` smoke-test script for validating CLI engine + model combinations
- ux(stats): simplify StatsHeaderBar layout — remove retro uptime/corp tag, fix narrow-column layout using column-first flex instead of viewport-based breakpoints
- ux(devops): include work item title in saved plan filename for easier identification
- ux(devops): auto-calculate start time as (now − duration) when filling in duration in the Log Time dialog
- ux(devops): rename "AI Plan" tab to "AI Assist" with clearer descriptions — buttons now say "Generate AC & Subtasks" and "Review AC Quality" with helper text and tooltips explaining what each action does and which LLM is used
- ux(devops): extract "Save Plan" as standalone button in modal header — no longer buried inside the AI Assist tab; accessible from any tab with collapsible folder config

### Fixes

- fix(synergy): process API push entries sequentially to prevent duplicate/missing entries caused by concurrent Synergy API race conditions
- fix(cli): use stdin for cursor engine prompt — prevents Windows OS error 206 when work item prompts with images and description exceed the 32K command-line limit
- fix(cli): add `cursor agent` subcommand and SDK fallback to build_orchestrator and ai_review — resolves "cursor-agent not found" on systems where only `cursor agent` subcommand exists (Cursor 2.5+)
- fix(cli): limit Cursor CLI model list to Claude-only models — `cursor agent` uses Claude Agent SDK so non-Claude models (GPT, Gemini, Grok, etc.) return 404
- fix(devops): apply state filter client-side so the state dropdown always shows all available states instead of disappearing after selection
- fix(synergy): prevent false-positive customer matching in fuzzy lookup — no longer returns first partial LIKE/FTS result when no strict boundary match exists
- fix(devops): populate `startedAt` from build progress event so elapsed timer and progress bar work during active builds
- fix(cli): add `--verbose` flag for Claude/Kimi `stream-json` output — required by latest Claude CLI when combined with `--print`
- fix(activities): capture event values before state updater to prevent `currentTarget` null error when adding/editing activities
- fix(devops): prune stale work items after sync — items no longer matching the WIQL query (e.g. reassigned) are removed from local DB, preserving items referenced by worklogs or todos
- fix(cli): use bare command names as fallback so Windows resolves .exe/.cmd/.bat via PATHEXT — fixes "program not found" for CLI engines installed as native binaries instead of npm shims
- fix(synergy): use GET with query params for token endpoint
- fix(day): auto-close stale previous day instead of blocking new day start
- fix(wizard): run scrapers sequentially to prevent "another scraper running" error
- fix(tour): suppress chapter tips after user skips guided tour

## [0.2.5] - 2026-03-01

### Release Scope

- Commit range: v0.2.4..v0.2.5
- Commits in release: 1

### Fixes

- fix(test): harden remaining Playwright CI flakes (4e6f6a6) - 3 files changed, 89 insertions(+), 15 deletions(-); areas: tests; top files: tests/e2e/fixtures/pageUtils.ts, tests/e2e/news-summaries.spec.ts, tests/e2e/news.spec.ts.

## [0.2.4] - 2026-03-01

### Release Scope

- Commit range: v0.2.3..v0.2.4
- Commits in release: 2

### Fixes

- fix(ci): reduce Playwright stability contention (d7efd65) - 3 files changed, 30 insertions(+), 27 deletions(-); areas: package.json, tests; top files: package.json, tests/e2e/a11y.spec.ts, tests/e2e/fixtures/pageUtils.ts.

### Build & Release

- release: v0.2.4 (d97f4dd) - 15 files changed, 37 insertions(+), 22 deletions(-); areas: CHANGELOG.md, docs, package-lock.json, package.json; top files: CHANGELOG.md, docs/prompts/README.md, docs/prompts/_template.md.

## [0.2.3] - 2026-03-01

### Release Scope

- Commit range: v0.2.2..v0.2.3
- Commits in release: 2

### Fixes

- fix(test): harden settings and feed modal navigation (c5f2df0) - 2 files changed, 64 insertions(+), 27 deletions(-); areas: tests; top files: tests/e2e/fixtures/pageUtils.ts, tests/e2e/news.spec.ts.

### Build & Release

- release: v0.2.3 (a34de97) - 15 files changed, 37 insertions(+), 22 deletions(-); areas: CHANGELOG.md, docs, package-lock.json, package.json; top files: CHANGELOG.md, docs/prompts/README.md, docs/prompts/_template.md.

## [0.2.2] - 2026-03-01

### Release Scope

- Commit range: v0.2.1..v0.2.2
- Commits in release: 2

### Fixes

- fix(test): stabilize remaining Playwright CI flakes (26be074) - 5 files changed, 238 insertions(+), 139 deletions(-); areas: tests; top files: tests/e2e/background-tasks.spec.ts, tests/e2e/command-palette.spec.ts, tests/e2e/news-summaries.spec.ts.

### Build & Release

- release: v0.2.2 (df4fb53) - 15 files changed, 743 insertions(+), 722 deletions(-); areas: CHANGELOG.md, docs, package-lock.json, package.json; top files: CHANGELOG.md, docs/prompts/README.md, docs/prompts/_template.md.

## [0.2.1] - 2026-03-01

### Release Scope

- Commit range: v0.2.0..v0.2.1
- Commits in release: 2

### Fixes

- fix(ci): stabilize Playwright release gate (b39975c) - 4 files changed, 20 insertions(+), 15 deletions(-); areas: .github, package.json, tests; top files: .github/workflows/release.yml, package.json, tests/e2e/fixtures/pageUtils.ts.

### Build & Release

- release: v0.2.1 (f89567a) - 15 files changed, 352 insertions(+), 42 deletions(-); areas: CHANGELOG.md, docs, package-lock.json, package.json; top files: CHANGELOG.md, docs/prompts/README.md, docs/prompts/_template.md.

## [0.2.0] - 2026-03-01

### Release Scope

- Commit range: v0.1.23..v0.2.0
- Commits in release: 160

### Features

- feat(05-03): add CI stability job and eslint-plugin-playwright (a922623) - 4 files changed, 52 insertions(+); areas: .github, eslint.config.js, package-lock.json, package.json; top files: .github/workflows/release.yml, eslint.config.js, package.json.
- feat(05-01): add afterEach cleanup to all 17 E2E specs and replace waitForTimeout (0c78eae) - 17 files changed, 264 insertions(+), 7 deletions(-); areas: tests; top files: tests/e2e/a11y.spec.ts, tests/e2e/background-tasks.spec.ts, tests/e2e/command-palette.spec.ts.
- feat(04-01): slim SettingsButton.tsx orchestrator with React.lazy and startTransition (9434ebe) - 1 file changed, 180 insertions(+), 3023 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- feat(04-01): extract 10 settings tab components into settings subdirectory (0098d0e) - 11 files changed, 3125 insertions(+); areas: src/components; top files: src/components/modals/settings/AppearanceSettingsTab.tsx, src/components/modals/settings/AutomationSettingsTab.tsx, src/components/modals/settings/DevOpsSettingsTab.tsx.
- feat(04-02): replace useDeferredValue with 300ms debounce and 50-result cap (8c90f8c) - 1 file changed, 49 insertions(+), 14 deletions(-); areas: src/features; top files: src/features/devops/components/WorkItemsPanel.tsx.
- feat(04-02): memoize WorkLogCalendarBlock and stabilize parent callbacks (eb9e04f) - 2 files changed, 22 insertions(+), 14 deletions(-); areas: src/features; top files: src/features/worklog/components/WorkLogCalendar.tsx, src/features/worklog/components/WorkLogCalendarBlock.tsx.
- feat(03-04): add AC quality review scorecard with per-AC annotations (b82dac9) - 2 files changed, 247 insertions(+); areas: src/features; top files: src/features/devops/components/AcReviewScorecard.tsx, src/features/devops/components/ElaborationTab.tsx.
- feat(03-03): replace write-back buttons with clipboard copy (a805351) - 3 files changed, 126 insertions(+), 149 deletions(-); areas: src/features; top files: src/features/devops/components/ElaborationResults.tsx, src/features/devops/components/ElaborationTab.tsx, src/features/devops/components/SubtaskChecklist.tsx.
- feat: improve DevOps Work Items onboarding UX (4237782) - 2 files changed, 177 insertions(+), 30 deletions(-); areas: CHANGELOG.md, src/features; top files: CHANGELOG.md, src/features/devops/components/WorkItemsPanel.tsx.
- feat(03-03): add AI tab to WorkItemDetailModal (36bebbd) - 1 file changed, 26 insertions(+), 3 deletions(-); areas: src/features; top files: src/features/devops/components/WorkItemDetailModal.tsx.
- feat(03-03): wire elaboration store to LLM calls and create AI tab UI components (a9b90ac) - 4 files changed, 515 insertions(+), 22 deletions(-); areas: src/features, src/stores; top files: src/features/devops/components/ElaborationResults.tsx, src/features/devops/components/ElaborationTab.tsx, src/features/devops/components/SubtaskChecklist.tsx.
- feat(03-01): create elaboration Zustand store (17380f0) - 1 file changed, 406 insertions(+); areas: src/stores; top files: src/stores/elaborationStore.ts.
- feat(03-02): add elaboration prompt builders with TDD tests (ede6987) - 2 files changed, 409 insertions(+); areas: src/features; top files: src/features/devops/services/__tests__/elaborationPrompts.test.ts, src/features/devops/services/elaborationPrompts.ts.
- feat(03-01): add Rust Tauri commands for DevOps write-back (0fc83e5) - 2 files changed, 149 insertions(+); areas: src-tauri/src; top files: src-tauri/src/devops_api.rs, src-tauri/src/lib.rs.
- feat(03-02): add elaboration parser with TDD tests (3c28fbe) - 2 files changed, 400 insertions(+); areas: src/features; top files: src/features/devops/services/__tests__/elaborationParser.test.ts, src/features/devops/services/elaborationParser.ts.
- feat(03-01): create elaboration type definitions (6065407) - 1 file changed, 45 insertions(+); areas: src/types; top files: src/types/elaboration.ts.
- feat(02-03): add AI Provider section to LLM tab in SettingsButton (ff07ba5) - 1 file changed, 444 insertions(+), 288 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- feat(02-01): branch llmService.ts on llmMode for API vs CLI dispatch (5ba116a) - 1 file changed, 25 insertions(+); areas: src/services; top files: src/services/llm/llmService.ts.
- feat(02-01): add LlmMode/LlmApiProvider types and llm fields to settingsStore (f13ba7e) - 4 files changed, 173 insertions(+), 7 deletions(-); areas: .planning, src/stores; top files: .planning/ROADMAP.md, .planning/STATE.md, .planning/phases/02-llm-provider-infrastructure/02-02-SUMMARY.md.
- feat(02-02): register invoke_llm_api in lib.rs invoke_handler (2da21e2) - 1 file changed, 1 insertion(+); areas: src-tauri/src; top files: src-tauri/src/lib.rs.
- feat(02-04): add Zod schema validation to parseTableSuggestions (a6329aa) - 3 files changed, 44 insertions(+), 23 deletions(-); areas: package-lock.json, package.json, src/features; top files: package.json, src/features/worklog/services/bulkImport/cliService.ts.
- feat(02-02): implement invoke_llm_api in commands/ai.rs (223fbb9) - 1 file changed, 132 insertions(+); areas: src-tauri/src; top files: src-tauri/src/commands/ai.rs.
- feat(DiffViewer, ReviewPanel): implement build history filtering and pagination controls (41e92aa) - 5 files changed, 351 insertions(+), 31 deletions(-); areas: src/features; top files: src/features/devops/components/BuildHistoryControls.tsx, src/features/devops/components/DiffViewer.tsx, src/features/devops/components/ReviewPanel.tsx.
- feat(01-01): bind day buttons to mutationInFlight in DayWidget (c14d448) - 2 files changed, 280 insertions(+), 180 deletions(-); areas: src/components; top files: src/components/app/WidgetRegistry.tsx, src/components/common/DayWidget.tsx.
- feat(01-01): promote dayMutationInFlight to reactive Zustand state (cb521a7) - 1 file changed, 19 insertions(+), 19 deletions(-); areas: src/stores; top files: src/stores/dayStore.ts.
- feat(01-04): add loading spinner and friendly error/retry UI to SynergyWorkflowPanel (99cb8a9) - 1 file changed, 22 insertions(+), 4 deletions(-); areas: src/features; top files: src/features/synergy/components/SynergyWorkflowPanel.tsx.
- feat(01-04): add auto-retry-once and friendly errors to fetchRss (1e2d98f) - 2 files changed, 31 insertions(+), 10 deletions(-); areas: src/features, src/stores; top files: src/features/worklog/components/BulkImportView.tsx, src/stores/useSynergyStore.ts.
- feat(01-03): rework BackupRestorePanel with file pickers, styled modal, English UI (04095d8) - 1 file changed, 110 insertions(+), 70 deletions(-); areas: src/components; top files: src/components/panels/BackupRestorePanel.tsx.
- feat(01-02): update workLogStore — soft-delete undo and filtered load (eb41450) - 1 file changed, 7 insertions(+), 3 deletions(-); areas: src/stores; top files: src/stores/workLogStore.ts.
- feat(01-03): add export_backup_to_path and prepare_restore_from_path Rust commands (9beef99) - 2 files changed, 46 insertions(+); areas: src-tauri/src; top files: src-tauri/src/db/backup.rs, src-tauri/src/lib.rs.
- feat(01-02): add migration 050 — is_deleted soft-delete column (d11e7db) - 2 files changed, 10 insertions(+); areas: migrations, src-tauri/src; top files: migrations/050_worklog_soft_delete.sql, src-tauri/src/db/migrations.rs.
- feat: add Playwright test report. (1ecfc9c) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: playwright-report; top files: playwright-report/index.html.
- feat(a11y): integrate accessibility reviewer prompt and fix high priority issues (39af9b9) - 6 files changed, 130 insertions(+), 1 deletion(-); areas: docs, src/components, src/features; top files: docs/prompts/README.md, docs/prompts/accessibility-reviewer-prompt.md, docs/prompts/runs/2026-02-28-accessibility-reviewer.md.
- feat: Implement codex CLI path resolution for Windows (e094e8f) - 14 files changed, 925 insertions(+), 19 deletions(-); areas: .claude, src-tauri/src; top files: .claude/skills/debug/SKILL.md, .claude/skills/docs/SKILL.md, .claude/skills/feature/SKILL.md.
- feat: Add preparation step for Tauri externalBin stub in Linux CI (40d7912) - 1 file changed, 6 insertions(+); areas: .github; top files: .github/workflows/ci.yml.
- feat: Add various generated test, lint, and type-check report and log files. (61d8297) - 22 files changed, 205 insertions(+), 5 deletions(-); areas: err.txt, errs.txt, fail_log.json, fail_log2.json; top files: err.txt, errs.txt, fail_log.json.
- feat: Add GitHub Actions workflow for automated releases and documentation for release versioning. (acc24fd) - 6 files changed, 20 insertions(+), 551 deletions(-); areas: .github, docs; top files: .github/workflows/release.yml, docs/release-versioning.md.
- feat: Add Playwright CI strategy and extract Tauri Mocks #40 (e85b277) - 13 files changed, 1307 insertions(+), 237 deletions(-); areas: .github, tests; top files: .github/workflows/ci.yml, tests/e2e/core.spec.ts, tests/e2e/fixtures/tauriMock.ts.

### Fixes

- fix(05-02): audit and remove force:true from remaining 9 spec files (167b03e) - 9 files changed, 31 insertions(+), 34 deletions(-); areas: tests; top files: tests/e2e/background-tasks.spec.ts, tests/e2e/day.spec.ts, tests/e2e/devops-batch-timelog.spec.ts.
- fix(05-02): audit and remove force:true from pageUtils and high-count spec files (ee05245) - 5 files changed, 59 insertions(+), 59 deletions(-); areas: tests; top files: tests/e2e/core.spec.ts, tests/e2e/fixtures/pageUtils.ts, tests/e2e/news-summaries.spec.ts.
- fix(03-03): add --output-format text to Claude CLI invocation (88d6e52) - 1 file changed, 2 insertions(+); areas: src-tauri/src; top files: src-tauri/src/commands/ai.rs.
- fix(03-03): add dedicated elaboration LLM settings and improve parser robustness (ea20d55) - 5 files changed, 246 insertions(+), 11 deletions(-); areas: src/components, src/features, src/services, src/stores; top files: src/components/modals/SettingsButton.tsx, src/features/devops/services/elaborationParser.ts, src/services/llm/llmService.ts.
- fix(02-03): fix active button colors in retro theme (489ad0a) - 2 files changed, 14 insertions(+), 3 deletions(-); areas: src/components, src/styles; top files: src/components/modals/SettingsButton.tsx, src/styles/themes/retro.css.
- fix(01): revise 01-02 plan — add undo button task and migration header comment (b94a144) - 1 file changed, 81 insertions(+), 10 deletions(-); areas: .planning; top files: .planning/phases/01-core-stabilization/01-02-PLAN.md.
- fix: resolve typecheck errors and reopen race condition (7bba81e) - 4 files changed, 183 insertions(+), 12 deletions(-); areas: docs, src/stores, src/utils; top files: docs/prompts/README.md, src/stores/dayStore.ts, src/utils/duration.ts.
- Fix-onboarding-retry-test-and-update-changelog (253966c) - 2 files changed, 29 insertions(+), 1 deletion(-); areas: CHANGELOG.md, tests; top files: CHANGELOG.md, tests/e2e/onboarding.spec.ts.
- fix(perf): profile and optimize bootstrap and devops flows (cd45ebf) - 17 files changed, 1462 insertions(+), 229 deletions(-); areas: .github, CHANGELOG.md, docs, src/App.tsx; top files: .github/workflows/ci.yml, .github/workflows/release.yml, CHANGELOG.md.
- fix(data-integrity): harden db restore and devops sync writes (3d99890) - 9 files changed, 1103 insertions(+), 226 deletions(-); areas: CHANGELOG.md, src-tauri/src, src/services, src/stores; top files: CHANGELOG.md, src-tauri/src/commands/devops.rs, src-tauri/src/commands/mod.rs.
- Fix cross-platform traversal detection in ai command tests (84519fc) - 1 file changed, 5 insertions(+); areas: src-tauri/src; top files: src-tauri/src/commands/ai.rs.
- fix(security): harden local file and URL boundaries (a1225fb) - 11 files changed, 1118 insertions(+), 30 deletions(-); areas: CHANGELOG.md, package-lock.json, package.json, src-tauri/src; top files: CHANGELOG.md, package.json, src-tauri/src/commands/ai.rs.
- fix(ui): translate special blocks panel to English (48ddb78) - 2 files changed, 12 insertions(+), 13 deletions(-); areas: CHANGELOG.md, src/components; top files: CHANGELOG.md, src/components/panels/SpecialBlocksPanel.tsx.
- Fix QA sync/timer regressions and add smoke tests (d28486c) - 12 files changed, 629 insertions(+), 82 deletions(-); areas: src/components, src/services, src/stores, tests; top files: src/components/worklog/WorkLogPanel.tsx, src/services/synergy/autoSync.test.ts, src/services/synergy/autoSync.ts.
- fix: Allow unused mutable variable in build_cli_command function (301a330) - 1 file changed, 2 insertions(+); areas: src-tauri/src; top files: src-tauri/src/ai_review.rs.
- fix: Update variable names for clarity and improve logging for missing weather data (53553cc) - 4 files changed, 86 insertions(+), 43 deletions(-); areas: src-tauri/src, src/components, src/services; top files: src-tauri/src/lib.rs, src-tauri/src/youtube_music.rs, src/components/worklog/WorkLogCalendar.tsx.
- fix: Add platform-specific stubs for cursor resolution functions on non-Windows OS (5b31041) - 3 files changed, 40 insertions(+), 2 deletions(-); areas: src-tauri/src; top files: src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs, src-tauri/src/lib.rs.
- fix: wrap unstable inline functions in useCallback/useMemo to clear React hook lint warnings (5fcaa2f) - 3 files changed, 24 insertions(+), 30 deletions(-); areas: src/components; top files: src/components/onboarding/GuidedTourOverlay.tsx, src/components/panels/TodoPanel.tsx, src/components/worklog/WorkLogCalendarBlock.tsx.
- fix: exclude tests/e2e from vitest collection to prevent Playwright spec conflicts (dd88460) - 1 file changed, 12 insertions(+), 4 deletions(-); areas: vite.config.ts; top files: vite.config.ts.
- fix: resolve Playwright dual-version conflict and useMemo hook lint warnings (4557322) - 5 files changed, 48 insertions(+), 21 deletions(-); areas: .github, src/components; top files: .github/workflows/ci.yml, src/components/devops/BuildDashboard.tsx, src/components/devops/DiffViewer.tsx.
- fix: resolve 10 npm audit vulnerabilities via minimatch override (dc67d6d) - 4 files changed, 45 insertions(+), 61 deletions(-); areas: eslint.config.js, package-lock.json, package.json, src/components; top files: eslint.config.js, package.json, src/components/common/Animations.tsx.
- fix: resolve CI failures - remove duplicate playwright package and split Animations.tsx (fd43d0e) - 4 files changed, 109 insertions(+), 92 deletions(-); areas: package.json, src/components; top files: package.json, src/components/common/Animations.tsx, src/components/common/animationVariants.ts.
- fix(automation): Resolve integrity and concurrency bugs identified in QA (ce29a17) - 7 files changed, 152 insertions(+), 80 deletions(-); areas: docs, src/services, src/stores; top files: docs/QA_REPORT.md, src/services/synergy/autoSync.ts, src/stores/activityStore.ts.

### Tests

- test(02): complete UAT - 8 passed, 0 issues (bad7f1e) - 1 file changed, 58 insertions(+); areas: .planning; top files: .planning/phases/02-llm-provider-infrastructure/02-UAT.md.
- test: expand phase 3 coverage and tune devops search (f1391ae) - 11 files changed, 557 insertions(+), 21 deletions(-); areas: CHANGELOG.md, src/features, src/stores, tests; top files: CHANGELOG.md, src/features/devops/components/WorkItemsPanel.tsx, src/stores/dayStore.test.ts.
- test(e2e): stabilize day ci flow and quarantine pause hang (1d14a60) - 3 files changed, 48 insertions(+), 26 deletions(-); areas: CHANGELOG.md, tests; top files: CHANGELOG.md, tests/e2e/day.spec.ts, tests/e2e/fixtures/pageUtils.ts.
- test(e2e): expand mock coverage and failure paths (5fa5025) - 16 files changed, 2686 insertions(+), 89 deletions(-); areas: CHANGELOG.md, tests; top files: CHANGELOG.md, tests/e2e/background-tasks.spec.ts, tests/e2e/command-palette.spec.ts.
- test(devops): update commit tracking expectations for atomic sync writes (352c941) - 1 file changed, 30 insertions(+), 5 deletions(-); areas: src/stores; top files: src/stores/__tests__/devopsStore.commitTracking.test.ts.
- test: Fix remaining flake in E2E tests for a11y tab navigation and worklog time input (d4db294) - 3 files changed, 35 insertions(+), 10 deletions(-); areas: tests; top files: tests/e2e/a11y.spec.ts, tests/e2e/fixtures/tauriMock.ts, tests/e2e/worklog.spec.ts.
- test: stabilize e2e start-day setup and tauri sql mock (50b4f9d) - 3 files changed, 29 insertions(+), 28 deletions(-); areas: tests; top files: tests/e2e/core.spec.ts, tests/e2e/fixtures/pageUtils.ts, tests/e2e/fixtures/tauriMock.ts.
- test: Implement E2E specs for Settings, Day Management, and Synergy (Phase 2-4) (2f4919b) - 17 files changed, 4963 insertions(+), 56 deletions(-); areas: tests; top files: tests/e2e/a11y.spec.ts, tests/e2e/core.spec.ts, tests/e2e/day.spec.ts.
- test: Implement Work Log CRUD and E2E Utilities (9317cd4) - 10 files changed, 137 insertions(+), 771 deletions(-); areas: docs, tests; top files: docs/E2E_TESTING_GUIDE.md, tests/e2e/fixtures/pageUtils.ts, tests/e2e/worklog.spec.ts.
- test: Fix Tauri mocking and E2E Playwright stability - Strengthened Tauri IPC mock in core.spec.ts to bypass required tauri checks - Mocked SQL metadata (PRAGMA, _sqlx_migrations) so database migration scripts don't hang - Disabled Setup Wizard and Guided Tour via mock DB entries and local storage injection - Accelerated tests by mocking the Synergy Artifact fetching phase and skipping network lookups - Fixed a duplicate main element ID (main-content) in App.tsx for more reliable Playwright locators (c99b835) - 6 files changed, 511 insertions(+), 9 deletions(-); areas: .gitignore, package-lock.json, package.json, playwright.config.ts; top files: .gitignore, package.json, playwright.config.ts.

### Refactoring

- refactor(03-03): extract shared CLI output cleaning to cleanCliOutput utility (4cc5b10) - 4 files changed, 66 insertions(+), 17 deletions(-); areas: src/features, src/services; top files: src/features/devops/services/__tests__/elaborationParser.test.ts, src/features/devops/services/elaborationParser.ts, src/features/worklog/services/bulkImport/cliService.ts.
- refactor: clean up code formatting and improve readability in background_tasks, discovery, ai, and backup modules (6215c37) - 4 files changed, 165 insertions(+), 102 deletions(-); areas: src-tauri/src; top files: src-tauri/src/background_tasks.rs, src-tauri/src/cli/discovery.rs, src-tauri/src/commands/ai.rs.
- refactor(WorkLogCalendar): remove open hours calculation and related logic (c3a5074) - 1 file changed, 2 insertions(+), 20 deletions(-); areas: src/features; top files: src/features/worklog/components/WorkLogCalendar.tsx.
- Refactor Codex CLI path resolution on Windows and enhance error handling in Setup Wizard (6ac0eae) - 5 files changed, 79 insertions(+), 22 deletions(-); areas: src-tauri/src, src/components, tests; top files: src-tauri/src/cli/discovery.rs, src/components/modals/SetupWizardModal.tsx, tests/e2e/news-summaries.spec.ts.
- Refactor code structure and remove redundant code blocks for improved readability and maintainability (dcde626) - 71 files changed, 1929 insertions(+), 207 deletions(-); areas: src/App.tsx, src/components, src/features, src/stores; top files: src/App.tsx, src/components/app/DashboardGrid.tsx, src/components/app/GlobalModals.tsx.
- refactor: remove synergyWorkflowStore and add tests for useSynergyStore (f469c76) - 100 files changed, 1631 deletions(-); areas: src/components, src/features, src/hooks, src/services; top files: src/components/automation/SynergyLoginModal.tsx, src/components/devops/BatchTimeLogDialog.tsx, src/components/devops/BuildAnalyticsPanel.tsx.
- refactor: modularize CSS and implement theme variables (Phase 3) (1a220bc) - 5 files changed, 595 insertions(+), 911 deletions(-); areas: src/index.css, src/styles; top files: src/index.css, src/styles/base.css, src/styles/layout.css.
- refactor: modularize frontend and backend (Phase 1 & 2) (d7d702c) - 28 files changed, 4176 insertions(+), 4743 deletions(-); areas: src-tauri/Cargo.toml, src-tauri/src, src/App.tsx, src/components; top files: src-tauri/Cargo.toml, src-tauri/src/ai_review.rs, src-tauri/src/cli/discovery.rs.

### Documentation

- docs(phase-05): complete phase execution and verification (3a9389c) - 2 files changed, 101 insertions(+); areas: .planning; top files: .planning/STATE.md, .planning/phases/05-e2e-test-stabilization/05-VERIFICATION.md.
- docs(05-02): complete force:true click audit plan (34466b8) - 2 files changed, 144 insertions(+), 10 deletions(-); areas: .planning; top files: .planning/STATE.md, .planning/phases/05-e2e-test-stabilization/05-02-SUMMARY.md.
- docs(05-03): complete CI stability job + ESLint playwright plugin plan (9cd52fb) - 2 files changed, 119 insertions(+), 6 deletions(-); areas: .planning; top files: .planning/STATE.md, .planning/phases/05-e2e-test-stabilization/05-03-SUMMARY.md.
- docs(05-03): update test skill with stabilized E2E patterns (422a150) - 1 file changed, 15 insertions(+), 2 deletions(-); areas: .claude; top files: .claude/skills/test/SKILL.md.
- docs(05-01): complete afterEach cleanup and waitForTimeout removal plan (a23d85d) - 3 files changed, 135 insertions(+), 10 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/STATE.md, .planning/phases/05-e2e-test-stabilization/05-01-SUMMARY.md.
- docs(05): create phase plan (20df67f) - 4 files changed, 562 insertions(+), 2 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/phases/05-e2e-test-stabilization/05-01-PLAN.md, .planning/phases/05-e2e-test-stabilization/05-02-PLAN.md.
- docs(05): research phase domain (fdf6d0f) - 1 file changed, 335 insertions(+); areas: .planning; top files: .planning/phases/05-e2e-test-stabilization/05-RESEARCH.md.
- docs(05): capture phase context (861a937) - 1 file changed, 96 insertions(+); areas: .planning; top files: .planning/phases/05-e2e-test-stabilization/05-CONTEXT.md.
- docs(phase-04): fix STATE.md — remove stale frontmatter, mark phase 4 complete (1ba365d) - 1 file changed, 12 insertions(+), 25 deletions(-); areas: .planning; top files: .planning/STATE.md.
- docs(phase-04): complete phase execution and verification (d2cd601) - 2 files changed, 188 insertions(+); areas: .planning; top files: .planning/STATE.md, .planning/phases/04-performance-and-refactoring/04-VERIFICATION.md.
- docs(04-01): complete settings panel code splitting plan (ddb7f72) - 3 files changed, 144 insertions(+), 6 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/STATE.md, .planning/phases/04-performance-and-refactoring/04-01-SUMMARY.md.
- docs(04-02): complete calendar memo and search debounce plan (9fde82c) - 4 files changed, 155 insertions(+), 13 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/ROADMAP.md, .planning/STATE.md.
- docs(04-performance-and-refactoring): create phase plan (2101c03) - 3 files changed, 592 insertions(+), 2 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/phases/04-performance-and-refactoring/04-01-PLAN.md, .planning/phases/04-performance-and-refactoring/04-02-PLAN.md.
- docs(04): add phase 4 research and context (dc88167) - 1 file changed, 85 insertions(+); areas: .planning; top files: .planning/phases/04-performance-and-refactoring/04-CONTEXT.md.
- docs(04): research phase domain for performance and refactoring (c353f26) - 1 file changed, 469 insertions(+); areas: .planning; top files: .planning/phases/04-performance-and-refactoring/04-RESEARCH.md.
- docs: rename milestone from v1.0 to v0.2.0 across all planning docs (049debb) - 5 files changed, 12 insertions(+), 12 deletions(-); areas: .planning, CHANGELOG.md; top files: .planning/PROJECT.md, .planning/REQUIREMENTS.md, .planning/ROADMAP.md.
- docs: trim CHANGELOG and add maintenance rule to CLAUDE.md (d2c523c) - 2 files changed, 88 insertions(+), 694 deletions(-); areas: CHANGELOG.md, docs; top files: CHANGELOG.md, docs/CLAUDE.md.
- docs(phase-03): complete phase execution and verification (e71b0ac) - 2 files changed, 146 insertions(+), 8 deletions(-); areas: .planning; top files: .planning/STATE.md, .planning/phases/03-llm-work-item-elaboration/03-VERIFICATION.md.
- docs(03-04): complete plan summary and update tracking (2809bf6) - 2 files changed, 95 insertions(+), 8 deletions(-); areas: .planning; top files: .planning/STATE.md, .planning/phases/03-llm-work-item-elaboration/03-04-SUMMARY.md.
- docs(03-03): complete plan summary and update tracking (02046ec) - 2 files changed, 163 insertions(+), 7 deletions(-); areas: .planning; top files: .planning/STATE.md, .planning/phases/03-llm-work-item-elaboration/03-03-SUMMARY.md.
- docs(03-01): complete foundation types, store & backend commands plan (0a33cc7) - 3 files changed, 121 insertions(+), 7 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/STATE.md, .planning/phases/03-llm-work-item-elaboration/03-01-SUMMARY.md.
- docs(03-02): complete prompt construction and output parsing plan (bdd146f) - 3 files changed, 145 insertions(+), 17 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/STATE.md, .planning/phases/03-llm-work-item-elaboration/03-02-SUMMARY.md.
- docs(03): create phase 3 plans for LLM work item elaboration (223c9cb) - 5 files changed, 1036 insertions(+), 2 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/phases/03-llm-work-item-elaboration/03-01-PLAN.md, .planning/phases/03-llm-work-item-elaboration/03-02-PLAN.md.
- docs(03): research phase domain (3b56557) - 1 file changed, 563 insertions(+); areas: .planning; top files: .planning/phases/03-llm-work-item-elaboration/03-RESEARCH.md.
- docs(03): capture phase context (903868c) - 1 file changed, 98 insertions(+); areas: .planning; top files: .planning/phases/03-llm-work-item-elaboration/03-CONTEXT.md.
- docs: define v1.0 requirements and update state for Phase 3 (395d48c) - 2 files changed, 79 insertions(+), 7 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/STATE.md.
- docs: move [0.1] milestone section under [Unreleased] in CHANGELOG (9e24e84) - 1 file changed, 20 insertions(+), 20 deletions(-); areas: CHANGELOG.md; top files: CHANGELOG.md.
- docs: add v0.1 milestone audit — tech_debt status, 5/5 requirements (b4ae0c9) - 1 file changed, 114 insertions(+); areas: .planning; top files: .planning/v0.1-MILESTONE-AUDIT.md.
- docs(phase-02): complete phase execution (c006a51) - 2 files changed, 224 insertions(+); areas: .planning; top files: .planning/STATE.md, .planning/phases/02-llm-provider-infrastructure/02-VERIFICATION.md.
- docs(02-03): complete AI Provider Settings UI plan — retro fix and final SUMMARY (0e33e1b) - 2 files changed, 43 insertions(+), 15 deletions(-); areas: .planning; top files: .planning/STATE.md, .planning/phases/02-llm-provider-infrastructure/02-03-SUMMARY.md.
- docs(02-03): complete AI Provider settings UI plan — SUMMARY and ROADMAP (46fd8ce) - 2 files changed, 206 insertions(+), 101 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/phases/02-llm-provider-infrastructure/02-03-SUMMARY.md.
- docs(02-01): complete LLM mode routing plan — settingsStore + llmService (f1d29cf) - 3 files changed, 88 insertions(+), 3 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/STATE.md, .planning/phases/02-llm-provider-infrastructure/02-01-SUMMARY.md.
- docs(02-04): complete Zod bulk import validation plan (7622119) - 3 files changed, 99 insertions(+), 32 deletions(-); areas: .planning, src/stores; top files: .planning/STATE.md, .planning/phases/02-llm-provider-infrastructure/02-04-SUMMARY.md, src/stores/settingsStore.ts.
- docs(02): create phase 2 plan — 4 plans in 2 waves (fc96d92) - 5 files changed, 1158 insertions(+), 95 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/phases/02-llm-provider-infrastructure/02-01-PLAN.md, .planning/phases/02-llm-provider-infrastructure/02-02-PLAN.md.
- docs(02): research phase llm-provider-infrastructure (167266b) - 1 file changed, 605 insertions(+); areas: .planning; top files: .planning/phases/02-llm-provider-infrastructure/02-RESEARCH.md.
- docs(02): capture phase context (d19cbe1) - 1 file changed, 97 insertions(+); areas: .planning; top files: .planning/phases/02-llm-provider-infrastructure/02-CONTEXT.md.
- docs(phase-01): complete phase execution (477919b) - 2 files changed, 178 insertions(+); areas: .planning; top files: .planning/STATE.md, .planning/phases/01-core-stabilization/01-VERIFICATION.md.
- docs(01-01): complete day state race condition plan — SUMMARY, STATE, ROADMAP, REQUIREMENTS (e2a7f1d) - 4 files changed, 193 insertions(+), 99 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/ROADMAP.md, .planning/STATE.md.
- docs(01-04): complete plan — Synergy RSS retry and friendly error UI (d795735) - 1 file changed, 114 insertions(+); areas: .planning; top files: .planning/phases/01-core-stabilization/01-04-SUMMARY.md.
- docs(01-03): complete backup/restore file-picker plan — SUMMARY, STATE, ROADMAP, REQUIREMENTS (f528477) - 4 files changed, 117 insertions(+), 18 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/ROADMAP.md, .planning/STATE.md.
- docs(01-02): complete worklog soft-delete plan — SUMMARY, STATE, ROADMAP (de8442d) - 4 files changed, 110 insertions(+), 13 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/ROADMAP.md, .planning/STATE.md.
- docs(01): create phase plan — 4 plans covering STBL-01 through STBL-05 (462d9b8) - 5 files changed, 966 insertions(+), 2 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/phases/01-core-stabilization/01-01-PLAN.md, .planning/phases/01-core-stabilization/01-02-PLAN.md.
- docs(01): research phase 1 core stabilization (1962d1a) - 1 file changed, 598 insertions(+); areas: .planning; top files: .planning/phases/01-core-stabilization/01-RESEARCH.md.
- docs(01): capture phase context (6260315) - 1 file changed, 110 insertions(+); areas: .planning; top files: .planning/phases/01-core-stabilization/01-CONTEXT.md.
- docs: create roadmap (5 phases) (6dfc09d) - 3 files changed, 169 insertions(+), 16 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/ROADMAP.md, .planning/STATE.md.
- docs: define v1 requirements (cb4e98f) - 1 file changed, 90 insertions(+); areas: .planning; top files: .planning/REQUIREMENTS.md.
- docs: complete project research (f2d54a9) - 5 files changed, 1925 insertions(+); areas: .planning; top files: .planning/research/ARCHITECTURE.md, .planning/research/FEATURES.md, .planning/research/PITFALLS.md.
- docs: initialize project (606a11f) - 1 file changed, 79 insertions(+); areas: .planning; top files: .planning/PROJECT.md.
- docs: map existing codebase (eefe3fd) - 7 files changed, 1685 insertions(+); areas: .planning; top files: .planning/codebase/ARCHITECTURE.md, .planning/codebase/CONCERNS.md, .planning/codebase/CONVENTIONS.md.
- docs: update skill descriptions and remove allowed-tools for clarity test: enhance day management tests for pause, resume, end, and reopen functionality (ca1743a) - 12 files changed, 61 insertions(+), 12 deletions(-); areas: .claude, src/App.tsx, tests; top files: .claude/skills/debug/SKILL.md, .claude/skills/docs/SKILL.md, .claude/skills/feature/SKILL.md.
- docs: archive day pause resume investigation plan (265e4cc) - 2 files changed, 35 insertions(+), 40 deletions(-); areas: .cursor; top files: .cursor/plans/2026-02-26-playwright-day-pause-resume-root-cause-plan.md, .cursor/plans/implemented/2026-02-26-playwright-day-pause-resume-root-cause-plan.md.
- docs: close and archive current work plans (f661a4f) - 2 files changed, 38 insertions(+), 17 deletions(-); areas: .cursor; top files: .cursor/plans/2026-02-26-automated-testing-next-steps-plan.md, .cursor/plans/2026-02-26-performance-profiling-progress.md, .cursor/plans/implemented/2026-02-26-automated-testing-next-steps-plan.md.
- docs: save product architect run output for 2026-02-28 (f7ff00c) - 1 file changed, 274 insertions(+); areas: docs; top files: docs/prompts/runs/2026-02-28-product-architect.md.
- docs: run product-architect prompt and update execution history (24f8822) - 2 files changed, 5 insertions(+), 3 deletions(-); areas: docs; top files: docs/prompts/README.md, docs/prompts/product-architect-prompt.md.
- docs: add prompt execution tracking to library (d351f92) - 1 file changed, 16 insertions(+); areas: docs; top files: docs/prompts/README.md.
- docs: organize and refresh project prompt library (8348359) - 9 files changed, 798 insertions(+), 5 deletions(-); areas: docs; top files: docs/product-architect-prompt.md, docs/prompts/README.md, docs/prompts/_template.md.
- Update project documentation (92f9347) - 25 files changed, 1039 insertions(+), 152 deletions(-); areas: CHANGELOG.md, README.md, docs, scripts; top files: CHANGELOG.md, README.md, docs/FEATURES_DETAILED.md.
- docs: Add Playwright end-to-end testing guides and Tauri mocking documentation (e3d1e7b) - 2 files changed, 123 insertions(+); areas: docs; top files: docs/E2E_TESTING_GUIDE.md, docs/TAURI_MOCKING_ARCHITECTURE.md.
- docs: Document E2E Playwright testing and Tauri mocking fixes (57ac614) - 1 file changed, 33 insertions(+); areas: .cursor; top files: .cursor/plans/2026-02-22-tauri-playwright-e2e-fixes.md.

### Build & Release

- release: v0.2.0 (859c48d) - 14 files changed, 793 insertions(+), 113 deletions(-); areas: CHANGELOG.md, docs, package.json, src-tauri/Cargo.lock; top files: CHANGELOG.md, docs/prompts/README.md, docs/prompts/_template.md.
- chore: complete v0.2.0 Production Release milestone (531eb8d) - 37 files changed, 431 insertions(+), 167 deletions(-); areas: .planning, CHANGELOG.md; top files: .planning/MILESTONES.md, .planning/PROJECT.md, .planning/REQUIREMENTS.md.
- chore(05-01): add test:e2e:stable script for parallel no-retry execution (e2edd51) - 1 file changed, 1 insertion(+); areas: package.json; top files: package.json.
- chore: complete v0.1 milestone — archive phases 1-2, evolve planning docs (39f2a4a) - 32 files changed, 347 insertions(+), 230 deletions(-); areas: .planning, CHANGELOG.md; top files: .planning/MILESTONES.md, .planning/PROJECT.md, .planning/REQUIREMENTS.md.
- chore: add project config (0ecee1b) - 1 file changed, 12 insertions(+); areas: .planning; top files: .planning/config.json.
- chore: commit untracked test files and update release-manager prompt baseline (fee1132) - 5 files changed, 292 insertions(+), 2 deletions(-); areas: docs, src/stores, src/utils, src/vitest-env.d.ts; top files: docs/prompts/release-manager-prompt.md, src/stores/newsStore.test.ts, src/utils/duration.test.ts.
- chore: commit all current changes and add pause-resume debug plan (5b8225f) - 3 files changed, 41 insertions(+), 1 deletion(-); areas: .cursor, playwright-report; top files: .cursor/plans/2026-02-22-project-restructuring.md, .cursor/plans/2026-02-26-playwright-day-pause-resume-root-cause-plan.md, .cursor/plans/implemented/2026-02-22-project-restructuring.md.
- chore(changelog): improve unreleased generation and commit detail (bf9cd34) - 2 files changed, 475 insertions(+), 288 deletions(-); areas: CHANGELOG.md, scripts; top files: CHANGELOG.md, scripts/generate-changelog.ps1.
- chore: Remove various temporary output files and add a QA engineer prompt document. (073373b) - 39 files changed, 34 insertions(+), 4596 deletions(-); areas: docs; top files: docs/qa-engineer-prompt.md.
- chore: Add `errors_latest.txt` containing current ESLint warnings. (873d592) - 1 file changed, 17 insertions(+); areas: errors_latest.txt; top files: errors_latest.txt.
- chore: close resolved QA issues (899683c) - no diff stats available; areas: (no file changes); top files: (no files listed).
- chore: fix eslint any type errors and formatting issues; add ci pipeline (c3665ec) - 14 files changed, 759 insertions(+), 101 deletions(-); areas: .github, .husky, docs, package-lock.json; top files: .github/workflows/ci.yml, .husky/pre-commit, docs/qa-engineer-prompt.md.

### Other Changes

- wip: phase 03 paused at plan 03-03 task 3/3 (9656b5a) - 1 file changed, 52 insertions(+); areas: .planning; top files: .planning/phases/03-llm-work-item-elaboration/.continue-here.md.
- merge: DevOps onboarding UX improvements (242660b) - 2 files changed, 177 insertions(+), 30 deletions(-); areas: (no file changes); top files: (no files listed).
- Merge branch 'main' of https://github.com/vanachterjacob/DeveloperCompanion (654d5e6) - 7 files changed, 131 insertions(+), 2 deletions(-); areas: playwright-report; top files: playwright-report/index.html.
- Expand-E2E-failure-coverage-and-Playwright-local-helpers (96f5c80) - 7 files changed, 315 insertions(+), 4 deletions(-); areas: scripts, tests; top files: scripts/test/run-playwright-local.bat, scripts/test/stop-playwright-webserver.bat, tests/e2e/devops-build-review.spec.ts.
- Add-backup-restore-test-coverage-and-background-task-checks (40e889e) - 4 files changed, 424 insertions(+), 91 deletions(-); areas: src-tauri/src, src/components, tests; top files: src-tauri/src/db/backup.rs, src/components/automation/BackgroundTasksPanel.tsx, tests/e2e/background-tasks.spec.ts.
- merge: perf profiling progress into main (9a2ef52) - 17 files changed, 1462 insertions(+), 229 deletions(-); areas: CHANGELOG.md; top files: CHANGELOG.md.
- Document single-instance desktop fix (284b33d) - 1 file changed, 2 insertions(+); areas: CHANGELOG.md; top files: CHANGELOG.md.
- Prevent multiple app instances (05e2c99) - 3 files changed, 24 insertions(+), 1 deletion(-); areas: src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src; top files: src-tauri/Cargo.toml, src-tauri/src/lib.rs.
- Add random retro welcome titles (29dc2b3) - 1 file changed, 34 insertions(+), 1 deletion(-); areas: src/App.tsx; top files: src/App.tsx.
- Maak instellingen overal zoekbaar (dc4ea79) - 15 files changed, 1402 insertions(+), 202 deletions(-); areas: CHANGELOG.md, README.md, docs, package-lock.json; top files: CHANGELOG.md, README.md, docs/FEATURES_DETAILED.md.

## [0.1.23] - 2026-02-21

### Release Scope

- Commit range: v0.1.22..v0.1.23
- Commits in release: 10

### Features

- feat: Add LLM-powered bulk import functionality and comprehensive application feature documentation. (a3416ab) - 5 files changed, 208 insertions(+), 71 deletions(-); areas: docs, src-tauri/src, src/services; top files: docs/CLAUDE.md, docs/FEATURES_DETAILED.md, src-tauri/src/lib.rs.
- feat: Introduce core application structure with new components, stores, services, and utilities for work logging, scheduling, DevOps, Synergy integration, and UI elements. (b8185f5) - 97 files changed, 2528 insertions(+), 1665 deletions(-); areas: .github, CHANGELOG.md, docs, index.html; top files: .github/skills/skill-lookup/SKILL.md, CHANGELOG.md, docs/product-architect-prompt.md.
- feat: support comma decimal separator in all time input forms (91cbe03) - 3 files changed, 11 insertions(+), 12 deletions(-); areas: src/components; top files: src/components/devops/BatchTimeLogDialog.tsx, src/components/worklog/WorkLogBlockDialog.tsx, src/components/worklog/WorkLogPanel.tsx.
- feat: Add core Tauri backend with AI CLI invocation and auto-updater integration. (005ab0f) - 2 files changed, 46 insertions(+), 3 deletions(-); areas: src-tauri/src, src/hooks; top files: src-tauri/src/lib.rs, src/hooks/useAutoUpdater.ts.
- feat(activity): add default emoji icons for categories (69daf16) - 3 files changed, 69 insertions(+), 4 deletions(-); areas: migrations, src-tauri/src, src/stores; top files: migrations/049_activity_icons_emoji_defaults.sql, src-tauri/src/db/migrations.rs, src/stores/activityStore.ts.

### Fixes

- fix(issues): Address issue 22 and 23 via parsing tweaks and prompt tmpfile (a2312a3) - 7 files changed, 155 insertions(+), 66 deletions(-); areas: src-tauri/src, src/components, src/services, src/stores; top files: src-tauri/src/lib.rs, src/components/worklog/BulkImportTable.tsx, src/components/worklog/WorkLogCalendar.tsx.
- fix(#25): resolve synergy API push 404 returning meaningless errors (49d9591) - 3 files changed, 59 insertions(+), 11 deletions(-); areas: src-tauri/src, src/services, src/stores; top files: src-tauri/src/synergy_api.rs, src/services/synergy/synergyApi.ts, src/stores/synergyStore.ts.

### Build & Release

- release: v0.1.23 (08af9c2) - 5 files changed, 43 insertions(+), 7 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.

### Other Changes

- Add explicit substep labels (5963675) - 17 files changed, 1593 insertions(+), 16 deletions(-); areas: src/App.tsx, src/components, src/stores, src/types; top files: src/App.tsx, src/components/common/CommandPaletteButton.tsx, src/components/common/EditModeButton.tsx.
- Clarify REST API deliverable warning (7221c37) - 5 files changed, 35 insertions(+), 13 deletions(-); areas: src/components, src/index.css, src/stores; top files: src/components/modals/SetupWizardModal.tsx, src/components/worklog/BulkImportTable.tsx, src/components/worklog/BulkImportView.tsx.

## [0.1.22] - 2026-02-19

### Release Scope

- Commit range: v0.1.21..v0.1.22
- Commits in release: 24

### Features

- feat: implement Synergy sync improvements (issue #15) (bb13e77) - 5 files changed, 336 insertions(+), 143 deletions(-); areas: src/components, src/services, src/stores; top files: src/components/modals/SettingsButton.tsx, src/services/database.ts, src/services/synergy/autoSync.ts.
- feat: add multiple notification sound options and fix rust backend compilation (ac1d117) - 7 files changed, 136 insertions(+), 76 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/045_notification_sound_setting.sql, src-tauri/src/db/migrations.rs, src/App.tsx.
- feat: move StatsHeaderBar to sidebar and stretch across 2 columns in wide mode (5ca7584) - 2 files changed, 12 insertions(+), 27 deletions(-); areas: src/App.tsx, src/stores; top files: src/App.tsx, src/stores/layoutStore.test.ts.
- feat: implement individual timeline item visibility and compact dashboard layout (75c516d) - 10 files changed, 469 insertions(+), 128 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/legacy/044_seed_devops_organizations_initial.sql, src-tauri/src/lib.rs, src/App.tsx.
- feat: add Synergy login link to settings and fix accidental truncation (7992351) - 1 file changed, 912 insertions(+), 1300 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- feat: hide timeline in minimalist mode (a631fe0) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: src/App.tsx; top files: src/App.tsx.
- feat: implement Minimalist Mode (DevOps + Synergy Calendar only) (09c2945) - 4 files changed, 379 insertions(+), 305 deletions(-); areas: src/App.tsx, src/components, src/stores; top files: src/App.tsx, src/components/modals/SettingsButton.tsx, src/components/worklog/WorkLogPanel.tsx.
- feat: restructure settings menu with sidebar navigation (308797b) - 1 file changed, 879 insertions(+), 1285 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- feat: enhance retro theme, add boot sequence UI, and fix widget visibility easter eggs (315d17c) - 6 files changed, 233 insertions(+), 25 deletions(-); areas: index.html, src/App.tsx, src/index.css, src/stores; top files: index.html, src/App.tsx, src/index.css.

### Fixes

- Fix DevOps work item sync freeze and finalize DevOps settings updates (f446a93) - 7 files changed, 1065 insertions(+), 1129 deletions(-); areas: src/components, src/services, src/stores; top files: src/components/devops/DevOpsToolsModal.tsx, src/components/devops/WorkItemsPanel.tsx, src/components/modals/SettingsButton.tsx.
- Fix Synergy API push mode to avoid Playwright fallback (66c5413) - 3 files changed, 202 insertions(+), 66 deletions(-); areas: src/components, src/services; top files: src/components/worklog/WorkLogPanel.tsx, src/services/synergy/autoSync.test.ts, src/services/synergy/autoSync.ts.
- fix: resolve stale closure causing 'All entries already synced' on confirm push (9e1bf4a) - 1 file changed, 4 insertions(+), 2 deletions(-); areas: src/components; top files: src/components/worklog/WorkLogPanel.tsx.
- fix: make playNotificationBeep more robust for short retro sounds (6903d8b) - 1 file changed, 15 insertions(+), 8 deletions(-); areas: src/utils; top files: src/utils/sound.ts.
- fix: ensure priority and other missing columns exist regardless of migration state (20ae16f) - 1 file changed, 62 insertions(+), 86 deletions(-); areas: src/services; top files: src/services/database.ts.
- fix: ensure etag column exists on devops_work_items regardless of migration state (c601ee8) - 1 file changed, 8 insertions(+), 10 deletions(-); areas: src/services; top files: src/services/database.ts.
- fix: ensure synergy columns exist on devops_project_mappings regardless of migration state (43c26d8) - 2 files changed, 31 insertions(+), 15 deletions(-); areas: migrations, src/services; top files: migrations/044_seed_devops_organizations.sql, src/services/database.ts.
- fix: register migration 044 in Rust and ensure organizations are seeded and loaded during bootstrap (e6909f3) - 5 files changed, 21 insertions(+), 18 deletions(-); areas: src-tauri/src, src/App.tsx, src/hooks, src/services; top files: src-tauri/src/db/migrations.rs, src/App.tsx, src/hooks/useAppBootstrap.ts.
- fix: update seeded devops organizations to correct list (escbvba, cascade4nav, etc.) (40bde4f) - 3 files changed, 13 insertions(+), 4 deletions(-); areas: migrations, src/components, src/stores; top files: migrations/044_seed_devops_organizations.sql, src/components/devops/DevOpsToolsModal.tsx, src/stores/settingsStore.ts.
- fix: restore missing synergy login settings and re-add minimalist mode toggle (59f0581) - 1 file changed, 1300 insertions(+), 893 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.

### Build & Release

- release: v0.1.22 (ac10f91) - 5 files changed, 47 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.

### Other Changes

- Simplify todo UX, improve timeline toggle, and persist DevOps work item URLs (61146a0) - 13 files changed, 1633 insertions(+), 394 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/046_todo_productivity_upgrade.sql, migrations/047_expand_default_activities_balance.sql, migrations/048_todo_devops_work_item_url.sql.
- Merge branch 'feature/synergy-sync-improvements' into main (86a86fa) - 7 files changed, 542 insertions(+), 211 deletions(-); areas: (no file changes); top files: (no files listed).
- style: move minimalist mode toggle to appearance settings tab (34bf1e5) - 1 file changed, 14 insertions(+), 14 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- Stop dev server when starting client (29da89f) - 2 files changed, 12 insertions(+), 6 deletions(-); areas: package.json, scripts; top files: package.json, scripts/dev/start-client.ps1.

## [0.1.21] - 2026-02-19

### Release Scope

- Commit range: v0.1.20..v0.1.21
- Commits in release: 4

### Refactoring

- refactor: minor code cleanup in synergy components (43f41b6) - 2 files changed, 1 insertion(+), 2 deletions(-); areas: src/components, src/stores; top files: src/components/synergy/SynergyPushPreviewModal.tsx, src/stores/healthStore.ts.

### Documentation

- docs: update changelog for v0.1.21 (d59229e) - 1 file changed, 17 insertions(+), 1 deletion(-); areas: CHANGELOG.md; top files: CHANGELOG.md.

### Build & Release

- chore: sync package-lock.json for v0.1.21 (199b6b6) - 1 file changed, 62 insertions(+), 2 deletions(-); areas: package-lock.json; top files: package-lock.json.
- release: v0.1.21 (2a1a3b2) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.

## [0.1.20] - 2026-02-19

### Release Scope

- Commit range: v0.1.19..v0.1.20
- Commits in release: 19

### Features

- feat(ui): add retro-style notification sound for the retro theme (1f30e04) - 4 files changed, 71 insertions(+), 31 deletions(-); areas: src/App.tsx, src/components, src/hooks, src/utils; top files: src/App.tsx, src/components/modals/SettingsButton.tsx, src/hooks/useScheduledNotifications.ts.
- feat(llm): optimize gemini cli integration with auto model and yolo mode (f7628e5) - 9 files changed, 93 insertions(+), 49 deletions(-); areas: package-lock.json, package.json, src-tauri/src, src/components; top files: package.json, src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs.
- feat(llm): add gemini cli support and improve cli detection logic (6b462d4) - 5 files changed, 104 insertions(+), 7 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/lib.rs, src/components/modals/SettingsButton.tsx, src/components/modals/SetupWizardModal.tsx.
- feat(synergy): implement persistent session health indicator (issue #8) (e69e353) - 5 files changed, 145 insertions(+), 2 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/lib.rs, src-tauri/src/synergy_api.rs, src/components/common/IntegrationHealthIndicator.tsx.

### Fixes

- fix(synergy): resolve crash in push preview by fixing payload property names and hardening parser (8ab0e0c) - 2 files changed, 20 insertions(+), 20 deletions(-); areas: src/components; top files: src/components/synergy/SynergyPushPreviewModal.tsx, src/components/worklog/WorkLogPanel.tsx.
- fix(synergy): ensure all push actions go through the preview modal by refactoring push triggers (48f3031) - 5 files changed, 367 insertions(+), 15 deletions(-); areas: src-tauri/src, src/App.tsx, src/components, src/stores; top files: src-tauri/src/lib.rs, src/App.tsx, src/components/synergy/SynergyPushPreviewModal.tsx.
- fix(synergy): resolve trim error in login modal by using correct baseUrl and password retrieval (e20a395) - 4 files changed, 180 insertions(+), 2 deletions(-); areas: src/App.tsx, src/components, src/stores; top files: src/App.tsx, src/components/automation/SynergyLoginModal.tsx, src/components/common/IntegrationHealthIndicator.tsx.
- fix: introduce connection generation to resolve persistent database lock issues by forcing fresh connection pools. (794ce8a) - 4 files changed, 327 insertions(+); areas: .cursor; top files: .cursor/plans/2026-02-18-database-lock-stability.md, .cursor/plans/flexiblesidebar.md, .cursor/plans/implementation_plan.md.resolved.

### Refactoring

- refactor(ui): consolidate current activity into DayTimeline (995f67f) - 8 files changed, 717 insertions(+), 204 deletions(-); areas: README.md, docs, src/App.tsx, src/components; top files: README.md, docs/FEATURES_DETAILED.md, docs/wiki/Home.md.
- refactor(dayStore): use upsert for start day logic (29cb8d0) - 1 file changed, 21 insertions(+), 20 deletions(-); areas: src/stores; top files: src/stores/dayStore.ts.

### Documentation

- docs(plans): update flexible sidebar layout plan to draft status (cafe769) - 5 files changed, 600 insertions(+), 574 deletions(-); areas: src/App.tsx, src/components, src/stores; top files: src/App.tsx, src/components/common/WidgetWrapper.tsx, src/stores/layoutStore.test.ts.
- docs: consolidate database lock plan to single strategy (101dd2a) - 11 files changed, 370 insertions(+), 304 deletions(-); areas: scripts, src/App.tsx, src/components, src/index.css; top files: scripts/dev/restart-dev.ps1, scripts/dev/start-client.ps1, scripts/dev/tail-app-log.ps1.

### Build & Release

- release: v0.1.20 (1bc6bb7) - 4 files changed, 71 insertions(+), 24 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- chore: tussentijdse commit (5e8b03c) - 35 files changed, 3046 insertions(+), 686 deletions(-); areas: docs, package.json, scripts, src-tauri/src; top files: docs/wiki/DatabaseLockDiagnostics.md, docs/wiki/Home.md, package.json.
- chore(scripts): add dev lifecycle and client start commands (4c066f6) - 7 files changed, 168 insertions(+); areas: package.json, scripts; top files: package.json, scripts/dev/restart-dev.bat, scripts/dev/restart-dev.ps1.

### Other Changes

- optimize: keep YouTube Music playing when closing the separate window by hiding it instead (c37a0f1) - 3 files changed, 24 insertions(+), 4 deletions(-); areas: src-tauri/src, src/stores; top files: src-tauri/src/lib.rs, src-tauri/src/youtube_music.rs, src/stores/youtubeMusicStore.ts.
- accessibility: improve a11y, add personalized retro easter eggs and UI tweaks (b701204) - 8 files changed, 624 insertions(+), 58 deletions(-); areas: index.html, src/App.tsx, src/components, src/index.css; top files: index.html, src/App.tsx, src/components/common/StatsFooterBar.tsx.
- security: harden cli calls, update vulnerable dependencies, and improve html sanitization (b6ddd1e) - 7 files changed, 728 insertions(+), 539 deletions(-); areas: package-lock.json, package.json, src-tauri/Cargo.lock, src-tauri/src; top files: package.json, src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs.
- #7 refactor(App): implement dynamic sidebar widget rendering (44beb4a) - 6 files changed, 391 insertions(+), 247 deletions(-); areas: src/App.tsx, src/components, src/stores; top files: src/App.tsx, src/components/common/Animations.tsx, src/components/common/WidgetWrapper.tsx.

## [0.1.19] - 2026-02-17

### Release Scope

- Commit range: v0.1.18..v0.1.19
- Commits in release: 24

### Features

- feat: Initialize Tauri backend for agent functionality and update Vite dependency. (497a968) - 2 files changed, 2 insertions(+), 15 deletions(-); areas: package-lock.json, package.json; top files: package.json.
- feat: Introduce Review Panel for generating feedback build prompts from selected comments and related code. (219041d) - 7 files changed, 113 insertions(+), 26 deletions(-); areas: migrations, src-tauri/src, src/components, src/stores; top files: migrations/043_devops_build_jobs_additional_prompt.sql, src-tauri/src/build_orchestrator.rs, src-tauri/src/db/migrations.rs.
- feat: Add core Tauri backend with AI CLI invocation and initial UI components for worklog, time tracking, and integrations. (c80ca2e) - 8 files changed, 1644 insertions(+), 16 deletions(-); areas: issue_content.html, src-tauri/src, src/components, src/services; top files: issue_content.html, src-tauri/src/lib.rs, src/components/devops/TimeLogDialog.tsx.
- feat: Implement AI code review functionality with LLM CLI integration and UI components for DevOps work items. (a8eac68) - 8 files changed, 778 insertions(+), 53 deletions(-); areas: src-tauri/src, src/components, src/services; top files: src-tauri/src/ai_review.rs, src-tauri/src/app_dependencies.rs, src-tauri/src/build_orchestrator.rs.
- feat: add WorkItemDetailModal component for displaying work item details and related actions. (067564f) - 1 file changed, 2 insertions(+), 1 deletion(-); areas: src/components; top files: src/components/devops/WorkItemDetailModal.tsx.
- feat: Introduce a comprehensive settings store and initial DevOps features, including AI review and build orchestration. (ae28888) - 5 files changed, 113 insertions(+), 4 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs, src/components/devops/DevOpsToolsModal.tsx.
- feat: Initialize Tauri application with Rust backend for CLI tool invocation and DevOps integration, including new HTML utilities. (aeea3f1) - 10 files changed, 530 insertions(+), 18 deletions(-); areas: package-lock.json, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml, src-tauri/src/lib.rs.
- feat: Implement AI code review functionality for DevOps builds with new store, backend module, and UI components. (b14ff4f) - 5 files changed, 143 insertions(+), 63 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/ai_review.rs, src/components/devops/ReviewPanel.tsx, src/components/devops/WorkItemDetailModal.tsx.
- feat: Implement build concurrency checks and improve CLI command handling in DevOps workflow (50bd5d8) - 4 files changed, 157 insertions(+), 63 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/build_orchestrator.rs, src/components/devops/WorkItemsPanel.tsx, src/stores/devopsBuildStore.ts.
- feat: Add WorkItemsPanel component and synergyStore for managing DevOps work items. (7b0e108) - 2 files changed, 342 insertions(+), 43 deletions(-); areas: src/components, src/stores; top files: src/components/devops/WorkItemsPanel.tsx, src/stores/synergyStore.ts.
- feat: Implement a build orchestration system to manage DevOps work item builds, CLI tool execution, and Git operations. (6b3bf59) - 5 files changed, 126 insertions(+), 100 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/build_orchestrator.rs, src-tauri/src/lib.rs, src/components/devops/DevOpsToolsModal.tsx.
- feat: Enhance CLI integration and DevOps build workflow (1d487a5) - 8 files changed, 895 insertions(+), 52 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs, src-tauri/src/lib.rs.
- feat(cursor): add dependency checks and improve CLI integration in DevOps settings (bb7fd65) - 7 files changed, 293 insertions(+), 174 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs, src-tauri/src/lib.rs.
- feat: enhance CLI engine descriptions and error handling (3ffcf8f) - 5 files changed, 160 insertions(+), 16 deletions(-); areas: src-tauri/src, src/components; top files: src-tauri/src/lib.rs, src/components/devops/DevOpsToolsModal.tsx, src/components/modals/SettingsButton.tsx.

### Fixes

- Fix Cursor CLI failure on Windows by injecting bundled ripgrep into PATH (32ee324) - 1 file changed, 55 insertions(+), 2 deletions(-); areas: src-tauri/src; top files: src-tauri/src/lib.rs.
- fix(db): add SQLite concurrency handling to prevent locked errors (0efa9cd) - 15 files changed, 609 insertions(+), 269 deletions(-); areas: docs, migrations, src-tauri/src, src/components; top files: docs/CLAUDE.md, docs/FEATURES_DETAILED.md, docs/release-versioning.md.

### Refactoring

- refactor: replace custom JSON comment stripper with json_comments (3bf2a01) - 3 files changed, 11 insertions(+), 52 deletions(-); areas: src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src; top files: src-tauri/Cargo.toml, src-tauri/src/app_dependencies.rs.
- refactor: move dependency markdown generation to backend (83ed52b) - 6 files changed, 30 insertions(+), 61 deletions(-); areas: src-tauri/src, src/components, src/services, src/stores; top files: src-tauri/src/app_dependencies.rs, src/components/devops/ReviewPanel.tsx, src/components/devops/WorkItemDetailModal.tsx.

### Documentation

- docs: add release documentation checklist and improve AI review (a8c8178) - 9 files changed, 775 insertions(+), 106 deletions(-); areas: docs, src-tauri/src, src/components; top files: docs/release-versioning.md, src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs.

### Build & Release

- release: v0.1.19 (d625438) - 6 files changed, 181 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, scripts, src-tauri/Cargo.lock; top files: CHANGELOG.md, package.json, scripts/generate-changelog.ps1.
- chore(gitignore): ignore scraped issue content (2b6f58f) - 2 files changed, 4 insertions(+), 1558 deletions(-); areas: .gitignore, issue_content.html; top files: .gitignore, issue_content.html.

### Other Changes

- Update Cursor model validation and options to support latest frontier models like opus-4.6 (8810a12) - 2 files changed, 22 insertions(+), 16 deletions(-); areas: src-tauri/src, src/stores; top files: src-tauri/src/lib.rs, src/stores/settingsStore.ts.
- Use cursor.cmd for agent invocation to prevent GUI windows (8bc898c) - 1 file changed, 44 insertions(+), 14 deletions(-); areas: src-tauri/src; top files: src-tauri/src/lib.rs.
- Add Tab key functionality (fb9cfe8) - 3 files changed, 118 insertions(+), 118 deletions(-); areas: src/components; top files: src/components/synergy/SynergyCustomerCombobox.tsx, src/components/synergy/SynergyDeliverableCombobox.tsx, src/components/synergy/SynergyProjectCombobox.tsx.

## [0.1.18] - 2026-02-16

### Release Scope

- Commit range: v0.1.17..v0.1.18
- Commits in release: 4

### Documentation

- docs: enhance installation troubleshooting and update customer scraper logic (bd8d675) - 10 files changed, 158 insertions(+), 51 deletions(-); areas: docs, scripts, src/components, src/hooks; top files: docs/wiki/Installation.md, scripts/synergy/synergy-customers-scraper.mjs, src/components/modals/AboutButton.tsx.
- docs: update README and wiki sync workflow (cbe5497) - 7 files changed, 121 insertions(+), 23 deletions(-); areas: .github, README.md, docs, src/components; top files: .github/workflows/release.yml, .github/workflows/wiki-sync.yml, README.md.

### Build & Release

- release: v0.1.18 (e5bd66a) - 5 files changed, 9 insertions(+), 5 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- chore: add .editorconfig and husky pre-commit hook for security checks (e0cdd7f) - 11 files changed, 431 insertions(+), 17 deletions(-); areas: .ai, .editorconfig, .github, .husky; top files: .ai/prompts/code-review.md, .ai/prompts/commit.md, .editorconfig.

## [0.1.17] - 2026-02-16

### Release Scope

- Commit range: v0.1.16..v0.1.17
- Commits in release: 5

### Features

- feat: enhance synchronization and error handling in autoSync and related stores (ca94f30) - 8 files changed, 131 insertions(+), 78 deletions(-); areas: src-tauri/src, src/hooks, src/services, src/stores; top files: src-tauri/src/synergy_api.rs, src/hooks/useAppBootstrap.ts, src/services/synergy/autoSync.ts.

### Fixes

- fix: remove unnecessary cursor.cmd from Windows CLI candidates (8facb42) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: src-tauri/src; top files: src-tauri/src/lib.rs.

### Documentation

- docs: update release versioning guidelines and changelog policy (23c0f61) - 2 files changed, 494 insertions(+), 56 deletions(-); areas: CHANGELOG.md, docs; top files: CHANGELOG.md, docs/release-versioning.md.

### Build & Release

- release: v0.1.17 (938487b) - 5 files changed, 27 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.

### Other Changes

- Add unit tests for preSyncValidation, dayStore, timerStore, and timer utility functions (0ad63c7) - 21 files changed, 4909 insertions(+), 49 deletions(-); areas: .github, docs, src/services, src/stores; top files: .github/skills/prompt-engineering-patterns/SKILL.md, .github/skills/prompt-engineering-patterns/assets/prompt-template-library.md, .github/skills/prompt-engineering-patterns/references/chain-of-thought.md.

## [0.1.16] - 2026-02-14

### Release Scope

- Commit range: v0.1.15..v0.1.16
- Commits in release: 8

### Features

- feat: enhance error handling and notifications in App component (779b4fd) - 20 files changed, 603 insertions(+), 105 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/040_worklog_audit_log.sql, migrations/041_worklog_batch_import_id.sql, src-tauri/src/db/migrations.rs.
- feat: add Git commit handling and unclean repository checks in DevOps build process (14e9c27) - 2 files changed, 178 insertions(+), 14 deletions(-); areas: src-tauri/src, src/stores; top files: src-tauri/src/outlook_synergy_import.rs, src/stores/devopsBuildStore.ts.
- feat: enhance DevOps tools and UI components (2487ba4) - 30 files changed, 1395 insertions(+), 449 deletions(-); areas: README.md, docs, package-lock.json, scripts; top files: README.md, docs/FEATURES_DETAILED.md, docs/release-versioning.md.
- feat: Implement new UI components for work logging, timers, and various modals, including Synergy integration. (a9de997) - 18 files changed, 4855 insertions(+), 4294 deletions(-); areas: package-lock.json, package.json, src/components; top files: package.json, src/components/common/ActivityList.tsx, src/components/common/Animations.tsx.
- feat: Add detailed product architect innovation plan and related documentation files. (0ffe998) - 3 files changed, 286 insertions(+); areas: docs; top files: docs/product-architect-prompt.md.
- feat: Implement automatic Synergy worklog synchronization with API and Playwright fallback, and add new backend services for AI review, AL search, and project scanning, alongside a plan for QA improvements. (9a75537) - 13 files changed, 765 insertions(+), 272 deletions(-); areas: docs, package.json, src-tauri/src, src/services; top files: docs/qa-engineer-prompt.md, package.json, src-tauri/src/ai_review.rs.

### Build & Release

- release: v0.1.16 (b5b389c) - 6 files changed, 23 insertions(+), 6 deletions(-); areas: CHANGELOG.md, package-lock.json, package.json, src-tauri/Cargo.lock; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- chore: update Cargo.lock for v0.1.15 (9ba0c4d) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: src-tauri/Cargo.lock; top files: src-tauri/Cargo.lock.

## [0.1.15] - 2026-02-12

### Release Scope

- Commit range: v0.1.14..v0.1.15
- Commits in release: 8

### Features

- feat: Add workflow detail caching and retrieval functions in WorkLogCalendar (2ff9558) - 1 file changed, 198 insertions(+), 60 deletions(-); areas: src/components; top files: src/components/worklog/WorkLogCalendar.tsx.
- feat: Implement feedback selection and build prompt features (43dc8f3) - 9 files changed, 615 insertions(+), 158 deletions(-); areas: src/components, src/services, src/stores; top files: src/components/devops/CommentsModal.tsx, src/components/devops/DevOpsToolsModal.tsx, src/components/devops/ReviewPanel.tsx.
- feat: Enhance DevOps build process with custom branch support and AI build options (9386d8c) - 17 files changed, 567 insertions(+), 53 deletions(-); areas: migrations, src-tauri/src, src/components, src/hooks; top files: migrations/039_devops_build_jobs_starting_branch.sql, src-tauri/src/build_orchestrator.rs, src-tauri/src/db/migrations.rs.
- feat: enhance concurrency handling in runWithConcurrencyLimit to return failures alongside results (a7c850e) - 22 files changed, 1008 insertions(+), 154 deletions(-); areas: scripts, src-tauri/src, src/App.tsx, src/components; top files: scripts/db/migration-smoke-test.mjs, src-tauri/src/background_tasks.rs, src-tauri/src/devops_api.rs.
- feat: QA review phase 1 - enhance App component with bootstrap error handling and UI feedback (a8534fa) - 35 files changed, 708 insertions(+), 811 deletions(-); areas: .github, AGENTS.md, docs, src-tauri/src; top files: .github/workflows/release.yml, AGENTS.md, docs/SYNERGY_OPEN_REGISTRATION_PATCH_REPORT.md.
- feat: add QA Audit Bug & Edge Case Report for Developer Companion (fc0e527) - 1 file changed, 231 insertions(+); areas: .cursor; top files: .cursor/plans/2026-02-11-qa-audit-bug-edge-case-report.md.

### Refactoring

- Refactor and enhance error handling across various components (e9dd0fa) - 15 files changed, 409 insertions(+), 185 deletions(-); areas: package-lock.json, scripts, src-tauri/src, src/components; top files: scripts/dev/start.bat, scripts/dev/tauri-fast.mjs, src-tauri/src/background_tasks.rs.

### Build & Release

- release: v0.1.15 (67ad0ca) - 3 files changed, 3 insertions(+), 3 deletions(-); areas: package.json, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.

## [0.1.14] - 2026-02-11

### Release Scope

- Commit range: v0.1.13..v0.1.14
- Commits in release: 8

### Features

- feat: enhance WorkLogCalendar with loading state and animations (e3ad112) - 3 files changed, 43 insertions(+), 9 deletions(-); areas: src/components, tailwind.config.cjs; top files: src/components/worklog/WorkLogCalendar.tsx, src/components/worklog/WorkLogCalendarBlock.tsx, tailwind.config.cjs.
- feat: enhance DevOpsToolsModal and work item title detection (77b5fb8) - 3 files changed, 46 insertions(+), 3 deletions(-); areas: src/components, src/services; top files: src/components/devops/DevOpsToolsModal.tsx, src/services/devops/__tests__/workItemService.test.ts, src/services/devops/workItemService.ts.
- feat: update settings and enhance CLI model handling (b05c25d) - 15 files changed, 413 insertions(+), 146 deletions(-); areas: index.html, package-lock.json, src-tauri/src, src/App.tsx; top files: index.html, src-tauri/src/build_orchestrator.rs, src-tauri/src/lib.rs.

### Build & Release

- release: v0.1.14 (8bd7b14) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.

### Other Changes

- Status filter pills appear above the build cards when there are multiple statuses present. Each pill is a toggle button styled with the status's color: (37110c0) - 1 file changed, 69 insertions(+), 1 deletion(-); areas: src/components; top files: src/components/devops/DiffViewer.tsx.
- Merge branch 'main' of https://github.com/vanachterjacob/DeveloperCompanion (60829f1) - 18 files changed, 500 insertions(+), 143 deletions(-); areas: src-tauri/src; top files: src-tauri/src/build_orchestrator.rs.
- Add Support for Claude CLI (b7803be) - 3 files changed, 65 insertions(+), 18 deletions(-); areas: package-lock.json, src-tauri/src; top files: src-tauri/src/build_orchestrator.rs.
- Update Gitignore (123409e) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: .gitignore; top files: .gitignore.

## [0.1.13] - 2026-02-11

### Release Scope

- Commit range: v0.1.12..v0.1.13
- Commits in release: 3

### Features

- feat: enhance work log and synergy integration (8c27657) - 45 files changed, 3518 insertions(+), 433 deletions(-); areas: docs, migrations, package-lock.json, src-tauri/src; top files: docs/FEATURES_DETAILED.md, docs/IMPROVEMENTS.md, docs/SYNERGY_OPEN_REGISTRATION_PATCH_REPORT.md.
- feat: implement weather proxy and enhance weather data fetching (5eda6c4) - 3 files changed, 161 insertions(+), 39 deletions(-); areas: src-tauri/src, src/services; top files: src-tauri/src/lib.rs, src-tauri/src/weather.rs, src/services/weather.ts.

### Build & Release

- release: v0.1.13 (3ab6073) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.

## [0.1.12] - 2026-02-10

### Release Scope

- Commit range: v0.1.11..v0.1.12
- Commits in release: 1

### Build & Release

- release: v0.1.12 (46f9cad) - 5 files changed, 11 insertions(+), 5 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.

## [0.1.11] - 2026-02-10

### Release Scope

- Commit range: v0.1.10..v0.1.11
- Commits in release: 1

### Build & Release

- release: v0.1.11 (08c0197) - 7 files changed, 31 insertions(+), 16 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.

## [0.1.10] - 2026-02-10

### Release Scope

- Commit range: v0.1.9..v0.1.10
- Commits in release: 1

### Build & Release

- release: v0.1.10 (b8d4d4b) - 5 files changed, 18 insertions(+), 12 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.toml, src/components; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.

## [0.1.9] - 2026-02-10

### Release Scope

- Commit range: v0.1.8..v0.1.9
- Commits in release: 3

### Features

- feat: enhance weather widget and modal with location settings and geocoding support (25f2c83) - 7 files changed, 605 insertions(+), 118 deletions(-); areas: migrations, package-lock.json, src-tauri/src, src/components; top files: migrations/037_weather_location_settings.sql, src-tauri/src/db/migrations.rs, src/components/common/WeatherWidget.tsx.

### Fixes

- fix: correct release notes URL to point to public updates repo (ee91d76) - 4 files changed, 146 insertions(+), 6 deletions(-); areas: .github, CHANGELOG.md, docs, src/hooks; top files: .github/workflows/release.yml, CHANGELOG.md, docs/release-versioning.md.

### Build & Release

- release: v0.1.9 (d028a03) - 5 files changed, 15 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.

## [0.1.8] - 2026-02-10

### Release Scope

- Commit range: v0.1.7..v0.1.8
- Commits in release: 14

### Features

- feat: integrate local commit scanning and enhance work item link management (18f3e86) - 17 files changed, 1906 insertions(+), 119 deletions(-); areas: migrations, src-tauri/src, src/components, src/services; top files: migrations/036_devops_work_item_links.sql, src-tauri/src/al_search.rs, src-tauri/src/db/migrations.rs.
- feat: enhance security and sanitization across components (ca11c2f) - 16 files changed, 488 insertions(+), 119 deletions(-); areas: src-tauri/src, src/components, src/services, src/stores; top files: src-tauri/src/secure_storage.rs, src/components/devops/DevOpsToolsModal.tsx, src/components/devops/WorkItemDetailModal.tsx.
- feat: Implement upgrade work item filtering and enhance project mapping logic (d037c6b) - 8 files changed, 247 insertions(+), 41 deletions(-); areas: src/components, src/index.css, src/services, src/stores; top files: src/components/devops/WorkItemsPanel.tsx, src/index.css, src/services/devops/__tests__/projectMappingKey.test.ts.
- feat: Update button styles for improved UI consistency and accessibility (a0dbbdf) - 6 files changed, 17 insertions(+), 11 deletions(-); areas: src/components, src/utils; top files: src/components/devops/BuildAnalyticsPanel.tsx, src/components/devops/DevOpsToolsModal.tsx, src/components/devops/WorkItemDetailModal.tsx.
- feat: Enhance UI settings with density modes, reduced motion toggle, and date/time preferences (3454938) - 14 files changed, 914 insertions(+), 37 deletions(-); areas: src/components, src/hooks, src/index.css, src/stores; top files: src/components/common/Toast.tsx, src/components/modals/SettingsButton.tsx, src/components/worklog/WorkLogBlockDialog.tsx.
- feat: add retro theme option and update theme handling logic (e089d94) - 4 files changed, 261 insertions(+), 4 deletions(-); areas: src/components, src/hooks, src/index.css, src/stores; top files: src/components/modals/SettingsButton.tsx, src/hooks/useApplyTheme.ts, src/index.css.
- feat: add UI theme customization and improve component styling (a323251) - 18 files changed, 320 insertions(+), 156 deletions(-); areas: package-lock.json, src/components, src/hooks, src/stores; top files: src/components/calendar/FullscreenCalendarModal.tsx, src/components/devops/BatchTimeLogDialog.tsx, src/components/devops/BuildDashboard.tsx.
- feat: add comprehensive documentation for Developer Companion (2fce494) - 3 files changed, 523 insertions(+); areas: docs; top files: docs/wiki/Home.md, docs/wiki/Installation.md, docs/wiki/Settings.md.
- feat: implement edge case hardening plan for security improvements (7b7379d) - 13 files changed, 520 insertions(+), 19 deletions(-); areas: package-lock.json, src-tauri/src, src/components, src/services; top files: src-tauri/src/devops_api.rs, src-tauri/src/lib.rs, src/components/scrapers/RssFeedTestPanel.tsx.

### Fixes

- fix: update release notes URL to point to updates repo (7af620f) - 1 file changed, 3 insertions(+), 2 deletions(-); areas: .github; top files: .github/workflows/release.yml.

### Refactoring

- refactor: simplify release URL resolution in useAutoUpdater hook (9def06d) - 1 file changed, 11 deletions(-); areas: src/hooks; top files: src/hooks/useAutoUpdater.ts.

### Documentation

- chore: update documentation and improve formatting consistency (9b02004) - 157 files changed, 5819 insertions(+), 3091 deletions(-); areas: AGENTS.md, README.md, docs, package-lock.json; top files: AGENTS.md, README.md, docs/IMPROVEMENTS.md.

### Build & Release

- release: v0.1.8 (0a375d3) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.
- chore: remove outdated additional edge case hardening plan document (e6842e7) - 5 files changed, 693 insertions(+); areas: .cursor; top files: .cursor/PLAN_GUIDELINES.md, .cursor/plans/2026-02-10-PLAN_BACKEND_HARDENING.md, .cursor/plans/2026-02-10-additional-edge-case-hardening-plan.md.

## [0.1.7] - 2026-02-09

### Release Scope

- Commit range: v0.1.6..v0.1.7
- Commits in release: 7

### Features

- feat: integrate Outlook tool availability check and enhance settings management (58f8818) - 4 files changed, 333 insertions(+), 47 deletions(-); areas: src-tauri/src, src/components; top files: src-tauri/src/lib.rs, src-tauri/src/outlook_synergy_import.rs, src/components/modals/SettingsButton.tsx.
- feat: add news summary settings and migration support (bbcea00) - 7 files changed, 468 insertions(+), 82 deletions(-); areas: AGENTS.md, migrations, src-tauri/src, src/components; top files: AGENTS.md, migrations/035_news_summary_settings.sql, src-tauri/src/db/migrations.rs.
- feat: enhance AboutButton with current version notes and improved UI (300db4f) - 4 files changed, 129 insertions(+), 17 deletions(-); areas: src-tauri/src, src/components; top files: src-tauri/src/ai_review.rs, src-tauri/src/al_compiler.rs, src-tauri/src/build_orchestrator.rs.
- feat: add customer ID resolution by code in Synergy API (658ed5d) - 5 files changed, 185 insertions(+), 3 deletions(-); areas: package-lock.json, src-tauri/src, src/components, src/services; top files: src-tauri/src/lib.rs, src-tauri/src/synergy_api.rs, src/components/modals/WeekOverviewModal.tsx.
- feat: standardize language and improve English consistency across the application (4d0008f) - 24 files changed, 145 insertions(+), 133 deletions(-); areas: AGENTS.md, src/App.tsx, src/components, src/services; top files: AGENTS.md, src/App.tsx, src/components/modals/SetupWizardModal.tsx.
- feat: enhance visibility-aware intervals across components (f9e7dbf) - 25 files changed, 430 insertions(+), 248 deletions(-); areas: scripts, src-tauri/src, src/components, src/hooks; top files: scripts/synergy/synergy-auth.mjs, src-tauri/src/al_compiler.rs, src-tauri/src/git_workflow.rs.

### Build & Release

- release: v0.1.7 (66126a2) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.

## [0.1.6] - 2026-02-09

### Release Scope

- Commit range: v0.1.5..v0.1.6
- Commits in release: 28

### Features

- feat: enhance scraper components with progress tracking and state management (a7db3bc) - 14 files changed, 864 insertions(+), 1327 deletions(-); areas: src-tauri/NS - New Sales, src-tauri/src, src/components, src/hooks; top files: src-tauri/NS - New Sales/Cod50037.NSNewSalesMgt.al, src-tauri/NS - New Sales/Enum50004.NSDocumentType.al, src-tauri/NS - New Sales/Pag50025.NSNewSalesTypes.al.
- feat: enhance scraper progress tracking and estimation (d3bee7e) - 5 files changed, 380 insertions(+), 42 deletions(-); areas: scripts, src-tauri/src, src/components; top files: scripts/synergy/synergy-customers-scraper.mjs, scripts/synergy/synergy-deliverables-scraper.mjs, scripts/synergy/synergy-projects-scraper.mjs.
- feat: enhance DevOps tools with state change notifications and work item logging (c2946f1) - 16 files changed, 1926 insertions(+), 113 deletions(-); areas: src-tauri/src, src/components, src/services, src/stores; top files: src-tauri/src/al_search.rs, src-tauri/src/lib.rs, src/components/devops/BatchTimeLogDialog.tsx.
- feat: enhance BuildDashboard and DevOps tools with inline commenting and navigation (491c162) - 15 files changed, 2455 insertions(+), 119 deletions(-); areas: src/components, src/services, src/stores; top files: src/components/devops/BuildDashboard.tsx, src/components/devops/DevOpsToolsModal.tsx, src/components/devops/DiffViewer.tsx.
- feat: enhance BuildDashboard and DevOps tools with new features (91bee76) - 15 files changed, 1936 insertions(+), 277 deletions(-); areas: src-tauri/NS - New Sales, src-tauri/src, src/components, src/stores; top files: src-tauri/NS - New Sales/Cod50037.NSNewSalesMgt.al, src-tauri/NS - New Sales/Enum50004.NSDocumentType.al, src-tauri/NS - New Sales/Pag50025.NSNewSalesTypes.al.
- feat: enhance WorkItemsPanel with organization selection and sorting features (6409f9f) - 10 files changed, 602 insertions(+), 494 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/build_orchestrator.rs, src/components/devops/BuildAnalyticsPanel.tsx, src/components/devops/BuildDashboard.tsx.
- feat: enhance DevOps tools integration and UI improvements (88b42da) - 5 files changed, 98 insertions(+), 52 deletions(-); areas: src/App.tsx, src/components; top files: src/App.tsx, src/components/common/CommandPalette.tsx, src/components/devops/DevOpsToolsModal.tsx.
- feat: enhance DevOps integration with automatic time logging and project mapping (817af6a) - 38 files changed, 5491 insertions(+), 132 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/033_devops_synergy_mapping.sql, migrations/034_devops_build_jobs_add_columns.sql, src-tauri/src/ai_review.rs.
- feat: implement DevOps integration and settings management (4b0d130) - 26 files changed, 5086 insertions(+), 15 deletions(-); areas: migrations, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src; top files: migrations/030_devops_integration.sql, migrations/031_devops_builds.sql, migrations/032_devops_phase1_2_extensions.sql.
- feat: integrate synergy URL handling across components (a5e6266) - 6 files changed, 19 insertions(+), 15 deletions(-); areas: src/components; top files: src/components/common/UpdateBanner.tsx, src/components/modals/AboutButton.tsx, src/components/news/NewsArticleCard.tsx.
- feat: integrate synergy project and customer selection in TodoPanel (c8593ab) - 5 files changed, 191 insertions(+), 36 deletions(-); areas: migrations, src-tauri/src, src/components, src/stores; top files: migrations/029_todo_synergy_lookup.sql, src-tauri/src/db/migrations.rs, src/components/panels/TodoPanel.tsx.
- feat: enhance user experience with new features and UI improvements (5b4c433) - 37 files changed, 2002 insertions(+), 149 deletions(-); areas: README.md, docs, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: README.md, docs/FEATURES_DETAILED.md, docs/PRESENTATION_GUIDE.md.
- feat: enhance audio state management during track transitions (165e680) - 1 file changed, 114 insertions(+), 5 deletions(-); areas: src-tauri/src; top files: src-tauri/src/youtube_music.rs.
- feat: add Vitest support and enhance settings with notification grace period (7227bc6) - 17 files changed, 1062 insertions(+), 99 deletions(-); areas: migrations, package-lock.json, package.json, src/App.tsx; top files: migrations/015_auto_sync_settings.sql, migrations/017_sync_verification.sql, package.json.
- feat: add SettingsGroup component to enhance settings UI organization (ada0374) - 1 file changed, 683 insertions(+), 540 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- feat: add support for OpenAI Codex CLI and enhance settings UI (f01f945) - 23 files changed, 3119 insertions(+), 256 deletions(-); areas: migrations, package-lock.json, package.json, src-tauri/src; top files: migrations/028_news_article_summaries.sql, package.json, src-tauri/src/db/migrations.rs.
- feat: enhance error handling and JSON parsing across components (f2e986c) - 20 files changed, 1016 insertions(+), 109 deletions(-); areas: src-tauri/src, src/components, src/main.tsx, src/services; top files: src-tauri/src/background_tasks.rs, src-tauri/src/lib.rs, src/components/common/ErrorBoundary.tsx.
- feat: enhance button titles for improved user experience (1c40c01) - 12 files changed, 305 insertions(+), 58 deletions(-); areas: src-tauri/src, src/App.tsx, src/components, src/stores; top files: src-tauri/src/lib.rs, src/App.tsx, src/components/common/CommandPaletteButton.tsx.
- feat: enhance news feed functionality with AI and BC groups (b538971) - 9 files changed, 396 insertions(+), 65 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/025_news_feed_ai_sources.sql, migrations/026_news_feed_split_groups.sql, migrations/027_news_feed_add_anthropic.sql.
- feat: integrate news feed functionality (93f9821) - 17 files changed, 1250 insertions(+), 16 deletions(-); areas: migrations, package-lock.json, src-tauri/src, src/App.tsx; top files: migrations/023_news_feed.sql, migrations/024_news_feed_fix_sources.sql, src-tauri/src/db/migrations.rs.

### Fixes

- fix: improve settings button behavior and UI consistency (def5a21) - 4 files changed, 33 insertions(+), 32 deletions(-); areas: src/components, src/stores; top files: src/components/modals/SettingsButton.tsx, src/components/news/NewsFeedModal.tsx, src/stores/newsStore.ts.

### Refactoring

- refactor: update setup scripts and enhance CLI engine options (a5c3e57) - 10 files changed, 58 insertions(+), 18 deletions(-); areas: AGENTS.md, scripts, setup.bat, setup.sh; top files: AGENTS.md, scripts/setup.bat, scripts/setup.sh.
- refactor: simplify SQL migration inclusion in database migrations (8f73fa4) - 1 file changed, 34 insertions(+), 30 deletions(-); areas: src-tauri/src; top files: src-tauri/src/db/migrations.rs.
- refactor: streamline documentation and enhance agent guidelines (e3a36d6) - 12 files changed, 741 insertions(+), 1867 deletions(-); areas: AGENTS.md, README.md, docs; top files: AGENTS.md, README.md, docs/AGENTS.md.
- refactor: remove sync verification feature and related settings (8ca8b1a) - 12 files changed, 5 insertions(+), 1349 deletions(-); areas: migrations, scripts, src/components, src/services; top files: migrations/015_auto_sync_settings.sql, migrations/017_sync_verification.sql, scripts/synergy/synergy-worklogs-scraper.mjs.

### Documentation

- Update documentation for development commands and architecture details (ec4d437) - 4 files changed, 152 insertions(+), 30 deletions(-); areas: docs; top files: docs/AGENTS.md, docs/CLAUDE.md, docs/FEATURES_DETAILED.md.

### Build & Release

- release: v0.1.6 (d6eb8fc) - 5 files changed, 44 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.

### Other Changes

- Update agents md (822ff71) - 1 file changed, 321 insertions(+), 120 deletions(-); areas: AGENTS.md; top files: AGENTS.md.

## [0.1.5] - 2026-02-06

### Release Scope

- Commit range: v0.1.4..v0.1.5
- Commits in release: 1

### Build & Release

- release: v0.1.5 (29d1123) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.

## [0.1.4] - 2026-02-06

### Release Scope

- Commit range: v0.1.3..v0.1.4
- Commits in release: 2

### Build & Release

- chore: sync Cargo.lock for v0.1.4 (5f56182) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: src-tauri/Cargo.lock; top files: src-tauri/Cargo.lock.
- release: v0.1.4 (cb42054) - 8 files changed, 52 insertions(+), 20 deletions(-); areas: .github, docs, package.json, src-tauri/Cargo.toml; top files: .github/workflows/release.yml, docs/CLAUDE.md, package.json.

## [0.1.3] - 2026-02-06

### Release Scope

- Commit range: v0.1.2..v0.1.3
- Commits in release: 3

### Features

- feat: add GitHub CLI commands to settings for enhanced functionality (4880cb3) - 1 file changed, 6 insertions(+), 1 deletion(-); areas: .claude; top files: .claude/settings.local.json.

### Build & Release

- release: v0.1.3 (ef805a2) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.
- chore: update version to 0.1.2 and enhance app metadata (ba389bb) - 9 files changed, 319 insertions(+), 6 deletions(-); areas: package-lock.json, src-tauri/Cargo.lock, src/App.tsx, src/components; top files: src/App.tsx, src/components/common/UpdateBanner.tsx, src/components/modals/AboutButton.tsx.

## [0.1.2] - 2026-02-06

### Release Scope

- Commit range: v0.1.1..v0.1.2
- Commits in release: 1

### Build & Release

- release: enforce version consistency and prepare v0.1.2 (8fc6bcc) - 5 files changed, 67 insertions(+), 3 deletions(-); areas: .github, docs, package.json, src-tauri/Cargo.toml; top files: .github/workflows/release.yml, docs/release-versioning.md, package.json.

## [0.1.1] - 2026-02-06

### Release Scope

- Commit range: v0.1.0..v0.1.1
- Commits in release: 3

### Features

- feat: add internal remarks field to work log entries and related components (ddfc4e6) - 36 files changed, 531 insertions(+), 73 deletions(-); areas: .github, migrations, package-lock.json, scripts; top files: .github/workflows/release.yml, migrations/022_work_log_internal_remarks.sql, scripts/synergy/synergy-push.mjs.
- feat: Update README and CLAUDE documentation for installation and auto-updater (4fa528c) - 4 files changed, 162 insertions(+), 72 deletions(-); areas: README.md, docs, src-tauri/Cargo.lock; top files: README.md, docs/CLAUDE.md.

### Refactoring

- refactor: Update synergy push method to prioritize API over Playwright (eecfff7) - 5 files changed, 41 insertions(+), 38 deletions(-); areas: src/components, src/stores; top files: src/components/automation/BackgroundTasksPanel.tsx, src/components/modals/SettingsButton.tsx, src/components/modals/SetupWizardModal.tsx.

## [0.1.0] - 2026-02-05

### Release Scope

- Commit range: v0.1..v0.1.0
- Commits in release: 0

## [0.1] - 2026-02-28

### Release Scope

- Commit range: v0.1 (initial history)
- Commits in release: 355

### Features

- feat(02-03): add AI Provider section to LLM tab in SettingsButton (ff07ba5) - 1 file changed, 444 insertions(+), 288 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- feat(02-01): branch llmService.ts on llmMode for API vs CLI dispatch (5ba116a) - 1 file changed, 25 insertions(+); areas: src/services; top files: src/services/llm/llmService.ts.
- feat(02-01): add LlmMode/LlmApiProvider types and llm fields to settingsStore (f13ba7e) - 4 files changed, 173 insertions(+), 7 deletions(-); areas: .planning, src/stores; top files: .planning/ROADMAP.md, .planning/STATE.md, .planning/phases/02-llm-provider-infrastructure/02-02-SUMMARY.md.
- feat(02-02): register invoke_llm_api in lib.rs invoke_handler (2da21e2) - 1 file changed, 1 insertion(+); areas: src-tauri/src; top files: src-tauri/src/lib.rs.
- feat(02-04): add Zod schema validation to parseTableSuggestions (a6329aa) - 3 files changed, 44 insertions(+), 23 deletions(-); areas: package-lock.json, package.json, src/features; top files: package.json, src/features/worklog/services/bulkImport/cliService.ts.
- feat(02-02): implement invoke_llm_api in commands/ai.rs (223fbb9) - 1 file changed, 132 insertions(+); areas: src-tauri/src; top files: src-tauri/src/commands/ai.rs.
- feat(DiffViewer, ReviewPanel): implement build history filtering and pagination controls (41e92aa) - 5 files changed, 351 insertions(+), 31 deletions(-); areas: src/features; top files: src/features/devops/components/BuildHistoryControls.tsx, src/features/devops/components/DiffViewer.tsx, src/features/devops/components/ReviewPanel.tsx.
- feat(01-01): bind day buttons to mutationInFlight in DayWidget (c14d448) - 2 files changed, 280 insertions(+), 180 deletions(-); areas: src/components; top files: src/components/app/WidgetRegistry.tsx, src/components/common/DayWidget.tsx.
- feat(01-01): promote dayMutationInFlight to reactive Zustand state (cb521a7) - 1 file changed, 19 insertions(+), 19 deletions(-); areas: src/stores; top files: src/stores/dayStore.ts.
- feat(01-04): add loading spinner and friendly error/retry UI to SynergyWorkflowPanel (99cb8a9) - 1 file changed, 22 insertions(+), 4 deletions(-); areas: src/features; top files: src/features/synergy/components/SynergyWorkflowPanel.tsx.
- feat(01-04): add auto-retry-once and friendly errors to fetchRss (1e2d98f) - 2 files changed, 31 insertions(+), 10 deletions(-); areas: src/features, src/stores; top files: src/features/worklog/components/BulkImportView.tsx, src/stores/useSynergyStore.ts.
- feat(01-03): rework BackupRestorePanel with file pickers, styled modal, English UI (04095d8) - 1 file changed, 110 insertions(+), 70 deletions(-); areas: src/components; top files: src/components/panels/BackupRestorePanel.tsx.
- feat(01-02): update workLogStore — soft-delete undo and filtered load (eb41450) - 1 file changed, 7 insertions(+), 3 deletions(-); areas: src/stores; top files: src/stores/workLogStore.ts.
- feat(01-03): add export_backup_to_path and prepare_restore_from_path Rust commands (9beef99) - 2 files changed, 46 insertions(+); areas: src-tauri/src; top files: src-tauri/src/db/backup.rs, src-tauri/src/lib.rs.
- feat(01-02): add migration 050 — is_deleted soft-delete column (d11e7db) - 2 files changed, 10 insertions(+); areas: migrations, src-tauri/src; top files: migrations/050_worklog_soft_delete.sql, src-tauri/src/db/migrations.rs.
- feat: add Playwright test report. (1ecfc9c) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: playwright-report; top files: playwright-report/index.html.
- feat(a11y): integrate accessibility reviewer prompt and fix high priority issues (39af9b9) - 6 files changed, 130 insertions(+), 1 deletion(-); areas: docs, src/components, src/features; top files: docs/prompts/README.md, docs/prompts/accessibility-reviewer-prompt.md, docs/prompts/runs/2026-02-28-accessibility-reviewer.md.
- feat: Implement codex CLI path resolution for Windows (e094e8f) - 14 files changed, 925 insertions(+), 19 deletions(-); areas: .claude, src-tauri/src; top files: .claude/skills/debug/SKILL.md, .claude/skills/docs/SKILL.md, .claude/skills/feature/SKILL.md.
- feat: Add preparation step for Tauri externalBin stub in Linux CI (40d7912) - 1 file changed, 6 insertions(+); areas: .github; top files: .github/workflows/ci.yml.
- feat: Add various generated test, lint, and type-check report and log files. (61d8297) - 22 files changed, 205 insertions(+), 5 deletions(-); areas: err.txt, errs.txt, fail_log.json, fail_log2.json; top files: err.txt, errs.txt, fail_log.json.
- feat: Add GitHub Actions workflow for automated releases and documentation for release versioning. (acc24fd) - 6 files changed, 20 insertions(+), 551 deletions(-); areas: .github, docs; top files: .github/workflows/release.yml, docs/release-versioning.md.
- feat: Add Playwright CI strategy and extract Tauri Mocks #40 (e85b277) - 13 files changed, 1307 insertions(+), 237 deletions(-); areas: .github, tests; top files: .github/workflows/ci.yml, tests/e2e/core.spec.ts, tests/e2e/fixtures/tauriMock.ts.
- feat: Add LLM-powered bulk import functionality and comprehensive application feature documentation. (a3416ab) - 5 files changed, 208 insertions(+), 71 deletions(-); areas: docs, src-tauri/src, src/services; top files: docs/CLAUDE.md, docs/FEATURES_DETAILED.md, src-tauri/src/lib.rs.
- feat: Introduce core application structure with new components, stores, services, and utilities for work logging, scheduling, DevOps, Synergy integration, and UI elements. (b8185f5) - 97 files changed, 2528 insertions(+), 1665 deletions(-); areas: .github, CHANGELOG.md, docs, index.html; top files: .github/skills/skill-lookup/SKILL.md, CHANGELOG.md, docs/product-architect-prompt.md.
- feat: support comma decimal separator in all time input forms (91cbe03) - 3 files changed, 11 insertions(+), 12 deletions(-); areas: src/components; top files: src/components/devops/BatchTimeLogDialog.tsx, src/components/worklog/WorkLogBlockDialog.tsx, src/components/worklog/WorkLogPanel.tsx.
- feat: Add core Tauri backend with AI CLI invocation and auto-updater integration. (005ab0f) - 2 files changed, 46 insertions(+), 3 deletions(-); areas: src-tauri/src, src/hooks; top files: src-tauri/src/lib.rs, src/hooks/useAutoUpdater.ts.
- feat(activity): add default emoji icons for categories (69daf16) - 3 files changed, 69 insertions(+), 4 deletions(-); areas: migrations, src-tauri/src, src/stores; top files: migrations/049_activity_icons_emoji_defaults.sql, src-tauri/src/db/migrations.rs, src/stores/activityStore.ts.
- feat: implement Synergy sync improvements (issue #15) (bb13e77) - 5 files changed, 336 insertions(+), 143 deletions(-); areas: src/components, src/services, src/stores; top files: src/components/modals/SettingsButton.tsx, src/services/database.ts, src/services/synergy/autoSync.ts.
- feat: add multiple notification sound options and fix rust backend compilation (ac1d117) - 7 files changed, 136 insertions(+), 76 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/045_notification_sound_setting.sql, src-tauri/src/db/migrations.rs, src/App.tsx.
- feat: move StatsHeaderBar to sidebar and stretch across 2 columns in wide mode (5ca7584) - 2 files changed, 12 insertions(+), 27 deletions(-); areas: src/App.tsx, src/stores; top files: src/App.tsx, src/stores/layoutStore.test.ts.
- feat: implement individual timeline item visibility and compact dashboard layout (75c516d) - 10 files changed, 469 insertions(+), 128 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/legacy/044_seed_devops_organizations_initial.sql, src-tauri/src/lib.rs, src/App.tsx.
- feat: add Synergy login link to settings and fix accidental truncation (7992351) - 1 file changed, 912 insertions(+), 1300 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- feat: hide timeline in minimalist mode (a631fe0) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: src/App.tsx; top files: src/App.tsx.
- feat: implement Minimalist Mode (DevOps + Synergy Calendar only) (09c2945) - 4 files changed, 379 insertions(+), 305 deletions(-); areas: src/App.tsx, src/components, src/stores; top files: src/App.tsx, src/components/modals/SettingsButton.tsx, src/components/worklog/WorkLogPanel.tsx.
- feat: restructure settings menu with sidebar navigation (308797b) - 1 file changed, 879 insertions(+), 1285 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- feat: enhance retro theme, add boot sequence UI, and fix widget visibility easter eggs (315d17c) - 6 files changed, 233 insertions(+), 25 deletions(-); areas: index.html, src/App.tsx, src/index.css, src/stores; top files: index.html, src/App.tsx, src/index.css.
- feat(ui): add retro-style notification sound for the retro theme (1f30e04) - 4 files changed, 71 insertions(+), 31 deletions(-); areas: src/App.tsx, src/components, src/hooks, src/utils; top files: src/App.tsx, src/components/modals/SettingsButton.tsx, src/hooks/useScheduledNotifications.ts.
- feat(llm): optimize gemini cli integration with auto model and yolo mode (f7628e5) - 9 files changed, 93 insertions(+), 49 deletions(-); areas: package-lock.json, package.json, src-tauri/src, src/components; top files: package.json, src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs.
- feat(llm): add gemini cli support and improve cli detection logic (6b462d4) - 5 files changed, 104 insertions(+), 7 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/lib.rs, src/components/modals/SettingsButton.tsx, src/components/modals/SetupWizardModal.tsx.
- feat(synergy): implement persistent session health indicator (issue #8) (e69e353) - 5 files changed, 145 insertions(+), 2 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/lib.rs, src-tauri/src/synergy_api.rs, src/components/common/IntegrationHealthIndicator.tsx.
- feat: Initialize Tauri backend for agent functionality and update Vite dependency. (497a968) - 2 files changed, 2 insertions(+), 15 deletions(-); areas: package-lock.json, package.json; top files: package.json.
- feat: Introduce Review Panel for generating feedback build prompts from selected comments and related code. (219041d) - 7 files changed, 113 insertions(+), 26 deletions(-); areas: migrations, src-tauri/src, src/components, src/stores; top files: migrations/043_devops_build_jobs_additional_prompt.sql, src-tauri/src/build_orchestrator.rs, src-tauri/src/db/migrations.rs.
- feat: Add core Tauri backend with AI CLI invocation and initial UI components for worklog, time tracking, and integrations. (c80ca2e) - 8 files changed, 1644 insertions(+), 16 deletions(-); areas: issue_content.html, src-tauri/src, src/components, src/services; top files: issue_content.html, src-tauri/src/lib.rs, src/components/devops/TimeLogDialog.tsx.
- feat: Implement AI code review functionality with LLM CLI integration and UI components for DevOps work items. (a8eac68) - 8 files changed, 778 insertions(+), 53 deletions(-); areas: src-tauri/src, src/components, src/services; top files: src-tauri/src/ai_review.rs, src-tauri/src/app_dependencies.rs, src-tauri/src/build_orchestrator.rs.
- feat: add WorkItemDetailModal component for displaying work item details and related actions. (067564f) - 1 file changed, 2 insertions(+), 1 deletion(-); areas: src/components; top files: src/components/devops/WorkItemDetailModal.tsx.
- feat: Introduce a comprehensive settings store and initial DevOps features, including AI review and build orchestration. (ae28888) - 5 files changed, 113 insertions(+), 4 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs, src/components/devops/DevOpsToolsModal.tsx.
- feat: Initialize Tauri application with Rust backend for CLI tool invocation and DevOps integration, including new HTML utilities. (aeea3f1) - 10 files changed, 530 insertions(+), 18 deletions(-); areas: package-lock.json, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml, src-tauri/src/lib.rs.
- feat: Implement AI code review functionality for DevOps builds with new store, backend module, and UI components. (b14ff4f) - 5 files changed, 143 insertions(+), 63 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/ai_review.rs, src/components/devops/ReviewPanel.tsx, src/components/devops/WorkItemDetailModal.tsx.
- feat: Implement build concurrency checks and improve CLI command handling in DevOps workflow (50bd5d8) - 4 files changed, 157 insertions(+), 63 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/build_orchestrator.rs, src/components/devops/WorkItemsPanel.tsx, src/stores/devopsBuildStore.ts.
- feat: Add WorkItemsPanel component and synergyStore for managing DevOps work items. (7b0e108) - 2 files changed, 342 insertions(+), 43 deletions(-); areas: src/components, src/stores; top files: src/components/devops/WorkItemsPanel.tsx, src/stores/synergyStore.ts.
- feat: Implement a build orchestration system to manage DevOps work item builds, CLI tool execution, and Git operations. (6b3bf59) - 5 files changed, 126 insertions(+), 100 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/build_orchestrator.rs, src-tauri/src/lib.rs, src/components/devops/DevOpsToolsModal.tsx.
- feat: Enhance CLI integration and DevOps build workflow (1d487a5) - 8 files changed, 895 insertions(+), 52 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs, src-tauri/src/lib.rs.
- feat(cursor): add dependency checks and improve CLI integration in DevOps settings (bb7fd65) - 7 files changed, 293 insertions(+), 174 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs, src-tauri/src/lib.rs.
- feat: enhance CLI engine descriptions and error handling (3ffcf8f) - 5 files changed, 160 insertions(+), 16 deletions(-); areas: src-tauri/src, src/components; top files: src-tauri/src/lib.rs, src/components/devops/DevOpsToolsModal.tsx, src/components/modals/SettingsButton.tsx.
- feat: enhance synchronization and error handling in autoSync and related stores (ca94f30) - 8 files changed, 131 insertions(+), 78 deletions(-); areas: src-tauri/src, src/hooks, src/services, src/stores; top files: src-tauri/src/synergy_api.rs, src/hooks/useAppBootstrap.ts, src/services/synergy/autoSync.ts.
- feat: enhance error handling and notifications in App component (779b4fd) - 20 files changed, 603 insertions(+), 105 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/040_worklog_audit_log.sql, migrations/041_worklog_batch_import_id.sql, src-tauri/src/db/migrations.rs.
- feat: add Git commit handling and unclean repository checks in DevOps build process (14e9c27) - 2 files changed, 178 insertions(+), 14 deletions(-); areas: src-tauri/src, src/stores; top files: src-tauri/src/outlook_synergy_import.rs, src/stores/devopsBuildStore.ts.
- feat: enhance DevOps tools and UI components (2487ba4) - 30 files changed, 1395 insertions(+), 449 deletions(-); areas: README.md, docs, package-lock.json, scripts; top files: README.md, docs/FEATURES_DETAILED.md, docs/release-versioning.md.
- feat: Implement new UI components for work logging, timers, and various modals, including Synergy integration. (a9de997) - 18 files changed, 4855 insertions(+), 4294 deletions(-); areas: package-lock.json, package.json, src/components; top files: package.json, src/components/common/ActivityList.tsx, src/components/common/Animations.tsx.
- feat: Add detailed product architect innovation plan and related documentation files. (0ffe998) - 3 files changed, 286 insertions(+); areas: docs; top files: docs/product-architect-prompt.md.
- feat: Implement automatic Synergy worklog synchronization with API and Playwright fallback, and add new backend services for AI review, AL search, and project scanning, alongside a plan for QA improvements. (9a75537) - 13 files changed, 765 insertions(+), 272 deletions(-); areas: docs, package.json, src-tauri/src, src/services; top files: docs/qa-engineer-prompt.md, package.json, src-tauri/src/ai_review.rs.
- feat: Add workflow detail caching and retrieval functions in WorkLogCalendar (2ff9558) - 1 file changed, 198 insertions(+), 60 deletions(-); areas: src/components; top files: src/components/worklog/WorkLogCalendar.tsx.
- feat: Implement feedback selection and build prompt features (43dc8f3) - 9 files changed, 615 insertions(+), 158 deletions(-); areas: src/components, src/services, src/stores; top files: src/components/devops/CommentsModal.tsx, src/components/devops/DevOpsToolsModal.tsx, src/components/devops/ReviewPanel.tsx.
- feat: Enhance DevOps build process with custom branch support and AI build options (9386d8c) - 17 files changed, 567 insertions(+), 53 deletions(-); areas: migrations, src-tauri/src, src/components, src/hooks; top files: migrations/039_devops_build_jobs_starting_branch.sql, src-tauri/src/build_orchestrator.rs, src-tauri/src/db/migrations.rs.
- feat: enhance concurrency handling in runWithConcurrencyLimit to return failures alongside results (a7c850e) - 22 files changed, 1008 insertions(+), 154 deletions(-); areas: scripts, src-tauri/src, src/App.tsx, src/components; top files: scripts/db/migration-smoke-test.mjs, src-tauri/src/background_tasks.rs, src-tauri/src/devops_api.rs.
- feat: QA review phase 1 - enhance App component with bootstrap error handling and UI feedback (a8534fa) - 35 files changed, 708 insertions(+), 811 deletions(-); areas: .github, AGENTS.md, docs, src-tauri/src; top files: .github/workflows/release.yml, AGENTS.md, docs/SYNERGY_OPEN_REGISTRATION_PATCH_REPORT.md.
- feat: add QA Audit Bug & Edge Case Report for Developer Companion (fc0e527) - 1 file changed, 231 insertions(+); areas: .cursor; top files: .cursor/plans/2026-02-11-qa-audit-bug-edge-case-report.md.
- feat: enhance WorkLogCalendar with loading state and animations (e3ad112) - 3 files changed, 43 insertions(+), 9 deletions(-); areas: src/components, tailwind.config.cjs; top files: src/components/worklog/WorkLogCalendar.tsx, src/components/worklog/WorkLogCalendarBlock.tsx, tailwind.config.cjs.
- feat: enhance DevOpsToolsModal and work item title detection (77b5fb8) - 3 files changed, 46 insertions(+), 3 deletions(-); areas: src/components, src/services; top files: src/components/devops/DevOpsToolsModal.tsx, src/services/devops/__tests__/workItemService.test.ts, src/services/devops/workItemService.ts.
- feat: update settings and enhance CLI model handling (b05c25d) - 15 files changed, 413 insertions(+), 146 deletions(-); areas: index.html, package-lock.json, src-tauri/src, src/App.tsx; top files: index.html, src-tauri/src/build_orchestrator.rs, src-tauri/src/lib.rs.
- feat: enhance work log and synergy integration (8c27657) - 45 files changed, 3518 insertions(+), 433 deletions(-); areas: docs, migrations, package-lock.json, src-tauri/src; top files: docs/FEATURES_DETAILED.md, docs/IMPROVEMENTS.md, docs/SYNERGY_OPEN_REGISTRATION_PATCH_REPORT.md.
- feat: implement weather proxy and enhance weather data fetching (5eda6c4) - 3 files changed, 161 insertions(+), 39 deletions(-); areas: src-tauri/src, src/services; top files: src-tauri/src/lib.rs, src-tauri/src/weather.rs, src/services/weather.ts.
- feat: enhance weather widget and modal with location settings and geocoding support (25f2c83) - 7 files changed, 605 insertions(+), 118 deletions(-); areas: migrations, package-lock.json, src-tauri/src, src/components; top files: migrations/037_weather_location_settings.sql, src-tauri/src/db/migrations.rs, src/components/common/WeatherWidget.tsx.
- feat: integrate local commit scanning and enhance work item link management (18f3e86) - 17 files changed, 1906 insertions(+), 119 deletions(-); areas: migrations, src-tauri/src, src/components, src/services; top files: migrations/036_devops_work_item_links.sql, src-tauri/src/al_search.rs, src-tauri/src/db/migrations.rs.
- feat: enhance security and sanitization across components (ca11c2f) - 16 files changed, 488 insertions(+), 119 deletions(-); areas: src-tauri/src, src/components, src/services, src/stores; top files: src-tauri/src/secure_storage.rs, src/components/devops/DevOpsToolsModal.tsx, src/components/devops/WorkItemDetailModal.tsx.
- feat: Implement upgrade work item filtering and enhance project mapping logic (d037c6b) - 8 files changed, 247 insertions(+), 41 deletions(-); areas: src/components, src/index.css, src/services, src/stores; top files: src/components/devops/WorkItemsPanel.tsx, src/index.css, src/services/devops/__tests__/projectMappingKey.test.ts.
- feat: Update button styles for improved UI consistency and accessibility (a0dbbdf) - 6 files changed, 17 insertions(+), 11 deletions(-); areas: src/components, src/utils; top files: src/components/devops/BuildAnalyticsPanel.tsx, src/components/devops/DevOpsToolsModal.tsx, src/components/devops/WorkItemDetailModal.tsx.
- feat: Enhance UI settings with density modes, reduced motion toggle, and date/time preferences (3454938) - 14 files changed, 914 insertions(+), 37 deletions(-); areas: src/components, src/hooks, src/index.css, src/stores; top files: src/components/common/Toast.tsx, src/components/modals/SettingsButton.tsx, src/components/worklog/WorkLogBlockDialog.tsx.
- feat: add retro theme option and update theme handling logic (e089d94) - 4 files changed, 261 insertions(+), 4 deletions(-); areas: src/components, src/hooks, src/index.css, src/stores; top files: src/components/modals/SettingsButton.tsx, src/hooks/useApplyTheme.ts, src/index.css.
- feat: add UI theme customization and improve component styling (a323251) - 18 files changed, 320 insertions(+), 156 deletions(-); areas: package-lock.json, src/components, src/hooks, src/stores; top files: src/components/calendar/FullscreenCalendarModal.tsx, src/components/devops/BatchTimeLogDialog.tsx, src/components/devops/BuildDashboard.tsx.
- feat: add comprehensive documentation for Developer Companion (2fce494) - 3 files changed, 523 insertions(+); areas: docs; top files: docs/wiki/Home.md, docs/wiki/Installation.md, docs/wiki/Settings.md.
- feat: implement edge case hardening plan for security improvements (7b7379d) - 13 files changed, 520 insertions(+), 19 deletions(-); areas: package-lock.json, src-tauri/src, src/components, src/services; top files: src-tauri/src/devops_api.rs, src-tauri/src/lib.rs, src/components/scrapers/RssFeedTestPanel.tsx.
- feat: integrate Outlook tool availability check and enhance settings management (58f8818) - 4 files changed, 333 insertions(+), 47 deletions(-); areas: src-tauri/src, src/components; top files: src-tauri/src/lib.rs, src-tauri/src/outlook_synergy_import.rs, src/components/modals/SettingsButton.tsx.
- feat: add news summary settings and migration support (bbcea00) - 7 files changed, 468 insertions(+), 82 deletions(-); areas: AGENTS.md, migrations, src-tauri/src, src/components; top files: AGENTS.md, migrations/035_news_summary_settings.sql, src-tauri/src/db/migrations.rs.
- feat: enhance AboutButton with current version notes and improved UI (300db4f) - 4 files changed, 129 insertions(+), 17 deletions(-); areas: src-tauri/src, src/components; top files: src-tauri/src/ai_review.rs, src-tauri/src/al_compiler.rs, src-tauri/src/build_orchestrator.rs.
- feat: add customer ID resolution by code in Synergy API (658ed5d) - 5 files changed, 185 insertions(+), 3 deletions(-); areas: package-lock.json, src-tauri/src, src/components, src/services; top files: src-tauri/src/lib.rs, src-tauri/src/synergy_api.rs, src/components/modals/WeekOverviewModal.tsx.
- feat: standardize language and improve English consistency across the application (4d0008f) - 24 files changed, 145 insertions(+), 133 deletions(-); areas: AGENTS.md, src/App.tsx, src/components, src/services; top files: AGENTS.md, src/App.tsx, src/components/modals/SetupWizardModal.tsx.
- feat: enhance visibility-aware intervals across components (f9e7dbf) - 25 files changed, 430 insertions(+), 248 deletions(-); areas: scripts, src-tauri/src, src/components, src/hooks; top files: scripts/synergy/synergy-auth.mjs, src-tauri/src/al_compiler.rs, src-tauri/src/git_workflow.rs.
- feat: enhance scraper components with progress tracking and state management (a7db3bc) - 14 files changed, 864 insertions(+), 1327 deletions(-); areas: src-tauri/NS - New Sales, src-tauri/src, src/components, src/hooks; top files: src-tauri/NS - New Sales/Cod50037.NSNewSalesMgt.al, src-tauri/NS - New Sales/Enum50004.NSDocumentType.al, src-tauri/NS - New Sales/Pag50025.NSNewSalesTypes.al.
- feat: enhance scraper progress tracking and estimation (d3bee7e) - 5 files changed, 380 insertions(+), 42 deletions(-); areas: scripts, src-tauri/src, src/components; top files: scripts/synergy/synergy-customers-scraper.mjs, scripts/synergy/synergy-deliverables-scraper.mjs, scripts/synergy/synergy-projects-scraper.mjs.
- feat: enhance DevOps tools with state change notifications and work item logging (c2946f1) - 16 files changed, 1926 insertions(+), 113 deletions(-); areas: src-tauri/src, src/components, src/services, src/stores; top files: src-tauri/src/al_search.rs, src-tauri/src/lib.rs, src/components/devops/BatchTimeLogDialog.tsx.
- feat: enhance BuildDashboard and DevOps tools with inline commenting and navigation (491c162) - 15 files changed, 2455 insertions(+), 119 deletions(-); areas: src/components, src/services, src/stores; top files: src/components/devops/BuildDashboard.tsx, src/components/devops/DevOpsToolsModal.tsx, src/components/devops/DiffViewer.tsx.
- feat: enhance BuildDashboard and DevOps tools with new features (91bee76) - 15 files changed, 1936 insertions(+), 277 deletions(-); areas: src-tauri/NS - New Sales, src-tauri/src, src/components, src/stores; top files: src-tauri/NS - New Sales/Cod50037.NSNewSalesMgt.al, src-tauri/NS - New Sales/Enum50004.NSDocumentType.al, src-tauri/NS - New Sales/Pag50025.NSNewSalesTypes.al.
- feat: enhance WorkItemsPanel with organization selection and sorting features (6409f9f) - 10 files changed, 602 insertions(+), 494 deletions(-); areas: src-tauri/src, src/components, src/stores; top files: src-tauri/src/build_orchestrator.rs, src/components/devops/BuildAnalyticsPanel.tsx, src/components/devops/BuildDashboard.tsx.
- feat: enhance DevOps tools integration and UI improvements (88b42da) - 5 files changed, 98 insertions(+), 52 deletions(-); areas: src/App.tsx, src/components; top files: src/App.tsx, src/components/common/CommandPalette.tsx, src/components/devops/DevOpsToolsModal.tsx.
- feat: enhance DevOps integration with automatic time logging and project mapping (817af6a) - 38 files changed, 5491 insertions(+), 132 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/033_devops_synergy_mapping.sql, migrations/034_devops_build_jobs_add_columns.sql, src-tauri/src/ai_review.rs.
- feat: implement DevOps integration and settings management (4b0d130) - 26 files changed, 5086 insertions(+), 15 deletions(-); areas: migrations, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src; top files: migrations/030_devops_integration.sql, migrations/031_devops_builds.sql, migrations/032_devops_phase1_2_extensions.sql.
- feat: integrate synergy URL handling across components (a5e6266) - 6 files changed, 19 insertions(+), 15 deletions(-); areas: src/components; top files: src/components/common/UpdateBanner.tsx, src/components/modals/AboutButton.tsx, src/components/news/NewsArticleCard.tsx.
- feat: integrate synergy project and customer selection in TodoPanel (c8593ab) - 5 files changed, 191 insertions(+), 36 deletions(-); areas: migrations, src-tauri/src, src/components, src/stores; top files: migrations/029_todo_synergy_lookup.sql, src-tauri/src/db/migrations.rs, src/components/panels/TodoPanel.tsx.
- feat: enhance user experience with new features and UI improvements (5b4c433) - 37 files changed, 2002 insertions(+), 149 deletions(-); areas: README.md, docs, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: README.md, docs/FEATURES_DETAILED.md, docs/PRESENTATION_GUIDE.md.
- feat: enhance audio state management during track transitions (165e680) - 1 file changed, 114 insertions(+), 5 deletions(-); areas: src-tauri/src; top files: src-tauri/src/youtube_music.rs.
- feat: add Vitest support and enhance settings with notification grace period (7227bc6) - 17 files changed, 1062 insertions(+), 99 deletions(-); areas: migrations, package-lock.json, package.json, src/App.tsx; top files: migrations/015_auto_sync_settings.sql, migrations/017_sync_verification.sql, package.json.
- feat: add SettingsGroup component to enhance settings UI organization (ada0374) - 1 file changed, 683 insertions(+), 540 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- feat: add support for OpenAI Codex CLI and enhance settings UI (f01f945) - 23 files changed, 3119 insertions(+), 256 deletions(-); areas: migrations, package-lock.json, package.json, src-tauri/src; top files: migrations/028_news_article_summaries.sql, package.json, src-tauri/src/db/migrations.rs.
- feat: enhance error handling and JSON parsing across components (f2e986c) - 20 files changed, 1016 insertions(+), 109 deletions(-); areas: src-tauri/src, src/components, src/main.tsx, src/services; top files: src-tauri/src/background_tasks.rs, src-tauri/src/lib.rs, src/components/common/ErrorBoundary.tsx.
- feat: enhance button titles for improved user experience (1c40c01) - 12 files changed, 305 insertions(+), 58 deletions(-); areas: src-tauri/src, src/App.tsx, src/components, src/stores; top files: src-tauri/src/lib.rs, src/App.tsx, src/components/common/CommandPaletteButton.tsx.
- feat: enhance news feed functionality with AI and BC groups (b538971) - 9 files changed, 396 insertions(+), 65 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/025_news_feed_ai_sources.sql, migrations/026_news_feed_split_groups.sql, migrations/027_news_feed_add_anthropic.sql.
- feat: integrate news feed functionality (93f9821) - 17 files changed, 1250 insertions(+), 16 deletions(-); areas: migrations, package-lock.json, src-tauri/src, src/App.tsx; top files: migrations/023_news_feed.sql, migrations/024_news_feed_fix_sources.sql, src-tauri/src/db/migrations.rs.
- feat: add GitHub CLI commands to settings for enhanced functionality (4880cb3) - 1 file changed, 6 insertions(+), 1 deletion(-); areas: .claude; top files: .claude/settings.local.json.
- feat: add internal remarks field to work log entries and related components (ddfc4e6) - 36 files changed, 531 insertions(+), 73 deletions(-); areas: .github, migrations, package-lock.json, scripts; top files: .github/workflows/release.yml, migrations/022_work_log_internal_remarks.sql, scripts/synergy/synergy-push.mjs.
- feat: Update README and CLAUDE documentation for installation and auto-updater (4fa528c) - 4 files changed, 162 insertions(+), 72 deletions(-); areas: README.md, docs, src-tauri/Cargo.lock; top files: README.md, docs/CLAUDE.md.
- feat: Add auto-updater via GitHub Releases (fad18d5) - 11 files changed, 530 insertions(+), 5 deletions(-); areas: .github, package-lock.json, package.json, src-tauri/Cargo.lock; top files: .github/workflows/release.yml, package.json, src-tauri/Cargo.toml.
- feat: Integrate YouTube Music support and remove Spotify functionality (5e31dc2) - 12 files changed, 1217 insertions(+), 109 deletions(-); areas: src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src, src/App.tsx; top files: src-tauri/Cargo.toml, src-tauri/src/lib.rs, src-tauri/src/youtube_music.rs.
- feat: Add web session push method for Synergy integration (fcaa09d) - 13 files changed, 2684 insertions(+), 102 deletions(-); areas: docs, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src; top files: docs/synergy-web-session-push-progress.md, src-tauri/Cargo.toml, src-tauri/src/lib.rs.
- feat: Add support for conditional display of deliverable fields in worklog components (255aaf6) - 16 files changed, 1122 insertions(+), 150 deletions(-); areas: scripts, src-tauri/src, src/components, src/services; top files: scripts/synergy/synergy-push.mjs, src-tauri/src/lib.rs, src-tauri/src/synergy_api.rs.
- feat: Add Synergy API push integration (9de3eaa) - 17 files changed, 1699 insertions(+), 8 deletions(-); areas: migrations, src-tauri/src, src/components, src/services; top files: migrations/020_synergy_api_push_settings.sql, migrations/021_synergy_user_email.sql, src-tauri/src/db/migrations.rs.
- feat: add bulk import functionality for worklog entries (71fb440) - 15 files changed, 2079 insertions(+), 107 deletions(-); areas: migrations, src-tauri/src, src/components, src/services; top files: migrations/019_bulk_import_settings.sql, src-tauri/src/db/migrations.rs, src-tauri/src/lib.rs.
- feat(worklog): prevent drag/click handlers from firing on linked workflow button (5fe6fd8) - 1 file changed, 8 insertions(+); areas: src/components; top files: src/components/worklog/WorkLogCalendarBlock.tsx.
- feat(timers): implement multiple timers functionality in WorkLogPanel (5c19ce5) - 22 files changed, 1573 insertions(+), 44 deletions(-); areas: AGENTS.md, docs, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: AGENTS.md, docs/PLAN_MULTIPLE_TIMERS.md, src-tauri/Cargo.toml.
- feat(synergy): enhance Synergy login handling and update related scripts fix(synergy): correct script paths in error messages fix(synergy): improve session validation logic in worklog panel refactor(setupWizard): streamline Synergy login process and UI updates (0a7f438) - 13 files changed, 343 insertions(+), 56 deletions(-); areas: package-lock.json, scripts, src-tauri/src, src/components; top files: scripts/dev/sync-synergy-assets.mjs, scripts/synergy/discover-synergy-rss.mjs, scripts/synergy/synergy-auth.mjs.
- feat(worklog): add legend visibility for worklog and workflow items (366a8bd) - 2 files changed, 203 insertions(+), 27 deletions(-); areas: src/components; top files: src/components/worklog/WorkLogCalendar.tsx, src/components/worklog/WorkLogCalendarBlock.tsx.
- feat(synergy): implement synergy import, scraper, and Playwright integration (f3e6d58) - 70 files changed, 9040 insertions(+), 26953 deletions(-); areas: .gitignore, scripts, src/components, src/services; top files: .gitignore, scripts/dev/sync-synergy-assets.mjs, scripts/synergy-calendar-week-export.mjs.
- feat: add detailed presentation guide for Developer Companion (f02e597) - 2 files changed, 627 insertions(+); areas: docs; top files: docs/FEATURES_DETAILED.md, docs/PRESENTATION_GUIDE.md.
- feat: add synergyVerifiedAt field to work log entries and improve workflow item visibility logic (f3b0a7b) - 4 files changed, 3 insertions(+), 452 deletions(-); areas: ROOT_STRUCTURE.md, STRUCTURE.md, src/components, src/stores; top files: ROOT_STRUCTURE.md, STRUCTURE.md, src/components/worklog/WorkLogCalendar.tsx.
- feat: add archive filtering functionality to WorkLogPanel component (3f1a014) - 1 file changed, 365 insertions(+), 2 deletions(-); areas: src/components; top files: src/components/worklog/WorkLogPanel.tsx.
- feat: add BackgroundTasksPanel component for managing background tasks and scrapers (d980c5f) - 34 files changed, 2702 insertions(+), 55 deletions(-); areas: README.md, docs, migrations, src-tauri/Cargo.lock; top files: README.md, docs/CLAUDE.md, migrations/015_auto_sync_settings.sql.
- feat: add WorkLogTemplateSelector component with template management functionality (8b2d30c) - 87 files changed, 530 insertions(+), 8954 deletions(-); areas: .gitignore, AGENTS.md, CLAUDE.md, ROOT_STRUCTURE.md; top files: .gitignore, AGENTS.md, CLAUDE.md.
- feat: add autostart functionality and portable distribution option (760d291) - 15 files changed, 832 insertions(+), 10 deletions(-); areas: migrations, package-lock.json, package.json, scripts; top files: migrations/014_autostart_setting.sql, package.json, scripts/build-installer.bat.
- feat: implement worklog templates feature (63249fc) - 9 files changed, 947 insertions(+), 4 deletions(-); areas: CLAUDE.md, README.md, migrations, src/components; top files: CLAUDE.md, README.md, migrations/013_worklog_templates.sql.
- feat: Implement Command Palette with various commands and hotkeys (151400e) - 16 files changed, 1258 insertions(+), 30 deletions(-); areas: CLAUDE.md, IMPROVEMENTS.md, README.md, package-lock.json; top files: CLAUDE.md, IMPROVEMENTS.md, README.md.
- feat: add comprehensive improvement proposals for Developer Companion, focusing on LLM integration, UI/UX enhancements, automation, and technical architecture (99078f4) - 1 file changed, 357 insertions(+); areas: IMPROVEMENTS.md; top files: IMPROVEMENTS.md.
- feat: add CLAUDE.md for project guidance and command reference (086bdb0) - 1 file changed, 209 insertions(+); areas: CLAUDE.md; top files: CLAUDE.md.
- feat: add RSS discovery and testing panels for Synergy integration (06abc20) - 10 files changed, 1902 insertions(+), 2 deletions(-); areas: scripts, src-tauri/src, src/components, src/services; top files: scripts/discover-synergy-rss.mjs, scripts/test-synergy-rss-feeds.mjs, src-tauri/src/lib.rs.
- feat: add export and synergy tools components with modals for enhanced functionality (abfac35) - 30 files changed, 2301 insertions(+), 490 deletions(-); areas: DELIVERABLES_SCRAPER_PROGRESS.md, PROJECT_PLAN.md, scripts, src-tauri/src; top files: DELIVERABLES_SCRAPER_PROGRESS.md, PROJECT_PLAN.md, scripts/synergy-auth.mjs.
- feat: enhance WorkLogBlockDialog with flexible duration input parsing and validation (c6958e9) - 1 file changed, 135 insertions(+), 75 deletions(-); areas: src/components; top files: src/components/WorkLogBlockDialog.tsx.
- feat: implement Synergy RSS auto-fetch functionality with settings in the UI (fc9297d) - 4 files changed, 158 insertions(+), 3 deletions(-); areas: src/App.tsx, src/components, src/hooks, src/stores; top files: src/App.tsx, src/components/SettingsButton.tsx, src/hooks/useSynergyRssAutoFetch.ts.
- feat: update secure credential storage details in README and add dedicated section (76af180) - 1 file changed, 14 insertions(+), 2 deletions(-); areas: README.md; top files: README.md.
- feat: add secure credential storage and retrieval functionality (1709d30) - 4 files changed, 156 insertions(+), 68 deletions(-); areas: src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src, src/components; top files: src-tauri/Cargo.toml, src-tauri/src/lib.rs, src/components/SettingsButton.tsx.
- feat: add WorkLogCalendar component with drag-and-drop functionality for work log entries (6c128a4) - 14 files changed, 2232 insertions(+), 17 deletions(-); areas: package-lock.json, src/App.tsx, src/components, src/stores; top files: src/App.tsx, src/components/CalendarButton.tsx, src/components/FullscreenCalendarModal.tsx.
- feat: add synergy workflow panel and related functionality (fc16e8f) - 14 files changed, 2002 insertions(+), 17 deletions(-); areas: migrations, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src; top files: migrations/011_synergy_workflow_items.sql, src-tauri/Cargo.toml, src-tauri/src/lib.rs.
- feat: switch browser from Chromium to Firefox in scraping scripts (28a2853) - 8 files changed, 21 insertions(+), 14 deletions(-); areas: package-lock.json, scripts; top files: scripts/synergy-auth.mjs, scripts/synergy-customers-scraper.mjs, scripts/synergy-deliverables-scraper.mjs.
- feat: implement migration for work log sync status and update database schema (eb51fed) - 11 files changed, 492 insertions(+), 208 deletions(-); areas: apply-migration-010.bat, migrations, scripts, src/components; top files: apply-migration-010.bat, migrations/010_work_log_sync_status.sql, scripts/apply-migration-010.mjs.
- feat: add synergy projects and customers scrapers (d773acf) - 18 files changed, 36754 insertions(+), 15 deletions(-); areas: migrations, package-lock.json, package.json, scripts; top files: migrations/009_work_log_deliverables.sql, package.json, scripts/synergy-customers-scraper.mjs.
- feat: implement secure storage for Synergy credentials and enhance settings management (9042d0e) - 12 files changed, 217 insertions(+), 32 deletions(-); areas: AGENTS.md, README.md, setup.bat, setup.sh; top files: AGENTS.md, README.md, setup.bat.
- feat: enhance Synergy integration with new commands and add notification plugin (2e3e967) - 6 files changed, 63 insertions(+), 37 deletions(-); areas: AGENTS.md, package.json, scripts; top files: AGENTS.md, package.json, scripts/tauri-fast.mjs.
- feat: update Tauri script for improved Visual Studio integration and modify package.json for script execution (e4bbe9f) - 4 files changed, 127 insertions(+), 2 deletions(-); areas: README.md, package-lock.json, package.json, scripts; top files: README.md, package.json, scripts/tauri.mjs.
- feat: integrate Playwright for Synergy automation and enhance settings management (7f02300) - 16 files changed, 1865 insertions(+), 34 deletions(-); areas: README.md, package-lock.json, package.json, scripts; top files: README.md, package.json, scripts/synergy-auth.mjs.
- feat: integrate Synergy functionality into work log and application bootstrap (6cd9892) - 21 files changed, 9959 insertions(+), 11417 deletions(-); areas: migrations, package.json, public, scripts; top files: migrations/006_synergy_integration.sql, migrations/007_synergy_customer_selection.sql, package.json.
- feat: enhance app functionality with new panels and work log improvements (75f40ed) - 17 files changed, 20469 insertions(+), 254 deletions(-); areas: src/App.tsx, src/components, src/hooks, src/stores; top files: src/App.tsx, src/components/DailyStatsPanel.tsx, src/components/ExportPanel.tsx.
- feat: enhance project plan and README with new features and setup instructions (c87cd5b) - 47 files changed, 2265 insertions(+), 274 deletions(-); areas: AGENTS.md, PROJECT_PLAN.md, README.md, migrations; top files: AGENTS.md, PROJECT_PLAN.md, README.md.
- feat: enhance notification settings and special day blocks management (98117c1) - 19 files changed, 1515 insertions(+), 111 deletions(-); areas: README.md, migrations, src-tauri/Cargo.toml, src-tauri/src; top files: README.md, migrations/003_special_blocks_and_notification_settings.sql, src-tauri/Cargo.toml.
- feat: implement work log and todo features with UI components (b3bd907) - 7 files changed, 566 insertions(+), 11 deletions(-); areas: README.md, src/App.tsx, src/components, src/stores; top files: README.md, src/App.tsx, src/components/TodoPanel.tsx.
- feat: add day management and wellness features (4e22fbd) - 25 files changed, 1777 insertions(+), 146 deletions(-); areas: .gitignore, README.md, migrations, package-lock.json; top files: .gitignore, README.md, migrations/002_day_management_and_wellness.sql.
- feat: initialize Tauri application with SQLite integration and basic todo functionality (18dd4a8) - 52 files changed, 9349 insertions(+), 8 deletions(-); areas: .gitignore, PROJECT_PLAN.md, README.md, index.html; top files: .gitignore, PROJECT_PLAN.md, README.md.

### Fixes

- fix(02-03): fix active button colors in retro theme (489ad0a) - 2 files changed, 14 insertions(+), 3 deletions(-); areas: src/components, src/styles; top files: src/components/modals/SettingsButton.tsx, src/styles/themes/retro.css.
- fix(01): revise 01-02 plan — add undo button task and migration header comment (b94a144) - 1 file changed, 81 insertions(+), 10 deletions(-); areas: .planning; top files: .planning/phases/01-core-stabilization/01-02-PLAN.md.
- fix: resolve typecheck errors and reopen race condition (7bba81e) - 4 files changed, 183 insertions(+), 12 deletions(-); areas: docs, src/stores, src/utils; top files: docs/prompts/README.md, src/stores/dayStore.ts, src/utils/duration.ts.
- Fix-onboarding-retry-test-and-update-changelog (253966c) - 2 files changed, 29 insertions(+), 1 deletion(-); areas: CHANGELOG.md, tests; top files: CHANGELOG.md, tests/e2e/onboarding.spec.ts.
- fix(perf): profile and optimize bootstrap and devops flows (cd45ebf) - 17 files changed, 1462 insertions(+), 229 deletions(-); areas: .github, CHANGELOG.md, docs, src/App.tsx; top files: .github/workflows/ci.yml, .github/workflows/release.yml, CHANGELOG.md.
- fix(data-integrity): harden db restore and devops sync writes (3d99890) - 9 files changed, 1103 insertions(+), 226 deletions(-); areas: CHANGELOG.md, src-tauri/src, src/services, src/stores; top files: CHANGELOG.md, src-tauri/src/commands/devops.rs, src-tauri/src/commands/mod.rs.
- Fix cross-platform traversal detection in ai command tests (84519fc) - 1 file changed, 5 insertions(+); areas: src-tauri/src; top files: src-tauri/src/commands/ai.rs.
- fix(security): harden local file and URL boundaries (a1225fb) - 11 files changed, 1118 insertions(+), 30 deletions(-); areas: CHANGELOG.md, package-lock.json, package.json, src-tauri/src; top files: CHANGELOG.md, package.json, src-tauri/src/commands/ai.rs.
- fix(ui): translate special blocks panel to English (48ddb78) - 2 files changed, 12 insertions(+), 13 deletions(-); areas: CHANGELOG.md, src/components; top files: CHANGELOG.md, src/components/panels/SpecialBlocksPanel.tsx.
- Fix QA sync/timer regressions and add smoke tests (d28486c) - 12 files changed, 629 insertions(+), 82 deletions(-); areas: src/components, src/services, src/stores, tests; top files: src/components/worklog/WorkLogPanel.tsx, src/services/synergy/autoSync.test.ts, src/services/synergy/autoSync.ts.
- fix: Allow unused mutable variable in build_cli_command function (301a330) - 1 file changed, 2 insertions(+); areas: src-tauri/src; top files: src-tauri/src/ai_review.rs.
- fix: Update variable names for clarity and improve logging for missing weather data (53553cc) - 4 files changed, 86 insertions(+), 43 deletions(-); areas: src-tauri/src, src/components, src/services; top files: src-tauri/src/lib.rs, src-tauri/src/youtube_music.rs, src/components/worklog/WorkLogCalendar.tsx.
- fix: Add platform-specific stubs for cursor resolution functions on non-Windows OS (5b31041) - 3 files changed, 40 insertions(+), 2 deletions(-); areas: src-tauri/src; top files: src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs, src-tauri/src/lib.rs.
- fix: wrap unstable inline functions in useCallback/useMemo to clear React hook lint warnings (5fcaa2f) - 3 files changed, 24 insertions(+), 30 deletions(-); areas: src/components; top files: src/components/onboarding/GuidedTourOverlay.tsx, src/components/panels/TodoPanel.tsx, src/components/worklog/WorkLogCalendarBlock.tsx.
- fix: exclude tests/e2e from vitest collection to prevent Playwright spec conflicts (dd88460) - 1 file changed, 12 insertions(+), 4 deletions(-); areas: vite.config.ts; top files: vite.config.ts.
- fix: resolve Playwright dual-version conflict and useMemo hook lint warnings (4557322) - 5 files changed, 48 insertions(+), 21 deletions(-); areas: .github, src/components; top files: .github/workflows/ci.yml, src/components/devops/BuildDashboard.tsx, src/components/devops/DiffViewer.tsx.
- fix: resolve 10 npm audit vulnerabilities via minimatch override (dc67d6d) - 4 files changed, 45 insertions(+), 61 deletions(-); areas: eslint.config.js, package-lock.json, package.json, src/components; top files: eslint.config.js, package.json, src/components/common/Animations.tsx.
- fix: resolve CI failures - remove duplicate playwright package and split Animations.tsx (fd43d0e) - 4 files changed, 109 insertions(+), 92 deletions(-); areas: package.json, src/components; top files: package.json, src/components/common/Animations.tsx, src/components/common/animationVariants.ts.
- fix(automation): Resolve integrity and concurrency bugs identified in QA (ce29a17) - 7 files changed, 152 insertions(+), 80 deletions(-); areas: docs, src/services, src/stores; top files: docs/QA_REPORT.md, src/services/synergy/autoSync.ts, src/stores/activityStore.ts.
- fix(issues): Address issue 22 and 23 via parsing tweaks and prompt tmpfile (a2312a3) - 7 files changed, 155 insertions(+), 66 deletions(-); areas: src-tauri/src, src/components, src/services, src/stores; top files: src-tauri/src/lib.rs, src/components/worklog/BulkImportTable.tsx, src/components/worklog/WorkLogCalendar.tsx.
- fix(#25): resolve synergy API push 404 returning meaningless errors (49d9591) - 3 files changed, 59 insertions(+), 11 deletions(-); areas: src-tauri/src, src/services, src/stores; top files: src-tauri/src/synergy_api.rs, src/services/synergy/synergyApi.ts, src/stores/synergyStore.ts.
- Fix DevOps work item sync freeze and finalize DevOps settings updates (f446a93) - 7 files changed, 1065 insertions(+), 1129 deletions(-); areas: src/components, src/services, src/stores; top files: src/components/devops/DevOpsToolsModal.tsx, src/components/devops/WorkItemsPanel.tsx, src/components/modals/SettingsButton.tsx.
- Fix Synergy API push mode to avoid Playwright fallback (66c5413) - 3 files changed, 202 insertions(+), 66 deletions(-); areas: src/components, src/services; top files: src/components/worklog/WorkLogPanel.tsx, src/services/synergy/autoSync.test.ts, src/services/synergy/autoSync.ts.
- fix: resolve stale closure causing 'All entries already synced' on confirm push (9e1bf4a) - 1 file changed, 4 insertions(+), 2 deletions(-); areas: src/components; top files: src/components/worklog/WorkLogPanel.tsx.
- fix: make playNotificationBeep more robust for short retro sounds (6903d8b) - 1 file changed, 15 insertions(+), 8 deletions(-); areas: src/utils; top files: src/utils/sound.ts.
- fix: ensure priority and other missing columns exist regardless of migration state (20ae16f) - 1 file changed, 62 insertions(+), 86 deletions(-); areas: src/services; top files: src/services/database.ts.
- fix: ensure etag column exists on devops_work_items regardless of migration state (c601ee8) - 1 file changed, 8 insertions(+), 10 deletions(-); areas: src/services; top files: src/services/database.ts.
- fix: ensure synergy columns exist on devops_project_mappings regardless of migration state (43c26d8) - 2 files changed, 31 insertions(+), 15 deletions(-); areas: migrations, src/services; top files: migrations/044_seed_devops_organizations.sql, src/services/database.ts.
- fix: register migration 044 in Rust and ensure organizations are seeded and loaded during bootstrap (e6909f3) - 5 files changed, 21 insertions(+), 18 deletions(-); areas: src-tauri/src, src/App.tsx, src/hooks, src/services; top files: src-tauri/src/db/migrations.rs, src/App.tsx, src/hooks/useAppBootstrap.ts.
- fix: update seeded devops organizations to correct list (escbvba, cascade4nav, etc.) (40bde4f) - 3 files changed, 13 insertions(+), 4 deletions(-); areas: migrations, src/components, src/stores; top files: migrations/044_seed_devops_organizations.sql, src/components/devops/DevOpsToolsModal.tsx, src/stores/settingsStore.ts.
- fix: restore missing synergy login settings and re-add minimalist mode toggle (59f0581) - 1 file changed, 1300 insertions(+), 893 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- fix(synergy): resolve crash in push preview by fixing payload property names and hardening parser (8ab0e0c) - 2 files changed, 20 insertions(+), 20 deletions(-); areas: src/components; top files: src/components/synergy/SynergyPushPreviewModal.tsx, src/components/worklog/WorkLogPanel.tsx.
- fix(synergy): ensure all push actions go through the preview modal by refactoring push triggers (48f3031) - 5 files changed, 367 insertions(+), 15 deletions(-); areas: src-tauri/src, src/App.tsx, src/components, src/stores; top files: src-tauri/src/lib.rs, src/App.tsx, src/components/synergy/SynergyPushPreviewModal.tsx.
- fix(synergy): resolve trim error in login modal by using correct baseUrl and password retrieval (e20a395) - 4 files changed, 180 insertions(+), 2 deletions(-); areas: src/App.tsx, src/components, src/stores; top files: src/App.tsx, src/components/automation/SynergyLoginModal.tsx, src/components/common/IntegrationHealthIndicator.tsx.
- fix: introduce connection generation to resolve persistent database lock issues by forcing fresh connection pools. (794ce8a) - 4 files changed, 327 insertions(+); areas: .cursor; top files: .cursor/plans/2026-02-18-database-lock-stability.md, .cursor/plans/flexiblesidebar.md, .cursor/plans/implementation_plan.md.resolved.
- Fix Cursor CLI failure on Windows by injecting bundled ripgrep into PATH (32ee324) - 1 file changed, 55 insertions(+), 2 deletions(-); areas: src-tauri/src; top files: src-tauri/src/lib.rs.
- fix(db): add SQLite concurrency handling to prevent locked errors (0efa9cd) - 15 files changed, 609 insertions(+), 269 deletions(-); areas: docs, migrations, src-tauri/src, src/components; top files: docs/CLAUDE.md, docs/FEATURES_DETAILED.md, docs/release-versioning.md.
- fix: remove unnecessary cursor.cmd from Windows CLI candidates (8facb42) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: src-tauri/src; top files: src-tauri/src/lib.rs.
- fix: correct release notes URL to point to public updates repo (ee91d76) - 4 files changed, 146 insertions(+), 6 deletions(-); areas: .github, CHANGELOG.md, docs, src/hooks; top files: .github/workflows/release.yml, CHANGELOG.md, docs/release-versioning.md.
- fix: update release notes URL to point to updates repo (7af620f) - 1 file changed, 3 insertions(+), 2 deletions(-); areas: .github; top files: .github/workflows/release.yml.
- fix: improve settings button behavior and UI consistency (def5a21) - 4 files changed, 33 insertions(+), 32 deletions(-); areas: src/components, src/stores; top files: src/components/modals/SettingsButton.tsx, src/components/news/NewsFeedModal.tsx, src/stores/newsStore.ts.
- fix: Pin @tauri-apps npm packages to 2.9.x to match Rust crate versions (f58f3dd) - 2 files changed, 11 insertions(+), 11 deletions(-); areas: package-lock.json, package.json; top files: package.json.
- fix(synergy): use JavaScript approach for date/time fields when Playwright locator fails (56afd26) - 1 file changed, 89 insertions(+), 67 deletions(-); areas: scripts; top files: scripts/synergy/synergy-push.mjs.
- fix(synergy): fix time field input detection and add value verification (e2d151b) - 1 file changed, 1931 insertions(+); areas: scripts; top files: scripts/synergy/synergy-push.mjs.
- fix: correct code block formatting in README and remove outdated Synergy setup instructions (59de00a) - 1 file changed, 1 insertion(+), 22 deletions(-); areas: README.md; top files: README.md.

### Tests

- test(02): complete UAT - 8 passed, 0 issues (bad7f1e) - 1 file changed, 58 insertions(+); areas: .planning; top files: .planning/phases/02-llm-provider-infrastructure/02-UAT.md.
- test: expand phase 3 coverage and tune devops search (f1391ae) - 11 files changed, 557 insertions(+), 21 deletions(-); areas: CHANGELOG.md, src/features, src/stores, tests; top files: CHANGELOG.md, src/features/devops/components/WorkItemsPanel.tsx, src/stores/dayStore.test.ts.
- test(e2e): stabilize day ci flow and quarantine pause hang (1d14a60) - 3 files changed, 48 insertions(+), 26 deletions(-); areas: CHANGELOG.md, tests; top files: CHANGELOG.md, tests/e2e/day.spec.ts, tests/e2e/fixtures/pageUtils.ts.
- test(e2e): expand mock coverage and failure paths (5fa5025) - 16 files changed, 2686 insertions(+), 89 deletions(-); areas: CHANGELOG.md, tests; top files: CHANGELOG.md, tests/e2e/background-tasks.spec.ts, tests/e2e/command-palette.spec.ts.
- test(devops): update commit tracking expectations for atomic sync writes (352c941) - 1 file changed, 30 insertions(+), 5 deletions(-); areas: src/stores; top files: src/stores/__tests__/devopsStore.commitTracking.test.ts.
- test: Fix remaining flake in E2E tests for a11y tab navigation and worklog time input (d4db294) - 3 files changed, 35 insertions(+), 10 deletions(-); areas: tests; top files: tests/e2e/a11y.spec.ts, tests/e2e/fixtures/tauriMock.ts, tests/e2e/worklog.spec.ts.
- test: stabilize e2e start-day setup and tauri sql mock (50b4f9d) - 3 files changed, 29 insertions(+), 28 deletions(-); areas: tests; top files: tests/e2e/core.spec.ts, tests/e2e/fixtures/pageUtils.ts, tests/e2e/fixtures/tauriMock.ts.
- test: Implement E2E specs for Settings, Day Management, and Synergy (Phase 2-4) (2f4919b) - 17 files changed, 4963 insertions(+), 56 deletions(-); areas: tests; top files: tests/e2e/a11y.spec.ts, tests/e2e/core.spec.ts, tests/e2e/day.spec.ts.
- test: Implement Work Log CRUD and E2E Utilities (9317cd4) - 10 files changed, 137 insertions(+), 771 deletions(-); areas: docs, tests; top files: docs/E2E_TESTING_GUIDE.md, tests/e2e/fixtures/pageUtils.ts, tests/e2e/worklog.spec.ts.
- test: Fix Tauri mocking and E2E Playwright stability - Strengthened Tauri IPC mock in core.spec.ts to bypass required tauri checks - Mocked SQL metadata (PRAGMA, _sqlx_migrations) so database migration scripts don't hang - Disabled Setup Wizard and Guided Tour via mock DB entries and local storage injection - Accelerated tests by mocking the Synergy Artifact fetching phase and skipping network lookups - Fixed a duplicate main element ID (main-content) in App.tsx for more reliable Playwright locators (c99b835) - 6 files changed, 511 insertions(+), 9 deletions(-); areas: .gitignore, package-lock.json, package.json, playwright.config.ts; top files: .gitignore, package.json, playwright.config.ts.

### Refactoring

- refactor: clean up code formatting and improve readability in background_tasks, discovery, ai, and backup modules (6215c37) - 4 files changed, 165 insertions(+), 102 deletions(-); areas: src-tauri/src; top files: src-tauri/src/background_tasks.rs, src-tauri/src/cli/discovery.rs, src-tauri/src/commands/ai.rs.
- refactor(WorkLogCalendar): remove open hours calculation and related logic (c3a5074) - 1 file changed, 2 insertions(+), 20 deletions(-); areas: src/features; top files: src/features/worklog/components/WorkLogCalendar.tsx.
- Refactor Codex CLI path resolution on Windows and enhance error handling in Setup Wizard (6ac0eae) - 5 files changed, 79 insertions(+), 22 deletions(-); areas: src-tauri/src, src/components, tests; top files: src-tauri/src/cli/discovery.rs, src/components/modals/SetupWizardModal.tsx, tests/e2e/news-summaries.spec.ts.
- Refactor code structure and remove redundant code blocks for improved readability and maintainability (dcde626) - 71 files changed, 1929 insertions(+), 207 deletions(-); areas: src/App.tsx, src/components, src/features, src/stores; top files: src/App.tsx, src/components/app/DashboardGrid.tsx, src/components/app/GlobalModals.tsx.
- refactor: remove synergyWorkflowStore and add tests for useSynergyStore (f469c76) - 100 files changed, 1631 deletions(-); areas: src/components, src/features, src/hooks, src/services; top files: src/components/automation/SynergyLoginModal.tsx, src/components/devops/BatchTimeLogDialog.tsx, src/components/devops/BuildAnalyticsPanel.tsx.
- refactor: modularize CSS and implement theme variables (Phase 3) (1a220bc) - 5 files changed, 595 insertions(+), 911 deletions(-); areas: src/index.css, src/styles; top files: src/index.css, src/styles/base.css, src/styles/layout.css.
- refactor: modularize frontend and backend (Phase 1 & 2) (d7d702c) - 28 files changed, 4176 insertions(+), 4743 deletions(-); areas: src-tauri/Cargo.toml, src-tauri/src, src/App.tsx, src/components; top files: src-tauri/Cargo.toml, src-tauri/src/ai_review.rs, src-tauri/src/cli/discovery.rs.
- refactor: minor code cleanup in synergy components (43f41b6) - 2 files changed, 1 insertion(+), 2 deletions(-); areas: src/components, src/stores; top files: src/components/synergy/SynergyPushPreviewModal.tsx, src/stores/healthStore.ts.
- refactor(ui): consolidate current activity into DayTimeline (995f67f) - 8 files changed, 717 insertions(+), 204 deletions(-); areas: README.md, docs, src/App.tsx, src/components; top files: README.md, docs/FEATURES_DETAILED.md, docs/wiki/Home.md.
- refactor(dayStore): use upsert for start day logic (29cb8d0) - 1 file changed, 21 insertions(+), 20 deletions(-); areas: src/stores; top files: src/stores/dayStore.ts.
- refactor: replace custom JSON comment stripper with json_comments (3bf2a01) - 3 files changed, 11 insertions(+), 52 deletions(-); areas: src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src; top files: src-tauri/Cargo.toml, src-tauri/src/app_dependencies.rs.
- refactor: move dependency markdown generation to backend (83ed52b) - 6 files changed, 30 insertions(+), 61 deletions(-); areas: src-tauri/src, src/components, src/services, src/stores; top files: src-tauri/src/app_dependencies.rs, src/components/devops/ReviewPanel.tsx, src/components/devops/WorkItemDetailModal.tsx.
- Refactor and enhance error handling across various components (e9dd0fa) - 15 files changed, 409 insertions(+), 185 deletions(-); areas: package-lock.json, scripts, src-tauri/src, src/components; top files: scripts/dev/start.bat, scripts/dev/tauri-fast.mjs, src-tauri/src/background_tasks.rs.
- refactor: simplify release URL resolution in useAutoUpdater hook (9def06d) - 1 file changed, 11 deletions(-); areas: src/hooks; top files: src/hooks/useAutoUpdater.ts.
- refactor: update setup scripts and enhance CLI engine options (a5c3e57) - 10 files changed, 58 insertions(+), 18 deletions(-); areas: AGENTS.md, scripts, setup.bat, setup.sh; top files: AGENTS.md, scripts/setup.bat, scripts/setup.sh.
- refactor: simplify SQL migration inclusion in database migrations (8f73fa4) - 1 file changed, 34 insertions(+), 30 deletions(-); areas: src-tauri/src; top files: src-tauri/src/db/migrations.rs.
- refactor: streamline documentation and enhance agent guidelines (e3a36d6) - 12 files changed, 741 insertions(+), 1867 deletions(-); areas: AGENTS.md, README.md, docs; top files: AGENTS.md, README.md, docs/AGENTS.md.
- refactor: remove sync verification feature and related settings (8ca8b1a) - 12 files changed, 5 insertions(+), 1349 deletions(-); areas: migrations, scripts, src/components, src/services; top files: migrations/015_auto_sync_settings.sql, migrations/017_sync_verification.sql, scripts/synergy/synergy-worklogs-scraper.mjs.
- refactor: Update synergy push method to prioritize API over Playwright (eecfff7) - 5 files changed, 41 insertions(+), 38 deletions(-); areas: src/components, src/stores; top files: src/components/automation/BackgroundTasksPanel.tsx, src/components/modals/SettingsButton.tsx, src/components/modals/SetupWizardModal.tsx.
- Refactor scraper execution to use node sidecar and improve dependency management (152e5c5) - 22 files changed, 361 insertions(+), 1509 deletions(-); areas: .gitignore, scripts, src-tauri/build.rs, src-tauri/src; top files: .gitignore, scripts/build/build-installer.bat, scripts/build/build-portable.bat.
- refactor(worklog): improve WorkLogBlockDialog and WorkLogCalendar components (bcd62be) - 11 files changed, 2169 insertions(+), 235 deletions(-); areas: docs, scripts, src/components, src/stores; top files: docs/IMPROVEMENTS.md, scripts/discover-synergy-rss.mjs, scripts/synergy-calendar-week-export.mjs.
- Refactor Synergy Base URL handling across components and stores (16257ce) - 14 files changed, 81 insertions(+), 357 deletions(-); areas: src/App.tsx, src/components, src/hooks, src/stores; top files: src/App.tsx, src/components/CommandPalette.tsx, src/components/CustomersScraperPanel.tsx.
- Refactor code structure for improved readability and maintainability (a950297) - 16 files changed, 9955 insertions(+), 222 deletions(-); areas: fix-migrations.sql, migrations, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: fix-migrations.sql, migrations/010_work_log_sync_status.sql, migrations/012_synergy_workflow_realized_dates.sql.

### Documentation

- docs: add v0.1 milestone audit — tech_debt status, 5/5 requirements (b4ae0c9) - 1 file changed, 114 insertions(+); areas: .planning; top files: .planning/v0.1-MILESTONE-AUDIT.md.
- docs(phase-02): complete phase execution (c006a51) - 2 files changed, 224 insertions(+); areas: .planning; top files: .planning/STATE.md, .planning/phases/02-llm-provider-infrastructure/02-VERIFICATION.md.
- docs(02-03): complete AI Provider Settings UI plan — retro fix and final SUMMARY (0e33e1b) - 2 files changed, 43 insertions(+), 15 deletions(-); areas: .planning; top files: .planning/STATE.md, .planning/phases/02-llm-provider-infrastructure/02-03-SUMMARY.md.
- docs(02-03): complete AI Provider settings UI plan — SUMMARY and ROADMAP (46fd8ce) - 2 files changed, 206 insertions(+), 101 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/phases/02-llm-provider-infrastructure/02-03-SUMMARY.md.
- docs(02-01): complete LLM mode routing plan — settingsStore + llmService (f1d29cf) - 3 files changed, 88 insertions(+), 3 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/STATE.md, .planning/phases/02-llm-provider-infrastructure/02-01-SUMMARY.md.
- docs(02-04): complete Zod bulk import validation plan (7622119) - 3 files changed, 99 insertions(+), 32 deletions(-); areas: .planning, src/stores; top files: .planning/STATE.md, .planning/phases/02-llm-provider-infrastructure/02-04-SUMMARY.md, src/stores/settingsStore.ts.
- docs(02): create phase 2 plan — 4 plans in 2 waves (fc96d92) - 5 files changed, 1158 insertions(+), 95 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/phases/02-llm-provider-infrastructure/02-01-PLAN.md, .planning/phases/02-llm-provider-infrastructure/02-02-PLAN.md.
- docs(02): research phase llm-provider-infrastructure (167266b) - 1 file changed, 605 insertions(+); areas: .planning; top files: .planning/phases/02-llm-provider-infrastructure/02-RESEARCH.md.
- docs(02): capture phase context (d19cbe1) - 1 file changed, 97 insertions(+); areas: .planning; top files: .planning/phases/02-llm-provider-infrastructure/02-CONTEXT.md.
- docs(phase-01): complete phase execution (477919b) - 2 files changed, 178 insertions(+); areas: .planning; top files: .planning/STATE.md, .planning/phases/01-core-stabilization/01-VERIFICATION.md.
- docs(01-01): complete day state race condition plan — SUMMARY, STATE, ROADMAP, REQUIREMENTS (e2a7f1d) - 4 files changed, 193 insertions(+), 99 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/ROADMAP.md, .planning/STATE.md.
- docs(01-04): complete plan — Synergy RSS retry and friendly error UI (d795735) - 1 file changed, 114 insertions(+); areas: .planning; top files: .planning/phases/01-core-stabilization/01-04-SUMMARY.md.
- docs(01-03): complete backup/restore file-picker plan — SUMMARY, STATE, ROADMAP, REQUIREMENTS (f528477) - 4 files changed, 117 insertions(+), 18 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/ROADMAP.md, .planning/STATE.md.
- docs(01-02): complete worklog soft-delete plan — SUMMARY, STATE, ROADMAP (de8442d) - 4 files changed, 110 insertions(+), 13 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/ROADMAP.md, .planning/STATE.md.
- docs(01): create phase plan — 4 plans covering STBL-01 through STBL-05 (462d9b8) - 5 files changed, 966 insertions(+), 2 deletions(-); areas: .planning; top files: .planning/ROADMAP.md, .planning/phases/01-core-stabilization/01-01-PLAN.md, .planning/phases/01-core-stabilization/01-02-PLAN.md.
- docs(01): research phase 1 core stabilization (1962d1a) - 1 file changed, 598 insertions(+); areas: .planning; top files: .planning/phases/01-core-stabilization/01-RESEARCH.md.
- docs(01): capture phase context (6260315) - 1 file changed, 110 insertions(+); areas: .planning; top files: .planning/phases/01-core-stabilization/01-CONTEXT.md.
- docs: create roadmap (5 phases) (6dfc09d) - 3 files changed, 169 insertions(+), 16 deletions(-); areas: .planning; top files: .planning/REQUIREMENTS.md, .planning/ROADMAP.md, .planning/STATE.md.
- docs: define v1 requirements (cb4e98f) - 1 file changed, 90 insertions(+); areas: .planning; top files: .planning/REQUIREMENTS.md.
- docs: complete project research (f2d54a9) - 5 files changed, 1925 insertions(+); areas: .planning; top files: .planning/research/ARCHITECTURE.md, .planning/research/FEATURES.md, .planning/research/PITFALLS.md.
- docs: initialize project (606a11f) - 1 file changed, 79 insertions(+); areas: .planning; top files: .planning/PROJECT.md.
- docs: map existing codebase (eefe3fd) - 7 files changed, 1685 insertions(+); areas: .planning; top files: .planning/codebase/ARCHITECTURE.md, .planning/codebase/CONCERNS.md, .planning/codebase/CONVENTIONS.md.
- docs: update skill descriptions and remove allowed-tools for clarity test: enhance day management tests for pause, resume, end, and reopen functionality (ca1743a) - 12 files changed, 61 insertions(+), 12 deletions(-); areas: .claude, src/App.tsx, tests; top files: .claude/skills/debug/SKILL.md, .claude/skills/docs/SKILL.md, .claude/skills/feature/SKILL.md.
- docs: archive day pause resume investigation plan (265e4cc) - 2 files changed, 35 insertions(+), 40 deletions(-); areas: .cursor; top files: .cursor/plans/2026-02-26-playwright-day-pause-resume-root-cause-plan.md, .cursor/plans/implemented/2026-02-26-playwright-day-pause-resume-root-cause-plan.md.
- docs: close and archive current work plans (f661a4f) - 2 files changed, 38 insertions(+), 17 deletions(-); areas: .cursor; top files: .cursor/plans/2026-02-26-automated-testing-next-steps-plan.md, .cursor/plans/2026-02-26-performance-profiling-progress.md, .cursor/plans/implemented/2026-02-26-automated-testing-next-steps-plan.md.
- docs: save product architect run output for 2026-02-28 (f7ff00c) - 1 file changed, 274 insertions(+); areas: docs; top files: docs/prompts/runs/2026-02-28-product-architect.md.
- docs: run product-architect prompt and update execution history (24f8822) - 2 files changed, 5 insertions(+), 3 deletions(-); areas: docs; top files: docs/prompts/README.md, docs/prompts/product-architect-prompt.md.
- docs: add prompt execution tracking to library (d351f92) - 1 file changed, 16 insertions(+); areas: docs; top files: docs/prompts/README.md.
- docs: organize and refresh project prompt library (8348359) - 9 files changed, 798 insertions(+), 5 deletions(-); areas: docs; top files: docs/product-architect-prompt.md, docs/prompts/README.md, docs/prompts/_template.md.
- Update project documentation (92f9347) - 25 files changed, 1039 insertions(+), 152 deletions(-); areas: CHANGELOG.md, README.md, docs, scripts; top files: CHANGELOG.md, README.md, docs/FEATURES_DETAILED.md.
- docs: Add Playwright end-to-end testing guides and Tauri mocking documentation (e3d1e7b) - 2 files changed, 123 insertions(+); areas: docs; top files: docs/E2E_TESTING_GUIDE.md, docs/TAURI_MOCKING_ARCHITECTURE.md.
- docs: Document E2E Playwright testing and Tauri mocking fixes (57ac614) - 1 file changed, 33 insertions(+); areas: .cursor; top files: .cursor/plans/2026-02-22-tauri-playwright-e2e-fixes.md.
- docs: update changelog for v0.1.21 (d59229e) - 1 file changed, 17 insertions(+), 1 deletion(-); areas: CHANGELOG.md; top files: CHANGELOG.md.
- docs(plans): update flexible sidebar layout plan to draft status (cafe769) - 5 files changed, 600 insertions(+), 574 deletions(-); areas: src/App.tsx, src/components, src/stores; top files: src/App.tsx, src/components/common/WidgetWrapper.tsx, src/stores/layoutStore.test.ts.
- docs: consolidate database lock plan to single strategy (101dd2a) - 11 files changed, 370 insertions(+), 304 deletions(-); areas: scripts, src/App.tsx, src/components, src/index.css; top files: scripts/dev/restart-dev.ps1, scripts/dev/start-client.ps1, scripts/dev/tail-app-log.ps1.
- docs: add release documentation checklist and improve AI review (a8c8178) - 9 files changed, 775 insertions(+), 106 deletions(-); areas: docs, src-tauri/src, src/components; top files: docs/release-versioning.md, src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs.
- docs: enhance installation troubleshooting and update customer scraper logic (bd8d675) - 10 files changed, 158 insertions(+), 51 deletions(-); areas: docs, scripts, src/components, src/hooks; top files: docs/wiki/Installation.md, scripts/synergy/synergy-customers-scraper.mjs, src/components/modals/AboutButton.tsx.
- docs: update README and wiki sync workflow (cbe5497) - 7 files changed, 121 insertions(+), 23 deletions(-); areas: .github, README.md, docs, src/components; top files: .github/workflows/release.yml, .github/workflows/wiki-sync.yml, README.md.
- docs: update release versioning guidelines and changelog policy (23c0f61) - 2 files changed, 494 insertions(+), 56 deletions(-); areas: CHANGELOG.md, docs; top files: CHANGELOG.md, docs/release-versioning.md.
- chore: update documentation and improve formatting consistency (9b02004) - 157 files changed, 5819 insertions(+), 3091 deletions(-); areas: AGENTS.md, README.md, docs, package-lock.json; top files: AGENTS.md, README.md, docs/IMPROVEMENTS.md.
- Update documentation for development commands and architecture details (ec4d437) - 4 files changed, 152 insertions(+), 30 deletions(-); areas: docs; top files: docs/AGENTS.md, docs/CLAUDE.md, docs/FEATURES_DETAILED.md.
- CSP + file-read restricties + README/setup fix + quality gates (lint/format/typecheck). (261589d) - 138 files changed, 7957 insertions(+), 5184 deletions(-); areas: .prettierignore, .prettierrc.json, README.md, docs; top files: .prettierignore, .prettierrc.json, README.md.

### Build & Release

- chore: complete v0.1 milestone — archive phases 1-2, evolve planning docs (39f2a4a) - 32 files changed, 347 insertions(+), 230 deletions(-); areas: .planning, CHANGELOG.md; top files: .planning/MILESTONES.md, .planning/PROJECT.md, .planning/REQUIREMENTS.md.
- chore: add project config (0ecee1b) - 1 file changed, 12 insertions(+); areas: .planning; top files: .planning/config.json.
- chore: commit untracked test files and update release-manager prompt baseline (fee1132) - 5 files changed, 292 insertions(+), 2 deletions(-); areas: docs, src/stores, src/utils, src/vitest-env.d.ts; top files: docs/prompts/release-manager-prompt.md, src/stores/newsStore.test.ts, src/utils/duration.test.ts.
- chore: commit all current changes and add pause-resume debug plan (5b8225f) - 3 files changed, 41 insertions(+), 1 deletion(-); areas: .cursor, playwright-report; top files: .cursor/plans/2026-02-22-project-restructuring.md, .cursor/plans/2026-02-26-playwright-day-pause-resume-root-cause-plan.md, .cursor/plans/implemented/2026-02-22-project-restructuring.md.
- chore(changelog): improve unreleased generation and commit detail (bf9cd34) - 2 files changed, 475 insertions(+), 288 deletions(-); areas: CHANGELOG.md, scripts; top files: CHANGELOG.md, scripts/generate-changelog.ps1.
- chore: Remove various temporary output files and add a QA engineer prompt document. (073373b) - 39 files changed, 34 insertions(+), 4596 deletions(-); areas: docs; top files: docs/qa-engineer-prompt.md.
- chore: Add `errors_latest.txt` containing current ESLint warnings. (873d592) - 1 file changed, 17 insertions(+); areas: errors_latest.txt; top files: errors_latest.txt.
- chore: close resolved QA issues (899683c) - no diff stats available; areas: (no file changes); top files: (no files listed).
- chore: fix eslint any type errors and formatting issues; add ci pipeline (c3665ec) - 14 files changed, 759 insertions(+), 101 deletions(-); areas: .github, .husky, docs, package-lock.json; top files: .github/workflows/ci.yml, .husky/pre-commit, docs/qa-engineer-prompt.md.
- release: v0.1.23 (08af9c2) - 5 files changed, 43 insertions(+), 7 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- release: v0.1.22 (ac10f91) - 5 files changed, 47 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- chore: sync package-lock.json for v0.1.21 (199b6b6) - 1 file changed, 62 insertions(+), 2 deletions(-); areas: package-lock.json; top files: package-lock.json.
- release: v0.1.21 (2a1a3b2) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.
- release: v0.1.20 (1bc6bb7) - 4 files changed, 71 insertions(+), 24 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- chore: tussentijdse commit (5e8b03c) - 35 files changed, 3046 insertions(+), 686 deletions(-); areas: docs, package.json, scripts, src-tauri/src; top files: docs/wiki/DatabaseLockDiagnostics.md, docs/wiki/Home.md, package.json.
- chore(scripts): add dev lifecycle and client start commands (4c066f6) - 7 files changed, 168 insertions(+); areas: package.json, scripts; top files: package.json, scripts/dev/restart-dev.bat, scripts/dev/restart-dev.ps1.
- release: v0.1.19 (d625438) - 6 files changed, 181 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, scripts, src-tauri/Cargo.lock; top files: CHANGELOG.md, package.json, scripts/generate-changelog.ps1.
- chore(gitignore): ignore scraped issue content (2b6f58f) - 2 files changed, 4 insertions(+), 1558 deletions(-); areas: .gitignore, issue_content.html; top files: .gitignore, issue_content.html.
- release: v0.1.18 (e5bd66a) - 5 files changed, 9 insertions(+), 5 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- chore: add .editorconfig and husky pre-commit hook for security checks (e0cdd7f) - 11 files changed, 431 insertions(+), 17 deletions(-); areas: .ai, .editorconfig, .github, .husky; top files: .ai/prompts/code-review.md, .ai/prompts/commit.md, .editorconfig.
- release: v0.1.17 (938487b) - 5 files changed, 27 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- release: v0.1.16 (b5b389c) - 6 files changed, 23 insertions(+), 6 deletions(-); areas: CHANGELOG.md, package-lock.json, package.json, src-tauri/Cargo.lock; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- chore: update Cargo.lock for v0.1.15 (9ba0c4d) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: src-tauri/Cargo.lock; top files: src-tauri/Cargo.lock.
- release: v0.1.15 (67ad0ca) - 3 files changed, 3 insertions(+), 3 deletions(-); areas: package.json, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.
- release: v0.1.14 (8bd7b14) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.
- release: v0.1.13 (3ab6073) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.
- release: v0.1.12 (46f9cad) - 5 files changed, 11 insertions(+), 5 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- release: v0.1.11 (08c0197) - 7 files changed, 31 insertions(+), 16 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- release: v0.1.10 (b8d4d4b) - 5 files changed, 18 insertions(+), 12 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.toml, src/components; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- release: v0.1.9 (d028a03) - 5 files changed, 15 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- release: v0.1.8 (0a375d3) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.
- chore: remove outdated additional edge case hardening plan document (e6842e7) - 5 files changed, 693 insertions(+); areas: .cursor; top files: .cursor/PLAN_GUIDELINES.md, .cursor/plans/2026-02-10-PLAN_BACKEND_HARDENING.md, .cursor/plans/2026-02-10-additional-edge-case-hardening-plan.md.
- release: v0.1.7 (66126a2) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.
- release: v0.1.6 (d6eb8fc) - 5 files changed, 44 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: CHANGELOG.md, package.json, src-tauri/Cargo.toml.
- release: v0.1.5 (29d1123) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.
- chore: sync Cargo.lock for v0.1.4 (5f56182) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: src-tauri/Cargo.lock; top files: src-tauri/Cargo.lock.
- release: v0.1.4 (cb42054) - 8 files changed, 52 insertions(+), 20 deletions(-); areas: .github, docs, package.json, src-tauri/Cargo.toml; top files: .github/workflows/release.yml, docs/CLAUDE.md, package.json.
- release: v0.1.3 (ef805a2) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml; top files: package.json, src-tauri/Cargo.toml.
- chore: update version to 0.1.2 and enhance app metadata (ba389bb) - 9 files changed, 319 insertions(+), 6 deletions(-); areas: package-lock.json, src-tauri/Cargo.lock, src/App.tsx, src/components; top files: src/App.tsx, src/components/common/UpdateBanner.tsx, src/components/modals/AboutButton.tsx.
- release: enforce version consistency and prepare v0.1.2 (8fc6bcc) - 5 files changed, 67 insertions(+), 3 deletions(-); areas: .github, docs, package.json, src-tauri/Cargo.toml; top files: .github/workflows/release.yml, docs/release-versioning.md, package.json.

### Other Changes

- Merge branch 'main' of https://github.com/vanachterjacob/DeveloperCompanion (654d5e6) - 7 files changed, 131 insertions(+), 2 deletions(-); areas: playwright-report; top files: playwright-report/index.html.
- Expand-E2E-failure-coverage-and-Playwright-local-helpers (96f5c80) - 7 files changed, 315 insertions(+), 4 deletions(-); areas: scripts, tests; top files: scripts/test/run-playwright-local.bat, scripts/test/stop-playwright-webserver.bat, tests/e2e/devops-build-review.spec.ts.
- Add-backup-restore-test-coverage-and-background-task-checks (40e889e) - 4 files changed, 424 insertions(+), 91 deletions(-); areas: src-tauri/src, src/components, tests; top files: src-tauri/src/db/backup.rs, src/components/automation/BackgroundTasksPanel.tsx, tests/e2e/background-tasks.spec.ts.
- merge: perf profiling progress into main (9a2ef52) - 17 files changed, 1462 insertions(+), 229 deletions(-); areas: CHANGELOG.md; top files: CHANGELOG.md.
- Document single-instance desktop fix (284b33d) - 1 file changed, 2 insertions(+); areas: CHANGELOG.md; top files: CHANGELOG.md.
- Prevent multiple app instances (05e2c99) - 3 files changed, 24 insertions(+), 1 deletion(-); areas: src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src; top files: src-tauri/Cargo.toml, src-tauri/src/lib.rs.
- Add random retro welcome titles (29dc2b3) - 1 file changed, 34 insertions(+), 1 deletion(-); areas: src/App.tsx; top files: src/App.tsx.
- Maak instellingen overal zoekbaar (dc4ea79) - 15 files changed, 1402 insertions(+), 202 deletions(-); areas: CHANGELOG.md, README.md, docs, package-lock.json; top files: CHANGELOG.md, README.md, docs/FEATURES_DETAILED.md.
- Add explicit substep labels (5963675) - 17 files changed, 1593 insertions(+), 16 deletions(-); areas: src/App.tsx, src/components, src/stores, src/types; top files: src/App.tsx, src/components/common/CommandPaletteButton.tsx, src/components/common/EditModeButton.tsx.
- Clarify REST API deliverable warning (7221c37) - 5 files changed, 35 insertions(+), 13 deletions(-); areas: src/components, src/index.css, src/stores; top files: src/components/modals/SetupWizardModal.tsx, src/components/worklog/BulkImportTable.tsx, src/components/worklog/BulkImportView.tsx.
- Simplify todo UX, improve timeline toggle, and persist DevOps work item URLs (61146a0) - 13 files changed, 1633 insertions(+), 394 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components; top files: migrations/046_todo_productivity_upgrade.sql, migrations/047_expand_default_activities_balance.sql, migrations/048_todo_devops_work_item_url.sql.
- Merge branch 'feature/synergy-sync-improvements' into main (86a86fa) - 7 files changed, 542 insertions(+), 211 deletions(-); areas: (no file changes); top files: (no files listed).
- style: move minimalist mode toggle to appearance settings tab (34bf1e5) - 1 file changed, 14 insertions(+), 14 deletions(-); areas: src/components; top files: src/components/modals/SettingsButton.tsx.
- Stop dev server when starting client (29da89f) - 2 files changed, 12 insertions(+), 6 deletions(-); areas: package.json, scripts; top files: package.json, scripts/dev/start-client.ps1.
- optimize: keep YouTube Music playing when closing the separate window by hiding it instead (c37a0f1) - 3 files changed, 24 insertions(+), 4 deletions(-); areas: src-tauri/src, src/stores; top files: src-tauri/src/lib.rs, src-tauri/src/youtube_music.rs, src/stores/youtubeMusicStore.ts.
- accessibility: improve a11y, add personalized retro easter eggs and UI tweaks (b701204) - 8 files changed, 624 insertions(+), 58 deletions(-); areas: index.html, src/App.tsx, src/components, src/index.css; top files: index.html, src/App.tsx, src/components/common/StatsFooterBar.tsx.
- security: harden cli calls, update vulnerable dependencies, and improve html sanitization (b6ddd1e) - 7 files changed, 728 insertions(+), 539 deletions(-); areas: package-lock.json, package.json, src-tauri/Cargo.lock, src-tauri/src; top files: package.json, src-tauri/src/ai_review.rs, src-tauri/src/build_orchestrator.rs.
- #7 refactor(App): implement dynamic sidebar widget rendering (44beb4a) - 6 files changed, 391 insertions(+), 247 deletions(-); areas: src/App.tsx, src/components, src/stores; top files: src/App.tsx, src/components/common/Animations.tsx, src/components/common/WidgetWrapper.tsx.
- Update Cursor model validation and options to support latest frontier models like opus-4.6 (8810a12) - 2 files changed, 22 insertions(+), 16 deletions(-); areas: src-tauri/src, src/stores; top files: src-tauri/src/lib.rs, src/stores/settingsStore.ts.
- Use cursor.cmd for agent invocation to prevent GUI windows (8bc898c) - 1 file changed, 44 insertions(+), 14 deletions(-); areas: src-tauri/src; top files: src-tauri/src/lib.rs.
- Add Tab key functionality (fb9cfe8) - 3 files changed, 118 insertions(+), 118 deletions(-); areas: src/components; top files: src/components/synergy/SynergyCustomerCombobox.tsx, src/components/synergy/SynergyDeliverableCombobox.tsx, src/components/synergy/SynergyProjectCombobox.tsx.
- Add unit tests for preSyncValidation, dayStore, timerStore, and timer utility functions (0ad63c7) - 21 files changed, 4909 insertions(+), 49 deletions(-); areas: .github, docs, src/services, src/stores; top files: .github/skills/prompt-engineering-patterns/SKILL.md, .github/skills/prompt-engineering-patterns/assets/prompt-template-library.md, .github/skills/prompt-engineering-patterns/references/chain-of-thought.md.
- Status filter pills appear above the build cards when there are multiple statuses present. Each pill is a toggle button styled with the status's color: (37110c0) - 1 file changed, 69 insertions(+), 1 deletion(-); areas: src/components; top files: src/components/devops/DiffViewer.tsx.
- Merge branch 'main' of https://github.com/vanachterjacob/DeveloperCompanion (60829f1) - 18 files changed, 500 insertions(+), 143 deletions(-); areas: src-tauri/src; top files: src-tauri/src/build_orchestrator.rs.
- Add Support for Claude CLI (b7803be) - 3 files changed, 65 insertions(+), 18 deletions(-); areas: package-lock.json, src-tauri/src; top files: src-tauri/src/build_orchestrator.rs.
- Update Gitignore (123409e) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: .gitignore; top files: .gitignore.
- Update agents md (822ff71) - 1 file changed, 321 insertions(+), 120 deletions(-); areas: AGENTS.md; top files: AGENTS.md.
- Remove outdated plans for potential improvements, Spotify widget implementation, automation enhancements, and bulk import features. These files have been deleted as they are no longer relevant to the current project direction. (fdfbdc1) - 22 files changed, 302 insertions(+); areas: src/App.tsx, src/components, src/stores; top files: src/App.tsx, src/components/common/EditModeButton.tsx, src/components/common/WidgetWrapper.tsx.
- Spotify Plan (25e700b) - 12 files changed, 1745 insertions(+), 4 deletions(-); areas: src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src, src/App.tsx; top files: src-tauri/Cargo.toml, src-tauri/src/lib.rs, src-tauri/src/spotify.rs.
- Enhance scraper navigation and debugging capabilities; update installer to use WebView2 bootstrapper (3210720) - 6 files changed, 62 insertions(+), 17 deletions(-); areas: scripts, src/App.tsx; top files: scripts/build/build-installer.bat, scripts/synergy/synergy-customers-scraper.mjs, scripts/synergy/synergy-deliverables-scraper.mjs.
- Builden v1 (7a0e425) - 6 files changed, 221 insertions(+), 27 deletions(-); areas: .gitignore, README.md, scripts, src-tauri/src; top files: .gitignore, README.md, scripts/build/build-installer.bat.
- Betere kalenderlaadtijden (6879638) - 5 files changed, 1052 insertions(+), 73 deletions(-); areas: scripts, src-tauri/src, src/components, src/services; top files: scripts/discover-synergy-calendar-xhr.mjs, src-tauri/src/lib.rs, src/components/scrapers/CalendarXhrDiscoveryPanel.tsx.
- Remove RSS from fetching data (ced89ff) - 5 files changed, 817 insertions(+), 144 deletions(-); areas: scripts, src/components; top files: scripts/discover-synergy-calendar-xhr.mjs, src/components/scrapers/CalendarXhrDiscoveryPanel.tsx, src/components/synergy/SynergyToolsModal.tsx.
- Remove Sessions Functionality (0034a6f) - 10 files changed, 5 insertions(+), 2314 deletions(-); areas: docs, package-lock.json, src-tauri/src, src/components; top files: docs/synergy-web-session-push-progress.md, src-tauri/src/lib.rs, src-tauri/src/synergy_web_session.rs.
- Spint2 en bugfixes (99aa9b7) - 19 files changed, 3028 insertions(+), 368 deletions(-); areas: .gitignore, .prettierignore, scripts, src-tauri/Cargo.lock; top files: .gitignore, .prettierignore, scripts/synergy/synergy-customers-scraper.mjs.
- English (54e60ee) - 52 files changed, 1019 insertions(+), 885 deletions(-); areas: README.md, docs, migrations, src-tauri/src; top files: README.md, docs/FEATURES_DETAILED.md, docs/IMPROVEMENTS.md.
- SynergyFixes (75d0be7) - 5 files changed, 136 insertions(+), 21 deletions(-); areas: migrations, src-tauri/src, src/components, src/services; top files: migrations/013_worklog_templates.sql, src-tauri/src/db/migrations.rs, src/components/worklog/WorkLogCalendar.tsx.
- Add output files for synergy push process with detailed logs (c708556) - 22 files changed, 6270 insertions(+), 104 deletions(-); areas: AGENTS.md, scripts, src/components, src/services; top files: AGENTS.md, scripts/synergy-push.mjs, src/components/WorkLogPanel.tsx.
- Add output logs for synergy push process (716913f) - 39 files changed, 12831 insertions(+), 138 deletions(-); areas: AGENTS.md, DELIVERABLES_SCRAPER_PROGRESS.md, README.md, migrations; top files: AGENTS.md, DELIVERABLES_SCRAPER_PROGRESS.md, README.md.
- Merge branch 'main' of https://github.com/vanachterjacob/DeveloperCompanion (6302426) - 80 files changed, 22991 insertions(+), 412 deletions(-); areas: README.md, package-lock.json, package.json; top files: README.md, package.json.
- Add initial project plan and functional requirements for Developer Dag Companion (4316634) - 1 file changed, 928 insertions(+); areas: PROJECT_PLAN.md; top files: PROJECT_PLAN.md.

## Older History

See [commit history](https://github.com/vanachterjacob/DeveloperCompanion/commits/main) for complete details.
