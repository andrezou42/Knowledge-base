# AltMill 4×8 — ATC, Spindle, TLS and Pneumatics

_Last reviewed: 2026-10-01_

This page covers the Sienci Automatic Tool Changer installed on our AltMill 4×8.

## Our ATC hardware

- 2.2 kW air-cooled ATC spindle
- 6-position rack
- 6 ISO20 holders
- ER20 collets
- Tool Length Sensor (TLS)
- ATC expansion hardware for SLB-EXT
- Clear Cut dust shoe
- 8 mm pneumatic line
- Sienci filter/regulator
- manual shutoff / quick-disconnect valve
- shared upstream Gweike shop compressor

Official kit specification:
https://resources.sienci.com/view/atc-specifications/

## Spindle and rack limits

- 2.2 kW output
- 7,500–24,000 RPM
- constant torque from 18,000 RPM upward
- ceramic bearings
- ISO20 holders
- ER20 collets
- rack maximum tool diameter: 2 in
- rack maximum cutter shank: 1/2 in
- our rack capacity: 6 tools

The rack limit matters independently of the ER20 collet system. A physically larger surfacing cutter may fit the spindle but not safely fit in the automatic rack.

## Air requirements

Sienci's published requirement:
- **100 PSI operating pressure**
- **3 CFM at 90 PSI or better**
- **40 µm or better coalescing filtration**

Our setup:
```
Gweike compressor
  ↓
manual shutoff / isolation valve
  ↓
Sienci filter/regulator
  ↓
8 mm pneumatic line
  ↓
ATC spindle
```

The upstream compressor can run at a higher system pressure if all downstream hardware is rated for it. The Sienci regulator should set the ATC branch to the required pressure.

Avoid treating "1 MPa at the main compressor" as the ATC pressure setting; 1 MPa is about 145 PSI and the ATC branch is regulated separately.

## Normal pressure indication

During setup, Sienci instructs checking the pressure light on the spindle:
- white = pressure condition is acceptable;
- red = check compressor pressure, regulator pressure and whether the manual valve is open.

A temporary air leak can occur the first time the hardware is connected before the ATC software configuration is completed. A continuing leak afterward is a troubleshooting condition.

Official setup:
https://resources.sienci.com/view/atc-software/

## Tool-holder assembly

For ISO20 + ER20:

1. Snap the ER20 collet into the collet nut first.
2. Insert the cutter.
3. Thread the nut onto the ISO20 holder.
4. Tighten using the proper two-wrench method.
5. Keep tool stick-out only as long as necessary.
6. Do not tighten an empty ER20 collet.

Before loading a holder:
- clean the ISO20 taper and spindle taper,
- clean the collet and nut,
- remove chips/dust,
- inspect the cutter and holder for damage.

Any contamination on the taper can affect runout and repeatability.

## Tool numbering

ATC tool number determines the requested physical tool.

For our current permanent assignments:
- **T1 — 1/4 in SpeTool SPE-X upcut**
- **T2 — 1/8 in SpeTool SPE-X O-flute**
- T3–T6 not yet standardized

Store tool numbers in the CAM tool database so the correct T-number is exported automatically.

Sienci's ATC system can also remap a requested tool number to a rack tool, but a simple fixed physical assignment is easier to audit while we are learning the machine.

Official overview:
https://resources.sienci.com/view/atc-overview/

## TLS behavior

The TLS is not the same as AutoZero.

- **AutoZero** establishes the workpiece/work-coordinate reference.
- **TLS** measures the currently loaded tool after a tool change.

With the Sienci ATC workflow, each automatically loaded tool is probed on the TLS so the work zero can be retained across tools.

Do not manually re-zero Z after every ATC change unless the specific workflow calls for it; doing so can defeat the intended tool-length compensation process.

## ATC software prerequisites

Current Sienci instructions require:
- gSender **1.6.2 or newer**
- SLB-EXT firmware **20260525**
- microSD card mounted in the controller, preferably the supplied card
- ATC macros installed through gSender's Accessory Installation workflow
- ATC enabled in Config → Tool Changing

Current stable gSender reviewed 2026-10-01 is 1.6.4.

Official pages:
- https://resources.sienci.com/view/atc-before-you-begin/
- https://resources.sienci.com/view/atc-software/

## Rack-location setup: high-risk detail

During automatic rack-location setup, Sienci tells the user to position the ATC sensor roughly **1–2 mm above and centered over the rack stud**.

Important: the sensor LED can trigger even when the sensor is not positioned correctly enough for the automated grid search. If "Find Rack" fails, do not repeatedly launch the routine blindly; re-center the sensor carefully first.

On a 4×8, this setup can involve a lot of walking between the computer and the far end of the machine. A second person is useful for observing sensors and clearance.

## First tool-change validation

Before a real multi-tool job:

1. Home the machine.
2. Confirm pressure light and rack/TLS sensors.
3. Command T1.
4. Watch pickup and TLS probing.
5. Return/change to T2.
6. Confirm T1 returns to slot 1.
7. Confirm T2 is collected from slot 2 and probes.
8. Return to T1.
9. Confirm repeatability and no interference with rack/dust shoe.

If an E-stop interrupts a tool change, Sienci's recovery sequence is:
- power-cycle controller,
- reconnect,
- release/cycle E-stop and unlock,
- home again,
- then retry.

Official final checks:
https://resources.sienci.com/view/atc-final-checks/

## Known software issue that matters

gSender 1.6.0 and 1.6.1 had a documented ATC configuration-reset problem that could result in the machine crashing into the tool rack. Sienci's ATC troubleshooting explicitly says to use **1.6.2 or above**.

Our default should therefore be the current stable build, not an early 1.6.x release.

## ATC warm-up

Sienci provides a spindle warm-up G-code and recommends warm-up particularly when:
- the shop is cold,
- the spindle has been idle,
- or unusual bearing sound is present.

The maintenance page describes an approximately 10-minute warm-up routine that spins the spindle without machine motion.

See:
https://resources.sienci.com/view/am4x8-maintenance/
