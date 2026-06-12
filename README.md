# LumaCue

LumaCue is a local Windows desktop app for Twitch song requests, queue control, and OBS overlays. It runs a Python backend locally, wraps the control surface in an Electron desktop shell, and keeps OBS/browser URLs stable for streaming.

## What LumaCue Does

- Accepts song requests from the desktop Quick Add panel, web player, Streamer.bot, and Twitch Channel Points.
- Resolves songs through YouTube Music / YouTube with ranking, fallbacks, and local learned rules.
- Supports Spotify track links by reading public Spotify embed metadata and resolving the matching playable track.
- Plays normal YouTube embeds and can fall back to direct audio for embed-blocked videos through yt-dlp.
- Imports and plays local audio files from the player library rail.
- Can keep the queue filled automatically with Auto DJ using related YouTube Music discovery, saved songs, and play history.
- Provides a global Blocklist for blocked artists, keywords, and video IDs across manual requests, Twitch redemptions, Local Music, saved songs, playlists, and Auto DJ.
- Provides OBS overlays for now-playing and queue display.
- Includes a desktop shell with queue drawer, command palette, Twitch setup, About / Updates, and launcher-based updates.
- Supports Twitch Device Code login by default, with an optional Cloudflare Worker OAuth broker for Authorization Code Flow without shipping a client secret in the desktop app.
- Refreshes broadcaster and bot access tokens automatically when they expire or are close to expiring.
- Stores queue, overlay settings, learned rules, and Twitch configuration locally.

## Local Music and Auto DJ

The Player's **Local** tab can import MP3, WAV, FLAC, M4A, AAC, OGG, and OPUS files. Imported files are copied into LumaCue's local data directory and queued as `local:<id>` tracks, so playback does not depend on the original file staying in the same folder.

Local tracks use the same player controls as YouTube tracks: play/pause, skip, restart, loop, volume, progress, queue sync, desktop playback state, and play history.

Auto DJ can refill the queue up to the configured target length. It prefers related YouTube Music discovery, then Saved Songs, then older play history entries when available. Recently played songs are skipped by default so Auto DJ does not immediately replay tracks that just left the player. Local Music remains manually importable and playable, but it is not used as an automatic refill source. Viewer requests are not removed or replaced.

The global Blocklist applies to Local Music too. If a local track matches a blocked artist, keyword, or video ID, LumaCue rejects the queue action and shows the matching Blocklist rule.

## Current Release

The desktop package version is managed in `desktop/package.json`.

Public built artifacts are published to:

- `xyhoxx/lumacue-releases`

The source repository is separate from the public release-artifact repository.

## Requirements

### Installed App

- Windows.
- Internet access for first install and updates.
- Twitch Affiliate or Partner status is required for Channel Points custom rewards.
- OBS Browser Source for stream overlays.

### Development

- Windows / PowerShell.
- The project-local portable Python runtime in `python_portable/`.
- Node.js and npm for the Electron desktop package.
- Python dependencies from `requirements.txt`.

## Running Locally

From the project root:

```powershell
.\run.bat
```

Useful local URLs:

- Player: `http://localhost:5000/player.html`
- OBS player overlay: `http://127.0.0.1:5000/overlay-player.html`
- Overlay settings: `http://localhost:5000/overlay-settings.html`
- Queue-only overlay: `http://localhost:5000/overlay-queue`
- Resolver debug: `http://localhost:5000/request/resolve?q=<query>`

The fixed OBS URL is:

```text
http://127.0.0.1:5000/overlay-player.html
```

Do not change this URL without updating OBS setup documentation and compatibility notes.

## Discord Rich Presence

The desktop app supports Discord Rich Presence through LumaCue's built-in Discord RPC application.

Discord displays the application name and default icon from Discord Developer Portal. If Discord still shows an old bot/app name, update the built-in Discord application in the Developer Portal before publishing.

Override it for local development with an environment variable:

```powershell
$env:LUMACUE_DISCORD_CLIENT_ID = "<your-discord-application-client-id>"
npm --prefix .\desktop run dev
```

For installed builds, an override can be placed in the desktop user-data config file:

```text
%APPDATA%\LumaCue\discord-rpc.json
```

Example:

```json
{
  "enabled": true,
  "clientId": "<your-discord-application-client-id>",
  "largeImageKey": "lumacue",
  "largeImageText": "LumaCue"
}
```

Set `LUMACUE_DISCORD_RPC=0` to force-disable the integration for a run.

The current track artwork is sent as the large Rich Presence image when Discord accepts the HTTPS artwork URL. The artwork image is not made clickable; the track title can link to YouTube when a video ID is available. `largeImageKey` is used as the small/fallback app image; the default key is `lumacue`, so upload a Rich Presence asset with key `lumacue` to replace the generic Discord application icon.
When the broadcaster is offline, the visible Discord card is kept close to a music-player layout: song title, artist, and progress. Requester context is moved to the small LumaCue icon hover text so the card stays clean.

When the connected Twitch broadcaster account is live, LumaCue switches its Discord activity type to `Streaming` with the broadcaster's Twitch URL. The visible card uses the stream title and stream thumbnail as the primary presentation, then shows the current song, artist, requester, and song progress in the playback context line when a song is active. If no song is active, it falls back to the Twitch stream title/category. When the stream goes offline, the desktop app falls back to the normal song presence.

## Desktop Development

Run the Electron shell in development mode:

```powershell
npm --prefix .\desktop run dev
```

Run the custom launcher directly:

```powershell
npm --prefix .\desktop run dev:launcher
```

Build an unpacked desktop app:

```powershell
npm --prefix .\desktop run build:dir
```

Build the installer and update packages:

```powershell
npm --prefix .\desktop run build:release
```

Publish built release artifacts:

```powershell
npm --prefix .\desktop run publish:github
```

Full release pipeline:

```powershell
npm --prefix .\desktop run release
```

## CI/CD Release Flow

GitHub Actions release automation is defined in `.github/workflows/release.yml`.

The workflow runs when:

- A version tag such as `v0.3.0` is pushed.
- The workflow is started manually from the GitHub Actions tab.

Release tags must match `desktop/package.json`. For example, package version `0.3.0` must be released with tag `v0.3.0`.

The release job runs on the self-hosted Windows runner because the build needs the local `python_portable/` runtime. The publish step uploads release assets to `xyhoxx/lumacue-releases` and updates public release notes from `CHANGELOG.md`.

Documentation-only release note sync is handled by `.github/workflows/release-notes.yml`. It runs when README, CHANGELOG, or the sync script changes, and it can be started manually from the GitHub Actions tab. This workflow updates the public release repository README, CHANGELOG, and every existing GitHub release page that has a matching section in `CHANGELOG.md`.

Run the same sync locally:

```powershell
npm --prefix .\desktop run sync:release-notes
```

## Update System

LumaCue uses a custom launcher in front of the packaged app.

Current release assets can include:

- Offline installer: `LumaCue-Setup-Offline-<version>.exe`
- Online setup stub, when built by the setup script.
- Full app package: `LumaCue-win-x64-<version>.zip`
- App-only package: `LumaCue-app-win-x64-<version>.zip`
- Runtime package: `LumaCue-runtime-win-x64-<version>.zip`
- Patch package: `LumaCue-patch-<from>-to-<version>.zip`
- Manifest: `lumacue-update.json`
- Electron updater metadata: `latest.yml`

The manifest keeps a full package fallback for older launchers. New launchers can use app-only and runtime-split packages.

## Twitch Setup

LumaCue uses a Cloudflare Worker OAuth broker by default. No client secret is stored in the desktop app.

For longer-lived Authorization Code Flow sessions, LumaCue uses the Cloudflare Worker broker in `workers/twitch-oauth-broker`. The Worker stores `TWITCH_CLIENT_SECRET` as a Cloudflare secret, exchanges Twitch authorization codes server-side, and returns only short-lived one-time tickets to the local app. The default broker origin is `https://lumacue-twitch-oauth-broker.xyhoxx.workers.dev`; set `LUMACUE_TWITCH_AUTH_BROKER_URL` only when testing another broker deployment.

Required accounts:

- Broadcaster: manages Channel Points rewards and redemption state.
- Bot: sends chat replies and listens for chat responses when viewers need to choose between ambiguous songs.

Broadcaster scopes:

- `channel:manage:redemptions`
- `channel:read:redemptions`
- `channel:bot`

Bot scopes:

- `user:read:chat`
- `user:write:chat`
- `user:bot`

Channel Points custom rewards require the broadcaster channel to have Twitch Affiliate or Partner status.

## Local Data

Local state is intentionally not committed.

Local development now defaults `TWITCH_SONGS_DATA_DIR` to `%APPDATA%\LumaCue\backend-state-dev` so runtime state and imported Local Music files do not clutter the repo root. Set `TWITCH_SONGS_DATA_DIR` yourself if you want another location.

Common state files:

- `queue_state.json`
- `saved_songs.json`
- `overlay_settings.json`
- `overlay_presets.json`
- `overlay_visual_preset_overrides.json`
- `lumacue_learning.json`
- `twitch_config.json`

Packaged desktop builds store backend state under the app user data directory rather than inside the installed program folder.

## Tests and Checks

Python tests:

```powershell
.\python_portable\python.exe -m unittest discover -s tests
```

Compile key Python files:

```powershell
.\python_portable\python.exe -m py_compile app.py state.py twitch_integration.py tui.py
```

Updater tests:

```powershell
npm --prefix .\desktop run test:updater
```

Renderer smoke QA:

```powershell
npm --prefix .\desktop run qa:renderer
```

## Internal Docs

- Resolver scoring: `docs/resolver-scoring.md`
- Twitch redemption lifecycle: `docs/redemption-lifecycle.md`

## Troubleshooting

### Twitch says Client-ID does not match

The saved Twitch login was created with a different Twitch Client ID than the built-in LumaCue Twitch app. Log out and reconnect the broadcaster and bot accounts, then sync the reward again.

### Channel Points reward cannot be created

Twitch only allows custom Channel Points rewards on Affiliate or Partner channels.

### A YouTube song skips

Some videos require sign-in, are age-restricted, or block playback paths. LumaCue handles embed-blocked videos with direct audio where possible, but sign-in-only videos cannot be played reliably.

### OBS overlay is blank

Confirm the backend is running and use:

```text
http://127.0.0.1:5000/overlay-player.html
```

If OBS is using another URL or a stale browser source cache, refresh the Browser Source.
