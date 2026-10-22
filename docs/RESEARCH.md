# How Velzr Tweaks decides what is worth doing

Most tweak tools are a long list of registry values copied from forum posts. Many of them do nothing, some are the Windows default already, and a few make games slower. Velzr Tweaks sorts every tweak by what is actually known about it and never puts an unproven one into "Optimize everything".

## The four evidence levels

| Label | Meaning | In "Optimize everything"? |
|---|---|---|
| **Proven** | Microsoft documents the behavior, or a reproducible measurement shows the effect. | Yes, if it fits your PC |
| *(no label)* **Plausible** | The mechanism is known. The gain is small or depends on the PC. | Yes, if it fits your PC |
| **No proof** | No proven benefit, or the value is the Windows default already. | Never |
| **Can hurt** | Measurements show possible costs in FPS or latency. | Never |

Everything marked "No proof" or "Can hurt" stays available as a single button, so you can test it yourself with the built-in **Tweak test**: Velzr measures the FPS, switches the tweak, measures again and shows what it really did on your PC.

Every label has a short reason and, where there is one, a link to the source. Open the info of a tweak to see it.

## What the research found

### Proven

- **Timer resolution.** Since Windows 10 version 2004, and more strictly on Windows 11, the timer resolution a program asks for only applies to that program. Without it `Sleep(1)` sleeps about 15.6 ms, with a fine timer about 1.5 ms. Velzr holds the fine resolution while a game runs and offers the global switch. Source: [valleyofdoom/PC-Tuning, research](https://github.com/valleyofdoom/PC-Tuning/blob/main/docs/research.md) and [Bruce Dawson, "The Great Rule Change"](https://randomascii.wordpress.com/2020/10/04/windows-timer-resolution-the-great-rule-change).
- **Memory integrity (HVCI) and the hypervisor.** In published benchmarks the virtualization-based security costs a few percent FPS depending on the game. It also lowers the protection against driver attacks, so it is a trade-off and never recommended automatically. Source: [Tom's Hardware](https://www.tomshardware.com/news/windows-11-gaming-benchmarks-performance-vbs-hvci-security).
- **Mouse acceleration, sticky keys, Game DVR.** Documented behavior with a direct effect.

### Common tweaks that do nothing

- **Win32PrioritySeparation = 38 (0x26)** means short, variable time slices with a 3:1 foreground preference. That is how Windows already behaves on desktops, so setting it changes nothing provable.
- **MMCSS "Games" task values.** No game registers with the task "Games" (Fortnite registers as "Audio"), so the values never apply. "Clock Rate" has no effect and "Latency Sensitive" is the default already; wrong values can even disable the task. Source: [djdallmann/GamingPCSetup, MMCSS research](https://github.com/djdallmann/GamingPCSetup/blob/master/CONTENT/RESEARCH/WINSERVICES/README.md).
- **Nagle's algorithm off (TcpAckFrequency, TCPNoDelay).** Only touches TCP. Most shooters, Fortnite included, send UDP.
- **QoS DSCP marking** only helps if your router and provider honor it. Most home networks do not.
- **TCP fine tuning, QoS reserve, NTFS memory usage, distributed timers, dynamic tick.** Mechanism known, benefit for games not shown.
- **CPU minimum 100 %, maximum 100 %, core parking off, boost mode.** The High performance and Ultimate Performance plans already do this, and Ryzen and current Intel CPUs manage boost themselves.

### Tweaks that can make things worse

- **Network throttling off (NetworkThrottlingIndex = 0xFFFFFFFF).** Almost every tweak tool sets this. Measurements show that the network driver's processing time (DPC) rises noticeably without the throttle, so the default is better for games. Source: [djdallmann/GamingPCSetup, network research](https://github.com/djdallmann/GamingPCSetup/blob/master/CONTENT/RESEARCH/NETWORK/README.md).
- **Interrupt moderation off.** More than ten times as many interrupts; "Medium" gave the best results in the same research.
- **Radeon Anti-Lag.** The driver holds the processor back so the graphics card does not fall behind. At very high FPS, where the processor is the limit, it can cost FPS. Source: [Guru3D thread](https://forums.guru3d.com/threads/disadvantages-to-radeon-anti-lag-why-not-enabled-by-default.438984/).

### Hardware it should not break

- **Ryzen with two chiplets and 3D V-Cache (7900X3D, 7950X3D, 9900X3D, 9950X3D)** only run games on the fast chiplet if the Xbox Game Bar and Game Mode detect the game. On these CPUs, Velzr treats the Game Bar tweaks as a trade-off and never applies them automatically.
- **Windows 10 and Windows 11** are detected at start. Tweaks that need Windows 11 are locked on Windows 10, and Windows versions older than 2004 and Windows Server are read-only.

## What the PC check and the background check rely on

The biggest remaining levers are often not tweaks at all. The PC check measures them on your PC and says so when it cannot be sure.

- **Single RAM stick.** One stick connects the memory only half as wide. [Micro Center](https://www.microcenter.com/site/mc-news/article/single-vs-dual-channel-ram-for-gaming.aspx) compared 1 × 16 GB with 2 × 16 GB: the average was up to 38 % higher in some games, the lowest frame rates sometimes more than twice as high, and in other games nothing changed. Not measured for Fortnite.
- **Resizable BAR / Smart Access Memory.** Measured from the size of the memory window through which the processor reaches the graphics memory (256 MB means probably off). TechPowerUp quotes AMD's promise of up to 6 % in some games. The result is shown as "probably" and can be cross-checked with GPU-Z.
- **PCIe lanes, monitor refresh rate, frame limits in the Radeon driver (Chill, Boost, frame rate target), power saver plan.** Read directly from Windows and the driver; they are facts about your setup, not tips.
- **Background programs.** The check measures processor time over about 4 seconds. The known-troublemaker list only contains software for which user reports could be read: [Blur Busters thread on RGB software](https://forums.blurbusters.com/viewtopic.php?t=13184) (Armoury Crate, Aura, L-Connect, Aorus, iCUE) and the [ROG forum thread on iCUE](https://rog-forum.asus.com/t5/amd-600-series/icue-hwinfo64-causing-issues/td-p/900264) (an iCUE bug on AM5 boards that Corsair fixed with 4.29.203). These are user reports, not our own measurement, and the app says so.

## What the Fortnite ping page relies on

- Epic publishes the ping addresses of its data centers (`ping-<region>.ds.on.epicgames.com`, 16 listed) in the help article "Fortnite latency and ping troubleshooting". The page measures exactly these with ICMP. Fortnite itself uses UDP, so the values are an approximation, as Epic also notes.
- Epic recommends a wired connection, QoS on the router, no large uploads while playing, current router firmware and leaving the matchmaking region on Auto. A subregion preference exists (Settings > Game > Language and Region) and may lengthen queue times.
- The page does not measure the game traffic and does not change the route. A relay service needs its own servers; if the router is the problem (high router ping and jitter), a relay over the same Wi-Fi does not help.
- Distance sets a floor: light in fibre needs about 1 ms per 100 km there and back, so zero ping is impossible. The page therefore reports the gap between minimum and average as the part that can still be won.

## Method

1. Collect every tweak from the main published tuning guides and tweak tools.
2. For each one, look for (a) documentation from Microsoft or the vendor, (b) a reproducible measurement, (c) the Windows default value.
3. Sort into the four levels above and write down the reason and the source.
4. Whatever has no proof can be tested on your own PC with the Tweak test, because no list can know your hardware.

The sorting lives in [`src/catalog/evidence.js`](../src/catalog/evidence.js) in the app, one line per tweak with its note and source. If you find a better source or a measurement that contradicts one of the entries, please open an issue.

## Main sources

- [valleyofdoom/PC-Tuning](https://github.com/valleyofdoom/PC-Tuning): guide and research with measurements (timer resolution, interrupts, power, services).
- [djdallmann/GamingPCSetup](https://github.com/djdallmann/GamingPCSetup): research on MMCSS, services and the network stack.
- [Tom's Hardware](https://www.tomshardware.com/news/windows-11-gaming-benchmarks-performance-vbs-hvci-security): benchmark of VBS and HVCI in games.
- [Bruce Dawson, Random ASCII](https://randomascii.wordpress.com/2020/10/04/windows-timer-resolution-the-great-rule-change): timer resolution rule change.
- [Guru3D](https://forums.guru3d.com/threads/disadvantages-to-radeon-anti-lag-why-not-enabled-by-default.438984/): Anti-Lag downsides.
