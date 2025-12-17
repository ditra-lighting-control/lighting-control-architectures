# Architectural & Media Façade Lighting Control

Technical reference for lighting control architectures used in architectural, dynamic, and media façade lighting systems.

This section describes how lighting control systems are designed for buildings, façades, bridges, landmarks, and public spaces — ranging from static architectural illumination to complex, pixel-based media façades.

The focus is on **system architecture, protocols, and control logic**, not on artistic content or specific products.

---

## Scope

Architectural and façade lighting control systems typically address the following tasks:

- precise control of light levels, color, and timing,
- synchronization across large fixture groups,
- scalability from small installations to thousands of controlled points,
- reliable operation in permanent outdoor environments.

This section covers:

- static architectural lighting control,
- dynamic lighting systems with time-based scenes,
- media façade and pixel-mapped installations,
- integration with scheduling and management software.

---

## Control Models

Common architectural lighting control models include:

- centralized playback controllers,
- distributed control using networked nodes.

Control may be continuous (real-time playback) or event-based (scene triggering, schedules).

---

## Control & Transport Protocols
Architectural lighting and media façade projects typically combine several layers of control and transport. Commonly used standards and interfaces include:

- **sACN / E1.31 (ANSI E1.31)** streams DMX-style control data over IP networks and is typically transported over **UDP** (unicast and/or multicast). Timing and reliability therefore depend on network engineering (segmentation, multicast control, IGMP snooping, QoS, redundancy).
- **Art-Net** is a widely used IP protocol for transporting DMX universes and is typically implemented over **UDP**. Performance and stability depend on network topology and configuration, especially at large universe counts.

- **DMX512-A (ANSI E1.11)** is the base standard for DMX data transport at the physical/link level.
- **RDM (ANSI E1.20)** is a bidirectional management/diagnostics protocol that operates **over DMX512-A** (same line), enabling discovery, addressing, configuration, and status reporting.

- **DALI (IEC 62386)** defines the underlying wired lighting control protocol and device types.
- **DALI-2** is a **certification/interoperability program** (based on IEC 62386) that constrains implementations and requires standardized behavior to improve multi-vendor compatibility.
- **D4i (DiiA)** is a DALI-2–based specification set targeting luminaire/in-driver data (e.g., diagnostics and asset-related data), depending on ecosystem requirements.

- **KiNet** is a **proprietary** UDP/IP-based protocol used within the **Philips Color Kinetics** ecosystem (not an open, cross-vendor standard).

- **Pixel-level LED control interfaces** for media façades, where content is mapped to individual pixels/segments:
  - clocked data interfaces often described as **SPI-like** signaling (data + clock) toward LED drivers/pixel ICs,
  - timing-based single-line pixel signaling used by some addressable LED families,
  - **PWM at the driver level** as the underlying dimming method (a modulation technique, not a transport protocol).
  
> Note: the exact stack is project-specific and depends on required synchronization, bandwidth, distance, diagnostics needs, and vendor ecosystem; this list is not exhaustive.


---

## Media Façade Systems

Media façade lighting introduces additional architectural requirements:

- pixel mapping and addressing,
- high channel counts and bandwidth planning,
- frame synchronization across multiple controllers,
- tight frame timing / synchronization (requires proper network design and clocking strategy)

These systems often integrate video or generative content translated into lighting data.

---

## Software Layer

Architectural lighting systems typically rely on dedicated software for:

- fixture mapping and grouping,
- scene and timeline creation,
- content playback and scheduling,
- system monitoring and diagnostics.

Software acts as a coordination layer between creative intent and physical infrastructure.

---

## Design Considerations

Key architectural considerations include:

- network topology and redundancy,
- latency and synchronization tolerance,
- long-term maintainability,
- separation of creative control and operational monitoring.

This documentation treats architectural lighting as an **engineering system**, not a visual effect.
