# LumaCue

[ไทย](README.md) | [English](README_EN.md)

LumaCue is a music player for Twitch streams on Windows 10 or newer. Viewers can request songs through Channel Points while you manage the queue, let Auto DJ fill gaps, and show the current track in OBS.

**Get started:** [Download Online Setup](https://github.com/xyhoxx/lumacue-releases/releases/latest/download/LumaCue-Setup-Online.exe) (internet required), or [see every file in the latest release](https://github.com/xyhoxx/lumacue-releases/releases/latest).

## Which file do I need?

- **Regular install:** `LumaCue-Setup-Online.exe` is small and downloads the app during setup.
- **Install without internet:** `LumaCue-Setup-Offline-<version>.exe` includes everything needed and can be kept for later.
- **No installer:** Extract `LumaCue-win-x64-<version>.zip` and run the portable app.

Files named `LumaCue-app-*`, `LumaCue-runtime-*`, `LumaCue-patch-*`, `latest.yml`, and manifest files are for the updater. You do not need to download them yourself.

## Set up your stream

1. Open LumaCue and add music from search, YouTube or YouTube Music links, Spotify links, or audio files on your PC.
2. For viewer requests, open **Twitch**, connect your **Broadcaster** account, choose a Channel Points reward, and start listening. Custom Channel Points rewards require a Twitch Affiliate or Partner channel.
3. To show music in OBS, add a **Browser Source** with this URL. Keep LumaCue open while streaming:

   ```text
   http://127.0.0.1:5000/overlay-player.html
   ```

You can also use LumaCue as a music player without connecting Twitch or OBS.

## While you're live

- Reorder or remove queued songs and block tracks or artists you do not want played.
- Let Auto DJ fill an emptying queue without replacing viewer requests.
- Show the current track and queue in OBS; the Browser Source URL stays the same between songs.
- Show your music in Discord with Rich Presence.

## Data and security

Your queue, settings, imported local music, and overlay settings stay on your PC. Twitch tokens are stored locally and protected with Windows DPAPI. The Twitch client secret is held by the account connection service, not bundled with the desktop app.

If antivirus software warns about LumaCue, do not disable protection or add an exclusion right away. Check the file and where you downloaded it. The reports below cover **one v0.8.11 executable only**, not the latest release or every installer.

<details>
<summary>Scan results for LumaCue.exe v0.8.11</summary>

`LumaCue.exe` inside `LumaCue-app-win-x64-0.8.11.zip` has SHA-256:

`B49A5EE1AF577CA78836B1DB6B5022344B69E3194EF6BE0AE1719EBBE297AA13`

[VirusTotal](https://www.virustotal.com/gui/file/b49a5ee1af577ca78836b1db6b5022344b69e3194ef6be0ae1719ebbe297aa13) showed `0/69` at the time of the scan: no participating vendor flagged that exact hash in that scan.

![VirusTotal scan result for LumaCue v0.8.11](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/virustotal-v0.8.11-detection.png)

[Kaspersky OpenTIP](https://opentip.kaspersky.com/B49A5EE1AF577CA78836B1DB6B5022344B69E3194EF6BE0AE1719EBBE297AA13/results) reported `0` detections and `0` suspicious activities for the same hash in its scan.

![Kaspersky OpenTIP analysis for LumaCue v0.8.11](https://raw.githubusercontent.com/xyhoxx/lumacue-releases/master/assets/security/opentip-v0.8.11-dynamic-analysis.png)

</details>

## If something isn't working

- **Twitch asks for new permissions:** Use **Reconnect** on the Broadcaster account. You do not need to remove your reward or set it up again.
- **Can't create a Channel Points reward:** Check that your channel has Twitch Affiliate or Partner status.
- **OBS shows no track:** Keep LumaCue running and check that the Browser Source URL matches the one above.

[See what changed in each release](CHANGELOG_EN.md).

The source code is not public yet. This repository hosts installers and update files; if the source is opened later, details will be added here.
