Pi BOX

Bill of Materials (BOM) – Version 1.0

This document lists the hardware components required to build Pi BOX v1.0 based on the frozen architectural decisions. It is intended for:
	•	build planning
	•	procurement tracking
	•	future upgrades
	•	GitHub documentation

The BOM is divided into core, power, network, RF, and expansion-ready sections.

⸻

1. Compute Nodes (Core System)

Item	Quantity	Notes
Raspberry Pi 5 (8 GB or higher)	2	One for core intelligence (pibox-core), one for RF/SDR (pibox-rf)
Raspberry Pi Zero / Zero W	2	One for MMDVM (pibox-dv), one for sensors (pibox-env)
MicroSD cards (32–64 GB)	4	One per Pi; quality, endurance-rated preferred


⸻

2. Power System

Item	Quantity	Notes
12V 10A SMPS	1	Central power supply for entire Pi BOX
DC-DC buck converters (12V → 5V)	4–6	Separate regulation for Pi Zero and Pi 5 zones
Power distribution terminal block	1	Clean star-style power distribution
Inline blade or resettable fuses	Optional	Per-zone protection
Power wiring (appropriately rated)	As required	Short internal runs preferred


⸻

3. Network Infrastructure (Internal Spine)

Item	Quantity	Notes
Ethernet switch (5–8 port, unmanaged)	1	Internal-only network spine
Ethernet patch cables (short)	4–6	Board-to-switch connections
RJ45 panel mount or couplers	Optional	For clean enclosure wiring


⸻

4. LTE / Connectivity (Core Node)

Item	Quantity	Notes
SIM7600 4G LTE modem	1	Data, SMS, voice calling
LTE antennas	2	Diversity/MIMO if supported
SIM card	1	Active plan
USB cable (short, shielded)	1	Pi 5 ↔ LTE modem


⸻

5. Digital Voice (MMDVM Node)

Item	Quantity	Notes
MMDVM hotspot board	1	Connected to Pi Zero (pibox-dv)
UHF/VHF antenna	1	As required by MMDVM configuration
RF coax cables	As required	Short, quality cables


⸻

6. RF / SDR System

Item	Quantity	Notes
SDR transceiver or SDR receiver	1	For SSB, CW, spectrum work
RF frontend (filters, preamps)	Optional	Depending on SDR choice
HF/VHF antennas	As required	External to enclosure
RF connectors and adapters	As required	Minimise conversion stages


⸻

7. Environmental & Weather Sensors

Item	Quantity	Notes
Temperature / humidity sensor	1+	e.g. I2C or SPI
Pressure sensor	Optional	For weather trends
Air quality sensors	Optional	Future expansion
Sensor wiring / headers	As required	Clean GPIO routing


⸻

8. Enclosure & Mechanical

Item	Quantity	Notes
Enclosure (metal or RF-shielded preferred)	1	Space for expansion
Mounting hardware (standoffs, screws)	As required	Non-conductive preferred
Cooling fans (optional)	1–2	Controlled airflow zones
Cable ties / cable management	As required	Internal cleanliness


⸻

9. Monitoring & Safety (Recommended)

Item	Quantity	Notes
Temperature probes	Optional	Power & RF zones
Power monitoring module	Optional	Voltage/current tracking
Grounding straps	Optional	RF noise control


⸻

10. Expansion Reserve (Intentional)

Reserved capacity for:
	•	additional Raspberry Pi nodes
	•	storage (SSD / NVMe via USB)
	•	accelerators
	•	battery backup
	•	additional RF modules

These are not populated in v1.0 but are part of the physical design philosophy.

⸻

BOM Status
	•	Version: 1.0
	•	Scope: Pi BOX v1.0 build
	•	Change policy: update only with documented design revisions

This BOM is a living document but should remain stable during the initial build phase.
