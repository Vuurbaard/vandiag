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

Found by OCR search of the whole PDF (diagnostics/log.md T-024). The PCM on
the van is a Continental SID208, Ford part number BK21-12A650-AC, with three
lever-lock connectors side by side. Which physical position is which has not
been confirmed for C175E/C175T. The left connector (cream lever) has 48
cavities and so cannot be C175B (T-025). **The middle connector (black lever,
brown/orange housing, TE 1563196-1) has 53 cavities and is C175B** (T-026):
five large cavities 1–5 in one row, then rows 6–17, 18–29, 30–41, 42–53 with
medium-size cavities at the row ends. Open point: in the T-026 photo large
cavity 5 looks empty and 4 looks populated, while p.238 has VPWR on 5 and
nothing on 4. Confirmed by eye in T-027: 1 and 5 empty, 2, 3, 4 populated.
**Treat every C175B pin number below as unverified for this van until the
cause of this mismatch is known.**

Cavities holding a terminal, by eye from the mating face (T-030; the reporter
says this was hard to see and may contain mistakes): large 2, 3, 4; 6, 8, 9,
11, 13–17; 18–24, 26–28; 30, 33, 34, 37, 38, 39; 44–47, 52. By this list the
diagram's pins 5, 7, 10, 29, 42, 48 and 53 are empty on the van, so the
moulded numbers do not line up with the diagram's pin numbers. Identify pins
by measurement from known ends, not from the table below.

Measured on the van so far (moulded cavity numbers):

| Cavity | Finding | Log |
| --- | --- | --- |
| 1, 5 | Empty | T-027 |
| 2 | **Supply pin**: connected to the PCM side of fuse F35 (beep with F35 pulled; 3.9–4 Ω with fuse in, value to be re-measured). No connection to ground. p.238 calls pin 2 a ground | T-030, T-033, T-034, T-035 |
| 3, 4 | Terminal present; not connected to F35. Function unknown | T-027, T-033 |

| Connector | Circuits seen so far | Source |
| --- | --- | --- |
| C175B | Power, grounds, wake, relay control (p.238); HS CAN (p.298); exhaust gas temperature sensor 3, pin 8 (p.245) | sections 151-2, 23-17 |
| C175E | Fuel metering valve pin 25, shield pin 37 (p.239); coolant temperature sensor pins 18/22 (p.245). Wired straight to engine-mounted parts | sections 151-2 / 151-10 |
| C175T | Oxygen sensor, fuel vaporizer pump (p.239); intake air, ambient air, exhaust gas temperature 1 and 2 (p.245). Runs through inline connectors C134/C139/C144 | sections 151-2 / 151-10 |

OCR page hits (200dpi, may be incomplete): C175B on p.101, 102, 104, 232,
237, 238, 242, 245, 246, 249–253, 281, 282, 294, 298, 348, 373, 514; C175E on
p.89, 239, 243, 247, 376; C175T on p.99, 239–241, 243–245, 250, 253, 348,
376, 501.

To pick out C175B on the van, look for its wire set from p.238: four
black-green (pins 2, 3, 42, 53), one black-yellow (pin 7), three yellow-grey
(pins 29, 17, 5), one yellow-blue (pin 48), one violet-orange (pin 28).

**Physical position/appearance of C175B is still unconfirmed** — this PDF
does not appear to have a "connector end views" appendix (checked the final
pages, p.633–637, none found). Identify it in the van directly: Ford
connectors are normally labeled on the housing itself near the latch/lever.

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
