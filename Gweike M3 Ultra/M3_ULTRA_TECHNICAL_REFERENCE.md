# Gweike M3 Ultra - technical reference

_Last revised: 2026-09-20_

Purpose: a machine-specific quick reference so routine setup, troubleshooting, mode changes, and compressor questions can be answered without rereading the complete manuals.

Primary sources used here:

- Gweike M-Series User Manual set (15 PDFs, 138 pages)
- Gweike M3 Ultra Installation Preparation Guide
- 3 kW Screw Air Compressor Instruction Manual (English)

Source hierarchy: items marked **Manual-confirmed** come directly from the supplied Gweike documents. Items marked **Observed / unresolved** are from this machine, prior testing, or component identification and should not be treated as factory specifications.

---

## 1. Machine / installation quick facts

### Physical installation

**Manual-confirmed**

- Installation-guide drawing gives an approximate machine envelope of **2185 mm wide x 1190 mm deep x 1098 mm high**.
- Keep **at least 1.2 m clearance on all sides** according to the Installation Preparation Guide. The unpacking guide says at least 1 m; use the stricter 1.2 m value when planning space.
- Floor flatness: **within +/-10 mm**.
- Floor loading: **more than 500 kg/m2**.
- Avoid strong nearby vibration; the guide calls for vibration isolation / a seismic ditch if necessary.
- Recommended environment: **0 C to 40 C**, well ventilated, low dust, non-corrosive, no leaks.
- Keep the control unit, servo system, and display away from strong electromagnetic interference. The guide specifically says to keep the machine away from arc welding and EDM equipment.
- Avoid one-sided heating from direct sunlight or strong drafts that could thermally distort the machine.
- Provide suitable fire extinguishers and unobstructed fire exits.

**Material-area note:** the installation-preparation materials table lists a **1300 x 900 mm** material area. Treat that as the preparation-guide material size, not as a definitive statement of the full CNC travel envelope.

### Electrical

**Manual-confirmed**

- M3 machine power: **<=5 kW**.
- Supply: **220-240 V, 50/60 Hz**.
- Installation guide specifies **6 mm2 cable** for the machine supply.
- Commissioning connection guide calls for protected circuits / air switches rated **>=30 A** for the bed and for the voltage-stabilizer / laser circuit in the illustrated single-phase arrangement.
- The installation guide requires a **stabilized power supply** for the laser system and specifies line-voltage fluctuation under 5 percent.
- **Do not power the air compressor or exhaust fan through the laser's regulated / stabilized supply.** The guide warns that their load changes can disturb laser power.
- Protective earth resistance should be **<4 ohms**.
- The machine has a **built-in 500 W smoke-exhaust fan** with about **5 A starting current**. The installation guide says to start the exhaust fan before initiating the laser welder to reduce breaker-tripping risk.
- Wiring is to be performed by a qualified electrician.

### Computer / control connection

**Manual-confirmed**

- Windows only; the supplied manuals explicitly say Apple/macOS is not supported.
- Installation Preparation Guide: Windows 10/11, Ethernet port, i3-class processor or better, **8 GB RAM or more**.
- CNC-to-PC communication is by **Ethernet**.
- The wireless control handle uses **two AAA batteries** plus a USB receiver connected to the PC.

---

## 2. Cooling, exhaust, and fire protection

### Water chiller / CO2 tube

**Manual-confirmed**

- Use **distilled or purified water**. Do not use mineral water.
- Initial fill stated in the manuals: about **7 L** to the green level.
- Installation guide: high-temperature setpoint may be **30 C**; low-temperature setpoint typically **20-25 C**, adjusted for season / ambient conditions.
- Below 0 C ambient, use antifreeze based on **ethylene glycol or propylene glycol**.
- **Do not use alcohol or corrosive antifreeze.**
- Before CO2 cutting, verify the laser tube is full of circulating water and has **no bubbles**.

### Exhaust / receiving cart

**Manual-confirmed**

- Connect the smoke-exhaust duct during installation.
- The material-receiving cart should contain flame-resistant sacrificial material such as **sand, gravel, fireproof brick, marble slab, or metal plate**, to protect the lower sheet metal from heat and sparks.

---

## 3. Gas inputs: limits, purity, and routing

### M3 rear gas-input limits

**Manual-confirmed - Installation Preparation Guide**

| M3 input | Maximum inlet pressure |
|---|---:|
| Nitrogen (N2) | **2.5 MPa** |
| Compressed air | **1.6 MPa** |
| Oxygen (O2) | **0.8 MPa** |

- Gas must be **clean, oil-free, and water-free** at the machine inlet.
- The connection guide shows **8 mm white pneumatic tubing** from the gas regulators to the corresponding rear machine inlets.
- Commissioning settings shown by Gweike: **N2 = 2.0 MPa**, **O2 = 0.8 MPa**.
- Installation guide purity requirements: **N2 >=99.99%**, **O2 >99.6%**.

### External bottled-gas regulators

**Manual-confirmed**

- Nitrogen regulator listed for preparation: input >=15 MPa, adjustable output **0.2-3.0 MPa**.
- Oxygen regulator listed for preparation: input >=15 MPa, adjustable output **0.05-1.2 MPa**.
- These regulator output ranges are component capabilities; they do **not** override the M3 inlet limits above.

### Liquid-gas supply figures and an O2 inconsistency

The Installation Preparation Guide gives these liquid-gas-system examples:

- O2 vaporizer: about **1.0 m3/min**, output **1.0 MPa**, purity >99.6%.
- N2 vaporizer: about **1.5 m3/min for <=3 kW**, 2.2 m3/min above 3 kW, output **2.0 MPa**, purity >=99.99%.

**Important:** the same guide also states the M3 O2 inlet maximum is **0.8 MPa**, and the connection guide tells the installer to set O2 to **0.8 MPa**. Treat **0.8 MPa as the machine-side limit** unless Gweike provides a machine-specific revision saying otherwise.

---

## 4. Fiber-head pneumatic architecture - black vs white tubing

This resolves an earlier point of confusion.

### Normal flatbed CNC fiber configuration

**Manual-confirmed - Installing Laser Source**

1. The fiber head is installed on the crossbeam.
2. The **black air pipe is removed from the laser head and parked on the clip** at the right side of the head.
3. The **white hard air pipe from the platform pneumatic circuit is connected to the laser head**.
4. The height-adjuster signal cable is connected.
5. The optical-fiber cable is secured so that it cannot be pinched or sharply bent.

Therefore the black and white tubes are **not documented as separate N2 and O2 hoses**. Gas selection happens upstream; the CNC head receives the selected platform gas through the white hard line.

### Fiber-optic cable handling

**Manual-confirmed**

- Minimum optical-fiber bend diameter: **>20 cm**.
- After installing the head, move it to the far right and move the gantry through its travel to verify the fiber cable moves freely, without squeezing or tight bends.

### Converting the fiber head to handheld cleaning / welding

**Manual-confirmed - Laser Head Disassembly and Cleaning Function**

Before removal:

1. Close the **main air-pressure valve**.
2. Click **Purge** to release residual gas in the machine.
3. Power off the equipment and disconnect the network cable.
4. Remove the signal-amplifier cable and **white air pipe**.
5. Reconnect the **black air pipe** to the head.
6. Remove the head and fiber assembly from the machine and connect the laser signal cable to the welding-machine interface.

This is the clearest factory documentation for the black air line seen near the carriage.

---

## 5. Internal gas control / air test controls

**Manual-confirmed**

- The wireless pendant includes **Air Blowing**. The manual says an external gas source must be connected and turned on first.
- Software gas test path: **Layer -> Run Parameters -> Select Gas -> Blowing test**.
- Calibration / flying-cut instructions explicitly tell the operator to perform a blowing test before cutting.

**Observed / component identification**

- The photographed L&T **EPV2-50312** is an electro-pneumatic proportional pressure regulator, not a compressor. It is consistent with an electronically controlled assist-gas circuit.
- Exact upstream plumbing and pressure supplied to this EPV on this particular M3 Ultra have not yet been traced.

---

## 6. CO2 air assist - what the factory manuals do and do not say

**Manual-confirmed**

The complete M-Series manual set documents CO2 focusing, chiller operation, exhaust fan, CO2 power switch, software mode, parameter import, framing, and cutting. It does **not** identify a dedicated built-in CO2 air-assist compressor, does not give a CO2 nozzle-air pressure specification, and does not document a control for switching such a pump on.

Therefore:

- The **500 W built-in fan is exhaust**, not nozzle air assist.
- A separate built-in CO2 assist pump remains **unconfirmed by the supplied Gweike factory manuals**.
- Do not assume the M3's 1.6 MPa compressed-air inlet limit is the safe pressure of the small CO2 nozzle tube.

**Observed / unresolved**

- On this machine, manually feeding approximately **0.6 MPa** compressed air into the CO2-head air line produced visibly cleaner cuts than the previous setup.
- That is a useful empirical observation, but **0.6 MPa is not documented by Gweike as the approved CO2-head pressure** in the supplied manuals.
- Still unresolved: where the small CO2 air line originates, whether there is an undocumented low-pressure pump on this unit, and the maximum pressure rating of the CO2 branch.

---

## 7. Software installation and configuration

### Initial setup

**Manual-confirmed - Installation of Software**

1. Power-on order used in commissioning: **main power -> voltage stabilizer -> laser -> machine tool**.
2. Copy the supplied software from the USB drive to the PC.
3. Install **vcredist_X86** runtime.
4. Open the main application, choose **online mode**, password **3721**.
5. Import the machine/platform configuration XML using:
   **Start -> Parameter Recovery -> Import Parameters from File**.
6. Connect PC and CNC by Ethernet.
7. Install batteries in the wireless handle and connect its receiver.
8. Configure the local IP / auto-recognition and restart hardware.
9. On reconnect, the machine automatically homes toward the **left-front**. If it moves in the wrong direction, use the emergency stop immediately.

### Important passwords found in the supplied manuals

| Function | Password |
|---|---:|
| Main app / platform configuration / lead changes | **3721** |
| Air-cooled welding machine advanced parameters | **2000** |
| Welding-machine cleaning mode | **5000** |
| Laser-source detection software engineer login | **123456** |

These are documented service / setup passwords. Record changes before altering machine configuration.

---

## 8. Wireless pendant - practical cheat sheet

**Manual-confirmed**

Useful pendant functions include:

- X/Y jog: left, right, forward, backward.
- Rapid / step movement toggle.
- **Follow On / Follow Off** for capacitive height following. If following is poor or the stand-off is excessive, perform head calibration before use.
- **Shutter On / Off** - prerequisite for fiber laser emission.
- **Laser spot fire** - shutter must first be on; after spot firing the shutter automatically closes.
- Red-light control.
- **Air Blowing** - test external gas flow.
- **Trace Border / Frame** - verify drawing location and material fit before processing.
- Fn + Z controls Z-axis up/down.
- Fn + W controls platform movement for taller work such as bent parts / square tube.
- Fn + Go to Origin - quick return to cutting origin.
- Fn + Z-Calibrt - quick laser-head calibration.
- Start / Pause / Stop processing.

---

## 9. Fiber CNC cutting - normal workflow

**Manual-confirmed - Cutting and Carving**

1. Place material and close the cover.
2. Turn on required process gases. The manual's commissioning example uses **N2 2.0 MPa** and **O2 0.8 MPa**.
3. In software choose **Fiber Cutting** mode.
4. Open the drawing.
5. Import the corresponding material/thickness process file.
6. Sort small geometry first and simulate the toolpath.
7. Perform quick head calibration.
8. Run an air/gas blowing test to verify the path is open.
9. Frame / trace the border and confirm the red light lies on the material.
10. Start cutting.

### Parameter-file naming conventions

The manual explains examples such as:

- SS = stainless steel
- 2.0 mm = sheet thickness
- 2.0S = 2.0 single nozzle
- F0 = focus position 0
- N2 / O2 / AIR = assist gas

This naming convention is useful when selecting the supplied process files.

### Fiber engraving + cut in one job

**Manual-confirmed**

- Select marking geometry -> **Common -> Scan Engraving -> Convert to Marking Drawing**.
- Put engraving and cutting geometry on different layers/colors.
- Use manual sorting so **engraving happens before cutting**.
- Manual gives a marking-speed example of about **300-800 mm/s** for the engraving layer; import the actual cutting process for the cut layer based on material/thickness.

---

## 10. Fiber-head calibration and flying cutting

### Floating-head calibration

**Manual-confirmed**

- Always place a **metal plate under the fiber head** before calibration.
- Software path: **System Analysis -> FTC -> Floating-head Calibration**.
- The head descends and senses the metal automatically.

### Flying cutting

**Manual-confirmed**

- Arc flying cutting is shown for repeated circles.
- Straight flying cutting is shown for repeated rectangular geometry.
- Flying cutting is intended for **batch cutting of regular/repeated graphics**.
- Irregular geometry may not meet the flying-cutting conditions and the software will reject it.
- Simulate before processing and run the gas blowing test.

---

## 11. CO2 flatbed cutting / engraving - normal workflow

**Manual-confirmed - Cutting and Carving**

### CO2 cutting

1. Use the **built-in focusing tool** to set CO2 focus.
2. Turn on **fan -> water chiller -> CO2 switch**.
3. Confirm the CO2 tube is filled with water and contains no bubbles.
4. Software: **Start -> CO2 Laser**.
5. Import the drawing.
6. Assign colors/layers and import material-specific CO2 parameters.
7. The manual uses the **first green layer for engraving** and other colors for cutting.
8. Sort small geometry first.
9. Simulate.
10. Trace the border / frame.
11. Start.

### CO2 engraving + cutting

- Convert engraving geometry using **Scan Engraving -> Convert to Marking Drawing**.
- Put engraving and cutting on separate layers.
- Manually sort so **engraving occurs before cutting**.
- The manual again gives a marking-speed example of **300-800 mm/s** for the engraving layer, with cutting parameters imported according to material and thickness.

The manual does not add a CO2 air-assist step to this workflow.

---

## 12. Handheld fiber modes

These pressure values are mode-specific recommendations from the M-Series manuals. They are **not universal fiber-cutting pressures**.

### Handheld cleaning

**Manual-confirmed**

- Gas: nitrogen, compressed air, or argon.
- Recommended pressure: **0.5 MPa**.
- Cleaning-mode password: **5000**.
- The test setup places the gun head about **120 mm from the plate** and recommends holding it at an angle rather than perpendicular.
- Ground connection is required as shown in the manual.

### Handheld welding

**Manual-confirmed**

- Wire feeder and its signal cable are required; the manual notes the machine may alarm if the wire-feeder signal is not connected.
- Welding-tip / copper-cap bore should match wire diameter.
- Gun-head focal setting is generally shown as **+3**.
- Recommended assist-gas pressure: approximately **0.2 MPa**.
- Ground clamp goes to the conductive work platform.
- Select material and thickness on the welding interface, then enable wire feed, laser, and red light.

### Handheld cutting

**Manual-confirmed**

- Remove the wire-feed assembly and install the **cutting-specific nozzle**.
- Recommended air pressure: approximately **0.6 MPa**.
- Set scanning width to **0**.
- Set wire-feed mode to manual.
- Ground to a conductive metal work platform.
- Start the cut from the **edge of the plate** to reduce blowhole-related damage.

---

## 13. CNC cleaning, quenching, and welding on the flatbed

### CNC cleaning

**Manual-confirmed**

- Set the head geometry so the plate is **120 mm from the center of the side screw hole of the gun head**.
- Shield the height adjuster, disconnect its cable, remove the extension tube from the cutting head, and raise the CO2 head to its highest position.
- Welding-machine advanced-parameter password: **2000**; the procedure changes stop-delay time.
- Switch welding-machine interface to cleaning mode with password **5000**.
- Recommended maximum frequency: **60 Hz**.
- Recommended maximum swing width for cleaning: **20 mm**.
- Example line spacing: about **18 mm**, slightly less than the 20 mm swing width.
- Use straight-line flying cutting for the raster-like passes.
- Recommended gas pressure: **>1.0 MPa**.

### CNC quenching

Same general setup as CNC cleaning, but:

- Recommended maximum frequency: **60 Hz**.
- Recommended maximum swing width: **10 mm**.
- Gas pressure recommendation: **>1.0 MPa**.
- Power is selected according to plate thickness and desired quenching hardness.

### CNC welding

**Manual-confirmed**

- Install the welding-specific nozzle.
- Nozzle-to-work distance: approximately **3-5 mm**.
- Recommended gas pressure: **0.3 MPa**.
- Frequency and swing are adjusted on the welding-machine interface; the CNC cutting software controls speed/power for these converted workflows.

### After CNC cleaning / quenching / welding mode changes

**Manual-confirmed**

- Do **not** immediately command a normal return-to-origin after modified configurations.
- The flatbed manual recommends returning the **X axis separately first**, then Y where applicable.
- Restore the welding-machine stop-delay setting after the operation.
- Re-import the original platform/process parameters or restore the modified settings.

---

## 14. Rotary-axis setup

Rotary work reuses an existing machine-axis drive rather than adding an independent always-connected rotary axis.

### Rotary fiber / CO2 cutting and marking

**Manual-confirmed**

- For the fiber/CO2 rotary cutting and marking workflows, disconnect the **Y-axis driver motor and encoder cables** and connect the rotary-axis motor/encoder cables.
- Position the rotary axis **parallel to X**.
- Rotary lead formula shown by Gweike:
  **lead = pi x D x (26/48)**
  where D is work diameter; the manual says adjust gear ratio if the actual hardware differs.
- Enter platform configuration with password **3721** to change the lead.
- For rotary tube cutting, the flattened drawing width equals the tube circumference **pi x D**; the other dimension corresponds to the required tube length.
- Fiber rotary cutting / marking examples recommend about **0.3 MPa** air pressure.
- For CO2 rotary mode, manually set focus using the CO2 focal-length ruler.

### Rotary CNC cleaning / quenching / welding

**Manual-confirmed**

- These workflows instead disconnect the **X-axis driver** and connect the rotary axis there.
- Position the rotary axis **parallel to Y**.
- The same lead formula and password 3721 are used.

### Critical restore warning

After rotary configuration changes:

- Do not immediately use a normal global return-to-origin.
- The manuals repeatedly recommend returning **X to origin separately first** (and then Y where applicable).
- Re-import original parameters / restore the original lead and platform configuration after rotary work.

---

## 15. Laser-source diagnostic software

**Manual-confirmed**

- Use the supplied **USB-to-RS232** cable: 9-pin connector to laser, USB to computer.
- Open the laser-detection software.
- Engineer password: **123456**.
- COM port is intended to auto-detect. If it fails, try another USB port or PC.
- Real-time laser status is available in the main interface.
- Previous alarms are viewed under **LOG** / offline records.
- The software also exposes laser usage time / decrypt functions.

---

## 16. 3 kW screw compressor - installation and electrical reference

The compressor PDF is a screw-compressor-series manual. Confirm the actual unit nameplate before applying a generic table value.

### Electrical table for the 3 kW model

**Manual-confirmed**

- Motor: **3 kW**.
- Table supply: **240 V**.
- Table current: **23 A**.
- Cable: **6 mm2 x 2 + PE**.
- Recommended motor-protection circuit breaker in the table: **63 A**.
- Grounding resistance: **<4 ohms**.
- A separate electrical supply for the compressor is recommended.

### Installation

**Manual-confirmed**

- Clean, dry, ventilated indoor location.
- Ambient temperature should stay **below 40 C and above freezing** during normal use.
- Maintain **>600 mm** clearance from walls/ceiling for service and cooling.
- Install on a solid, level base.
- Main compressed-air piping should slope about **1-2 degrees** to assist condensate drainage.
- Minimize elbows and unnecessary valves to reduce pressure loss.
- Use piping rated for the maximum system pressure.
- Install a **ball valve between the receiver tank and downstream machine/system**.

### Package components / air path

The compressor flow diagram shows an integrated system including:

- intake air filter
- screw air end
- oil / air separator
- oil filter and oil circuit
- cooler / radiator
- receiver tank
- filtration
- **cold / refrigerated dryer**

The M3 requires dry, oil-free air at its inlet. The compressor itself is oil-lubricated, so maintenance of the separator, filters, dryer, and drains is important. The supplied manuals do not give an ISO compressed-air quality class.

---

## 17. Compressor pressure control - loading vs unloading

**Manual-confirmed**

The compressor controller uses two pressure setpoints:

- **Loading pressure:** pressure below which the compressor starts / loads again.
- **Unloading pressure:** upper pressure at which the compressor unloads.

The manual's controller illustration shows **0.65 MPa loading / 0.80 MPa unloading**, but this is a screenshot/example in a generic series manual, **not a stated required setting for the user's 1.5 MPa unit**.

Key rule from the manual:

- **Never operate above the exhaust pressure on the compressor nameplate.**

Do not confuse:

1. compressor load/unload or receiver pressure,
2. M3 rear inlet pressure,
3. internal regulated pressure,
4. actual cutting-head process pressure.

They are different quantities.

---

## 18. Compressor normal operation and shutdown

### Before starting

**Manual-confirmed**

- For a new machine, long-idle machine, or relocated compressor, perform the trial-operation checks.
- Verify pipe joints, instruments, and electrical connections.
- Confirm the exhaust valve is open.
- Check oil level.
- Check cooling system and safety / relief valves.
- Before routine operation, with separator pressure at **0 MPa**, drain condensate from the oil/air separator and close the drain again.

### Automatic operation

- Start button begins preloading and closes the venting solenoid.
- Pressure rises until the unloading setpoint.
- When pressure falls to the loading setpoint, the compressor starts/loads automatically again.

### Normal shutdown

**Manual-confirmed**

- Do not normally press Stop while the unit is loaded; unload first.
- Use the normal Stop button. The controller performs a shutdown countdown.
- After the compressor stops, wait about **2-3 minutes for the inverter fan to stop** before switching off main power.
- Do not use the emergency stop or abruptly cut power except in an actual emergency; the manual warns this can cause oil injection or faults.

---

## 19. Compressor protection / alarm values

**Manual-confirmed**

- High exhaust-temperature warning: **105 C**.
- High exhaust-temperature shutdown: **108 C**.
- Compressor cannot start below approximately **-15 C** ambient according to the controller protection section.
- Safety valve opens if separator-outlet pressure exceeds about **1.1x rated exhaust pressure**.
- Bleed valve opening reference: **rated discharge pressure + 0.15 MPa** when separator restriction creates excessive differential pressure.
- Safety / relief valves are factory adjusted; do not arbitrarily readjust them.

Common major shutdowns listed by the controller include high exhaust pressure, high exhaust temperature, motor/fan overload, phase loss, temperature-sensor fault, and pressure-sensor fault.

---

## 20. Compressor maintenance quick reference

**Manual-confirmed**

### Condensate

- Excessive water can emulsify the compressor oil and damage the air end.
- Drain condensate before the next day's start as required.
- If equipped with the optional electronic drain, the manual suggests timed drainage **2-3 times per day**.
- In high humidity with intermittent operation, the manual calls for regular manual drainage and periodically running the cooling fan.

### Filters / oil

Items monitored by the controller include:

- intake air filter
- oil filter
- oil/air separator element
- lubricating oil

The controller can issue service-life warnings for these items; reset the corresponding service timer after replacement.

### Electronic drain valve

- Use the **TEST** button periodically.
- If little/no water drains, inspect the drain filter.
- Drain-valve filter cleaning interval stated in the manual: **monthly**.
- Depressurize and isolate the valve before service.

### Cooler / inverter cleaning

- Dust buildup in the cooler can drive high exhaust temperature.
- The manual specifies **0.6-1.2 MPa compressed air** for radiator/inverter dust removal.
- Disconnect power first and protect electrical components from debris.
- Wear at least **KN95-level respiratory protection and eye protection** during this dust-cleaning procedure.

### Useful troubleshooting pointers

- High running current: check excessive exhaust pressure, wrong oil, blocked separator, supply voltage, vibration, motor/contactor faults.
- High exhaust temperature: check oil level, oil cooler, dust filter, oil specification, oil filter, fan, temperature-sensor wiring, oil-return restriction.
- High oil content in delivered air: check overfilled separator, return line, separator element, loose assembly, minimum-pressure valve, high temperature, wrong oil.
- Abnormal start / high current with separator pressure above **0.4 MPa**: ensure separator pressure is released before starting; inspect minimum-pressure valve and venting solenoid.

---

## 21. Configuration-change warnings worth remembering

These are easy to forget and can cause confusing behavior later.

**Manual-confirmed**

- Platform configuration password is **3721**.
- Rotary-axis work changes the X- or Y-axis drive assignment and the axis lead. Restore the original configuration afterward.
- Converted CNC cleaning/quenching/welding modes change welding-machine stop-delay and other settings. Restore them afterward.
- The manuals repeatedly warn **not to command a normal full return-to-origin immediately after these configuration changes**. Return the specified axis separately first.
- After parameter experiments, re-import the original parameter file / platform configuration as directed by the manual.

---

## 22. Source discrepancies / items that should not be silently reconciled

1. **Oxygen pressure:** Installation Guide says M3 O2 input <=0.8 MPa; its liquid-O2 example lists 1.0 MPa output. Connection Guide says set O2 to 0.8 MPa. Use the lower machine limit unless Gweike confirms otherwise.
2. **Machine clearance:** Installation Preparation Guide says 1.2 m on all sides; Unpacking guide says at least 1 m. Use 1.2 m for planning.
3. **Compressor pressure:** the generic compressor controller screenshot shows 0.65/0.80 MPa, but this is not proof of the required setpoints for the 1.5 MPa compressor. The nameplate is authoritative for maximum pressure.
4. **CO2 air assist:** the factory manuals supplied do not document a built-in CO2 air-assist compressor or CO2 air pressure. Do not promote distributor claims or the user's 0.6 MPa experiment to a factory specification.

---

## 23. Owner observations / unresolved machine-specific items

These are useful for future troubleshooting but are **not factory specifications**.

- Manually supplying about **0.6 MPa** compressed air to the CO2-head air tube produced cleaner cuts on this machine than the previous low/unknown-air setup.
- The purpose and rating of the small CO2-head air branch still need to be traced.
- Confirm whether the user's machine has any undocumented low-pressure CO2 pump.
- Trace the EPV2-50312's upstream supply and downstream destination.
- Photograph and label the rear gas panel, all gantry pneumatic tube endpoints, and internal gas manifold when convenient.

---

## 24. Source map - where to look if more detail is needed

### Complete M-Series User Manual ZIP

- **1. Unpacking and installation** - initial placement, accessories, exhaust duct, 7 L chiller fill, fire-resistant receiving-cart material.
- **2. Connection guide** - electrical commissioning, voltage stabilizer, N2/O2 tubing, 2.0 MPa N2 and 0.8 MPa O2, switch checks.
- **3. Installing laser source** - optical-fiber routing, >20 cm bend diameter, black vs white air pipe, height-adjuster connection.
- **4. Installation of software** - Windows setup, vcredist_X86, password 3721, XML parameter recovery, Ethernet, homing direction.
- **5. Introduction of handle function** - pendant controls, follow, shutter, spot fire, air blowing, frame, calibration, start/pause/stop.
- **6. Cutting and carving** - normal fiber and CO2 cutting/engraving workflows and parameter-file naming.
- **7. Laser head disassembly and cleaning function** - purge procedure, handheld conversion, 0.5 MPa cleaning gas, password 5000.
- **8. Hand welding** - wire feeder setup, focal +3, 0.2 MPa gas.
- **9. Hand cutting** - cutting nozzle, 0.6 MPa, scan width 0, edge-start warning.
- **10. Calibration + flight cutting** - floating-head calibration, gas blow test, straight/arc flying-cut rules.
- **Laser source detection** - RS232 diagnostic software, engineer password 123456, alarm logs.
- **Rotary axis cutting laser and CO2** - Y-axis drive substitution, lead formula, tube flattening, restore warnings.
- **Rotary axis carving laser and CO2** - rotary marking workflow and 0.3 MPa fiber-marking example.
- **Flatbed CNC cleaning/quenching/welding** - 120 mm setup, passwords 2000/5000, frequency/swing, >1 MPa cleaning/quenching and 0.3 MPa welding.
- **Rotary CNC cleaning/quenching/welding** - X-axis drive substitution, rotary parallel to Y, same restoration warnings.

### Installation Preparation Guide M3 Ultra

Use for site dimensions/clearance, power, grounding, environment, cooling-water requirements, gas inlet limits/purity, and bottled-gas regulator requirements.

### 3 kW Screw Air Compressor Manual

Use for compressor installation, electrical table, load/unload logic, normal stop procedure, protection values, drainage, filters/oil/separator maintenance, electronic drain service, and troubleshooting.

---

## Change log

- **2026-09-20:** Expanded from the complete supplied M-Series manual set, Installation Preparation Guide, and 3 kW compressor manual. Added site/electrical/cooling specs, gas architecture, black/white tube routing, software/passwords, pendant controls, fiber and CO2 workflows, handheld modes, CNC cleaning/quenching/welding, rotary setup, compressor operation/protection/maintenance, and explicit source discrepancies.
