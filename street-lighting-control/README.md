# Street Lighting Control Architectures

Technical reference for **street and urban lighting control architectures** used in roadway, municipal, and infrastructure lighting networks.

This section describes how modern street lighting systems are engineered to **optimize energy consumption**, **reduce operational costs**, **improve safety**, and **support scalable Smart City integration** across large outdoor environments.

The focus is on **system architecture, control levels, communication technologies, and engineering trade-offs**, not on specific products.

---

## Scope

Street lighting control systems typically address the following technical objectives:

- energy efficiency through dimming and adaptive control,
- centralized and distributed automation of lighting assets,
- operational reliability and fault transparency,
- scalability from single streets to city-wide networks,
- long-term operation in harsh outdoor environments.

This repository section covers:

- cabinet / segment (group) control architectures,
- individual luminaire control models,
- communication technologies used in street lighting,
- sensor-based adaptive lighting,
- solar-powered and off-grid lighting systems,
- centralized management software and Smart City integration.

---

## Control Levels in Street Lighting

Street lighting networks are commonly structured across multiple control levels.

### 1. Cabinet / Segment Control

Segment (group) control is based on a centralized controller installed in an electrical cabinet that manages an entire feeder or lighting group.

Typical characteristics:

- feeder line switching (via contactors/relays) and coordination with protective devices (breakers/fuses),
- monitoring of voltage/current/energy via metering hardware (where installed),
- integration with meters and cabinet-level sensors,
- centralized scheduling, alarms, and diagnostics.

This architecture is widely used due to its **reliability, simplicity, and cost efficiency**, especially in highways, industrial zones, and large uniform networks.

---

### 2. Individual Luminaire Control

Individual control enables per-pole or per-luminaire management using pole-mounted or in-luminaire control nodes.

Key properties:

- per-luminaire dimming and monitoring,
- localized fault detection,
- support for adaptive lighting scenarios.

Typical form factors include **NEMA** and **Zhaga** (standardized controller interfaces/connectors), and in-luminaire or pole-mounted nodes that control the LED driver via **driver interfaces** such as **DALI / D4i** or **0–10 V**, depending on luminaire design.


Individual control is often deployed selectively or combined with segment control in **hybrid architectures**.

---

## Communication Technologies

Street lighting systems rely on several communication layers depending on network topology and constraints.

### Power Line Communication (PLC)

- Uses existing power cables for data transmission.
- Best suited for centralized, lighting-only feeder lines.
- Cost-efficient and reliable in uniform networks.
- Often effective on dedicated or relatively “clean” feeder lines.
- Performance can degrade under electrical noise, impedance changes, or significant non-lighting loads on the same circuit.

PLC remains a common choice for linear streets and highways.

---

### Sub-GHz Wireless RF (868 / 915 MHz)

- Typically deployed in mesh or star/point-to-multipoint topologies.
- Suitable for decentralized power supplies.
- Performs well in low- to medium-density urban environments.

---

### Cellular (GSM / LTE / NB-IoT)

- Provides wide-area coverage.
- Used for remote locations or dense urban areas with RF limitations.
- Enables direct cloud connectivity per node.

---

## Adaptive and Sensor-Based Lighting

Street lighting increasingly integrates sensors to enable adaptive behavior.

Common sensor inputs include:

- motion and presence detection,
- traffic flow and density,
- ambient light (lux),
- weather and environmental conditions,
- pole vibration or tilt.

Sensor data enables **dimming-on-demand**, weather-based adjustments, and enhanced operational awareness.

---

## Solar-Powered and Off-Grid Lighting

Solar-powered street lighting systems operate independently from grid power and rely on:

- solar panels,
- battery storage,
- smart charge and lighting control.

Control is essential to:

- protect battery health,
- optimize energy usage,
- ensure reliable operation during low-sunlight periods.

Remote monitoring via cellular connectivity allows early fault detection and lifecycle optimization, making solar lighting suitable for rural and infrastructure-limited areas.

---

## Software and Central Management

Street lighting control systems require centralized software platforms to provide:

- scheduling and astronomical control,
- geolocation and asset mapping,
- real-time telemetry and event logging,
- fault management and diagnostics,
- API-based integration with Smart City platforms.

The software layer acts as the **operational core** of modern street lighting networks.

---

## Typical System Architecture

A complete street lighting control system typically includes:

- cabinet or segment controllers,
- pole-level control nodes,
- sensors and auxiliary inputs,
- communication modules (PLC, RF, cellular),
- centralized management software,
- monitoring dashboards and analytics,
- integration interfaces for city platforms.

These components form a resilient, scalable lighting infrastructure suitable for long-term urban operation.

---

## Engineering Considerations

Key design considerations include:

- communication reliability and redundancy,
- fault isolation and diagnostics granularity,
- scalability and upgrade paths,
- lifecycle cost and maintenance access,
- regulatory and environmental constraints.

Street lighting control is treated here as an **infrastructure engineering system**, not merely a lighting application.
