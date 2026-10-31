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

`PopcornPalaceUpdater.exe` is a separate, self-contained Windows program included beside `PopcornPalace.exe`. Choose **Open updater** in the app: the updater opens its own progress window, downloads the ZIP, checks its size and SHA-256, extracts it and saves rollback files while the main app stays open. Choose **Install and restart** in the updater to close the app, replace the files in place and restart it. The updater runs from a copy outside the installation folder so both EXEs can be replaced. It does not use PowerShell and does not require a separate .NET installation. Your library stays in your Windows profile. Rollback copies remain under the profile’s `updates/updater-…/previous` directory. Numeric failure stages are included in exported diagnostics. Folders that require administrator rights cannot be updated automatically; extract a new download into a writable folder instead. You can also open `PopcornPalaceUpdater.exe` directly; from beta 7 it closes the matching main app automatically before replacement, including when launched directly. It requests normal window closure and waits for matching main/player processes. If they remain unresponsive, it offers a force-close limited to that installation. Declining or a persistent file lock stops replacement. The updater itself and other installation folders are excluded.

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

## Windows verification investigation

The verification issue remains unresolved in beta 5. The beta 4 diagnostic procedure below still applies.

Beta 4 is a diagnostic build for the unresolved case where the website opens but the app catalogue request receives HTTP 403. It is not a confirmed access fix. With local diagnostic logging enabled, open **Verify site**, let its page load, select **Return to app** once, close the window, then use **Settings → Diagnostics → Export logs**. Observers record only client/route classes, cookie-presence flags, counts, response statuses and challenge flags. They do not modify requests, cookie values or browser protections. Logs remain local until explicitly exported.

## Opt-in cookie-exclusion diagnosis (beta 6)

Open **Verify site**, let its page load, and choose **Diagnose**. A native confirmation explains the privacy details before anything is captured. With local logging enabled, the action records a bounded metadata-only network trace during one ordinary catalogue check. Temporary metadata can include URLs/network details, but sensitive capture modes are never enabled. The app saves only request/cookie counts and fixed exclusion-reason codes to exported diagnostics, then deletes the temporary trace. Cleanup failures are reported and stale app-owned traces are retried at next startup. Raw traces are never included in diagnostic export.

After diagnosis, close the verification window and use **Settings → Diagnostics → Export logs**. The summary covers cookies considered for that request; cookie names and values are excluded, so reasons are not assigned to named individual cookies. A missing matching request/event is inconclusive. This remains an investigation build, not a confirmed verification fix. It does not change requests, browser identity or access protections.

## Installing the beta 7 updater change

To use the new shutdown behavior while updating an older build, close any previous updater window, download **PopcornPalaceUpdater.exe** and **UPDATER-NOTICES.txt** from the beta 7 release, place them beside your existing **PopcornPalace.exe**, then run the new updater. On **Install and restart**, it closes the matching app and checks file release before replacing anything. Alternatively, extract the full beta 7 ZIP into a new writable folder. History and favorites stay in the Windows profile.
