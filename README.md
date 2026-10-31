# Popcorn Palace for Windows

Portable desktop port of Popcorn Palace Mobile, based on the Android 0.6.24 behavior. For Windows 10/11 **64-bit (x64)**.

## Install and run

1. Download the Windows `.zip` from the latest release.
2. Right-click it and choose **Extract All**. Keep the entire **PopcornPalace** folder together, in a folder you can write to.
3. Open **PopcornPalace.exe** inside that extracted folder.

No Java, VLC, Android emulator or separate browser runtime is required. This first beta is not Authenticode signed. It has been packaged and tested with automated parser/library/UI checks; installation and streaming still need real Windows verification.

## Site verification

Use **Verify site**, complete any site check in the page below the toolbar, then choose **Return to app**. The app also checks once after the site page finishes loading. It returns automatically only when its own catalogue request succeeds, then retries your interrupted action. If access is still blocked, the window stays open and shows the result; closing it does not claim verification succeeded.

## Features copied from Android

- Discover and category navigation: Movies, TV Shows, anime sub/dub movies/series and Audiobooks, with genre filters and sort controls.
- Search remains in the selected catalogue. Discover searches everything. Anime evidence checks use title genres/countries and matching known editions; unverified classifications are withheld in restricted searches.
- Title details, cover/banner art, season buttons and numeric episode ordering.
- Favorites with multiple custom categories and type/edition overrides; category creation, rename and removal.
- Watched-only Watch History and Finished Episodes, grouped by show/season. Unwatched episodes appear in Continue Watching. Remove a title from Continue Watching with Undo while retaining its history.
- Saved resume position, approximate watch time, manual watched/unwatched overrides, automatic watched marking at 95% or the end, and Next marking the episode being left watched.
- Video and audiobooks, seek/volume/full screen, keyboard shortcuts, and system media controls when supported.
- Playback continues when minimized or locked. Opening another list in the app pauses it. Closing the window exits.
- Android/Windows history/favorites backup import and export. This is a manual transfer; it is not automatic cloud sync. Import backs up existing data and merges newer records.
- Normal visible site verification, session clearing, bounded local diagnostic logs and offline changelog.

## Updates

**Upgrading from beta 1 or beta 2:** if Install and restart closes the app without reopening, download the latest ZIP from Releases, extract **all** files into a new writable folder, and run `PopcornPalace.exe`. This one-time manual update installs the corrected updater. History and favorites remain in your Windows profile.

This repository is independent of the Android repository. The app checks `windows-update.json` when it opens and periodically when it returns to the foreground. Updates require approval, then download from this repository's GitHub Releases. The app validates the exact repository/asset URL, version, byte size and SHA-256 before offering **Install and restart**.

The portable updater uses Windows PowerShell to check the checksum again, extract the package and save a rollback copy before the app closes. Once ready, it waits for the app to exit, replaces application files in place with retries for locked files, and restarts it. It does not rename the installation directory. Your library stays in your Windows user profile, outside the app folder. Replaced files are retained under the app profile’s `updates/install-…/previous` directory for rollback. Numeric install stages and Windows error codes are included in exported diagnostics. Folders that require administrator rights cannot be updated automatically; extract a new download into a writable folder instead.

## Shortcuts

- Space: play/pause, while Player is focused.
- Left/right arrows: seek 10 seconds.
- F: full-screen player; Escape exits full screen.
- F11: full-screen window.
- Ctrl+F: search. Ctrl+plus/minus: interface zoom.

## Privacy and limits

History, favorites, settings and site cookies stay on your PC. Diagnostics contain fixed event names/numbers and OS/app version details, not titles, searches, full URLs, cookies, headers, credentials or response contents. Nothing is uploaded automatically except ordinary catalogue/media/update requests. Export logs only when you choose.

The catalogue and streaming depend on NEPU and supported codecs. Verification must be completed by the user; no CAPTCHA bypass, DRM removal or protected-embed circumvention is included. Offline media downloading and subtitles are not currently offered, matching the Android build. Chromium/hls.js is a different player from Android Media3, so supported streams may differ. Audiobooks depend on the source publishing a usable navigation link or search result.

This repository hosts **release packages and publishing metadata/documentation only**. Application source is private. The Electron package necessarily contains compiled/packaged application code needed to run; it is not a source-code protection mechanism. No signing keys, API keys, site sessions or user logs belong in this repository.

Independent project; not affiliated with NEPU, Popcorn Palace, VRChat, Microsoft or Electron.
