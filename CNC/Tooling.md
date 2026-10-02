# CNC Tooling Inventory

_Last updated: 2026-10-01_

This file records CNC cutters currently on hand for future CAM, feeds/speeds, and toolpath planning.

## Current end mills / router bits

| # | Brand | Tool | Diameter | Shank | Cutting length | Flutes | Coating / series | Part / SKU | Notes |
|---|---|---|---|---|---|---|---|---|---|
| 1 | SpeTool | Solid-carbide V-groove / chamfer end mill, 45° | 1/4 in | 1/4 in | — | 4 | TiAlN | W06017 / ECP4F-1/4-45-FBA | User-described as “Speedtool carbide end mill, 45 degrees, ECP4F-D1/4 inch, W06017.” Manufacturer lists 2 in overall length and 18,000 RPM recommended. |
| 2 | SpeTool | Spiral upcut end mill, SPE-X | 1/4 in | 1/4 in | 1 in | 2 | SPE-X / TAC | W04020 | User has this bit on hand. SpeTool catalog data identifies W04020 as a 1/4 in cutting diameter, 1/4 in shank, 1 in cutting length, 2-1/2 in overall length upcut. |
| 3 | Amana Tool | Solid-carbide Spektra spiral plunge down-cut | 1/4 in | 1/4 in | 3/4 in | — | Spektra | 46202-K | User-described as “Manna Tools quarter inch spiral downcut, 46202-K.” Manufacturer identifies it as Amana Tool 46202-K. |
| 4 | SpeTool | Spiral O-flute upcut end mill, SPE-X | 1/4 in | 1/4 in | 1 in | 1 | SPE-X | Likely W03001 SPE-X | Exact part number was not supplied by user; manufacturer match based on stated 1/4 in O-flute SPE-X configuration. |
| 5 | SpeTool | Spiral O-flute upcut end mill, SPE-X | 1/8 in | 1/4 in | 3/4 in | 1 | SPE-X | Likely W03002 SPE-X | User described “SP 1/8 inch, diameter 1 quarter inch”; interpreted as 1/8 in cutting diameter with 1/4 in shank. Exact part number was not supplied by user. |

## Current AltMill spoilboard fastener decision

For the current AltMill 4×8 spoilboard setup:
- Top: 3/4 in MDF
- Bottom: 3/4 in plywood
- Fastener: #8 × 1 in construction screw
- Planned screw-head recess depth: 8 mm
- Planned MDF clearance-hole diameter: 4.5 mm
- Recess diameter remains to be finalized against the actual screw-head diameter before machining.

## Notes for future CAM planning

- Confirm the exact physical bit and flute length before programming any cut that approaches the listed cutting-length limit.
- Tool #5 is suitable for small-diameter interpolation where a 1/4 in shank can be held in the ATC ER20 collet.
- O-flute tools should be considered first for plastics/acrylic where appropriate.
- Downcut Tool #3 is useful when top-surface finish is the priority in wood/MDF/plywood; chip evacuation and full-depth slotting limits still need to be considered.
- The 45° V-groove tool is primarily for engraving, V-grooves, chamfers, and related detail work rather than ordinary pocket clearing.
