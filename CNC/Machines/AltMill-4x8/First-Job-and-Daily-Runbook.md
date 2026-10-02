# AltMill 4×8 — First Job and Daily Operating Runbook

_Last reviewed: 2026-10-01_

This page is the short operational sequence to use once the machine has passed commissioning.

It is intentionally separate from the dated setup log and the deeper troubleshooting pages.

## Before powering up

- Clear the table, Y racks, linear rails, ATC rack and TLS area.
- Confirm the workpiece and clamps/screws cannot enter the cutter path.
- Confirm the correct ISO20 holders/tools are physically in the intended rack slots.
- Confirm the dust hose is supported and cannot push the ATC dust shoe into the rack.
- Verify the E-stop is accessible.

## Power and connect

1. Turn on the shop air supply.
2. Confirm the Sienci regulator is supplying the required ATC pressure.
3. Turn on the SLB-EXT/controller.
4. Turn on the VFD/spindle system.
5. Open gSender and connect using **grblHAL**.
6. Verify the expected **AltMill 4×8** profile/configuration is active.
7. If anything about the machine configuration looks different from the last known-good state, stop and diagnose before jogging.

## Home first

**Home the machine before using the ATC.**

The rack and TLS workflow depend on machine coordinates. Homing also re-establishes the dual-Y square relationship.

If homing does not complete cleanly, do not continue to zeroing or a job.

Official ATC final-check guidance:
https://resources.sienci.com/view/atc-final-checks/

## Tool-rack check

Our current permanent tool assignments begin with:
- T1 — 1/4 in SpeTool SPE-X upcut
- T2 — 1/8 in SpeTool SPE-X O-flute

Before a multi-tool file:
- compare the CAM tool numbers with the physical rack;
- remember Sienci numbers a rack from **left to right**, with the left-most slot as T1;
- inspect the gSender Tool Timeline;
- use software remapping only deliberately and make the remap obvious to the operator.

The ATC's default workflow probes each tool on the TLS after loading. Work zeros are retained; do **not** re-zero after every automatic tool change.

Official overview:
https://resources.sienci.com/view/atc-overview/

## Establish the work zero

The CAM origin and physical zero must match.

For our normal flat-table work:
1. Decide the CAM origin before exporting.
2. Select the intended workspace, normally **G54**.
3. Load a suitable tool.
4. Set X/Y/Z using AutoZero or a deliberate manual method.
5. Move the touch plate and magnet completely out of the cutting area before the job.

### AutoZero notes

Current Sienci AutoZero setup in gSender:
- Config → Probe → Touch plate type = **AutoZero**
- **Probe** input inverted ON
- leave the **Toolsetter** inversion unchanged unless the machine setup specifically requires otherwise

For X/Y probing the AutoZero block normally references the bottom-left corner of rectangular stock. For Z-only work it can be flipped and placed on the material surface.

Official AutoZero instructions:
https://resources.sienci.com/view/addons-autozero/

## Before pressing Start

Use this condensed gate:

- [ ] Machine homed successfully
- [ ] Correct g-code file
- [ ] Correct workspace (usually G54)
- [ ] CAM origin = physical zero
- [ ] Stock thickness verified
- [ ] Stock held flat and securely
- [ ] Clamps/screws clear of toolpaths
- [ ] Correct T numbers and rack tools
- [ ] Feed, plunge, RPM and cut depths reviewed
- [ ] Visualizer / bounding box makes sense
- [ ] Safe Z clearance makes sense
- [ ] Tool rack / TLS keep-out area is clear
- [ ] Dust shoe and hose clear through tool changes
- [ ] Dust collection ON
- [ ] Air pressure normal
- [ ] VFD/spindle ready
- [ ] Operator remains at machine

Sienci's general checklist:
https://resources.sienci.com/view/cnc-running-jobs/

## First real ATC job

For the first multi-tool job, use a small, inexpensive workpiece and a simple operation sequence.

The purpose is to validate:
- tool numbers match physical rack positions;
- the Sienci ATC postprocessor generated the expected tool changes;
- pickup and return are smooth;
- each tool touches the TLS cleanly;
- spindle resumes correctly;
- the machine returns to the expected XY position;
- work zero is preserved across tools.

Watch the **first tool change closely from a safe position**. Sienci's own first-project guide uses the same approach.

Official first-project guide:
https://resources.sienci.com/view/atc-first-project/

## During the job

Stop if there is:
- a sudden change in mechanical sound;
- repeated clunk at the middle Y joint;
- unexpected rack/dust-shoe contact;
- wrong tool pickup;
- tool holder not seating cleanly;
- abnormal air loss;
- motor fault or VFD alarm;
- unexpected move toward rack, TLS, clamp or stock;
- smoke, overheating or electrical smell.

Do not leave the CNC cutting unattended.

## After the job

- Wait until spindle and motion are fully stopped.
- Remove chips/dust from rack, rails and TLS area.
- Inspect the bit and holder if the cut sounded abnormal.
- Record a new problem or non-obvious lesson in a dated log rather than relying on memory.
- If a collision, stall or E-stop occurred, re-home and re-validate the affected subsystem before the next job.

## First production milestones

Before treating the machine as production-ready, verify all of the following at least once:

1. Smooth full-axis jogging, including across the Y center joint.
2. Reliable homing multiple times.
3. Spoilboard surfaced with no unexplained ridges or steps.
4. XY square checked with a known-square test.
5. Spindle tram acceptable for the intended work.
6. T1 → T2 → T1 ATC cycle repeated cleanly.
7. TLS gives consistent tool-length behavior.
8. Simple single-tool cut completes correctly.
9. Small multi-tool ATC job completes correctly.
10. Full-sheet bounding/travel test performed before the first valuable 4×8 sheet.
