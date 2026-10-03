# AltMill 4×8 Commissioning / ATC Debug Log — 2026-10-02

This log records the trial-and-error work completed while commissioning axis motion, homing, and the Sienci ATC on the AltMill 4×8.

## 1. Y-axis scaling / aggressive homing fault — solved

### Symptom
- Initial homing was extremely aggressive and the gantry/arms slammed into the stops.
- X motion appeared normal.
- A commanded 100 mm Y move produced about 400 mm of physical travel.

### Cause found
The two Y-axis motor drivers were set to the wrong microstep DIP configuration:
- **Wrong Y setting:** OFF OFF ON ON ON
- This is the Z-style 1/4-step configuration.
- **Correct X/Y setting:** OFF OFF OFF ON ON
- **Correct Z setting:** OFF OFF ON ON ON

The exact 4:1 physical-motion error was consistent with the 1/4 vs 1/16 microstep mismatch.

### Corrective action
- Changed both Y motors to OFF OFF OFF ON ON.
- Confirmed X was already OFF OFF OFF ON ON.
- Confirmed Z was OFF OFF ON ON ON.
- Retested measured travel on X, Y, and Z.
- All three axes now move the commanded distance accurately.
- Retested homing; the violent/aggressive homing behavior disappeared.

## 2. Initial ATC setup and first rack pickup failure

### First setup
- Completed the Sienci ATC setup wizard successfully.
- Wizard ran through rack/TLS calibration without reporting an error.
- Initial gSender version was **1.6.1**.

### Failure
- When probing/loading Tool 1, the spindle did not line up with the holder.
- First observed error was mainly in **Y**, several centimetres too far toward the rear.
- The spindle pushed the holder out of position and the operation was aborted.

### Software finding
- gSender 1.6.1 was behind Sienci's later ATC fixes.
- Updated to **gSender 1.6.4**.
- Reran the complete ATC setup wizard.

## 3. Second ATC calibration: Y improved, X then appeared wrong

After recalibration in gSender 1.6.4:
- Y alignment looked much better.
- Tool 1 pickup then appeared about **15 mm too far left in X**.
- Repeated pickup attempts were aborted before damage.

Physical rack mounting was checked and appeared correct:
- 6-tool rack in the correct 4×8 arrangement.
- Rack position/mounting visually consistent with Sienci instructions.
- The large X error could not be explained by the rack simply being slightly out of position.

## 4. ATC keep-out zone discovered

While investigating the ATC position, manual jogging appeared to stop in the rear-right part of the machine.

Observed approximate boundary:
- X ≈ **611.93 mm**
- Y ≈ **-151.2 mm**

This initially looked like a soft-limit problem, but was identified as the **ATC rack keep-out zone**.

Conclusion:
- This is intentional collision protection around the rear-right ATC area.
- It is not evidence that the machine has lost X/Y travel.
- Keep-out should normally remain enabled.
- Disable it only temporarily and deliberately for controlled diagnostics with Z safely raised.

## 5. Rack-coordinate verification

The stored Tool 1 rack coordinate was inspected.

Important value:
- **G59.1 X = 694.43 mm**

Manual movement to machine X = 694.43 aligned the spindle approximately with Tool 1.

Y also looked close, although visually it may have been about **5 mm too far toward the rear**. This remains worth checking later, but it was not large enough to explain the earlier major failures.

Important finding:
- During an automatic probe/load attempt, gSender also reported approximately **X = 694.43 mm**.
- Therefore the stored rack X coordinate itself did not appear to be 15 mm wrong.

This created an unresolved contradiction at the time:
- reported machine coordinate looked correct,
- but physical alignment had appeared wrong.

## 6. Homing-repeatability investigation

Because the same nominal machine coordinate appeared to land differently after some homing cycles, homing repeatability became a suspect.

A pointed V-bit was manually loaded into the ATC spindle and used as a physical reference.

### Manual ATC load/unload confirmed
Current gSender 1.6.4 behavior:
- **Long-press Load** = manual load workflow.
- **Long-press Unload** = manual unload workflow.
- During manual unload, support the ISO20 holder by hand before pressing the physical spindle release button; the holder can release immediately.

Both manual load and manual unload were tested successfully.

### Pointed-bit homing test
Initial test method:
- home machine,
- move to approximately X300 / Y-300,
- mark position,
- repeat.

During the first round, a work zero was changed. The next move to the same displayed X/Y landed at a different physical mark, especially in Y.

After that:
- repeated homing cycles consistently returned to the same marked position with no obvious visible difference.

### Interpretation
The one-time shift during this test may have been caused by changing the **work coordinate zero**, not by a change in physical homing.

This means the pointed-bit experiment does **not yet prove** that homing had previously been drifting.

For a definitive test, repeat using only machine coordinates:
- home,
- command a fixed **G53** position,
- mark it,
- re-home,
- command the same G53 position again,
- do not change X0/Y0/Z0 during the test.

## 7. Work coordinates vs ATC machine coordinates

Important distinction established:

- Normal X0/Y0/Z0 changes the **work coordinate system** (normally G54).
- The ATC rack uses stored rack coordinates and **G53 machine-coordinate moves**.
- Therefore ordinary work-zero changes should **not directly alter ATC rack pickup positions**.

However, changing work zero can make manual diagnostic moves appear inconsistent if work coordinates and machine coordinates are mixed during testing.

This is now considered a likely source of confusion in some of the manual position checks, but it does not fully explain the original automatic ATC misses.

## 8. Current status

At the end of the session:
- X/Y/Z commanded travel is correct.
- Homing no longer behaves aggressively.
- Repeated pointed-bit homing tests currently appear repeatable.
- gSender is updated to **1.6.4**.
- ATC setup wizard has been rerun successfully.
- Manual ATC load/unload works.
- ATC rack keep-out behavior is understood.
- G59.1 Tool 1 X = **694.43 mm** has been independently checked.
- Two later ATC probe/load tests completed **successfully and aligned correctly**.

## 9. Current best conclusions

### Solved / understood
- 4× Y travel and violent homing: wrong Y microstep DIP settings.
- Rear-right travel restriction: ATC keep-out zone.
- Manual ATC load/unload procedure.
- Work-zero changes can alter ordinary displayed/commanded positions and confuse manual diagnostics.
- Current ATC calibration can successfully pick up/probe tools.

### Not yet proven
- A persistent mechanical homing-repeatability fault has **not** been demonstrated.
- A persistent rack-calibration error has **not** been demonstrated.
- The earlier 15 mm apparent X miss is still unexplained because the stored and reported machine X coordinate appeared correct.

## 10. Open questions / next tests

1. **Definitive homing repeatability**
   - Use a pointed tool and a fixed **G53** machine-coordinate target.
   - Repeat 5–10 home cycles without changing work zero.
   - Target repeatability: ideally within ~0.1 mm or better.

2. **If ATC misalignment happens again**
   - Do not immediately change calibration.
   - Record:
     - machine-coordinate DRO,
     - `$#` output,
     - G59.1 values,
     - active modal state with `$G`,
     - exact physical direction/magnitude of the miss.
   - Generate a gSender diagnostic report before resetting/reconfiguring if possible.

3. **Verify small Y offset**
   - Recheck whether the stored G59.1 Y position is actually centered on Tool 1.
   - The observed ~5 mm rearward visual offset may or may not be meaningful.

4. **Determine cause of the earlier intermittent ATC misses**
   - Possibilities still include transient controller/gSender state during commissioning, an earlier 1.6.1 ATC setup issue, or coordinate-system confusion during diagnostics.
   - Current evidence is insufficient to identify a single cause with confidence.

## 11. Operating rule going forward

Until the cause of the earlier intermittent miss is understood:
- home before ATC operation,
- use machine coordinates for ATC diagnostics,
- avoid changing work zero during repeatability tests,
- keep ATC keep-out enabled during normal operation,
- abort immediately if a rack approach is visibly misaligned.
