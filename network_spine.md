Pi BOX

Internal Network Spine & Foundation Decisions

This document records the first irreversible build decisions for Pi BOX. It exists to ensure architectural clarity, reproducibility, and long-term consistency. Once frozen, these decisions should not be changed casually.

⸻

Foundation Status
	•	Project phase: Build Start – Stage 1 (Foundation)
	•	Status: Network spine locked

Pi BOX is now treated as a distributed system, not a single-board computer project.

⸻

Internal Network Spine (Locked)

Selected Option

Option A – Internal Ethernet Spine

All Raspberry Pi nodes inside Pi BOX are connected via a dedicated internal Ethernet switch.

This decision was made to prioritise:
	•	RF cleanliness
	•	deterministic latency
	•	reliability
	•	ease of debugging
	•	long-term scalability

Wireless networking is intentionally avoided inside the enclosure.

⸻

Network Topology

            [ Internal Ethernet Switch ]
                     |
     -----------------------------------------
     |               |               |       |
 pibox-dv        pibox-env        pibox-core  pibox-rf
 (Pi Zero A)     (Pi Zero B)      (Pi 5 A)    (Pi 5 B)

Topology Characteristics
	•	Fully wired internal network
	•	No dependency on Wi-Fi for inter-node communication
	•	Predictable behaviour under load
	•	RF-safe for SDR and MMDVM operation

⸻

IP Addressing Scheme (Frozen)

A private, static subnet is used inside Pi BOX.

Subnet: 10.42.0.0/24

Node Role	Hostname	IP Address
Digital Voice Node	pibox-dv	10.42.0.11
Environmental Node	pibox-env	10.42.0.12
Core / Intelligence Node	pibox-core	10.42.0.1
RF / SDR Node	pibox-rf	10.42.0.21

Addressing Rules
	•	pibox-core always uses .1
	•	Pi Zero nodes occupy the .1x range
	•	High-performance or RF nodes occupy the .2x range

This convention makes logs, alerts, and diagnostics immediately readable.

⸻

Traffic & Trust Model (Conceptual)
	•	All nodes send data to pibox-core
	•	No direct node-to-node communication for routine operation
	•	Observer nodes do not require internet access

Only pibox-core is permitted to:
	•	access LTE
	•	reach the public internet
	•	interact with APIs or AI services

This enforces the design rule:

One node thinks. Others observe.

⸻

Power Zoning Philosophy (Conceptual)

Although power wiring is not defined here, the following zones are assumed:
	•	Zone A – Low-noise, always-on
	•	Pi Zero nodes
	•	Zone B – High-draw, burst workloads
	•	Pi 5 nodes

Separate DC regulation with a shared ground is recommended to minimise RF noise and voltage sag.

⸻

Operating System Installation Order

To reduce ambiguity during initial bring-up, nodes should be prepared in the following order:
	1.	pibox-core
	2.	pibox-dv
	3.	pibox-env
	4.	pibox-rf

The core node defines the logical environment that all other nodes integrate into.

⸻

Design Freeze Notice

The decisions recorded in this document are considered foundational.

Changes should only be made if:
	•	a documented limitation is discovered
	•	a major version of Pi BOX is being planned

This document exists to prevent architectural drift as the project grows.

⸻

Document type: Foundation design reference
Scope: Network spine, addressing, and integration rules
Status: Frozen (Pi BOX v1.0)
