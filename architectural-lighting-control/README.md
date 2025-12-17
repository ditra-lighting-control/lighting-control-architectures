# Architectural & Media Façade Lighting Control Architectures

Technical reference for lighting control architectures used in **architectural, dynamic, and media façade lighting systems**.

This repository section describes how lighting control systems are engineered for buildings, façades, bridges, landmarks, and public spaces — ranging from static architectural illumination to complex, pixel-based media façades.

The focus is on **system architecture, control models, protocols, and design constraints**, not on artistic content or vendor-specific products.

---

## Scope

Architectural and façade lighting control systems are designed to address the following engineering tasks:

- precise control of light levels, color, and timing,
- synchronization across large fixture groups and façade segments,
- scalability from small static installations to high-resolution pixel systems,
- reliable long-term operation in permanent outdoor environments.

This section covers:

- static architectural lighting control,
- dynamic lighting systems with scheduled or programmed scenes,
- media façade and pixel-mapped installations,
- integration with scheduling, monitoring, and management software.

---

## Types of Architectural Lighting Systems

Architectural lighting systems generally fall into three categories, ordered by control complexity.

### 1. Static Architectural Lighting

Static systems provide fixed or slowly changing illumination for buildings and structures.

Characteristics:

- fixed white or tunable-white output,
- limited number of scenes or presets,
- long duty cycles and high reliability requirements,
- minimal real-time control.

Typical control interfaces include **DALI / DALI-2 / D4i**, **0–10 V**, and in some cases **DMX512-A** for RGBW fixtures used in a static (non-animated) way.

---

### 2. Dynamic Architectural Lighting

Dynamic systems enable color-changing scenes and programmed effects while preserving architectural integrity.

Characteristics:

- scene-based or timeline-based playback,
- scheduled transitions and seasonal/event-driven content,
- **predictable timing** for programmed effects (not continuous video playback).

These systems commonly use **DMX512-A**, **RDM**, **Art-Net**, or **sACN**, often combined with centralized or distributed playback controllers.

---

### 3. Media Façade Lighting (Pixel-Based)

Media façades treat the building envelope as a pixel canvas.

Characteristics:

- pixel- or segment-level addressing,
- frame-based playback (commonly in the ~25–60 fps range, content- and system-dependent),
- very high channel and universe counts,
- strict synchronization requirements.

Media façades typically rely on **Art-Net**, **sACN (ANSI E1.31)**, **KiNet**, and/or Ethernet-to-pixel architectures (e.g., Ethernet to SPI-like outputs), with pixel mapping and content engines acting as primary control sources.

---

## Control Models

Architectural lighting systems typically follow one or a combination of the following control models:

- **Centralized playback**  
  A controller or server executes scenes or timelines and distributes control data to fixtures.

- **Distributed control**  
  Multiple networked controllers or nodes execute synchronized logic across façade segments.

Control may be:

- **scene-based** (event- or schedule-triggered), or
- **frame-based** (continuous streaming for media façades).

---

## Control & Transport Protocols

Architectural and media façade systems combine multiple protocol layers depending on scale and complexity.

Common standards and interfaces include:

- **DMX512-A (ANSI E1.11)**  
  Defines the electrical interface and framing/timing for DMX data transport (up to 512 control slots per universe). Widely used for real-time parameter streaming.

- **RDM (ANSI E1.20)**  
  Bidirectional device discovery, addressing, configuration, and diagnostics **over DMX512-A** (on the same physical line), when supported by devices and the distribution topology.

- **Art-Net**  
  Widely used **UDP/IP** transport for DMX universes over Ethernet (commonly unicast and/or broadcast, depending on configuration). Scaling depends on network design and traffic strategy.

- **sACN / E1.31 (ANSI E1.31)**  
  Standards-based **UDP/IP** DMX-over-IP protocol supporting unicast and multicast distribution and source priority concepts. As a streaming protocol over a non-reliable IP transport, performance depends on network engineering.

- **DALI (IEC 62386)**  
  Wired architectural lighting control protocol and device type framework.

- **DALI-2**  
  IEC 62386-based device/interface requirements plus an interoperability certification approach intended to improve multi-vendor compatibility.

- **D4i**  
  A DALI-2–based specification set focused on luminaire/in-driver data (e.g., diagnostics and asset-related data), depending on the project ecosystem.

- **KiNet**  
  Proprietary Ethernet-based protocol used in some pixel-based ecosystems.

- **Pixel-level LED interfaces**  
  Interfaces toward LED drivers/pixel ICs (e.g., SPI-like clocked data, timing-based single-line signaling), with **PWM at the driver level** as the underlying dimming method.

Protocol selection depends on synchronization requirements, bandwidth, diagnostics needs, distance, and system topology.

---

## Media Façade Systems

Media façade lighting introduces additional architectural constraints:

- pixel mapping and geometric modeling,
- bandwidth planning and universe segmentation,
- frame synchronization across multiple controllers,
- network latency and jitter management.

These systems often translate video, generative graphics, or data streams into lighting data and typically require separation of lighting traffic from general IT networks.

---

## Software Layer

Architectural lighting systems rely on software as an **execution and coordination layer**, responsible for:

- fixture mapping and addressing,
- scene and timeline programming,
- pixel mapping and content conversion,
- playback scheduling and priority handling,
- monitoring, diagnostics, and logging.

Software bridges creative intent and physical infrastructure and may operate standalone or integrate with higher-level city or facility management platforms.

---

## Design Considerations

Key engineering considerations include:

- network topology and redundancy,
- synchronization and latency tolerance,
- maintainability over long service lifetimes,
- separation of creative control and operational monitoring,
- regulatory and environmental constraints.

Architectural lighting is treated here as an **engineering system**, not a visual effect.

---

## Relation to Other Domains

Architectural and media façade lighting shares protocols with entertainment lighting and interfaces with Smart City platforms but differs in:

- operational logic,
- timing models,
- duty cycles and longevity requirements.

This repository focuses on the architectural domain and its specific control challenges.
