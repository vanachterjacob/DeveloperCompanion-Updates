# Changelog

All notable changes to DeveloperCompanion will be documented in this file.

## [0.1.11] - 2026-02-10

### Bug Fixes

- **Weather Widget**: Fixed city search timeout issue - added 5s timeout and better error handling for geocoding API

## [0.1.10] - 2026-02-10

### Bug Fixes

- **Update Banner**: Fixed release notes text color for light mode visibility

## [0.1.9] - 2026-02-10

### New Features

- **Weather Widget**: Enhanced weather widget and modal with location settings and geocoding support (#25f2c83)

### Bug Fixes

- **Release Notes**: Fixed "Full release notes" URL to correctly point to public updates repository (#ee91d76)
- **Changelog Publishing**: Added automatic CHANGELOG.md upload to public updates repo during release workflow

## [0.1.8] - 2026-02-10

### New Features

- **Local Commit Scanning**: Integrated commit scanning with enhanced work item link management (#18f3e86)

### Improvements

- **Security**: Enhanced security and sanitization across components (#ca11c2e)
- **Code Quality**: Upgrade work item filtering and enhanced PR handling (#...)

### Documentation

- Updated documentation and improved formatting consistency (#9b02004)
- Removed outdated additional edge case hardening plan document (#e6842e7)

## [0.1.7] - 2026-02-10

### New Features

- **Release Notes**: Fixed release notes URL to point to public updates repository

## [0.1.6] - 2026-02-09

### New Features

- **Azure DevOps Integration**: Full DevOps integration with settings management, automatic time logging, project mapping, organization selection, and work item sorting (#4b0d130, #817af6a, #88b42da, #6409f9f)
- **Build Dashboard**: New BuildDashboard with inline commenting, navigation, state change notifications, and work item logging (#91bee76, #491c162, #c2946f1)
- **News Feed**: Integrated news feed functionality with AI and BC groups (#93f9821, #b538971)
- **Synergy Enhancements**: Project and customer selection in TodoPanel, URL handling across components (#c8593ab, #a5e6266)
- **Scraper Progress Tracking**: Enhanced scraper components with progress tracking, estimation, and state management (#d3bee7e, #a7db3bc)
- **OpenAI Codex CLI**: Added support for OpenAI Codex CLI with enhanced settings UI (#f01f945)
- **Settings UI**: New SettingsGroup component for better settings organization (#ada0374)
- **Testing**: Added Vitest support for unit testing (#7227bc6)
- **Notifications**: Added notification grace period setting (#7227bc6)
- **Audio**: Enhanced audio state management during track transitions (#165e680)
- **UX**: Enhanced button titles for improved user experience (#1c40c01)

### Bug Fixes

- Improved settings button behavior and UI consistency (#def5a21)
- Enhanced error handling and JSON parsing across components (#f2e986c)

### Refactoring

- Removed sync verification feature and related settings (#8ca8b1a)
- Simplified SQL migration inclusion in database migrations (#8f73fa4)
- Updated setup scripts and enhanced CLI engine options (#a5c3e57)
- Streamlined documentation and enhanced agent guidelines (#e3a36d6)

### Documentation

- Updated documentation for development commands and architecture details (#ec4d437)
- Updated agents guide (#822ff71)

## [0.1.5] and earlier

See [commit history](https://github.com/vanachterjacob/DeveloperCompanion/commits/main) for previous changes.
