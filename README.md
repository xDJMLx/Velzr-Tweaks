<p align="center">
  <img src="docs/banner.svg" alt="Velzr Tweaks: More FPS. Less ping. Fully reversible." width="100%">
</p>

<p align="center">
  <a href="https://github.com/xDJMLx/Velzr-Tweaks/releases/latest"><img alt="Latest version" src="https://img.shields.io/github/v/release/xDJMLx/Velzr-Tweaks?style=for-the-badge&color=2f6fe8&label=Version"></a>
  <img alt="Windows 10 and 11" src="https://img.shields.io/badge/Windows-10%20%7C%2011-2f6fe8?style=for-the-badge">
  <img alt="Free" src="https://img.shields.io/badge/Price-free-2f6fe8?style=for-the-badge">
</p>

<h3 align="center">Get more out of your PC. No risk, no sales pitch.</h3>

<p align="center">
  <a href="https://github.com/xDJMLx/Velzr-Tweaks/releases/latest"><b>⬇ Download</b></a>
  &nbsp;·&nbsp;
  <a href="#getting-started">Getting started</a>
  &nbsp;·&nbsp;
  <a href="#faq">FAQ</a>
  &nbsp;·&nbsp;
  <a href="README.de.md">Deutsch</a>
</p>

---

**Velzr Tweaks** tunes Windows for gaming: less background load, steadier frame times, a more stable ping and less input lag. The app detects your PC (processor, graphics card, memory, Wi-Fi, laptop or desktop, Windows 10 or 11) and only suggests what actually helps on your machine. Everything is backed up first and can be undone with one click.

The app speaks your language: it starts in the language of your Windows installation (currently English, German, Spanish, French, Portuguese, Russian, Polish and Turkish) and falls back to English otherwise. You can switch the language any time under Settings.

## Why Velzr Tweaks?

| | |
|---|---|
| **Everything is reversible** | Before every change the app stores the original values. "Revert all" restores them, even weeks later. |
| **Fits your PC** | No one-size-fits-all list. A weak laptop gets different recommendations than a high-end desktop. |
| **For all games** | Not built for a single game. The recommendations work in every game. |
| **See what it brings** | Built-in FPS measurement with a before/after comparison, plus a ping analysis. No promises, just numbers from your PC. |
| **Transparent** | Every tweak can be expanded and shows exactly which setting is changed. |
| **Private** | No account, no telemetry. No data about you is sent anywhere. |

## Results

| PC | Result |
|---|---|
| Ryzen 7 9700X · RX 6700 XT, Fortnite (performance mode) | from about 350 to about 600 FPS on average |
| Very weak PC with Windows 10 | about +86 % average FPS |

> **Important:** These are reports from testers, not lab measurements. How much you gain depends on your PC, your drivers and the game. **The weaker the PC and the more background load, the bigger the gain.** Strong PCs gain less. Check it yourself with the built-in measurement: take a "Before", apply the tweaks, take an "After".

## Screenshots

<table>
  <tr>
    <td width="50%"><img src="docs/screenshots/recommended.png" alt="Home"><br><sub><b>Home:</b> one button optimizes everything that fits your PC</sub></td>
    <td width="50%"><img src="docs/screenshots/categories.png" alt="Windows tweaks"><br><sub><b>Tweaks:</b> every tweak is a button that lights up when it is on</sub></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/tweak-list.png" alt="Network tweaks"><br><sub><b>Grouped</b> by how well they fit your PC</sub></td>
    <td><img src="docs/screenshots/game-boost.png" alt="Game Boost"><br><sub><b>Game Boost:</b> automatic optimization when a game starts</sub></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/measurement.png" alt="FPS measurement"><br><sub><b>Measurement:</b> FPS, ping and system load before and after</sub></td>
    <td><img src="docs/screenshots/settings.png" alt="Settings"><br><sub><b>Settings:</b> language, Windows mode, lite mode, compatibility</sub></td>
  </tr>
</table>

## What's inside

- **Home:** one button, "Optimize everything", applies every useful tweak for your PC. "Safe setup" is the guided version, undo is one key.
- **Over 100 tweaks** in 7 categories: Windows, input and latency, network, power, graphics, debloat, Fortnite. Each tweak is a button that lights up in your accent color when it is on. Grouped by whether they fit your system; tweaks without a measurable effect on speed, latency or background load are not included.
- **FPS measurement** in any game (like PresentMon), with average, 1 % low and 0.1 % low.
- **Ping analysis:** breaks your ping down into Wi-Fi, internet path and behavior under load (bufferbloat), with findings and a before/after comparison.
- **Game Boost:** raises the priority of your game, holds the fine timer resolution and, if you like, closes background programs while the game runs.
- **Hardware tips:** the app also shows what software cannot fix, for example single-channel RAM or a disabled EXPO profile.
- **Windows updates:** if an update resets settings, the app offers "Apply again".
- **Windows 10 and 11:** the app detects your Windows version at start and only offers tweaks that fit it. Supported: Windows 10 version 2004 (build 19041) and newer, and Windows 11. On older versions or Windows Server the app only shows information and changes nothing.
- **For weak PCs:** lite mode, low background load, fitting recommendations.
- **Your language:** follows the Windows language automatically, switchable in Settings.
- Plus cleanup, startup manager, mouse tools and profiles you can export.

## Getting started

1. **[Download the Velzr Tweaks setup](https://github.com/xDJMLx/Velzr-Tweaks/releases/latest)**. There is one file per Windows: **`Velzr-Tweaks-Setup-<version>-Windows10.exe`** for Windows 10 and **`Velzr-Tweaks-Setup-<version>-Windows11.exe`** for Windows 11. Not sure which one you have? Press Windows key + R, type `winver`.
2. Run it. Windows shows a warning because the installer is not digitally signed: **"More info" → "Run anyway"**. Confirm the administrator prompt; it is needed because the app changes system settings.
3. On **Home** click **"Optimize everything"** (or **"Safe setup"** for the guided version). The app creates a restore point and applies the selection.
4. Restart, play, and check the result with **Measurement**.

Not happy? **"Revert all"** (key **R**) or simply uninstall.

## FAQ

<details>
<summary><b>Is it safe?</b></summary>

The app only uses documented Windows settings. The original values are stored before every change, and before the first apply it can create a Windows restore point. Tweaks with side effects are marked "Expert" or "Trade-off" and are not part of the normal recommendation.
</details>

<details>
<summary><b>Can I get banned for it (anti-cheat)?</b></summary>

The app does not change game files and does not interfere with games, anti-cheat systems or in-game network traffic. It changes Windows settings that anyone can also set by hand. There are deliberately no features that influence hit registration or game mechanics.
</details>

<details>
<summary><b>Why does the app need administrator rights?</b></summary>

Because Windows settings such as services, power plans and the registry can only be changed with administrator rights. Without them the app can only show information.
</details>

<details>
<summary><b>Why does Windows warn me during installation?</b></summary>

The installer is not digitally signed (a certificate costs money), so Windows warns about any unknown software. Only download it from this page. The checksum (SHA-256) is listed with every release.
</details>

<details>
<summary><b>Does it run on Windows 10?</b></summary>

Yes, from Windows 10 version 2004 (build 19041) on. The app detects the Windows version at start and only shows tweaks that fit it. Older Windows versions and Windows Server are not supported: there the app changes nothing. Under Settings → Compatibility you can see which tweaks fit your PC and why the rest is hidden.
</details>

<details>
<summary><b>How many FPS does it bring?</b></summary>

There is no general answer. On weak PCs with a lot of background load big jumps are possible, on strong PCs rather small ones. Often hardware helps more, for example a second memory stick. The app measures it for you so you do not have to take anything on faith.
</details>

<details>
<summary><b>What does it cost? What happens to my data?</b></summary>

It is free. There is no account and no telemetry. The app asks GitHub once a day whether a new version exists (can be turned off), and the ping measurements talk to Cloudflare and Amazon data centers. Nothing else.
</details>

<details>
<summary><b>How do I get updates?</b></summary>

The app shows "Update <version>" at the top as soon as a new version appears here under Releases. You download it and run it. Settings and backups are kept.
</details>

<details>
<summary><b>Which languages are supported?</b></summary>

English, German, Spanish, French, Portuguese (Brazil), Russian, Polish and Turkish. The app picks the language of your Windows installation automatically and uses English if yours is not available yet (more languages can be added, see Issues). You can change the language under Settings.
</details>

<details>
<summary><b>The window stays empty or black. What can I do?</b></summary>

This can happen on some PCs, most likely because of the graphics driver. On Windows 10 the app therefore draws its window without the graphics card by default (Settings → Software rendering). If the window is still empty, the app notices it after a few seconds and restarts itself, first with software rendering and then in safe mode. You can also press **F9** in the window to switch to the next mode, or start it manually with `--software-render` or `--safe-mode` (right-click the shortcut → Properties → add it after the path in "Target"). Problems are written to `%APPDATA%\Velzr Tweaks\data\app.log`; please attach that file when you report an issue.
</details>

## Help and feedback

Something does not work or a tweak causes problems? Open a ticket under **Issues** and attach the file from **Settings → Export diagnostics**. It contains the program version, system data and the error log, but no personal data.

## Notice

Velzr Tweaks is not affiliated with Microsoft, Epic Games, AMD, NVIDIA, Intel or any other company mentioned. All trademarks belong to their owners. Use is at your own risk; the full terms are in the app under Settings → About Velzr Tweaks.

---

<p align="center"><sub><a href="CHANGELOG.md">Changelog</a> · <a href="README.de.md">Deutsch</a></sub></p>
