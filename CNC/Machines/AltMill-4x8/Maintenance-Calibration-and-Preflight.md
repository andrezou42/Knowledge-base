# AltMill 4×8 — Maintenance, Calibration and Pre-Flight

_Last reviewed: 2026-10-01_

## Routine maintenance

Current 4×8-specific Sienci guidance recommends periodic lubrication based on use/distance rather than calendar time.

The current page gives a practical interval of roughly **165 hours of use** for:
- rack lubrication,
- linear-guide lubrication,
- ballscrew lubrication.

A prior version of the page also described maintenance around each 100 km of linear travel. Treat 165 hours as the current simple shop interval and shorten it under heavy dust, production use or obvious lubricant loss.

Official page:
https://resources.sienci.com/view/am4x8-maintenance/

## Lubricants / cleaning

Sienci's current 4×8 page specifies:
- white lithium grease for rack/pinion,
- lithium grease for guide/ballscrew maintenance,
- shop towels,
- nylon brush for rack,
- soft brush for ballscrews,
- Scotch-Brite only as needed for light surface rust.

An older version also permits continuing Mobil Vactra #2 / 3-in-1 oil on linear guides if already using that system.

The key is consistency and cleanliness; do not mix random greases/oils without checking compatibility.

## Rack and pinion

Every maintenance cycle:
1. Remove dust/chips with a nylon brush.
2. Inspect rack teeth and pinion.
3. Apply white lithium grease.
4. Jog the machine so the grease distributes along the full rack.
5. Listen for any change in sound through the middle table joint.

If rack noise develops unexpectedly:
- verify the drive tension screw is fully set/bottomed as intended,
- verify the pivot screw is tight,
- verify the pinion is lubricated.

Official troubleshooting:
https://sienci.zendesk.com/hc/en-us/articles/47762168514580-AltMill-4x8-Troubleshooting

## Linear rails

- Wipe rails before adding lubricant; do not turn dust into abrasive paste.
- Inspect blocks/rails for chips, MDF dust and rust.
- Lubricate according to Sienci's current procedure.
- Jog end-to-end afterward to distribute lubricant.

## Ballscrews

The 4×8 uses ballscrews on X and Z.

- Remove packed debris from the screw threads with a soft brush.
- Apply the recommended grease conservatively.
- Jog through full accessible travel to distribute.

Unexpected squeal, chatter or stiffness should be investigated rather than covered with excess grease.

# Squaring

The AltMill uses dual Y homing so the gantry can automatically re-establish square when homed.

Sienci's AltMill squaring procedure uses gSender's **XY Squaring** tool to measure the error and then correct the Y dual-homing offset.

Reference:
https://resources.sienci.com/view/am-squaring-tramming/

## When to check square

Check XY square after:
- initial commissioning,
- table-joint or Y-drive work,
- a collision,
- moving the machine,
- unexplained dimensional error,
- repeated diagonal mismatch on known-square test geometry.

Do not compensate bad mechanics with CAM scaling.

# Tramming

Tram means the spindle rotation axis is perpendicular to the XY plane.

### Symptoms of poor tram
- ridges after spoilboard surfacing,
- one side of a wide surfacing cutter consistently cutting deeper,
- visible "steps" between adjacent pocket passes,
- inconsistent bottom finish even when Z motion itself is stable.

Sienci's AltMill mount is designed to register using shoulder screws and reference features. If fine correction is required, Sienci documents using the eccentric bushing / alternate fastener arrangement to pivot the mount.

Reference:
https://resources.sienci.com/view/am-squaring-tramming/

## Tramming order

1. Make sure the machine frame/table joint is mechanically sound.
2. Secure the spoilboard.
3. Surface enough area to create a machine-referenced plane.
4. Check tram with a dial-indicator tramming arm.
5. Adjust spindle mount if required.
6. Re-surface a small test area.
7. Only then remove more spoilboard.

Do not chase tram by repeatedly taking deep spoilboard passes.

# Daily / pre-job checklist

Use this before routine work.

### Machine
- [ ] No loose objects on table or rails.
- [ ] Rack/linear rails visibly clear.
- [ ] No new unusual noise or binding.
- [ ] E-stop is reachable.
- [ ] Machine is homed.
- [ ] Correct gSender machine profile is loaded.

### ATC / spindle
- [ ] VFD powered.
- [ ] Air supply on.
- [ ] Regulator at required ATC pressure.
- [ ] Pressure indicator normal.
- [ ] Tool holders clean.
- [ ] Correct tools are in intended rack slots.
- [ ] TLS area is clear.
- [ ] Dust shoe clearance is appropriate for the job.

### Workpiece
- [ ] Correct stock and thickness.
- [ ] Stock is square/positioned as intended.
- [ ] Workholding is secure.
- [ ] Screws/clamps are outside the toolpath or modeled intentionally.
- [ ] Spoilboard has enough remaining thickness.

### CAM / G-code
- [ ] Correct file loaded.
- [ ] Correct units.
- [ ] Correct origin convention.
- [ ] Correct G54/workspace.
- [ ] X/Y/Z zero matches CAM.
- [ ] Tool numbers correct.
- [ ] Feed, plunge, RPM and depth of cut reviewed.
- [ ] Visualizer/outline fits within safe machine travel.
- [ ] No unexpected rapid into rack/TLS/clamps.

Official general pre-flight:
https://resources.sienci.com/view/cnc-running-jobs/

# Spindle warm-up

Sienci recommends a short warm-up routine, especially:
- in a cold shop,
- after a long idle period,
- when spindle bearing sound is unusual.

The supplied warm-up G-code takes roughly 10 minutes and spins the spindle without moving the machine.

Do not start heavy cutting on a very cold spindle if a warm-up is practical.
