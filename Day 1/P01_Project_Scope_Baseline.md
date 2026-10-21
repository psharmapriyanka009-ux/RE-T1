# Project Scope Baseline: AeroVanguard AV-X9 Aetheris (Block II)
**Document Identifier:** `P01_Project_Scope_Baseline.md`  
**Internal Reference:** AVT-MOD-PROP-2026-R4 / TRAIN-002  
**Security Classification:** RESTRICTED / Commercial-in-Confidence / Internal Engineering Review  

---

## 1. Document Control

### 1.1 Document Metadata
| Metadata Field | Value |
|---|---|
| **Document Title** | Project Scope Baseline — AeroVanguard AV-X9 Aetheris (Block II) Tactical UAS |
| **Document ID / Filename** | `P01_Project_Scope_Baseline.md` |
| **Platform Designation** | AeroVanguard AV-X9 Aetheris (Block II) |
| **Project Reference** | AVT-MOD-PROP-2026-R4 |
| **Target Evaluation Standard** | High-Altitude Long-Endurance Tactical UAS / Defense Evaluation Standard |
| **Prepared By** | Priyanka Sharma |
| **Assigned Engineering Role** | Systems Requirements & Configuration Engineer |
| **Authorizing Task Order** | TRAIN-002 (Requirements Baseline) |
| **Issue Date** | 22 October 2026 |
| **Document Version** | Version 0.2 — Updated Baseline (AeroVanguard AV-X9 Reference) |
| **Document Status** | Draft — For Internal Engineering Review |
| **Primary Source Document** | `AVT-AETH-2026-X9` (*AV-X9 Aetheris Platform: Project Introduction & System Architecture Overview*, authored by Dr. Aris Thorne, VP of Defense Engineering, AeroVanguard Technologies Ltd.) |

### 1.2 Revision History
| Revision | Release Date | Author / Role | Description of Changes / Release Notes | Status |
|---|---|---|---|---|
| **v0.1** | 22 October 2026 | Priyanka Sharma<br>*Systems Requirements & Configuration Engineer* | Initial draft created under Task Order TRAIN-002. | Superseded |
| **v0.2** | 22 October 2026 | Priyanka Sharma<br>*Systems Requirements & Configuration Engineer* | Comprehensive baseline realignment incorporating primary technical blueprint `AVT-AETH-2026-X9`. Integrated confirmed technical parameters: operational ceiling 6,500m AMSL, wind shear up to 25 m/s, -30°C thermal envelope, 1550nm 1.2 Gbps FSO link (18 km range), 4K Sony CMOS + 640x512 FLIR Boson LWIR gimbal, 275 TOPS Nvidia Jetson Orin Industrial SOM, <250 µs inner-loop latency, DO-178C / DO-254 safety standards, and <0.8m/hr GNSS-denied VIO drift bounds. | Draft — For Internal Review |

---

## 2. Purpose

The purpose of this Project Scope Baseline document is to establish a rigorous, traceable, and unambiguous systems-engineering foundation for the **AeroVanguard AV-X9 Aetheris (Block II)** autonomous high-altitude tactical Unmanned Aerial System (UAS).

Specifically, this document:
1. **Defines System Scope and Boundaries:** Formally delineates the physical, electromagnetic, and cyber boundaries of the AV-X9 Aetheris platform, bounding onboard avionics, sensory ingress, edge compute substrates, and tactical effectors.
2. **Decomposes Major System Functions:** Identifies and documents primary system functions across the 18 core PECLF subsystems, establishing clear functional ownership.
3. **Establishes the Requirements Baseline:** Serves as the authoritative engineering input for subsequent authoring of the System Requirements Specification (SRS), Subsystem Requirements Documents (SSRDs), Interface Control Documents (ICDs), and Verification Cross-Reference Matrices (VCRM).
4. **Governs Constraints and Assumptions:** Catalogs technical, environmental, operational, and regulatory constraints (including DO-178C and DO-254 compliance tracking) alongside genuine engineering assumptions.
5. **Differentiates Task Training Authorization from Lifecycle Roadmap:** Explicitly distinguishes desk-based requirements modeling under Task `TRAIN-002` from the capital-intensive 18-month hardware manufacturing, HIL integration, and flight evaluation roadmap.
6. **Catalogs Unresolved Technical Decisions:** Identifies open technical questions and interface parameters requiring stakeholder closure during Milestone 1 (M1–4).

---

## 3. Project Overview

### 3.1 Platform Identity and Stated Purpose
The **AeroVanguard AV-X9 Aetheris (Block II)**—designated under Project Reference **`AVT-MOD-PROP-2026-R4`**—is a sovereign, autonomous multi-role Unmanned Aerial System (UAS) engineered specifically for persistent Intelligence, Surveillance, and Reconnaissance (ISR) and precision tactical logistics across severe high-altitude mountain frontiers and complex electronically jammed airspace.

### 3.2 Operational Challenges Addressed
The AV-X9 Aetheris platform is architected to eliminate four fundamental operational bottlenecks inherent in conventional commercial and legacy military drones:
*   **GNSS Jamming & Spoofing:** Hostile high-power Electronic Warfare (EW) emitters cause complete loss of GPS/GLONASS signals, inducing catastrophic positional drift, fly-aways, and mission loss in standard UAS.
*   **Extreme Alpine Weather:** Low atmospheric density at high altitudes ($\approx 6,000\text{m}$ to $6,500\text{m}$ AMSL) combined with extreme sub-zero freezing temperatures (down to $-30^\circ\text{C}$) degrades aerodynamic lift, drops motor efficiency by up to 35%, and drastically cuts electrochemical battery discharge capacity.
*   **High RF Signature:** Legacy omnidirectional radio command and video transmissions allow enemy spectrum analyzer units to detect, locate, and counter-target drone operating positions and friendly launch sites.
*   **Telemetry Latency & Congestion:** Streaming raw uncompressed high-definition video over congested tactical radio bands saturates scarce tactical bandwidth and exposes ground telemetry stations to adversary RF direction-finding.

### 3.3 Core Engineering Innovations and Concepts
*   **Physical-Electromagnetic-Cyber Layer Fusion (PECLF):** An 8-layer unified system framework combining carbon-composite stealth aerodynamics, cold-weather dual-stage brushless propulsion, multi-spectral optoelectronics, wideband RF monitoring, TPM 2.0 silicon security, and real-time neural edge inference engines into a single synchronized tactical asset.
*   **AeroCore Heterogeneous Edge AI Substrate:** Zero-cloud onboard inferencing powered by an Nvidia Jetson Orin Industrial System-on-Module (SOM) featuring 64GB RAM and 275 TOPS compute rating (with 32 TOPS dedicated NPU/GPU tensor hardware), executing INT8-quantized YOLOv8 and Vision Transformer models at 60 FPS.
*   **AetherNav Resilient VIO Matrix:** Continuous, drift-bounded 6-DOF navigation combining dual stereo visual odometry, tactical-grade 200Hz IMU units, and onboard Digital Elevation Model (DEM) terrain matching, sustaining position error $<0.8\text{m}$ per hour without satellite navigation.
*   **AetherBeam Optical Laser Link:** Directional 1550nm Free-Space Optical (FSO) laser array utilizing coarse-fine fast steering mirrors, delivering jam-proof 1.2 Gbps data throughput up to 18 km line-of-sight, backed by encrypted Software-Defined Radio (SDR) channels.
*   **Multi-Spectral Perception Suite (OptiSight):** Gyro-stabilized daylight 4K Sony CMOS optical gimbal, 640x512 uncooled FLIR Boson Long-Wave Infrared (LWIR) bolometer, 4-channel acoustic microphone array, and micro-GPR subsurface sensing.
*   **Stealth & Structural Resilience:** Faceted low-RCS carbon monocoque airframe with embedded radar-absorbing material (RAM) and integrated heating coils, yielding an estimated RCS $<0.01\text{ m}^2$ across X and Ku radar bands.
*   **Hardware Root of Trust & Data Sovereignty:** TPM 2.0 cryptographic security vault enforcing cryptographically signed firmware boot steps, encrypted memory partitions, and instantaneous zero-trace RAM and flash memory purging upon airframe capture or breach.

### 3.4 Stated Development Lifecycle
Project AV-X9 Aetheris executes across an 18-month phased engineering lifecycle governed by a 5-Tier Sovereign Indigenization Framework and a strict 10-Tier Verification Ladder:
*   **Milestone 1 (Months 1–4):** Digital Twin & Software Simulation Freeze (VanguardFlight OS, Gazebo simulation, baseline neural optimization).
*   **Milestone 2 (Months 5–8):** Bench-Level Hardware-in-the-Loop (HIL) Testbed & Thermal Profiling down to $-30^\circ\text{C}$.
*   **Milestone 3 (Months 9–12):** Alpha Airframe Prototype Fabrication & Controlled Tethered/Free Flight Trials.
*   **Milestone 4 (Months 13–16):** Beta Integrated Multi-Modal Payload Prototype & GNSS-Denied Corridor Flight Trials.
*   **Milestone 5 (Months 17–18):** Pre-Induction High-Altitude Field Trials & Defense Qualification Dossier Compilation.

---

## 4. System Scope

The system scope of the AeroVanguard AV-X9 Aetheris (Block II) encompasses the complete tactical UAS, bounded by its carbon monocoque airframe, optical/RF apertures, sensory interfaces, and secure ground communication links:

```mermaid
graph TD
    subgraph AV_X9_System_Boundary ["AeroVanguard AV-X9 Aetheris (Block II) Platform Boundary"]
        subgraph Ingress_Layer ["Layer A: Physical Perception Suite (OptiSight & Transducers)"]
            S1[4K Daylight Sony CMOS Gimbal]
            S2[640x512 FLIR Boson LWIR Sensor]
            S3[Tactical-Grade 200Hz IMU]
            S4[4-Channel Acoustic Microphone Array]
            S5[Micro-GPR Subsurface Radar]
            S6[10 MHz - 6 GHz SDR Antenna Array]
        end

        subgraph Edge_Compute ["Layer C: AeroCore Edge-AI Processing Fabric"]
            C1[Nvidia Jetson Orin Industrial SOM - 64GB RAM / 275 TOPS]
            C2[Vanguard-Linux OS - 5.15 PREEMPT_RT / ROS 2 Humble]
            C3[TensorRT 8.5 INT8 Execution Pipeline - 60 FPS]
            C4[Zero-Copy Shared Memory IPC Queues]
        end

        subgraph Flight_Avionics ["Layer B: Avionics & Flight Stabilization Core"]
            F1[Dual-Redundant STM32H7 ARM Cortex-M7 MCUs]
            F2[VanguardFlight OS / Custom PX4 Autopilot Stack]
            F3[Deterministic Control Loops < 250 µs Latency]
            F4[Dual Redundant CAN-BUS 2.0B Micro-XRCE Bridge]
        end

        subgraph Comms_Effectors ["Layer E & G: Tactical Communications & Effectors"]
            E1[AetherBeam 1550nm Directional FSO Laser - 1.2 Gbps / 18 km]
            E2[Encrypted Frequency-Hopping SDR RF Backup Link]
            E3[AeroDrop Precision Logistical Cargo Pod]
            E4[Opto-Isolated Dual-Redundant Discrete Release Interlocks]
        end

        subgraph Cyber_Enclave ["Layer H: Cybersecurity Enclave (TPM 2.0)"]
            H1[TPM 2.0 Silicon Root of Trust]
            H2[Cryptographically Signed Secure Bootloader]
            H3[Zero-Trace Instant RAM & Flash Memory Purge Circuit]
        end
    end

    %% Interfaces
    Ingress_Layer -->|MIPI-CSI 4-Lane / SPI / USB 3.0 / PCIe x2| Edge_Compute
    Edge_Compute <-->|Redundant CAN-BUS 2.0B / MAVLink 2.0| Flight_Avionics
    Flight_Avionics -->|Opto-Isolated IO / RS-422| Comms_Effectors
    Cyber_Enclave -.->|Hardware Interlock & Sanitization| Edge_Compute
    Cyber_Enclave -.->|Hardware Interlock & Sanitization| Flight_Avionics

    E1 -.->|Line-of-Sight Laser Beam| Ground_FSO[Friendly Optical Ground Terminal]
    E2 -.->|Encrypted SDR Channel| Tactical_GCS[Tactical Ground Control Station]
```

### 4.1 System Subsystems Breakdown (18 Core Subsystems across PECLF)
1. **Module 01: VIO Navigation Subsystem (AetherNav):** Fuses dual optical feature streams, tactical 200Hz IMU, and DEM databases to achieve $<0.8\text{m}$ drift per hour under satellite denial.
2. **Module 02: Multi-Spectral Perception Subsystem (OptiSight):** Dual-sensor daylight 4K Sony CMOS and 640x512 uncooled FLIR Boson thermal camera over MIPI-CSI 4-Lane Gen3 direct DMA.
3. **Module 03: Edge-AI Engine Subsystem (AeroCore):** Nvidia Jetson Orin Industrial SOM (64GB RAM, 275 TOPS, 32 TOPS tensor core) running TensorRT 8.5 INT8 models at 60 FPS for segmentation, YOLOv8 object extraction, and change detection.
4. **Module 04: EW & DSP Sensing Subsystem (SpectraSense):** Wideband SDR covering 10 MHz to 6 GHz and 4-channel acoustic array running TDoA signal processing.
5. **Module 05: Laser Communications Subsystem (AetherBeam):** 1550nm narrow-beam Free-Space Optical laser providing 1.2 Gbps data transfer up to 18 km line-of-sight via fast steering mirrors over RS-422.
6. **Module 06: Payload Delivery Unit Subsystem (AeroDrop):** Wind-compensated precision logistical cargo delivery managed via pitot tube wind estimation and dual-redundant opto-isolated interlocks.
7. **Subsystem 07: Avionics & Flight Stabilization:** Dual-redundant STM32H7 microcontrollers executing VanguardFlight OS with $<250\ \mu\text{s}$ deterministic attitude loops.
8. **Subsystem 08: Autopilot Communications Bridge:** Redundant CAN-BUS 2.0B transporting MAVLink 2.0 packets via micro-XRCE agents.
9. **Subsystem 09: Structural Airframe & Stealth:** Faceted carbon-composite monocoque airframe with embedded RAM yielding RCS $<0.01\text{ m}^2$ (X and Ku bands).
10. **Subsystem 10: High-Altitude Propulsion:** Dual-stage high-efficiency brushless electric motors matched to high-altitude low-Reynolds propeller blades.
11. **Subsystem 11: Thermal Battery Management:** Self-heating insulated battery cells maintaining nominal discharge down to $-30^\circ\text{C}$.
12. **Subsystem 12: Pitot-Static & Air Data System:** Measures airspeed, barometric altitude, and ambient density profiles up to 6,500m AMSL.
13. **Subsystem 13: Micro-GPR Subsurface Radar:** High-frequency subsurface ground-penetrating radar streaming 16-bit IQ samples over USB 3.0 / PCIe x2.
14. **Subsystem 14: Secondary Tactical RF Data Link:** Frequency-hopping, cryptographically encrypted SDR RF transceiver for optical link fallback.
15. **Subsystem 15: Fast Steering Mirror (FSM) PAT:** 200Hz closed-loop gyro-compensated steering mirrors ensuring laser tracking under 25 m/s wind shear.
16. **Subsystem 16: TPM 2.0 Hardware Security Vault:** Cryptographic enclave enforcing Secure Boot and managing encrypted partitions.
17. **Subsystem 17: Anti-Tamper & Zero-Trace Sanitization Circuitry:** Active micro-switches and voltage monitoring triggering instant flash memory destruction and RAM purging upon capture.
18. **Subsystem 18: Digital Twin & SITL Environment:** High-fidelity Gazebo simulation models replicating Himalayan terrain, 25 m/s wind turbulence, and EW jamming.

---

## 5. In-Scope Activities

### 5.1 Overall 18-Month Project Scope (`AVT-MOD-PROP-2026-R4`)
*   System Requirements Specification (SRS) baselining and DO-178C / DO-254 compliance tracking.
*   Gazebo digital twin simulation modeling with full vehicle dynamics in alpine wind shear.
*   Software-in-the-Loop (SIL) and Hardware-in-the-Loop (HIL) testbed assembly and verification.
*   Nvidia Jetson Orin Industrial edge AI pipeline compilation with TensorRT 8.5 INT8 models.
*   Carbon monocoque airframe fabrication, wind tunnel testing, and RAM material integration.
*   Sub-zero environmental chamber qualification down to $-30^\circ\text{C}$ (Tier 5).
*   Tethered hover trials (Tier 6), clean open-air flight (Tier 7), and GNSS-denied flight corridors (Tier 8).
*   Multi-sensor integrated payload flight trials (Tier 9) and high-altitude field demonstration at 6,500m AMSL (Tier 10).

### 5.2 Current Training Authorization Scope (`TRAIN-002`, 22 October 2026)
*   Systems requirements analysis and technical decomposition of blueprint `AVT-AETH-2026-X9`.
*   Authoring and configuration control of the official Project Scope Baseline document (`P01_Project_Scope_Baseline.md`).
*   Identification, formalization, and maintenance of the project Constraints Register, Assumptions Register, and Open Scope Questions Register.
*   Authoring and verification of the multi-tab Initial Requirements Register workbook (`P02_Initial_Requirements_Register.xlsx`).
*   Local desk-based modeling, documentation verification, and Git version control workflows within the authorized workspace.

---

## 6. Out-of-Scope Activities and Boundaries

### 6.1 Explicitly Out-of-Scope Under Task Order TRAIN-002
*   **Live Flight Testing:** Prohibited under `TRAIN-002` (applies to project Milestones M3–M5).
*   **Outdoor Field Deployment:** Prohibited under `TRAIN-002` (applies to project Milestone M5).
*   **Physical Hardware Assembly & Wiring:** Prohibited under `TRAIN-002` (applies to HIL Testbed M2).
*   **Hardware / Prototype Procurement:** Prohibited under `TRAIN-002` financial restrictions.
*   **Paid Commercial Cloud Services & APIs:** Prohibited under `TRAIN-002` resource constraints.
*   **Personal Financial Outlays:** Prohibited under `TRAIN-002` governance controls.

---

## 7. Major System Functions

| Function ID | System Function | Description | Relevant Subsystem / Layer | Source Reference |
|---|---|---|---|---|
| **FUNC-DFT-001** | Dual-Stream 4K/LWIR Perception Ingress | Capture and hardware-synchronize 4K daylight Sony CMOS video and 640x512 uncooled FLIR Boson thermal video via MIPI-CSI 4-Lane Gen3 DMA. | OptiSight / Layer A | Sec 1.2, Sec 7 (Mod 02), Sec 8.1 |
| **FUNC-DFT-002** | Acoustic Impulse Localization | Ingest 4-channel microphone signals and compute directional Time-Difference-of-Arrival (TDoA) bearing vectors to hostile acoustic emissions. | SpectraSense / Layer A & D | Sec 1.2, Sec 4, Sec 7 (Mod 04) |
| **FUNC-DFT-003** | Subsurface Radar Ingress | Capture 16-bit IQ samples from a micro-GPR antenna over USB 3.0 / PCIe x2 into dedicated DSP buffers to detect buried tactical targets. | SpectraSense / Layer A & C | Sec 3.2, Sec 8.1 |
| **FUNC-DFT-004** | Precision GNSS-Denied 6-DOF State Estimation | Fuse dual optical feature streams, tactical 200Hz IMU rates, and DEM databases via EKF3 to sustain position error $<0.8\text{m}$ per hour without GNSS. | AetherNav / Layer B | Sec 1.1, Sec 2.2, Sec 7 (Mod 01) |
| **FUNC-DFT-005** | High-Rate Deterministic Flight Control | Execute closed-loop attitude stabilization and waypoint trajectory execution with latency $<250\ \mu\text{s}$ on dual STM32H7 microcontrollers. | VanguardFlight OS / Layer B | Sec 1.1, Sec 1.2, Sec 8.2, Sec 10 |
| **FUNC-DFT-006** | Zero-Cloud Edge Semantic Segmentation | Execute INT8-quantized YOLOv8 and Vision Transformer models onboard at 60 FPS using Nvidia Jetson Orin Industrial SOM (275 TOPS). | AeroCore / Layer C & F | Sec 1.1, Sec 6.1, Sec 6.2 |
| **FUNC-DFT-007** | Temporal Optical Change Detection | Perform real-time comparative neural inferencing between live video and historical terrain embeddings to detect ground infrastructure alterations. | AeroCore / Layer F | Sec 1.1, Sec 2.2, Sec 7 (Mod 03) |
| **FUNC-DFT-008** | Wideband RF Spectrum Sensing | Continuously scan radio frequencies from 10 MHz to 6 GHz using Software-Defined Radio to generate RF spectrum occupancy grids and emitter profiles. | SpectraSense / Layer D | Sec 4, Sec 7 (Mod 04) |
| **FUNC-DFT-009** | Directional 1550nm Laser Communications | Transmit high-bandwidth mission intelligence at 1.2 Gbps up to 18 km line-of-sight over a directional 1550nm FSO optical laser array. | AetherBeam / Layer E | Sec 1.1, Sec 2.2, Sec 7 (Mod 05) |
| **FUNC-DFT-010** | Closed-Loop Fast Steering Mirror (FSM) Tracking | Maintain optical laser beam tracking using 200Hz gyro coordinate offsets over RS-422, compensating for airframe vibration and 25 m/s wind shear. | AetherBeam / Layer E | Sec 4, Sec 8.1 |
| **FUNC-DFT-011** | Encrypted Tactical SDR Fallback Link | Maintain frequency-hopping, cryptographically encrypted RF communications for command and telemetry fallback when optical links are obscured. | Layer E | Sec 2.2, Sec 5.2 (Stage 5) |
| **FUNC-DFT-012** | Wind-Compensated Ballistic Cargo Release | Compute ballistic release trajectories using real-time pitot wind estimates and ground speed, triggering precision logistical cargo pod unlatching. | AeroDrop / Layer G | Sec 7 (Mod 06), Sec 8.1 |
| **FUNC-DFT-013** | Dual-Redundant Effector Safety Interlocking | Inforce opto-isolated solid-state dual high/low discrete logic interlocks to prevent uncommanded release or accidental drop during boot/fault states. | AeroDrop / Layer G | Sec 8.1 |
| **FUNC-DFT-014** | Continuous Health & Watchdog Audit | Continuously monitor subsystem heartbeats over redundant CAN-BUS 2.0B, executing autonomous failsafe return-to-base on link loss. | Layer B & Layer C | Sec 8.1, Sec 8.2 |
| **FUNC-DFT-015** | TPM 2.0 Cryptographic Secure Boot | Cryptographically verify all boot steps, kernel binaries, and ROS 2 Humble nodes from silicon power-on using hardware TPM 2.0 root of trust. | Cybersecurity Enclave / Layer H | Sec 1.2, Sec 6.1, Sec 6.2 |
| **FUNC-DFT-016** | Instant Zero-Trace Memory Purging | Execute hardware-enforced cryptographic destruction of flash memory and instant RAM purging upon detection of airframe capture or enclosure breach. | Cybersecurity Enclave / Layer H | Sec 1.2, Sec 3.2, Sec 6.2 |

---

## 8. System Architecture and Boundaries

### 8.1 The 8-Layer PECLF Framework
| Layer Identifier | Layer Name | Principal Functional Responsibility | Documented Inter-Layer Relationships & Data Transfers |
|---|---|---|---|
| **Layer A** | Sensor Ingress | Captures 4K visual, 640x512 thermal, 10MHz–6GHz RF, acoustic, and subsurface radar signals without cloud assistance. | Streams raw frames via MIPI-CSI 4-Lane Gen3 DMA and USB 3.0/PCIe x2 into Layer C; feeds micro-switches to Layer H. |
| **Layer B** | VIO Pose Estimator | Fuses high-rate 200Hz IMU, visual odometry, and DEM elevation databases via EKF3 to generate 6-DOF vehicle pose for autopilot. | Transmits 6-DOF pose and velocity vectors to PX4 inner loops; exchanges mission data with Layer C over redundant CAN-BUS 2.0B. |
| **Layer C** | AeroCore Compute | High-throughput edge computing engine (Nvidia Jetson Orin Industrial SOM, 64GB RAM, 275 TOPS) managing shared memory IPC queues. | Ingests raw data from Layer A; drives TensorRT 8.5 INT8 models; routes tactical data to Layer E and Layer F. |
| **Layer D** | RF Spectrum Monitor | Monitors 10 MHz to 6 GHz contested spectrum, characterizes hostile RF signatures, and maps occupancy grids. | Delivers RF intercept vectors and jamming alerts to Layer B (for evasive path planning) and Layer E (for link adaptation). |
| **Layer E** | Laser/SDR Data Link | High-bandwidth 1550nm directional FSO laser (1.2 Gbps, 18 km range) backed by frequency-hopping encrypted SDR. | Receives compressed video and target coordinates from Layer F/C; forwards ground command packets to Layer B. |
| **Layer F** | AI Target Engine | Executes onboard neural inferencing (YOLOv8, Vision Transformers) for object extraction, segmentation, and change detection at 60 FPS. | Consumes synchronized tensors from Layer C; outputs target bounding boxes, classifications, and alerts to Layer B, E, and G. |
| **Layer G** | Authorized Effectors | Controls wind-compensated AeroDrop logistical cargo pod unlatching and defense equipment under hardware interlocks. | Receives trigger signals from Layer B/F; governed by opto-isolated dual-redundant discrete logic interlocks and Layer H authority. |
| **Layer H** | Cybersecurity Enclave | TPM 2.0 hardware root of trust enforcing secure boot, signed firmware validation, and auto-destruct zero-trace RAM/flash wipe. | Cryptographically interlocks boot authorization for Layers B, C, and G; triggers instant memory wipe upon physical enclosure breach. |

### 8.2 Architectural Isolation Firewalls
*   **Asynchronous Hardware Firewall:** The flight control system runs on dedicated dual-redundant bare-metal ARM Cortex-M7 processors (STM32H7) physically independent of the Linux Edge-AI compute module. Any software crash or memory overload within the neural inference engine cannot compromise inner-loop attitude stability ($<250\ \mu\text{s}$ latency), waypoint navigation, or return-to-base protocols.
*   **Direct Memory Access (DMA) Ingress:** Multi-lane MIPI-CSI Gen3 camera buses stream directly into GPU memory via DMA, eliminating CPU overhead and maintaining zero frame drops.
*   **Air-Gapped Vanguard-Linux Environment:** All inter-process communication is confined to local shared memory IPC queues (POSIX `shm`) under hardened Linux 5.15 PREEMPT_RT, with complete physical and logical isolation from unauthenticated external networks.
*   **Opto-Isolated Effector Interlocks:** Cargo pod release lines use opto-isolated solid-state I/O requiring dual-redundant discrete logic signals, preventing uncommanded release during boot transients or subsystem fault states.

---

## 9. Constraints

| Constraint ID | Constraint Description | Category | Source / Reason | Status / Clarification |
|---|---|---|---|---|
| **CST-ENV-001** | **Operational Flight Ceiling:** The airframe, aerodynamics, and propulsion must operate up to 6,500m AMSL. | Environmental | `AVT-AETH-2026-X9`, Executive Summary | **Confirmed Design Specification.** |
| **CST-ENV-002** | **Wind Shear Envelope:** The flight control and airframe must withstand localized mountain wind shear up to 25 m/s. | Environmental | `AVT-AETH-2026-X9`, Executive Summary | **Confirmed Design Specification.** |
| **CST-ENV-003** | **Sub-Zero Thermal Envelope:** All electronics, propulsion, and self-heating battery cells must operate down to -30°C. | Environmental / Thermal | `AVT-AETH-2026-X9`, Executive Summary & Tier 5 | **Confirmed Design Specification.** |
| **CST-SAF-001** | **DO-178C & DO-254 Compliance:** Flight software and avionics electronic hardware must follow DO-178C and DO-254 safety processes. | Safety / Regulatory | `AVT-AETH-2026-X9`, Sec 4 (Systems Safety) | **Confirmed Compliance Requirement.** |
| **CST-ARC-001** | **Zero-Cloud Air-Gapped Architecture:** All state estimation, AI inferencing, and mission logic must execute onboard without cloud reliance. | Architectural | `AVT-AETH-2026-X9`, Sec 1.1 | **Confirmed Requirement.** |
| **CST-ARC-002** | **Hardware Flight Control Isolation:** Bare-metal ARM Cortex-M7 (STM32H7) must remain physically segregated from Linux edge compute. | Architectural / Safety | `AVT-AETH-2026-X9`, Sec 8.2 | **Confirmed Requirement.** |
| **CST-TRN-001** | **Zero Physical Deployment:** No live flight testing, outdoor trials, or hardware procurement under Task Order TRAIN-002. | Operational / Training | Task Order `TRAIN-002` Restrictions | **Active & Mandatory for Current Task.** |

---

## 10. Assumptions Register

| Assumption ID | Assumption Statement | Rationale | Impact if Incorrect | Validation Needed | Status |
|---|---|---|---|---|---|
| **ASM-ENG-001** | **Maximum Takeoff Weight (MTOW) & Payload Capacity:** It is assumed that MTOW ($\approx 25\text{–}40\text{ kg}$) and payload mass capacity exist in the classified proposal annex `AVT-MOD-PROP-2026-R4`. | Blueprint provides operating ceiling (6,500m) and motor efficiency, but exact airframe mass values are omitted. | Discrepancy in structural stress calculations and motor thrust sizing during Milestone 3. | Project Lead (Dr. Aris Thorne) confirmation of MTOW and payload mass. | **Pending Confirmation** |
| **ASM-ENG-002** | **Flight Endurance Target:** It is assumed that mission endurance is designed for $\ge 4\text{ to }6\text{ hours}$ based on high-altitude long-endurance UAS domain classification. | Classified under Target Domain: High-Altitude Long-Endurance Tactical UAS. | Sizing of battery management system and thermal insulation pack. | Confirmation of nominal and threshold mission endurance hours. | **Pending Confirmation** |
| **ASM-ENG-003** | **Ground Optical Terminal Interface:** It is assumed that ground optical FSO receiving terminals are developed under a separate GCS work package. | System blueprint defines airborne 1550nm laser head and 18 km line-of-sight range. | Unallocated interface responsibilities between airborne transceiver and ground terminal. | Definition of ground terminal interface standards in future ICD. | **Pending Confirmation** |

---

## 11. Dependencies and External Interfaces

### 11.1 Documented Hardware & Software Interfaces
*   **Camera to AI Core:** MIPI-CSI 4-Lane Gen3 streaming raw YUV422 and 14-bit thermal video directly via DMA.
*   **SDR to DSP Engine:** USB 3.0 / PCIe x2 streaming 16-bit IQ complex samples into prioritized DSP ring buffers.
*   **Autopilot Bridge:** Redundant CAN-BUS 2.0B transporting MAVLink 2.0 packets between PX4 autopilot and ROS 2 Humble micro-XRCE agents.
*   **Cargo Release Interlock:** Opto-isolated solid-state discrete I/O with dual high/low logic signals.
*   **FSO Laser Gimbal:** High-speed RS-422 bus transmitting 200Hz gyro coordinate vectors to fast steering mirrors.

### 11.2 External Operational Interfaces
*   **Friendly Optical Ground Station:** Line-of-sight 1550nm laser beam reception up to 18 km range at 1.2 Gbps throughput.
*   **Tactical GCS (RF):** Secondary encrypted SDR frequency-hopping command/telemetry link.
*   **Tactical Drop Zone:** Physical ground drop target receiving precision aerodynamic logistical payloads via AeroDrop unlatch actuation.

---

## 12. Open Questions and Clarifications

| Question ID | Open Question / Parameter Gap | Impact | Relevant Source | Required Clarification |
|---|---|---|---|---|
| **QUE-SCP-001** | What are the exact numerical values for **Maximum Takeoff Weight (MTOW)** and **AeroDrop payload mass limit** (in kg)? | Essential for propulsion sizing, battery pack dimensioning, and Gazebo flight simulation. | Executive Summary, Sec 7 (Mod 06) | VP of Defense Engineering to confirm MTOW and cargo pod mass limits. |
| **QUE-SCP-002** | What is the target **mission flight endurance** (hours) under continuous operating conditions at -30°C? | Dictates battery pack capacity (Wh) and self-heating energy budget. | Executive Summary, Sec 2.1 | Propulsion team to define endurance threshold at 6,500m AMSL. |
| **QUE-SCP-003** | What specific **DO-178C and DO-254 Design Assurance Levels (DAL)** (e.g. DAL B vs DAL C) apply to VanguardFlight OS and STM32H7 avionics? | Establishes the rigor of formal verification, structural coverage (MC/DC), and artifact audit requirements. | Sec 4 (Systems Safety) | Systems Safety lead to publish formal Software/Hardware Development Plans (PSAC / PHAC). |

---

## 13. Scope Risks and Boundary Issues

*   **RSK-SCP-001: Thermal Power Balance at -30°C in Rarefied Air:** Dual brushless motors, self-heating battery cells, and 275 TOPS Orin compute generate conflicting thermal profiles in thin air ($\approx 0.5\text{ kg/m}^3$). Mitigated by Milestone 2 bench-level thermal profiling and Tier 5 environmental chamber validation.
*   **RSK-SCP-002: FSO Optical Laser Alignment under 25 m/s Wind Shear:** Laser link stability at 18 km requires fast steering mirror jitter compensation under severe turbulence. Mitigated by closed-loop 200Hz gyro feedback over RS-422 and automated fallback to encrypted SDR RF.
*   **RSK-SCP-003: Safety Certification Overhead (DO-178C / DO-254):** Compliance tracking for dual STM32H7 firmware requires extensive structural coverage and traceability dossiers. Mitigated by early baseline freeze in Milestone 1.

---

## 14. Scope Acceptance and Review Checklist

| Checklist Review Item | Verification Criteria | Status | Engineering Notes |
|---|---|---|---|
| **Document Control & Metadata** | Identifies project name, document ID, role, author, date, version, status, and source reference. | **Complete** | Formally aligned with `AVT-MOD-PROP-2026-R4` and `AVT-AETH-2026-X9`. |
| **Purpose Definition** | Clear justification for scope baseline establishment and its role in requirements engineering. | **Complete** | Establishes single source of truth for SRS, SSRDs, and ICDs. |
| **System Overview & Context** | Details platform purpose, operational challenges, core technologies, and 18-month lifecycle. | **Complete** | Details 6,500m ceiling, 25 m/s wind shear, -30°C cold, and PECLF concept. |
| **System Scope & Boundaries** | Defines physical, logical, sensory, and computational boundaries across all PECLF layers. | **Complete** | Details 18 subsystems across 8 layers with Mermaid architectural diagram. |
| **In-Scope Boundary Definition** | Segregates overall 18-month project activities from authorized training scope. | **Complete** | Explicitly separates overall project from `TRAIN-002` desk tasks. |
| **Out-of-Scope Boundary Definition** | Explicitly catalogs training restrictions without misrepresenting the wider project roadmap. | **Complete** | Confirms flight testing occurs in later project phases (M3–M5). |
| **Major System Functions** | Structured table documenting major functions with descriptions, subsystems, and source citations. | **Complete** | Formally cataloged in Section 7 (FUNC-DFT-001 through FUNC-DFT-016). |
| **PECLF Architecture Mapping** | Summarizes 8 layers, table of responsibilities, and structural isolation firewalls. | **Complete** | Details bare-metal Cortex-M7 vs Linux Orin SOM decoupling (<250 µs latency). |
| **Constraints Register** | Catalogs training, technical, operational, environmental, and DO-178C/DO-254 constraints. | **Complete** | Comprehensive register created in Section 9 (CST-ENV-001 to CST-TRN-001). |
| **Assumptions Register** | Identifies genuine engineering assumptions requiring confirmation, their rationale, and impact. | **Complete** | Documented in Section 10 (ASM-ENG-001 to ASM-ENG-003). |
| **Dependencies & External Interfaces** | Documents internal inter-module data buses and external communication interfaces. | **Complete** | Fully outlined in Section 11 (MIPI-CSI, CAN-BUS 2.0B, USB 3.0, RS-422, FSO, SDR). |
| **Open Questions & Scope Decisions** | Captures unresolved technical decisions, performance threshold gaps, and missing details. | **Complete** | Tabulated in Section 12 (QUE-SCP-001 to QUE-SCP-003). |
| **Scope Risks & Boundary Issues** | Evaluates evidence-based technical risks, impacts, and engineering controls. | **Complete** | Detailed in Section 13 (RSK-SCP-001 to RSK-SCP-003). |
| **Source Traceability & Rigor** | Grounded strictly in supplied technical blueprint (`AVT-AETH-2026-X9`). | **Complete** | All claims cite specific sections of the AeroVanguard technical reference. |
| **Readiness for Peer Review** | Document is internally consistent, technically accurate, and structured for engineering review. | **Complete** | Ready for submission to Chief Systems Architect (Dr. Aris Thorne). |

---

## 15. References

1. **Primary Project Technical Overview:**
   * **Document ID:** `AVT-AETH-2026-X9`
   * **Title:** *AV-X9 Aetheris Platform: Project Introduction & System Architecture Overview (Next-Generation Autonomous High-Altitude Tactical Multi-Sensor Edge-AI System)*
   * **Author / Chief Systems Architect:** Dr. Aris Thorne, VP of Defense Engineering, AeroVanguard Technologies Ltd.
   * **Classification:** RESTRICTED / Commercial-in-Confidence / Technical Reference
   * **Cited Sections & Pages:**
     * Section 1: *System Definition* (Operational System Definition & Primary Engineering Domains) — Page 1 of 12
     * Section 2: *Operational Context* (Operational Bottlenecks Addressed & Objective Pillars) — Page 2 of 12
     * Section 3: *Architecture* (Layered Architecture Flow PECLF & Block Functional Overview) — Page 3 of 12
     * Section 4: *Engineering Domains* (Cross-Domain Technical Scope & 13 Specialized Disciplines) — Page 4 of 12
     * Section 5: *Information Flow* (End-to-End Information Processing Lifecycle & 7-Stage Pipeline) — Page 5 of 12
     * Section 6: *Technology Stack* (Ecosystem Architecture & Software Frameworks) — Page 6 of 12
     * Section 7: *Subsystem Modules* (Modular Subsystem Decomposition: Modules 01 to 06) — Page 7 of 12
     * Section 8: *Integration & Safety* (Hardware/Software Interface Standards & Isolation Firewalls) — Page 8 of 12
     * Section 9: *Lifecycle & Budget* (18-Month Development Roadmap & Budget Allocations) — Page 9 of 12
     * Section 10: *Testing Ladder* (10-Tier Verification Ladder & Formal Exit Criteria) — Page 10 of 12
     * Section 11: *Conclusion* (Strategic Horizon & Executive Summary at a Glance) — Page 11 of 12
2. **Authorizing Task Order:**
   * **Task Identifier:** `TRAIN-002`
   * **Task Name:** Requirements Baseline
   * **Assigned Role:** Systems Requirements & Configuration Engineer (Priyanka Sharma)
   * **Task Authorization Date:** 22 October 2026
   * **Mandated Deliverables:** `P01_Project_Scope_Baseline.md` & `P02_Initial_Requirements_Register.xlsx`
3. **Master Proposal Reference:**
   * **Proposal Identifier:** `AVT-MOD-PROP-2026-R4`
   * **Framework:** High-Altitude Long-Endurance Tactical UAS / Defense Evaluation Standard
