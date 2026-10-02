# Diagnostic log

Append-only. Do not edit or delete past entries to match a later theory — if a
result turns out to be wrong or incomplete, add a new entry that references the
original ID (e.g. "See T-001; conditions were incomplete").

Use the entry format defined in the repository README ("Diagnostic log format").
Sequential IDs: `T-001`, `T-002`, …

## T-001 — Characterize start attempt and preserve pre-test state

- Date/time: 2026-09-16 (exact time not recorded)
- Performed by: Sander
- Goal: Determine no-crank vs. crank-no-start vs. starts-and-stalls, and capture dash/audio behavior on a start attempt.
- Source: N/A (observational, no diagram used)
- Vehicle state: battery voltage not yet measured; key turned to crank position; engine off before and after
- Tool and mode: N/A (visual/audible observation only)
- Connector state: N/A — nothing disconnected
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A (data-gathering step)
- Actual result:
  - Key turned to crank, held briefly ("wait a bit"). Starter does **not** turn the engine — no-crank confirmed.
  - Chime audible on key-on/crank attempt.
  - Instrument cluster displays message: **"Engine, Service Now"** (exact wording as reported; icon/color not yet recorded).
  - Audible voice/text message from speakers to the effect of: **"Emergency contact not available. Visit a dealer for maintenance."** (paraphrased by reporter; likely a SYNC/911Assist-style system message — exact wording not yet confirmed).
  - Reporter unsure whether the two messages are related to each other or independent.
- Interpretation: No-crank confirmed (updates README checklist). The SYNC/emergency-assist message implies the cluster and SYNC/APIM module are at least partially active and able to display/announce messages; whether this reflects a genuine network fault (consistent with H-03 PCM comms failure) or a separate/unrelated SYNC subsystem message (e.g. modem/TCU-specific) is not yet established. Do not treat this as confirming a network-wide fault yet — needs the full module scan (checklist item 2) to see which modules do/don't respond.
- Evidence files/photos: none yet — recommend photographing the cluster message and noting exact icon/text next attempt.
- Next action: See T-002.

## T-002 — Relay/battery observation and pre-replacement timeline (reported, not yet measured)

- Date/time: 2026-09-16 (exact time not recorded)
- Performed by: Sander
- Goal: Capture remaining detail from the T-001 start attempt (relay behavior, battery state) and establish the timeline of symptom onset relative to the battery replacement.
- Source: N/A (reported/observational)
- Vehicle state: batteries reported freshly charged; exact resting voltage not yet given as a number
- Tool and mode: N/A
- Connector state: N/A
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result:
  - A large relay located next to the two (twin starter) batteries audibly clicks every time the key is turned to crank. Relay identity (label/number) and which circuit it belongs to are not yet confirmed against the wiring diagram — do not assume it is the starter relay.
  - Battery voltage described only qualitatively as "good" after a charger session; reporter believes battery condition is not the cause. No numeric reading recorded yet, and no reading taken *during* a crank attempt (under load).
  - **New timeline detail:** the very first symptom was the key remote/fob suddenly no longer unlocking the van "the next day," and this happened **before** the battery replacement. The old batteries (dated 2015) were then suspected and replaced as a reaction to that symptom, not because of a prior known power/no-start complaint. Replacing both batteries did not fix the no-start/no-comms issue.
- Interpretation: This weakens simple causation from H-01 ("problem appeared after battery replacement") — the earliest known symptom (remote entry failure) predates the battery swap, so the battery replacement looks like a troubleshooting reaction to an earlier fault rather than the origin of it. Whether the fob/remote-entry failure and the current no-crank/no-PCM-comms fault share one root cause (e.g. BCM, RF receiver, network, or a slow parasitic drain that was already present in 2015-dated batteries) or are two separate faults is unconfirmed. The relay click confirms *some* command/coil-power path is functional but does not confirm the relay passes load current or that the correct circuit is involved — needs diagram identification before further conclusions.
- Evidence files/photos: none yet.
- Next action: see follow-up questions in conversation; still need dash lamp list, immobilizer icon behavior, a numeric battery voltage reading (both batteries individually, at rest and if possible during a crank attempt), relay label/ID if visible, and whether the remote-entry fault is still present today / whether a spare fob or mechanical key was tried.

## T-003 — Remote-entry clarification and disclosure of prior driver's seat removal

- Date/time: 2026-09-16 (exact time not recorded)
- Performed by: Sander
- Goal: Clarify remote-entry fault scope; capture a newly disclosed prior repair action (driver's seat removed for cleaning) that had not been mentioned before.
- Source: N/A (reported)
- Vehicle state: N/A
- Tool and mode: N/A
- Connector state: **Driver's seat was previously removed** (to clean the seat and the floor underneath), meaning the seat wiring harness connector(s) were disconnected and later reconnected at some point. Number of connectors, whether the battery was disconnected first, and whether every connector was fully re-seated/locked are not yet known.
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result:
  - Remote fob cannot unlock the van (confirmed still failing today). Central locking itself works — turning the physical key blade in the driver door lock cylinder locks/unlocks normally. Reporter considers the fob a non-issue since the van can't be started regardless.
  - **New disclosure:** the driver's seat was removed at some point (for cleaning) — order relative to the fob failure and battery replacement not yet established.
- Interpretation: Since mechanical-key central locking works, the BCM/door-lock actuator output path has power, ground, and is functional — this makes a totally dead BCM or main BCM power/ground fault less likely, and suggests the RF remote-entry failure may be a separate, lower-priority fault (e.g. fob battery/pairing/RF receiver) rather than proof of a shared root cause. Not conclusive either way.
  The driver's-seat removal is a new, previously-undisclosed event and a strong candidate root cause: seat harness connectors are a common real-world source of exactly this symptom pattern (network/module communication faults, intermittent power) if a connector is left unseated, a locking tab isn't clipped, a pin is pushed back, or a connector was missed entirely during reassembly. This must be checked before deeper electrical testing, and needs to be placed on the diagnostic timeline relative to when the no-start/no-comms fault and the fob failure began.
- Evidence files/photos: none yet — recommend photographing the seat connectors before and after inspection.
- Next action: establish timeline order (seat removal vs. fob failure vs. battery replacement) and visually inspect all seat harness connectors for full engagement — see follow-up questions in conversation.

## T-004 — Timeline sequencing (reported)

- Date/time: 2026-09-16 (exact time not recorded)
- Performed by: Sander
- Goal: Order the seat removal, a 2-week idle period, and the fob failure on one timeline.
- Source: N/A (reported)
- Vehicle state: N/A
- Tool and mode: N/A
- Connector state: unchanged from T-003; still not inspected
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result: Reported order of events:
  1. Driver's seat removed (start of cleaning project).
  2. Van then sat unused for a **2-week holiday**.
  3. Returned, resumed cleaning the van. Fob worked fine at this point.
  4. "One day" after that, the fob stopped working.
  5. (Previously logged, T-002/H-01) Old 2015 batteries were then suspected and replaced — did not fix no-start/no-comms.
  - Not yet established: whether the seat was fully reinstalled (bolted down, all connectors reconnected and locked) *before* leaving for holiday, or reinstalled *after* returning, and how that reinstall timing relates to when the fob stopped working.
- Interpretation: The van standing idle for 2 weeks is a plausible innocent explanation for the batteries (dated 2015) being found weak/old — doesn't by itself point to a fault. The open question that actually matters is whether the fob failure happened shortly after the seat connectors were last handled (supporting the seat-connector hypothesis) or well after (weakening it). Needs the reinstall-timing detail to interpret.
- Evidence files/photos: none yet.
- Next action: get reinstall-timing detail and perform the visual seat-connector inspection (still outstanding from T-003).

## T-005 — Full narrative timeline (reported)

- Date/time: 2026-09-16 (exact time not recorded)
- Performed by: Sander
- Goal: Establish the complete, ordered sequence of events from seat removal to the current no-start/no-comms fault.
- Source: N/A (reported)
- Vehicle state: N/A
- Tool and mode: N/A
- Connector state: see sequence below
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result: Reported order of events, superseding the partial picture in T-004:
  1. Driver's seat removed **before** the holiday, specifically as an anti-theft measure (an immobilized/seatless van is harder to drive away).
  2. Two-week holiday — van sits with seat out.
  3. Returns from holiday. Seat cleaned indoors, in the living room (i.e. away from the van, fully disconnected). Van interior also cleaned a bit, seat still not yet back in.
  4. **One day, notices the fob doesn't work.** At this point the seat is still out of the van.
  5. Inspects batteries — finds them "kinda dead." Decides to replace both.
  6. Waits for replacement batteries, then fits both new batteries.
  7. **Reattaches the seat.**
  8. Turns the key in the ignition for the first time since all this work — this is the **first-ever occurrence** of the chime + "Engine, Service Now" + SYNC-style "visit a dealer" message (i.e. today's T-001 symptom did not exist before this point; it began immediately after the new batteries were fitted and the seat reattached).
  9. Removes the seat **again** afterward, to get back at the batteries and "the fuse box there" (confirms a fuse box is located in the same under-seat area as the batteries, alongside the relay noted in T-002).
  10. With the seat removed a second time, turns the key again — **same chime / "Engine, Service Now" result**, unchanged.
  - Not yet established: during this second seat removal (step 9–10), were the seat's own wiring harness connectors actually unplugged, or was only the seat cushion/frame moved aside while its plugs stayed connected? This determines how much weight the "same result with seat off" observation carries against the seat-connector hypothesis.
  - Not yet established: exact battery reinstall procedure — order of terminal connection, whether polarity was verified (e.g. with a meter, or by matching old cable to same post), whether the two batteries are confirmed wired in parallel (as they should be) rather than accidentally in series, any sparks noticed, and whether the fuses in that same under-seat fuse box have been visually inspected since.
- Interpretation: This is a materially different — and much more useful — picture than T-002/T-004 suggested. Two important shifts:
  1. The fob failure happened while the seat was still fully removed and disconnected, which is *consistent with* (but doesn't prove) a seat-connector or under-seat-power cause, since nothing in that area was connected at the time.
  2. Critically, the current no-start/"Engine, Service Now"/no-PCM-comms fault has **never existed before the battery replacement + seat reattachment**, and it appeared on the very first key-turn afterward. That is a much stronger, more immediate temporal correlation than "next day" — this now makes an error or damage introduced during the battery reinstall (polarity, a blown fuse, a poorly seated main power connector, a chafed/pinched wire during seat reassembly) the leading hypothesis, ahead of a generic "seat connector not fully seated" theory.
  The fact that the symptom was identical with the seat removed the second time is evidence *against* a simple "seat connector not seated" cause — but only if that second removal genuinely disconnected the seat's own harness. If it didn't, this data point doesn't discriminate anything.
- Evidence files/photos: none yet.
- Next action: clarify whether the seat's own connectors were unplugged during the second removal, and inspect the battery reinstall (polarity, parallel vs. series, terminal tightness) and the local fuse box for damage — see follow-up questions in conversation.

## T-006 — Reinstall visual check, seat-connector clarification, and CAN resistance measurement

- Date/time: 2026-09-16 (exact time not recorded)
- Performed by: Sander
- Goal: Close out the battery/fuse visual check, confirm seat-connector handling, and record a new CAN-bus resistance measurement.
- Source: N/A (visual check) / N/A (resistance measurement — meter make/model, exact conditions not yet recorded)
- Vehicle state: not fully specified for the resistance reading — ignition/sleep state, how long the vehicle had been undisturbed, and battery connection state are not yet confirmed
- Tool and mode: multimeter, resistance/ohms mode (assumed — not explicitly confirmed)
- Connector state: seat harness connectors reported disconnected on **both** seat removals (not just the frame moved aside) — see interpretation
- Reference/ground point: N/A
- Probe points: reported as OBD-II DLC pins 6 (CAN-H) and 14 (CAN-L) — not yet explicitly reconfirmed for this specific reading, assumed consistent with historical H-06 method
- Expected result: a healthy dual-terminated HS-CAN bus reads ~60 Ω across CAN-H/CAN-L (two 120 Ω terminators in parallel) when fully asleep
- Actual result:
  - Battery reinstall (terminal matching, parallel wiring, tightness) and the under-seat fuse box: both **visually** checked, no problems seen. Visual only — no meter continuity/voltage check of individual fuses yet, no independent polarity verification with a meter.
  - Seat harness connectors were **disconnected** (not just the seat frame moved) on both the first and second seat removals; the no-start/no-comms symptom was unchanged either way.
  - New measurement: **CAN-H to CAN-L resistance ≈ 120 Ω** (reproduces the historical H-06 reading of 118–120 Ω, now from a fresh, user-performed measurement rather than an unverified historical report).
- Interpretation:
  - The seat-connector hypothesis is now significantly weakened: connectors were fully unplugged both times and the fault didn't change. Keeping it open only as a low-priority "damaged during handling" possibility, not as a live intermittent-connection cause.
  - The visual-only battery/fuse check is reassuring but not conclusive — it doesn't rule out a fuse that reads open under load, a resistive/corroded terminal, or a subtly wrong reconnection. Still worth a loaded voltage check later, but no longer the most efficient next step.
  - **120 Ω instead of the expected ~60 Ω is a real, meaningful signature**: it is consistent with only one of the two HS-CAN termination resistors being present in the measured loop, i.e. the network is effectively split, or one terminator's module/branch is disconnected, unpowered, or internally faulted. This does **not** yet identify *which* module or wire — per the repository's rule 8, this must not be used to justify replacing a module without first verifying power, ground, and wiring. It does, however, strongly justify a full module scan next, to see which modules respond and which don't, which will localize which segment/branch of the bus is missing.
- Evidence files/photos: none yet.
- Next action: run and report a complete FORScan module scan (all modules found vs. not found, plus adapter/model/mode and any error text), and confirm the exact conditions used for the 120 Ω reading (how long the vehicle sat undisturbed, ignition state, meter mode, exact pins).

## T-007 — FORScan full module/DTC scan (photo of results)

- Date/time: 2026-09-16 (exact time not recorded)
- Performed by: Sander
- Goal: Full module discovery/DTC scan to see which modules communicate and which don't, to localize the branch missing from the CAN bus (per T-006 interpretation).
- Source: N/A (FORScan tool output, not the diagram)
- Vehicle state: not fully specified (ignition state during scan not explicitly confirmed, assumed key ON per prior request)
- Tool and mode: FORScan v2.3.71, vehicle profile "Ford Transit / Tourneo Custom Duratorq Turbo Diesel Common Rail Injection 2.2L 2012.7...". Reporter notes a a specific saved profile is required to get any readings at all — without loading that profile, no readings occur. Adapter model and switch/auto mode not yet recorded.
- Connector state: OBD-II adapter connected
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result (transcribed from photo, module: code list):
  - **PCM: Error** — detail pane: "Unable to read DTC / Module: Powertrain Control Module". PCM is the only module that outright fails to respond to a DTC read.
  - APIM: B1D79:13-0B, U0151:00-0B, U0423:00-0B, U0452:00-0B
  - SASM: U3003:62-28
  - PAM: U0100:87-2F, U0121:87-2F, U0401:86-2F, U0415:86-2F, B1B52:14-2F
  - HCM: U0121:00-0B
  - BCMii: U0100:00-0A, U0121:00-0A, U0151:00-0A, U023A:00-0A, B10AD:87-0A, B109E:87-0A
  - IPMB: None
  - FCDIM: U3006:16-28
  - ACM: U3006:16-28, B1A56:15-2F, B1A03:11-28, B1A04:11-28
  - IPC: P1607:82-2F, U0121:00-2F, U0422:64-2F, U0415:64-2F, U0401:64-2F, U0100:00-2F
  - All modules other than PCM returned a real DTC list, i.e. FORScan successfully read each of them individually.
- Interpretation (unconfirmed detail flagged): every module except PCM is reachable and returned its own stored codes — this means the OBD-II DLC wiring, the FORScan adapter, and the CAN bus as a whole are fundamentally working enough to reach APIM, SASM, PAM, HCM, BCMii, FCDIM, ACM, and IPC. **PCM is uniquely silent.** Several other modules log U0100 ("Lost Communication with ECM/PCM", generic SAE definition — not yet confirmed against FORScan's own on-screen text) and U0401 ("Invalid Data Received From ECM/PCM") — consistent with them simply reporting that *they* lost contact with the PCM, i.e. a downstream/cascading symptom, not a general network failure. This lines up very well with the T-006 resistance finding: if the PCM houses one of the two HS-CAN termination resistors (a plausible but unconfirmed layout), losing the PCM from the bus would explain both "PCM won't respond" and "~120 Ω instead of ~60 Ω."
  Several modules (PAM, HCM, BCMii, IPC) also show U0121/U0415/U0422, which on generic SAE lists relate to lost/invalid data from an ABS-type module — **not yet confirmed**, since FORScan's own definition text for these codes hasn't been captured (only PCM's definition pane was visible in the photo). It's also unconfirmed whether these are *current* or *stored/historical* codes (e.g. logged during the period batteries were dead) — DTC memory can persist until cleared. Do not treat the ABS-related reading as confirmed until FORScan's own text and current/stored status are checked.
  Net effect: this scan meaningfully narrows the fault toward the **PCM's own circuit** (power, ground, wake feed, connector, or internal fault) rather than a DLC/gateway/global-network problem, and does so without yet needing module replacement (per rule 8, power/ground/wiring must still be verified before concluding PCM is internally faulty).
- Evidence files/photos: photo of FORScan DTC screen provided by reporter (not yet saved into `evidence/scans/`).
- Next action: verify PCM grounds by voltage-drop test, using diagram data already on hand (PDF page 1, printed section 151-2: PCM connector C175B pins 2, 3, 42, 53 grounded via G105; pin 7 grounded via G104) — see proposed test in conversation. Also: click through 2–3 of the U0121/U0415/U0422 codes in FORScan to capture their exact on-screen definitions and current/stored status.

## T-008 — Recalled dash light: traction-control/ESC icon (reported, unconfirmed)

- Date/time: 2026-09-16 (exact time not recorded)
- Performed by: Sander
- Goal: Capture a recalled observation of a dash warning icon (car with squiggly/skid lines — traction control / ESC) and its possible link to the ABS/SASM-related DTCs seen in T-007.
- Source: N/A (recalled observation, not a fresh check)
- Vehicle state: unspecified — not tied to a specific dated key-on attempt
- Tool and mode: N/A
- Connector state: N/A
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result: Reporter recalls the traction-control/ESC icon (car silhouette with skid-mark lines) being lit at some point. Unsure whether this was because traction control was manually switched off (via a dash button) or because of a genuine ABS/ESC module fault. Reporter believes the separate dedicated ABS icon (circle/text "ABS") was *not* lit, based on not recalling noticing it — not a confirmed negative check.
- Interpretation: Ambiguous as reported. A steadily-lit traction-control icon **without** the ABS icon is the normal, expected appearance when traction control is manually disabled via a dash switch — not necessarily a fault. However, it could also align with the U0121/U0415/U0422 codes on PAM/HCM/BCMii/IPC (T-007), if those do turn out to reference an ABS/ESC-family module (SASM), and with historical H-05 ("ABS also reported as not functioning"). Not enough here to promote to a confirmed finding either way.
- Evidence files/photos: none.
- Next action: on the next key-on, deliberately look at the cluster for (a) whether the traction-control icon is steady or flashing, (b) whether the separate ABS icon is lit at all, and (c) whether there's a physical traction-control/ESC-off button on the dash that could explain it being manually disabled. This is secondary to the still-pending PCM ground voltage-drop test from T-007.

## T-009 — Unidentified engine-bay multi-pin connector opened for pin inspection

- Date/time: 2026-09-16 (exact time not recorded, after T-007/T-008, while looking for C175B)
- Performed by: Sander
- Goal: (Reporter's own test) Inspect pin condition on a large, lever/cam-locked multi-pin connector found in the engine bay while searching for the PCM/connector C175B.
- Source: N/A (identity of this connector not yet established — not yet confirmed to be C175B or any other diagram-named connector)
- Vehicle state: not fully specified
- Tool and mode: none (visual only)
- Connector state: reporter intentionally opened this connector by hand (exact release method not understood/repeatable); **current state (plugged back in vs. still open) not yet confirmed as of this entry**
- Reference/ground point: N/A
- Probe points: N/A (visual pin inspection only, no meter used)
- Expected result: N/A
- Actual result:
  - Connector is a large sealed multi-circuit type (~10+ wires: red, several brown/tan, light blue, green/olive, white, purple visible in photo) with a black hinged lever/cam-style lock, mounted near a corrugated conduit and close to what looks like a fuse/relay box, in the engine bay (exact side/location not yet specified).
  - Reporter confirms this is **not** connector C175B.
  - **With this connector unplugged, the dashboard does not light up at all** — a materially different (more severe/total) result than the previously established baseline (T-001: chime + "Engine, Service Now" + SYNC message, dash otherwise responsive).
  - Reporter unplugged it deliberately but cannot recall or reproduce the exact release mechanism, and does not currently know for certain whether it is now fully reconnected and locked.
- Interpretation: This connector sits on a circuit that the dash instrument cluster depends on for any illumination — it is clearly a significant shared power/ground/signal path, whatever component it belongs to. This is a useful data point but **introduces a new, uncontrolled variable**: if it is not currently fully reseated and locked, all testing done after this point (including a repeat of the basic key-on check) would be invalid, and this disconnection event itself could now be confounding the investigation, independent of the original fault. This event happened after T-001 and T-007, so it does not retroactively affect those earlier results, which were taken before this connector was ever touched.
- Evidence files/photos: photo of the connector, showing it partly separated with the pin/socket faces visible (not yet saved to `evidence/photos/`).
- Next action: confirm current physical state (plugged in and fully locked, or still open); if not certain it's fully seated, carefully reconnect and verify before any further testing; then repeat the T-001 baseline key-on check to confirm nothing changed as a result of this exploration, before resuming the PCM ground test plan.

## T-010 — Reconnected engine-bay connector confirmed; external "C175B" pinout source checked and rejected

- Date/time: 2026-09-16 (exact time not recorded)
- Performed by: Sander
- Goal: Close out T-009 and evaluate an externally-found PDF claiming to be a C175B pinout.
- Source: https://www.ford-trucks.com/forums/attachment.php?attachmentid=269495 (checked, see interpretation)
- Vehicle state: N/A
- Tool and mode: N/A
- Connector state: the T-009 connector is confirmed plugged back in; dash confirmed lighting up again (baseline behavior restored)
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result: reporter found a PDF on a Ford Truck Enthusiasts forum thread titled "2006 F-150 5.4 4x4 Pcm pinout," attachment labeled "C175B." The forum's own attachment description states it was **"Generated by ChatGPT"** and documents a PCM connector for a **2006 Ford F-150 with a 5.4L V8** — not this repository's vehicle (2016 Ford Transit Custom V362, 2.2L TDCi).
- Interpretation: **Do not use this file for this vehicle.** Two independent reasons: (1) it is for a completely different Ford platform, market, and engine — Ford connector labels like "C175B" are not standardized across platforms/model years, so a matching label is coincidence, not confirmation (per README rule 4, diagram applicability must be verified by engine/build, and this fails that check outright); (2) even for its stated vehicle, the source itself says it was AI-generated from a forum upload, not an official Ford diagram, so it would be unreliable even if the vehicle matched. This does not replace the need to locate C175B's actual pinout in the supplied repository PDF (`Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`) or another vehicle-correct source.
- Evidence files/photos: none (source rejected, not saved).
- Next action: still need to (a) physically identify/locate connector C175B on the actual van (photo of its label, per the earlier request) or (b) find its pinout in the correct wiring-diagram PDF already in this repo, before doing the PCM ground voltage-drop test with confirmed pin numbers.

## T-011 — Located additional C175B (PCM, 2.2L) pin data in the wiring-diagram PDF

- Date/time: 2026-09-16 (exact time not recorded)
- Performed by: Claude (diagram search, at reporter's request, "for later")
- Goal: Locate more of connector C175B's pinout ahead of time, specifically anything relevant to power/network testing, since the PDF has no index/text layer and pages had to be sampled visually.
- Source: `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`, sampled pages 290–309 (this vehicle is 2.2L; the document interleaves near-identical-looking pages for a 2.0L variant, which must not be used)
- Vehicle state: N/A
- Tool and mode: N/A
- Connector state: N/A
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result: confirmed additional **C175B** (2.2L, section 23-17) pins:
  - **Pin 10 = HS CAN+, pin 11 = HS CAN−** (PDF p.298, "Start/Stop system" diagram) — direct PCM-side CAN bus pins.
  - Pin 41 = SMCS (same page).
  - Pin 52 = LFC, pin 27 = HFC (PDF p.294, "Cooling Fan" diagram) — fan control outputs, not diagnostically relevant here but confirms the connector/section.
  - **Not found in this pass:** the 2.2L PCM main power-feed circuit (battery/ignition-switched supply, fuses, main relay). A 2.0L version of this circuit was found (PDF p.300: fuses F15/F44, a DC/DC converter box, connector labeled "C0175B" pin 74) but this must **not** be used for this vehicle.
- Interpretation: **Critical naming trap identified** — this document contains two visually similar connector labels: **"C175B"** (no leading zero, section "23-x", confirmed correct for this vehicle's 2.2L PCM) and **"C0175B"** (with a leading zero, section "24-x", belongs to the 2.0L engine variant only). They are not the same connector and must not be cross-used, per README rule 4. All pin data logged above is C175B (2.2L) only. The PCM main power-feed page has not yet been located for 2.2L specifically — do not substitute the 2.0L page found at PDF p.300 for it.
  The new CAN+ / CAN− pins (10/11) are directly useful for the still-pending PCM investigation: once back-probe access is available, these can be checked/compared against DLC pins 6/14 to help localize where the bus is broken relative to the PCM.
- Evidence files/photos: none (source is the repository's own PDF, already cited).
- Next action: still need (a) the 2.2L PCM main power-feed page (not yet found), and (b) the pending PCM ground voltage-drop test and physical identification of C175B on the actual van. No urgency — reporter is between diagnostic sessions.

## T-012 — Located PCM power/relay/wake circuit via OCR search of the PDF

- Date/time: 2026-09-16 (exact time not recorded)
- Performed by: Claude, with reporter's approval to install `tesseract` OCR (`sudo pacman -S tesseract tesseract-data-eng`, run by reporter in their own terminal since this session has no interactive sudo prompt)
- Goal: Find the still-missing 2.2L PCM main power-feed page after manual page-sampling (T-011) failed to locate it.
- Source: `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`, all 637 pages
- Vehicle state: N/A
- Tool and mode: `pdftoppm` at 300dpi (first attempt at 120dpi was too low-resolution for usable OCR) + `tesseract --psm 11`, output searched with `grep`/`awk` for "175B" across all pages, then candidate pages cross-checked against power-related keywords (JUNCTION BOX, VPWR, VBATT, RELAY)
- Connector state: N/A
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result: OCR search found **C175B mentions scattered across pages 89–515** (PCM circuitry is not clustered in one contiguous section in this compiled PDF — confirms manual sampling was always going to struggle). Cross-referencing candidates against power keywords surfaced **PDF page 238** (confirmed "2.2L" in the corner) as the PCM power/relay/wake circuit. Visually verified (not just OCR-trusted) — see updated pinout in `references/diagram-notes.md`: pins 28 (PCM WAKE), 29/17/5 (VPWR), 48 (PCMRC), plus grounds 2/3/7/42/53 which match the p.1 grounds page exactly.
- Interpretation: We now have diagram-confirmed pin data for grounds, power (VPWR/wake/relay-control), and CAN bus (pins 10/11, from T-011) — everything needed to fully test the PCM's external requirements per README rule 8, once physical back-probe access is available. The OCR approach (needed a 300dpi re-render; the first 120dpi pass was unusable) is a viable way to search this PDF in future if more pages are needed, without burning many manual visual-sampling calls.
- Evidence files/photos: none (source is the repository's own PDF, already cited). OCR intermediate files were written to a local scratch directory outside the repo, not committed.
- Next action: nothing further needed from the diagram for now. Still pending: physical identification of C175B on the van, and the actual voltage tests (grounds, VPWR, WAKE, CAN) once back-probe pins arrive. No urgency — reporter is between diagnostic sessions.

## T-013 — First numeric battery voltage reading

- Date/time: 2026-09-29 (exact time not recorded)
- Performed by: Sander
- Goal: Get the first numeric battery voltage reading, which T-002 asked for.
- Source: N/A
- Vehicle state: not yet specified. Unknown: key position, how long since the last charge, key-on or crank attempt, and whether any load (doors open, dome lights) was on.
- Tool and mode: multimeter, DC volts (model not recorded)
- Connector state: not specified. Unknown whether both batteries were still connected in parallel or were measured separately.
- Reference/ground point: not specified. Assumed to be across the battery posts.
- Probe points: not specified
- Expected result: a fully charged, rested 12 V lead-acid/AGM battery reads about 12.6–12.8 V. Near 12.4 V means about 75% charge, near 12.2 V about 50–60%, and below about 12.0 V means discharged.
- Actual result: **12.28 V**
- Interpretation: If this is a rested, key-off reading across the posts, the batteries are only about half charged. That is lower than expected for batteries T-002 described as "freshly charged," so it suggests either a slow drain (a parasitic draw, possibly a module that stays awake) or an incomplete charge. It is not a reading taken while cranking, so it neither confirms nor rules out a supply problem as the cause of the no-crank. 12.28 V is well above the level where modules normally stop communicating, and every other module answered in T-007, so this voltage alone does **not** explain why the PCM is silent. The PCM circuit tests (grounds, VPWR, WAKE) from T-012 stay the leading next step. Conditions still need confirming before the number is used further.
- Evidence files/photos: none.
- Next action: confirm the measurement conditions (see conversation), then do the loaded/key-on voltage check as part of the C175B power tests.

## T-014 — Measurement conditions for T-013 confirmed

- Date/time: 2026-09-29 (exact time not recorded)
- Performed by: Sander
- Goal: Fill in the missing conditions for the T-013 battery voltage reading.
- Source: N/A
- Vehicle state: key off. Van idle for about 2 weeks (last recorded session was 2026-09-16, T-007 to T-012). Not yet known when the batteries were last charged, or whether anything was charging them during the idle period.
- Tool and mode: multimeter, DC volts
- Connector state: both batteries connected together (normal parallel setup)
- Reference/ground point: battery − post
- Probe points: directly on the battery posts (not the clamps)
- Expected result: see T-013
- Actual result: confirms T-013's **12.28 V** as a fully rested, key-off, open-circuit reading of the combined battery pack.
- Interpretation: With the van this well rested, surface charge is not a factor. 12.28 V is a genuine state of charge of about 50–60%. Whether this is a problem depends on when the batteries were last fully charged:
  - If they were charged fully around 2026-09-16 or later, losing this much in 2 weeks while idle points to an **abnormal parasitic drain**, meaning something is not going to sleep. That fits the original 2015-dated batteries going flat and the fob symptom (T-002) as well. Not confirmed.
  - If they were last charged long before that, 12.28 V may just be normal self-discharge plus the key-on sessions on 2026-09-16.
  None of this changes the T-013 conclusion that 12.28 V does not by itself explain the silent PCM.
- Evidence files/photos: none.
- Next action: find out the last full-charge date; take the key-on and (optionally) cranking readings requested in T-013. A parasitic-draw (current) test is a candidate for later, after the PCM power tests, depending on the charge history.

## T-015 — Last full-charge date unknown

- Date/time: 2026-09-29
- Performed by: Sander
- Goal: Establish when the batteries were last fully charged, to interpret T-013/T-014.
- Source: N/A
- Vehicle state: N/A
- Tool and mode: N/A
- Connector state: N/A
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result: unknown. The garage charged them last, possibly a month or more ago. No exact date.
- Interpretation: The T-014 question cannot be answered from history. 12.28 V after an unknown period of a month or more fits normal self-discharge plus the key-on sessions just as well as a parasitic drain. The drain hypothesis stays **open but unsupported**. It can't be settled from this data; a controlled test is needed: charge fully, record the date, then recheck the rested voltage after a known number of days.
- Evidence files/photos: none.
- Next action: fully charge the batteries (record the date/time the charge finished), then take the T-013 key-off / key-on / crank readings on a known-good supply.

## T-016 — Battery voltage after charging

- Date/time: 2026-10-02 (exact time not recorded)
- Performed by: Sander
- Goal: Recharge the batteries and record the voltage, as asked for in T-015.
- Source: N/A
- Vehicle state: not yet specified. Unknown: key position, when the charge finished, and how long the charger had been off before the reading.
- Tool and mode: multimeter, DC volts (assumed, as in T-013)
- Connector state: not specified. Assumed both batteries connected in parallel, as in T-014. Unknown whether the charger was still connected.
- Reference/ground point: not specified. Assumed battery − post, as in T-014.
- Probe points: not specified. Assumed directly on the battery posts, as in T-014.
- Expected result: about 12.6–12.8 V for a fully charged, rested pack (see T-013). A reading taken soon after charging can sit higher than the true rested value because of surface charge.
- Actual result: **12.75 V** (up from 12.28 V in T-013/T-014)
- Interpretation: The pack took a charge and now reads in the fully-charged range. If the reading was taken soon after the charger came off, some of it is surface charge and the rested value will be a little lower; that still leaves the supply good enough for the PCM circuit tests. This gives the known starting point T-015 asked for: a rested key-off reading after a known number of days will show whether there is an abnormal drain. It does not change the T-013 conclusion that battery voltage alone does not explain the silent PCM.
- Evidence files/photos: none.
- Next action: confirm when the charge finished and how long the charger was off before the reading; then take the key-on reading at the battery posts that T-013 asked for.

## T-017 — Measurement conditions for T-016 confirmed

- Date/time: 2026-10-02 (exact time not recorded)
- Performed by: Sander
- Goal: Fill in the missing conditions for the T-016 battery voltage reading.
- Source: N/A
- Vehicle state: key off. Charge finished about 6 hours before the reading.
- Tool and mode: multimeter, DC volts
- Connector state: assumed both batteries connected in parallel and the charger disconnected (not explicitly stated)
- Reference/ground point: at the batteries themselves
- Probe points: at the batteries themselves (posts vs. clamps not explicitly stated)
- Expected result: see T-016
- Actual result: confirms T-016's **12.75 V** as a key-off reading taken about 6 hours after charging.
- Interpretation: After 6 hours most surface charge has gone, so 12.75 V is a genuine near-full state of charge. The supply is now a known-good starting point for the key-on reading and the PCM circuit tests. It is also the baseline for the drain check from T-015: charge finished on 2026-10-02, about 6 hours before a 12.75 V reading. A rested key-off reading after a known number of days, with no key-on sessions in between or with those noted, can be compared against it.
- Evidence files/photos: none.
- Next action: key-on reading at the battery posts (outstanding since T-013), and optionally the lowest voltage during a crank attempt.
