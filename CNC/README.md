# CNC Knowledge Base

_Last reviewed: 2026-10-01_

This folder is the working reference for CNC machines, tooling, setup decisions, operating procedures, maintenance, troubleshooting, and dated shop logs.

## Current primary machine

**Sienci AltMill 4×8**
- Joinery configuration
- Sienci 2.2 kW Automatic Tool Changer (ATC) spindle
- 6-tool ATC rack
- Tool Length Sensor (TLS)
- AutoZero touch plate
- SLB-EXT controller running grblHAL
- gSender control software
- Vortex Rotary Axis, 48 in rail, closed-loop version

Current stage: machine is assembled and being commissioned. The immediate work is first functional checks, ATC validation, spoilboard surfacing, then first real cutting tests.

## Fast navigation

### Machine reference
- [AltMill 4×8 — machine profile and key specifications](./Machines/AltMill-4x8/README.md)
- [Commissioning and spoilboard surfacing](./Machines/AltMill-4x8/Commissioning-and-Spoilboard.md)
- [ATC spindle, tool rack, TLS and pneumatics](./Machines/AltMill-4x8/ATC-Spindle-and-Pneumatics.md)
- [Software, firmware, CAM and post-processors](./Machines/AltMill-4x8/Software-Firmware-and-CAM.md)
- [Maintenance, squaring, tramming and pre-flight checks](./Machines/AltMill-4x8/Maintenance-Calibration-and-Preflight.md)
- [Troubleshooting and community notes](./Machines/AltMill-4x8/Troubleshooting-and-Community-Notes.md)

### What we physically own
- [Equipment inventory](./Equipment-Inventory.md)
- [Tooling inventory](./Tooling.md)

### Dated records
- [2026-10-01 AltMill setup log](./Logs/2026-10-01-AltMill-Setup.md)

## How to use this knowledge base

The machine pages are organized by **what you are trying to do**, not by the order information was learned.

- Need a number such as travel, speed, spindle RPM or repeatability? → Machine profile.
- About to surface the spoilboard or run a first test? → Commissioning.
- ATC failed, air is leaking, rack pickup looks wrong, or TLS is involved? → ATC page, then troubleshooting.
- Need to export from Aspire/VCarve/Fusion or check gSender/firmware? → Software/CAM.
- Machine is leaving ridges, going out of square, sounding rough, or is due for lubrication? → Maintenance/calibration.
- An alarm or strange behavior appears? → Troubleshooting.
- Need to know which cutter or accessory is actually on hand? → Equipment/Tooling inventory.

## Source hierarchy

For machine-specific facts, use this order:

1. **Current Sienci AltMill 4×8 documentation**
2. **Current Sienci ATC / SLB-EXT / gSender documentation**
3. **Sienci support troubleshooting articles**
4. **Sienci Community Forum posts, especially posts by Sienci staff/engineers**
5. Reddit and other owner reports as anecdotal evidence only

Community reports are useful for discovering failure modes, but they are not treated as specifications unless confirmed by Sienci documentation.

## Important configuration-specific warning

This machine is in **joinery configuration with an ATC rack**. Do not blindly apply travel numbers from:
- the default 4×8 configuration,
- the non-ATC 4×8,
- the AltMill 2×4 or 4×4,
- or older MK1/MK2 instructions.

The joinery + ATC combination has its own usable Y geometry. See the machine profile for the distinction.

## Documentation freshness

The AltMill 4×8 is a newer machine and Sienci has been updating the documentation frequently during 2026. When a procedure affects firmware, ATC behavior, limits, or safety, verify the current Sienci page before making permanent configuration changes.
