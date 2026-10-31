# Windows changelog

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
