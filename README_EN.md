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
  <a href="CHANGELOG_EN.md">Changelog</a>
</p>

## Download

**Recommended for most users: Online Setup**

1. Open the [latest release](https://github.com/xyhoxx/lumacue-releases/releases/latest).
2. Under **Assets**, download `LumaCue-Setup-Online.exe`.
3. Run the installer, then open LumaCue from Start Menu or the desktop shortcut.

`LumaCue-Setup-Online.exe` is the smallest and quickest installer. It downloads the current app during setup, so an internet connection is required.

Use `LumaCue-Setup-Offline-<version>.exe` when you want to save the full installer for a PC that will be offline during installation.

| File | Use it when... | Intended for |
| --- | --- | --- |
| `LumaCue-Setup-Online.exe` | You have internet access and want the fastest, smallest installer. | Recommended for most users |
| `LumaCue-Setup-Offline-<version>.exe` | The PC will be offline during installation, or you want to keep a full installer. | Offline or reusable installation |
| `LumaCue-win-x64-<version>.zip` | You specifically need the full portable package. | Advanced users only |
| `LumaCue-app-*`, `LumaCue-runtime-*`, `LumaCue-patch-*`, `latest.yml`, manifest | Never for a normal manual install. | Managed automatically by the updater |

## Quick Start

1. **Install LumaCue** using the online installer, or the offline installer when needed.
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
- Internet connection for Online Setup, updates, and online music resolution
- OBS Browser Source for overlays
- Twitch Affiliate or Partner status for Channel Points Custom Rewards

## Privacy and Security

- LumaCue runs its playback queue, settings, local music library, and overlay service on your PC.
- Twitch tokens are stored locally and protected with Windows DPAPI.
- The desktop app does not contain the Twitch client secret. The authorization service keeps that secret server-side.

### Security Verification

LumaCue `v0.8.0` is classified as **Clean** by [Kaspersky OpenTIP](https://opentip.kaspersky.com/2A17E9EA05FD27CE2D2D7B9AE1905DEB0F2C47CEDE89A170CE7C90CE5BF9A23A/results?tab) for the following `LumaCue.exe` SHA-256:

`2A17E9EA05FD27CE2D2D7B9AE1905DEB0F2C47CEDE89A170CE7C90CE5BF9A23A`

The dynamic analysis reports `0` detections and `0` suspicious activities. Its single network activity is categorized as `Good`, not as a threat detection.

![Kaspersky OpenTIP dynamic analysis for LumaCue v0.8.0](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/opentip-v0.8.0-dynamic-analysis.png)

VirusTotal scanned the same file hash with 69 security vendors, and **none flagged it as malicious (`0/69`)** at the time of the scan ([view the scan result](https://www.virustotal.com/gui/file/2a17e9ea05fd27ce2d2d7b9ae1905deb0f2c47cede89a170ce7c90ce5bf9a23a/detection)).

![VirusTotal detection result for LumaCue v0.8.0](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/virustotal-v0.8.0-detection.png)

This result applies only to the file and hash above. Always download installers from the official release page.

## Troubleshooting

- **Which file should I download?** Use `LumaCue-Setup-Online.exe` when you have internet access. Use `LumaCue-Setup-Offline-<version>.exe` for an offline installation.
- **Twitch asks to reconnect?** Use the Broadcaster **Reconnect** button. It refreshes authorization without clearing your reward or listener setup.
- **Channel Points reward cannot be created?** Twitch requires Affiliate or Partner status.
- **OBS overlay is blank?** Confirm LumaCue is running and use `http://127.0.0.1:5000/overlay-player.html`.

## Source Code

LumaCue source code is currently private while the project continues to mature. The public repository hosts installers, update packages, release notes, and setup guidance only.

Open source is a possibility for the future. Any contributor and developer documentation will be published when that decision is made.
