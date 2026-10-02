# AltMill 4×8 — Troubleshooting and Community Notes

_Last reviewed: 2026-10-01_

This page separates **confirmed Sienci troubleshooting** from **community observations**.

Primary official troubleshooting source:
https://sienci.zendesk.com/hc/en-us/articles/47762168514580-AltMill-4x8-Troubleshooting

## Fast symptom table

| Symptom | First things to check |
|---|---|
| Clunk/roughness crossing middle Y joint | Rail/rack joint alignment; left/right matched sections; debris at joint |
| Rack/pinion noise | Drive tension screw, pivot screw, pinion lubrication |
| Axis will not move | Motor power LED, motor alarm, wiring, machine profile / motor settings |
| Wrong direction/speed/distance | AltMill 4×8 profile, motor DIP switches, couplers, firmware settings |
| Alarm 10 / 15 while homing | Sensor position, Y1/Y2 sensor/motor connections, mechanical resistance |
| Motor alarm + Alarm 10 | Binding/mechanical resistance or interrupted closed-loop feedback |
| Alarm 14 / spindle not responding | VFD/spindle/controller communications |
| Alarm 2 travel exceeded | Job/origin outside machine bounds; not homed; soft-limit conflict |
| Error 33 | Re-export with GRBL millimeter post |
| ATC "keep-out" error | Machine is in protected rack area; move away appropriately |
| ATC loads wrong tool | Tool numbers / rack slots / remapping |
| ATC rack find fails | Re-center sensor 1–2 mm above rack stud; LED alone is not enough |
| Constant ATC air hiss | Confirm ATC software configuration completed; inspect pneumatic path |
| Surface has parallel ridges | Check spindle tram |
| Surfacing leaves untouched islands | More shallow surfacing required or spoilboard/table warp |

# 4×8-specific mechanical issues

## 1. Middle table joint

This is the single most machine-specific mechanical risk on the 4×8.

Sienci warns that rack and linear-rail alignment at the joint is critical. If the machine:
- clicks,
- thumps,
- hesitates,
- changes pitch,
- or creates a motor alarm

at the same Y position near the table joint, stop treating it as a generic feeds/speeds problem.

Check:
- joint cleanliness,
- rail alignment,
- rack alignment,
- whether the correct left/right matched Y sections were used,
- table level/height at the joint.

Official assembly:
https://resources.sienci.com/view/am4x8-joining-the-tables/

## 2. Rack/pinion noise

Sienci's support article points to:
- drive tension screw not fully set,
- loose pivot screw,
- inadequate pinion grease.

Because our Y axis can move much faster than typical hobby-CNC screw drives, unusual rack noise should be investigated early rather than ignored.

# Homing and closed-loop alarms

The 4×8 uses dual Y motors/sensors.

For Alarm 10/15 during homing:
- identify which axis triggers it;
- verify Y1 motor cable is paired with Y1 sensor/controller ports;
- verify Y2 is paired with Y2;
- check inductive sensor adjustment;
- make sure bump stops/flags are correctly installed;
- check for physical resistance.

If a motor alarm accompanies Alarm 10, Sienci notes this can mean:
- excess mechanical resistance, or
- loss/interruption of closed-loop feedback.

Power-cycle, move away from bump stops/sensors, and re-test only after removing the likely cause.

# Travel / soft-limit errors

Alarm 2 usually means the commanded path exceeds the configured machine bounds.

Before disabling any protection:
1. Home.
2. Verify the CAM origin.
3. Verify the work zero.
4. Inspect the bounding box.
5. Confirm the project fits the **actual joinery + ATC** travel.

For normal jobs, changing/turning off limits should not be the first solution.

The special exception is Sienci's own 4×8 spoilboard-surfacing procedure, which currently instructs disabling hard/soft limits for that controlled edge-reaching routine and re-enabling them immediately afterward.

# Error 33 and inch G-code

Sienci identifies inch-post rounding as a source of Error 33 because two lines may round to duplicate/invalid motion data.

Preferred fix:
- export using **grbl mm**.

Do not try to "repair" a large generated file by hand unless the exact cause is known.

# ATC troubleshooting highlights

Official ATC final checks:
https://resources.sienci.com/view/atc-final-checks/

## Wrong tool
- confirm CAM T number,
- confirm physical rack slot,
- confirm tool remapping if enabled.

## Interrupted tool change
If the E-stop was used during a change:
1. controller off/on,
2. reconnect,
3. cycle/release E-stop,
4. unlock machine,
5. home,
6. retry only after checking physical alignment.

## Keep-out error
The ATC software protects the rack area. A keep-out error can be normal if trying to jog where the rack is located.

## Rack crash caused by reset options
Sienci documents a gSender **1.6.0 / 1.6.1** bug where ATC option settings could reset and the machine could crash into the rack. The official fix is **gSender 1.6.2 or newer**.

Our default as of this review: **1.6.4 stable**.

# Community notes

Community reports are less mature for the 4×8 than for older AltMills because the 4×8 only entered broad owner use in 2026. Use these reports to identify things to inspect, not as authoritative configuration values.

## Hardware revision differences

A May 2026 Sienci forum discussion with a Sienci ATC engineer notes that multiple Z-axis gantry plate variants exist across the AltMill family and that the 4×8 plate is different from older/smaller-machine plates.

Practical lesson:
- if a photo/video for a 2×4 or 4×4 shows different ATC mounting holes, do not assume our 4×8 is missing hardware;
- use the 4×8/ATC-specific instructions or ask Sienci support when the physical plate does not match documentation.

Community thread:
https://forum.sienci.com/t/atc-spindle-mounting-plate/26378

## Air-compressor discussions

Owners have discussed whether small compressors with less than the published 3 CFM rating can be supplemented with tanks because tool-change air use is intermittent.

For our shop this is not worth experimenting with because the Gweike compressor is already available. Follow the official requirement instead:
- 100 PSI,
- 3 CFM @ 90 PSI or better,
- good filtration.

Forum example:
https://forum.sienci.com/t/atc-air-requirements/25031

## Software community signal

gSender continues active development. The public issue tracker includes reports involving:
- tool changes,
- soft-limit behavior after tool changes,
- grblHAL streaming errors on some configurations,
- connection issues,
- "Start From" behavior.

These are not all confirmed to affect AltMill 4×8 + Sienci ATC. The practical rule is:
- stay on stable releases for normal operation,
- read release notes before upgrading,
- test homing/spindle/ATC/TLS after an update,
- do not run a valuable workpiece as the first test after a major software change.

Issue tracker:
https://github.com/Sienci-Labs/gsender/issues

# When to stop and investigate

Stop the machine instead of "seeing if it gets better" when:
- sound changes abruptly,
- the machine binds or clunks at a repeatable location,
- a closed-loop motor alarms,
- spindle speed is not what was commanded,
- ATC holder does not enter/leave the taper cleanly,
- rack pickup alignment looks visibly wrong,
- tool probes off-center on TLS,
- tool number does not match the rack,
- a rapid move approaches a clamp/rack/TLS unexpectedly,
- smoke, overheating or electrical smell appears.

The E-stop is for preventing or limiting a crash; it is cheaper than testing the machine's mechanical strength.
