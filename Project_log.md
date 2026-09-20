# ESP32 3.1 Audio System

> **Status:** 🟡 In development
> **Project type:** Personal engineering project
> **Domain:** Embedded / Electronics / Digital Audio / Hardware
> **Platform:** ESP32
> **Author:** Tomasz Ślęczkowski
> **Started:** 2026-09-20

---

## 1. Project Overview

### 1.1 Description

ESP32 3.1 Audio System is a personal engineering project focused on developing a custom 3.1 audio device based on the ESP32 platform.

The system is intended to combine multiple audio sources, wireless connectivity, digital audio processing and multi-channel amplification into a single integrated device.

The initial target functionality includes:

* Spotify Connect
* Bluetooth Audio
* Wi-Fi connectivity
* 3.1-channel audio output
* Left channel
* Right channel
* Subwoofer channel
* Digital audio processing
* Multi-channel amplification
* Configuration and control from the embedded system

The project is being developed incrementally, starting from requirements and architecture and progressing toward a functional hardware prototype.

---

# 2. Project Goals

## 2.1 Primary Goal

Develop a functional 3.1 audio system integrating wireless audio sources with a custom embedded hardware platform.

## 2.2 Engineering Goals

The project is also intended to provide practical experience in:

* Embedded systems
* ESP32 development
* Digital audio
* Audio interfaces
* Hardware architecture
* PCB design
* Power supply design
* Firmware development
* Wireless communication
* Hardware/software integration
* Debugging and measurement
* Engineering documentation

---

# 3. Target Functionality

| Feature         | Target   | Status |
| --------------- | -------- | ------ |
| ESP32 platform  | Required | 🟡     |
| Wi-Fi           | Required | 🟡     |
| Spotify Connect | Required | 🟡     |
| Bluetooth Audio | Required | 🟡     |
| Left channel    | Required | 🟡     |
| Right channel   | Required | 🟡     |
| Subwoofer       | Required | 🟡     |
| Digital audio   | Required | 🟡     |
| DAC / CODEC     | TBD      | ⚪      |
| DSP             | TBD      | ⚪      |
| Amplifier       | TBD      | ⚪      |
| Power supply    | TBD      | ⚪      |
| Custom PCB      | Planned  | ⚪      |
| Enclosure       | Planned  | ⚪      |

### Status legend

* 🟢 Completed
* 🟡 In progress
* ⚪ Planned / TBD
* 🔴 Problem / blocked

---

# 4. System Requirements

This section will contain measurable technical requirements.

The values should be updated as the design progresses.

## 4.1 Audio

| Parameter          | Requirement | Actual | Status |
| ------------------ | ----------- | ------ | ------ |
| Configuration      | 3.1         | TBD    | 🟡     |
| Sample rate        | TBD         | TBD    | ⚪      |
| Bit depth          | TBD         | TBD    | ⚪      |
| Frequency response | TBD         | TBD    | ⚪      |
| THD+N              | TBD         | TBD    | ⚪      |
| SNR                | TBD         | TBD    | ⚪      |
| Output power L/R   | TBD         | TBD    | ⚪      |
| Output power SUB   | TBD         | TBD    | ⚪      |

---

## 4.2 Connectivity

| Interface       | Requirement           | Status |
| --------------- | --------------------- | ------ |
| Wi-Fi           | Required              | 🟡     |
| Bluetooth       | Required              | 🟡     |
| Spotify Connect | Required              | 🟡     |
| USB             | TBD                   | ⚪      |
| Ethernet        | Not planned initially | ⚪      |

---

## 4.3 Power

| Parameter            | Requirement | Actual | Status |
| -------------------- | ----------- | ------ | ------ |
| Input voltage        | TBD         | TBD    | ⚪      |
| Maximum system power | TBD         | TBD    | ⚪      |
| Standby power        | TBD         | TBD    | ⚪      |
| Logic supply         | TBD         | TBD    | ⚪      |
| Audio supply         | TBD         | TBD    | ⚪      |

---

# 5. Initial System Architecture

The initial concept is based around the ESP32 as the central control and connectivity platform.

```text
                        ┌───────────────────────┐
                        │         ESP32         │
                        │                       │
                        │       Wi-Fi           │
                        │   Spotify Connect     │
                        │   Bluetooth Audio     │
                        │                       │
                        └───────────┬───────────┘
                                    │
                                    │ Digital Audio
                                    │
                                    ▼
                        ┌───────────────────────┐
                        │    AUDIO PROCESSING   │
                        │                       │
                        │      DAC / CODEC      │
                        │         DSP           │
                        │          TBD          │
                        └───────────┬───────────┘
                                    │
                         ┌──────────┼──────────┐
                         │          │          │
                         ▼          ▼          ▼
                        LEFT       RIGHT      SUB
                         │          │          │
                         ▼          ▼          ▼
                       AMP L      AMP R      AMP SUB
                         │          │          │
                         ▼          ▼          ▼
                     Speaker L   Speaker R   Subwoofer
```

This architecture is preliminary and will change as technical requirements become more precise.

---

# 6. Architecture Questions

Before committing to the final hardware design, the following questions need to be answered:

* Which ESP32 variant is appropriate?
* Which ESP32 audio interfaces are required?
* How will Spotify Connect be implemented?
* How will Bluetooth Audio be implemented?
* Is simultaneous Wi-Fi and Bluetooth operation required?
* What audio format will be used internally?
* Which digital audio interface will be used?
* Is an external DAC required?
* Is an external CODEC required?
* Is DSP processing required?
* Where should crossover processing take place?
* How will the subwoofer signal be generated?
* What amplifier topology should be used?
* What output power is required?
* What speaker impedance will be used?
* How will the system be powered?
* How will analogue and digital grounds be handled?
* What thermal requirements exist?
* Will the final system require a custom PCB?
* What enclosure constraints exist?

These questions will be answered progressively rather than assumed at the beginning of the project.

---

# 7. Engineering Decisions

This section records important design decisions.

The goal is not only to document **what** was selected, but also **why**.

---

## Decision #001 — Main MCU

**Status:** 🟡 Under investigation

### Candidates

* ESP32
* ESP32-S3
* ESP32-A series
* Other ESP32 variants

### Requirements

The selected platform must provide sufficient resources for:

* Wireless connectivity
* Audio processing
* Bluetooth functionality
* Wi-Fi functionality
* Required audio interfaces
* Firmware
* Future expansion

### Decision

**TBD**

### Reason

**TBD**

### Alternatives considered

**TBD**

---

## Decision #002 — Digital Audio Interface

**Status:** ⚪ Not decided

Possible interfaces:

* I2S
* Other suitable digital audio interface

### Decision

**TBD**

### Reason

**TBD**

---

## Decision #003 — DAC / CODEC

**Status:** ⚪ Not decided

### Candidates

**TBD**

### Decision

**TBD**

### Reason

**TBD**

---

## Decision #004 — Amplifier

**Status:** ⚪ Not decided

### Requirements

The amplifier stage must be selected according to:

* Speaker impedance
* Required output power
* Supply voltage
* Efficiency
* Thermal performance
* Audio quality
* Physical size
* Availability
* Cost

### Decision

**TBD**

### Reason

**TBD**

---

# 8. Research Log

Use this section to record technical research before making decisions.

---

## Research #001 — ESP32 Audio Capabilities

**Date:** 2026-09-20

### Question

Can the selected ESP32 platform handle the required combination of:

* Wi-Fi
* Bluetooth
* Spotify Connect
* Digital audio
* 3.1 processing?

### Findings

TBD

### Sources

TBD

### Conclusion

TBD

---

## Research #002 — Spotify Connect

**Date:** TBD

### Question

What software/library architecture should be used to implement Spotify Connect?

### Findings

TBD

### Sources

TBD

### Conclusion

TBD

---

## Research #003 — Bluetooth Audio

**Date:** TBD

### Question

Which Bluetooth audio profile and implementation should be used?

### Findings

TBD

### Sources

TBD

### Conclusion

TBD

---

# 9. Development Timeline

This section records major project milestones.

---

## 2026-09-20 — Project Started

### Completed

* Created initial project concept
* Defined basic 3.1 configuration
* Selected ESP32 as the initial platform
* Defined Spotify Connect as a target feature
* Defined Bluetooth Audio as a target feature
* Started engineering documentation

### Result

Initial project architecture created.

### Next step

Research ESP32 variants and audio architecture.

---

# 10. Experiments

Every important experiment should be documented here.

The objective is to record measurable results rather than only describing what happened.

---

## Experiment #001 — TBD

**Date:** TBD

### Objective

TBD

### Hypothesis

TBD

### Setup

TBD

### Equipment

* TBD

### Procedure

1. TBD
2. TBD
3. TBD

### Expected result

TBD

### Measured result

TBD

### Conclusion

TBD

### Photos

TBD

---

# 11. Measurements

This section will contain actual measurements from the prototype.

Whenever possible, record:

* Instrument
* Model
* Measurement conditions
* Supply voltage
* Load
* Ambient conditions
* Measurement result
* Date

---

## Measurement #001

**Parameter:** TBD

**Instrument:** TBD

**Model:** TBD

**Conditions:** TBD

**Result:** TBD

**Date:** TBD

---

# 12. Hardware Development

## 12.1 Schematic

**Status:** ⚪ Not started

Files:

```text
hardware/
└── schematic/
```

---

## 12.2 PCB

**Status:** ⚪ Not started

Planned documentation:

* Schematic
* PCB layout
* PCB revision
* Gerber files
* BOM
* Pick & Place
* Design rules
* Manufacturing notes

---

## 12.3 Bill of Materials

| Reference | Component    | Part Number | Quantity | Status |
| --------- | ------------ | ----------- | -------: | ------ |
| U1        | ESP32        | TBD         |        1 | ⚪      |
| U2        | DAC / CODEC  | TBD         |        1 | ⚪      |
| U3        | Amplifier    | TBD         |        1 | ⚪      |
| PSU       | Power supply | TBD         |        1 | ⚪      |

---

# 13. Firmware

## 13.1 Planned Architecture

```text
firmware/
│
├── main/
│
├── audio/
│
├── bluetooth/
│
├── wifi/
│
├── spotify/
│
├── dsp/
│
└── system/
```

The final architecture will be updated during development.

---

## 13.2 Firmware Milestones

| Milestone                     | Status |
| ----------------------------- | ------ |
| ESP32 development environment | ⚪      |
| Basic firmware                | ⚪      |
| Wi-Fi connection              | ⚪      |
| Bluetooth                     | ⚪      |
| Audio output                  | ⚪      |
| Spotify Connect               | ⚪      |
| Audio routing                 | ⚪      |
| DSP / crossover               | ⚪      |
| System configuration          | ⚪      |

---

# 14. Problems & Debugging

This section is especially important.

Do not remove failed experiments.

Document them.

---

## Problem #001 — TBD

**Date:** TBD

### Symptom

TBD

### Expected behaviour

TBD

### Actual behaviour

TBD

### Initial hypothesis

TBD

### Tests performed

TBD

### Root cause

TBD

### Solution

TBD

### Verification

TBD

### Lesson learned

TBD

---

# 15. Design Changes

Record every meaningful design change.

---

## Change #001

**Date:** TBD

### Previous solution

TBD

### New solution

TBD

### Reason for change

TBD

### Expected benefit

TBD

### Result

TBD

---

# 16. Prototype Revisions

Use revision numbers for hardware.

---

## Revision 0 — Concept

**Status:** 🟡

Initial architecture and requirements.

---

## Revision 1 — Prototype

**Status:** ⚪ Planned

Expected changes:

* First hardware implementation
* Basic audio path
* ESP32 integration
* Initial measurements

---

## Revision 2

**Status:** ⚪ Planned

Changes:

TBD

---

# 17. Testing Plan

Before calling the project complete, the following areas should be tested.

### Functional tests

* [ ] ESP32 boots correctly
* [ ] Wi-Fi connection works
* [ ] Bluetooth connection works
* [ ] Spotify Connect works
* [ ] Audio output works
* [ ] Left channel works
* [ ] Right channel works
* [ ] Subwoofer works
* [ ] Audio routing works
* [ ] System recovers from connection loss

### Audio tests

* [ ] Frequency response
* [ ] Output level
* [ ] Channel separation
* [ ] Noise floor
* [ ] Distortion
* [ ] Subwoofer crossover
* [ ] Maximum output level

### Hardware tests

* [ ] Power consumption
* [ ] Thermal performance
* [ ] Long-term stability
* [ ] Startup behaviour
* [ ] Protection behaviour

---

# 18. Known Limitations

At the current stage:

* Hardware architecture is not finalized.
* DAC / CODEC has not been selected.
* Amplifier has not been selected.
* Power supply architecture has not been finalized.
* Spotify Connect implementation has not been finalized.
* Bluetooth implementation has not been finalized.
* Audio processing architecture has not been finalized.
* No custom PCB exists yet.

This section will be updated throughout development.

---

# 19. Current Status

**Overall status:** 🟡 In development

### Completed

* [x] Project concept
* [x] Initial system definition
* [x] Basic 3.1 architecture
* [x] Initial ESP32 selection
* [x] Documentation structure

### In progress

* [ ] ESP32 platform research
* [ ] Audio architecture
* [ ] Connectivity architecture
* [ ] Component selection

### Planned

* [ ] Prototype
* [ ] Firmware
* [ ] Schematic
* [ ] PCB
* [ ] Measurements
* [ ] Audio testing
* [ ] Enclosure
* [ ] Final documentation

---

# 20. Next Steps

Current priorities:

1. Determine the exact ESP32 variant.
2. Investigate Spotify Connect implementation options.
3. Investigate Bluetooth Audio implementation.
4. Define the digital audio architecture.
5. Determine whether an external DAC / CODEC is required.
6. Define the 3.1 signal path.
7. Determine the crossover strategy.
8. Select the amplifier architecture.
9. Define the power architecture.
10. Update the system block diagram.
11. Create the first hardware architecture proposal.

---

# 21. Project Photos

Photos will be added as the project progresses.

Recommended structure:

```text
images/
│
├── project-start/
├── prototype/
├── pcb/
├── measurements/
├── debugging/
└── final/
```

Example:

```markdown
![Initial prototype](images/project-start/initial-prototype.jpg)
```

---

# 22. Useful Documents

| Document               | Description           |
| ---------------------- | --------------------- |
| `README.md`            | Project overview      |
| `PROJECT_LOG.md`       | Development journal   |
| `docs/requirements.md` | Detailed requirements |
| `docs/architecture.md` | System architecture   |
| `docs/decisions/`      | Engineering decisions |
| `hardware/`            | Hardware design       |
| `firmware/`            | Firmware              |
| `measurements/`        | Measurements          |

---

# 23. Lessons Learned

This section should contain knowledge gained during the project.

### Lesson #001

**Date:** TBD

**Topic:** TBD

**What I learned:**

TBD

**How this affects the design:**

TBD

---

# 24. Final Project Summary

> This section will be completed after the project reaches a stable prototype.

### Final architecture

TBD

### Main components

TBD

### Measured performance

TBD

### Problems encountered

TBD

### Solutions implemented

TBD

### Final cost

TBD

### Development time

TBD

### What I would change in Revision 2

TBD

---

# 25. Portfolio Summary

Short version for the public portfolio:

> **ESP32 3.1 Audio System**
> Personal embedded audio project involving ESP32, wireless audio connectivity, digital audio processing, multi-channel amplification and custom hardware development. The project is documented from initial requirements and architecture through prototyping, debugging, measurements and final validation.

---

## Changelog

| Date       | Version | Description                 |
| ---------- | ------- | --------------------------- |
| 2026-09-20 | v0.1    | Initial project log created |

---
