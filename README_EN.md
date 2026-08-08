# LumaCue

<p align="center">
  <img src="https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/lumacue-icon.png" alt="LumaCue" width="132">
</p>

<p align="center">
  <strong>Twitch song requests, queue control, Auto DJ, and OBS music overlays for Windows streamers.</strong>
</p>

<p align="center">
  <a href="README.md">TH</a>
  &nbsp;|&nbsp;
  <a href="README_EN.md"><strong>EN</strong></a>
  &nbsp;|&nbsp;
  <a href="https://github.com/xyhoxx/lumacue-releases/releases/latest">Download for Windows</a>
  &nbsp;|&nbsp;
  <a href="CHANGELOG_EN.md">Release updates</a>
</p>

## Download

**Have an internet connection? Use Online Setup.**

1. Open the [latest release](https://github.com/xyhoxx/lumacue-releases/releases/latest).
2. Under **Assets**, download `LumaCue-Setup-Online.exe`.
3. Run the installer, then open LumaCue from Start Menu or the desktop shortcut.

`LumaCue-Setup-Online.exe` is the smallest and quickest option. It downloads the latest LumaCue build while installing, so it needs an internet connection.

Use `LumaCue-Setup-Offline-<version>.exe` when you want to save the full installer for a PC that will be offline during installation.

| File | Use it when... | Intended for |
| --- | --- | --- |
| `LumaCue-Setup-Online.exe` | You have internet access and want a quick install. | Recommended option |
| `LumaCue-Setup-Offline-<version>.exe` | The PC will be offline during installation, or you want to keep a full installer. | Offline or reusable installation |
| `LumaCue-win-x64-<version>.zip` | You want to use LumaCue as a portable app without installing it. | People who do not want to install |
| `LumaCue-app-*`, `LumaCue-runtime-*`, `LumaCue-patch-*`, `latest.yml`, manifest | Never for a normal manual install. | Managed automatically by the updater |

## Quick Start

1. **Install LumaCue** using the online installer, or the offline installer when needed.
2. Open **Twitch** in LumaCue and connect your **Broadcaster** account. Use **Reconnect** whenever LumaCue asks for newly required Twitch permissions.
3. Create or select the Channel Points reward, then start listening.
4. In OBS, add a **Browser Source** using:

   ```text
   http://127.0.0.1:5000/overlay-player.html
   ```

## What LumaCue Does

- Let viewers request songs through Twitch Channel Points.
- Reorder, remove, and manage requests with the global Blocklist, learned rules, and Auto DJ.
- Show the current track and queue in OBS through one stable Browser Source URL.
- Add YouTube, YouTube Music, Spotify track or playlist links, and local audio files.
- Run locally on your Windows PC with a desktop control surface and Discord Rich Presence.

## Requirements

- Windows 10 or newer
- Internet connection for Online Setup, updates, and online music resolution
- OBS Browser Source for overlays
- Twitch Affiliate or Partner status for Channel Points Custom Rewards

## Privacy and Security

- LumaCue runs its playback queue, settings, local music library, and overlay service on your PC.
- Twitch tokens are stored locally and protected with Windows DPAPI.
- The desktop app does not contain the Twitch client secret. The authorization service keeps that secret server-side.

### Security Verification

The checked file is `LumaCue.exe` inside `LumaCue-app-win-x64-0.8.6.zip`. Its SHA-256 is:

`78F1EF8EB881B09A91F46E4181A619F8D8504F479CAD412A8942757B86FFAA36`

[VirusTotal](https://www.virustotal.com/gui/file/78f1ef8eb881b09a91f46e4181a619f8d8504f479cad412a8942757b86ffaa36/detection) reported `0/68`: no security vendor flagged the file as malicious at the time of the scan.

![VirusTotal scan result for LumaCue v0.8.6](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/virustotal-v0.8.6-detection.png)

[Kaspersky OpenTIP](https://opentip.kaspersky.com/78F1EF8EB881B09A91F46E4181A619F8D8504F479CAD412A8942757B86FFAA36/results) reported `0` detections and `0` suspicious activities. Its single network activity was rated Good. Two extracted files were not categorized, which is not a malware detection.

![Kaspersky OpenTIP analysis for LumaCue v0.8.6](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/opentip-v0.8.6-dynamic-analysis.png)

These results cover only the file and hash above, not the installer or every release asset. Download LumaCue only from this repository's release page.

## Troubleshooting

- **Which file should I download?** Use `LumaCue-Setup-Online.exe` when you have internet access. Use `LumaCue-Setup-Offline-<version>.exe` for an offline installation.
- **Twitch asks to reconnect?** Use the Broadcaster **Reconnect** button. It refreshes authorization without clearing your reward or listener setup.
- **Channel Points reward cannot be created?** Twitch requires Affiliate or Partner status.
- **OBS overlay is blank?** Confirm LumaCue is running and use `http://127.0.0.1:5000/overlay-player.html`.

## Source Code

LumaCue source code is currently private. This public repository contains installers, update packages, release notes, and setup help for users.

LumaCue may become open source in the future. Developer documentation will be added if and when that happens.
