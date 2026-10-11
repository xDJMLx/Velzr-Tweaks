# Changelog

## 1.4.1

- **Fix for an empty window:** on some PCs (reported on a Windows 10 PC) the window stayed dark and nothing loaded, most likely because of the graphics driver. The app now checks shortly after start whether it shows anything and, if not, restarts itself once with software rendering. It can also be set under Settings → Software rendering or started with `--software-render`.
- Start errors are shown on screen with restart buttons instead of a blank window, and everything that goes wrong at start is written to the log (`%APPDATA%\Velzr Tweaks\data\app.log`).

## 1.4.0

- **New interface:** icon rail on the left, every tweak is a button that lights up in your accent color. One "Optimize everything" button on Home applies all useful tweaks for your PC. Calmer neutral colors, no blur or mouse-light effects, lighter animations.
- **Fewer, better tweaks:** 39 tweaks with no measurable effect on speed, latency or background load were removed (pure cosmetics, privacy-only switches, placebo tweaks). Tweaks for specific problems or hardware now sit in their own group.
- Categories are now Windows, Input & latency, Network, Power, Graphics, Debloat and Fortnite.
- **Windows check at start:** the app shows whether you run Windows 10 or 11 and how many tweaks fit. Supported: Windows 10 from version 2004 (build 19041) and Windows 11. Older versions, Windows Server and unknown versions are read-only: nothing is applied.
- "Optimize everything" no longer touches tweaks that change visible behavior (Windows search, Remote Desktop, DNS, visual effects) and, on laptops, tweaks that shorten battery life. They stay available as single buttons.
- Flat buttons without 3D effect, softer glow, smoother and more uniform animations.
- The free trial and license system were removed: Velzr Tweaks is free, download it from GitHub.

## 1.3.1

- **More languages:** French, Portuguese (Brazil), Russian, Polish and Turkish join English, German and Spanish. The app picks the language of your Windows installation automatically.
- The installer now also shows the license page in these languages.
- Cyrillic text is shown in the app font (Inter) instead of a fallback font.
- Plural forms follow each language's rules (for example Russian and Polish have three forms).

## 1.3.0

- **International:** the app now starts in the language of your Windows installation. Available: English, German and Spanish. If your language is not available yet, English is used. Switch the language any time under Settings → Appearance.
- Everything is translated: all tweak names and descriptions, recommendations, ping findings, measurements, dialogs, legal texts and the installer (the installer shows the license page in the Windows language).
- Numbers, dates and units follow the chosen language.
- The ping analysis is re-worded when you open an older result, so old results also appear in the current language.
- Fixed: the update check was scheduled from the wrong place and did not run reliably.
- The GitHub page and release notes are now in English (German README: `README.de.md`).

## 1.2.0

- **Free:** no trial period and no license keys any more. All features are free permanently.
- **Updates via GitHub:** the app asks once a day whether a new version exists and shows it at the top with the release notes (can be turned off under Settings).
- **Detects Windows updates:** if applied tweaks were reset by a Windows update, the app offers "Apply again".
- **Windows 10 and Windows 11:** the app adapts the tweak selection to the Windows version. Under Settings → Compatibility you can see which tweaks fit this PC and why the rest is hidden.
- Fixed: the Windows version restriction used to apply only to tweaks with further requirements, now it applies to all.

## 1.1.0

**New design**
- Completely redesigned interface: flat and calm, without blur and glow effects. This means much less GPU and CPU load, even on weak laptops.
- New start page with a score card, new navigation bar with icons, uniform cards, lists and dialogs.
- Lite mode for weak PCs (automatic with little RAM, few cores or a laptop without a dedicated graphics card).

**New**
- Ping analysis: breaks the ping down into Wi-Fi, internet path and behavior under load, with findings and a before/after comparison.
- Ping package and timer holder (0.5 ms, starts with Windows, no window).
- Recommendations apply to all games, not just Fortnite. Game Boost recognizes your own games.
- Recommendations adapt to Intel/AMD, hard drive/SSD, laptop/desktop and weak PCs.
- RAM tips with real values (dual channel, EXPO/XMP) on the start page.
- Welcome dialog with terms of use, privacy notice and licenses (Settings → About Velzr Tweaks).
- Diagnostics export and error log for support.
- Windows 10 mode: tweaks sorted by Windows version, new Windows 10 tweaks (News and interests, Cortana), search highlights tweak, mode selectable under Settings.
- Compatibility overview in Settings: shows which tweaks fit this PC and why others are hidden.
- "Optimizations for windowed mode" only from Windows 11 22H2 (according to Microsoft), "Distribute timers across all cores" from Windows 10 2004.
- Detection of Windows updates: if applied tweaks are reset afterwards, the app offers "Apply again".

**Improved**
- Faster state checks (only changed tweaks after applying), less background load, PowerShell processes with low priority.

## 1.0.0

- First version: catalog with backup and undo, Fortnite editor, FPS measurement, Game Boost, cleanup, startup manager.
