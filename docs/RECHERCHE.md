# Woher Velzr Tweaks weiß, was sich lohnt

Die meisten Tweak-Programme sind eine lange Liste von Registry-Werten aus Forenbeiträgen. Viele davon bewirken nichts, manche sind schon der Windows-Standard und ein paar machen Spiele langsamer. Velzr Tweaks ordnet jeden Tweak danach ein, was darüber tatsächlich bekannt ist, und nimmt nie etwas Unbelegtes in „Alles optimieren“ auf.

## Die vier Beweisstufen

| Marke | Bedeutung | In „Alles optimieren“? |
|---|---|---|
| **Belegt** | Microsoft dokumentiert das Verhalten oder eine reproduzierbare Messung zeigt die Wirkung. | Ja, wenn er zu deinem PC passt |
| *(ohne Marke)* **Plausibel** | Der Wirkmechanismus ist bekannt. Der Gewinn ist klein oder hängt vom PC ab. | Ja, wenn er zu deinem PC passt |
| **Ohne Nachweis** | Kein belegter Nutzen, oder der Wert ist schon der Windows-Standard. | Nie |
| **Kann schaden** | Messungen zeigen mögliche Nachteile bei FPS oder Latenz. | Nie |

Alles mit „Ohne Nachweis“ oder „Kann schaden“ bleibt als einzelner Knopf verfügbar, damit du es mit dem eingebauten **Tweak-Test** selbst prüfen kannst: Velzr misst die FPS, schaltet den Tweak um, misst erneut und zeigt, was er auf deinem PC wirklich getan hat.

Jede Marke hat eine kurze Begründung und, wo es eine gibt, einen Link zur Quelle. Öffne dafür die Info eines Tweaks.

## Was die Recherche ergeben hat

### Belegt

- **Timer-Auflösung.** Seit Windows 10 Version 2004, strenger unter Windows 11, gilt die Timer-Auflösung, die ein Programm anfordert, nur für dieses Programm. Ohne sie schläft `Sleep(1)` etwa 15,6 ms, mit feinem Timer etwa 1,5 ms. Velzr hält die feine Auflösung, solange ein Spiel läuft, und bietet den globalen Schalter an. Quelle: [valleyofdoom/PC-Tuning, Research](https://github.com/valleyofdoom/PC-Tuning/blob/main/docs/research.md) und [Bruce Dawson, „The Great Rule Change“](https://randomascii.wordpress.com/2020/10/04/windows-timer-resolution-the-great-rule-change).
- **Speicher-Integrität (HVCI) und Hypervisor.** In veröffentlichten Benchmarks kostet die Virtualisierungs-Sicherheit je nach Spiel einige Prozent FPS. Sie senkt zugleich den Schutz vor Treiber-Angriffen, deshalb ist das eine Abwägung und wird nie automatisch empfohlen. Quelle: [Tom’s Hardware](https://www.tomshardware.com/news/windows-11-gaming-benchmarks-performance-vbs-hvci-security).
- **Mausbeschleunigung, Einrasttasten, Game DVR.** Dokumentiertes Verhalten mit direkter Wirkung.

### Beliebte Tweaks, die nichts bewirken

- **Win32PrioritySeparation = 38 (0x26)** bedeutet kurze, variable Zeitscheiben mit Vordergrund-Bevorzugung 3:1. So verhält sich Windows auf Desktops ohnehin, der Wert ändert nichts Belegbares.
- **MMCSS-Werte der Aufgabe „Games“.** Kein Spiel meldet sich bei der Aufgabe „Games“ an (Fortnite nutzt „Audio“), die Werte greifen also nie. „Clock Rate“ hat keine Wirkung, „Latency Sensitive“ ist schon Standard, falsche Werte können die Aufgabe sogar lahmlegen. Quelle: [djdallmann/GamingPCSetup, MMCSS-Recherche](https://github.com/djdallmann/GamingPCSetup/blob/master/CONTENT/RESEARCH/WINSERVICES/README.md).
- **Nagle-Algorithmus aus (TcpAckFrequency, TCPNoDelay).** Betrifft nur TCP. Die meisten Shooter, auch Fortnite, senden UDP.
- **QoS-DSCP-Markierung** hilft nur, wenn Router und Provider sie beachten. Die meisten Heimnetze tun das nicht.
- **TCP-Feintuning, QoS-Reserve, NTFS-Speichernutzung, verteilte Timer, Dynamic Tick.** Wirkmechanismus bekannt, Nutzen für Spiele nicht gezeigt.
- **CPU-Minimum 100 %, Maximum 100 %, Core Parking aus, Boost-Modus.** Der Hochleistungs- und der Ultimative Energieplan tun das bereits, und Ryzen und aktuelle Intel-CPUs steuern den Boost selbst.

### Tweaks, die schaden können

- **Netzwerkdrosselung aus (NetworkThrottlingIndex = 0xFFFFFFFF).** Fast jedes Tweak-Programm setzt das. Messungen zeigen, dass die Verarbeitungszeit des Netzwerktreibers (DPC) ohne die Drosselung deutlich steigt, der Standardwert ist für Spiele besser. Quelle: [djdallmann/GamingPCSetup, Netzwerk-Recherche](https://github.com/djdallmann/GamingPCSetup/blob/master/CONTENT/RESEARCH/NETWORK/README.md).
- **Interrupt-Moderation aus.** Mehr als zehnmal so viele Unterbrechungen. „Mittel“ gab in derselben Recherche die besten Ergebnisse.
- **Radeon Anti-Lag.** Der Treiber bremst den Prozessor, damit die Grafikkarte nicht zurückfällt. Bei sehr hohen FPS, wo der Prozessor begrenzt, kann das FPS kosten. Quelle: [Guru3D-Thread](https://forums.guru3d.com/threads/disadvantages-to-radeon-anti-lag-why-not-enabled-by-default.438984/).

### Hardware, die nichts abbekommen soll

- **Ryzen mit zwei Chiplets und 3D V-Cache (7900X3D, 7950X3D, 9900X3D, 9950X3D)** starten Spiele nur dann auf dem schnellen Chiplet, wenn Xbox Game Bar und Spielmodus das Spiel erkennen. Auf diesen CPUs behandelt Velzr die Game-Bar-Tweaks als Abwägung und wendet sie nie automatisch an.
- **Windows 10 und Windows 11** werden beim Start erkannt. Tweaks, die Windows 11 brauchen, sind unter Windows 10 gesperrt. Windows-Versionen vor 2004 und Windows Server sind schreibgeschützt.

## Worauf PC-Check und Hintergrund-Check beruhen

Die größten verbleibenden Hebel sind oft gar keine Tweaks. Der PC-Check misst sie auf deinem PC und sagt es, wenn er sich nicht sicher ist.

- **Nur ein RAM-Riegel.** Ein Riegel bindet den Speicher nur halb so breit an. [Micro Center](https://www.microcenter.com/site/mc-news/article/single-vs-dual-channel-ram-for-gaming.aspx) verglich 1 × 16 GB mit 2 × 16 GB: Der Durchschnitt war in einzelnen Spielen bis zu 38 % höher, die niedrigsten Bildraten teils mehr als doppelt so hoch, in anderen Spielen änderte sich nichts. Für Fortnite nicht gemessen.
- **Resizable BAR / Smart Access Memory.** Gemessen an der Größe des Speicherfensters, über das der Prozessor den Grafikspeicher erreicht (256 MB bedeutet wahrscheinlich aus). TechPowerUp nennt das AMD-Versprechen von bis zu 6 % in einzelnen Spielen. Das Ergebnis steht als „wahrscheinlich“ da und lässt sich mit GPU-Z gegenprüfen.
- **PCIe-Lanes, Bildwiederholrate des Monitors, Bildraten-Limits im Radeon-Treiber (Chill, Boost, Bildraten-Ziel), Energiesparplan.** Direkt aus Windows und dem Treiber gelesen; das sind Tatsachen über dein System, keine Tipps.
- **Hintergrundprogramme.** Der Check misst die Prozessorzeit über etwa 4 Sekunden. Die Liste bekannter Störer enthält nur Software, zu der Nutzerberichte gelesen werden konnten: der [Blur-Busters-Thread zu RGB-Software](https://forums.blurbusters.com/viewtopic.php?t=13184) (Armoury Crate, Aura, L-Connect, Aorus, iCUE) und der [ROG-Forum-Thread zu iCUE](https://rog-forum.asus.com/t5/amd-600-series/icue-hwinfo64-causing-issues/td-p/900264) (ein iCUE-Fehler auf AM5-Boards, den Corsair mit 4.29.203 behoben hat). Das sind Nutzerberichte, keine eigene Messung, und die App sagt das auch.

## Worauf die Seite Fortnite-Ping beruht

- Epic veröffentlicht die Ping-Adressen seiner Rechenzentren (`ping-<region>.ds.on.epicgames.com`, 16 aufgeführt) im Hilfeartikel „Fortnite latency and ping troubleshooting“. Die Seite misst genau diese per ICMP. Fortnite selbst nutzt UDP, die Werte sind also eine Näherung, was auch Epic anmerkt.
- Epic empfiehlt Kabel, QoS im Router, keine großen Uploads beim Spielen, aktuelle Router-Firmware und die Matchmaking-Region auf Auto. Eine Subregion-Präferenz gibt es (Einstellungen > Spiel > Sprache und Region), sie kann die Wartezeit verlängern.
- Die Seite misst nicht den Spielverkehr und ändert nicht den Weg. Ein Relay braucht eigene Server; liegt das Problem am Router (hoher Router-Ping und Schwankung), hilft ein Relay über dasselbe WLAN nicht.
- Die Entfernung setzt eine Untergrenze: Licht im Glasfaserkabel braucht etwa 1 ms pro 100 km hin und zurück, Null Ping ist also unmöglich. Die Seite nennt deshalb die Lücke zwischen Minimum und Durchschnitt als den Teil, der noch zu gewinnen ist.

## Methode

1. Alle Tweaks aus den wichtigsten veröffentlichten Tuning-Anleitungen und Tweak-Programmen sammeln.
2. Zu jedem suchen: (a) Dokumentation von Microsoft oder dem Hersteller, (b) eine reproduzierbare Messung, (c) den Windows-Standardwert.
3. In die vier Stufen oben einordnen und Begründung und Quelle notieren.
4. Was keinen Nachweis hat, kann man mit dem Tweak-Test auf dem eigenen PC prüfen, denn keine Liste kennt deine Hardware.

Die Einordnung steht in der App in [`src/catalog/evidence.js`](../src/catalog/evidence.js), eine Zeile pro Tweak mit Hinweis und Quelle. Wenn du eine bessere Quelle oder eine Messung kennst, die einem Eintrag widerspricht, eröffne bitte ein Issue.

## Hauptquellen

- [valleyofdoom/PC-Tuning](https://github.com/valleyofdoom/PC-Tuning): Anleitung und Recherche mit Messungen (Timer-Auflösung, Interrupts, Energie, Dienste).
- [djdallmann/GamingPCSetup](https://github.com/djdallmann/GamingPCSetup): Recherche zu MMCSS, Diensten und dem Netzwerk-Stack.
- [Tom’s Hardware](https://www.tomshardware.com/news/windows-11-gaming-benchmarks-performance-vbs-hvci-security): Benchmark von VBS und HVCI in Spielen.
- [Bruce Dawson, Random ASCII](https://randomascii.wordpress.com/2020/10/04/windows-timer-resolution-the-great-rule-change): Änderung der Timer-Regel.
- [Guru3D](https://forums.guru3d.com/threads/disadvantages-to-radeon-anti-lag-why-not-enabled-by-default.438984/): Nachteile von Anti-Lag.
