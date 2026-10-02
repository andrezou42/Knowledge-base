# AltMill 4×8 — Commissioning and Spoilboard Surfacing

_Last reviewed: 2026-10-01_

This page is the practical first-use sequence for our assembled AltMill 4×8.

It supplements the dated [2026-10-01 setup log](../../Logs/2026-10-01-AltMill-Setup.md), which records our actual spoilboard geometry and screw pattern.

## Recommended commissioning order

### 1. Mechanical final checks

Before a cutting test:

- Confirm all table-frame fasteners are tight.
- Confirm leveling-foot clamp nuts are tight.
- Confirm the table is level at the corners.
- Confirm X/Z ballscrew couplers are fully tight on both motor and screw sides.
- Confirm white lithium grease is present on the Y rack and pinion.
- Jog across the center table joint and listen/feel for a clunk or binding.
- Confirm nothing can enter the rack/pinion or linear-rail paths.

Sienci's 4×8-specific final check page:
https://resources.sienci.com/view/am4x8-final-checks/

## 2. Electrical and sensor checks

- Controller and VFD should be on the correct dedicated circuits.
- Verify X/Y motor DIP switches: **OFF, OFF, OFF, ON, ON**.
- Verify Z motor DIP switches: **OFF, OFF, ON, ON, ON**.
- Check motor wires for loose spring-terminal connections.
- Verify each inductive sensor responds to metal and its indicator changes.
- Confirm the machine can jog smoothly in all axes.
- Confirm the spindle can start and reach commanded speed without alarms.
- Confirm homing completes normally.

If homing or motion is wrong, do not proceed to surfacing; use the troubleshooting page first.

## 3. Software baseline

For the ATC system:
- use **gSender 1.6.2 or newer**;
- current stable version reviewed on 2026-10-01 is **1.6.4**;
- controller firmware required by the current Sienci ATC instructions is **grblHAL 20260525**.

Details: [Software-Firmware-and-CAM.md](./Software-Firmware-and-CAM.md)

## 4. ATC validation before a real multi-tool job

Complete the ATC setup wizard and confirm:
- rack sensor is active,
- TLS input works,
- pressure indicator is correct,
- T1 can be picked up and returned cleanly,
- T2 can be picked up and returned cleanly,
- each loaded tool automatically probes on the TLS,
- the tool goes back to the correct rack position.

Do this at slow observation speed and with a hand ready for the E-stop. A rack collision is not an acceptable "test."

See [ATC-Spindle-and-Pneumatics.md](./ATC-Spindle-and-Pneumatics.md).

# Spoilboard construction — our machine

Our current arrangement:
- lower permanent layer: 3/4 in plywood
- replaceable top spoilboard: 3/4 in MDF
- segmented top MDF
- recessed permanent fasteners below the surfacing plane

This differs from Sienci's default recommendation of MDF table surface + MDF sacrificial wasteboard, but the functional principle is the same: the top sacrificial surface must be securely mounted and then machined parallel to the machine's XY plane.

Our exact screw pattern and panel dimensions are in the setup log.

## Why surfacing matters

Surfacing does not "level the table to gravity." It creates a spoilboard surface parallel to the machine's XY motion.

A correctly surfaced board improves:
- consistent shallow engraving,
- consistent pocket depths,
- through-cut reliability,
- Z-zero repeatability,
- vacuum/glue/tape contact where applicable.

If a wide surfacing bit leaves repeating ridges, suspect **spindle tram** before assuming the MDF is bad.

# Sienci's current 4×8 surfacing procedure

Official page:
https://resources.sienci.com/view/am4x8-surfacing-wasteboard/

Sienci's current guidance for the 4×8 includes:

- establish the actual reachable surfacing area by jogging with the surfacing bit installed;
- reference area is about **49 × 103 in (1245 × 2616 mm)**, depending on cutter diameter and configuration;
- keep individual cut depth at **1 mm / 0.04 in or less**;
- typical total removal starts around **1 mm / 0.04 in**, increasing only if needed for warp/imperfections;
- around **20,000 RPM** works for MDF/wood;
- approximately **8,000 mm/min** is a suitable 4×8 MDF surfacing feed, with slower feed potentially improving finish;
- remove the dust shoe if it risks collision near the travel limits;
- continue to use dust extraction and a respirator because MDF surfacing produces very fine dust.

### About Sienci's stepover wording

The current page says to use about **40% overlap**. Treat that as the key target. The same paragraph uses "stepover" and "overlap" somewhat inconsistently, so do not interpret the wording as permission for an extreme step width. For the first surface, prioritize a conservative overlap and inspect the finish.

## Critical limits warning

Sienci's surfacing guide currently instructs users to disable hard and soft limits because otherwise the surfacing routine can produce Alarm 2 near the machine edge. It also explicitly instructs re-enabling those limits after surfacing and power-cycling the controller.

For our machine:

1. Home first.
2. Verify by jogging that the planned surfacing extents are physically safe.
3. Keep a conservative margin around the rack, TLS, tool rack and dust-shoe geometry.
4. Disable limits only for the surfacing operation if necessary.
5. Stay with the machine throughout the job.
6. Re-enable hard/soft limits immediately afterward.
7. Power-cycle as required so the settings take effect.

Do not leave the machine in a "limits disabled" state after surfacing.

## First surfacing pass for our 1 in BINSTAK bit

The owned cutter is a 1 in diameter, 1/4 in shank surfacing/slab-flattening bit.

Practical first-pass approach:
- physically identify the exact BINSTAK cutter/SKU if possible and verify its maximum permitted RPM; **the cutter manufacturer's RPM limit overrides Sienci's generic 20,000 RPM surfacing example**;
- verify cutter is undamaged and securely tightened;
- use the shallowest pass that will reveal high/low areas;
- only if the cutter is rated appropriately, use Sienci's 20,000 RPM / ~8,000 mm/min guidance as an upper starting reference, not a requirement;
- if uncertain about bit balance or cut quality, start slower and observe;
- do not take a deep corrective pass immediately;
- inspect for tram ridges after the first complete pass.

The machine's 25,000 mm/min Y maximum is **not** a reasonable spoilboard-surfacing feed simply because the axis can move that fast.

## What to inspect after the first pass

- **Unswept islands:** spoilboard/table is not yet fully cleaned up; another shallow pass may be needed.
- **Parallel ridges between passes:** likely spindle tram error.
- **Localized gouge or step:** possible loose spoilboard, Z issue, cutter issue or sudden deflection.
- **Clunk crossing the center of the machine:** table-joint/rack/rail alignment problem; stop and diagnose.
- **Chatter:** reduce aggressiveness and check tool stick-out, tightness, spindle/tool condition and machine mechanics.
