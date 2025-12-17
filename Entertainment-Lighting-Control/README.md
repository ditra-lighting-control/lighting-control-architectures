# Theatre & Stage Lighting Control Architectures

Technical reference for **theatre and stage lighting control architectures** used in fixed venues and performance environments, including drama theatres, opera houses, concert halls, and multi-purpose auditoriums.

This repository documents **show-oriented lighting control**: how systems are designed to run repeatable performances (rehearsals → previews → shows), where cues are executed by an operator and synchronized with audio, video, and stage automation.

The focus is on **system architecture, protocols, cueing/playback models, and operational design patterns** that provide predictable timing, maintainability, and fault isolation in production workflows.

The content is vendor-neutral and focuses on **engineering principles**, not specific products or artistic content.


---

## Scope

This repository covers lighting control systems designed for **theatrical and stage-based performance**, where lighting is synchronized with music, scenography, movement, and dramaturgy.

Key focus areas:

- predictable timing and repeatable playback
- cue-based operation
- long-term operational stability
- redundancy and fault isolation
- interoperability with audio, video, and automation systems

Lighting control is treated as a **real-time performance system**, not as an infrastructure service.

---

## 1. Theatre Lighting Control Characteristics

Theatrical lighting systems differ fundamentally from architectural or urban lighting systems:

- cue-based execution instead of continuous automation
- predictable timing for rehearsed playback (achieved through proper system design)
- high channel density per fixture
- live operator interaction
- synchronization with other show systems

Reliability and repeatability are critical, as shows are executed repeatedly over long production cycles.

---

## 2. Types of Theatre Lighting Systems

### 2.1 Conventional Fixtures

- tungsten or LED luminaires
- intensity-based control
- historically driven by dimmer racks
- controlled via **DMX512-A** using defined dimmer curves and console/dimmer configuration

Still widely used in drama theatres and classical stages.

---

### 2.2 Automated and Intelligent Fixtures

- moving heads (spot, wash, beam)
- LED profiles and hybrid luminaires
- multi-parameter control, typically including:
  - pan / tilt
  - zoom / focus
  - color mixing
  - gobos, shutters, animation wheels

Each fixture occupies multiple DMX channels and requires structured patching, parameter management, and cue programming.

---

### 2.3 LED and Pixel-Based Elements

- LED bars, battens, tubes, grids
- scenic and set-integrated lighting elements
- often require **multi-universe distribution** via Art-Net or sACN when pixel-mapped or high-density

Common in contemporary theatre, opera, and experimental performance spaces.

---

## 3. Core Control Protocols

### 3.1 DMX512-A (ANSI E1.11)

Primary control transport for theatrical lighting.

Typical properties:

- up to **512 control slots** per universe
- streaming refresh rate depends on slot count and transmitter implementation (for a full 512-slot universe, refresh is typically up to ~44 Hz)
- designed for low-latency, continuous parameter streaming (no delivery acknowledgements)
- **bus wiring** (commonly daisy-chained), requiring correct termination; splitters are used for branching and isolation

---

### 3.2 RDM (ANSI E1.20)

Bidirectional extension to DMX512-A operating on the same DMX line.

Enables:

- fixture discovery
- addressing and configuration
- diagnostics and status monitoring

Often used to simplify commissioning and maintenance, subject to line loading, device support, and RDM-friendly distribution design.

---

### 3.3 Art-Net

Widely used DMX-over-IP protocol for:

- distributing many universes over Ethernet
- connecting consoles to remote gateways/nodes
- integrating pixel-mapped elements and media servers

Commonly implemented over **UDP**. Performance and stability depend on network topology and configuration (segmentation, broadcast/unicast strategy, and overall traffic levels).

---

### 3.4 sACN / E1.31 (ANSI E1.31)

Standards-based streaming protocol for DMX-style control over IP networks.

Typical characteristics:

- commonly implemented over **UDP**
- supports unicast and multicast distribution
- includes source priority concepts (useful for merging and fallback behaviors)
- scales well when multicast is engineered correctly (e.g., IGMP, multicast containment)

Often preferred in modern theatre installations with many universes and structured networks.

---

### 3.5 Timecode and Control Interfaces

Used for synchronization and show-control integration:

- **SMPTE timecode / MTC (MIDI Time Code)** — timeline-locked synchronization between show systems
- **OSC** — network control for triggers and continuous parameter updates
- **MIDI** — widely used for control/synchronization in production workflows (including timecode transport and show-control messages where applicable)

---

## 4. System Architecture

A typical theatre lighting control system includes:

### 4.1 Lighting Consoles

Primary operator interface.

Core capabilities typically include:

- cue stacks and playback lists
- palettes (color / position / beam)
- effects engines
- live overrides and manual control

Consoles output DMX directly and/or via Art-Net / sACN through network infrastructure.

---

### 4.2 Gateways and Nodes

Ethernet-to-DMX interfaces used for signal distribution and locality.

Typical placement:

- FOH and control rooms
- stage wings
- under-stage technical areas
- near trusses and scenic elements

Used for distribution, segmentation, electrical isolation, and fault containment.

---

### 4.3 Splitters, Repeaters, and Isolators

Used to:

- prevent signal degradation on long or complex DMX runs
- create branches while maintaining correct termination behavior
- isolate failures (electrical and topology-related)
- improve robustness in permanent installations

Common and often essential in fixed venues.

---

### 4.4 Media and Show Servers

Used when lighting integrates with video, pixel mapping, or generative content.

Typical functions:

- pixel mapping and patch abstraction
- video-to-light conversion
- synchronization with audio and automation systems

Connected via Art-Net, sACN, and/or show-control interfaces (timecode, OSC, MIDI, etc.).

---

## 5. Control Logic and Operation

### 5.1 Cue-Based Programming

Lighting states are defined as discrete cues with:

- fade times
- follow / wait logic
- priority and override behavior (console- and workflow-specific)

This model is fundamental to theatrical lighting operation.

---

### 5.2 Live Operation

Although theatre is primarily cue-driven, operators may use:

- manual overrides
- executor faders
- live effects and busking techniques

Especially relevant in experimental, concert, and hybrid productions.

---

### 5.3 Synchronization

Lighting systems commonly synchronize with:

- audio playback
- video timelines
- stage automation

Using timecode, OSC, MIDI, or dedicated show-control frameworks, depending on the venue and production pipeline.

---

## 6. Reliability and Redundancy

Theatre lighting systems are designed for:

- long rehearsal cycles
- repeatable nightly performances
- predictable behavior over extended periods

Common strategies include:

- isolated DMX lines and opto-splitting
- segmented universes and clear patch boundaries
- redundant network paths (where supported by the architecture)
- controlled startup and recovery behavior (power sequencing, safe states, fallback sources)

---

## 7. Typical Applications

Theatre lighting control architectures are used in:

- drama theatres
- opera houses
- musical theatre venues
- concert halls
- black box theatres
- academic and experimental stages

Many venues combine theatrical, architectural, and media-based lighting within a single control ecosystem.

---

## Intended Audience

This repository is intended for:

- theatre lighting designers
- system engineers
- integrators of permanent performance venues
- technical directors
- educators and students in stage technologies

---

## Relation to Other Domains

Theatre lighting shares protocols with architectural and media lighting systems but differs in:

- operational logic
- timing expectations and playback workflows
- control philosophy and human-in-the-loop operation

This repository focuses specifically on **stage and performance-oriented architectures**.
