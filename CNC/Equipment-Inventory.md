# CNC Equipment Inventory

_Last updated: 2026-10-01_

This is the master inventory for the current CNC setup. It records the main machines, Sienci/AltMill accessories, rotary and probing equipment, pneumatic hardware, and cutters known to be on hand.

## Primary CNC system

### Sienci AltMill 4×8

Current main CNC:
- Sienci AltMill 4×8
- configured in joinery configuration
- ATC spindle system installed
- 6-tool ATC rack installed
- Tool Length Sensor (TLS) installed
- SLB-EXT / grblHAL control system
- gSender used as the machine sender/controller interface

The 4×8 replaced an originally ordered AltMill MK2 4×4. The 4×4 line was cancelled/refunded and is not part of the current machine inventory.

### Sienci purchase history

#### Order #82342 — 2025-11-21
- AutoZero Touch Plate — quantity 1 — C$120

#### Order #82643 — 2025-11-29
Original order:
- AltMill MK2 4×4 — quantity 1 — C$4,290 — later cancelled/refunded
- ATC Air Filter Regulator Kit — quantity 1 — C$120
- Automatic Tool Changer — quantity 1 — C$4,040
  - configuration: **ATC + 6-Tool Rack Kit**
  - ordered for AltMill 2×4 / 4×4 family
- Vortex Rotary Axis — **48 in rail with closed loop** — quantity 1 — C$720

#### Order #82851 — 2025-12-04
Replacement/final machine order:
- AltMill 4×8 — quantity 1 — C$10,390
- the previously ordered 4×4 appears as quantity 0 / refunded
- completion record also carries the following accessories:
  - ATC Air Filter Regulator Kit — quantity 1
  - Automatic Tool Changer, **ATC + 6-Tool Rack Kit** — quantity 1
  - Vortex Rotary Axis, **48 in rail with closed loop** — quantity 1

The final completed order therefore confirms the current 4×8 machine together with the ATC package, regulator kit, and Vortex rotary system.

## ATC / spindle hardware

Known hardware currently associated with the AltMill:
- ATC spindle
- 6-position tool rack
- Tool Length Sensor (TLS)
- ISO20 / ER20 tool-holder system
- ER20 collets
- ISO20/collet wrench set
- ATC pneumatic release system
- ATC air filter/regulator
- manual blue-handle pneumatic shutoff / quick-disconnect valve
- 8 mm push-to-connect pneumatic tubing/fittings

Current permanent tool-number plan started with:
- **T1:** 1/4 in SpeTool upcut
- **T2:** 1/8 in SpeTool O-flute

Additional rack assignments can be added as the remaining tools are standardized.

## Rotary equipment

- Sienci **Vortex Rotary Axis**
- 48 in rail
- closed-loop version
- intended to be used with the ATC Rotary Wrap Y postprocessor for rotary jobs

## Probing / zeroing equipment

- Sienci AutoZero Touch Plate
- Sienci Tool Length Sensor (TLS)

Roles:
- AutoZero: establishes work X/Y/Z reference
- TLS: measures tool length after ATC tool changes and preserves the work coordinate system

## Pneumatic / air equipment

### Sienci ATC air hardware
- filter/regulator with pressure gauge
- blue-handle shutoff / quick-disconnect valve
- 8 mm pneumatic line and push fittings

ATC operating pressure target:
- approximately **90–100 PSI**
- approximately **0.62–0.69 MPa**

### Shared compressor
- large Gweike screw air compressor from the Gweike laser setup
- currently used as the upstream air source for the AltMill ATC
- compressor can provide higher upstream pressure; the Sienci regulator is used to reduce the ATC supply to the required pressure

## Current CNC cutters / bits

| # | Brand | Tool | Cutting diameter | Shank | Known part / SKU | Notes |
|---|---|---|---:|---:|---|---|
| 1 | SpeTool | 45° V-groove / chamfer cutter | 1/4 in | 1/4 in | W06017 / ECP4F-1/4-45-FBA | 4-flute, TiAlN; engraving/chamfer/detail work |
| 2 | SpeTool | SPE-X spiral upcut end mill | 1/4 in | 1/4 in | W04020 | Current T1; 1 in cutting length |
| 3 | Amana Tool | Spektra spiral plunge downcut | 1/4 in | 1/4 in | 46202-K | Useful when top-surface finish is important |
| 4 | SpeTool | SPE-X O-flute upcut | 1/4 in | 1/4 in | likely W03001-SPE-X | Exact SKU still to be physically verified |
| 5 | SpeTool | SPE-X O-flute upcut | 1/8 in | 1/4 in | likely W03002-SPE-X | Current T2; exact SKU still to be physically verified |
| 6 | BINSTAK | spoilboard surfacing / slab-flattening bit | 1 in | 1/4 in | Amazon purchase; exact manufacturer SKU not recorded | Shipped Feb. 2025; suitable for AltMill spoilboard surfacing |

Detailed cutter specifications and CAM notes are kept in [Tooling.md](./Tooling.md).

## Current table / spoilboard system

- permanent lower table/base: 3/4 in plywood
- replaceable upper spoilboard: 3/4 in MDF
- upper MDF is segmented into three Y-direction panels
- current actual MDF width: approximately 49.125 in
- current planned fastener: #8 × 1 in construction screw
- current screw-head recess: 10 mm diameter, 8 mm deep
- current MDF clearance hole: 4.5 mm

See the dated setup log in [Logs/2026-10-01-AltMill-Setup.md](./Logs/2026-10-01-AltMill-Setup.md) for the detailed hole pattern, CAM settings, and first-run preparation.

## Other CNC machine on hand

- Genmitsu ProVerXL 4030 V2
- extended to approximately 6060 using the Genmitsu extension kit

This is separate from the AltMill 4×8 system but remains part of the CNC equipment inventory.

## Items to verify / add later

- exact SKU for the 1/4 in SpeTool O-flute
- exact SKU for the 1/8 in SpeTool O-flute
- final permanent T3–T6 rack assignments
- exact count of spare ISO20 holders / ER20 collets on hand
- any dust shoe, vacuum, mist/coolant, or dedicated workholding accessories added later
