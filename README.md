# lighting-control-architectures
Technical reference for lighting control architectures used in street, architectural, media façade, and entertainment lighting systems.
This repository documents **core principles, system architectures, protocols, and design patterns** used in modern lighting control — from city-scale street lighting networks to pixel-based media façades and real-time entertainment systems.
The content is vendor-neutral and focuses on **engineering logic**, not product promotion.
## Scope

This repository covers lighting control systems across three major domains:

- **Street & Urban Lighting Control**
- **Architectural & Media Façade Lighting**
- **Entertainment & Stage Lighting Control**

Each domain is described through:

- control levels and system topology,
- communication technologies and protocols,
- typical hardware and software roles,
- architectural trade-offs and limitations.

---

## 1. Street Lighting Control

Street lighting control architectures are deployed to optimize energy use, reduce operating costs, and improve safety, while maintaining reliable long-term operation across large outdoor networks.

Covered topics:

- Cabinet / segment (group) control
- Individual luminaire control (NEMA, Zhaga, pole-mounted luminaire nodes)
- Communication technologies:
    - PLC (Power Line Communication)
    - Sub-GHz RF (868 / 915 MHz)
    - GSM / LTE / cellular IoT
- Sensor-based adaptive lighting
- Solar-powered and off-grid lighting systems
- Central Management Systems (CMS) and Smart City integration

Focus areas:

- energy efficiency,
- fault detection and diagnostics,
- city-scale monitoring,
- interoperability and standards.

---

## 2. Architectural & Media Façade Lighting

Architectural and media façade lighting control combines precise technical control with flexible system architectures, supporting projects from static architectural illumination to complex, time-synchronized dynamic and pixel-based displays.

Covered topics:

- Static architectural lighting
- Dynamic architectural lighting
- Media façade (pixel-based) lighting systems
- Protocols:
    - DMX512, RDM
    - Art-Net, sACN (E1.31), KiNet
    - DALI / D4i
    - SPI / PWM and native pixel protocols
- Pixel mapping and video-to-light workflows
- Network design for high-universe-count systems
- Synchronization, latency, and performance constraints
- Integration with scheduling systems and city platforms

Special attention is given to **system architecture**, not artistic content.

---

## 3. Entertainment & Stage Lighting Control

Technical reference for entertainment and stage lighting control architectures used in live performance environments. Covers real-time, deterministic lighting systems based on DMX512-A, RDM, Art-Net, and sACN, including control of intelligent fixtures, moving heads, and pixel-based systems.

Covered topics:

- Lighting consoles and cue-based control
- Art-Net / sACN distribution networks
- DMX gateways, nodes, splitters, and isolators
- Media servers and pixel engines
- Show control integration (OSC, MIDI, SMPTE timecode)
- Touring and fixed-installation architectures
- Redundancy and fault isolation strategies

Use cases include theatres, concerts, festivals, broadcast studios, and immersive installations.

---

## 4. Software Layers

The repository describes software roles across lighting systems, including:

- Central Management Systems (CMS) for street lighting
- Architectural scene design tools
- Media façade and pixel-mapping software
- Scheduling, playback, and timeline engines
- Telemetry, diagnostics, and logging
- API-based integration with Smart City platforms

Software is treated as an **architectural layer**, not as an implementation detail.

---

## Intended Audience

This repository is intended for:

- lighting engineers and system designers,
- urban infrastructure planners,
- system integrators and technical consultants,
- developers working with lighting CMS or media systems,
- researchers and educators in lighting technologies.
