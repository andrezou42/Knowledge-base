# AltMill 4×8 — Software, Firmware, CAM and Post-Processors

_Last reviewed: 2026-10-01_

## Control stack

Our working stack is:

```
Aspire / Vectric (CAD/CAM)
        ↓
Sienci ATC-capable post processor
        ↓
G-code file
        ↓
gSender
        ↓
SLB-EXT
        ↓
grblHAL
        ↓
AltMill + ATC spindle
```

## Current gSender baseline

As of 2026-10-01:

- **gSender 1.6.4** is the latest stable release located in the official repository.
- **gSender 1.7.0-Edge-2** exists as a pre-release/beta build.
- Sienci explicitly describes Edge releases as testing software; for normal machine use, stay on the stable branch unless a beta feature is specifically needed.

Release source:
https://github.com/Sienci-Labs/gsender/releases

### Important stable changes for our machine

**1.6.2**
- required baseline for current ATC documentation;
- updated ATC configuration behavior;
- improved compatibility with newer grblHAL firmware;
- fixed several tool-change workflow issues.

**1.6.3**
- added a TLS installation wizard;
- additional probing and SD-card improvements.

**1.6.4**
- current stable as reviewed;
- bug fixes and config updates;
- probing UI changed so non-default corner selection was removed and probing defaults to bottom-left behavior.

Before following an old screenshot/tutorial, check whether the UI changed after that tutorial was made.

## Firmware

Current official Sienci SLB-EXT firmware identified in the ATC setup docs:
- **Main_grblHAL 20260525**

Sienci describes 20260525 as the current main SLB-EXT grblHAL build and states it requires gSender 1.6.2 or newer.

Firmware reference:
https://github.com/Sienci-Labs/Resources/blob/main/superlongboard/slb-firmware-flashing.md

### Firmware-update rule

Do not update firmware just because a newer file exists somewhere.

Before flashing:
- back up / record changed settings;
- verify the release is intended for SLB-EXT;
- use USB, not Ethernet, for the flash process;
- turn off signal-controlled accessories;
- follow the current Sienci flashing instructions;
- after flashing, re-check the AltMill 4×8 profile, ATC configuration, homing, rack position and TLS behavior before a cutting job.

## Machine profile

After initial setup or a reset:
- gSender → Config
- select the **AltMill 4×8** machine profile
- restore/apply defaults as directed
- power-cycle when required

A wrong profile can create incorrect motor, travel, homing and limit behavior.

Official assembly/controller page:
https://resources.sienci.com/view/am4x8-controller-and-vfd/

## CAM post-processors

For ordinary non-ATC GRBL-family jobs, Sienci recommends millimeter GRBL posts, including:
- Vectric / Aspire / VCarve → **grbl (mm)**
- Fusion 360 → **grbl** with safe retract checks

Official post-processor page:
https://resources.sienci.com/view/cnc-post-processors/

### Why millimeter output is preferred

Sienci's 4×8 troubleshooting guide documents **Error 33** as a potential consequence of inch-post rounding producing duplicate/invalid motion data. Their recommendation is to export using a **grbl mm** post processor.

Therefore, even if the design is dimensioned in inches, prefer millimeter G-code output where supported.

## ATC jobs

For automatic tool changing, use the Sienci ATC-compatible post processor rather than an ordinary generic GRBL post.

ATC workflow:
1. Assign a real tool number in the Aspire/Vectric tool database.
2. Build all toolpaths for the job.
3. Export them together in one ATC-capable G-code file.
4. Verify T numbers match the intended rack tools.
5. Load in gSender.
6. Review the visualizer/tool timeline.
7. Home the machine.
8. Set the work zero.
9. Run only after checking rack/TLS/pressure status.

Sienci overview:
https://resources.sienci.com/view/atc-overview/

## Rotary jobs

Our Vortex uses a different workflow/postprocessor from normal flat work.

The equipment inventory records our intended post as the Sienci **ATC Rotary Wrap Y** postprocessor.

Do not use the rotary post for ordinary 2D sheet work and do not assume normal Y travel/zero conventions while rotary mode is active.

After a rotary job, verify gSender has properly restored the normal machine mode/settings before the next flat job.

## Fusion 360 safety note

Sienci recommends in Fusion:
- Safe Retracts = **Clearance Height**, not G28, unless the setup is deliberately designed around G28;
- Output M6 and Tool Number should be enabled only when the tool-change workflow requires them.

This matters because an unintended G28 can send the machine to a machine-coordinate position that does not match the expected workpiece clearance.

## Before running unfamiliar G-code

Use as many of these checks as practical:
- inspect the gSender visualizer;
- verify the displayed bounding box fits the workpiece and machine travel;
- verify units;
- verify G54/work coordinate;
- verify all tool numbers;
- verify spindle RPM is within 7,500–24,000 for the ATC spindle;
- verify safe Z movements;
- confirm no moves enter the rack/TLS keep-out area unexpectedly;
- use gSender's Check Mode / validation tools for new or questionable files;
- perform an outline/boundary check before starting when useful.

## Current software issue awareness

The public gSender issue tracker continues to show active bug reports. These reports are useful warning signals but are not proof that every issue applies to our configuration.

Before adopting a new major stable release:
- read its release notes,
- search for ATC/SLB-EXT regressions,
- keep a known-good installer/version available,
- validate homing, spindle, ATC and TLS before production work.

Official issue tracker:
https://github.com/Sienci-Labs/gsender/issues
