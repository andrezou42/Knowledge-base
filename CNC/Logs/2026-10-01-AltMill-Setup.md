# AltMill 4×8 Setup Log — 2026-10-01

This log records the decisions, setup work, and less-obvious details established while preparing the AltMill 4×8 for its first spoilboard machining and ATC tests.

## 1. Table and spoilboard setup

- Machine: Sienci AltMill 4×8, joinery configuration, with ATC spindle/tool rack/TLS.
- Permanent lower base: 3/4 in plywood fastened to the aluminum crossbeams.
- Replaceable upper spoilboard: 3/4 in MDF, made from three panels:
  - front panel: Y = 0–43.000 in
  - middle panel: Y = 43.000–72.750 in
  - rear panel: Y = 72.750–96.000 in
- Actual MDF width is about 49.125 in. The MDF overhangs the nominal 48 in base by 1.125 in on the left.
- Current working coordinate convention for the spoilboard file:
  - actual front-left MDF corner = X0 / Y0
  - front = Y0
  - rear/ATC side = Y96
- Planned 60 permanent fastener locations:
  - X from actual left: 2.625, 13.875, 25.125, 36.375, 47.625 in
  - Y: 1.500, 11.500, 21.500, 31.500, 41.500, 44.500, 53.420, 62.330, 71.250, 74.250, 84.380, 94.500 in
- Equivalent X positions measured leftward from the actual right-front corner:
  - 1.500, 12.750, 24.000, 35.250, 46.500 in
- Temporary screws should go between the permanent rows/columns so the CNC does not machine into them. Useful midpoint X values measured from the right are approximately 7.125, 18.375, 29.625, and 40.875 in.

## 2. Spoilboard screw and CAM plan

Current fastener plan:
- #8 × 1 in construction screws
- 10 mm diameter screw-head recess
- recess depth: 8.0 mm / 0.315 in
- 4.5 mm clearance hole through MDF

Current two-tool Aspire plan:
- T1: 1/4 in SpeTool SPE-X upcut
  - pocket the 10 mm head recesses
  - start depth 0
  - cut depth 0.315 in
- T2: 1/8 in SpeTool O-flute
  - interpolate the 4.5 mm clearance holes with a 2D Profile toolpath, Inside
  - start depth 0.315 in
  - final depth should just break through the MDF into the plywood by about 0.020 in
  - if actual MDF thickness differs from nominal, second-tool cut depth = MDF thickness + 0.020 in − 0.315 in

Important detail: the 1/8 in cutter has enough flute length for this because the 10 mm recess is machined first. The smaller cutter begins from the pocket floor rather than from the original MDF surface.

## 3. Aspire / gSender / ATC workflow

- Controller/firmware choice: grblHAL.
- Normal flat-table jobs use the ATC postprocessor.
- Rotary jobs use the ATC Rotary Wrap Y postprocessor.
- Current permanent ATC numbering started as:
  - T1 = 1/4 in SpeTool upcut
  - T2 = 1/8 in SpeTool O-flute
- Tool numbers should be stored in Aspire's Tool Database for the AltMill machine profile so selecting the tool automatically carries the correct T number.
- For a real ATC job, save both toolpaths into one G-code file with the ATC-capable Sienci postprocessor so the file contains the tool-change commands.
- AutoZero establishes the work coordinate. TLS measures tool length after ATC changes; it does not determine tool diameter for CAM.
- Machine should be homed before ATC rack moves because rack/TLS locations use machine coordinates.

Joinery + ATC travel notes:
- X machine width: about 49.8 in.
- Remaining on-table Y travel with ATC: about 95.25 in.
- Joinery front overhang adds about 3.7 in of spindle reach, for about 98.95 in total geometric Y span.
- A full 96 in sheet can therefore be shifted forward roughly 1.5–2 in and still be cut over its full length.

## 4. ATC hardware details learned

### ISO20 / ER20 tool holders
- Do not rely on hand-tightening.
- Snap the ER20 collet into the collet nut first.
- Insert the cutter, thread the nut onto the ISO20 holder, then tighten with the supplied two-wrench set.
- Keep cutter stick-out only as long as necessary.
- Do not tighten an empty ER20 collet.

### First ATC test procedure
Not yet completed at the time of this log. Planned sequence:
1. Confirm air supply and pressure.
2. Home the machine.
3. In gSender ATC tab, command Load T1.
4. Verify rack pickup and TLS probing.
5. Command Load T2 and watch T1 return to slot 1, T2 pickup, and TLS probing.
6. Use E-stop immediately if alignment is clearly wrong.

### E-stop pendant
The three small black buttons attached to the E-stop are normal job-control buttons, not additional emergency stops. Default functions are Resume, Pause, and Stop. The red mushroom remains the actual emergency-stop control.

## 5. ATC pneumatic setup

Parts identified from the supplied Sienci kit:
- large green/black unit with gauge = air filter/regulator
- stainless part with blue lever = manual quick-disconnect/shutoff ball valve
- orange collars = 8 mm push-to-connect pneumatic fittings

Correct air path:

```text
Gweike screw compressor
        ↓
blue-handled shutoff valve
        ↓
Sienci filter/regulator IN
        ↓
Sienci filter/regulator OUT
        ↓
8 mm line through AltMill
        ↓
ATC spindle
```

Key details:
- Keep the filter/regulator upright with the bowl and drain downward.
- Do not connect the ATC line to the drain at the bottom of the bowl.
- Final regulator output for the ATC should be about 90–100 PSI, approximately 0.62–0.69 MPa.
- The large compressor can provide a higher upstream pressure (for example around 0.8–1.0 MPa if within the ratings of the hose/fittings/regulator), but the ATC itself should receive the regulated 90–100 PSI supply.
- Cut pneumatic tubing square and push it fully into the orange push fittings.

## 6. Surfacing-bit status

A purchase search found that a BINSTAK spoilboard surfacing bit was ordered and shipped from Amazon in February 2025:
- 1 in cutting diameter
- 1/4 in shank
- carbide-tipped spoilboard/slab-flattening cutter

Conclusion for the current AltMill:
- It is adequate for surfacing the 4×8 MDF spoilboard.
- A more expensive/larger surfacing bit mainly buys faster coverage, better balance/manufacturing, better carbide, and sometimes replaceable inserts; it does not inherently create a flatter plane.
- Flatness is more dependent on spindle tram, runout, cutter condition, and the surfacing toolpath.
- A wider cutter can make tram error more visible by leaving ridges if the spindle is tilted.
- The Sienci ATC/ER20 setup accepts up to a 1/2 in shank; 5/8 in and 3/4 in shank surfacing cutters are not appropriate for this spindle.
- Future upgrade, if needed for productivity: an indexable surfacing cutter around 1.5–2 in diameter with a 1/2 in shank.

For the first surfacing pass, use a light cut and inspect whether the entire board cleans up before removing more MDF.

## 7. Open items / next checks

- Measure actual MDF thickness before finalizing the clearance-hole breakthrough depth.
- Measure the actual #8 screw-head diameter before permanently locking the 10 mm pocket diameter.
- Physically install the Sienci regulator/valve and verify no air leaks.
- Set final ATC regulator pressure and confirm the spindle pressure indicator.
- Complete a manual T1 → T2 → T1 ATC test before running the spoilboard G-code.
- After the board is permanently screwed down, surface the MDF and inspect for tram ridges before taking deeper passes.
