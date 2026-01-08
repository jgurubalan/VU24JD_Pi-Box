# VU24JD_Pi-Box
Pi BOX

Project Overview and Idea Book

Pi BOX is a modular, multi-node Raspberry Pi–based system designed as a long-term platform for learning, experimentation, communication, and personal automation. The guiding idea behind Pi BOX is to avoid building a single overloaded system and instead create a distributed micro-cluster inside one physical enclosure, where each node has a clear, well-defined role.

This document serves as:
	•	A printable reference for future use
	•	An idea book for ongoing development
	•	A high-level design document suitable for a GitHub repository

⸻

Core Philosophy
	1.	Modularity
Each Raspberry Pi has a single dominant role. Nodes can be added, removed, or repurposed without redesigning the entire system.
	2.	Reliability through Separation
Critical services (radio, sensors, LTE, automation) are isolated so that failure of one node does not cascade to others.
	3.	Educational Transparency
Every subsystem should be understandable, documentable, and reproducible. Pi BOX is as much a learning tool as it is a functional system.
	4.	Future-Proofing
Space, power, and logical addressing are reserved for expansion. Pi BOX is intended to evolve over years.

⸻

Physical Infrastructure
	•	Enclosure: Custom or adapted enclosure with airflow zoning
	•	Power Supply: 12V, 10A SMPS (centralized)
	•	Power Distribution: Internal DC step-down converters for individual nodes
	•	Cooling: Passive by default, with provision for active cooling if required
	•	Expansion Space: Reserved slots for future Raspberry Pi boards, RF modules, storage, or accelerators

⸻

System Architecture (Node-Based Design)

Pi BOX consists of four primary nodes in version 1.0:

Node 1: Pi Zero A — Digital Voice / MMDVM Node
	•	Hardware: Raspberry Pi Zero
	•	Operating System: Raspberry Pi OS (Lite)
	•	Primary Role: MMDVM hotspot

Responsibilities:
	•	Digital voice modes (DMR / YSF / D-STAR as configured)
	•	Stable, low-latency RF timing
	•	Minimal background services for reliability

Design Rationale:
This node is intentionally isolated to ensure uninterrupted digital voice operation without interference from CPU-heavy or network-heavy services.

⸻

Node 2: Pi Zero B — Weather and Environmental Sensors Node
	•	Hardware: Raspberry Pi Zero
	•	Operating System: Raspberry Pi OS
	•	Primary Role: Sensor data acquisition

Responsibilities:
	•	Reading weather and environmental sensors
	•	Local buffering of sensor data
	•	Periodic data transmission to the core node

Design Rationale:
Sensor data collection remains active even if higher-level services are offline. This node is optimized for GPIO and low-power, continuous operation.

⸻

Node 3: Pi 5 A — Core Brain, LTE, and Assistant Node
	•	Hardware: Raspberry Pi 5
	•	Connectivity: SIM7600 4G LTE modem
	•	Primary Role: Central intelligence and control

Responsibilities:
	•	LTE data, SMS, and voice call handling
	•	Integration with LLM services (e.g., OpenAI or local models)
	•	Alert generation and reminder logic
	•	Automated outgoing phone calls
	•	Web hosting (Pi BOX dashboard and APIs)
	•	Control plane for other nodes

Design Rationale:
This node acts as the orchestrator and external interface of Pi BOX. It is the only node intended to have direct internet exposure under normal operation.

⸻

Node 4: Pi 5 B — RF / SDR / SSB / CW Node
	•	Hardware: Raspberry Pi 5
	•	Primary Role: Radio frequency experimentation

Responsibilities:
	•	SDR receiving and transmitting
	•	SSB and CW decoding
	•	Spectrum monitoring and recording
	•	Digital signal processing pipelines

Design Rationale:
RF and DSP workloads are CPU- and I/O-intensive and are isolated to prevent interference with LTE, automation, or digital voice services.

⸻

Inter-Node Communication (Conceptual)
	•	Internal LAN or direct Ethernet
	•	Message-based communication preferred
	•	Candidate protocols:
	•	MQTT for telemetry and events
	•	REST APIs for control and configuration

Nodes do not directly log into each other for routine operation. All coordination is service-based.

⸻

Software Design Principles
	•	Headless-first operation
	•	Minimal OS installs per node
	•	Clear service boundaries
	•	Configuration via files, not hardcoding
	•	Logging designed for human readability

⸻

Future Expansion Ideas
	•	Additional Raspberry Pi compute nodes
	•	Dedicated storage or NAS node
	•	GPU or accelerator support
	•	Additional RF bands and modes
	•	Battery backup and power monitoring
	•	Advanced automation and scheduling
	•	Local-only LLM deployment

⸻

Long-Term Vision

Pi BOX is intended to become:
	•	A personal communications hub
	•	A learning and experimentation platform
	•	A resilient always-on assistant
	•	A documented, reproducible open project

This document is a living reference and will evolve as Pi BOX grows.

⸻

Version: 1.0
Status: Initial design freeze (conceptual)
