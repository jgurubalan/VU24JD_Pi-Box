Pi BOX

Bill of Materials (BOM) – Version 1.0

Markdown note: This document is written using GitHub Flavored Markdown (GFM).
Tables require one blank line before and after to render correctly on GitHub.

This document lists the hardware components required to build Pi BOX v1.0 based on frozen architectural decisions. It is intended for:
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
MicroSD cards (32–64 GB, endurance-rated)	4	One per Raspberry Pi


⸻

2. Power System

Item	Quantity	Notes
12V 10A SMPS	1	Central power supply for entire Pi BOX
DC–DC buck converters (12V → 5V)	4–6	Separate regulation for Pi Zero and Pi 5 zones
Power distribution terminal block	1	Star-style internal power distribution
Inline blade fuses or resettable fuses	Optional	Per-zone protection
Internal power wiring (appropriately rated)	As required	Short runs preferred


⸻

3. Network Infrastructure (Internal Spine)

Item	Quantity	Notes
Ethernet switch (5–8 port, unmanaged)	1	Dedicated internal network spine
Ethernet patch cables (short length)	4–6	Pi-to-switch connections
RJ45 panel mount or couplers	Optional	Clean enclosure routing


⸻

4. LTE / External Connectivity (Core Node)

Item	Quantity	Notes
SIM7600 4G LTE modem	1	Data, SMS, and voice calls
LTE antennas	2	Diversity / MIMO if supported
SIM card	1	Active data/voice plan
Shielded USB cable (short)	1	Pi 5 ↔ LTE modem


⸻

5. Digital Voice Subsystem (MMDVM Node)

Item	Quantity	Notes
MMDVM hotspot board	1	Connected to pibox-dv
VHF / UHF antenna	1	As required by configuration
RF coaxial cables	As required	Keep runs short


⸻

6. RF / SDR Subsystem

Item	Quantity	Notes
SDR receiver or transceiver	1	For SSB, CW, and spectrum work
RF frontend (filters, preamps)	Optional	Depends on SDR choice
HF / VHF antennas	As required	External to enclosure
RF adapters and connectors	As required	Minimise conversion stages


⸻

7. Environmental & Weather Sensors

Item	Quantity	Notes
Temperature / humidity sensor	1+	I2C or SPI preferred
Pressure sensor	Optional	Weather trend analysis
Air quality sensors	Optional	Future expansion
Sensor wiring and headers	As required	Clean GPIO routing


⸻

8. Enclosure & Mechanical Components

Item	Quantity	Notes
Enclosure (metal or RF-shielded preferred)	1	Space reserved for expansion
Mounting hardware (standoffs, screws)	As required	Non-conductive where possible
Cooling fans	Optional (1–2)	Zoned airflow
Cable management (ties, clips)	As required	Maintain internal order


⸻

9. Monitoring & Safety (Recommended)

Item	Quantity	Notes
Temperature probes	Optional	Power and RF zones
Power monitoring module	Optional	Voltage and current tracking
Grounding straps	Optional	RF noise control


⸻

10. Expansion Reserve (Intentional)

The enclosure, power budget, and network design intentionally reserve capacity for:
	•	additional Raspberry Pi nodes
	•	external or internal storage (SSD / NVMe via USB)
	•	compute accelerators
	•	battery backup and UPS modules
	•	additional RF modules or bands

These items are not populated in v1.0 but are part of the long-term Pi BOX design philosophy.

⸻

BOM Status
	•	Version: 1.0
	•	Scope: Pi BOX v1.0 hardware build
	•	Change policy: Update only with documented design revisions

This BOM is a living document but should remain stable during the initial build phase.
