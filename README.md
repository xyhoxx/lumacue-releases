# LumaCue

<p align="center">
  <img src="https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/lumacue-icon.png" alt="LumaCue" width="132">
</p>

<p align="center">
  <strong>Twitch song requests, queue control, Auto DJ, and OBS music overlays for Windows streamers.</strong>
</p>

<p align="center">
  <a href="README.md"><strong>EN</strong></a>
  &nbsp;|&nbsp;
  <a href="README_TH.md">TH</a>
  &nbsp;|&nbsp;
  <a href="https://github.com/xyhoxx/lumacue-releases/releases/latest">Download for Windows</a>
  &nbsp;|&nbsp;
  <a href="CHANGELOG.md">Changelog</a>
</p>

## Download

**Recommended for most users**

1. Open the [latest release](https://github.com/xyhoxx/lumacue-releases/releases/latest).
2. Under **Assets**, download `LumaCue-Setup-Offline-<version>.exe`.
3. Run the installer, then open LumaCue from Start Menu or the desktop shortcut.

`LumaCue-Setup-Offline-<version>.exe` includes the app and everything it needs to run. You do **not** need to download ZIP, patch, runtime, `latest.yml`, or manifest files manually.

| File | Use it when... | Intended for |
| --- | --- | --- |
| `LumaCue-Setup-Offline-<version>.exe` | You are installing LumaCue normally. | Normal installation and first-time setup |
| `LumaCue-win-x64-<version>.zip` | You specifically need the full portable package. | Advanced users only |
| `LumaCue-app-*`, `LumaCue-runtime-*`, `LumaCue-patch-*`, `latest.yml`, manifest | Never for a normal manual install. | Managed automatically by the updater |

## Quick Start

1. **Install LumaCue** using the offline installer.
2. Open **Twitch** in LumaCue and connect your **Broadcaster** account. Use **Reconnect** whenever LumaCue asks for newly required Twitch permissions.
3. Create or select the Channel Points reward, then start listening.
4. In OBS, add a **Browser Source** using:

   ```text
   http://127.0.0.1:5000/overlay-player.html
   ```

## Why LumaCue?

- Let viewers request songs through Twitch Channel Points.
- Keep requests manageable with queue controls, global Blocklist, learned rules, and Auto DJ.
- Show now-playing and queue overlays in OBS with a stable local Browser Source URL.
- Add YouTube, YouTube Music, Spotify track or playlist links, and local audio files.
- Run locally on your Windows PC with a desktop control surface and Discord Rich Presence.

## Requirements

- Windows 10 or newer
- Internet connection for installation, updates, and online music resolution
- OBS Browser Source for overlays
- Twitch Affiliate or Partner status for Channel Points Custom Rewards

## Privacy and Security

- LumaCue runs its playback queue, settings, local music library, and overlay service on your PC.
- Twitch tokens are stored locally and protected with Windows DPAPI.
- The desktop app does not contain the Twitch client secret. The authorization service keeps that secret server-side.

## Troubleshooting

- **Which file should I download?** Use `LumaCue-Setup-Offline-<version>.exe`.
- **Twitch asks to reconnect?** Use the Broadcaster **Reconnect** button. It refreshes authorization without clearing your reward or listener setup.
- **Channel Points reward cannot be created?** Twitch requires Affiliate or Partner status.
- **OBS overlay is blank?** Confirm LumaCue is running and use `http://127.0.0.1:5000/overlay-player.html`.

## Source Code

LumaCue source code is currently private while the project continues to mature. The public repository hosts installers, update packages, release notes, and setup guidance only.

Open source is a possibility for the future. Any contributor and developer documentation will be published when that decision is made.
