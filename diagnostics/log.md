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

## T-018 — Battery voltage at key-on

- Date/time: 2026-10-02 (exact time not recorded)
- Performed by: Sander
- Goal: See how far the battery voltage drops under the key-on load (outstanding since T-013).
- Source: N/A
- Vehicle state: key ON, held about 10 seconds; no crank attempt made; engine off. Rested key-off voltage beforehand 12.75 V (T-016/T-017).
- Tool and mode: multimeter, DC volts
- Connector state: assumed both batteries connected in parallel, charger disconnected
- Reference/ground point: same spot on the battery as T-016/T-017
- Probe points: same spot on the battery as T-016/T-017
- Expected result: a drop of a few tenths of a volt, staying above about 12.2 V. Below about 12 V at key-on alone would point to a weak pack or a poor main connection.
- Actual result: **about 12.35 V** (a drop of about 0.40 V from 12.75 V). No reading during cranking.
- Interpretation: Within the expected range. The pack holds up under the key-on load, so the battery supply is not what keeps the PCM silent. This reading does not test the heavy starter cables, because no crank current was drawn. Whether the voltage was steady or still falling at 10 seconds was not recorded.
- Evidence files/photos: none.
- Next action: move on to the PCM power circuit. See T-019.

## T-019 — PDF p.238 re-read: F14 rating corrected, F35 found in the VPWR path

- Date/time: 2026-10-02
- Performed by: Claude (diagram re-read at 300dpi)
- Goal: Pick the least invasive first test on the PCM power circuit now that the battery supply is confirmed good.
- Source: `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`, PDF page 238, printed "2.2L", PCM section 151-2
- Vehicle state: N/A
- Tool and mode: N/A
- Connector state: N/A
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result:
  - **Correction to T-012 / `references/diagram-notes.md`:** AJB fuse F14 is **5A**, not 3A. This matches the "F14 5 A" in historical entry H-08.
  - **Not noted before:** the PCM relay output (relay pin 5) reaches the PCM through **BJB fuse F35 (15A)**, then wire CBB35 (YE-GY) and splice S103 to C175B pins 29/17/5 (VPWR).
  - The relay coil is fed from F14 on relay pin 1. Relay pin 2 goes on wire CE302 (YE-BU) to C175B pin 48 (PCMRC). The relay therefore only closes when the PCM itself completes the coil circuit.
  - F15 (40A) feeds the relay switch contact on relay pin 3.
- Interpretation:
  - Historical entry H-12 ("pin 2 no feed", "F35 about 0.04 V without a relay") now has a likely reading: if it refers to this relay and this fuse, both results are what the diagram predicts with the relay removed, and are not evidence of a fault. H-12's connector and conditions were never documented, so this is unconfirmed.
  - F35 is a test point for the whole chain without access to C175B. Voltage on F35 at key-on means F15, the relay contacts, and the PCM's own relay command all work. No voltage on F35 means the relay is not closing, and the cause is upstream: F14/F15 feed, the relay, the wake signal, or the PCM not commanding it.
  - The physical locations of the AJB and BJB are not confirmed from the diagram. H-08 places "F14 5 A and F15 40 A" in the engine bay, which is reported history only.
- Evidence files/photos: none (source is the repository's own PDF).
- Next action: measure voltage on both test points of F35 (15A) at key-off and key-on, reference battery −.

## T-020 — F35 and the PCM relay located via the owner's manual fuse chart

- Date/time: 2026-10-02
- Performed by: Claude (lookup at reporter's request, from a link in the reporter's own notes)
- Goal: Find where F35 physically is, so the T-019 test can be done.
- Source: Ford online owner's manual, "Fuse Specification Chart - 2.2L Diesel" (fordservicecontent.com, variantid 6946, moidRef G539642), layout figures E148826 (engine compartment fuse box) and E148827 (passenger compartment fuse box). Model year is not stated on the page.
- Vehicle state: N/A
- Tool and mode: N/A
- Connector state: N/A
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result:
  - **F35 (15A, "Powertrain control module") is in the engine compartment fuse box**: right-hand column of small fuses (F33–F39), third from the top, next to relays R16/R17.
  - **R17 in the engine compartment fuse box is the Powertrain control module relay.**
  - F14 (5A) and F15 (40A), both "Powertrain control module", are listed in the **passenger compartment fuse box**.
  - F7 (7.5A, engine compartment fuse box) is listed as "Powertrain control module. Telematics control unit module." This feed is not on PDF p.238.
  - The passenger compartment fuse box has its own, unrelated F35.
  - Layout images saved to `references/fuse-boxes/`; details in `references/diagram-notes.md`.
- Interpretation:
  - Fuse numbers, ratings and the PCM relay match PDF p.238, so the diagram's "Battery Junction Box" is the engine compartment fuse box and its "Auxiliary Junction Box" is the passenger compartment fuse box. This mapping is inferred, not stated by either source.
  - Historical entry H-11 ("R17 produced a whining sound") may be about the PCM relay, if H-11's R17 was in the engine compartment box. A relay that whines or buzzes is usually being switched rapidly or held weakly. That would fit a PCM that starts to power up and drops out again. Unconfirmed: H-11 never recorded which box.
  - Historical entry H-08 places "F14 5 A and F15 40 A" in the engine bay, while the owner's manual puts the PCM's F14/F15 in the passenger compartment box. Those earlier checks may have been done on the wrong fuses. Unconfirmed.
  - The page gives no model year. Compare the layout image with the real box before measuring.
- Evidence files/photos: `references/fuse-boxes/E148826-engine-compartment-fuse-box.jpg`, `references/fuse-boxes/E148827-passenger-compartment-fuse-box.jpg`
- Next action: the F35 test from T-019, in the engine compartment fuse box. While the key is on, also listen and feel for whether R17 clicks once, buzzes, or does nothing.

## T-021 — Voltage at F35 (PCM relay output), key off and key on

- Date/time: 2026-10-02 (exact time not recorded)
- Performed by: Sander
- Goal: Find out whether the PCM relay closes at key-on and delivers power towards the PCM (test proposed in T-019).
- Source: `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`, PDF page 238, printed "2.2L", PCM section 151-2; fuse position from owner's manual figure E148826 (T-020)
- Vehicle state: battery 12.75 V rested (T-017), about 12.35 V at key-on (T-018); key OFF, then key ON; engine off
- Tool and mode: multimeter, DC volts
- Connector state: fuse F35 left in place, nothing disconnected
- Reference/ground point: assumed battery − as instructed (not explicitly restated)
- Probe points: both test points on top of F35 (15A), engine compartment fuse box
- Expected result: key off about 0 V on both points; key on about battery voltage on both points if the relay closes.
- Actual result:
  - Key off: **0 V** on both test points.
  - Key on: **12.38 V** on both test points.
  - Not reported: what relay R17 does at key-on (single click, buzz/whine, nothing), and whether the real box matches the layout picture. Finding F35 where the picture shows it suggests it does.
- Interpretation:
  - F35 is intact, and at key-on full battery voltage leaves the fuse box for the PCM. F15 (40A) and the relay contacts are therefore working. This also clears the doubt raised in T-020 about H-08's check of F14/F15.
  - Per p.238 the relay coil is fed from F14 (hot at all times) and its other side goes only to PCM pin 48 (PCMRC). The relay is open with the key off and closed with the key on, so something is switching pin 48 with the key. A wire shorted to ground would hold the relay closed with the key off too, and that is not what was measured. The simplest reading is that **the PCM wakes up and commands its own relay**. That needs the PCM to have its wake signal, at least one ground, and working logic. It matches the garage's report H-04 ("PCM powers up but has no output").
  - A meter cannot tell a steadily closed relay from one that chatters quickly; a stable 12.38 V reading makes heavy chatter unlikely but does not rule it out (see H-11).
  - This weakens "missing PCM power/wake" as the cause. Not yet shown: that the 12.38 V actually arrives at C175B pins 29/17/5 (wire CBB35, splice S103), and that all five grounds hold under load.
  - With the PCM apparently awake but absent from the bus, and 120 Ω instead of 60 Ω at the DLC (T-006), the CAN wiring between the PCM (C175B pins 10/11) and the rest of the network becomes the leading suspect, ahead of an internal PCM fault. Whether one of the two terminators is inside the PCM is still unconfirmed.
- Evidence files/photos: none.
- Next action: check F7 (7.5A, engine compartment fuse box, the remaining PCM fuse) key off and key on. After that the tests move to the PCM connector C175B.

## T-022 — Voltage at F7, and relay R17 emits a high-pitched tone at key-on

- Date/time: 2026-10-02 (exact time not recorded)
- Performed by: Sander
- Goal: Check the remaining PCM fuse (F7) and observe what the PCM relay R17 does at key-on (asked for in T-020/T-021).
- Source: owner's manual fuse chart and figure E148826 (T-020) for F7 and R17; PDF page 238, printed "2.2L", section 151-2 for the relay circuit. F7's own circuit has not been traced in the wiring diagram.
- Vehicle state: key OFF, then key ON; engine off. Battery about 12.3–12.4 V at key-on (T-018, T-021).
- Tool and mode: multimeter, DC volts; relay behavior by ear
- Connector state: F7 left in place. **Relay R17 was pulled out with the ignition on** as part of the observation; assumed refitted afterwards (not stated).
- Reference/ground point: assumed battery − as instructed
- Probe points: both test points on top of F7 (7.5A), engine compartment fuse box
- Expected result: both test points equal; battery voltage at least with the key on. Relay: a single click at key-on, then silent.
- Actual result:
  - F7, key off: **0 V** on both test points.
  - F7, key on: **12.28 V** on both test points.
  - With the ignition on, **R17 buzzes heavily: a steady high-pitched tone, not a rattle.**
  - Pulling R17 with the ignition on makes the tone stop.
- Interpretation:
  - F7 is intact and is an ignition-switched feed (dead with the key off). Together with T-021, every fuse listed for the PCM in the owner's manual now has voltage at key-on, except F14, whose function is shown indirectly by the relay closing.
  - This reproduces historical entry H-11 ("R17 produced a whining sound") as a fresh observation and settles which R17 it was.
  - A relay coil on steady DC is silent after its click. A continuous tone means the coil current is being switched on and off rapidly. The contacts still pass a steady 12.38 V (T-021), so the switching is too fast for the contacts to follow.
  - Per p.238 the only thing that switches this coil is the PCM, on pin 48 (PCMRC). So either (a) the PCM's relay command is pulsing, or (b) the relay itself is faulty. For (a), one explanation that would also account for the missing CAN communication is a PCM that keeps restarting, for example because a supply pin or ground at C175B drops out under load. That is a hypothesis, not a finding. Whether a pulsed relay command is normal on this van is not known either.
  - The tone stopping when R17 is pulled shows R17 is involved, but pulling it also cuts power to everything it feeds (wire CE612 to other engine-control loads), so it does not prove the sound comes from the relay body itself.
  - Key-on sessions today have used some charge; the T-017 drain baseline of 12.75 V no longer applies cleanly.
- Evidence files/photos: none. A short phone video with sound of the tone would be useful evidence.
- Next action: with the key off, swap R17 with an identical relay from the same box (same part number and pin layout printed on the case) and check whether the tone follows the relay or stays at the R17 position.

## T-023 — Relay swap R17/R9: tone stays at the R17 position; tone continues about a minute after key-off

- Date/time: 2026-10-02 (exact time not recorded)
- Performed by: Sander
- Goal: Find out whether the high-pitched tone (T-022) comes from a faulty relay or from the signal driving it.
- Source: owner's manual figure E148826 (T-020) for relay positions; PDF page 238, printed "2.2L", section 151-2 for the relay circuit
- Vehicle state: key OFF for the swap, then key ON; engine off
- Tool and mode: none (by ear)
- Connector state: relays R17 (PCM) and R9 (starter motor) exchanged; reported as the same relay type. Markings on the case not recorded. Whether they have been swapped back is not stated.
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: tone stays at the R17 position if the drive signal causes it; tone moves to R9 or disappears if the original relay is faulty.
- Actual result:
  - With the former R9 relay in the R17 position: **same high-pitched tone** at key-on.
  - New observation: **the tone continues for about a minute after the key is removed**, then stops.
- Interpretation:
  - The relay is not the fault. The tone comes from how the coil at the R17 position is driven, which per p.238 is the PCM on pin 48 (PCMRC).
  - The minute of run-on after key-off is the self-latch described on p.238: the PCM holds its own relay closed for a while after the key is off, then releases it. So the PCM is powered, awake, and running at least enough of its program to manage its own shutdown. It is still absent from the CAN bus (T-007).
  - The T-021 "key off = 0 V" reading at F35 must have been taken with the relay released (before key-on, or more than about a minute after key-off). Unconfirmed, but it fits.
  - It is still not known whether a pulsed relay command is normal on this PCM or a sign of trouble (unstable supply or ground at the PCM, or an internal fault). The orderly one-minute shutdown fits a PCM that is running steadily better than one that keeps restarting, but does not settle it.
  - Everything that can be checked from the fuse box has now been checked. The open questions are all at connector C175B: supply on pins 29/17/5, the five grounds under load, and the CAN wires on pins 10/11.
- Evidence files/photos: none.
- Next action: physically locate the PCM and connector C175B on the van (still outstanding from T-010/T-012) and photograph the connector and its label, without unplugging anything yet. Confirm the two relays are back in their original positions.

## T-024 — PCM located; it has three connectors (C175B, C175E, C175T), C175B not yet identified

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander (photo), Claude (diagram search)
- Goal: Physically locate the PCM and connector C175B (next action from T-023).
- Source: `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`, OCR search of all 637 pages (200dpi, `tesseract --psm 11`) for "C175"; PDF pages 238, 239 and 245, all printed "2.2L", PCM sections 151-2 / 151-10, read visually
- Vehicle state: not stated; nothing measured
- Tool and mode: N/A (visual)
- Connector state: nothing disconnected (stated by reporter)
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result:
  - PCM found. Label: **Continental SID208**, Ford part number **BK21-12A650-AC**, "1PGC", "J38AC", date 15-12-11, serial S180146202. Where on the van it sits has not been recorded yet.
  - The PCM has **three** connectors side by side, each with a rotating lever lock. In the photo: left has a cream/white lever and a thick taped harness going down into a large conduit; middle has a black lever with a brown slide lock (a letter "A" appears to be moulded on the lever) and loose brown/green/blue/white/violet wires; right has a black lever and its own conduit. No connector name is readable on any housing in the photo.
  - The OCR search finds three connector names on the 2.2L PCM: **C175B** (28 hits), **C175T** (16 hits), **C175E** (6 hits). C0175B/C0175E are the 2.0L equivalents and do not apply.
  - p.239 and p.245 show which circuits use which connector: C175E carries engine-mounted items wired straight to the PCM (fuel metering valve pin 25, coolant temperature sensor pins 18/22); C175T carries sensors that pass through inline connectors C134/C139/C144 (oxygen sensor, intake and ambient air temperature, exhaust gas temperature 1 and 2); C175B carries power, grounds, CAN (p.238, p.298) and exhaust gas temperature sensor 3 on pin 8.
- Interpretation:
  - The diagram has no connector face views, so it does not say which physical position is C175B. This is still open.
  - C175B is the only one of the three that should hold four black-green wires (pins 2, 3, 42, 53), one black-yellow (pin 7) and three yellow-grey (pins 29, 17, 5), per p.238. That wire set is the way to identify it without unplugging anything.
  - The loose wires visible at the middle connector are thin and in sensor-type colours, with no black-green or yellow-grey visible. That fits C175T or C175E better than C175B, but the photo shows only part of that bundle, so this is weak.
  - The date code 15-12-11 on the PCM is consistent with a van first registered 2016-04-15.
- Evidence files/photos: `evidence/photos/2026-10-05-pcm-three-connectors.png`
- Next action: without unplugging, look at the wires entering each of the three connectors and report which one has the group of black-green and yellow-grey wires; photograph each connector's wire side and any moulded markings or pin numbers. Also record where on the van the PCM sits, and whether relays R17/R9 are back in their original positions (still open from T-023).

## T-025 — Left PCM connector unplugged: 48 cavities, so it is not C175B

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: (Reporter's own step) Identify which of the three PCM connectors is C175B.
- Source: PDF page 238, printed "2.2L", section 151-2 (C175B pin numbers up to 53); pages 239 and 245 (C175E up to pin 37, C175T up to pin 47 seen so far)
- Vehicle state: key state and time since key-off at the moment of unplugging not stated
- Tool and mode: N/A (visual)
- Connector state: **left PCM connector (cream/white lever) unplugged.** Not yet confirmed reconnected.
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result:
  - The mating face has cavity numbers moulded at the row ends: **1, 13, 25, 37** on one end and **12, 24, 36, 48** on the other. Four rows of 12, **48 cavities**. The two columns at the 12/24/36/48 end are larger terminals.
  - Markings on the housing: TE logo, what reads as "0-1719679-2" on the grey part and "9-2236284-9" on the black wire cover, and a letter "C". Read from a photo, not verified.
  - Wires visible at the cover: green, white, orange, light blue. No black-green or yellow-grey group visible, but most of the bundle is hidden by the cover.
  - No green or white corrosion visible on the terminals in the photo. Some sand/dirt on the outside near the seal. The photo is not sharp enough to judge individual terminals.
- Interpretation:
  - C175B has ground pins 42 and 53 (p.238 and the p.1 grounds index). A 48-cavity connector has no pin 53, so **the left connector is not C175B**. It is C175E or C175T; which one is not established.
  - C175B is therefore the middle or the right connector, whichever has more than 48 cavities. This overturns the weak hint in T-024 that the middle connector looked unlike C175B.
  - Unplugging one PCM connector with the others attached changes nothing about earlier results, but the baseline should be rechecked after reconnecting (dash lights up as in T-001).
- Evidence files/photos: `evidence/photos/2026-10-05-pcm-left-connector-side.png`, `evidence/photos/2026-10-05-pcm-left-connector-face.png`
- Next action: reconnect the left connector and close its lever fully. Then, key out for at least 2 minutes, unplug the middle connector only and photograph its face and the moulded cavity numbers. The connector numbered past 48 is C175B.

## T-026 — Middle PCM connector unplugged: 53 cavities, matches C175B; large cavity 5 looks empty in the photo

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Identify C175B (next action from T-025).
- Source: PDF page 238, printed "2.2L", section 151-2 (pin 5 re-read from a 300dpi crop: VPWR on 29, 17, 5; GND on 7, 2, 3, 42, 53)
- Vehicle state: key state and time since key-off at the moment of unplugging not stated
- Tool and mode: N/A (visual)
- Connector state: **middle PCM connector (black lever, brown/orange housing) unplugged.** Whether the left connector was reconnected first is not stated. Right connector not touched.
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: a connector numbered past 48, with at least a cavity 53.
- Actual result:
  - Moulded cavity numbers on the face: a bottom row of **five large cavities numbered 1 to 5**, then four rows whose end cavities are marked **6 / 17, 18 / 29, 30 / 41, 42 / 53**. That is **53 cavities**. The row-end cavities are a medium size, the rest small.
  - Markings: TE logo, "1563196-1" and "PBT-GF30" on the face, "0-1563201-1" and "PA66-GF25" on the lever, letter "A" on the lever. Read from photos, not verified.
  - In the photo the three middle large cavities show a metal terminal, and **the two outer large cavities (1 and 5) look empty**. Read from one photo at an angle; not verified.
  - No green or white corrosion visible. Several wires in sensor-type colours leave the cover; the wires for the large cavities are not visible.
- Interpretation:
  - **The middle connector is C175B**, on two grounds: it has 53 cavities, and the pins p.238 uses for power and ground (2, 3, 5 and row ends 17, 29, 42, 53) fall on the larger cavities, as expected for current-carrying pins. The right connector has not been examined, so this rests on the match and not on elimination.
  - **Open discrepancy:** p.238 puts VPWR on pin 5 and grounds on pins 2 and 3, with nothing on pin 4. The photo suggests terminals in 2, 3 and 4 and none in 5. Either the photo misleads (terminal hidden or recessed), or this van's connector is populated differently from the diagram. This must be settled from the wire side before any reading is taken on "pin 5". Do not assume.
- Evidence files/photos: `evidence/photos/2026-10-05-pcm-middle-connector-face.png`, `evidence/photos/2026-10-05-pcm-middle-connector-side.png`
- Next action: on this connector, establish which of the five large cavities have a wire and each wire's colour (expected per p.238: black-green in 2 and 3, yellow-grey in 5), plus the colours at cavities 7, 17, 29, 42 and 53. Then reconnect, close the lever, and confirm the dash lights up as before.

## T-027 — C175B large cavities: 2, 3 and 4 populated, 1 and 5 empty (visual)

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Settle the discrepancy raised in T-026 between the connector photo and p.238.
- Source: PDF page 238, printed "2.2L", section 151-2
- Vehicle state: key state not stated
- Tool and mode: visual, looking into the cavities from the mating face. The wire side cannot be seen; the connector's plastic cover is in the way.
- Connector state: C175B (middle PCM connector) unplugged
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: per p.238, terminals in 2 and 3 (GND) and 5 (VPWR), none in 4.
- Actual result: **no metal in cavities 1 and 5. Cavities 2, 3 and 4 have a terminal.** Wire colours not determined.
- Interpretation:
  - The T-026 photo reading was right: this connector does not match p.238 at the large cavities. p.238 shows a wire on pin 5 and none on pin 4; the van has the opposite. Reading the moulded numbers in the other direction does not help, because the two outer cavities are the empty ones either way.
  - Not known: whether the diagram has pin 4 mislabelled as 5, whether this van is a different build from the one the diagram covers (README rule 4), or whether the cavity numbering in the diagram follows a different scheme from the numbers moulded on the housing. Until this is settled, **every C175B pin number taken from the diagram is unverified for this van**, including CAN on 10/11.
  - The function of cavities 2, 3 and 4 can be established by meter without the diagram.
- Evidence files/photos: `evidence/photos/2026-10-05-pcm-middle-connector-face.png` (T-026)
- Next action: with C175B unplugged and the key out, measure DC volts and then resistance to ground on large cavities 2, 3 and 4.

## T-028 — C175B large cavities 2, 3 and 4: 0 V and about 0 Ω to ground

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Establish by meter what the three populated large cavities of C175B are (next action from T-027).
- Source: PDF page 238, printed "2.2L", section 151-2
- Vehicle state: key out (as instructed; not restated), battery connected
- Tool and mode: AstroAI AM33D multimeter (manual ranging), DC volts, then ohms. Ohms range used not stated; 200 Ω was the instruction.
- Connector state: C175B unplugged; other two PCM connectors assumed plugged in
- Reference/ground point: **not stated** (battery negative or a body bolt near the PCM)
- Probe points: harness-side terminals in large cavities 2, 3 and 4, from the mating face
- Expected result: 0 V on all; two cavities under about 1 Ω (grounds) and one clearly higher (supply), if p.238 is only off by one pin.
- Actual result:
  - DC volts: **0 V on 2, 3 and 4.**
  - Leads together: reported as "0.02".
  - Ohms: reported as **"0 ohms" on 2, 3 and 4.** Exact displayed digits not given.
- Interpretation:
  - All three large terminals have a low-resistance path to the reference point. Read plainly, 2, 3 and 4 are all grounds, and none of the large cavities is the supply pin. That differs from p.238 by more than one mislabelled pin.
  - Not yet safe to conclude: the range and exact digits were not reported, and on a higher range a few ohms would also display as about zero. A supply wire seen through a low-resistance load could then be mistaken for a ground.
  - An ohmmeter reading shows continuity only. It does not show that these grounds carry load; that needs a voltage-drop test with the PCM connected and powered.
- Evidence files/photos: none.
- Next action: find where the supply from fuse F35 actually lands on C175B, by resistance between the F35 test point and cavities 4, 17 and 29.

## T-029 — Measurement conditions for T-028 confirmed

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Close the gaps in T-028's recorded setup.
- Source: N/A
- Vehicle state: as T-028
- Tool and mode: AstroAI AM33D, ohms, **200 Ω range**
- Connector state: as T-028
- Reference/ground point: **a ground point in the engine bay that the reporter has used for earlier measurements**; battery negative could not be reached with the leads. Exact location not recorded.
- Probe points: as T-028
- Expected result: N/A
- Actual result: range and reference confirmed as above.
- Interpretation:
  - On the 200 Ω range a reading of about zero means well under 1 Ω, so the T-028 caveat about a higher range no longer applies. **Large cavities 2, 3 and 4 of C175B are all connected to body ground.** p.238 shows only 2 and 3 as grounds and has no wire on 4.
  - The reference was a body ground, not battery negative, so this says nothing about the path from the body back to the battery.
- Evidence files/photos: none.
- Next action: unchanged from T-028: resistance between the F35 test point and cavities 4, 17 and 29.

## T-030 — C175B cavity population by eye; cavity 4 reads 0 Ω to a fuse, cavity 2 reads about 4 Ω

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Find which C175B cavities are fed by fuse F35 (next action from T-028/T-029), and record which cavities hold a terminal.
- Source: PDF page 238, printed "2.2L", section 151-2; p.298 section 23-17 for CAN pins; F35 position from owner's manual figure E148826 (T-020)
- Vehicle state: key out (as instructed; not restated), battery connected
- Tool and mode: visual with a light; AstroAI AM33D, DC volts, then ohms (range not restated, 200 Ω instructed)
- Connector state: C175B unplugged
- Reference/ground point: engine-bay ground used before (T-029) for the voltage reading
- Probe points: test point on top of the fuse; harness-side terminals in large cavities 4 and 2
- Expected result: 0 V on F35; under 1 Ω between F35 and any cavity that is a supply pin.
- Actual result:
  - Cavities with a terminal, as seen from the mating face. **The reporter says this was hard to see and may contain mistakes.**
    - Row 6–17: 6, 8, 9, 11, 13, 14, 15, 16, 17
    - Row 18–29: 18, 19, 20, 21, 22, 23, 24, 26, 27, 28
    - Row 30–41: 30, 33, 34, 37, 38, 39
    - Row 42–53: 44, 45, 46, 47, 52
    - Large row (T-027): 2, 3, 4
  - F35: **0 V**.
  - Fuse to cavity 4: **0 Ω**. Fuse to cavity 2: **3.9 to 4 Ω**.
  - The message says "f15" for the resistance readings and "f35" for the voltage reading. Taken as F35 for both, **unconfirmed**. The medium cavities were not measured.
- Interpretation:
  - If the fuse was F35: cavity 4 is directly connected to the PCM supply fuse, so **cavity 4 is a supply pin**, and the supply line shows about 4 Ω to ground (seen via ground cavity 2). That is where p.238 draws "pin 5".
  - This conflicts with T-028, where cavity 4 was reported as about 0 Ω to ground. Cavity 4 cannot be both 0 Ω to ground and 0 Ω to F35 while F35 is 4 Ω from ground cavity 2. One of the readings was mis-taken or reported loosely. Not resolved.
  - If the fuse really was an F15, the reading must be discarded: the passenger-compartment F15 is hot at all times, and resistance cannot be measured on a live circuit.
  - Whether about 4 Ω from the supply line to ground with the key off is normal is not known. Other engine-control loads hang on the same relay output (wire CE612, not traced).
  - By this list, several cavities the diagram uses are empty on the van: 5 (VPWR), 29 (VPWR), 7, 42 and 53 (GND), 10 (HS CAN+), 48 (PCMRC). The numbers moulded on this housing therefore do not line up with the pin numbers on p.238/p.298, by more than one pin. Possible causes: the diagram's numbering scheme differs from the housing's, or the diagram is for a different build. The list itself is uncertain, so no mapping is drawn from it.
  - Consequence: C175B pins must be identified on the van by measurement from known ends (F35 for supply, ground for grounds, relay R17 socket for the relay control wire, DLC for CAN), not read off the diagram.
- Evidence files/photos: none new. Marked image for the follow-up: `evidence/photos/marked-C175B-face-2-3-4.jpg`
- Next action: repeat as one set, 200 Ω range, exact display digits: leads together; ground to cavities 2, 3, 4; F35 to cavities 2, 3, 4; F35 to ground. Confirm which fuse was used.

## T-031 — Repeat readings on C175B cavities 2, 3, 4 contradict each other; meter setup in doubt

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Resolve the conflict between T-028 and T-030 with one consistent set of readings.
- Source: N/A
- Vehicle state: key out (as instructed; not restated), battery connected
- Tool and mode: AstroAI AM33D, ohms (200 Ω range as instructed, not restated), then continuity/beep mode for step 3
- Connector state: C175B unplugged
- Reference/ground point: engine-bay ground used before (T-029)
- Probe points: harness-side terminals in large cavities 2, 3, 4; test point on top of F35, engine compartment fuse box
- Expected result: if cavity 4 is the supply pin: ground to 2 and 3 about 0 Ω, ground to 4 about 4 Ω; F35 to 4 about 0 Ω; F35 to ground about 4 Ω.
- Actual result:
  - **T-030 fuse confirmed: F35 in the engine compartment fuse box**, for both the voltage and the resistance readings.
  - Leads together: "0.02".
  - Ground to cavities 2, 3, 4: "0" on all three.
  - F35 to cavities 2, 3, 4 on ohms: no usable reading; the reporter says the meter "reads weird" with the tips together and "measures nothing". In beep mode: **beeps only between F35 and cavity 2**; no beep to 3 or 4.
  - F35 to engine-bay ground: "0".
- Interpretation:
  - These readings cannot all be true, and they also contradict T-030 (F35 to cavity 4 was 0 Ω and F35 to cavity 2 was about 4 Ω; now the beep is on cavity 2 and not on 4). If F35 is 0 Ω to ground and cavities 2, 3 and 4 are 0 Ω to ground, F35 should beep to all three.
  - A true dead short from the F35 line to ground is ruled out by T-021: F35 held 12.38 V at key-on and the 15 A fuse did not blow.
  - The likely cause is in the measuring, not the van: meter range or mode, lead or battery condition, or poor contact when touching the terminals lightly from the front. A leads-together value of "0.02" has two decimals, which the 200 Ω range would not normally show; that suggests a higher range, on which a few ohms and zero look the same. Unconfirmed.
  - **No pin identification is drawn from T-028, T-030 or T-031 until the meter setup is verified.** What stands: cavities 1 and 5 are empty, 2, 3 and 4 hold terminals (T-027), and F35 is the engine compartment fuse.
- Evidence files/photos: none.
- Next action: verify the meter: photo of the dial, lead jacks and display with the tips held together on the ohms setting used.

## T-032 — Meter setup verified: 200 Ω range, OL open, 00.0 shorted

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Check the meter setup doubted in T-031.
- Source: N/A
- Vehicle state: N/A
- Tool and mode: AstroAI AM33D, dial on Ω 200, black lead in COM, red lead in VΩmA; fine needle-type probe tips
- Connector state: N/A
- Reference/ground point: N/A
- Probe points: probe tips apart, then held together
- Expected result: over-range with tips apart; about 0 with tips together, one decimal.
- Actual result: tips apart **"OL."**; tips together **"00.0"**.
- Interpretation:
  - The meter, range, jacks and leads are fine. The suspicion in T-031 that a higher range was in use is **withdrawn**; the reported "0.02" and "0" were loose transcriptions of a 00.x display. This meter shows "OL", not a single "1", when over range.
  - The contradictions between T-028, T-030 and T-031 are therefore not explained by the meter. Remaining candidates: unsteady contact on the terminals from the front, or the circuit not being fully dead. The other two PCM connectors and the battery are still connected, and a small standing voltage on a wire makes a resistance reading meaningless. Neither is confirmed.
  - A way round both: pull fuse F35, which per p.238 leaves the wire from the fuse to the PCM supply pins connected to nothing else, and measure on that isolated wire.
- Evidence files/photos: `evidence/photos/2026-10-05-meter-200ohm-tips-apart.png`, `evidence/photos/2026-10-05-meter-200ohm-tips-together.png`
- Next action: key out, F35 pulled, C175B unplugged: resistance from each of the two F35 socket slots to cavities 2, 3, 4 and to ground.

## T-033 — F35 pulled: one socket slot beeps to cavity 2 only, the other to none (ground readings missing)

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Find the C175B supply cavity on the isolated fuse-to-PCM wire (next action from T-032).
- Source: PDF page 238, printed "2.2L", section 151-2
- Vehicle state: key out (as instructed; not restated), battery connected
- Tool and mode: AstroAI AM33D, continuity/beep mode (chosen by the reporter; beeps below a few tens of ohms, exact threshold not looked up)
- Connector state: C175B unplugged; fuse F35 pulled (taken from the reporter's use of "slot a / slot b"; not explicitly confirmed)
- Reference/ground point: N/A for the readings reported
- Probe points: the two terminals of the empty F35 socket ("slot A", "slot B", arbitrary names); harness-side terminals in large cavities 2, 3, 4
- Expected result: one slot beeps to exactly one large cavity (the supply pin) and not to ground; the other slot beeps to no cavity.
- Actual result:
  - Slot A: **no beep** to cavities 2, 3 or 4.
  - Slot B: **beep to cavity 2 only**; no beep to 3 or 4.
  - Slot A to ground and slot B to ground: **not reported.**
  - An earlier reading the same day, "F35 to cavity: only cavity 2 beeps", was probably taken with the fuse in place and is not used.
- Interpretation: two readings fit, and the missing ground readings decide between them.
  - (a) Slot B is the PCM side of the fuse and **cavity 2 is the supply pin**. Then slot B must not beep to ground. This would contradict T-028, where cavity 2 read about 0 Ω to ground, unless that reading was taken through the fuse and the other loads.
  - (b) Slot B is the relay side, which reaches ground through other engine-control loads at a few ohms, and **cavity 2 is a ground**. Then slot B beeps to ground too, and the supply pin is not among the large cavities, because slot A reached none of them.
  - Under (b), cavities 3 and 4 should also have beeped if they are grounds as T-028 suggests. They did not, in T-031 or here. So either they are not grounds, or contact on them from the front is poor.
  - T-030 (fuse to cavity 4 at 0 Ω) fits neither reading and stays unexplained.
- Evidence files/photos: none. Slot naming shown in `references/fuse-boxes/F35-socket-slots-A-B.png`.
- Next action: with F35 still out, beep test slot A to ground, slot B to ground, and cavities 2, 3 and 4 each to ground.

## T-034 — F35 pulled: neither socket slot beeps to ground; cavities 2, 3, 4 do not beep to ground either

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Decide between readings (a) and (b) of T-033.
- Source: PDF page 238, printed "2.2L", section 151-2
- Vehicle state: key out (as instructed; not restated), battery connected
- Tool and mode: AstroAI AM33D, continuity/beep mode
- Connector state: C175B unplugged; F35 pulled (assumed, as T-033)
- Reference/ground point: engine-bay ground used before (T-029); exact location still not recorded
- Probe points: both F35 socket terminals; harness-side terminals in large cavities 2, 3, 4
- Expected result: (a) slot B silent to ground, cavity 2 silent to ground, 3 and 4 beep if they are grounds; (b) slot B and cavity 2 beep to ground.
- Actual result: **no beep** from slot A to ground, slot B to ground, or cavities 2, 3, 4 to ground.
- Interpretation:
  - Slot B is connected to cavity 2 (T-033) and neither reaches ground. That is reading (a): **cavity 2 of C175B is connected to the PCM side of fuse F35, so it is a supply pin.** This is a positive continuity result seen three times, which carries more weight than the silent ones. p.238 shows pin 2 as a ground and pin 5 as the supply, so the diagram's numbers do not match the moulded numbers here either.
  - Cavities 3 and 4 not beeping to ground contradicts T-028 and T-031, where all three large cavities read about 0 Ω to the same ground point with the fuse in. Not resolved. Possible causes: poor contact at the ground point or on the terminals this time; or the earlier "0" readings were disturbed. Because every reading to ground was silent in this round, **the ground point itself is unverified for this round.**
  - What cavities 3 and 4 are remains open.
- Evidence files/photos: none.
- Next action: verify the engine-bay ground point in beep mode against two other bare-metal points, then repeat cavities 3 and 4 to ground.

## T-035 — Correction: earlier "0 Ω" readings were "0L." (over range); ground point not confirmed

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Verify the engine-bay ground point (next action from T-034); the reporter also corrects earlier readings.
- Source: N/A
- Vehicle state: key out (as instructed; not restated), battery connected
- Tool and mode: AstroAI AM33D, continuity/beep mode
- Connector state: C175B unplugged; F35 assumed still pulled
- Reference/ground point: engine-bay ground used before; location still not recorded
- Probe points: ground point to two other bare-metal points; ground point to cavities 3 and 4
- Expected result: beep between ground point and other bare metal.
- Actual result:
  - **No beep on any of them**, including ground point to other bare metal.
  - **Correction from the reporter:** the "0 ohms" readings earlier today were probably the display showing **"0L."** (over range, no connection), misread as zero.
- Interpretation:
  - This corrects T-028, T-030 and T-031. Wherever those entries record "0" or "0 Ω" on the ohms range, read **over range (more than 200 Ω)**:
    - T-028/T-031: cavities 2, 3 and 4 showed **no** connection to the ground point. The T-029 conclusion that all three are grounds is **withdrawn**.
    - T-030: F35 to cavity 4 was **no** connection, not 0 Ω. The conclusion there that cavity 4 is a supply pin is **withdrawn**.
    - T-031: F35 to ground was over range, so there is no sign of a short on the supply line.
  - The one numeric reading stands as reported: **F35 test point to cavity 2 = 3.9 to 4 Ω** (T-030, fuse in place). Together with the beeps in T-031/T-033 this confirms cavity 2 is fed from F35.
  - With that correction all of today's readings agree with each other. The contradictions noted in T-030 to T-034 are resolved.
  - **New question:** about 4 Ω is high for a short length of supply wire; a sound wire and fuse would read well under 1 Ω. It may just be contact resistance of a fine probe tip touched lightly on the terminal. If it is real, it matters: at 1 A it would drop about 4 V on the PCM supply, which could make the PCM unstable. Not concluded; needs a careful repeat.
  - The ground point did not beep to other bare metal, so it is not confirmed as a good reference for resistance work today. Earlier voltage readings taken against a ground (T-021, T-022) are not affected: they showed full battery voltage, which a bad reference cannot produce. What cavities 3 and 4 are is still open.
- Evidence files/photos: marked image for the follow-up: `evidence/photos/marked-C175B-face-2-supply.jpg`
- Next action: with F35 out, measure resistance on the 200 Ω range between F35 socket slot B and cavity 2, with firm steady contact.

## T-036 — F35 slot B to cavity 2 is a steady 3.9–4.0 Ω

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Find out whether the 4 Ω of T-030 was contact resistance or real (next action from T-035).
- Source: PDF page 238, printed "2.2L", section 151-2
- Vehicle state: key out (as instructed; not restated), battery connected
- Tool and mode: AstroAI AM33D, Ω 200 range; tips together 00.0 (T-032)
- Connector state: C175B unplugged; F35 pulled (as instructed; not restated)
- Reference/ground point: N/A
- Probe points: F35 socket slot B; harness-side terminal in large cavity 2
- Expected result: under about 1 Ω if this is a direct wire and the earlier value was contact resistance.
- Actual result: **3.9 or 4.0 Ω**, repeated.
- Interpretation:
  - The value is real: it is steady and repeats after re-seating the probes. Contact resistance is normally erratic.
  - It can be read two ways, and **the T-034/T-035 statement that cavity 2 is the supply pin was premature**:
    - (a) Slot B is the PCM side of the fuse, cavity 2 is a supply pin, and the wire or a joint in it has about 4 Ω too much. That would be a fault big enough to disturb the PCM.
    - (b) Slot B is the relay side of the fuse. Per p.238 that side also feeds other engine-control loads (wire CE612). Cavity 2 would then be a PCM output that switches one of those loads, and the 4 Ω is simply that component's own resistance. A large cavity suits a high-current output as well as a supply. Nothing would be wrong.
  - A steady round value of 4.0 Ω looks more like a component than a bad joint, so (b) is at least as likely as (a). Not decided.
  - Deciding test: find what the *other* slot (A) connects to. The PCM side of the fuse must reach its supply cavities at well under 1 Ω. Slot A reached none of the large cavities (T-033), so the supply would be on the medium or small cavities, as p.238 also suggests for two of its three supply pins.
- Evidence files/photos: marked image for the follow-up: `evidence/photos/marked-C175B-face-6-17-18-30.jpg`
- Next action: resistance on the 200 Ω range from slot A, then slot B, to medium cavities 30, 18, 6 and 17.

## T-037 — F35 slots A and B: no connection to medium cavities 30, 18, 6; cavity 17 is empty

- Date/time: 2026-10-05 (exact time not recorded)
- Performed by: Sander
- Goal: Find which F35 socket slot is the PCM side by locating the supply cavities (next action from T-036).
- Source: PDF page 238, printed "2.2L", section 151-2
- Vehicle state: key out (as instructed; not restated), battery connected
- Tool and mode: AstroAI AM33D, Ω 200 range (as instructed; not restated)
- Connector state: C175B unplugged; F35 pulled
- Reference/ground point: N/A
- Probe points: F35 socket slots A and B; harness-side terminals in medium cavities 30, 18, 6, 17
- Expected result: one slot under 1 Ω to one or more medium cavities.
- Actual result:
  - Slot A and slot B to cavity 30: no reading. To 18: no reading. To 6: no reading.
  - **Cavity 17 is empty** (corrects the T-030 list, which had 17 populated).
- Interpretation:
  - None of the medium cavities with a terminal is fed from F35. Medium cavities 17, 29, 42 and 53, where p.238 puts two supply pins and two grounds, are all empty by T-030 and this entry. The p.238 pin numbers clearly do not apply to the numbers moulded on this housing.
  - The only connection found so far between the F35 socket and C175B is slot B to cavity 2 at 3.9–4.0 Ω (T-036). Either that is the supply path, with a fault in it, or the supply pins are small cavities and cavity 2 is a switched output. Still undecided.
  - Quickest way to decide: establish directly which F35 slot is the relay side, from the R17 relay socket. Per p.238 the relay output terminal goes straight to one side of F35.
- Evidence files/photos: none.
- Next action: pull relay R17; DC volts on each socket terminal; then resistance from each dead terminal to F35 slots A and B.

## T-038 — Correction: the middle PCM connector is C175T, not C175B; the wiring diagram was right

- Date/time: 2026-10-05 (evening)
- Performed by: Claude (online research at the reporter's request, then re-check against the repository PDF)
- Goal: The reporter asked for a search for the correct wiring diagram, since the C175B pin numbers from p.238 did not fit the connector measured in T-026 to T-037.
- Source:
  - `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`, PDF pages 238, 239, 240, 244, 245, 294, 298, all printed "2.2L"
  - Bench-programming note for the SID208 in PSA vans (blog.obdii365.com, 2021-10-07, as quoted in search results; the page itself could not be opened): "+12v (pin 5, 28, 39)", "GND (pin 2, 3, 7)", "CAN Hi (10) and Lo (11)"
  - JustAnswer UK, two Transit Custom no-start/U0100 cases (as quoted in search results; pages return 403): the PCM "fails to ground pin 48" so relay R17 "does not provide power to PCM pins 5, 17 and 29"
- Vehicle state: N/A
- Tool and mode: web search; visual read of PDF pages
- Connector state: as left by the reporter at the end of the session; **not recorded** (C175B/C175T, F35 and possibly R17 may still be out)
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result:
  - No better wiring diagram for this van was found online. Pinout material for the SID208 is mostly ECU-tuning bench notes; the two that could be read agree with the repository diagram's C175B numbers (grounds 2, 3, 7; supply on 5; CAN on 10/11; relay control on 48; supply on 5, 17, 29).
  - Comparing the diagram's pin lists with the cavities the reporter found populated on the middle connector (T-030, T-037):
    - **C175T** pins found in the diagram: 2, 3, 6, 8, 11, 13, 14, 16, 18, 21, 22, 26, 27, 28, 30, 33, 34, 37, 47. **All 19 are populated** on the middle connector.
    - **C175B** pins found in the diagram: 2, 3, 5, 7, 8, 10, 11, 17, 27, 28, 29, 41, 42, 48, 52, 53. **Nine of these 16 are empty** on the middle connector (5, 7, 10, 17, 29, 41, 42, 48, 53).
- Interpretation:
  - **The middle connector is C175T.** The T-026 identification as C175B was wrong: it rested on the 53-cavity count, and C175T uses the same 53-cavity housing. This was Claude's error, not a measuring error.
  - **The wiring diagram is not wrong for this van.** The statements in T-027, T-030, T-034 to T-037 that its pin numbers do not match the housing are withdrawn. The reporter's cavity list, taken under poor visibility, matches the diagram's C175T on every pin checked.
  - The steady 3.9–4.0 Ω from F35 "slot B" to cavity 2 (T-036) now has a plain explanation: C175T pin 2 is the fuel vaporizer pump (p.239), which is fed from the PCM relay output through fuse F39. Slot B is therefore the relay side of F35, and the 4 Ω is most likely the pump's own resistance. **No fault is indicated by any reading in T-027 to T-037.** That cavity 3 (oxygen sensor heater per p.239) showed no path to the fuse is not explained; the sensor may not be fitted on this build. Low priority.
  - By elimination **the right-hand connector is C175B** and the left, 48-cavity one is C175E. Neither is directly verified. T-024's first impression (middle connector has thin sensor-coloured wires, unlike C175B) was correct.
  - The online cases describe the same circuit (R17, pin 48, pins 5/17/29) with a different symptom: there the relay never closes. Here it closes and buzzes (T-021 to T-023). They are context, not evidence about this van.
  - Nothing has yet been measured on the real C175B.
- Evidence files/photos: `evidence/photos/marked-pcm-connectors-identified.jpg`
- Next action: confirm that F35, R17 and both unplugged connectors are back in place. Then, key out for at least 2 minutes, unplug the right-hand connector and check it is C175B: 53 cavities, with terminals in large cavities 2, 3 and 5 and medium cavities 17, 29, 42 and 53.

## T-039 — Right-hand PCM connector unplugged: population matches C175B

- Date/time: 2026-10-06 (exact time not recorded)
- Performed by: Sander (visual check and photo), Claude (photo read)
- Goal: Confirm that the right-hand PCM connector is C175B before measuring on it (next action from T-038).
- Source: `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`, PDF page 238, printed "2.2L", section 151-2; PDF page 298, printed "2.2L", section 23-17 (pin 41)
- Vehicle state: not stated; key out for at least 2 minutes was the instruction
- Tool and mode: N/A (visual)
- Connector state: right-hand PCM connector unplugged. **Not reported:** whether F35, R17/R9 and the middle and left connectors are back in place (asked in T-038).
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: 53 cavities; terminals in large cavities 2, 3 and 5 and medium cavities 17, 29, 42 and 53.
- Actual result:
  - Reported: **2, 3, 5, 17, 29, 41 and 53 all hold a metal terminal.** Cavity 42 was not mentioned.
  - From the photo (Claude's reading): black outer housing with a red face, moulded part number 1563196-1, the same 53-cavity housing as the middle connector. Large cavities 1 and 4 empty; 2, 3 and 5 with terminals. Right-hand medium column 53, 41, 29, 17 all with terminals. Left-hand medium column: **42 shows a terminal**; 30, 18 and 6 look empty. Small cavities not judged.
  - Wire colours on the back of the connector not reported.
- Interpretation:
  - **The right-hand connector is C175B.** All seven cavities that p.238 uses for supply and ground on the large and medium positions hold a terminal, including large cavity 5 and medium 17, 29 and 53, which are empty on the middle connector (C175T). Cavity 41 holding a terminal also fits: p.298 puts SMCS on C175B pin 41.
  - Cavity 42 rests on the photo only. The 2-to-42 reading in the next test settles it.
  - The T-038 identification is now confirmed by direct observation rather than by elimination.
  - Nothing electrical has been measured on C175B yet.
- Evidence files/photos: `evidence/photos/2026-10-06-pcm-right-connector-face.png`; marked image for the follow-up: `evidence/photos/marked-C175B-right-groups-ground-supply.jpg`
- Next action: with C175B unplugged and the key out, resistance on the 200 Ω range between harness-side cavities: 2 to 3, 2 to 42, 2 to 53 (ground group, splice S101), 5 to 17, 5 to 29 (supply group, splice S103), then 2 to 5. This needs no ground reference, which is still unverified since T-035.

## T-040 — C175B harness side: ground group and supply group each joined, no short between them

- Date/time: 2026-10-06 (exact time not recorded)
- Performed by: Sander
- Goal: Check that the ground wires and the supply wires of C175B each still join at their splice, without relying on a ground reference (next action from T-039).
- Source: `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`, PDF page 238, printed "2.2L", section 151-2
- Vehicle state: key out (as instructed; not restated), battery connected
- Tool and mode: AstroAI AM33D, Ω 200 range (as instructed; not restated)
- Connector state: C175B unplugged. State of F35, R17/R9 and the other two PCM connectors still not reported.
- Reference/ground point: N/A (cavity to cavity)
- Probe points: harness-side terminals of C175B from the mating face, as marked in `evidence/photos/marked-C175B-right-groups-ground-supply.jpg`
- Expected result: under 1 Ω within the ground group (2, 3, 42, 53) and within the supply group (5, 17, 29); clearly not near zero between 2 and 5.
- Actual result (digits as reported):
  - 2 to 3: **0.00**
  - 2 to 42: **0.02**
  - 2 to 53: **0.00**
  - 5 to 17: **0.02**
  - 5 to 29: **0.00**
  - 2 to 5: **0L.**
- Interpretation:
  - Ground wires on 2, 3, 42 and 53 are joined to each other at well under 1 Ω, as p.238 draws them (GD120, splice S101). Cavity 42 does hold a terminal, which settles the open point from T-039.
  - Supply wires on 5, 17 and 29 are joined to each other at well under 1 Ω, as p.238 draws them (CBB35, splice S103).
  - No connection between the supply group and the ground group with the PCM unplugged and the relay open, so there is no short on the PCM supply line.
  - This is the first set of readings on the real C175B, and every one matches the diagram. It further confirms the T-039 identification.
  - Not shown by this test: that the ground group actually reaches the body and battery negative (G105), that the supply group reaches fuse F35, and how either behaves under load. Ground pin 7 (G104) is not covered either.
- Evidence files/photos: marked image for the follow-up: `evidence/photos/marked-C175B-right-7-10-11.jpg`
- Next action: on the 200 Ω range, cavity 2 to cavity 7 (second ground, also a check of the small-cavity numbering), then cavity 10 to cavity 11 (HS CAN pair on the harness side, p.298). Small-cavity numbers are counted along the row from medium cavity 6 and are not moulded on the face; treat them as unconfirmed until the 2-to-7 reading and the wire colours agree.

## T-041 — C175B harness side: 2 to 7 has continuity; 10 to 11 (HS CAN pair) reads 0L

- Date/time: 2026-10-06 (exact time not recorded)
- Performed by: Sander (readings), Claude (diagram read)
- Goal: Check ground pin 7 and the small-cavity numbering, then see whether the CAN pair at the PCM plug reaches the rest of the network (next action from T-040).
- Source: `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`, PDF page 238 (section 151-2) for pin 7; PDF page 298 (section 23-17) for pins 10/11; **PDF page 218, printed "2.2L", Module Communications Network (the sheet p.298 refers to as 14-5)** for the route of the CAN pair, found by OCR search for wire name VDB04
- Vehicle state: key out (as instructed; not restated), battery connected. How long the key had been out is not recorded.
- Tool and mode: AstroAI AM33D, Ω 200 range (as instructed; not restated)
- Connector state: C175B unplugged. State of F35, R17/R9 and the other two PCM connectors still not reported.
- Reference/ground point: N/A (cavity to cavity)
- Probe points: harness-side terminals of C175B from the mating face, as marked in `evidence/photos/marked-C175B-right-7-10-11.jpg`. Small-cavity numbers were counted along the row from medium cavity 6 by Claude; they are not moulded on the face.
- Expected result: 2 to 7 under about 1 Ω. 10 to 11: about 120 Ω if the pair reaches the network and one end resistor.
- Actual result:
  - 2 to 7: **varies between 0.04 and 1.00** (as reported).
  - 10 to 11: **0L** (over range, more than 200 Ω).
  - Wire colours behind 7, 10 and 11 not reported.
- Interpretation:
  - 2 to 7: there is a connection, so the cavity counted as 7 is a ground. That supports the counting method. The variation is most likely probe contact on a small terminal; a loose or corroded joint in the pin-7 ground path (GD121, S118, G104) or between G104 and G105 is not excluded. To repeat with steadier contact later.
  - 10 to 11 reading 0L means no end resistor is seen from the PCM plug. **If** the two cavities probed really are 10 and 11 and both tips touched metal, the CAN pair is open somewhere between this plug and the rest of the network. That would explain the PCM being awake but silent (T-021 to T-023), the 120 Ω at the diagnostic socket (T-006) if the PCM holds the second end resistor, and U0100 in the other modules (T-007). **Not yet concluded:** the cavity identity rests on counting, small terminals are easy to miss, and only the 200 Ω range was used.
  - New from p.218: the PCM's CAN wires (C175B 10 = VDB04 white-blue, 11 = VDB05 white, twisted) run to splices **S107/S108**. From those splices one leg goes through **C1010 pins 3/4** to the **ABS module (C135 pins 26/14)**, and the other goes through **C139 pins 47/48** to splices S297/S296, where the restraints module and the rest of the network join. So the PCM and the ABS module share one branch behind C139.
  - That fits the scan in T-007: PCM does not answer, **the ABS module is not in the list of responding modules at all**, and PAM, HCM, BCMii and IPC store U0121 (lost communication with ABS, generic definition, still unconfirmed in FORScan's own text). Also H-05 (ABS reported not working) and T-008 (traction-control icon). Two modules missing that share one branch points at that branch (C139 pins 47/48 or the wire either side of it) rather than at the PCM itself. Hypothesis, not a finding.
  - Against a fully unmated C139: the same connector carries the relay feeds on pins 6 and 24 and the wake signal on pin 23 (p.238), and those work (T-021). So if C139 is involved it would be individual terminals, not the whole connector.
  - The restraints module is not in the T-007 list either; it sits on the network side of C139 per p.218. Unexplained; FORScan may simply not list it in that view.
  - Also noted while searching: C175B pin 39 is the ignition feed from BJB fuse F7 (CBB07, green-blue; PDF p.104) and pin 47 is the START signal from the ignition switch through C210 pin 51 and C139 pin 16 (CDC35, blue-white; PDF p.101/102).
  - Where C139 sits on the van is not known yet.
- Evidence files/photos: none new.
- Next action: confirm the cavity identity from the wire side (a twisted white-blue and white pair must enter the two cavities probed), then repeat 10 to 11 on the 20 kΩ range with firm contact.

## T-042 — C175B cavities 10 to 11 read about 19 kΩ: a module, but no end resistor and no network

- Date/time: 2026-10-06 (exact time not recorded)
- Performed by: Sander (reading and photos), Claude (diagram read)
- Goal: Confirm or refute the 0L reading of T-041 with better contact and a higher range.
- Source: `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`, all printed "2.2L", Module Communications Network: PDF page 214 (DLC, sheet 14-1), page 216 (sheet 14-3), page 217 (sheet 14-4), page 218 (sheet 14-5). Sheet numbers are inferred from the cross-references between the pages.
- Vehicle state: key out (as instructed; not restated), battery connected
- Tool and mode: AstroAI AM33D, kΩ range (display shows kΩ with two decimals, so the 20 kΩ range). Thin pin probes with banana sockets pushed into the cavities from the mating face, because the meter's own tips do not fit.
- Connector state: C175B unplugged. State of F35, R17/R9 and the other two PCM connectors still not reported.
- Reference/ground point: N/A (cavity to cavity)
- Probe points: the two cavities marked 10 and 11 in `evidence/photos/marked-C175B-right-7-10-11.jpg`. The reporter's photo shows the pins in exactly those two positions: the last small cavity of the bottom-left block and the first of the bottom-middle block.
- Expected result: about 0.12 kΩ if the pair reaches the network and one end resistor; over range if the pair is open and nothing else hangs on it.
- Actual result:
  - **18.85 to just over 19 kΩ**; the photo shows 18.97 kΩ.
  - The wires at the back of the plug cannot be seen; the connector cover blocks the view. Cavity identity by wire colour is therefore not confirmed.
- Interpretation:
  - T-041's "0L" on the 200 Ω range and this reading agree: the true value is about 19 kΩ, far above 200 Ω.
  - About 19 kΩ is not an end resistor (120 Ω) and not an open wire. It is the order of size of the input of one or two CAN transceivers. So these two cavities do carry a CAN pair with at least one module on it, which also supports the cavity counting. Per p.218 the modules that share this stretch with the PCM are the ABS module (through C1010) and, on the far side of C139, the restraints module.
  - What is missing is everything else: the diagnostic socket sees 120 Ω (T-006, H-06) and eight modules answer there (T-007). If the PCM plug were on the same copper, it would read 120 Ω or less. **The stretch of HS CAN that serves the PCM is cut off from the part of the network that the diagnostic socket is on.** This is now supported by two independent observations (resistance here, module list in T-007) but the break itself has not been located or measured directly.
  - It also means the PCM most likely holds the second end resistor: the socket sees one (120 Ω) and this stretch has none without the PCM. Inferred.
  - Resistance was measured with the battery connected and other modules possibly not asleep, so the exact value is not reliable. The conclusion only needs "kilo-ohms, not about 120 Ω".
  - Full route from the diagnostic socket to the PCM, per the four sheets: DLC C251 pins 6/14 → S211/S210 (BCM joins) → S217/S218 → S220/S221 (steering column module joins) → C263 pins 2/8 → S202/S203 (SYNC module joins) → C264 pins 2/8 → C210 pins 68/67 → **C311 pins 44/45** → S922/S921 (parking aid module joins) → C900 pins 4/10 → S904/S905 → C900 pins 12/6 → **C311 pins 42/43** → (C192 on early production) → S297/S296 (restraints module joins) → **C139 pins 47/48** → S107/S108 (PCM joins; ABS module through C1010 pins 3/4).
  - Modules that answered in T-007 (BCM, steering column/SASM, SYNC/APIM, parking aid/PAM and others) all sit before S922/S921 on this route. Modules that did not appear (restraints, PCM, ABS) all sit after it. **That places the break between S922/S921 and S297/S296: C900 pins 4/10 or 12/6, the S904/S905 stretch, C311 pins 42/43, or C192 if fitted.** Inferred from the scan list; FORScan may omit a module for other reasons, so this is a working hypothesis.
  - The bus passes through C311 twice. The diagram has no connector location views and the BEMM does not mention C311 or C900, so where they sit on the van is unknown. The fault first appeared right after work under the driver's seat (T-005), where several connectors were unplugged (T-006). Whether C311 or C900 is one of those is not known.
  - This shifts the leading hypothesis away from the PCM and its own supply and ground, all of which have so far measured as drawn (T-021, T-040).
- Evidence files/photos: `evidence/photos/2026-10-06-c175b-probes-in-10-11.png`, `evidence/photos/2026-10-06-c175b-10-11-meter-18.97k.png`
- Next action: photograph every connector that was unplugged around the driver's seat and the battery area, without unplugging anything, and report how many there are, their colours and roughly how many pins each has. Airbag connectors (usually yellow) are not to be unplugged or probed.

## T-043 — Research: what C311 and C900 are, and where they probably sit

- Date/time: 2026-10-06
- Performed by: Claude (online search at the reporter's request, then the repository's own manuals)
- Goal: Find where connectors C311 and C900 are on the van (suspect stretch from T-042).
- Source:
  - Web search (several queries on C311/C900/Transit Custom/HS CAN): **nothing found that names C311 or C900 or gives their location.** Forum threads on fordtransit.org describe water running down the A-pillar on Transit Customs and corroding connectors and the BCM; general context only.
  - `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf`, all printed "2.2L": PDF page 112 (fuse F34, rear wipers), page 125 (interior lamps, early production), page 521 (sliding door ajar switches), page 609 (lane departure warning), page 217 (network sheet 14-4)
  - `benl_montagehandleiding-Transit-Custom.pdf` (BEMM), printed pages 139, 140 and the ground point table on printed page 165
- Vehicle state: N/A
- Tool and mode: N/A
- Connector state: N/A
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result:
  - **C311** carries, besides the HS CAN pair on 44/45 and 42/43: the right-hand rear door wiper feed (pin 24, p.112), the right-hand sliding door ajar switch (pin 8, p.521), the luggage compartment and interior lamp feed (pin 26, p.125), the lane departure camera feed (pin 28, p.609) and a ground to G306 (pin 22, p.609). The same pages show a **C300** carrying the left-hand equivalents (left rear door wiper pin 24, left sliding door ajar switch pin 6).
  - **C900** carries the feed to the front interior lamp and the vanity mirror lamps (pin 11, p.125) and, per p.217, the HS CAN pair out (pins 4/10) and back (pins 12/6). The lane departure camera hangs off the same harness through C913/C919 (p.609).
  - The BEMM names a main harness (14401), a left body harness (14405) and a right body harness (14A005), joined to the main harness by one connector each. Its ground table puts ground points of the 14A005 harness at the A-pillar and at the D-pillar. It gives no connector numbers and no picture of these connectors.
  - Neither manual has a connector location view.
- Interpretation (all inferred, none confirmed on the van):
  - C311 is the connector between the main harness and the **right-hand body harness**; C300 is its left-hand twin. Because the right-hand body harness starts at the A-pillar, C311 is most likely low down at the **right-hand A-pillar** (behind the lower trim / kick panel on the passenger side of a left-hand-drive van), not under the driver's seat.
  - C900 joins the body harness to the **roof (headliner) harness**, so it should be high up, probably at the top of a pillar on the right-hand side.
  - The HS CAN bus goes up into the roof harness through C900 and comes back down through it. On p.217 the stretch between the two C900 passes (S904/S905) is drawn inside the "lane departure warning" option box. Whether this van has the camera, and how the loop is closed when it does not, is not known.
  - This weakens the under-seat suggestion made in T-042: nothing found so far places C311 or C900 near the driver's seat.
  - C311 and C900 also carry lamp and door-switch circuits. If the front interior lamp, the load-area lamps and the right-hand sliding door warning all work, both connectors are at least plugged in, and the fault would be limited to the CAN terminals or wires.
- Evidence files/photos: none.
- Next action: no-tools check of the circuits that share C311 and C900: front interior lamp, load-area lamps, right sliding door open warning, airbag warning lamp at key-on; and report whether a camera sits behind the rear-view mirror.

## T-044 — C311 location: reporter finds "seats" online; A-pillar inference of T-043 downgraded

- Date/time: 2026-10-06
- Performed by: Sander (online find, source not recorded), Claude (re-check of the repository diagram's OCR text)
- Goal: Reconcile the reporter's find that C311 is "in seats" with T-043.
- Source: OCR text of `Ford-Transit-Custom-1-2012-2020-–-Wiring-Diagrams.pdf` (200dpi, may be incomplete); PDF pages 18, 110, 116, 553, 555, 556 for seat circuits
- Vehicle state: N/A
- Tool and mode: N/A
- Connector state: N/A
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result:
  - The reporter found C311 described online as a seat connector. Which vehicle and which page is not recorded.
  - In this van's diagram the seat circuits (heated seats and others) use C334, C335, C341A–F, C363, C369, C3501 and C3660C. C311 does not appear on those pages. C311 appears on p.112, 125, 217, 521 and 609 with the circuits listed in T-043, and needs at least 45 cavities.
  - Other connectors numbered 3xx in this diagram: C310A/C310B (restraints control module), C300, C340.
- Interpretation:
  - Ford connector numbers are assigned per model. On other Ford models C311 is a seat connector, which is probably what the online find refers to. In this van's diagram C311 is not a seat connector.
  - But the 3xx numbers in this diagram belong to parts in the cabin floor area (seat connectors, restraints module). So C311 may sit on the cabin floor near the front seats rather than at the A-pillar. **The A-pillar location in T-043 was an inference from a BEMM ground table and is no better supported than a floor location.** Both stay open until the connector is seen on the van.
  - What to look for is the same either way: a large connector (45 cavities or more) with a twisted white-blue and white pair, not one of the small seat plugs.
- Evidence files/photos: none.
- Next action: unchanged from T-043 (lamp, door warning and airbag lamp check), plus photos of every connector around the driver's seat base and floor as asked in T-042.

## T-045 — Outside source for C311 on the sister model: inline connector under the passenger-side dash, known for water ingress

- Date/time: 2026-10-06
- Performed by: Sander (found the thread), Claude (read it)
- Goal: Settle where C311 sits (open since T-043/T-044).
- Source: motorhomefun.co.uk forum thread "Help headlight's keep turning on" (thread 270715), post #8 of 2022-09-18, with a photographed printout headed "Transit 2019 MY – Camper conversion / High Roof Tipper conversion". **This is about the large Transit (Mk8), not the Transit Custom.**
- Vehicle state: N/A
- Tool and mode: N/A
- Connector state: N/A
- Reference/ground point: N/A
- Probe points: N/A
- Expected result: N/A
- Actual result:
  - The printout says: "Check connector C311 on the right side of the vehicle, beneath the cup holder on passenger side of the dash", "Connector C311 is prone to water ingress via the cup holder or the drain running from the screen", "Generally they can be resolved by removing the connectors, cleaning and applying some contact grease".
  - Its location drawing shows C311 at the foot of the A-pillar / side of the dash, next to C340, C210 and C3660C, with the restraints module C310A/C310B on the floor nearby. It lists C311 as an inline connector, black, male half on harness 14401, female half on a body harness (number not readable in the photo), with a large multi-row face.
  - The forum post quotes: "the source of the short is the C311 connector which is located on the passenger side of the van in the dash under the cup holder", "This happens from condensation from the windscreen".
- Interpretation:
  - The connector names on that drawing (C311, C340, C210, C3660C, C310A/B, harness 14401) all occur in this van's diagram too, so the two models appear to share the naming. That makes it likely, not certain, that the Transit Custom's C311 is in the same place: **low on the right-hand side of the dash, at the A-pillar, which is the passenger side on this left-hand-drive van.**
  - This agrees with the T-043 inference (main harness to right-hand body harness, at the A-pillar) and makes the floor-near-the-seats alternative of T-044 less likely.
  - A connector known for water ingress and corrosion, carrying the HS CAN pair twice (pins 42–45), fits the suspect stretch of T-042 well. Still a hypothesis: nothing has been seen or measured at C311 on this van, and the source covers another model and another symptom (lights staying on).
  - The "seats" find reported in T-044 is not explained by this source.
- Evidence files/photos: `references/connectors/transit-2019MY-C311-location-printout.png` (copy of the forum attachment)
- Next action: find C311 behind the lower trim on the right-hand side of the dash / right A-pillar foot and photograph it in place, without unplugging. Look for water marks, green or white deposits, and damp carpet.
