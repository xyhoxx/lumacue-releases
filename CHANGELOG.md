# LumaCue Changelog

Product release notes for LumaCue desktop builds. Public releases contain built installer and update artifacts only.

## 0.6.8 - Twitch OAuth Completion Polish

### Changed
- Twitch OAuth completion pages now replace the callback query string with a clean local path after handling the ticket, so the browser address bar no longer exposes the OAuth ticket.
- Restyled the Twitch connected/failed browser pages with centered placement, subtle particles, a cleaner status mark, and LumaCue-themed background treatment.

## 0.6.7 - Twitch OAuth 1010 Hotfix

### Fixed
- Fixed Cloudflare `error code: 1010` during Twitch OAuth broker callback by sending a LumaCue User-Agent and JSON Accept header from the backend HTTP client instead of the default Python urllib signature.

## 0.6.6 - Twitch OAuth Broker

### Added
- Added a Cloudflare Worker Twitch OAuth broker project for Authorization Code Flow with a Worker-side client secret, short-lived one-time tickets, and Durable Object-backed login sessions.
- Added backend support for broker-based Twitch login and refresh.

### Changed
- Twitch Connect now uses a unified auth start endpoint so the desktop UI can open either broker login or Device Code login without separate UI paths.
- Twitch OAuth broker now has a built-in default origin for LumaCue builds instead of requiring every desktop runtime to set `LUMACUE_TWITCH_AUTH_BROKER_URL`.
- Twitch OAuth now targets the new LumaCue Twitch application used by the Cloudflare broker.
- Twitch config migration now clears saved accounts and stale device-code flows when the built-in Twitch Client ID changes, forcing a clean reconnect instead of failing broker callback validation.

## 0.6.5 - Auto DJ and Twitch Session Fixes

### Added
- Local Music imports now optimize non-OPUS audio to OPUS when possible, reducing stored file size while preserving stream-ready audio quality.
- Packaged desktop builds now include a bundled ffmpeg binary for Local Music optimization, with fallback to the original file when optimization is unavailable.

### Changed
- Auto DJ now uses saved songs and play history only. Local Music remains manually importable/playable, but it no longer auto-fills the queue.
- The Local tab Auto DJ control now uses a compact switch treatment, and crowded library tabs can scroll horizontally instead of squeezing text.

### Fixed
- Fixed legacy Auto DJ settings that still listed Local Music as a source causing local tracks to be queued automatically.
- Fixed Twitch broadcaster/bot expired-session status so invalid refresh tokens are reported as reconnect-required instead of looping silently.
- Reduced repeated Twitch refresh attempts after a refresh token failure by adding a short retry backoff.
- Fixed Overlay Settings sliders rendering as doubled tracks in the embedded desktop view.

## 0.6.4 - Discord Presence Clear Hotfix

### Fixed
- Discord Rich Presence now clears stale LumaCue activity when the desktop shell starts idle with no current track.
- LumaCue now waits briefly for Discord activity clear to complete before shutting down the RPC connection during app quit.
- Reduced confusion in release logs by clarifying that missing local patch bases are downloaded from the previous GitHub release when needed.

## 0.6.3 - Install Cache Cleanup

### Changed
- The launcher now runs install-cache cleanup whenever it opens an installed app, including already up-to-date, offline fallback, bootstrap, and freshly updated launches.
- Update downloads are treated as disposable cache after install, so stale package zips and update manifests are removed automatically.

### Fixed
- Prevented old version folders, staging folders, and updater download files from accumulating under the local LumaCue install root after multiple updates.
- Cleanup now preserves the active app version, shared runtime, user data, Twitch tokens, local library data, and unrelated files in the updater download folder.

## 0.6.2 - Native Discord IPC Adapter

### Changed
- Replaced the third-party Discord RPC package with LumaCue's own minimal Discord IPC adapter for Rich Presence.
- The desktop Discord integration now implements the local IPC handshake, `SET_ACTIVITY`, clear activity, request nonce tracking, reconnect handling, and broken-pipe recovery directly.

### Fixed
- Hardened Discord Rich Presence against duplicate transport errors and stale IPC socket writes so Discord restarts or closed clients do not surface as Electron main-process crashes.

## 0.6.1 - Discord RPC Crash Hotfix

### Fixed
- Fixed a main-process crash when Discord Rich Presence hit a broken Discord IPC pipe (`write EPIPE`) on machines where Discord was closed, restarting, or exposing a stale RPC socket.
- Discord RPC transport failures now disconnect and retry in the background instead of showing Electron's native JavaScript error dialog or stopping LumaCue.

## 0.6.0 - Local Music Auto DJ

### Added
- Added Local Music import for MP3, WAV, FLAC, M4A, AAC, OGG, and OPUS files. Imported files are copied into the local app data directory and queued as `local:<id>` tracks so the player never depends on the original file path.
- Added a Local tab in the player library rail with import, play, queue, refresh, and delete actions for local tracks.
- Added Auto DJ settings and queue refill support. When enabled, Auto DJ keeps the queue at a target length using Local Music first, then saved songs and play history when available.
- Added backend API routes for local library listing, file import, local audio streaming with range support, local queueing, deletion, Auto DJ settings, and manual Auto DJ refill.
- Added regression tests for Local Music import/streaming, Auto DJ refill behavior, and Twitch token refresh paths.

### Changed
- Local tracks now play through the same player controls, progress bar, volume slider, restart button, loop behavior, desktop playback-state bridge, and queue lifecycle as YouTube tracks.
- Saved Songs and queue persistence now preserve local-track metadata so a saved local song can be queued and played again.
- The packaged desktop backend now bundles the new Local Music and Auto DJ modules.

### Fixed
- Fixed Twitch broadcaster and bot sessions showing as expired when refresh tokens were still available. Status checks, stream status checks, reward sync/list/select calls, chat EventSub subscription, redemption EventSub subscription, and token validation now refresh expired or nearly expired tokens before reporting disconnected or retrying a Twitch request.

## 0.5.0 - Album Player Redesign

### Added
- Added optional Discord Rich Presence for the desktop app, showing the current track, artist/requester context, play/pause state, and playback timestamps when configured.
- Added LumaCue's built-in Discord RPC application as the default presence app, with override support through `LUMACUE_DISCORD_CLIENT_ID` or the desktop `discord-rpc.json` user-data file.
- Added a richer Discord RPC payload with Listening activity type, per-track artwork as the large image when available, a cleaner title/artist layout, `lumacue` as the small/fallback image asset key, requester context in the small-icon hover text, and clickable YouTube track title details.
- Added Twitch live-stream override for Discord RPC: when the connected broadcaster channel is live, LumaCue switches its activity type to Streaming with the Twitch channel URL, uses the stream title and thumbnail as the primary card, and shows the current song, artist, requester, and song progress in the playback context line when a song is active.

### Changed
- Reworked the desktop shell player into an album-first layout with centered square artwork, track metadata, progress, and controls.
- Added a cover-art driven blurred backdrop treatment for the player surface while keeping controls readable for stream operation.
- Simplified desktop shell player controls so playback actions sit under the artwork instead of inside a large utility console card.
- Updated player metadata copy to show artist and requester details without decorative text glyphs.
- Refined compact player sizing so the artwork, title, progress, controls, and queue panel fit without horizontal overflow.
- Changed the desktop player artwork treatment to a circular rotating-disc shape so rotation reads naturally.
- Added track-change motion for artwork, backdrop, metadata, and controls so the next song does not cut in abruptly.
- Added a product-wide broadcast media-console visual layer across the desktop shell, command row, queue drawer, native panels, and player queue surfaces.
- Started the Overlay Settings redesign with an OBS-first embedded layout, neutral media-console controls, and tighter preview/tools placement.
- Consolidated Overlay Settings CSS so the current embedded media-console layer no longer fights several older visual override passes.
- Replaced the remaining teal Overlay Settings fallback tokens with the same warm media-console palette used by the final embedded layer.
- Updated the design/product contracts to move LumaCue toward a premium media-console direction while preserving live-operator density.
- Removed the remaining outer frame from native desktop panels and tightened Twitch setup into a denser operator layout.
- Replaced remaining native Electron system notices with a themed LumaCue dialog window for tray About, backend restart, and backend startup failure messages.
- Softened sidebar navigation hover feedback so it reads as a text-and-icon state instead of a boxed card.
- Blended the desktop player surface into the surrounding shell by removing the framed player island, softening edge masks, and keeping the library rail as the only strong panel.
- Restrained the player artwork backdrop so bright covers create a small ambient halo instead of washing the whole player surface into a gray rectangle.
- Restored a visible cover-art blur wash for the desktop player while keeping it masked into the shell instead of a rectangular backdrop.
- Recolored the desktop player Library rail toward a warmer dark panel so the queue surface no longer reads as flat gray.
- Tuned the desktop player backdrop toward a muted full-surface cover blur with grey-green top light and a warm lower fade, matching the intended album-player reference more closely.
- Reduced the player backdrop blur so artwork shapes remain faintly recognizable, and overscanned the embedded player to hide hard top and bottom seams inside the shell.
- Added a lighter detail layer to the player backdrop and matched the player body background to the wash so any exposed shell edge blends instead of reading as a separate rectangle.
- Restored the embedded player frame to fill the shell stage after the overscan attempt collapsed the player into a short strip.

### Fixed
- Fixed Quick Add suggestions for Thai queries that resolve through the normal resolver fallback instead of the YT Music songs-only index.
- Added a desktop Quick Add fallback to `/request/resolve` when `/request/suggest` returns no candidates.
- Replaced remaining question-mark inspect icons with a search/inspect icon in the sidebar and queue drawer.
- Centered the sidebar inspect icon and matched its sizing more closely to the queue inspect action.
- Synced the desktop shell queue preview from backend state after Quick Add and whenever the embedded player receives queue updates.
- Kept the album backdrop synchronized with the active track artwork across initial load and lazy artwork updates.
- Restored artwork rotation as the visual toggle behavior while keeping the album-derived backdrop visible.
- Removed the outer desktop player frame so the player surface is not a card nested inside another card.
- Rebalanced the redesign color system so green is reserved for real online/ready status indicators instead of progress bars, focus states, tabs, and section labels.
- Replaced remaining question-mark matching copy with inspect-action wording.
- Fixed the embedded Overlay Settings active tab indicator so it no longer covers the current tab label.
- Fixed the remaining desktop shell paths that could show OS-native error boxes for backend failures.

## 0.4.0 - Desktop UI Foundation

### Changed
- Reworked the desktop shell into a quieter control-console layout for live stream operation.
- Rebalanced the desktop visual layer with restrained ambient texture while reducing heavy blur, glow, shadow, and glass effects.
- Tightened sidebar navigation, Quick Add, queue preview, native panels, and command palette spacing for faster scanning.
- Standardized desktop, player, and overlay-settings font stacks around Windows-native UI fonts with Thai fallback.
- Replaced several text-symbol navigation glyphs with clearer small-size icons, including a local vendored Twitch brand SVG.
- Replaced shell toolbar, queue action, and reward refresh text glyphs with theme-consistent masked icons.
- Replaced player control, library, and row-action text glyphs with the same masked-icon approach used by the desktop shell.
- Reduced repeated UI motion and replaced layout-width progress transitions with transform-based progress fills.
- Added source-aware shell motion: keyboard-opened command palette and queue drawer respond immediately, while pointer-opened surfaces keep short spatial transitions.
- Added responsive shell transitions for compact sidebar labels and queue layout changes.

### Fixed
- Fixed native desktop panels overlapping after switching views by clearing stale animation state and relying on shell transitions.
- Fixed stale view transition classes for About, Learned Rules, and Play Analytics.
- Fixed About / Updates, Learned Rules, and Play Analytics layouts that could visually collide during quick navigation.

### Documentation
- Added product and design contracts for LumaCue's desktop UI direction, including Blocks.so and TheSVG usage rules.
- Added dependency guidelines for future UI packages so new libraries must be used, packaged offline, and justified by real interaction needs.

## 0.3.5 - Backend Startup Hotfix

### Fixed
- Fixed the packaged backend exiting immediately on launch ("LumaCue backend stopped"). The Play Analytics module (`history.py`, added in 0.3.2) was never bundled with the installer, so the backend crashed on startup with a missing-module error. It is now included in the build.

### Notes
- Affected installed builds 0.3.2 through 0.3.4. Running from source was unaffected.

## 0.3.4 - Resolver Cleanup Follow-up

### Changed
- Completed a small song-resolver cleanup pass after the 0.3.3 audit.
- No user-facing playback, queue, Twitch, or update behavior changed in this release.

## 0.3.3 - Resolver and Redemption Audit

### Fixed
- Kept Twitch Channel Points artist-choice requests on the same auto-refund lifecycle as normal requests. When auto-refund is enabled, a selected song is fulfilled only after it actually starts playing.
- Fixed resolver score diagnostics so the displayed component breakdown uses the same scoring source as the selected song score, including the version-artist mismatch penalty.

### Changed
- Consolidated resolver scoring into a single component source used by ranking and debug output.
- Removed unused legacy resolver/artwork helper code that had no callers.

### Documentation
- Added internal documentation for resolver scoring rules and Twitch redemption lifecycle behavior.

## 0.3.2 - Play Analytics

### Added
- New **Play Analytics** panel in the sidebar: total plays, unique songs, and unique requesters at a glance, plus ranked top songs, top artists, and top requesters with bar charts, and a recent-plays list.
- Every song that actually plays is logged to local play history (`play_history.jsonl`); a song that's skipped or fails before playing is not counted.
- **Export CSV** of the full play history, and **Clear history** to reset it.

### Notes
- History is stored locally only; nothing is uploaded.

## 0.3.1 - Auto-Refund Channel Points

### Added
- Channel-point redemptions are now refunded automatically when a song never plays because it was skipped, removed, cleared from the queue, or unplayable (e.g. age-restricted).
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
