# Changelog

## 1.8.1

- **New: loading screen.** The window now shows the Velzr logo with a spinner and "Checking tweaks and hardware …" from the very first moment and until the start page is filled with real data. Before, the first seconds looked empty and it was unclear whether anything was happening.

## 1.8.0

- **New: Fortnite ping** (Tools). Measures only, it changes nothing in the game and redirects no game traffic.
  - *Ping lab:* measures all 16 ping addresses that Epic publishes for Fortnite at the same time (minimum, average, jitter, loss), names the closest data center and says whether a subregion preference can pay off or "Auto" is the right setting. It also shows the gap between your minimum and your average, which is the part you can still win.
  - *Spike detective:* pings your router and the Epic server every second while you play and assigns each ping spike: if the router jumps at the same time, the cause is your home network (Wi-Fi, router, a device filling the line); if the router stays calm, it is on the path after it. A router that is unsteady on its own is reported as a home network problem, a router that does not answer ping is reported as not assignable.
  - *Fix and measure again:* applies the existing Ping package and compares the last two runs (spikes, jitter, loss).
  - *Provider report:* a ready text with your measurements for your internet provider, following the template in Epic's help article (ICMP versus UDP note included).
  - A relay or tunnel like a booster service is not part of it: it needs rented servers, and over the same Wi-Fi it would not help if the router is the problem.
- **Fix:** The tweak "Network adapter: power saving off" used a setting that Windows does not offer for this command, so it never took effect (and could report an error when reverting). It is removed; "Network card: forbid switching off to save power" already does the same and stays in the Ping package.
- **Fix:** The spike detective now stops its small ping helpers when you close the app, stops by itself after 3 hours, and keeps at most 3 hours of data.
- Every tweak script was checked automatically against the commands and parameters of Windows PowerShell (384 scripts), tests pass in all 8 languages.

## 1.7.0

- **New: PC check on the Home page.** It reads your PC (nothing is changed) and shows what costs FPS but cannot be fixed with a tweak: only one RAM stick (single channel), memory running below its rated speed (EXPO/XMP off), Resizable BAR / Smart Access Memory probably off (measured from the size of the graphics memory window), the graphics card connected with fewer PCIe lanes than possible, the monitor running below its possible refresh rate, Radeon Chill, Radeon Boost, the frame rate target and Anti-Lag in the graphics driver, and an active power saver plan. Every note shows the measured value and, where there is one, a source.
- **New: Background check** (Game Boost). It measures for about 4 seconds which programs use processor time right now and marks known troublemakers (RGB software such as Armoury Crate, L-Connect, Aorus / RGB Fusion and iCUE, based on reports on the Blur Busters and ROG forums, marked as user reports, not our own measurement). Nothing is closed on its own: "Close now" asks first, and "Close at game start" adds the program to the Game Boost list.
- The fixed Radeon checklist on the Home page hides the points the PC check already measures.

## 1.6.0

- **Every tweak now shows how well it is proven.** *Proven* (Microsoft documentation or a reproducible measurement), *No proof* (no proven benefit, or the value is the Windows default already) and *Can hurt* (measurements show possible costs). Open the info of a tweak to see the reason and a link to the source. The research behind it is in `docs/RESEARCH.md`.
- **Unproven tweaks are never part of "Optimize everything" and never recommended.** They sit in their own group "No proof or with downsides, for testing only" and stay available as single buttons for the Tweak test. This affects, for example, the multimedia scheduler values, Nagle's algorithm (Fortnite uses UDP), TCP fine tuning, QoS reserve, power plan values that the High performance plan sets already, and the network throttling switch, which measurements show can raise the network driver's processing time.
- **Ryzen with two chiplets and 3D V-Cache (7900X3D, 7950X3D, 9900X3D, 9950X3D):** these CPUs only start games on the fast chiplet when the Xbox Game Bar and Game Mode detect the game. The Game Bar tweaks are now shown as a trade-off on these CPUs and never applied automatically.
- New tweak: **Microsoft Store: no automatic app updates**, so the Store does not download in the background during a match.

## 1.5.1

- **New: Tweak test** (Measurement → Tweak test). Velzr measures the FPS, switches one tweak, measures again and shows what it really does on your PC. "Test all active tweaks" does this for every active tweak without a restart one after another, restores everything afterwards and lists the ones that cost FPS, with a button to undo them.
- **14 tweaks are back** that 1.4 had removed because their benefit was unproven: Fortnite fullscreen optimizations off, global fullscreen optimizations off, global timer resolution, dynamic tick off, distribute timers, QoS reserve off, TCP fine tuning, network card wake-up off, CPU minimum 100 %, core parking off, aggressive boost, maximum processor state 100 %, energy estimation off and Storage Sense off. They are available as single buttons so you can check each with the new test. The ones that change behavior for every game or turn off Wake-on-LAN stay out of "Optimize everything".
- Radeon Anti-Lag and hardware GPU scheduling are no longer part of "Optimize everything": at very high FPS, where the processor is the limit, they can cost FPS. They stay available as single buttons; check them with the tweak test.

## 1.5.0

- **Two versions, one for Windows 10 and one for Windows 11.** Download `Velzr-Tweaks-Setup-1.5.0-Windows10.exe` or `...-Windows11.exe`. The Windows 10 version is built on an older, well-proven browser engine (Electron 30) and draws its window without the graphics card by default, which avoids the empty window some Windows 10 PCs showed. Both versions have the same tweaks and features.
- If you run the version for the other Windows, the Home page shows a note with a link to the right download. The update check offers the matching installer.

## 1.4.4

- **More help for an empty window:** on Windows 10 the app now draws its window without the graphics card by default (Settings → Software rendering). If the window stays empty anyway, the app switches itself step by step: software rendering, then safe mode. If nothing helps, a dialog shows the technical details to send to the developer. **F9** in the window switches to the next step by hand; `--safe-mode` starts directly in safe mode.
- If the window process cannot start at all (a security feature of Windows or other software blocks it), the app jumps straight to safe mode instead of trying the steps one after another.
- The start log now includes processor, memory and the display mode.

## 1.4.3

- **Setup at first start:** after the terms (and once after an update) the app asks how it should look: Normal, or Lite mode for weak PCs and laptops (no animations and effects, less background work). Weak PCs are preselected. You can change it later under Settings → Lite mode.
- Fixed: clicking the text next to the terms checkbox no longer opens the terms window.

## 1.4.2

- **Fix for a dark window where nothing loads (Windows 10, animations turned off):** when Windows has "Show animations" switched off (common on weak laptops and after performance tweaks), the app's reduced-motion mode ran its looping loading animations at a speed of a thousandth of a millisecond. That kept the processor busy and the window never finished loading. Reduced motion now simply switches the animations off.

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
