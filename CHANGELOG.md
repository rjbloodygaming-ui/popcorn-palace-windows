# Windows changelog

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
