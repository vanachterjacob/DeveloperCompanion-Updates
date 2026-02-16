# Changelog

All notable changes to DeveloperCompanion will be documented in this file.

This changelog is generated from git tags and commit ranges, with per-commit scope and diff stats.

## [0.1.17] - 2026-02-16

### Release Scope

- Commit range: v0.1.16..v0.1.17
- Commits in release: 5

### Features

- feat: enhance synchronization and error handling in autoSync and related stores (ca94f30) - 8 files changed, 131 insertions(+), 78 deletions(-); areas: src-tauri/src, src/hooks, src/services, src/stores.

### Fixes

- fix: remove unnecessary cursor.cmd from Windows CLI candidates (8facb42) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: src-tauri/src.

### Documentation

- docs: update release versioning guidelines and changelog policy (23c0f61) - 2 files changed, 494 insertions(+), 56 deletions(-); areas: CHANGELOG.md, docs.

### Other Changes

- Add unit tests for preSyncValidation, dayStore, timerStore, and timer utility functions (0ad63c7) - 21 files changed, 4909 insertions(+), 49 deletions(-); areas: .claude, .cursor, docs, src/services.

## [0.1.16] - 2026-02-14

### Release Scope

- Commit range: v0.1.15..v0.1.16
- Commits in release: 8

### Features

- feat: enhance error handling and notifications in App component (779b4fd) - 20 files changed, 603 insertions(+), 105 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components.
- feat: add Git commit handling and unclean repository checks in DevOps build process (14e9c27) - 2 files changed, 178 insertions(+), 14 deletions(-); areas: src-tauri/src, src/stores.
- feat: enhance DevOps tools and UI components (2487ba4) - 30 files changed, 1395 insertions(+), 449 deletions(-); areas: README.md, docs, package-lock.json, scripts.
- feat: Implement new UI components for work logging, timers, and various modals, including Synergy integration. (a9de997) - 18 files changed, 4855 insertions(+), 4294 deletions(-); areas: .cursor, package-lock.json, package.json, src/components.
- feat: Add detailed product architect innovation plan and related documentation files. (0ffe998) - 3 files changed, 286 insertions(+); areas: .cursor, docs.
- feat: Implement automatic Synergy worklog synchronization with API and Playwright fallback, and add new backend services for AI review, AL search, and project scanning, alongside a plan for QA improvements. (9a75537) - 13 files changed, 765 insertions(+), 272 deletions(-); areas: .cursor, docs, package.json, src-tauri/src.

### Build & Release

- release: v0.1.16 (b5b389c) - 6 files changed, 23 insertions(+), 6 deletions(-); areas: CHANGELOG.md, package-lock.json, package.json, src-tauri/Cargo.lock.
- chore: update Cargo.lock for v0.1.15 (9ba0c4d) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: src-tauri/Cargo.lock.

## [0.1.15] - 2026-02-12

### Release Scope

- Commit range: v0.1.14..v0.1.15
- Commits in release: 8

### Features

- feat: Add workflow detail caching and retrieval functions in WorkLogCalendar (2ff9558) - 1 file changed, 198 insertions(+), 60 deletions(-); areas: src/components.
- feat: Implement feedback selection and build prompt features (43dc8f3) - 9 files changed, 615 insertions(+), 158 deletions(-); areas: src/components, src/services, src/stores.
- feat: Enhance DevOps build process with custom branch support and AI build options (9386d8c) - 17 files changed, 567 insertions(+), 53 deletions(-); areas: .cursor, migrations, src-tauri/src, src/components.
- feat: enhance concurrency handling in runWithConcurrencyLimit to return failures alongside results (a7c850e) - 22 files changed, 1008 insertions(+), 154 deletions(-); areas: .cursor, scripts, src-tauri/src, src/App.tsx.
- feat: QA review phase 1 - enhance App component with bootstrap error handling and UI feedback (a8534fa) - 35 files changed, 708 insertions(+), 811 deletions(-); areas: .cursor, .github, AGENTS.md, docs.
- feat: add QA Audit Bug & Edge Case Report for Developer Companion (fc0e527) - 1 file changed, 231 insertions(+); areas: .cursor.

### Refactoring

- Refactor and enhance error handling across various components (e9dd0fa) - 15 files changed, 409 insertions(+), 185 deletions(-); areas: .cursor, package-lock.json, scripts, src-tauri/src.

### Build & Release

- release: v0.1.15 (67ad0ca) - 3 files changed, 3 insertions(+), 3 deletions(-); areas: package.json, src-tauri/Cargo.toml, src-tauri/tauri.conf.json.

## [0.1.14] - 2026-02-11

### Release Scope

- Commit range: v0.1.13..v0.1.14
- Commits in release: 8

### Features

- feat: enhance WorkLogCalendar with loading state and animations (e3ad112) - 3 files changed, 43 insertions(+), 9 deletions(-); areas: src/components, tailwind.config.cjs.
- feat: enhance DevOpsToolsModal and work item title detection (77b5fb8) - 3 files changed, 46 insertions(+), 3 deletions(-); areas: src/components, src/services.
- feat: update settings and enhance CLI model handling (b05c25d) - 15 files changed, 413 insertions(+), 146 deletions(-); areas: index.html, package-lock.json, src-tauri/src, src/App.tsx.

### Build & Release

- release: v0.1.14 (8bd7b14) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/tauri.conf.json.

### Other Changes

- Status filter pills appear above the build cards when there are multiple statuses present. Each pill is a toggle button styled with the status's color: (37110c0) - 1 file changed, 69 insertions(+), 1 deletion(-); areas: src/components.
- Merge branch 'main' of https://github.com/vanachterjacob/DeveloperCompanion (60829f1) - 18 files changed, 500 insertions(+), 143 deletions(-); areas: src-tauri/src.
- Add Support for Claude CLI (b7803be) - 3 files changed, 65 insertions(+), 18 deletions(-); areas: .claude, package-lock.json, src-tauri/src.
- Update Gitignore (123409e) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: .gitignore.

## [0.1.13] - 2026-02-11

### Release Scope

- Commit range: v0.1.12..v0.1.13
- Commits in release: 3

### Features

- feat: enhance work log and synergy integration (8c27657) - 45 files changed, 3518 insertions(+), 433 deletions(-); areas: .cursor, docs, migrations, package-lock.json.
- feat: implement weather proxy and enhance weather data fetching (5eda6c4) - 3 files changed, 161 insertions(+), 39 deletions(-); areas: src-tauri/src, src/services.

### Build & Release

- release: v0.1.13 (3ab6073) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/tauri.conf.json.

## [0.1.12] - 2026-02-10

### Release Scope

- Commit range: v0.1.11..v0.1.12
- Commits in release: 1

### Build & Release

- release: v0.1.12 (46f9cad) - 5 files changed, 11 insertions(+), 5 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml.

## [0.1.11] - 2026-02-10

### Release Scope

- Commit range: v0.1.10..v0.1.11
- Commits in release: 1

### Build & Release

- release: v0.1.11 (08c0197) - 7 files changed, 31 insertions(+), 16 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml.

## [0.1.10] - 2026-02-10

### Release Scope

- Commit range: v0.1.9..v0.1.10
- Commits in release: 1

### Build & Release

- release: v0.1.10 (b8d4d4b) - 5 files changed, 18 insertions(+), 12 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.toml, src-tauri/tauri.conf.json.

## [0.1.9] - 2026-02-10

### Release Scope

- Commit range: v0.1.8..v0.1.9
- Commits in release: 3

### Features

- feat: enhance weather widget and modal with location settings and geocoding support (25f2c83) - 7 files changed, 605 insertions(+), 118 deletions(-); areas: migrations, package-lock.json, src-tauri/src, src/components.

### Fixes

- fix: correct release notes URL to point to public updates repo (ee91d76) - 4 files changed, 146 insertions(+), 6 deletions(-); areas: .github, CHANGELOG.md, docs, src/hooks.

### Build & Release

- release: v0.1.9 (d028a03) - 5 files changed, 15 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml.

## [0.1.8] - 2026-02-10

### Release Scope

- Commit range: v0.1.7..v0.1.8
- Commits in release: 14

### Features

- feat: integrate local commit scanning and enhance work item link management (18f3e86) - 17 files changed, 1906 insertions(+), 119 deletions(-); areas: .cursor, migrations, src-tauri/src, src/components.
- feat: enhance security and sanitization across components (ca11c2f) - 16 files changed, 488 insertions(+), 119 deletions(-); areas: .cursor, src-tauri/src, src/components, src/services.
- feat: Implement upgrade work item filtering and enhance project mapping logic (d037c6b) - 8 files changed, 247 insertions(+), 41 deletions(-); areas: src/components, src/index.css, src/services, src/stores.
- feat: Update button styles for improved UI consistency and accessibility (a0dbbdf) - 6 files changed, 17 insertions(+), 11 deletions(-); areas: .cursor, src/components, src/utils.
- feat: Enhance UI settings with density modes, reduced motion toggle, and date/time preferences (3454938) - 14 files changed, 914 insertions(+), 37 deletions(-); areas: .cursor, src/components, src/hooks, src/index.css.
- feat: add retro theme option and update theme handling logic (e089d94) - 4 files changed, 261 insertions(+), 4 deletions(-); areas: src/components, src/hooks, src/index.css, src/stores.
- feat: add UI theme customization and improve component styling (a323251) - 18 files changed, 320 insertions(+), 156 deletions(-); areas: package-lock.json, src/components, src/hooks, src/stores.
- feat: add comprehensive documentation for Developer Companion (2fce494) - 3 files changed, 523 insertions(+); areas: docs.
- feat: implement edge case hardening plan for security improvements (7b7379d) - 13 files changed, 520 insertions(+), 19 deletions(-); areas: .cursor, package-lock.json, src-tauri/src, src/components.

### Fixes

- fix: update release notes URL to point to updates repo (7af620f) - 1 file changed, 3 insertions(+), 2 deletions(-); areas: .github.

### Refactoring

- refactor: simplify release URL resolution in useAutoUpdater hook (9def06d) - 1 file changed, 11 deletions(-); areas: src/hooks.

### Documentation

- chore: update documentation and improve formatting consistency (9b02004) - 157 files changed, 5819 insertions(+), 3091 deletions(-); areas: .cursor, AGENTS.md, README.md, docs.

### Build & Release

- release: v0.1.8 (0a375d3) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/tauri.conf.json.
- chore: remove outdated additional edge case hardening plan document (e6842e7) - 5 files changed, 693 insertions(+); areas: .cursor.

## [0.1.7] - 2026-02-09

### Release Scope

- Commit range: v0.1.6..v0.1.7
- Commits in release: 7

### Features

- feat: integrate Outlook tool availability check and enhance settings management (58f8818) - 4 files changed, 333 insertions(+), 47 deletions(-); areas: src-tauri/src, src/components.
- feat: add news summary settings and migration support (bbcea00) - 7 files changed, 468 insertions(+), 82 deletions(-); areas: AGENTS.md, migrations, src-tauri/src, src/components.
- feat: enhance AboutButton with current version notes and improved UI (300db4f) - 4 files changed, 129 insertions(+), 17 deletions(-); areas: src-tauri/src, src/components.
- feat: add customer ID resolution by code in Synergy API (658ed5d) - 5 files changed, 185 insertions(+), 3 deletions(-); areas: package-lock.json, src-tauri/src, src/components, src/services.
- feat: standardize language and improve English consistency across the application (4d0008f) - 24 files changed, 145 insertions(+), 133 deletions(-); areas: AGENTS.md, src/App.tsx, src/components, src/services.
- feat: enhance visibility-aware intervals across components (f9e7dbf) - 25 files changed, 430 insertions(+), 248 deletions(-); areas: .claude, scripts, src-tauri/src, src/components.

### Build & Release

- release: v0.1.7 (66126a2) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/tauri.conf.json.

## [0.1.6] - 2026-02-09

### Release Scope

- Commit range: v0.1.5..v0.1.6
- Commits in release: 28

### Features

- feat: enhance scraper components with progress tracking and state management (a7db3bc) - 14 files changed, 864 insertions(+), 1327 deletions(-); areas: src-tauri/NS - New Sales, src-tauri/src, src/components, src/hooks.
- feat: enhance scraper progress tracking and estimation (d3bee7e) - 5 files changed, 380 insertions(+), 42 deletions(-); areas: scripts, src-tauri/src, src/components.
- feat: enhance DevOps tools with state change notifications and work item logging (c2946f1) - 16 files changed, 1926 insertions(+), 113 deletions(-); areas: src-tauri/src, src/components, src/services, src/stores.
- feat: enhance BuildDashboard and DevOps tools with inline commenting and navigation (491c162) - 15 files changed, 2455 insertions(+), 119 deletions(-); areas: src/components, src/services, src/stores.
- feat: enhance BuildDashboard and DevOps tools with new features (91bee76) - 15 files changed, 1936 insertions(+), 277 deletions(-); areas: src-tauri/NS - New Sales, src-tauri/src, src/components, src/stores.
- feat: enhance WorkItemsPanel with organization selection and sorting features (6409f9f) - 10 files changed, 602 insertions(+), 494 deletions(-); areas: src-tauri/src, src/components, src/stores.
- feat: enhance DevOps tools integration and UI improvements (88b42da) - 5 files changed, 98 insertions(+), 52 deletions(-); areas: .claude, src/App.tsx, src/components.
- feat: enhance DevOps integration with automatic time logging and project mapping (817af6a) - 38 files changed, 5491 insertions(+), 132 deletions(-); areas: .cursor, migrations, src-tauri/src, src/App.tsx.
- feat: implement DevOps integration and settings management (4b0d130) - 26 files changed, 5086 insertions(+), 15 deletions(-); areas: .cursor, migrations, src-tauri/Cargo.lock, src-tauri/Cargo.toml.
- feat: integrate synergy URL handling across components (a5e6266) - 6 files changed, 19 insertions(+), 15 deletions(-); areas: src/components.
- feat: integrate synergy project and customer selection in TodoPanel (c8593ab) - 5 files changed, 191 insertions(+), 36 deletions(-); areas: migrations, src-tauri/src, src/components, src/stores.
- feat: enhance user experience with new features and UI improvements (5b4c433) - 37 files changed, 2002 insertions(+), 149 deletions(-); areas: .cursor, README.md, docs, src-tauri/Cargo.lock.
- feat: enhance audio state management during track transitions (165e680) - 1 file changed, 114 insertions(+), 5 deletions(-); areas: src-tauri/src.
- feat: add Vitest support and enhance settings with notification grace period (7227bc6) - 17 files changed, 1062 insertions(+), 99 deletions(-); areas: .claude, migrations, package-lock.json, package.json.
- feat: add SettingsGroup component to enhance settings UI organization (ada0374) - 1 file changed, 683 insertions(+), 540 deletions(-); areas: src/components.
- feat: add support for OpenAI Codex CLI and enhance settings UI (f01f945) - 23 files changed, 3119 insertions(+), 256 deletions(-); areas: .claude, .cursor, migrations, package-lock.json.
- feat: enhance error handling and JSON parsing across components (f2e986c) - 20 files changed, 1016 insertions(+), 109 deletions(-); areas: .claude, .cursor, src-tauri/src, src-tauri/tauri.conf.json.
- feat: enhance button titles for improved user experience (1c40c01) - 12 files changed, 305 insertions(+), 58 deletions(-); areas: src-tauri/src, src/App.tsx, src/components, src/stores.
- feat: enhance news feed functionality with AI and BC groups (b538971) - 9 files changed, 396 insertions(+), 65 deletions(-); areas: migrations, src-tauri/src, src/App.tsx, src/components.
- feat: integrate news feed functionality (93f9821) - 17 files changed, 1250 insertions(+), 16 deletions(-); areas: .claude, migrations, package-lock.json, src-tauri/src.

### Fixes

- fix: improve settings button behavior and UI consistency (def5a21) - 4 files changed, 33 insertions(+), 32 deletions(-); areas: src/components, src/stores.

### Refactoring

- refactor: update setup scripts and enhance CLI engine options (a5c3e57) - 10 files changed, 58 insertions(+), 18 deletions(-); areas: AGENTS.md, scripts, setup.bat, setup.sh.
- refactor: simplify SQL migration inclusion in database migrations (8f73fa4) - 1 file changed, 34 insertions(+), 30 deletions(-); areas: src-tauri/src.
- refactor: streamline documentation and enhance agent guidelines (e3a36d6) - 12 files changed, 741 insertions(+), 1867 deletions(-); areas: .cursor, AGENTS.md, README.md, docs.
- refactor: remove sync verification feature and related settings (8ca8b1a) - 12 files changed, 5 insertions(+), 1349 deletions(-); areas: migrations, scripts, src/components, src/services.

### Documentation

- Update documentation for development commands and architecture details (ec4d437) - 4 files changed, 152 insertions(+), 30 deletions(-); areas: docs.

### Build & Release

- release: v0.1.6 (d6eb8fc) - 5 files changed, 44 insertions(+), 4 deletions(-); areas: CHANGELOG.md, package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml.

### Other Changes

- Update agents md (822ff71) - 1 file changed, 321 insertions(+), 120 deletions(-); areas: AGENTS.md.

## [0.1.5] - 2026-02-06

### Release Scope

- Commit range: v0.1.4..v0.1.5
- Commits in release: 1

### Build & Release

- release: v0.1.5 (29d1123) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/tauri.conf.json.

## [0.1.4] - 2026-02-06

### Release Scope

- Commit range: v0.1.3..v0.1.4
- Commits in release: 2

### Build & Release

- chore: sync Cargo.lock for v0.1.4 (5f56182) - 1 file changed, 1 insertion(+), 1 deletion(-); areas: src-tauri/Cargo.lock.
- release: v0.1.4 (cb42054) - 8 files changed, 52 insertions(+), 20 deletions(-); areas: .github, docs, package.json, src-tauri/Cargo.toml.

## [0.1.3] - 2026-02-06

### Release Scope

- Commit range: v0.1.2..v0.1.3
- Commits in release: 3

### Features

- feat: add GitHub CLI commands to settings for enhanced functionality (4880cb3) - 1 file changed, 6 insertions(+), 1 deletion(-); areas: .claude.

### Build & Release

- release: v0.1.3 (ef805a2) - 4 files changed, 4 insertions(+), 4 deletions(-); areas: package.json, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/tauri.conf.json.
- chore: update version to 0.1.2 and enhance app metadata (ba389bb) - 9 files changed, 319 insertions(+), 6 deletions(-); areas: package-lock.json, src-tauri/Cargo.lock, src/App.tsx, src/components.

## [0.1.2] - 2026-02-06

### Release Scope

- Commit range: v0.1.1..v0.1.2
- Commits in release: 1

### Build & Release

- release: enforce version consistency and prepare v0.1.2 (8fc6bcc) - 5 files changed, 67 insertions(+), 3 deletions(-); areas: .github, docs, package.json, src-tauri/Cargo.toml.

## [0.1.1] - 2026-02-06

### Release Scope

- Commit range: v0.1.0..v0.1.1
- Commits in release: 3

### Features

- feat: add internal remarks field to work log entries and related components (ddfc4e6) - 36 files changed, 531 insertions(+), 73 deletions(-); areas: .claude, .github, migrations, package-lock.json.
- feat: Update README and CLAUDE documentation for installation and auto-updater (4fa528c) - 4 files changed, 162 insertions(+), 72 deletions(-); areas: .claude, README.md, docs, src-tauri/Cargo.lock.

### Refactoring

- refactor: Update synergy push method to prioritize API over Playwright (eecfff7) - 5 files changed, 41 insertions(+), 38 deletions(-); areas: src/components, src/stores.

## [0.1.0] - 2026-02-05

### Release Scope

- Commit range: v0.1.0 (initial history)
- Commits in release: 66

### Features

- feat: Add auto-updater via GitHub Releases (fad18d5) - 11 files changed, 530 insertions(+), 5 deletions(-); areas: .github, package-lock.json, package.json, src-tauri/Cargo.lock.
- feat: Integrate YouTube Music support and remove Spotify functionality (5e31dc2) - 12 files changed, 1217 insertions(+), 109 deletions(-); areas: .claude, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src.
- feat: Add web session push method for Synergy integration (fcaa09d) - 13 files changed, 2684 insertions(+), 102 deletions(-); areas: docs, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src.
- feat: Add support for conditional display of deliverable fields in worklog components (255aaf6) - 16 files changed, 1122 insertions(+), 150 deletions(-); areas: .cursor, scripts, src-tauri/src, src/components.
- feat: Add Synergy API push integration (9de3eaa) - 17 files changed, 1699 insertions(+), 8 deletions(-); areas: .claude, .cursor, migrations, src-tauri/src.
- feat: add bulk import functionality for worklog entries (71fb440) - 15 files changed, 2079 insertions(+), 107 deletions(-); areas: .cursor, migrations, src-tauri/src, src/components.
- feat(worklog): prevent drag/click handlers from firing on linked workflow button (5fe6fd8) - 1 file changed, 8 insertions(+); areas: src/components.
- feat(timers): implement multiple timers functionality in WorkLogPanel (5c19ce5) - 22 files changed, 1573 insertions(+), 44 deletions(-); areas: .claude, AGENTS.md, docs, src-tauri/Cargo.lock.
- feat(synergy): enhance Synergy login handling and update related scripts fix(synergy): correct script paths in error messages fix(synergy): improve session validation logic in worklog panel refactor(setupWizard): streamline Synergy login process and UI updates (0a7f438) - 13 files changed, 343 insertions(+), 56 deletions(-); areas: package-lock.json, scripts, src-tauri/src, src/components.
- feat(worklog): add legend visibility for worklog and workflow items (366a8bd) - 2 files changed, 203 insertions(+), 27 deletions(-); areas: src/components.
- feat(synergy): implement synergy import, scraper, and Playwright integration (f3e6d58) - 70 files changed, 9040 insertions(+), 26953 deletions(-); areas: .claude, .gitignore, scripts, src/components.
- feat: add detailed presentation guide for Developer Companion (f02e597) - 2 files changed, 627 insertions(+); areas: docs.
- feat: add synergyVerifiedAt field to work log entries and improve workflow item visibility logic (f3b0a7b) - 4 files changed, 3 insertions(+), 452 deletions(-); areas: ROOT_STRUCTURE.md, STRUCTURE.md, src/components, src/stores.
- feat: add archive filtering functionality to WorkLogPanel component (3f1a014) - 1 file changed, 365 insertions(+), 2 deletions(-); areas: src/components.
- feat: add BackgroundTasksPanel component for managing background tasks and scrapers (d980c5f) - 34 files changed, 2702 insertions(+), 55 deletions(-); areas: .claude, .cursor, README.md, docs.
- feat: add WorkLogTemplateSelector component with template management functionality (8b2d30c) - 87 files changed, 530 insertions(+), 8954 deletions(-); areas: .claude, .gitignore, AGENTS.md, CLAUDE.md.
- feat: add autostart functionality and portable distribution option (760d291) - 15 files changed, 832 insertions(+), 10 deletions(-); areas: .claude, .cursor, migrations, package-lock.json.
- feat: implement worklog templates feature (63249fc) - 9 files changed, 947 insertions(+), 4 deletions(-); areas: .cursor, CLAUDE.md, README.md, migrations.
- feat: Implement Command Palette with various commands and hotkeys (151400e) - 16 files changed, 1258 insertions(+), 30 deletions(-); areas: .cursor, CLAUDE.md, IMPROVEMENTS.md, README.md.
- feat: add comprehensive improvement proposals for Developer Companion, focusing on LLM integration, UI/UX enhancements, automation, and technical architecture (99078f4) - 1 file changed, 357 insertions(+); areas: IMPROVEMENTS.md.
- feat: add CLAUDE.md for project guidance and command reference (086bdb0) - 1 file changed, 209 insertions(+); areas: CLAUDE.md.
- feat: add RSS discovery and testing panels for Synergy integration (06abc20) - 10 files changed, 1902 insertions(+), 2 deletions(-); areas: scripts, src-tauri/capabilities, src-tauri/src, src/components.
- feat: add export and synergy tools components with modals for enhanced functionality (abfac35) - 30 files changed, 2301 insertions(+), 490 deletions(-); areas: .claude, .cursor, DELIVERABLES_SCRAPER_PROGRESS.md, PROJECT_PLAN.md.
- feat: enhance WorkLogBlockDialog with flexible duration input parsing and validation (c6958e9) - 1 file changed, 135 insertions(+), 75 deletions(-); areas: src/components.
- feat: implement Synergy RSS auto-fetch functionality with settings in the UI (fc9297d) - 4 files changed, 158 insertions(+), 3 deletions(-); areas: src/App.tsx, src/components, src/hooks, src/stores.
- feat: update secure credential storage details in README and add dedicated section (76af180) - 1 file changed, 14 insertions(+), 2 deletions(-); areas: README.md.
- feat: add secure credential storage and retrieval functionality (1709d30) - 4 files changed, 156 insertions(+), 68 deletions(-); areas: src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src, src/components.
- feat: add WorkLogCalendar component with drag-and-drop functionality for work log entries (6c128a4) - 14 files changed, 2232 insertions(+), 17 deletions(-); areas: .claude, .cursor, package-lock.json, src/App.tsx.
- feat: add synergy workflow panel and related functionality (fc16e8f) - 14 files changed, 2002 insertions(+), 17 deletions(-); areas: .cursor, migrations, src-tauri/Cargo.lock, src-tauri/Cargo.toml.
- feat: switch browser from Chromium to Firefox in scraping scripts (28a2853) - 8 files changed, 21 insertions(+), 14 deletions(-); areas: package-lock.json, scripts.
- feat: implement migration for work log sync status and update database schema (eb51fed) - 11 files changed, 492 insertions(+), 208 deletions(-); areas: apply-migration-010.bat, migrations, scripts, src/components.
- feat: add synergy projects and customers scrapers (d773acf) - 18 files changed, 36754 insertions(+), 15 deletions(-); areas: .claude, migrations, package-lock.json, package.json.
- feat: implement secure storage for Synergy credentials and enhance settings management (9042d0e) - 12 files changed, 217 insertions(+), 32 deletions(-); areas: AGENTS.md, README.md, setup.bat, setup.sh.
- feat: enhance Synergy integration with new commands and add notification plugin (2e3e967) - 6 files changed, 63 insertions(+), 37 deletions(-); areas: .cursor, AGENTS.md, package.json, scripts.
- feat: update Tauri script for improved Visual Studio integration and modify package.json for script execution (e4bbe9f) - 4 files changed, 127 insertions(+), 2 deletions(-); areas: README.md, package-lock.json, package.json, scripts.
- feat: integrate Playwright for Synergy automation and enhance settings management (7f02300) - 16 files changed, 1865 insertions(+), 34 deletions(-); areas: .cursor, README.md, package-lock.json, package.json.
- feat: integrate Synergy functionality into work log and application bootstrap (6cd9892) - 21 files changed, 9959 insertions(+), 11417 deletions(-); areas: .cursor, migrations, package.json, public.
- feat: enhance app functionality with new panels and work log improvements (75f40ed) - 17 files changed, 20469 insertions(+), 254 deletions(-); areas: src/App.tsx, src/components, src/hooks, src/stores.
- feat: enhance project plan and README with new features and setup instructions (c87cd5b) - 47 files changed, 2265 insertions(+), 274 deletions(-); areas: AGENTS.md, PROJECT_PLAN.md, README.md, migrations.
- feat: enhance notification settings and special day blocks management (98117c1) - 19 files changed, 1515 insertions(+), 111 deletions(-); areas: README.md, migrations, src-tauri/Cargo.toml, src-tauri/capabilities.
- feat: implement work log and todo features with UI components (b3bd907) - 7 files changed, 566 insertions(+), 11 deletions(-); areas: README.md, src/App.tsx, src/components, src/stores.
- feat: add day management and wellness features (4e22fbd) - 25 files changed, 1777 insertions(+), 146 deletions(-); areas: .gitignore, README.md, migrations, package-lock.json.
- feat: initialize Tauri application with SQLite integration and basic todo functionality (18dd4a8) - 52 files changed, 9349 insertions(+), 8 deletions(-); areas: .gitignore, .vscode, PROJECT_PLAN.md, README.md.

### Fixes

- fix: Pin @tauri-apps npm packages to 2.9.x to match Rust crate versions (f58f3dd) - 2 files changed, 11 insertions(+), 11 deletions(-); areas: package-lock.json, package.json.
- fix(synergy): use JavaScript approach for date/time fields when Playwright locator fails (56afd26) - 1 file changed, 89 insertions(+), 67 deletions(-); areas: scripts.
- fix(synergy): fix time field input detection and add value verification (e2d151b) - 1 file changed, 1931 insertions(+); areas: scripts.
- fix: correct code block formatting in README and remove outdated Synergy setup instructions (59de00a) - 1 file changed, 1 insertion(+), 22 deletions(-); areas: README.md.

### Refactoring

- Refactor scraper execution to use node sidecar and improve dependency management (152e5c5) - 22 files changed, 361 insertions(+), 1509 deletions(-); areas: .gitignore, scripts, src-tauri/build.rs, src-tauri/capabilities.
- refactor(worklog): improve WorkLogBlockDialog and WorkLogCalendar components (bcd62be) - 11 files changed, 2169 insertions(+), 235 deletions(-); areas: docs, scripts, src-tauri/capabilities, src/components.
- Refactor Synergy Base URL handling across components and stores (16257ce) - 14 files changed, 81 insertions(+), 357 deletions(-); areas: src/App.tsx, src/components, src/hooks, src/stores.
- Refactor code structure for improved readability and maintainability (a950297) - 16 files changed, 9955 insertions(+), 222 deletions(-); areas: fix-migrations.sql, migrations, src-tauri/Cargo.lock, src-tauri/Cargo.toml.

### Documentation

- CSP + file-read restricties + README/setup fix + quality gates (lint/format/typecheck). (261589d) - 138 files changed, 7957 insertions(+), 5184 deletions(-); areas: .prettierignore, .prettierrc.json, README.md, docs.

### Other Changes

- Remove outdated plans for potential improvements, Spotify widget implementation, automation enhancements, and bulk import features. These files have been deleted as they are no longer relevant to the current project direction. (fdfbdc1) - 22 files changed, 302 insertions(+); areas: .cursor, src/App.tsx, src/components, src/stores.
- Spotify Plan (25e700b) - 12 files changed, 1745 insertions(+), 4 deletions(-); areas: .cursor, src-tauri/Cargo.lock, src-tauri/Cargo.toml, src-tauri/src.
- Enhance scraper navigation and debugging capabilities; update installer to use WebView2 bootstrapper (3210720) - 6 files changed, 62 insertions(+), 17 deletions(-); areas: scripts, src-tauri/tauri.conf.json, src/App.tsx.
- Builden v1 (7a0e425) - 6 files changed, 221 insertions(+), 27 deletions(-); areas: .gitignore, README.md, scripts, src-tauri/src.
- Betere kalenderlaadtijden (6879638) - 5 files changed, 1052 insertions(+), 73 deletions(-); areas: scripts, src-tauri/src, src/components, src/services.
- Remove RSS from fetching data (ced89ff) - 5 files changed, 817 insertions(+), 144 deletions(-); areas: scripts, src-tauri/capabilities, src/components.
- Remove Sessions Functionality (0034a6f) - 10 files changed, 5 insertions(+), 2314 deletions(-); areas: docs, package-lock.json, src-tauri/src, src/components.
- Spint2 en bugfixes (99aa9b7) - 19 files changed, 3028 insertions(+), 368 deletions(-); areas: .cursor, .gitignore, .prettierignore, scripts.
- English (54e60ee) - 52 files changed, 1019 insertions(+), 885 deletions(-); areas: README.md, docs, migrations, src-tauri/src.
- SynergyFixes (75d0be7) - 5 files changed, 136 insertions(+), 21 deletions(-); areas: migrations, src-tauri/src, src/components, src/services.
- Add output files for synergy push process with detailed logs (c708556) - 22 files changed, 6270 insertions(+), 104 deletions(-); areas: AGENTS.md, scripts, src/components, src/services.
- Add output logs for synergy push process (716913f) - 39 files changed, 12831 insertions(+), 138 deletions(-); areas: AGENTS.md, DELIVERABLES_SCRAPER_PROGRESS.md, README.md, migrations.
- Merge branch 'main' of https://github.com/vanachterjacob/DeveloperCompanion (6302426) - 80 files changed, 22991 insertions(+), 412 deletions(-); areas: README.md, package-lock.json, package.json.
- Add initial project plan and functional requirements for Developer Dag Companion (4316634) - 1 file changed, 928 insertions(+); areas: PROJECT_PLAN.md.

## Older History

See [commit history](https://github.com/vanachterjacob/DeveloperCompanion/commits/main) for complete details.
