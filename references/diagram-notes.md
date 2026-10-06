# Diagram notes

Running index of confirmed page/connector/pin references from
`Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`. Only add entries once
confirmed against the diagram itself (cite PDF page + printed section/sheet
identifier). Do not guess or fill gaps — leave them open and note where to look
next.

This PDF has no text layer, bookmarks, or index (confirmed — `pdftotext`
returns nothing and there are no `/Outlines`), so pages can only be found by
visual sampling. Record what's found here so it doesn't need to be re-searched.

The document interleaves diagrams for two engine variants, sometimes on
adjacent pages, sometimes far apart. **Always check the "2.0L" / "2.2L" label
printed in the top-right corner of the page before using it** — this vehicle
is **2.2L**.

## Connector C175B — Powertrain Control Module (PCM), 2.2L

> ⚠️ Do not confuse with **C0175B** (leading zero) — that is the equivalent
> connector on the **2.0L** variant, under a different section index (24-x
> instead of 23-x). Pin numbers differ between the two and must not be mixed.

| Pin | Function | Source (PDF page / printed section) |
| --- | --- | --- |
| 2 | Ground (to G105) | p.1 & p.238, section 151-2 |
| 3 | Ground (to G105) | p.1 & p.238, section 151-2 |
| 7 | Ground (to G104) | p.1 & p.238, section 151-2 |
| 42 | Ground (to G105) | p.1 & p.238, section 151-2 |
| 53 | Ground (to G105) | p.1 & p.238, section 151-2 |
| 28 | PCM WAKE (from BCM, wire CE436) | p.238, section 151-2 |
| 29 | VPWR (switched battery power) | p.238, section 151-2 |
| 17 | VPWR (switched battery power) | p.238, section 151-2 |
| 5 | VPWR (switched battery power) | p.238, section 151-2 |
| 48 | PCMRC — PCM Relay Control (PCM's own output that holds its power relay closed) | p.238, section 151-2 |
| 10 | HS CAN+ | p.298, section 23-17 |
| 11 | HS CAN− | p.298, section 23-17 |
| 41 | SMCS (start/stop related) | p.298, section 23-17 |
| 27 | HFC (cooling fan, high speed) | p.294, section 23-17 |
| 52 | LFC (cooling fan, low speed) | p.294, section 23-17 |

### PCM power-feed circuit (found — PDF p.238, "2.2L")

- **AUXILIARY JUNCTION BOX (AJB, section 11-1)**, fuses **F15 (40A)** and
  **F14 (5A)**, both "Hot at all times" (section 13-7). An earlier version of
  this note said F14 was 3A; a 300dpi re-read of p.238 shows **5A** (see
  diagnostics/log.md T-019).
- These feed a dedicated **PCM relay**, physically inside the **BATTERY
  JUNCTION BOX (BJB)** (section 11-3), through connector C139:
  - F15 → C139 pin 6 → wire SB115 (WH-RD) → relay pin **3** (switch contact
    feed).
  - F14 → C139 pin 24 → wire SB114 (BN-RD) → relay pin **1** (coil feed).
- The relay's switched output (pin **5**) feeds two things:
  - **BJB fuse F35 (15A, section 13-7)** → wire CBB35 (YE-GY) → splice S103 →
    PCM connector C175B pins **29, 17, 5 (VPWR)**.
  - wire CE612 (GY-VT) → splice S112 → other engine-control loads (references
    A/B/C to sections 23-3 and 23-5; not traced).
- Relay coil pin **2** → wire CE302 (YE-BU) → C175B pin **48 (PCMRC)**. The
  coil is fed from F14 and the PCM completes the circuit on pin 48, so the
  relay only closes when the PCM itself commands it. This is the
  self-power-latch circuit that lets the PCM stay powered briefly after
  key-off.
- A separate wake signal from the BCM arrives on pin **28 (PCM WAKE)**, wire
  CE436 (VT-OG), from BCM connector C2280C pin 70 through C139 pin 23.
- Ground wires: pin 7 → GD121 (BK-YE) → S118 → G104; pins 2, 3, 42, 53 →
  GD120 (BK-GN) → S101 → G105 (section 10-1).
- **F35 is the easiest test point on this circuit**: voltage on it at key-on
  shows whether the PCM relay has closed, without needing access to C175B.
- Physical locations of the AJB and BJB on the van are not yet confirmed from
  the diagram (sections 11-1 / 11-3 not yet located in the PDF).
- Grounds shown on this same page (pins 2, 3, 7, 42, 53) match the p.1
  grounds-index page exactly — good cross-check that both sources are
  reliable.
- Found via OCR search (tesseract, 300dpi renders of all 637 pages) after
  manual page-sampling failed to locate it — see diagnostics/log.md T-012.

### The PCM has three connectors: C175B, C175E, C175T (2.2L)

The PCM on the van is a Continental SID208, Ford part number BK21-12A650-AC,
with three lever-lock connectors side by side (T-024). Marked photo:
`evidence/photos/marked-pcm-connectors-identified.jpg`.

| Position on the van | Housing | Cavities | Identity | Basis |
| --- | --- | --- | --- | --- |
| Left | Cream/white lever, TE 1719679 | 48 (4 × 12) | **C175E** | By elimination; pin numbers seen in the diagram (up to 40) fit 48 cavities. Not directly verified |
| Middle | Black lever, brown/orange housing, TE 1563196-1, "A" on lever | 53 | **C175T** | All 19 C175T pins found in the diagram are populated on the van; 9 of 16 C175B pins are empty (T-038) |
| Right | Black lever, black housing with red face, TE 1563196-1 | 53 | **C175B** | Terminals in large 2, 3, 5 and medium 17, 29, 41, 42, 53, as p.238/p.298 require (T-039) |

**Correction:** T-026 identified the middle connector as C175B because it has
53 cavities. That was wrong: C175T uses the same 53-cavity housing. T-027 to
T-037 were all measured on C175T. The diagram's pin numbers were never in
conflict with the van (T-038).

53-cavity layout as moulded on the housing: five large cavities 1–5 in one
row, then rows 6–17, 18–29, 30–41, 42–53 with medium-size cavities at the row
ends.

Circuits per connector, from the diagram:

| Connector | Pins and circuits seen so far | Source |
| --- | --- | --- |
| C175B | 2, 3, 42, 53 GND (G105); 7 GND (G104); 5, 17, 29 VPWR; 28 PCM WAKE; 48 PCMRC (p.238). 10 HS CAN+, 11 HS CAN−, 41 SMCS (p.298). 27 HFC, 52 LFC (p.294). 8 exhaust gas temperature sensor 3 (p.245) | sections 151-2, 23-17 |
| C175E | 25 fuel metering valve, 37 shield (p.239); 18/22 coolant temperature (p.245); 29/7/1 fuel rail pressure, 15/34/4 camshaft sensor, 5 oil pressure switch, 21/40/19 oil level/temperature (p.244). Wired straight to engine-mounted parts | sections 151-2 / 151-10 |
| C175T | 2 fuel vaporizer pump, 3 oxygen sensor heater, 16/27/13/14 oxygen sensor (p.239); 26 and 28 glow plug relay (p.240); 37/8/30 DPF pressure sensor (p.244); 11/6 intake air temp, 21/18 ambient air temp, 22/33 EGT1, 47/34 EGT2 (p.245) | sections 151-2 / 151-10 |

OCR page hits (200dpi, may be incomplete): C175B on p.101, 102, 104, 232,
237, 238, 242, 245, 246, 249–253, 281, 282, 294, 298, 348, 373, 514; C175E on
p.89, 239, 243, 247, 376; C175T on p.99, 239–241, 243–245, 250, 253, 348,
376, 501.

Cavities holding a terminal on the **middle connector (C175T)**, by eye from
the mating face (T-030, T-037; hard to see, may contain mistakes): large 2,
3, 4; 6, 8, 9, 11, 13–16; 18–24, 26–28; 30, 33, 34, 37, 38, 39; 44–47, 52.

Measured on C175T: cavity 2 reads a steady 3.9–4.0 Ω to one side of the F35
socket ("slot B") with the fuse pulled, and no connection to ground (T-033,
T-036). Per p.239 pin 2 is the fuel vaporizer pump, which is fed from the PCM
relay output through fuse F39. So slot B is the relay side of F35 and the
4 Ω is most likely the pump itself. No fault is indicated.

To confirm C175B on the van: 53 cavities, with terminals in large cavities 2,
3 and 5 and in medium cavities 17, 29, 42 and 53. Wire set from p.238: four
black-green (2, 3, 42, 53), one black-yellow (7), three yellow-grey (29, 17,
5), one yellow-blue (48), one violet-orange (28).

Outside corroboration of the C175B numbers (T-038): a bench-programming
pinout for the SID208 in PSA vans gives GND on 2, 3, 7, +12 V on 5, 28, 39 and
CAN on 10/11; a Transit Custom no-start case online cites PCM pin 48 for the
R17 relay control and pins 5, 17, 29 for PCM power.

This PDF does not appear to have a "connector end views" appendix (checked
the final pages, p.633–637, none found).

## HS CAN branch to the PCM and ABS module (PDF p.218, "2.2L", Module Communications Network)

p.298 refers to this sheet as 14-5. Found by OCR search for wire name VDB04
(T-041).

- C175B pin 10 (HS CAN+, VDB04 WH-BU) → splice **S107**; pin 11 (HS CAN−,
  VDB05 WH) → splice **S108**. Twisted pair.
- From S107/S108 down: **C1010 pins 3/4** → ABS module **C135 pins 26/14**.
- From S107/S108 up: **C139 pins 47/48** → splices **S297/S296** → restraints
  control module C310B pins 48/47, and on through C311 pins 42/43 (with C192
  pins 4/10 and 3/9 on early production) to the rest of the network (sheet
  14-4).
- The PCM and the ABS module therefore share one branch behind C139.
- No end resistor is drawn on this sheet. Where the two terminators sit is
  still unconfirmed.
- Other 2.2L network sheets are around PDF p.214–220 (p.214 has the DLC).
- Location of C139 on the van: not found yet.

Also on C175B: pin 39 = ignition feed from BJB F7 (CBB07 GN-BU, p.104);
pin 47 = START from the ignition switch via C210 pin 51 and C139 pin 16
(CDC35 BU-WH, p.101/102).

## Fuse box layouts (Ford owner's manual, "Fuse Specification Chart - 2.2L Diesel")

Source: Ford online owner's manual page linked from Sander's own notes
(fordservicecontent.com, variantid 6946, moidRef G539642). The page does not
state a model year, so check the layout against the real box before trusting a
position. Layout images saved in `references/fuse-boxes/`. See
diagnostics/log.md T-020.

| Owner's manual name | Wiring-diagram name (p.238) | PCM-related items | Layout image |
| --- | --- | --- | --- |
| Engine compartment fuse box | Battery Junction Box (BJB) | **F35 15A** PCM; **R17** PCM relay; F7 7.5A PCM + telematics module | `E148826-engine-compartment-fuse-box.jpg` |
| Passenger compartment fuse box | Auxiliary Junction Box (AJB) | **F14 5A** PCM; **F15 40A** PCM | `E148827-passenger-compartment-fuse-box.jpg` |

The name mapping is inferred from matching fuse numbers, ratings and the PCM
relay; neither document states it outright.

- **F35 position (engine compartment box):** right-hand column of small fuses
  (F33–F39, top to bottom), third from the top, directly left of the large
  relays R16/R17. R17 (PCM relay) is the third large relay down on the right
  edge.
- **The passenger compartment box also has a fuse numbered F35.** That is a
  different circuit. The PCM fuse is the one in the engine compartment box.
- F7 (7.5A, engine compartment box, bottom of the left-hand column of small
  fuses) is a PCM feed that does not appear on p.238. Its circuit has not been
  traced in the wiring diagram.
- Other engine compartment relays from the same page: R9 starter motor, R12
  fuel pump, R1 ignition relay 3, R2 not used.
