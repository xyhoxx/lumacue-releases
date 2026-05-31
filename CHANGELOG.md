# LumaCue Changelog

Product release notes for LumaCue desktop builds. Public releases contain built installer and update artifacts only.

## 0.3.1 - Auto-Refund Channel Points

### Added
- Channel-point redemptions are now refunded automatically when a song never plays — skipped, removed, queue cleared, or unplayable (e.g. age-restricted).
- Redemptions are fulfilled only once the song actually starts playing (works for both the normal player and the yt-dlp direct-audio fallback); songs that play even briefly are not refunded.
- Added a toggle in the Twitch panel's Redemptions card (default on). Pending redemptions persist across restarts.

### Notes
- With the toggle off, redemptions are fulfilled at queue time, as before.

## 0.3.0 - Spotify Link Requests

### Added
- Added Spotify track link support for Quick Add and Twitch Channel Points redemptions.
- Supported `open.spotify.com/track`, locale-prefixed Spotify links, and `spotify:track:` URIs.
- Spotify tracks are resolved through the public embed metadata page, then matched to YouTube Music / YouTube playback candidates.

### Notes
- Spotify playlists are not imported; viewer requests remain single-track requests.
- Age-restricted YouTube videos still require sign-in and are skipped when they cannot be played reliably.

## 0.2.28 - Learning Rule Persistence

### Fixed
- Preserved the original request query through queue and playback state so "Always pick this" rules are keyed to the viewer's actual search text.
- Fixed repeated broadcaster connection toasts so the notification dismisses normally.

## 0.2.27 - Device Login Visibility

### Fixed
- Fixed Twitch device-code approval panels remaining visible after the account was connected.

## 0.2.26 - Encrypted Twitch Tokens

### Added
- Encrypted saved Twitch access and refresh tokens with Windows DPAPI for the current Windows user.
- Added automatic migration from plaintext token storage to encrypted token storage.

### Changed
- Twitch device-code login now completes automatically after approval without requiring a separate Approved button.

## 0.2.25 - Twitch Panel Status and Persistence

### Fixed
- Twitch account status now reflects token expiry instead of only checking whether a token is stored.
- Connected and disconnected action buttons now update correctly.

### Improved
- Twitch device login auto-polls after approval.
- Selected Channel Points reward and bot test message settings persist across restarts.
- Twitch status refreshes while the Twitch panel is open.

## 0.2.24 - Standalone Player Control Layout

### Fixed
- Fixed the visual toggle displacing album art and overlapping playback controls outside desktop-shell mode.

## 0.2.23 - Thai Title Ambiguity Detection

### Fixed
- Improved ambiguity detection for Thai song titles embedded inside mixed-script YouTube video titles.
- Included YouTube video search results when checking same-title alternatives.

## 0.2.22 - Twitch Auto Token Refresh

### Fixed
- Added background refresh for Twitch access tokens during long sessions.
- Retried chat and redemption status calls once after token refresh when Twitch returns 401.

### Notes
- Accounts saved before refresh-token support may need one reconnect.

## 0.2.21 - Learned Thai Title Matching

### Improved
- Learned resolver rules can match shortened or expanded Thai titles for future searches.
- Collaboration text in artist/title hints is ignored when matching learned rules.

## 0.2.20 - Direct Audio Handles Embed Blocks

### Fixed
- Removed the backend pre-resolve embed rejection so embed-blocked YouTube videos can use the direct audio fallback.

## 0.2.19 - Direct Audio Streaming

### Added
- Added yt-dlp direct audio fallback for YouTube videos that cannot be embedded.
- Added local Range-request audio proxy support for seeking.
- Added background yt-dlp update checks and short-lived audio URL caching.

## 0.2.18 - Embed Fallback Filtering

### Fixed
- Rejected live, concert, session, and other version variants during embed-fallback searches unless requested.
- Added clearer chat feedback when no playable embed alternative is available.

## 0.2.17 - Pre-Resolve Embed Check

### Fixed
- Added a pre-resolve oEmbed check to avoid queuing videos known to block embedding.
- Cached embed-block checks per session.

## 0.2.16 - Embed Error Fallback

### Fixed
- Added player-side fallback search when the YouTube IFrame player reports embed errors.
- Blocked failed video IDs for the current query before trying alternatives.

## 0.2.15 - Numbered Ambiguity Selection

### Added
- Viewers can answer Twitch ambiguity prompts with `1`, `2`, or `3` instead of typing an artist name.

## 0.2.14 - Channel Points Reward Selector

### Added
- Added a Twitch reward dropdown for selecting an existing manageable Channel Points reward.

### Fixed
- Persisted Channel Points reward title, cost, and prompt across app restarts.

## 0.2.13 - Teach by URL Fixes

### Fixed
- Teach dialogs now preserve the original request query when saving rules.
- YouTube-only videos can be pinned by URL even when they do not appear in YTMusic song results.

## 0.2.12 - Resolver Guard Fixes

### Fixed
- Disabled cross-script top-result trust for mixed Thai + English artist queries.
- Added a minimum-view threshold for exact-title ambiguity alternatives.
- Added the `sukuyaki` to `sukiyaki` query alias.

## 0.2.11 - Quick Add Result Count

### Changed
- Increased Quick Add suggestions from 6 to 12.
- Increased backend candidate caps and dropdown height for easier comparison.

## 0.2.10 - Suggestion Ranking

### Fixed
- Merged song and video fallback candidates before ranking Quick Add suggestions.
- Used the full mixed-language query for video fallback searches.

## 0.2.9 - Artist Hint Guard

### Fixed
- Tightened compact-text matching for short Thai titles.
- Rejected candidates whose artist does not match the English artist hint in mixed Thai + English queries.

## 0.2.8 - Video Search Fallback

### Added
- Added YouTube video-search fallback for artists that are missing from the YTMusic song catalog.

## 0.2.7 - Launcher Self-Update and EventSub Stability

### Fixed
- Normalized zip paths during launcher self-update extraction.
- Fixed EventSub 429 reconnect storms with longer cooldown behavior.
- Refreshed expired Twitch tokens before EventSub reconnects.
- Made EventSub stop signals interrupt reconnect sleep.

## 0.2.6 - EventSub Reconnect Stability

### Fixed
- Added cooldown handling for Twitch EventSub 429 rate-limit responses.
- Refreshed expired Twitch tokens at startup and before EventSub reconnects.
- Made EventSub worker stop signals interrupt reconnect sleep promptly.

## 0.2.5 - Thai Split Search Fallback

### Fixed
- Added Thai-title-only fallback searches for mixed Thai + English artist queries.

## 0.2.4 - Teach by YouTube URL

### Added
- Added YouTube URL input to Teach dialogs so a specific video can be pinned for future requests.

## 0.2.3 - Queue Drawer and Resolver Tuning

### Fixed
- Prevented queue drawer animations from resetting rows during live queue updates.
- Fixed drag-to-reorder after skip operations.
- Raised queue drawer preview capacity to 20 tracks.
- Increased penalties for unrequested live/session versions.

## 0.2.2 - Startup and IPC Performance

### Improved
- Lazy-loaded YTMusic to reduce Flask startup delay.
- Reduced Electron progress IPC payload size.
- Cached queue preview/order data between full playback-state updates.

## 0.2.1 - Desktop and Player Animations

### Added
- Added GSAP-based motion for desktop toasts, teach dialogs, navigation transitions, queue rows, Quick Add suggestions, web player transitions, and OBS overlay song changes.

## 0.2.0 - Resolver Learning

### Added
- Added Teach dialogs explaining why a result was selected.
- Added resolver learning actions: Always pick, Never pick, and Pick this.
- Added Learned Rules panel with import, export, reset, and delete actions.
- Added backend APIs for resolver learning management.

## 0.1.42 - Update Verification and Build Pipeline

### Added
- Added SHA-512 verification for setup-stub downloads.
- Added launcher SHA-512 fields to `lumacue-update.json`.
- Added launcher version display.
- Added `build:release` and `release` scripts for the full release pipeline.

## 0.1.41 - Uninstall and Launcher Self-Update

### Added
- Added launcher self-update support from release manifest data.
- Added retry UI to the setup stub.
- Added extraction progress in the setup stub.

### Fixed
- Fixed Windows uninstall behavior.
- Fixed release-note encoding for GitHub release text.

## 0.1.40 - Installer Naming

### Changed
- Renamed online and offline setup artifacts to make installer behavior explicit.

## 0.1.39 - Native Setup Experience

### Changed
- Replaced the NSIS web installer UI with a small native setup stub that downloads and installs the Electron launcher.

## 0.1.38 - ASAR Extraction

### Fixed
- Fixed update extraction failures on `resources/app.asar` by using Electron's `original-fs` for extraction writes.

## 0.1.37 - Web Installer

### Added
- Added web-installer flow that installs the launcher first, then downloads the app package through the LumaCue launcher UI.
- Added first-install detection in the launcher.

### Fixed
- Fixed first-run loops when launcher version matched the manifest but no app package was installed yet.

## 0.1.36 - Silent Installer Launch

### Fixed
- Fixed post-install app launch when the installer runs in silent mode.

## 0.1.35 - Hidden Installer Attempt

### Fixed
- Improved hidden-window behavior for the installer and post-install launch path.

## 0.1.34 - Installer Window Suppression

### Fixed
- Suppressed the visible NSIS installer window so the LumaCue launcher remains the primary install UI.

## 0.1.33 - Launcher-First Install UI

### Changed
- Installed silently in the background while the LumaCue launcher provides visible install progress.

## 0.1.32 - Patch Staging Copy

### Fixed
- Excluded `python_portable` from patch staging copies to keep patch application fast.

## 0.1.31 - Silent Installer with Launcher UI

### Changed
- Switched to one-click silent per-user installs and opened the launcher immediately after install.

## 0.1.30 - Faster Restart to Apply

### Fixed
- Restart-to-apply updates now route through the custom launcher and app-only package path where available.

## 0.1.29 - Custom Update Dialog

### Changed
- Replaced the native update-ready dialog with a LumaCue-styled dark dialog.

## 0.1.28 - Single Instance and Launcher Cleanup

### Fixed
- Enforced a single running LumaCue instance.
- Enforced a single launcher window.
- Removed the launcher footer's "Custom updater" label.

## 0.1.27 - Patch Update and Launcher UI Fixes

### Fixed
- Fixed patch extraction after moving away from `extract-zip`.
- Made patch staging asynchronous so the launcher stays responsive.
- Removed transparent-window ghost-card artifacts.
- Prevented long error details from overflowing the launcher card.

## 0.1.26 - Download Cache Cleanup

### Changed
- Deleted old cached update zips after successful updates.

## 0.1.25 - Fresh Install Detection

### Fixed
- Avoided redundant downloads immediately after installing the same version through the NSIS installer.

## 0.1.24 - Streaming Extraction

### Fixed
- Replaced memory-heavy zip extraction with streaming extraction to prevent heap out-of-memory crashes.

## 0.1.23 - Faster Extraction and Cache

### Improved
- Switched update extraction to fflate for faster concurrent file writes.
- Added verified download cache reuse.

## 0.1.22 - JavaScript Extraction Only

### Fixed
- Removed PowerShell extraction to avoid antivirus false positives.

## 0.1.21 - Launcher Freeze Fix

### Fixed
- Moved old-app cleanup off the main launcher path so the UI can transition to app launch immediately after update apply.

## 0.1.20 - EventSub Status and Patch Stability

### Fixed
- Auto-refreshed EventSub status after starting the listener.
- Fell back safely when patch updates cannot be applied on fresh installs.
- Removed remaining launcher ghost-card artifacts.

## 0.1.19 - EventSub Dual Connections

### Fixed
- Split broadcaster and bot EventSub subscriptions onto separate WebSocket connections to satisfy Twitch token ownership rules.

## 0.1.18 - Native Extraction Path

### Fixed
- Ensured native Windows extraction is attempted before JavaScript fallback.

## 0.1.17 - Update Extraction Progress

### Improved
- Added per-file update extraction progress.
- Added native Windows ZipFile extraction with JavaScript fallback.

## 0.1.16 - EventSub Subscription Cleanup

### Fixed
- Cleaned stale Twitch EventSub subscriptions before creating new ones after reconnects.

## 0.1.15 - Twitch Login Mismatch Guard

### Fixed
- Added a preflight Client-ID check before Twitch reward sync.

## 0.1.14 - Runtime Split Manifest

### Added
- Added app-only and runtime package entries to the custom update manifest.
- Added launcher support for installing shared runtime packages.
- Kept full package fallback for older launchers.

## 0.1.13 - Legacy Launcher Compatibility

### Fixed
- Prevented duplicate startup windows when opened by older launchers.

## 0.1.12 - Unified Startup Handoff

### Fixed
- Kept the updater window visible until the desktop shell is ready.
- Removed the outer startup card surface.
- Adjusted zip entry order so shallow app files are extracted earlier.

## 0.1.11 - Patch Updater Transition

### Added
- Added patch-aware custom update support.
- Added shared runtime migration support.
- Added patch package generation.

### Changed
- Launcher-spawned apps can receive a shared runtime path.
- Patch updates apply over staged installed apps and fall back to full packages.

## 0.1.10 - About Panel Cleanup

### Fixed
- Removed duplicate runtime status card from About / Updates.
- Wrote GitHub release notes as UTF-8 without BOM.

## 0.1.9 - Native Zip Update Apply

### Fixed
- Replaced PowerShell update extraction with in-process Node extraction.
- Added staged app validation and safer promotion into versioned app folders.

## 0.1.8 - Launcher Handoff Cleanup

### Fixed
- Prevented launcher-spawned apps from running the legacy startup updater after handoff.

## 0.1.7 - Custom Launcher Foundation

### Added
- Added the first custom launcher startup path.
- Added custom update zip and manifest generation.
- Added updater core tests.

## 0.1.6 - About and Update Status

### Added
- Added About / Updates view with version, update state, progress, release links, and OBS URL actions.

## 0.1.5 - Shortcut Metadata

### Changed
- Simplified installer and shortcut description metadata to `LumaCue`.

## 0.1.4 - Startup Update Screen

### Added
- Added frameless startup loading screen.
- Added startup update checks before backend and shell startup.
- Added startup progress states for update, backend, and console launch.

## 0.1.3 - Silent Update Install

### Added
- Added GitHub Releases auto-update assets.
- Added desktop shortcut creation.

### Fixed
- Sanitized packaged backend resources to avoid shipping local runtime state.

## 0.1.2 - Packaged Desktop Polish

### Added
- Added installer icons, start-menu shortcut configuration, desktop Twitch setup flow, and OBS preview action.

### Fixed
- Added CORS handling for Electron `file://` shell requests.
- Fixed packaged tray icon loading.

## 0.1.1 - Public Auto-Update Baseline

### Added
- Added the first public LumaCue desktop release artifact.
- Added NSIS installer target, GitHub Releases metadata, and update status wiring.
