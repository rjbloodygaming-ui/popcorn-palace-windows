# Windows changelog

## 0.1.0-beta.5 — 2026-10-30

### Added

- PopcornPalaceUpdater.exe: a separate Windows updater with download progress and its own Install and restart button. The runtime is bundled; users do not need to install .NET.
- Direct updater launch support. Both app-launched and directly launched updates run from a temporary copy outside the installation folder, allowing both EXEs to be replaced.

### Fixed

- The main app stays open through download, checksum verification, extraction and rollback preparation. Only the updater’s confirmed install step requests app exit.
- Native download verification, bounded ZIP extraction, file-lock retries and rollback replace the PowerShell installation helper.

### Changed

- The app’s update prompt now opens the separate updater window. Download and installation are performed by the second EXE. Saved history and favorites remain in the Windows profile.
- The site-verification issue remains unresolved. Existing numeric verification diagnostics are retained.

## 0.1.0-beta.4 — 2026-10-30

### Added

- Diagnostic build for the unresolved Windows verification failure. Observes whether the browser and background requests send cookies, whether the clearance cookie is present, and the resulting HTTP status.
- Cookie-store presence and metadata checks, same-origin redirect flags, and separate challenge-header/markup flags. Logs contain numeric flags and counts only; cookie values, URLs, titles, credentials and raw headers are never recorded.

### Fixed

- The verification toolbar now identifies the rejected application check and displays its HTTP status instead of repeatedly asking for an already completed site check.

### Changed

- Automatic access checking runs once per verification window; further checks require Return to app. Network requests, cookies and browser protections are not modified by the observers.
- This is an investigation build, not a confirmed verification fix. Open Verify site, let the page load, select Return to app once, close the window and export diagnostics.

## 0.1.0-beta.3 — 2026-10-30

### Added

- Numeric update installation stages, Windows error codes and rollback status in exported diagnostics.
- A visible preparing-update state that prevents repeated install clicks.

### Fixed

- Replaced whole-folder renaming with in-place application file replacement, with retries for files still locked by Windows.
- The app stays open while the update helper checks the package, extracts it, tests write access and saves rollback files. It only exits after the helper reports ready.
- Preparation errors remain visible in the app. Failed replacement attempts restore saved files and reopen the previous app when recovery succeeds.

### Changed

- Users on beta 1 or beta 2 whose installer closes without restarting should manually extract this ZIP into a new writable folder once. Saved history and favorites remain in the Windows profile.

## 0.1.0-beta.2 — 2026-10-30

### Added

- Verification-stage and parsed-catalogue-count events in the existing privacy-filtered local diagnostics.

### Fixed

- The site-verification window now has a persistent Return to app toolbar. It confirms catalogue access using the same session before returning and retrying the interrupted search, title or episode.
- Closing or cancelling verification no longer reports successful verification. Failed checks stay visible in the window; completion never overrides a different screen opened later.
- Ordinary pages containing a Cloudflare Turnstile widget are no longer automatically treated as blocked pages. Actual challenge response headers and interstitials are still respected.
- Application requests retain the verified browser user agent and same-origin request context while keeping cookies restricted to their original origin.

### Changed

- The site remains in an isolated browser view with no application bridge or Node access. The Return to app toolbar is trusted local content. No challenge solving or protection bypass is automated.

## 0.1.0-beta.1 — 2026-10-30

### Added

- First Windows 10/11 x64 portable build, following the Android 0.6.24 app's catalogue, category, search and library behavior.
- Discover, Movies, TV Shows, anime sub/dub movie/series sections, Audiobooks, genre filters and sorting. Search stays in the selected section; Discover searches all categories.
- Title details, season selectors and numerically ordered episode lists, favorites with multiple custom categories, watched-only history/finished sections, and Continue Watching removal with Undo.
- Video and audiobook playback, resume positions, approximate watch time, manual watched toggles, automatic watched marking near completion, and Next episode marking the episode being left as watched.
- Keyboard and mouse controls, full screen, volume, seeking, minimized playback and system media controls where supported by Windows.
- Android/Windows JSON backup import and export, visible site verification and session clearing, local diagnostic viewing/export/disable/clear, and offline changelog.
- Independent Windows GitHub update checks on opening/foreground, size/SHA-256 verification, and confirmed installation/restart for portable installations.

### Changed

- Windows uses Chromium and hls.js rather than Android Media3. Codec and site compatibility require testing on a Windows PC.
- Closing the window exits the app; minimizing it continues playback. Opening an in-app list pauses playback, matching Android.
- Public repository contains release packages, update metadata and documentation. Development source and user data are kept private. No app source or session logs are published separately.
