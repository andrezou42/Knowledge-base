# AltMill 4×8 — Sources and Update Log

_Last research pass: 2026-10-01_

This page records what was reviewed to build the AltMill 4×8 knowledge base and makes future updates easier.

## Source policy

Priority:
1. Current Sienci AltMill 4×8 documentation
2. Current Sienci ATC / SLB-EXT / gSender documentation
3. Sienci support/Zendesk troubleshooting
4. Sienci Community Forum, especially Sienci staff/engineer replies
5. Other owner/community reports as anecdotal evidence

A community report is not promoted to a machine specification unless Sienci documentation confirms it.

# Official AltMill 4×8 sources reviewed

## Specifications
https://resources.sienci.com/view/am4x8-specifications/

Used for:
- dimensions and nominal cutting area
- maximum axis cutting speeds
- repeatability
- rack-and-pinion / ballscrew motion architecture
- motor torque
- controller
- electrical/environment information

Current facts captured:
- Y max ~25,000 mm/min
- X max ~16,000 mm/min
- Z max ~6,000 mm/min
- repeatability ±0.05 mm
- Y rack/pinion with gearbox
- X 16 mm ballscrew
- Z 12 mm ballscrew
- Y motors 3 Nm; X/Z 2 Nm

## Joinery configuration
https://resources.sienci.com/view/am4x8-joinery-configuration/

Used for our exact table configuration:
- 101 in on-table travel without ATC
- 95.25 in on-table travel with ATC
- 3.7 in front spindle-center overhang

Do not substitute generic default-configuration Y travel when planning our full-sheet jobs.

## Final checks
https://resources.sienci.com/view/am4x8-final-checks/

Used for:
- frame/fastener checks
- table level
- coupler checks
- rack grease
- motor DIP switches
- electrical/wiring checks

## Surfacing wasteboard
https://resources.sienci.com/view/am4x8-surfacing-wasteboard/

Current 4×8-specific procedure reviewed:
- reachable surfacing area determined by jogging
- reference approx. 49 × 103 in
- cut depth ≤ 1 mm
- ~40% overlap
- ~20,000 RPM
- ~8,000 mm/min in MDF
- remove dust shoe at travel limits
- disable hard/soft limits for this controlled routine, then re-enable and power-cycle immediately afterward

## Maintenance
https://resources.sienci.com/view/am4x8-maintenance/

Important revision found during this research pass:
- page updated 2026-09-28
- rack/pinion: 160 hours
- linear guides: 160 hours
- ballscrews: 165 hours
- spindle warm-up file: about 10 minutes

This superseded older distance-based/generalized wording found in earlier/cached versions.

## Squaring and tramming
https://resources.sienci.com/view/am-squaring-tramming/

Used for:
- gSender XY Squaring workflow
- dual-Y squaring concept
- spindle tramming and mount adjustment

## Controller / VFD
https://resources.sienci.com/view/am4x8-controller-and-vfd/

Used for:
- SLB-EXT/VFD installation context
- machine-profile/configuration workflow

# Official ATC sources reviewed

## ATC specifications
https://resources.sienci.com/view/atc-specifications/

Captured:
- 2.2 kW ATC spindle
- 7,500–24,000 RPM
- constant torque beginning at 18,000 RPM
- ISO20 / ER20
- ceramic bearings
- 6-tool rack in our configuration
- 2 in maximum rack tool diameter
- 1/2 in maximum rack shank
- 100 PSI operating air
- 3 CFM @ 90 PSI minimum
- 40 µm or better coalescing filtration

## Before you begin
https://resources.sienci.com/view/atc-before-you-begin/

Current software baseline:
- gSender 1.6.2+ required
- SLB-EXT firmware 20260525 expected
- ATC-specific CAM postprocessor required

## ATC software setup
https://resources.sienci.com/view/atc-software/

Used for:
- rack sensor and TLS checks
- ATC accessory installation
- rack-location setup
- sensor positioning / automated rack finding
- microSD-dependent macro configuration

## ATC overview
https://resources.sienci.com/view/atc-overview/

Used for:
- T-number → rack behavior
- automatic TLS probing after load
- retaining work zero across tool changes
- remapping behavior

## ATC final checks
https://resources.sienci.com/view/atc-final-checks/

Used for:
- left-to-right rack numbering with T1 at left
- tool-holder/ER20 assembly reminders
- homing requirement
- wrong-tool diagnostics
- interrupted tool-change recovery
- keep-out behavior
- documented gSender 1.6.0/1.6.1 rack-settings bug

## ATC first project
https://resources.sienci.com/view/atc-first-project/

Used for:
- small first multi-tool verification job
- Tool Timeline check
- watching first automatic tool change
- validating tool numbers, postprocessor and zero retention

# gSender / firmware sources reviewed

## gSender source/release history
https://github.com/Sienci-Labs/gsender

As reviewed 2026-10-01:
- current stable development-history release: **1.6.4**, dated 2026-09-15
- 1.6.3 added TLS installation workflow and additional ATC/tool-table improvements
- 1.6.2 is the current minimum called out by Sienci ATC documentation

Important: use stable builds for routine production; validate ATC/TLS/homing after upgrades.

## SLB / SLB-EXT firmware
https://github.com/Sienci-Labs/Resources/blob/main/superlongboard/slb-firmware-flashing.md

As reviewed 2026-10-01:
- latest documented SLB-EXT main build: **Main_grblHAL 20260525**
- requires gSender 1.6.2+
- firmware flashing must be done over USB, not Ethernet
- restore/re-check machine profile and custom settings after flashing

# Official troubleshooting sources reviewed

## AltMill 4×8 troubleshooting
https://sienci.zendesk.com/hc/en-us/articles/47762168514580-AltMill-4x8-Troubleshooting

Key 4×8-specific items:
- Y center-joint rail/rack alignment
- matched left/right Y sections
- rack/pinion noise checks
- motor DIP/settings
- Alarm 2 travel
- Error 33 and millimeter postprocessor

## Alarm 14 / Alarm 19
https://sienci.zendesk.com/hc/en-us/articles/34779231810964-Alarm-14-Alarm-19

Current clarification:
- AltMill 4×8/current firmware generally reports **Alarm 19**
- older firmware may report Alarm 14
- points to VFD/controller/RS485 communication or configuration

## Alarm 10 / Alarm 17 — motor fault
https://sienci.zendesk.com/hc/en-us/articles/36090373125396-Alarm-10-Alarm-17-Motor-Fault

Updated 2026-09-24:
- pre-May-2026 firmware: Alarm 10
- post-May-2026 firmware: Alarm 17
- distinguish a real `Motor Error` from E-stop/controller-related Alarm 10 behavior

## Alarm 15
https://sienci.zendesk.com/hc/en-us/articles/52202595650068-Alarm-15

Used for:
- dual-Y homing mismatch / anti-skew protection
- sensor, alignment and motor-setting checks

## Limit switch test
https://sienci.zendesk.com/hc/en-us/articles/37566087455380-AltMill-Limit-Switch-Test

Used for isolating:
- sensor
- cable
- controller input

# Other official operating sources reviewed

## Running jobs checklist
https://resources.sienci.com/view/cnc-running-jobs/

Used for:
- firmware/workspace check
- workholding
- zeroing
- correct file/tool
- pre-flight sequence

## AutoZero
https://resources.sienci.com/view/addons-autozero/

Current 2026 setup guidance captured in the operating runbook.

## Machine coordinates / work zero
https://resources.sienci.com/view/cnc-machine-coordinates/

Used for:
- machine coordinates vs work coordinates
- G54/workspace concept
- zero persistence after homing

# Community threads reviewed and retained

Only threads that produced a useful machine-specific lesson were retained.

## ATC spindle mounting plate variants
https://forum.sienci.com/t/atc-spindle-mounting-plate/26378

Sienci ATC engineer confirmed multiple Z-plate variants and that the 4×8 gantry plate differs from smaller AltMills.

Lesson: do not diagnose our 4×8 hardware from a 2×4/4×4 photo.

## ATC dust-shoe / rack interference
https://forum.sienci.com/t/atc-tool-change-causes-bottom-half-of-dust-shoe-to-drop/26805

Sienci staff identified slight rack contact on some machines; owner also identified hose compression force.

Lesson: watch dust-shoe/rack clearance and support the hose during early ATC tests.

## ATC setup tips
https://forum.sienci.com/t/atc-setup-tips-and-tricks/26629

Owner reported low-pressure faults when compressor cut-in allowed pressure to fall below ATC needs.

Lesson: validate **minimum pressure during actual tool changes**, not only tank maximum pressure.

## ATC air requirements discussion
https://forum.sienci.com/t/atc-air-requirements/25031

Useful mainly as background. Our shop has a large Gweike compressor, so we will follow Sienci's published air requirement rather than designing around a marginal small compressor.

## Full-sheet workholding discussion signal
Recent cabinet/full-sheet owners repeatedly emphasize that sheet flatness matters for dados, shallow pockets and repeatable Z depth.

For our work, solve full-sheet workholding as its own system rather than assuming a 4×8 table automatically keeps a 4×8 sheet flat.

# What was deliberately excluded

Not every forum post was copied into the KB.

Excluded unless later confirmed/relevant:
- order/shipping discussions
- pricing opinions
- unverified speed/feed recipes with unknown cutter/material
- modifications for other AltMill sizes
- third-party ATCs not installed on our machine
- isolated software complaints without reproduction or Sienci confirmation
- old instructions superseded by 4×8-specific 2026 pages

# When to refresh this research

Re-run this source review when any of the following happens:
- gSender stable version changes materially
- SLB-EXT firmware changes from 20260525
- Sienci revises ATC macros/tool-change architecture
- a recurring machine fault appears in our shop
- the machine receives a hardware upgrade
- Sienci publishes a newer 4×8 handbook/maintenance/surfacing procedure
- before changing hard/soft limit, homing or rack configuration values
