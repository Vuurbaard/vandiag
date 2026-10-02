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

**Physical location/appearance of C175B is still unconfirmed** — this PDF
does not appear to have a "connector end views" appendix (checked the final
pages, p.633–637, none found). Identify it in the van directly: Ford
connectors are normally labeled on the housing itself near the latch/lever.
