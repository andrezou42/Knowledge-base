# Sienci AltMill 4×8 — Machine Reference

_Last reviewed against Sienci documentation: 2026-10-01_

This is the canonical quick-reference page for our primary CNC.

## Our exact configuration

- Sienci AltMill 4×8
- Joinery configuration
- SLB-EXT 32-bit controller
- grblHAL firmware
- Sienci 2.2 kW ATC spindle
- 6-position ATC rack
- ISO20 tool holders with ER20 collets
- Tool Length Sensor (TLS)
- AutoZero touch plate
- gSender
- Vortex Rotary Axis, 48 in closed-loop version

See [Equipment-Inventory.md](../../Equipment-Inventory.md) for purchase history and the full list of owned accessories.

## Key factory specifications

| Item | Published specification |
|---|---|
| Overall machine size | 1676 × 2896 × 975 mm (66 × 114 × 38.4 in) |
| Nominal cutting area | 1265 × 2460 × 210 mm (49.8 × 104 × 8.3 in) |
| Max Y cutting speed | approx. 25,000 mm/min (1,000 IPM) |
| Max X cutting speed | approx. 16,000 mm/min (about 590 IPM) |
| Max Z cutting speed | approx. 6,000 mm/min (236 IPM) |
| Repeatability | ±0.05 mm (±0.002 in) |
| Y motion | Rack and pinion with precision gearbox reduction |
| X motion | 16 mm precision ballscrew |
| Z motion | 12 mm precision ballscrew |
| Linear guides | 15 mm profiled linear guide rails and blocks on all axes |
| Y motors | High-torque NEMA 23 closed-loop steppers, 3 Nm |
| X / Z motors | High-torque NEMA 23 closed-loop steppers, 2 Nm |
| Controller | SLB-EXT, 32-bit, grblHAL |
| Approx. assembled weight | 400 lb before add-ons |
| Standard spindle mount | 80 mm |

**Important:** these are axis/machine limits, not default machining feeds. Actual cutting feed is constrained by tool, material, chip load, spindle speed, depth of cut, workholding, and finish requirements.

Official source: https://resources.sienci.com/view/am4x8-specifications/

## Joinery + ATC travel: use the correct numbers

Several official Sienci pages quote different Y travel numbers because they refer to different configurations.

### Base 4×8
Published nominal Y cutting area: **104 in**.

### ATC in the normal/default geometry
Sienci states that the ATC rack reduces Y travel by about **5.3 in**, leaving approximately **99 in** on the 4×8.

### Our joinery configuration
Sienci states:
- joinery configuration without ATC: approximately **101 in on-table spindle travel**
- joinery configuration with ATC: approximately **95.25 in on-table travel**
- spindle center overhangs the front edge by about **3.7 in**

That gives roughly **98.95 in of geometric front-to-back reach** when the front overhang is included, even though only 95.25 in is on the table.

Practical consequence: a 96 in sheet can still be machined, but stock position, origin, dust-shoe/rack clearance, and actual machine limits must be checked before trusting a full-sheet toolpath.

Official sources:
- https://resources.sienci.com/view/am4x8-joinery-configuration/
- https://resources.sienci.com/view/atc-specifications/

## Spindle / ATC specifications

| Item | Specification |
|---|---|
| ATC spindle power | 2.2 kW |
| Spindle speed range | 7,500–24,000 RPM |
| Constant torque region | from 18,000 RPM |
| Spindle bearings | Ceramic |
| Tool holder | ISO20 |
| Collet system | ER20 |
| Maximum cutter shank in rack | 1/2 in |
| Maximum tool diameter in rack | 2 in |
| Our rack | 6 slots |
| Published spindle noise | about 60 dBA at 24,000 RPM |

Official source: https://resources.sienci.com/view/atc-specifications/

## Electrical and air

For the ATC system Sienci specifies separate circuits for the CNC/controller, 2.2 kW spindle, and compressor.

ATC air requirement:
- **100 PSI operating pressure**
- **3 CFM at 90 PSI or better**
- **40 µm or better coalescing filtration**

Our shop uses the large Gweike compressor as the upstream air source and regulates the AltMill branch at the Sienci filter/regulator.

Official source: https://resources.sienci.com/view/atc-specifications/

## Mechanical detail that matters most on this 4×8

The 4×8 Y axis is split into front and rear table/rail sections. Sienci explicitly warns that alignment of the two rack and linear-rail sections at the table joint is critical.

Symptoms of a bad joint/alignment can include:
- clunking or roughness crossing the middle joint,
- unusual rack-and-pinion sound,
- closed-loop motor alarms from excess mechanical resistance.

Do not treat a recurring clunk at the joint as normal.

Official sources:
- https://resources.sienci.com/view/am4x8-joining-the-tables/
- https://sienci.zendesk.com/hc/en-us/articles/47762168514580-AltMill-4x8-Troubleshooting

## Materials

Sienci lists the machine as suitable, with appropriate tooling and strategy, for:
- wood, plywood, MDF,
- acrylic and other plastics,
- composites such as ACM/Dibond,
- aluminum, brass and copper,
- some ferrous metals with appropriate lubrication and conservative machining strategy,
- foam.

For our sculptural work, the machine should generally be treated as a high-performance CNC router rather than as a rigid metalworking mill.

## Safety points worth keeping visible

- Do not leave the machine running unattended.
- Keep clear of the exposed rack-and-pinion assemblies; they are major pinch points.
- Wear eye and hearing protection.
- MDF dust requires effective collection plus respiratory protection during dusty operations such as surfacing.
- Do not mix hot metal chips with a wood-dust collection system.
- Before a job, verify workholding, tool, zero, clearance, spindle state and the correct file.

Official sources:
- https://resources.sienci.com/view/am4x8-safety/
- https://resources.sienci.com/view/cnc-running-jobs/
