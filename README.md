# LumaCue

Song request management for Twitch streamers — Windows desktop app with automatic updates.

---

## Download

| Installer | Size | Best for |
|-----------|------|----------|
| [**LumaCue-Setup-Online.exe**](https://github.com/xyhoxx/lumacue-releases/releases/latest/download/LumaCue-Setup-Online.exe) | ~66 KB | Most users — small download, gets the rest from the internet |
| [LumaCue-Setup-Offline-x.x.x.exe](https://github.com/xyhoxx/lumacue-releases/releases/latest) | ~700 MB | No internet at install time — everything bundled |

---

## Installing (Online Installer)

1. Download **LumaCue-Setup-Online.exe** from the link above
2. Double-click the file — a dark setup window appears immediately
3. The installer downloads and extracts the app in the background (~138 MB)
4. LumaCue launches automatically when done

No admin rights required. Installs to `%LOCALAPPDATA%\Programs\LumaCue`.  
A shortcut is added to your Desktop and Start Menu.

---

## Installing (Offline Installer)

1. Download **LumaCue-Setup-Offline-x.x.x.exe** from the [latest release](https://github.com/xyhoxx/lumacue-releases/releases/latest)
2. Double-click and follow the installer
3. LumaCue launches automatically after installation

---

## System Requirements

- Windows 10 (1903 or later) or Windows 11
- Internet connection *(Online installer and auto-update only)*
- .NET Framework 4.8 — pre-installed on Windows 10 1903+ and all Windows 11 versions

---

## Auto-Update

LumaCue checks for updates automatically every time you open it:

1. **Version check** — compares your installed version against the latest release
2. **Patch download** — downloads only the changed files (usually a few MB, not the full app)
3. **Apply and launch** — updates silently and opens the app right after

No restarts, no prompts. Just open LumaCue and it stays current.

> **Note:** The launcher itself (`%LOCALAPPDATA%\Programs\LumaCue\LumaCue.exe`) does not self-update.  
> If a launcher update is released, re-running the online installer will apply it.

---

## Uninstall

Go to **Settings → Apps** (or Control Panel → Programs and Features), find **LumaCue**, and click Uninstall.

---

*This repository contains built release artifacts only. Source code is private.*