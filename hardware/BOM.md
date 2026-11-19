# Stückliste (Bill of Materials)

Referenzen entsprechen dem Schaltplan `treppenlicht.kicad_sch`. Als CSV: [BOM.csv](BOM.csv).

| Ref | Anz. | Bauteil | Wert | Gehäuse | Hinweis |
|-----|-----:|---------|------|---------|---------|
| U1 | 1 | D1 mini ESP32 (Wemos/Lolin) | – | Steckleisten 2×8 | ESPHome-Board `wemos_d1_mini32` |
| Q1 | 1 | N-Kanal Logic-Level-MOSFET | IRLZ44N | TO-220 | Alternativen: IRLZ34N, IRLB8721, AO3400A (SMD) |
| R1 | 1 | Widerstand | 100 Ω | THT 0207 | Gate-Vorwiderstand |
| R2 | 1 | Widerstand | 10 kΩ | THT 0207 | Gate-Pulldown (LED aus beim Booten) |
| R3 | 1 | Widerstand | 10 kΩ | THT 0207 | LDR-Teiler (optional) |
| R4 | 1 | Fotowiderstand (LDR) | GL5528 | 5 mm | optional |
| D1 | 1 | Schottky-Diode | 1N5819 | DO-41 | Entkopplung der MCU-Versorgung |
| F1 | 1 | PTC-Sicherung | 1,1 A hold | Radial | z. B. Bourns MF-R110 |
| C1 | 1 | Elektrolytkondensator | 1000 µF / ≥ 10 V | Radial D8 | nah an Klemme J2 |
| C2 | 1 | Keramikkondensator | 100 nF | RM 5 | Abblocken |
| J1 | 1 | Schraubklemme 2-polig | RM 5,08 | – | Eingang 5 V (oder USB-Breakout mit Klemmen) |
| J2 | 1 | Schraubklemme 2-polig | RM 5,08 | – | LED-Streifen |
| J3, J4 | 2 | Stiftleiste 1×3 | RM 2,54 | – | PIR unten / oben |
| – | 2 | PIR-Bewegungsmelder | HC-SR501 o. ä. | – | 5 V Versorgung, 3,3 V-Ausgang |
| – | 1 | USB-Steckernetzteil | 5 V / 1 A | – | vorhanden |
| – | 1 | LED-Band 5 V, einfarbig | < 0,7 A | – | vorhanden |
| – | 1 | Lochrasterplatine | ca. 5×7 cm | – | Aufbau |
| – | – | Leitung | ≥ 0,5 mm² | – | 5 V / LED-Strecke |

## Strombudget (Netzteil 1 A)

| Verbraucher | Strom |
|-------------|------:|
| LED-Band bei 100 % | < 0,70 A |
| ESP32 (WLAN-Spitzen) | ~0,25–0,35 A |
| 2× PIR | ~0,10 A |
| **Summe Spitze** | **~1,05–1,15 A** |

Bei 100 % Helligkeit wäre das Netzteil an der Grenze. Die Firmware begrenzt deshalb
die Helligkeit standardmäßig auf **80 %** (LED ≈ 0,56 A, Summe < 0,9 A).
Mit einem 2-A-Netzteil kann der Wert auf 100 % erhöht werden.
