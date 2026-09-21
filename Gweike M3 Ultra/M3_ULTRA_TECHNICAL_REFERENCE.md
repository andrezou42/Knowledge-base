# Gweike M3 Ultra — technical reference

Sources: the uploaded complete Gweike M-Series manual set (15 manuals, 138 pages); *Installation Preparation Guide M3 Ultra*; and *3 kW Screw Air Compressor Manual (EN)*. This note separates documented facts from observations and unresolved details. Check the installed machine and compressor nameplates before changing settings.

## Assist-gas inputs and routing

| M3 input | Installation-guide maximum inlet pressure |
|---|---:|
| Nitrogen (N₂) | 2.5 MPa |
| Compressed air | 1.6 MPa |
| Oxygen (O₂) | 0.8 MPa |

The installation guide requires clean, oil-free, water-free gas. It specifies external pressure-reducing valves for bottled N₂ (regulator output range 0.2–3.0 MPa) and O₂ (0.05–1.2 MPa); it does not explicitly require a separate external regulator for compressed air. Regulator ranges are component capabilities, not permission to exceed M3 inlet limits. The M-Series connection instructions show 8 mm white tubing to the rear N₂ and O₂ connections, with settings of 2.0 MPa N₂ and 0.8 MPa O₂. The preparation guide also lists a 1.0 MPa nominal liquid-O₂-system output, conflicting with its 0.8 MPa O₂ inlet maximum; confirm the intended configuration with Gweike before using that figure.

For flatbed **CNC fiber cutting**, the M-Series head-installation instructions say to remove the **black air pipe** from the fiber head, park it on its clip, and connect the **white hard air pipe** from the platform pneumatic circuit. For **handheld cleaning/welding**, remove the white pipe and reconnect the black pipe. The manuals therefore do not identify these as separate N₂ and O₂ hoses. Gas selection/control occurs upstream of the white CNC head line. The manuals distinguish the black air pipe from the armored optical-fiber cable; do not identify every black gantry line as pneumatic by appearance. Keep the fiber cable's bend diameter greater than 20 cm.

Before removing the fiber head, close the main air-pressure valve and use **Purge** to release trapped gas. The pendant offers **Air Blowing** (with external gas connected and on); the software offers **Layer → Run Parameters → Select Gas → Blowing test**. The photographed EPV2-50312 is an electro-pneumatic proportional regulator associated with gas control; its exact upstream pressure and plumbing on this unit remain unverified.

## 3 kW screw compressor

The compressor manual describes configurable **loading** and **unloading** pressure: the unit loads when pressure drops to the loading setpoint and unloads at the unloading setpoint. Its page-16 controller illustration (approximately 0.65/0.80 MPa) is an example, not a required setting for this compressor. Do not exceed the compressor's **nameplate exhaust-pressure rating**. The package diagram includes filtration and a cold dryer; maintain them and verify delivered air meets the M3's dryness and cleanliness requirement. The manual calls for pressure-rated piping and a ball valve between the tank and machine.

**Compressor/tank pressure, M3 inlet pressure, and process/head pressure are different quantities.** The M3 compressed-air inlet limit of 1.6 MPa establishes neither a required compressor setting nor the safe pressure for every downstream branch. A 1.5 MPa compressor rating does not establish a universal 1.35–1.5 MPa operating setpoint.

## CO₂ system and unresolved air assist

The M-Series CO₂ workflow documents focusing, exhaust fan, water chiller, CO₂ switch/mode, parameter import, framing, and cutting. The official manuals confirm a **500 W exhaust fan**; they do not identify a dedicated built-in CO₂ air-assist pump or describe how to switch one on. The exhaust fan is distinct from nozzle air assist. Distributor claims about built-in assist may be configuration-specific.

The owner observed cleaner CO₂ cuts after manually feeding the CO₂-head tube from the compressed-air system at about **0.6 MPa**. This is an observation, not a documented Gweike CO₂ setting or proven rating for that tube/nozzle. The official documents reviewed do not establish (a) where this machine's small CO₂ nozzle line originates, (b) whether this unit has an undocumented low-pressure pump, or (c) the CO₂ circuit's maximum inlet pressure. Trace the installed line and obtain its rating or Gweike confirmation before treating the improvised connection as a standard setup. Do not apply the M3's 1.6 MPa compressed-air **input** limit to the small CO₂ tube.

## Source pointers

- *Complete Gweike M-Series manual set* (uploaded ZIP): fiber-head installation and handheld conversion; gas connection; pendant and software blowing controls; CO₂ cutting workflow.
- *Installation Preparation Guide M3 Ultra* (uploaded PDF): assist-gas inlet limits, purity requirement, bottled-gas regulator specifications, exhaust-fan specification.
- *3 kW Screw Air Compressor Manual (EN)* (uploaded PDF): package flow diagram (p. 6), pressure controller example (p. 16), loading/unloading operation and nameplate-pressure warning.

The source files were supplied in the prior conversation and are not reproduced here.

