# RudraEdge RE-T1 (Spectra)

## Requirements Acceptance Criteria and Verification Plan

### 1. Document Control

| Document Control Field | Information / Specification |
|---|---|
| **Project Name** | Project Rudra-Tactical | Platform: RudraEdge RE-T1 (Spectra) |
| **Document Title** | Requirements Acceptance Criteria and Verification Plan |
| **Document Identifier / Reference** | `REA-T1-VERIF-PLAN-2026-V1.0` / `P04_Requirements_Acceptance_Criteria.md` |
| **Prepared By** | Priyanka Sharma |
| **Assigned Engineering Role** | Systems Requirements & Configuration Engineer |
| **Document Release Date** | 23 October 2026 |
| **Document Version** | Version 1.0 — Formal Baseline Verification Draft |
| **Document Status** | Under Review — Pending Systems Engineering Review Board (SERB) Approval |
| **Target Evaluation Standard** | iDEX / DIO / MoD High-Altitude Tactical UAS Evaluation Standard |
| **Applicable Source Documents** | 1. `REA-T1-OVERVIEW-2026-V1.0` (*RudraEdge RE-T1 Spectra: Project Introduction & Technical Overview*, authored by Sarvesh Sharma, Founder & Project Lead)<br>2. `RE-iDEX-PROPOSAL-2026-R1` (*Master iDEX Proposal: Autonomous Tactical UAV • Multi-Sensor Edge-AI*)<br>3. `P01_Project_Scope_Baseline.md` (*Project Scope Baseline: Tactical UAS Engineering Scope*, Version 0.2)<br>4. [`P03_Numbered_Requirements_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/P03_Numbered_Requirements_Register.xlsx) (*Numbered Requirements Register*, Version 1.0, 23 October 2026) |

---

### 2. Purpose and Scope

#### 2.1 Purpose
This document establishes objective, measurable, and verifiable **Acceptance Criteria** and corresponding **Verification Plans** for each of the 37 numbered requirements captured in the [`P03_Numbered_Requirements_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/P03_Numbered_Requirements_Register.xlsx) for the **RudraEdge RE-T1 (Spectra)** autonomous tactical unmanned aerial system (UAS).

The primary objective is to eliminate ambiguity in requirements interpretation by defining:
1. **Quantifiable Pass Conditions:** Concrete criteria that dictate whether a capability or component satisfies its engineering obligation.
2. **Standardized Verification Methods:** The rigorous assignment of verification categories (**Test**, **Analysis**, **Inspection**, **Demonstration**) aligned with aerospace engineering discipline.
3. **Reproducible Verification Procedures:** Step-by-step technical procedures specifying necessary test environments (SIL, HIL, Environmental Chamber, Tethered Flight, and GNSS-Denied Test Corridors).
4. **Decision Rules & Evidence Governance:** Clear pass/fail decision rules and the specific objective artifacts (bus logs, raw telemetry, chamber test reports, source code diffs, calibration certificates) that must be retained for defense airworthiness qualification.

#### 2.2 Scope and Boundaries
* **In-Scope:** Verification planning, acceptance criteria formulation, test environment identification, pass/fail threshold mapping, and technical gap documentation across all 37 requirements registered in `P03` (13 Functional, 2 Security, 10 Performance, 6 Safety, and 6 Documentation).
* **Strictly Out-of-Scope (Desk-Based Boundary):** This task is strictly bounded to systems requirements engineering, verification architecture, and test planning. It **does not** include physical UAV hardware fabrication, live laboratory environmental chamber operations, firmware compiling, physical flight testing, or outdoor field trials.
* **No False Claims of Verification:** In adherence to professional engineering ethics, no requirement is marked as 'Passed' or 'Verified'. All requirements are designated with the verification status of **Planned**, pending execution against the formal 10-Tier Validation Ladder during subsequent lifecycle milestones.

---

### 3. References and Assumptions

#### 3.1 Primary Technical References
1. **REA-T1-OVERVIEW-2026-V1.0:** *RudraEdge RE-T1 (Spectra) Project Introduction & Technical Overview*, RudraEdge Aerospace, authored by Sarvesh Sharma. Covers 8-Layer PECLF framework, 20 frozen advanced capabilities, 10-Tier Validation Ladder, and 18-month phased engineering lifecycle.
2. **RE-iDEX-PROPOSAL-2026-R1:** *Master Proposal: Autonomous Tactical UAV • Multi-Sensor Edge-AI*, iDEX / DIO Framework, Ministry of Defence (MoD), New Delhi.
3. **P01_Project_Scope_Baseline.md:** *Project Scope Baseline*, Version 0.2 (22 October 2026). Documents active project constraints, assumptions, and subsystem boundaries.
4. **P03_Numbered_Requirements_Register.xlsx:** *Numbered Requirements Register*, Release 1.0 (23 October 2026). Provides the authoritative 37-record numbered requirements ledger.

#### 3.2 Approved Project Specifications vs. Working Engineering Assumptions
To ensure strict configuration control, approved engineering specifications are rigorously isolated from working assumptions requiring confirmation:

| Parameter / Domain | Approved Baseline Specification (`REA-T1-OVERVIEW-2026-V1.0`) | Unresolved Working Assumption / Gap | Validation Action Required |
|---|---|---|---|
| **Operational Ceiling** | 6,500 m Above Mean Sea Level (AMSL) | Max climb rate at 6,500 m AMSL is assumed >= 2.5 m/s | Formal CFD & Gazebo simulation audit in Milestone 1 |
| **Wind Shear Tolerance** | Mountain gusts and shear up to 25 m/s | Sustained gust duration assumed 3.0 seconds | High-fidelity wind turbulence injection in Gazebo SIL |
| **Thermal Chamber Envelope** | Electronics & avionics nominal operation down to -20°C (M2 & Tier 5) | Extreme excursion survival down to -30°C for Siachen deployments | Environmental chamber test protocol freeze in HIL plan |
| **Inner-Loop Control Latency** | Under 1 millisecond (< 1 ms) on bare-metal microcontroller (Tier 3) | Target latency stretch goal of < 250 µs cited in preliminary drafts | Oscilloscope / hardware timer profiling in HIL bench |
| **GNSS-Denied Drift Bound** | Sub-meter drift bounds sustained during GNSS-denied flight (Tier 8) | Target numerical metric < 0.8 m/hr CEP (95% confidence interval) | Optical ground truth tracking corridor validation |
| **Optical Communications (FSO)** | Directional laser link backed by encrypted SDR RF fallback | Throughput >= 1.2 Gbps over 18 km line-of-sight range | Optical power budget & link margin analysis |
| **Edge AI Processing Capacity** | Heterogeneous CPU/GPU/NPU/DSP with sovereign Indian silicon roadmap | Target 275 TOPS Orin baseline progressing to C-DAC VEGA / SHAKTI | TensorRT INT8 compiler benchmarking & power audit |
| **RF Spectrum Monitoring** | 400 MHz to 6 GHz wideband SDR RF antenna inputs (Module 04) | Lower band coverage down to 10 MHz evaluated as optional annex | Antenna size, VSWR matching, and front-end filter freeze |
| **Airframe Mass Properties** | Low-RCS faceted carbon-composite monocoque geometry | Maximum Takeoff Weight (MTOW) assumed ~25–40 kg; cargo payload ~5 kg | Structural weight budget sign-off by Project Lead |

---

### 4. Verification Method Definitions

In conformance with defense systems engineering standards (MIL-STD-961E, ISO/IEC/IEEE 29148, and the 10-Tier Validation Ladder), four distinct verification methods are applied:

```mermaid
graph TD
    VM[Verification Methods Hierarchy] --> T[Test: Quantitative Execution & Measurement]
    VM --> D[Demonstration: Qualitative Operational Execution]
    VM --> I[Inspection: Visual, Structural & Document Examination]
    VM --> A[Analysis: Mathematical Modeling, Simulation & Calculation]
    T --> ENV1[HIL / SIL Benches & Chamber Testing]
    D --> ENV2[SITL Gazebo & Controlled Flight Demonstrators]
    I --> ENV3[Schematics, Code Audits & Certification Packages]
    A --> ENV4[CFD, Radar RCS & Thermal Dissipation Models]
```

1. **Test (T):** Verification through systematic, instrumented execution of a component, subsystem, or integrated platform under specified operational or environmental stimuli. Quantitative measurements (e.g., latency in microseconds, drift in meters, throughput in Gbps, temperature in °C) are collected using calibrated measurement equipment and compared against numerical acceptance thresholds.
2. **Demonstration (D):** Verification through qualitative or observable operational execution of a functional feature without requiring precision parametric instrumentation. Confirms that an expected operational sequence, state transition, or functional mode executes successfully (e.g., automated laser fallback to SDR, waypoint sequencing, target bounding box display).
3. **Inspection (I):** Verification through visual, manual, or static automated examination of engineering deliverables, architectural drawings, circuit schematics, source code repositories, configuration files, and formal lifecycle documentation without active runtime execution (e.g., verifying physical circuit separation, checking git branch sign-offs, auditing DO-178C lifecycle data).
4. **Analysis (A):** Verification through mathematical modeling, aerodynamic simulations, computational fluid dynamics (CFD), structural finite element analysis (FEA), radar cross-section (RCS) electromagnetic modeling, or theoretical reliability and failure mode calculations (e.g., predicting RCS across X/Ku bands, proving thermal insulation dissipation margins).

---

### 5. Requirement-Wise Acceptance Criteria and Verification

The following subsections present the detailed acceptance criteria and verification plans for all 37 registered requirements. Requirement IDs, titles, and descriptions are preserved exactly from [`P03_Numbered_Requirements_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/P03_Numbered_Requirements_Register.xlsx).

#### REQ-F-001 — Multi-Spectral EO/IR Video Ingress & Synchronization

**Original Requirement:**
The system shall capture and hardware-synchronize daylight optical CMOS video and uncooled Long-Wave Infrared (LWIR) bolometer thermal video streams via high-speed MIPI-CSI camera interfaces routed directly to edge compute memory without host CPU overhead.

**Acceptance Criteria:**
* AC-1.1: The camera interface subsystem shall ingest both daylight optical video and uncooled LWIR bolometer thermal video streams simultaneously across dedicated MIPI-CSI multi-lane buses without CPU memory copying.
* AC-1.2: Hardware timestamp synchronization between corresponding optical and thermal video frames shall maintain an inter-frame skew of less than 5.0 milliseconds (<= 5.0 ms) under continuous operation.
* AC-1.3: Direct Memory Access (DMA) pipeline shall achieve zero frame drop (0% frame loss) across a continuous 30-minute stress capture bench run.

**Verification Method:**  
Demonstration

**Verification Procedure:**
1. Connect the multi-spectral EO/IR sensor rig to the edge compute board via the MIPI-CSI Gen3 interface in the Milestone 2 benchtop setup.
2. Initiate simultaneous dual-stream video capture across daylight optical and thermal bolometer sensors using the video ingress driver daemon.
3. Ingest frames into circular memory buffers for 30 continuous minutes while recording hardware GPIO frame sync strobe pulses and DMA transfer logs.
4. Compare hardware timestamps of corresponding optical and thermal frame pairs to compute delta skew and audit buffer frame drop counters.

**Required Inputs / Environment:**  
MIPI-CSI Gen3 dual camera rig (optical CMOS + LWIR bolometer), logic analyzer / oscilloscope monitoring hardware sync pulse, edge compute bench rig.

**Expected Result:**  
Dual synchronized video feeds populate shared memory via DMA; inter-stream frame timestamp delta <= 5 ms with zero buffer drops over 30 minutes.

**Pass/Fail Criteria:**  
PASS if dual streams ingest simultaneously with timestamp skew <= 5 ms and zero dropped frames over 30 minutes; FAIL if frame skew exceeds 5 ms or frame drop occurs.

**Verification Evidence:**  
Logic analyzer strobe timing capture plots, DMA memory buffer transfer logs, and 30-minute dual-stream raw video recordings.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Optical CMOS resolution (4K vs 1080p), lens focal length, and optical zoom ratios remain pending hardware vendor selection.

---

#### REQ-F-002 — Subsurface Micro-GPR Raw Data Ingress & Buffering

**Original Requirement:**
The system shall capture and stream 16-bit IQ complex radar samples from an onboard micro-Ground Penetrating Radar (GPR) antenna over high-speed SPI / USB 3.0 interfaces into prioritized DSP memory ring buffers to detect subsurface anomalies.

**Acceptance Criteria:**
* AC-2.1: The GPR ingress pipeline shall capture 16-bit in-phase and quadrature (IQ) raw complex radar echo samples from the antenna interface.
* AC-2.2: Data transfer across the high-speed SPI / USB 3.0 physical bus shall stream continuously into dedicated DSP ring buffers without ring-buffer overflow or memory stalls.
* AC-2.3: [TBD — Requires Engineering Clarification] Minimum pulse repetition frequency (PRF), radar center frequency (MHz/GHz), and maximum detectable soil/ice penetration depth (meters) must be formally specified.

**Verification Method:**  
Test

**Verification Procedure:**
1. Connect the micro-GPR front-end digital emulator to the high-speed SPI / USB 3.0 interface on the edge compute benchtop rig.
2. Transmit calibrated 16-bit IQ synthetic radar waveform data sequences continuously at nominal bus clock rate for 15 minutes.
3. Execute the dedicated DSP memory management thread with prioritized FIFO ring buffers.
4. Verify that all transmitted packets are written to host ring memory and check for buffer overrun interrupt flags.

**Required Inputs / Environment:**  
Micro-GPR antenna interface emulator, synthetic 16-bit IQ waveform generator, DSP host evaluation board.

**Expected Result:**  
16-bit IQ complex samples stream continuously across bus into DSP buffers without buffer overrun flags.

**Pass/Fail Criteria:**  
PASS if 100% of transmitted IQ radar packets are buffered without memory stalls or packet loss; FAIL if buffer overrun or checksum error occurs.

**Verification Evidence:**  
DSP FIFO ring buffer utilization logs, serial communication packet audit trace, and raw binary IQ sample capture dump.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Radar center frequency, RF emission limits, signal bandwidth, and soil/ice penetration depth thresholds remain undefined in overview; to be quantified in sensor ICD.

---

#### REQ-F-003 — 4-Channel Acoustic Array Ingress & TDoA Bearing Estimation

**Original Requirement:**
The system shall ingest acoustic air pressure signals from a synchronized 4-channel microphone array and execute Time-Difference-of-Arrival (TDoA) algorithms to calculate directional bearing estimates to acoustic impulse noises.

**Acceptance Criteria:**
* AC-3.1: The acoustic ingress subsystem shall capture synchronized 4-channel audio signals from a tetrahedral or planar microphone array simultaneously.
* AC-3.2: The onboard TDoA DSP algorithm shall detect acoustic impulse noises (simulated gunfire or rotor sound impulses) above ambient baseline noise.
* AC-3.3: The system shall output horizontal bearing angles (azimuth) to the acoustic impulse source within an angular accuracy tolerance of +/- 10 degrees (+/- 10 deg) in calm air conditions.
* AC-3.4: [TBD — Requires Engineering Clarification] Acoustic sampling frequency (kHz) and wind shear acoustic noise suppression thresholds require formal specification.

**Verification Method:**  
Demonstration

**Verification Procedure:**
1. Mount the calibrated 4-channel microphone array on the acoustic test bench in an anechoic or semi-anechoic acoustic chamber.
2. Emit calibrated acoustic impulse pulses at known azimuth angles (0, 45, 90, 180, 270 degrees) at a fixed distance (10 meters).
3. Execute the onboard TDoA DSP cross-correlation algorithm on the edge processing core.
4. Compare calculated directional bearing angles output by the TDoA algorithm against true geometric source angles.

**Required Inputs / Environment:**  
4-channel synchronized microphone array, calibrated acoustic impulse sound generator, angle-indexed acoustic test fixture.

**Expected Result:**  
The algorithm detects impulses across all 4 channels and outputs bearing azimuth angles within +/- 10 degrees of actual source locations.

**Pass/Fail Criteria:**  
PASS if calculated impulse bearings match known source angles within +/- 10 degrees across all test angles; FAIL if angular error exceeds 10 degrees or impulses are missed.

**Verification Evidence:**  
Time-Difference-of-Arrival cross-correlation logs, acoustic bearing output telemetry, and acoustic chamber test certificates.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Acoustic sampling rate, wind noise cancellation algorithm profile, and minimum impulse detection sensitivity threshold require definition.

---

#### REQ-F-004 — GNSS-Denied Multi-Sensor VIO State Estimation

**Original Requirement:**
The system shall maintain real-time 6-DOF vehicle pose and velocity estimation in GNSS-denied environments by fusing visual feature streams from tracking lenses, tactical-grade IMU angular rates, LiDAR range data, and onboard Digital Elevation Models (DEM) via extended Kalman filtering.

**Acceptance Criteria:**
* AC-4.1: The state estimation pipeline shall fuse optical feature tracking points, 200 Hz IMU linear acceleration/angular rates, and LiDAR range data within an extended Kalman filter (EKF) without receiving GNSS satellite ephemeris.
* AC-4.2: The state estimation pipeline shall cross-reference calculated altitude and terrain relief against an onboard digital elevation model (DEM).
* AC-4.3: The estimated 6-DOF vehicle pose and velocity vectors shall publish to the PX4 autopilot over ROS 2 topics at a continuous update rate of >= 30 Hz.
* AC-4.4: Sustained positional drift during GNSS-denied operation shall comply with REQ-P-005 (< 1.0 m drift bound).

**Verification Method:**  
Test

**Verification Procedure:**
1. Initialize the Gazebo high-fidelity mountain digital twin world simulating Siachen/Ladakh terrain profiles with simulated optical cameras, 200 Hz IMU, and LiDAR rangefinder.
2. Disable all simulated GPS/GNSS sensor topics in the simulation environment to induce complete GNSS denial.
3. Command a pre-programmed 5-kilometer closed-loop tactical flight pattern at varying simulated altitudes (50 m to 300 m AGL).
4. Log ground-truth vehicle pose from Gazebo physics engine and compare against VIO+DEM state estimation topic output at 30 Hz.
5. Calculate cumulative 3D Euclidean error over the trajectory duration.

**Required Inputs / Environment:**  
Gazebo SITL digital twin mountain world, preloaded 5-meter DEM grid database, simulated high-rate IMU and tracking camera streams.

**Expected Result:**  
Continuous 6-DOF pose publishing at >= 30 Hz with bounded positional drift adhering to sub-meter limits throughout GNSS-denied profile.

**Pass/Fail Criteria:**  
PASS if state estimation maintains continuous output at >= 30 Hz without divergence or filter reset throughout the trajectory; FAIL if state estimation drops below 30 Hz or diverges.

**Verification Evidence:**  
VIO state estimation ROS 2 topic telemetry bagfiles, Gazebo ground-truth pose log files, and 3D positional drift deviation error plots.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
DEM database spatial resolution (1m vs 5m) and maximum recovery time following temporary visual feature occlusion need formal specification.

---

#### REQ-F-005 — Dual-Redundant Autopilot Attitude Control & Waypoint Navigation

**Original Requirement:**
The system shall execute real-time attitude PID control loops, autonomous waypoint navigation, and trajectory execution using Swadeshi ROS 2 middleware integrated with custom PX4 autopilot flight firmware running on dedicated 32-bit automotive/aerospace microcontrollers.

**Acceptance Criteria:**
* AC-5.1: The flight firmware shall execute inner-loop attitude PID control loops on dedicated 32-bit automotive/aerospace microcontrollers (STM32 series).
* AC-5.2: Swadeshi ROS 2 mission coordination nodes shall communicate waypoint target coordinates to the PX4 autopilot flight stack via micro-XRCE-DDS agents over high-speed buses.
* AC-5.3: The system shall successfully execute autonomous waypoint transitions, altitude hold, and commanded heading transitions without human pilot stick inputs.
* AC-5.4: In the event of primary communication link severance, the autopilot shall autonomously execute a deterministic Return-to-Home (RTH) failsafe sequence.

**Verification Method:**  
Demonstration

**Verification Procedure:**
1. Deploy the Swadeshi ROS 2 middleware stack coupled to PX4 Autopilot SITL simulation integrated with Gazebo flight physics.
2. Upload a mission plan consisting of 10 sequential 3D waypoints including climbing turns and altitude changes.
3. Command autonomous mission engagement and record flight mode status, commanded vs actual attitude, and waypoint crossing flags.
4. Inject a synthetic ROS 2 node disconnect during transit to waypoint 5 to evaluate automatic transition to autonomous return-to-home mode.

**Required Inputs / Environment:**  
PX4 SITL firmware instance, Swadeshi ROS 2 micro-XRCE communication bridge, Gazebo aircraft dynamic model.

**Expected Result:**  
Autonomous sequencing across all waypoints with deterministic trajectory adherence; seamless auto-transition to RTH upon command link interruption.

**Pass/Fail Criteria:**  
PASS if all 10 waypoints are traversed within a 2-meter acceptance radius and RTH triggers deterministically upon simulated link loss; FAIL if uncommanded attitude divergence or mode lockup occurs.

**Verification Evidence:**  
MAVLink flight control log files (.ulg format), ROS 2 action server logs, and Gazebo trajectory tracking telemetry.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Bank angle limits, climb/descent rate bounds, and auto-return triggers require definition in SSRD. P02 cited VanguardFlight OS; REA-T1 mandates Swadeshi ROS 2 + custom PX4.

---

#### REQ-F-006 — Onboard Real-Time Neural Object Detection & Bounding Box Generation

**Original Requirement:**
The system shall execute optimized neural network models directly onboard the heterogeneous edge compute matrix to detect tactical targets and generate bounding boxes from synchronized video streams without ground-cloud reliance.

**Acceptance Criteria:**
* AC-6.1: The edge compute engine shall execute deep learning object detection models directly onboard using heterogeneous GPU/NPU cores with 0% cloud connectivity.
* AC-6.2: The detection engine shall ingest synchronized video frames and output 2D bounding box coordinates, class labels, and detection confidence scores.
* AC-6.3: [TBD — Requires Engineering Clarification] Minimum target detection mean Average Precision (mAP@0.50) and formalized target class taxonomy (military vehicles, personnel, fortifications) require formal definition.

**Verification Method:**  
Demonstration

**Verification Procedure:**
1. Flash the edge compute substrate with the baseline quantized neural object detection model (exported via ONNX and compiled for edge inference).
2. Play back a standardized test video dataset representing tactical mountain terrain featuring camouflaged vehicles and personnel.
3. Measure frame processing time and log output bounding box coordinates and classification metadata.
4. Calculate average inference latency and detection accuracy against annotated ground-truth labels.

**Required Inputs / Environment:**  
Annotated tactical video test dataset (1,000 frames), edge compute evaluation carrier board, quantized neural network model binary.

**Expected Result:**  
Zero-cloud real-time object detection generates bounding boxes and class IDs for tactical targets present in test video stream.

**Pass/Fail Criteria:**  
PASS if target objects are localized with bounding boxes and classes without network connectivity; FAIL if software crashes or requires external server offloading.

**Verification Evidence:**  
Inference output JSON metadata streams, annotated bounding box video recordings, and edge compute CPU/GPU loading telemetry.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Target class taxonomy (vehicles, personnel, fortifications) and minimum acceptable mean Average Precision (mAP) not stated. P02 cited YOLOv8 on Jetson Orin; REA-T1 specifies edge neural models.

---

#### REQ-F-007 — Vision Transformer Pixel-Level Semantic Terrain Segmentation

**Original Requirement:**
The system shall execute vision transformer and convolutional neural architectures on onboard edge acceleration hardware to generate real-time pixel-level semantic segmentation masks of ground terrain, obstacles, and camouflaged assets.

**Acceptance Criteria:**
* AC-7.1: The edge compute engine shall execute semantic segmentation neural networks onboard to classify each image pixel into distinct terrain and obstacle categories.
* AC-7.2: Generated pixel-level segmentation mask tensors shall be output to shared memory for consumption by obstacle avoidance and landing zone evaluation routines.
* AC-7.3: [TBD — Requires Engineering Clarification] Target mean Intersection-over-Union (mIoU) percentage and specific semantic class taxonomy (e.g., rock, snow, water, vegetation, structure) require formal baseline specification.

**Verification Method:**  
Demonstration

**Verification Procedure:**
1. Load the compiled semantic segmentation model onto the onboard heterogeneous compute matrix.
2. Feed a sequence of calibrated multi-spectral test frames containing varied Himalayan terrain features (crevasses, snowfields, boulders, ridgelines).
3. Capture the generated segmentation mask tensors from shared memory.
4. Overlay mask tensors onto original input frames to visually verify pixel alignment with physical terrain boundaries.

**Required Inputs / Environment:**  
Pre-recorded multi-spectral terrain dataset with pixel-level ground truth annotations, edge AI compute board.

**Expected Result:**  
Segmentation masks correctly delineate terrain boundaries, obstacles, and ground features without pipeline stalls.

**Pass/Fail Criteria:**  
PASS if pixel masks generate deterministically for each input frame and align with physical terrain structures; FAIL if segmentation pipeline drops frames or halts.

**Verification Evidence:**  
Color-coded semantic segmentation mask output images, shared memory transfer latency logs, and GPU utilization metrics.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Required semantic terrain classes, input resolution, and minimum acceptable mean Intersection-over-Union (mIoU) require formal baseline definition.

---

#### REQ-F-008 — Temporal Visual Change Detection & Ground Disturbance Flagging

**Original Requirement:**
The system shall perform comparative neural inference between live video streams and onboard historical terrain embeddings to automatically detect and flag ground modifications, fortifications, or vehicle tracks.

**Acceptance Criteria:**
* AC-8.1: The edge AI engine shall store historical terrain feature embeddings in local encrypted non-volatile memory.
* AC-8.2: The comparative change detection algorithm shall register incoming live video frames against corresponding geo-referenced historical embeddings.
* AC-8.3: The system shall generate a tactical change alert vector containing GPS/grid coordinates and bounding areas whenever significant visual disturbances (new fortifications, tire tracks, freshly dug earth) are detected.
* AC-8.4: [TBD — Requires Engineering Clarification] Minimum detectable physical disturbance dimensions (meters) and geo-referencing alignment tolerance require quantification.

**Verification Method:**  
Demonstration

**Verification Procedure:**
1. Preload the edge compute storage with baseline historical image embeddings of a designated tactical test area.
2. Ingest live simulated video of the same area modified with synthetic trenches, new tire tracks, and simulated military earthworks.
3. Execute the onboard Siamese / temporal comparison neural network.
4. Monitor the change detection output topic for alert coordinates and change mask polygons.

**Required Inputs / Environment:**  
Paired historical baseline and altered tactical test imagery sets, edge AI inference board.

**Expected Result:**  
System detects visual discrepancies between historical and current imagery, outputting geo-referenced change bounding coordinates.

**Pass/Fail Criteria:**  
PASS if altered ground regions are flagged with alert coordinates and false alarm rate remains below baseline threshold; FAIL if modified areas are missed.

**Verification Evidence:**  
Temporal difference heatmaps, change detection alert event log files, and visual comparison confirmation dossiers.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Historical embedding format, onboard geo-referencing tolerances, and minimum detectable ground disturbance dimensions need definition.

---

#### REQ-F-009 — Software-Defined Radio Wideband Spectrum Ingress & RF Mapping

**Original Requirement:**
The system shall ingest wideband radio frequency spectrum signals using Software-Defined Radio (SDR) to generate RF spectrum occupancy grids, characterize hostile radar signatures, and detect electronic emissions.

**Acceptance Criteria:**
* AC-9.1: The SDR ingress hardware shall capture wideband RF signals across the operational spectrum band (400 MHz to 6 GHz per REQ-P-010).
* AC-9.2: The DSP firmware shall perform real-time Fast Fourier Transform (FFT) processing to construct dynamic RF spectrum occupancy grids.
* AC-9.3: The system shall extract signal parameters (center frequency, bandwidth, pulse repetition interval) to characterize active emitter signatures.
* AC-9.4: Generated RF occupancy matrices shall publish to ROS 2 mission awareness topics without exceeding allocated inter-process memory limits.

**Verification Method:**  
Demonstration

**Verification Procedure:**
1. Connect the SDR receiver input to a calibrated RF signal generator inside an RF-shielded bench enclosure.
2. Inject synthetic RF pulses simulating tactical communications (UHF 433 MHz), tactical datalinks (2.4 GHz), and airborne surveillance radar (5.8 GHz).
3. Execute the onboard wideband spectrum scanning and DSP channelization algorithm.
4. Verify that detected RF energy peaks match injected frequencies and power levels in the output spectrum grid.

**Required Inputs / Environment:**  
Calibrated RF vector signal generator, RF-shielded bench enclosure, SDR transceiver hardware.

**Expected Result:**  
SDR captures RF signals across 400 MHz–6 GHz, extracts emitter center frequencies, and generates real-time spectrum occupancy grids.

**Pass/Fail Criteria:**  
PASS if injected RF frequencies are detected within +/- 50 kHz accuracy and spectrum occupancy grids update continuously; FAIL if signals are undetected or bus freezes.

**Verification Evidence:**  
FFT spectrum occupancy waterfall plots, detected emitter parameter logs, and VITA 49 radio transport packet capture traces.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Discrepancy flagged: REA-T1 Module 04 specifies 400 MHz to 6 GHz RF antenna inputs; P02 draft cited 10 MHz to 6 GHz. Antenna bandwidth and FFT bin resolution require clarification.

---

#### REQ-F-010 — Free-Space Optical (FSO) Directional Laser Telemetry Transmission

**Original Requirement:**
The system shall modulate and transmit tactical mission intelligence, target coordinates, and compressed mission video to friendly optical ground terminals over a directional Free-Space Optical (FSO) laser communications link.

**Acceptance Criteria:**
* AC-10.1: The FSO laser transmitter shall modulate and transmit serialized mission telemetry, target coordinates, and compressed video data over an optical laser beam.
* AC-10.2: The optical transmission shall operate in line-of-sight orientation toward a designated optical receiver terminal.
* AC-10.3: The laser transmitter shall generate zero detectable radio frequency emissions across the 10 MHz to 40 GHz electromagnetic spectrum.
* AC-10.4: Achieved data throughput and operating range shall satisfy REQ-P-006 (target >= 1.2 Gbps up to 18 km).

**Verification Method:**  
Demonstration

**Verification Procedure:**
1. Set up an optical line-of-sight test range linking the airborne FSO transmitter head to a calibrated optical ground terminal receiver.
2. Stream high-definition mission video and synthetic target telemetry packets through the FSO serializer.
3. Monitor received data bitstream on the ground terminal demodulator.
4. Verify data integrity via cyclic redundancy check (CRC) audit and measure RF spectrum emissions using a wideband spectrum analyzer to confirm RF silence.

**Required Inputs / Environment:**  
Airborne FSO laser transceiver prototype, optical ground receiver terminal, wideband spectrum analyzer for RF radiation verification.

**Expected Result:**  
Video and telemetry stream across optical laser link without packet corruption; zero RF emissions detected on spectrum analyzer.

**Pass/Fail Criteria:**  
PASS if optical link delivers valid demodulated video and data without RF leakage; FAIL if optical link fails to establish or radiates RF energy.

**Verification Evidence:**  
Optical power meter logs, bit error rate (BER) test readouts, received video playback recordings, and RF spectrum analyzer silence plots.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Laser optical wavelength (1550nm band in P02) and eye-safety classification standards require alignment with ground station transceiver ICD.

---

#### REQ-F-011 — Closed-Loop Coarse-Fine FSO Laser Pointing, Acquisition & Tracking

**Original Requirement:**
The system shall maintain closed-loop coarse-fine laser pointing, acquisition, and tracking (PAT) using fast steering mechanisms driven by high-rate gyro coordinate offsets over serial interfaces to compensate for airframe vibration and wind shear.

**Acceptance Criteria:**
* AC-11.1: The FSO gimbal and fast steering mirror mechanism shall receive 200 Hz gyro attitude coordinate offsets over the designated serial bus (RS-422).
* AC-11.2: The PAT control loop shall execute closed-loop beam stabilization compensating for induced angular platform vibrations and simulated wind shear.
* AC-11.3: Under angular disturbance vibrations of up to +/- 5 degrees, the optical beam centerline shall maintain tracking lock on the ground terminal receiver.
* AC-11.4: [TBD — Requires Engineering Clarification] Maximum allowable pointing jitter in microradians (µrad) and link re-acquisition time budget (ms) following optical break require specification.

**Verification Method:**  
Test

**Verification Procedure:**
1. Mount the FSO transceiver head on a 3-axis motion flight simulation table inside an optical testing laboratory.
2. Program the motion table to reproduce high-altitude angular turbulence and vibrations (up to 25 m/s wind shear dynamics).
3. Align the laser beam with a distant optical position-sensing detector (PSD).
4. Measure beam center displacement and pointing jitter on the PSD while the motion table executes angular oscillation profiles.

**Required Inputs / Environment:**  
3-axis multi-axis flight motion vibration table, high-speed position-sensing detector (PSD), FSO gimbal with fast steering mirror.

**Expected Result:**  
Coarse-fine PAT loops maintain continuous optical alignment on receiver during active angular perturbation.

**Pass/Fail Criteria:**  
PASS if beam maintains lock on receiver target without beam divergence during vibration test profile; FAIL if optical lock is lost.

**Verification Evidence:**  
PSD beam displacement tracking logs, RS-422 gyro offset command traces, and motion table dynamic profile logs.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Beam divergence angle, pointing jitter limit (microradians), and link re-acquisition latency budget need definition.

---

#### REQ-F-012 — Encrypted Frequency-Hopping SDR RF Telemetry Fallback

**Original Requirement:**
The system shall establish and maintain secondary frequency-hopping, cryptographically encrypted SDR RF communications for command, control, and telemetry fallback when optical laser links are obscured or unavailable.

**Acceptance Criteria:**
* AC-12.1: The communication subsystem shall continuously monitor FSO optical link carrier lock and signal-to-noise ratio.
* AC-12.2: Upon detection of complete optical beam obscuration (e.g., dense cloud/smoke obstruction), the communication controller shall automatically activate the secondary encrypted SDR RF link within <= 500 milliseconds.
* AC-12.3: All fallback command, control, and telemetry data transmitted over the SDR RF link shall be encrypted using hardware-accelerated authenticated cryptography (AES-256-GCM or approved sovereign algorithm).
* AC-12.4: The SDR link shall execute pseudo-random frequency hopping across authorized military frequency channels.

**Verification Method:**  
Demonstration

**Verification Procedure:**
1. Configure the communications bench with both active FSO optical link and standby encrypted SDR RF transceiver connected to a test GCS.
2. Initiate continuous telemetry and flight command transmission over the primary optical laser link.
3. Physically obstruct the optical beam path using an opaque shutter to simulate dense cloud cover.
4. Measure the latency between optical lock loss and automatic activation of the SDR RF link; verify that telemetry flow resumes over RF.
5. Capture transmitted RF packets with a spectrum analyzer and packet sniffer to verify frequency hopping and payload ciphertext encryption.

**Required Inputs / Environment:**  
Integrated dual FSO/RF communications testbench, optical beam physical shutter, RF packet analyzer, GCS transceiver.

**Expected Result:**  
Automatic failover from optical to encrypted SDR RF link occurs in <= 500 ms with uninterrupted vehicle command control.

**Pass/Fail Criteria:**  
PASS if RF fallback activates automatically in <= 500 ms with valid encrypted telemetry; FAIL if fallback exceeds 500 ms or command loss occurs.

**Verification Evidence:**  
Automatic link switchover timestamp logs, RF spectrum frequency-hopping waterfall traces, and encrypted packet capture files.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Optical-to-RF automatic switchover latency, frequency hopping rate, and encryption suite (e.g., AES-256-GCM) require specification.

---

#### REQ-F-013 — Wind-Compensated Ballistic Release & Payload Delivery Actuation

**Original Requirement:**
The system shall compute real-time ballistic release timing based on target coordinates, radar altitude, and real-time wind speed/direction estimations, and actuate mechanical unlatching of the precision cargo drop pod.

**Acceptance Criteria:**
* AC-13.1: The flight computer shall execute a ballistic trajectory drop algorithm incorporating real-time pitot airspeed, estimated wind vector, ground speed, and radar altitude AGL.
* AC-13.2: The system shall calculate the precise release point advance offset required to deliver the cargo pod to designated target ground coordinates.
* AC-13.3: Upon reaching the computed release window, the system shall command mechanical unlatching of the cargo pod via the dual-redundant opto-isolated safety interlock (REQ-S-004).
* AC-13.4: [TBD — Requires Engineering Clarification] Maximum payload mass capacity (kg), internal volume dimensions, and delivery Circular Error Probable (CEP) accuracy radius (meters) require formal specification.

**Verification Method:**  
Demonstration

**Verification Procedure:**
1. In the Gazebo SITL simulation environment, define a designated ground target coordinate and inject variable horizontal wind vectors (10 m/s to 20 m/s).
2. Fly the simulated aircraft toward the target drop zone at 150 m altitude AGL.
3. Monitor ballistic calculation outputs as the aircraft approaches the computed release advance point.
4. Confirm that the cargo release discrete trigger signal fires at the exact computed release point.
5. Track simulated cargo pod free-fall trajectory to measure ground impact distance relative to target coordinates.

**Required Inputs / Environment:**  
Gazebo simulation environment with wind physics engine, simulated cargo pod mass model, target coordinate coordinates.

**Expected Result:**  
Ballistic release point is dynamically computed compensating for wind shear; payload unlatch discrete triggers deterministically.

**Pass/Fail Criteria:**  
PASS if cargo release discrete signal fires at the computed ballistic point and simulated ground impact falls within target radius; FAIL if trigger misfires or misses target.

**Verification Evidence:**  
Ballistic calculator input/output log files, servo unlatch actuation electrical timestamp traces, and trajectory impact coordinates.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Cargo pod payload mass capacity (kg), volumetric envelope, and delivery Circular Error Probable (CEP) threshold are pending definition.

---

#### REQ-SEC-001 — Cryptographic Hardware Root of Trust & Multi-Stage Secure Boot

**Original Requirement:**
The system shall cryptographically authenticate all bootloader binaries, operating system kernels, and robotic middleware nodes from hardware power-on using a dedicated Hardware Root of Trust and cryptographically signed boot keys.

**Acceptance Criteria:**
* AC-SEC-1.1: The primary compute hardware shall incorporate a dedicated Hardware Root of Trust (TPM 2.0 or secure cryptoprocessor enclave) containing write-protected, fuse-locked public key certificates.
* AC-SEC-1.2: Stage 1 bootloader (ROM code) shall verify the cryptographic signature of the Stage 2 bootloader binary before handing over CPU execution.
* AC-SEC-1.3: Stage 2 bootloader shall authenticate the Linux kernel image, real-time device tree, and root filesystem hash using asymmetric public key cryptography (RSA-4096 or ECDSA P-384).
* AC-SEC-1.4: If any boot binary, kernel module, or ROS 2 node exhibits an invalid or missing signature, the bootloader shall halt execution immediately, enter a secure lock state, and log a cryptographic fault.

**Verification Method:**  
Test

**Verification Procedure:**
1. Flash the edge compute board with properly signed official firmware and kernel binaries; cycle power and verify that the system boots to operational multi-user target.
2. Inject a 1-byte corrupted modification into the signed Linux kernel binary file stored on flash.
3. Power cycle the board and capture serial UART bootloader debug console output.
4. Verify that the Stage 2 bootloader detects signature verification failure, halts boot execution, and prevents unauthorized OS kernel execution.

**Required Inputs / Environment:**  
Edge compute carrier board with Hardware Root of Trust silicon, official signed firmware images, corrupted test binary images.

**Expected Result:**  
Validly signed binaries boot normally; any corrupted or unsigned binary halts execution instantly at bootloader stage.

**Pass/Fail Criteria:**  
PASS if system boots with valid signatures and strictly aborts boot upon encountering modified binaries; FAIL if unsigned or modified code executes.

**Verification Evidence:**  
Serial UART secure boot console logs, cryptographic signature verification hash audit records, and TPM hardware status register dumps.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Specific hardware enclave silicon part and PKI hierarchy pending definition.

---

#### REQ-SEC-002 — Hardware-Enforced Zero-Trace Memory Sanitization & Anti-Tamper Wipe

**Original Requirement:**
The system shall trigger irreversible hardware-enforced cryptographic flash memory erasure and instant zero-trace RAM purging upon detection of physical enclosure breach, anti-tamper sensor activation, or airframe capture.

**Acceptance Criteria:**
* AC-SEC-2.1: The system enclosure shall incorporate active physical anti-tamper switches and mesh intrusion sensors.
* AC-SEC-2.2: Upon detection of enclosure breach, unauthorized chassis opening, or commanded emergency zeroization, dedicated hardware logic shall disconnect volatile cryptographic key memory within <= 10 milliseconds.
* AC-SEC-2.3: The system shall trigger instant cryptographic key erasure (destroying master decryption keys) and initiate irreversible NAND/eMMC flash memory sanitization / block erase.
* AC-SEC-2.4: Following sanitization, no unencrypted flight logs, neural model weights, mission waypoints, or cryptographic certificates shall remain recoverable via forensic analysis.

**Verification Method:**  
Test

**Verification Procedure:**
1. Connect the benchtop anti-tamper trigger circuit to the dedicated security hardware enclave on an engineering test unit loaded with test mission data.
2. Trigger the anti-tamper discrete input to simulate enclosure breach.
3. Measure the electrical key-wipe latency on an oscilloscope connected to the secure memory power disconnect rail.
4. Attempt to boot the board and extract storage contents using JTAG/forensic memory reader tools.
5. Verify that flash partitions are unreadable, master keys are zeroed, and confidential data cannot be reconstructed.

**Required Inputs / Environment:**  
Security engineering test board, oscilloscope monitoring key rail power, anti-tamper test switch fixture, external JTAG forensic programmer.

**Expected Result:**  
Hardware zeroizes cryptographic keys in <= 10 ms; non-volatile flash data becomes completely unrecoverable.

**Pass/Fail Criteria:**  
PASS if keys are wiped in <= 10 ms and forensic memory readout yields zero plain-text data or valid partitions; FAIL if key persists or flash is readable.

**Verification Evidence:**  
Oscilloscope voltage drop timing screenshots, post-wipe forensic memory dump hex files, and anti-tamper event audit records.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Flash sanitization execution time budget (ms) and tamper threshold voltages require formalization.

---

#### REQ-P-001 — Flight Control Inner-Loop Deterministic Execution Latency

**Original Requirement:**
The flight control attitude loops and stabilization algorithms running on dedicated real-time microcontrollers shall achieve deterministic inner-loop execution latency of under 1 millisecond (< 1 ms).

**Acceptance Criteria:**
* AC-P-1.1: The inner-loop attitude PID calculation (angular rate estimation to PWM motor/servo output command generation) shall execute within a latency bound of < 1.0 millisecond (< 1 ms) per cycle.
* AC-P-1.2: The inner-loop execution cycle frequency shall remain stable at >= 400 Hz (nominal 1 kHz where supported by MCU timers).
* AC-P-1.3: Maximum jitter across 100,000 consecutive execution loops under 90% CPU load shall not exceed +/- 50 microseconds (+/- 50 µs).
* AC-P-1.4: [Design Stretch Goal] The architecture shall support profiling toward < 250 µs inner-loop execution latency on 480 MHz bare-metal Cortex-M7 hardware.

**Verification Method:**  
Test

**Verification Procedure:**
1. Flash the bare-metal STM32 microcontroller with the baseline PX4 flight firmware containing GPIO toggle instrumentation around the inner attitude control loop.
2. Connect a calibrated 100 MHz digital oscilloscope or logic analyzer to the dedicated loop execution GPIO pin.
3. Run the flight controller on the Tier 3 HIL benchtop test rig while streaming synthetic sensor inputs at maximum bus rate for 60 continuous minutes.
4. Capture 100,000 consecutive loop execution duration measurements.
5. Compute maximum, minimum, average latency, and execution jitter.

**Required Inputs / Environment:**  
Bare-metal flight controller hardware (STM32 series), HIL sensor simulator, calibrated digital oscilloscope / logic analyzer.

**Expected Result:**  
Measured inner-loop execution latency is strictly < 1.0 ms across all captured cycles; maximum jitter is <= +/- 50 µs.

**Pass/Fail Criteria:**  
PASS if 100% of measured execution cycles complete in < 1.0 ms and jitter <= +/- 50 µs; FAIL if any cycle exceeds 1.0 ms.

**Verification Evidence:**  
Oscilloscope timing histogram screenshots, logic analyzer pulse duration export files (.csv), and HIL real-time latency report.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Discrepancy flagged: P02 draft cited <250 us; official REA-T1 Section 10 Tier 3 establishes inner-loop latency under 1 millisecond. Maximum jitter bounds require definition.

---

#### REQ-P-002 — High-Altitude Operational Service Ceiling

**Original Requirement:**
The airframe, aerodynamics, and propulsion subsystems shall sustain operational tactical flight at a service ceiling of up to 6,500 meters Above Mean Sea Level (AMSL) in low air-density mountain environments.

**Acceptance Criteria:**
* AC-P-2.1: The propulsion motor, propeller geometry, and aerodynamics shall generate sufficient aerodynamic lift and thrust to sustain steady-state level flight at 6,500 m AMSL in air density corresponding to standard Himalayan atmosphere (~0.65 kg/m³).
* AC-P-2.2: At 6,500 m AMSL, the propulsion system shall maintain a minimum residual climb rate margin of at least >= 1.0 meter per second (>= 1.0 m/s).
* AC-P-2.3: Motor winding and ESC electrical temperatures at 6,500 m AMSL cruise thrust shall remain within manufacturer continuous thermal ratings.

**Verification Method:**  
Test

**Verification Procedure:**
1. Mount the propulsion motor and flight propeller on an instrumented thrust stand inside a variable-pressure hypobaric environmental test chamber.
2. Evacuate chamber pressure down to ~440 hPa (equivalent to 6,500 m AMSL pressure altitude) at -15°C.
3. Execute motor throttle ramps from idle to maximum thrust while recording thrust (N), RPM, electrical voltage, current, and motor temperature.
4. Verify that generated thrust exceeds the simulated aircraft level flight weight and provides > 1.0 m/s climb excess thrust.

**Required Inputs / Environment:**  
Propulsion motor/propeller assembly, hypobaric pressure test chamber, calibrated multi-axis thrust/torque load cell, high-rate electrical power analyzer.

**Expected Result:**  
Propulsion generates required sustained thrust at 440 hPa low air density; motor/ESC temperatures remain within safe operational bounds.

**Pass/Fail Criteria:**  
PASS if measured thrust at 6,500 m equivalent pressure equals or exceeds level flight drag requirement plus 1.0 m/s climb thrust; FAIL if thrust is insufficient or motor overheats.

**Verification Evidence:**  
Hypobaric chamber test data logs, thrust vs RPM vs power curves at 440 hPa, and chamber calibration certificates.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Climb rate at 6,500m AMSL, take-off density altitude limits, and motor thrust degradation profiles require documentation in aerodynamic baseline.

---

#### REQ-P-003 — Flight Stabilization Mountain Wind Shear Resistance

**Original Requirement:**
The flight stabilization system, control surfaces, and airframe structure shall sustain stable controlled flight under localized mountain wind shear and gusts of up to 25 meters per second (25 m/s).

**Acceptance Criteria:**
* AC-P-3.1: The flight stabilization control algorithms shall reject abrupt localized wind shear gusts of up to 25.0 m/s without suffering loss of control.
* AC-P-3.2: During a 25 m/s gust disturbance, maximum airframe angular excursion shall not exceed +/- 20 degrees in pitch and +/- 30 degrees in roll.
* AC-P-3.3: The flight controller shall restore nominal aircraft attitude and heading within <= 2.5 seconds following gust cessation.
* AC-P-3.4: The carbon-composite airframe structure shall sustain aerodynamic gust loading without structural cracking or permanent aeroelastic deformation.

**Verification Method:**  
Test

**Verification Procedure:**
1. Configure the Gazebo / PX4 SITL simulation model with aerodynamic flight coefficients of the carbon-composite airframe.
2. Inject standardized discrete '1-cosine' gust profiles and Dryden localized wind turbulence with peak wind velocities up to 25 m/s.
3. Command level waypoint flight through the simulated shear boundary.
4. Measure angular attitude excursions (pitch/roll/yaw rates) and time required to return within +/- 2 degrees of trim attitude.

**Required Inputs / Environment:**  
Gazebo simulation environment with active Dryden/von Kármán turbulence injection models, PX4 SITL autopilot stack.

**Expected Result:**  
Vehicle attitude excursions remain within +/- 20 deg pitch and +/- 30 deg roll; nominal trim recovered within <= 2.5 s with zero stall.

**Pass/Fail Criteria:**  
PASS if vehicle recovers trim within 2.5 s without structural load exceedance or spin; FAIL if vehicle enters unrecoverable stall or attitude divergence.

**Verification Evidence:**  
Gazebo flight dynamic telemetry logs, commanded vs actual attitude time-series plots, and aerodynamic stability audit reports.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Maximum sustained gust duration at 25 m/s and angular attitude deviation tolerances require quantification in Gazebo digital twin test profiles.

---

#### REQ-P-004 — Sub-Zero Cold-Weather Operating Thermal Envelope

**Original Requirement:**
The system electronics, avionics, propulsion motors, and insulated battery management cells shall maintain nominal operational performance in ambient temperatures down to -20°C (with threshold evaluation down to -30°C).

**Acceptance Criteria:**
* AC-P-4.1: All avionics computing boards, microcontrollers, and sensor interfaces shall execute without timing faults, memory errors, or system resets at an ambient chamber temperature of -20°C.
* AC-P-4.2: The battery thermal management system shall maintain internal lithium cell core temperatures at >= +5°C via insulated enclosures and self-heating elements when soaked at -20°C ambient.
* AC-P-4.3: Propulsion motors and bearing assemblies shall achieve nominal rotation and startup torque without mechanical binding or freezing down to -20°C.
* AC-P-4.4: System shall undergo exploratory threshold qualification to assess cold survival down to -30°C.

**Verification Method:**  
Test

**Verification Procedure:**
1. Place the integrated avionics stack, edge compute board, sensors, and battery enclosure inside an environmental thermal test chamber (Tier 5).
2. Lower chamber temperature to -20°C at a rate of 1°C per minute; soak the system at -20°C for at least 4 hours.
3. Power on the system at -20°C; execute continuous built-in self-tests (BIST), bus communications, and simulated sensor streaming for 2 hours.
4. Record battery internal core temperatures, heater current draw, CPU clock frequencies, and communication error counters.
5. Ramp down to -30°C for exploratory threshold survival audit.

**Required Inputs / Environment:**  
Environmental temperature chamber capable of -40°C to +60°C, thermocouple thermal data logger, integrated avionics & battery prototype.

**Expected Result:**  
Electronics boot and operate nominally at -20°C; battery heaters maintain internal cell core at >= +5°C with zero communication dropouts.

**Pass/Fail Criteria:**  
PASS if 100% of avionics operate without reset or bus failure for 2 hours at -20°C and battery core stays >= +5°C; FAIL if any system resets, freezes, or fails to boot.

**Verification Evidence:**  
Environmental thermal chamber temperature/humidity logs, thermocouple time-history recordings, and system health audit files.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Discrepancy flagged: REA-T1 Section 9/10 specifies thermal chamber stress testing down to -20°C; P02 draft cited -30°C. Temperature envelope needs formal baseline clarification.

---

#### REQ-P-005 — GNSS-Denied Positional Drift Bound

**Original Requirement:**
The VIO and DEM terrain-matching navigation pipeline shall sustain continuous drift-bounded tactical flight in satellite-jammed airspace with sub-meter drift bounds (< 0.8m to 1.0m per hour positional error).

**Acceptance Criteria:**
* AC-P-5.1: During continuous autonomous flight in GNSS-denied conditions, the cumulative 2D horizontal positional drift shall not exceed 1.0 meter (< 1.0 m) per flight hour.
* AC-P-5.2: At least 95% of estimated position samples (95% Circular Error Probable - CEP) shall reside within the sub-meter error boundary relative to true spatial trajectory.
* AC-P-5.3: Vertical altitude error relative to the terrain DEM profile shall remain within +/- 1.5 meters throughout the 1-hour trajectory.

**Verification Method:**  
Test

**Verification Procedure:**
1. Execute a simulated 60-minute autonomous tactical reconnaissance mission in the Gazebo mountain digital twin with GPS topics disabled (Tier 8).
2. Record estimated vehicle position vectors from the VIO + DEM Kalman filter topic at 10 Hz.
3. Record true vehicle spatial coordinates from the simulation ground truth engine at 10 Hz.
4. Calculate instantaneous horizontal Euclidean error and plot cumulative drift error over the 60-minute duration.
5. Compute the 95th percentile Circular Error Probable (CEP) metric.

**Required Inputs / Environment:**  
Gazebo SITL digital twin with high-resolution terrain mesh, ground-truth trajectory logger, VIO+DEM state estimator.

**Expected Result:**  
Cumulative horizontal drift after 60 minutes is strictly < 1.0 m; 95% CEP metric confirms sub-meter drift bounds.

**Pass/Fail Criteria:**  
PASS if cumulative horizontal position error after 1 hour of GNSS-denied flight is < 1.0 m; FAIL if cumulative error exceeds 1.0 m.

**Verification Evidence:**  
60-minute trajectory ground-truth vs estimated pose CSV dataset, CEP error distribution plots, and Tier 8 exit criteria verification log.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Metric alignment: REA-T1 Tier 8 specifies 'Sub-meter drift bounds sustained'; P02 draft cited '<0.8m error per hour'. Statistical confidence interval (1-sigma vs 2-sigma CEP) needs definition.

---

#### REQ-P-006 — Directional Free-Space Optical Data Throughput & Link Range

**Original Requirement:**
The Free-Space Optical (FSO) laser communications subsystem shall deliver high-bandwidth, jam-proof data throughput (target >= 1.2 Gbps) over an optical line-of-sight range of up to 18 kilometers.

**Acceptance Criteria:**
* AC-P-6.1: The FSO laser communications transceiver shall sustain a continuous digital data throughput of at least 1.2 Gigabits per second (>= 1.2 Gbps).
* AC-P-6.2: The optical link shall maintain transmission integrity across an optical line-of-sight distance of up to 18.0 kilometers in clear atmospheric conditions (visibility >= 20 km).
* AC-P-6.3: Uncorrected Bit Error Rate (BER) across the 1.2 Gbps link at maximum range shall not exceed 10^-6 (10 to the power of -6), dropping to < 10^-9 with Forward Error Correction (FEC).

**Verification Method:**  
Test

**Verification Procedure:**
1. Establish an 18-kilometer terrestrial optical test link between two mountain vantage points with unobstructed line of sight.
2. Align the airborne FSO optical transceiver head with the optical ground station receiver using the automated PAT coarse-fine loop.
3. Transmit a pseudo-random binary sequence (PRBS-31) data pattern at 1.2 Gbps using an instrumented Ethernet bit error rate tester (BERT).
4. Measure continuous data throughput and bit errors over a 30-minute transmission test period.
5. Record atmospheric visibility and link attenuation parameters.

**Required Inputs / Environment:**  
FSO optical transceiver prototypes, optical ground terminal, 10GbE Bit Error Rate Tester (BERT), optical power meter.

**Expected Result:**  
Sustained data throughput >= 1.2 Gbps over 18 km range with FEC-corrected BER < 10^-9.

**Pass/Fail Criteria:**  
PASS if throughput >= 1.2 Gbps is sustained over 18 km with BER <= 10^-6 uncorrected; FAIL if throughput drops below 1.2 Gbps or link cannot be maintained.

**Verification Evidence:**  
BERT throughput and bit error log files, optical receiver power level records, and link range survey certificates.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Throughput and 18 km range metrics originated in preliminary project proposals; REA-T1 confirms FSO architecture. Atmospheric attenuation bounds in fog/snow require validation.

---

#### REQ-P-007 — Heterogeneous Edge Compute AI Processing Capacity

**Original Requirement:**
The onboard compute fabric shall integrate heterogeneous processing cores (CPU, GPU, NPU, and DSP) delivering dedicated neural acceleration with a planned migration roadmap to sovereign Indian processors (C-DAC VEGA / IIT Madras SHAKTI).

**Acceptance Criteria:**
* AC-P-7.1: The edge compute substrate shall provide heterogeneous hardware acceleration including multi-core CPU, high-throughput GPU/tensor cores, dedicated NPU blocks, and DSP kernels on an integrated carrier module.
* AC-P-7.2: Total onboard computational rating shall deliver sufficient neural throughput to concurrently execute semantic segmentation, object detection, and change detection pipelines without CPU saturation (CPU load <= 80%).
* AC-P-7.3: The software architecture shall employ containerized, open standard interfaces (ONNX / POSIX / OpenCL) to guarantee portability toward sovereign C-DAC VEGA and IIT Madras SHAKTI RISC-V silicon roadmaps.

**Verification Method:**  
Inspection

**Verification Procedure:**
1. Audit hardware architecture design documents, board schematics, and component datasheets to verify CPU/GPU/NPU/DSP heterogeneous hardware allocation.
2. Execute standardized neural benchmark suites on the edge substrate measuring compute performance across INT8 and FP16 tensor operations.
3. Review software API abstraction layer code to confirm zero hard-coded proprietary vendor locks and verify compliance with sovereign silicon porting guidelines.

**Required Inputs / Environment:**  
Edge compute carrier board schematics, component hardware datasheets, software abstraction layer source code repositories.

**Expected Result:**  
Hardware documentation confirms heterogeneous compute matrix; software abstraction demonstrates verified path to Indian RISC-V silicon.

**Pass/Fail Criteria:**  
PASS if board delivers heterogeneous cores and software stack demonstrates vendor-independent neural model execution; FAIL if single-point proprietary locked architectures are used.

**Verification Evidence:**  
Board hardware architecture specification dossiers, compute benchmark test execution reports, and software portability audit sign-offs.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Discrepancy flagged: P02 cited Nvidia Jetson Orin Industrial SOM (275 TOPS); REA-T1 emphasizes zero-cloud heterogeneous processing with progressive migration to C-DAC VEGA & SHAKTI silicon.

---

#### REQ-P-008 — Quantized Neural Inference Real-Time Frame Throughput

**Original Requirement:**
Onboard visual neural models optimized and compiled for low-latency integer quantization (INT8) shall achieve real-time inference execution throughput of up to 60 frames per second (60 FPS).

**Acceptance Criteria:**
* AC-P-8.1: Visual object detection and feature extraction neural networks quantized to 8-bit integer precision (INT8) shall achieve an average inference execution throughput of at least 60 frames per second (>= 60 FPS).
* AC-P-8.2: Maximum single-frame inference latency at 60 FPS shall remain strictly under 16.6 milliseconds (<= 16.6 ms) per frame.
* AC-P-8.3: INT8 quantization accuracy loss relative to original FP32 baseline models shall not exceed 2.0% (<= 2.0% mAP drop).
* AC-P-8.4: [TBD — Requires Engineering Clarification] Standard input tensor resolution (e.g., 640x640 vs 1080p) and batch size for the 60 FPS throughput requirement require definition.

**Verification Method:**  
Test

**Verification Procedure:**
1. Deploy the INT8 post-training quantized neural model onto the onboard edge accelerator.
2. Feed a stream of 10,000 sequential test video frames through the inference pipeline via DMA memory buffers.
3. Measure start-to-finish timestamp for each frame inference cycle using high-resolution hardware timers.
4. Compute average frames per second throughput, 99th percentile inference latency, and compare detection mAP against FP32 reference model.

**Required Inputs / Environment:**  
Quantized INT8 neural model binary, 10,000-frame calibrated video validation dataset, hardware timer profiler.

**Expected Result:**  
Inference pipeline processes >= 60 FPS with per-frame latency <= 16.6 ms and quantization accuracy degradation <= 2.0%.

**Pass/Fail Criteria:**  
PASS if average inference throughput >= 60 FPS and per-frame latency <= 16.6 ms; FAIL if throughput is < 60 FPS or latency exceeds 16.6 ms.

**Verification Evidence:**  
Inference benchmark timing execution logs, frame-by-frame latency CSV exports, and FP32 vs INT8 accuracy comparison matrix.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Input image resolution at 60 FPS (640x640 vs 1080p), inference batch size, and thermal dissipation profile under high altitude require definition.

---

#### REQ-P-009 — Low-RCS Stealth Airframe Radar Cross-Section

**Original Requirement:**
The faceted carbon-composite monocoque airframe with embedded radar-absorbing material (RAM) shall achieve a reduced Radar Cross-Section (target estimated < 0.01 m²) across X and Ku radar frequency bands.

**Acceptance Criteria:**
* AC-P-9.1: The airframe aerodynamic shaping shall incorporate faceted low-RCS design principles, edge alignment, and radar-absorbing structural composites.
* AC-P-9.2: The computed monostatic Radar Cross-Section (RCS) shall achieve an average value of less than 0.01 square meters (< 0.01 m²) across X-band (8.0 to 12.0 GHz) and Ku-band (12.0 to 18.0 GHz) radar frequencies.
* AC-P-9.3: The < 0.01 m² RCS reduction shall be achieved across frontal and lateral aspect cones (+/- 45 degrees azimuth, +/- 15 degrees elevation relative to nose).
* AC-P-9.4: [TBD — Requires Engineering Clarification] Anechoic chamber physical measurement protocol and target turntable angular increments require formal definition.

**Verification Method:**  
Analysis

**Verification Procedure:**
1. Import the high-fidelity 3D CAD surface model of the RE-T1 airframe into a certified computational electromagnetics (CEM) solver (e.g., Ansys HFSS / FEKO).
2. Apply electromagnetic material properties representing the carbon-fibre composite layup and radar-absorbing surface coatings across 8 to 18 GHz.
3. Simulate monostatic radar backscatter at 1-degree angular increments across 360-degree azimuth and +/- 30-degree elevation.
4. Compute the spatial average RCS in square meters (m²) and decibel square meters (dBsm) across frontal and lateral operational sectors.

**Required Inputs / Environment:**  
Validated 3D CAD geometry of the RE-T1 airframe, material dielectric / magnetic permeability properties, CEM simulation software.

**Expected Result:**  
Simulated frontal and lateral aspect RCS averages < 0.01 m² (-20 dBsm) across X and Ku frequency bands.

**Pass/Fail Criteria:**  
PASS if CEM simulation confirms average frontal/lateral RCS is < 0.01 m² across 8–18 GHz; FAIL if average RCS equals or exceeds 0.01 m².

**Verification Evidence:**  
Computational electromagnetics simulation report, 2D/3D RCS polar backscatter plots, and material permittivity laboratory test certificates.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Numerical threshold of <0.01 m² RCS originated in proposal specifications; specific azimuth/elevation aspect cones and anechoic chamber test protocol require definition.

---

#### REQ-P-010 — Wideband Software-Defined Radio Spectrum Monitoring Range

**Original Requirement:**
The Software-Defined Radio (SDR) subsystem shall operate across a continuous wideband radio frequency monitoring range spanning from 400 MHz to 6 GHz (with design evaluation spanning 10 MHz to 6 GHz).

**Acceptance Criteria:**
* AC-P-10.1: The SDR RF front-end and receiver tuner shall operate across a continuous tuning frequency range spanning from 400 MHz to 6.0 GHz.
* AC-P-10.2: Instantaneous digitized receiver bandwidth shall provide at least >= 40 MHz per channel across the tuning range.
* AC-P-10.3: Receiver noise figure shall remain <= 6.0 dB across the 400 MHz to 6 GHz band, ensuring detection of low-power tactical RF emitters.
* AC-P-10.4: [Design Annex] The system shall maintain architecture compatibility to evaluate extended HF/VHF coverage (10 MHz to 400 MHz) using external matching networks.

**Verification Method:**  
Test

**Verification Procedure:**
1. Connect the SDR receiver antenna input port to a calibrated RF signal synthesizer and noise source inside a screened RF testing room.
2. Step the injected signal from 400 MHz to 6.0 GHz in 50 MHz increments at calibrated input power levels (-90 dBm to -20 dBm).
3. Measure received signal-to-noise ratio (SNR), receiver sensitivity, instantaneous bandwidth, and receiver spurious-free dynamic range (SFDR).
4. Verify continuous frequency lock and absence of internal harmonic blind spots across the complete band.

**Required Inputs / Environment:**  
Calibrated RF signal generator, noise figure meter, spectrum analyzer, SDR receiver hardware unit.

**Expected Result:**  
SDR tunes continuously across 400 MHz–6 GHz with instantaneous bandwidth >= 40 MHz and noise figure <= 6.0 dB.

**Pass/Fail Criteria:**  
PASS if receiver locks and captures valid RF signals across all test frequencies from 400 MHz to 6 GHz; FAIL if tuner fails to lock or bandwidth is < 40 MHz.

**Verification Evidence:**  
SDR tuner frequency sweep test report, noise figure vs frequency calibration plots, and RF laboratory test records.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Discrepancy flagged: REA-T1 Module 04 specifies 400 MHz to 6 GHz wideband SDR RF antenna inputs; P02 draft cited 10 MHz to 6 GHz. Antenna hardware tuning steps and lower band cutoff require clarification.

---

#### REQ-S-001 — Asynchronous Hardware Firewall & Autopilot Core Isolation

**Original Requirement:**
The flight control software stack shall execute on dedicated bare-metal microcontrollers physically independent of the Linux edge compute operating system to guarantee that edge AI exceptions cannot compromise flight stability.

**Acceptance Criteria:**
* AC-S-1.1: The primary flight stabilization control stack (PX4) shall execute exclusively on dedicated bare-metal microcontrollers (STM32H7 / aerospace MCU) physically separate from the Linux edge compute microprocessor.
* AC-S-1.2: Electrical power rails supplying the flight microcontroller and the edge AI compute module shall be galvanically or regulator-isolated, ensuring compute power transients cannot brown out flight avionics.
* AC-S-1.3: Total software crash, kernel panic, out-of-memory exception, or power cutoff of the Linux edge compute module shall induce zero disruption (0 ms delay) to the flight microcontroller's attitude stabilization loops.

**Verification Method:**  
Inspection

**Verification Procedure:**
1. Inspect electrical board schematics and physical PCB layouts to confirm physical processor separation, independent power regulators, and dedicated oscillator clocks.
2. On the integrated HIL benchtop rig, initiate active attitude stabilization loops on the microcontroller.
3. Concurrently trigger a kernel panic and memory thrashing freeze on the Linux edge compute processor.
4. Monitor microcontroller PWM servo outputs and attitude telemetry to verify uninterrupted flight control execution.

**Required Inputs / Environment:**  
PCB layout schematics, electrical power distribution diagrams, instrumented HIL avionics testbench.

**Expected Result:**  
Physical circuit separation verified; total crash of Linux edge processor induces zero interruption in microcontroller attitude control outputs.

**Pass/Fail Criteria:**  
PASS if physical hardware separation is verified and flight controller sustains nominal loop timing through Linux crash; FAIL if flight controller resets or locks up.

**Verification Evidence:**  
Hardware design review sign-off records, PCB trace routing inspection reports, and HIL fault-injection test logs.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
None. Confirmed core architectural safety requirement verified in system architecture documentation.

---

#### REQ-S-002 — Airborne Flight Software & Electronic Hardware Safety Standards

**Original Requirement:**
The flight software lifecycle and airborne electronic hardware components shall adhere to structured safety and validation standards governed by the 10-Tier Validation Ladder and applicable aerospace airworthiness guidelines (DO-178C / DO-254 / iDEX Evaluation Standard).

**Acceptance Criteria:**
* AC-S-2.1: Flight software code development shall adhere to coding standards (MISRA C / safety subset) with structural code coverage verification.
* AC-S-2.2: Progression between verification stages shall strictly comply with formal exit gates defined in the 10-Tier Validation Ladder (Tier 1 to Tier 10).
* AC-S-2.3: Lifecycle verification artifacts, trace matrices, and problem reports shall be compiled in conformance with iDEX / DIO / MoD evaluation standards.
* AC-S-2.4: [TBD — Requires Engineering Clarification] Specific Design Assurance Level (DAL A, B, or C) allocation across subsystems requires formal publication in PSAC/PHAC.

**Verification Method:**  
Analysis

**Verification Procedure:**
1. Audit software repository commits against static analysis tools (e.g., Cppcheck / SonarQube) to verify zero critical safety violations.
2. Review the bidirectional Requirements Traceability Matrix linking all requirements to verification tiers.
3. Verify that test logs and formal gate sign-offs exist for each ascending tier before authorizing subsequent tier progression.
4. Compile safety compliance dossier mapping engineering processes to iDEX airworthiness guidelines.

**Required Inputs / Environment:**  
Flight software source code repository, static analysis rule sets, 10-Tier Validation Ladder gate records.

**Expected Result:**  
Software complies with aerospace safety standards; verification gate records demonstrate complete traceability to evaluation standards.

**Pass/Fail Criteria:**  
PASS if code analysis shows zero critical safety violations and traceability matrix achieves 100% requirement coverage; FAIL if unmapped requirements or unresolved critical safety flaws exist.

**Verification Evidence:**  
Static analysis audit certificates, bidirectional traceability matrix, and formal gate sign-off minutes.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Design Assurance Level (DAL) allocation or military airworthiness standard equivalent (iDEX / DIO guidelines vs DO-178C) requires formalization in Safety Plan.

---

#### REQ-S-003 — Redundant Avionics Bus Communications & Hardware Watchdog Failsafe

**Original Requirement:**
The system shall route autopilot-to-compute communications over deterministic high-speed buses with hardware watchdog heartbeats, automatically executing internal return-to-home or failsafe procedures upon communication link loss.

**Acceptance Criteria:**
* AC-S-3.1: Autopilot-to-compute communications shall be routed over dual-redundant physical buses (CAN-BUS 2.0B / Ethernet / high-speed UART).
* AC-S-3.2: Both the flight controller and the edge compute node shall exchange bidirectional heartbeat messages at a continuous rate of >= 10 Hz.
* AC-S-3.3: If heartbeat messages are lost for a duration exceeding 500 milliseconds (watchdog timeout window), the flight controller shall declare communication loss.
* AC-S-3.4: Upon declaring communication loss, the flight controller shall autonomously engage predefined failsafe behavior (autonomous Return-to-Home or safe altitude loiter).

**Verification Method:**  
Test

**Verification Procedure:**
1. Establish active communication between flight controller and edge compute boards on the benchtop test fixture.
2. Monitor CAN/Ethernet bus traffic using a protocol analyzer to verify continuous 10 Hz heartbeat packet exchange.
3. Physically disconnect the communication bus cable to simulate bus severance.
4. Measure the elapsed time until the flight controller triggers internal failsafe mode and commands autonomous RTH actuation.

**Required Inputs / Environment:**  
CAN/Ethernet protocol bus analyzer, benchtop avionics rig, physical bus disconnect switch.

**Expected Result:**  
Heartbeats verified at >= 10 Hz; bus disconnect triggers internal autonomous failsafe in exactly <= 500 ms.

**Pass/Fail Criteria:**  
PASS if failsafe engages within 500 ms of heartbeat cessation and commands RTH; FAIL if watchdog fails to trigger or exceeds 500 ms.

**Verification Evidence:**  
Protocol analyzer communication bus trace files, flight controller failsafe event log files, and watchdog timer oscilloscope traces.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Bus protocols: REA-T1 Table 2 specifies High-Speed UART / Ethernet with MAVLink 2.0 / Micro-XRCE-DDS and CAN bus. Watchdog timeout duration (ms) requires formal baseline setting.

---

#### REQ-S-004 — Dual-Redundant Opto-Isolated Cargo Release Safety Interlock

**Original Requirement:**
The precision cargo drop mechanism shall be controlled via opto-isolated solid-state I/O requiring dual-redundant discrete logic signals to prevent accidental payload unlatching during boot, power transients, or software faults.

**Acceptance Criteria:**
* AC-S-4.1: The physical actuation circuit for the cargo release servo mechanism shall be opto-isolated from edge compute digital logic.
* AC-S-4.2: Cargo unlatching shall strictly require simultaneous asserted states on two independent discrete hardware logic channels (Dual-Redundant High/Low or Arm + Fire discrete signals).
* AC-S-4.3: Power-on reset, software reboot, supply voltage brownout, or single-point discrete line short-to-ground / short-to-VCC shall not actuate the cargo release mechanism.
* AC-S-4.4: Cargo unlatch actuation shall occur only when both valid discrete signals are asserted within an authorized timing coincidence window of <= 50 ms.

**Verification Method:**  
Test

**Verification Procedure:**
1. Connect the opto-isolated cargo release interlock PCB to digital I/O signal generators and connect an oscilloscope to the output servo release trigger.
2. Cycle system power 50 times (power-on reset audit); verify that output trigger remains strictly disarmed (0V).
3. Assert Channel A alone; verify zero output actuation. Assert Channel B alone; verify zero output actuation.
4. Assert Channel A and Channel B simultaneously within the authorized 50 ms window; verify deterministic release actuation pulse.
5. Inject short-circuit faults to ground and +5V on each line individually; verify zero uncommanded actuation.

**Required Inputs / Environment:**  
Cargo release interlock circuit board, dual-channel programmable digital signal generator, multi-channel oscilloscope.

**Expected Result:**  
Mechanism actuates only upon dual-asserted coincidence signals; zero uncommanded release during boots, single-channel triggers, or short faults.

**Pass/Fail Criteria:**  
PASS if 100% of single-channel and transient tests produce zero release and dual-channel trigger fires deterministically; FAIL if accidental release occurs.

**Verification Evidence:**  
Oscilloscope voltage capture waveforms, power-on transient audit logs, and hardware safety interlock test reports.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Discrete logic signal voltage levels, hardware pull-down resistor values, and software interlock state machine transitions require definition.

---

#### REQ-S-005 — Air-Gapped Inter-Process Communication & Network Isolation

**Original Requirement:**
The edge compute software architecture shall restrict all inter-process communications to local shared memory (POSIX shm) or loopback sockets under a hardened air-gapped OS, strictly prohibiting unvetted external network bridging.

**Acceptance Criteria:**
* AC-S-5.1: The edge operating system shall be an air-gapped hardened Linux distribution with real-time kernel patches (PREEMPT_RT).
* AC-S-5.2: All robotic middleware communications between sensor ingress, AI inference, and navigation nodes shall execute exclusively over local POSIX shared memory (shm) or loopback Unix sockets.
* AC-S-5.3: All physical external network ports (Wi-Fi, Bluetooth, commercial Ethernet) shall be physically disabled or firmware-locked during flight operations.
* AC-S-5.4: Kernel network routing tables shall contain zero default gateways, and iptables firewall rules shall drop 100% of unvetted external ingress packets.

**Verification Method:**  
Inspection

**Verification Procedure:**
1. Inspect operating system kernel configuration, systemd service units, and network configuration files.
2. Audit ROS 2 middleware configuration files (`fastdds.xml` / `cyclonedds.xml`) to verify localhost-only transport bindings.
3. Execute network port scanning tools (e.g., Nmap) against physical hardware ports on the booted aircraft compute board.
4. Verify that zero listening network services are exposed to external physical connectors.

**Required Inputs / Environment:**  
Hardened Linux root filesystem image, network security port scanner, ROS 2 middleware XML configuration profiles.

**Expected Result:**  
Zero external network interfaces active; all IPC verified over shared memory / loopback; Nmap scan detects zero open listening ports.

**Pass/Fail Criteria:**  
PASS if all external listening ports are closed and IPC is strictly local; FAIL if any unauthenticated external network socket is accessible.

**Verification Evidence:**  
Nmap network audit report, kernel routing table dumps, and software architecture security inspection records.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
None. Confirmed architectural safety rule verified in Section 6.3 and Section 8.3 of REA-T1.

---

#### REQ-S-006 — Pre-Flight Benchtop Integration Zero Bus Collision Endurance

**Original Requirement:**
The integrated avionics, sensors, and inter-module communication buses shall sustain continuous operation for at least 48 hours with zero bus collisions during benchtop integration (Tier 4) prior to flight test authorization.

**Acceptance Criteria:**
* AC-S-6.1: All integrated avionics, sensors (EO/IR, SDR, acoustic, GPR, IMU), compute modules, and power supplies shall be interconnected on the Tier 4 benchtop rig.
* AC-S-6.2: The system shall operate continuously for an uninterrupted duration of at least 48.0 hours under nominal electrical load.
* AC-S-6.3: Digital communication buses (CAN-BUS, SPI, UART, Ethernet) shall log zero bus collisions (0 collisions) and zero unhandled packet dropouts.
* AC-S-6.4: Operating temperatures of all compute ICs and voltage regulators shall remain within verified manufacturer thermal limits throughout the 48-hour run.

**Verification Method:**  
Test

**Verification Procedure:**
1. Assemble the complete flight avionics, sensors, power distribution units, and communication harness on the Tier 4 benchtop integration rig.
2. Connect hardware bus analyzers to CAN, SPI, UART, and Ethernet lines with automated error frame and collision detection logging enabled.
3. Initiate continuous simulated mission execution loops streaming multi-sensor data at full operational rate.
4. Maintain continuous operation for 48 uninterrupted hours while logging bus traffic, error counters, and thermal sensor telemetry.
5. Audit logged data at the conclusion of 48 hours to confirm zero collisions and thermal compliance.

**Required Inputs / Environment:**  
Tier 4 benchtop avionics integration rig, CAN/Ethernet hardware bus logging analyzers, automated test script sequencer.

**Expected Result:**  
System executes continuously for 48 hours with zero bus collisions, zero system resets, and all component temperatures within specification.

**Pass/Fail Criteria:**  
PASS if 48 hours of continuous operation complete with exactly 0 bus collisions and zero unplanned reboots; FAIL if collision occurs or system resets.

**Verification Evidence:**  
48-hour continuous bus analyzer log files, thermal telemetry history plots, and Tier 4 formal exit gate verification report.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Bus collision logging mechanism, error frame thresholds, and bus load percentage criteria require formal definition in HIL test protocol.

---

#### REQ-D-001 — Baseline System Requirements Specification (SRS) Milestone Freeze

**Original Requirement:**
The engineering team shall baseline and freeze the comprehensive System Requirements Specification (SRS) governing all 20 frozen advanced capabilities during Milestone 1 (Months 1–4).

**Acceptance Criteria:**
* AC-D-1.1: A formal System Requirements Specification (SRS) document complying with ISO/IEC/IEEE 29148 standards shall be authored.
* AC-D-1.2: The SRS shall establish complete functional, performance, interface, safety, and security requirements covering all 20 frozen advanced capabilities.
* AC-D-1.3: The SRS shall be formally approved and configuration-frozen by the Systems Engineering Review Board (SERB) and customer stakeholders before exiting Milestone 1 (Month 4).

**Verification Method:**  
Inspection

**Verification Procedure:**
1. Conduct formal engineering review of the drafted SRS document against ISO/IEC/IEEE 29148 requirements quality checklist.
2. Audit requirements coverage against the 20 frozen advanced capabilities outlined in `REA-T1-OVERVIEW-2026-V1.0`.
3. Verify formal sign-off signatures from engineering leads and customer representatives.
4. Check git repository version tag to verify that the approved SRS document is baselined and locked under configuration control.

**Required Inputs / Environment:**  
Drafted System Requirements Specification (SRS) document, ISO/IEC/IEEE 29148 compliance checklist, 20 frozen capability scope definitions.

**Expected Result:**  
Formally signed, configuration-frozen SRS document archived in project repository prior to Milestone 1 exit.

**Pass/Fail Criteria:**  
PASS if SRS document covers all 20 capabilities, contains all required approval signatures, and is committed under a baseline release tag; FAIL if incomplete or unapproved.

**Verification Evidence:**  
Signed SRS approval sign-off certificate, git baseline commit tag verification hash, and SERB review meeting minutes.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
SRS structure alignment with IEEE 29148 / iDEX milestone review criteria. REA-T1 Section 1.4 notes 20 frozen advanced capabilities; P02 cited 18 subsystems.

---

#### REQ-D-002 — Configuration-Controlled Project Scope Baseline Maintenance

**Original Requirement:**
The engineering team shall maintain a configuration-controlled Project Scope Baseline document establishing system boundaries, functional decomposition, environmental constraints, and open scope decisions.

**Acceptance Criteria:**
* AC-D-2.1: The Project Scope Baseline document shall define clear physical, electromagnetic, and cyber boundaries for the RudraEdge RE-T1 system.
* AC-D-2.2: The document shall maintain an active register of project constraints, working assumptions, and open technical clarifications.
* AC-D-2.3: Any modifications to scope, system boundaries, or deliverable definitions shall be processed through formal Engineering Change Proposals (ECP).

**Verification Method:**  
Inspection

**Verification Procedure:**
1. Review `P01_Project_Scope_Baseline.md` in the project repository.
2. Verify that subsystem breakdown reflects the 8-layer PECLF architecture and current project naming conventions.
3. Audit the document's revision history table to ensure all modifications are chronologically documented with author, date, and rationales.

**Required Inputs / Environment:**  
`P01_Project_Scope_Baseline.md` repository file, git commit history log.

**Expected Result:**  
Up-to-date, auditable Project Scope Baseline maintained under version control reflecting current technical consensus.

**Pass/Fail Criteria:**  
PASS if Scope Baseline reflects approved system boundaries and contains complete revision control records; FAIL if scope boundaries are contradictory or undocumented.

**Verification Evidence:**  
Git version history log, signed scope change approval forms, and current release copy of `P01_Project_Scope_Baseline.md`.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Delivered initially as P01_Project_Scope_Baseline.md; requires version control updates to align with RudraEdge RE-T1 naming and parameters.

---

#### REQ-D-003 — Auditable Numbered Requirements Register Maintenance

**Original Requirement:**
The engineering team shall establish and maintain an auditable, uniquely numbered Requirements Register workbook categorizing functional, security, performance, safety, and documentation requirements.

**Acceptance Criteria:**
* AC-D-3.1: The requirements register shall assign unique, stable identifiers to 100% of identified system requirements adhering to `REQ-[CAT]-[SEQ]` schema.
* AC-D-3.2: The workbook shall incorporate all 14 mandated metadata columns, including rationale, source reference, priority, verification method, dependencies, status, and review notes.
* AC-D-3.3: Traceability mapping from previous draft IDs to new IDs shall be documented with zero orphan records.
* AC-D-3.4: The workbook shall feature automated formulas, frozen headers, autofilters, and data validation drop-downs.

**Verification Method:**  
Inspection

**Verification Procedure:**
1. Open [`P03_Numbered_Requirements_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/P03_Numbered_Requirements_Register.xlsx) in an automated script and spreadsheet viewer.
2. Execute duplicate ID and format regex validation across all requirement rows.
3. Audit all 14 mandated columns to verify zero blank mandatory cells.
4. Inspect traceability mapping, formula calculations in category summaries, and data validation picklists.

**Required Inputs / Environment:**  
[`P03_Numbered_Requirements_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/P03_Numbered_Requirements_Register.xlsx), automated openpyxl validation script.

**Expected Result:**  
Fully compliant 14-column requirements register with 37 unique IDs, live formulas, zero duplicates, and complete traceability.

**Pass/Fail Criteria:**  
PASS if 100% of validation assertions succeed and all 14 columns are properly populated; FAIL if duplicate IDs, blank cells, or broken formulas exist.

**Verification Evidence:**  
Automated validation script execution logs ([`validate_p03.py`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/validate_p03.py)) and approved copy of `P03_Numbered_Requirements_Register.xlsx`.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Delivered as P03_Numbered_Requirements_Register.xlsx under Task 1 on 23 October 2026, establishing unique stable IDs and review notes.

---

#### REQ-D-004 — Safety Lifecycle Compliance Data & Requirement Traceability Matrix

**Original Requirement:**
The engineering team shall establish and maintain lifecycle verification artifacts, requirement-to-test traceability matrices, and verification evidence complying with aerospace safety and validation standards.

**Acceptance Criteria:**
* AC-D-4.1: A bidirectional Requirements Traceability Matrix (RTM) linking every requirement (D1 through D20 / REQ-F-001 through REQ-D-006) to its corresponding verification procedure, test tier, and evidence artifact shall be established.
* AC-D-4.2: The RTM shall achieve 100% coverage, demonstrating that zero unverified requirements enter flight qualification.
* AC-D-4.3: Safety lifecycle documentation shall compile safety registers, Hazard Analyses (FHA), and Failure Mode and Effects Analyses (FMEA).

**Verification Method:**  
Inspection

**Verification Procedure:**
1. Ingest the formal RTM database or spreadsheet into the requirements traceability verification tool.
2. Verify forward traceability from requirement to test case and backward traceability from test artifact to requirement.
3. Check for orphan requirements (requirements with no test case) and orphan test cases (tests with no parent requirement).
4. Review System Hazard Analysis and FMEA reports for completeness against airborne safety guidelines.

**Required Inputs / Environment:**  
Bidirectional Requirements Traceability Matrix, FMEA reports, System Hazard Analysis registers.

**Expected Result:**  
Complete bidirectional traceability matrix verifying 100% requirements coverage with zero orphan records.

**Pass/Fail Criteria:**  
PASS if 100% of requirements map bidirectionally to test procedures and hazard analyses are documented; FAIL if traceability gaps exist.

**Verification Evidence:**  
Bidirectional traceability matrix report, FMEA safety dossier, and quality assurance audit sign-off certificates.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Selection of formal traceability database tool and bidirectional matrix linking requirements D1-D20 to test tiers pending project formalization.

---

#### REQ-D-005 — Hardware-in-the-Loop Integration & Thermal Profiling Test Reports

**Original Requirement:**
The engineering team shall compile formal test reports, 48-hour bus collision audit logs, power audits, and sub-zero thermal profiling reports down to -20°C for all integrated benchtop HIL avionics during Milestone 2.

**Acceptance Criteria:**
* AC-D-5.1: Formal HIL Integration Test Reports shall be authored documenting results from Milestone 2 and Tiers 3, 4, and 5.
* AC-D-5.2: The documentation package shall include 48-hour continuous bus collision audit logs verifying zero collisions on inter-module buses.
* AC-D-5.3: Thermal chamber profiling reports down to -20°C ambient shall record component temperature histories and power consumption audits.

**Verification Method:**  
Inspection

**Verification Procedure:**
1. Inspect the compiled Milestone 2 HIL Integration Test Report package.
2. Verify inclusion of raw bus analyzer data logs showing 48 hours of continuous operation with zero collisions.
3. Confirm that thermocouple data logs verify nominal thermal stabilization down to -20°C.
4. Check formal engineering review sign-offs from Hardware Lead and Systems Engineer.

**Required Inputs / Environment:**  
Milestone 2 HIL Integration Test Report, raw 48-hour bus collision log files, thermal chamber data plots.

**Expected Result:**  
Comprehensive, signed HIL test report package verifying benchtop avionics integration and sub-zero thermal endurance.

**Pass/Fail Criteria:**  
PASS if test report contains complete data logs, verifies zero bus collisions, and is signed by engineering leads; FAIL if reports are missing or incomplete.

**Verification Evidence:**  
Formally approved Milestone 2 HIL Test Report package and raw testbed instrument log archives.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Milestone 2 deliverable. Chamber thermal profiling down to -20°C aligned with REA-T1 Milestone 2 output (P02 cited -30°C).

---

#### REQ-D-006 — Comprehensive Defense Qualification & Pre-Induction Trial Dossiers

**Original Requirement:**
The project team shall compile comprehensive defense qualification dossiers, safety registers, failure mode analyses, and manufacturing documentation packages prior to Milestone 5 pre-induction field trials.

**Acceptance Criteria:**
* AC-D-6.1: A comprehensive Defense Qualification Dossier conforming to iDEX / DIO / MoD defense evaluation guidelines shall be compiled prior to Milestone 5.
* AC-D-6.2: The dossier shall consolidate all verification records across Tiers 1 through 10, including simulation models, HIL reports, flight envelope test cards, and high-altitude field demonstration logs.
* AC-D-6.3: The documentation package shall include series production manufacturing drawings, Bill of Materials (BOM), assembly work instructions, and quality control plans.

**Verification Method:**  
Inspection

**Verification Procedure:**
1. Audit the assembled Milestone 5 Pre-Induction Trial Dossier against MoD / iDEX evaluation guidelines.
2. Verify inclusion of complete test evidence covering all 10 tiers of the Validation Ladder.
3. Verify manufacturing documentation completeness, including BOMs, assembly procedures, and quality checklists.
4. Obtain formal sign-offs from Project Lead Sarvesh Sharma and quality assurance directors.

**Required Inputs / Environment:**  
Consolidated Defense Qualification Dossier, 10-Tier verification evidence binder, manufacturing drawing package.

**Expected Result:**  
Complete, auditable defense evaluation dossier prepared and approved for submission to Indian Armed Forces and MoD evaluators.

**Pass/Fail Criteria:**  
PASS if dossier contains complete verification records across all 10 tiers and satisfies defense evaluation submission requirements; FAIL if documentation is incomplete.

**Verification Evidence:**  
Signed Defense Qualification Dossier submission certificate, MoD evaluation acknowledgment, and manufacturing data package.

**Test Case ID:**  
`TBD — Test Case Not Yet Assigned`

**Status:**  
Planned

**Open Issues:**  
Milestone 5 final project deliverable dossier structure to follow formal iDEX demonstration and defense evaluation guidelines.

---

### 6. Requirements with Incomplete Acceptance Criteria

To prevent the introduction of unverified or fabricated engineering parameters, requirements whose complete quantitative pass thresholds depend on pending hardware selection, supplier datasheets, or classified payload parameters are formally cataloged below:

| Requirement ID | Missing Technical Information | Why Clarification is Necessary | Type of Decision / Specification Required | Suggested Responsible Discipline / Reviewer |
|---|---|---|---|---|
| **REQ-F-001** | Optical camera sensor resolution (4K vs 1080p), horizontal Field of View (FOV in degrees), and continuous zoom magnification ratio. | Prevents exact optical pixel density calculations and angular resolution verification during perception tests. | Sensor Selection & Interface Control Document (ICD) | Electro-Optics & Payload Lead |
| **REQ-F-002** | Micro-GPR RF center frequency, frequency sweep bandwidth (MHz), and soil/ice penetration depth (m). | Radar echo processing algorithms and antenna RF matching networks cannot be finalized without center frequency and bandwidth. | Radar Payload Specification & RF ICD | Subsurface Radar & DSP Lead |
| **REQ-F-003** | Acoustic sampling frequency (kHz) and minimum acoustic impulse detection sensitivity threshold (dB SPL). | Dictates DSP buffer sizing, ADC hardware selection, and acoustic noise filtering thresholds under turbulent winds. | Acoustic Sensor Specification | Signal Processing & Avionics Lead |
| **REQ-F-006** | Formal target class taxonomy and minimum acceptable mean Average Precision (mAP@0.50) threshold. | Prevents objective pass/fail determination during automated edge object detection verification. | Tactical AI Doctrine & Evaluation Criteria | Edge AI & Deep Learning Lead |
| **REQ-F-007** | Standardized semantic terrain class labels and minimum acceptable mean Intersection-over-Union (mIoU) percentage. | Autonomous obstacle avoidance and safe landing evaluation cannot be objectively scored without approved class definitions. | Edge AI Validation Guidelines | Computer Vision Lead |
| **REQ-F-008** | Minimum detectable ground disturbance physical dimensions (meters) and image geo-referencing spatial tolerance. | Prevents objective verification of whether small fortifications or minor tire tracks must trigger automated alerts. | Mission Operational Requirements Document | Tactical Intelligence Analyst / AI Lead |
| **REQ-F-011** | Maximum allowable laser pointing jitter in microradians (µrad) and link re-acquisition latency budget (ms). | High wind shear PAT testing cannot establish clear pass/fail beam divergence boundaries without jitter tolerances. | Optical GNC Engineering Baseline | Optical Communications & GNC Lead |
| **REQ-F-013** | Cargo drop pod maximum payload mass capacity (kg), internal volume envelope, and Circular Error Probable (CEP) delivery accuracy. | Airframe structural hardpoint stress calculations and ballistic calculator trajectory tuning depend on mass properties. | Mechanical Cargo Mechanism ICD | Mechanical & Payload Systems Lead |
| **REQ-P-004** | Confirmation whether -20°C is the formal environmental qualification threshold and -30°C represents an extreme survival boundary. | Dictates battery heater power consumption budgets and thermal insulation thickness in the airframe. | Environmental Qualification Test Plan | Thermal & Environmental Lead |
| **REQ-P-005** | Statistical confidence interval (1-sigma, 2-sigma, or 95% CEP) governing the < 1.0 m drift bound over 1 hour. | Ambiguous statistical bounds prevent mathematical consensus on GNSS-denied trajectory pass/fail results. | Navigation Accuracy Standard | Navigation & Guidance (GNC) Lead |
| **REQ-P-008** | Input video frame resolution (640x640 vs 1080p) and batch size for the 60 FPS INT8 inference requirement. | Throughput cannot be validated without freezing input tensor dimensions; larger matrices require higher TOPS. | AI Inference Specification | Edge AI Software Lead |

---

### 7. Verification Coverage Summary

A rigorous statistical summary of verification allocation across all 37 requirements is detailed below. Planned verification is strictly distinguished from completed verification:

#### 7.1 Requirements Status & Verification Metrics

| Verification Metric / Attribute | Quantity (Count) | Percentage of Total | Notes & Engineering Status |
|---|:---:|:---:|---|
| **Total Requirements Reviewed** | **37** | **100.0%** | Full requirements inventory baselined in `P03_Numbered_Requirements_Register.xlsx`. |
| **Requirements with Defined Acceptance Criteria** | **26** | **70.3%** | Unambiguous pass/fail conditions established using documented project specifications. |
| **Requirements Requiring Engineering Clarification** | **11** | **29.7%** | Specific numerical thresholds marked `TBD` pending sensor selection or ICD freeze (Section 6). |
| **Requirements with Assigned Verification Method** | **37** | **100.0%** | All 37 requirements assigned to Test, Demonstration, Inspection, or Analysis. |
| **Requirements with Formally Assigned Test Case IDs** | **0** | **0.0%** | All marked `TBD — Test Case Not Yet Assigned` (formal test cases allocated in M2 HIL plan). |
| **Requirements Actually Verified (Supported by Evidence)** | **0** | **0.0%** | **Desk-based phase:** Zero physical or simulation test runs claimed as completed. |
| **Requirements Pending Verification Execution** | **37** | **100.0%** | All 37 requirements scheduled for verification across the 10-Tier Validation Ladder. |

#### 7.2 Breakdown by Assigned Verification Method

| Verification Method | Requirements Count | Percentage | Primary Requirement Categories |
|---|:---:|:---:|---|
| **Test (T)** | **17** | **45.9%** | All Performance requirements (`REQ-P`), hardware security wiping (`REQ-SEC`), safety watchdog/interlocks (`REQ-S`), and VIO navigation. |
| **Demonstration (D)** | **10** | **27.0%** | Functional mission behaviors (`REQ-F`): EO/IR video ingress, acoustic TDoA, PX4 waypoint flight, edge AI models, FSO laser, and cargo release. |
| **Inspection (I)** | **8** | **21.6%** | All Documentation deliverables (`REQ-D`), compute architecture review (`REQ-P-007`), hardware isolation (`REQ-S-001`), and network air-gapping (`REQ-S-005`). |
| **Analysis (A)** | **2** | **5.4%** | Stealth RCS electromagnetic backscatter (`REQ-P-009`) and airborne safety compliance process audit (`REQ-S-002`). |
| **Total** | **37** | **100.0%** | **Comprehensive multi-method verification architecture** |

---

### 8. Review Checklist

Prior to baselining, this document was validated against the following systems engineering review checklist:

| # | Verification & Review Check Item | Verification Status | Compliance Evidence / Finding |
|---|---|:---:|---|
| 1 | **Requirement ID Preservation** | **COMPLIANT** | 100% of requirement IDs match [`P03_Numbered_Requirements_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/P03_Numbered_Requirements_Register.xlsx) exactly (`REQ-F-001` to `REQ-D-006`). Zero renumbering. |
| 2 | **Complete Requirement Inventory** | **COMPLIANT** | All 37 registered requirements have individual subsections under Section 5. Zero omissions. |
| 3 | **Objective Acceptance Criteria** | **COMPLIANT** | Vague phrases eliminated; pass conditions define observable signals, timing bounds, or explicit `TBD` markers. |
| 4 | **Method Appropriateness** | **COMPLIANT** | Verification methods allocated based on engineering feasibility (Test for quantitative metrics, Demonstration for functional behaviors). |
| 5 | **Pass/Fail Rule Documentation** | **COMPLIANT** | Every requirement contains explicit pass/fail decision rules with defined boundary conditions. |
| 6 | **Zero Fabrication of Specifications** | **COMPLIANT** | Numerical values derived strictly from `REA-T1-OVERVIEW-2026-V1.0`; missing parameters explicitly marked as `TBD`. |
| 7 | **Explicit Gap & Issue Logging** | **COMPLIANT** | Section 6 catalogs all 11 technical gaps with required decision types and responsible engineering disciplines. |
| 8 | **Evidence-Based Status Designation** | **COMPLIANT** | All requirements marked as `Planned`; zero unsupported claims of test execution or pre-mature approval. |
| 9 | **Scope & Baseline Consistency** | **COMPLIANT** | Fully aligned with `P01_Project_Scope_Baseline.md`, `P03_Numbered_Requirements_Register.xlsx`, and `REA-T1-OVERVIEW-2026-V1.0`. |

---

### 9. Conclusion

The **Requirements Acceptance Criteria and Verification Plan** (`P04_Requirements_Acceptance_Criteria.md`) successfully establishes an auditable, rigorous, and technically defensible verification baseline for the **RudraEdge RE-T1 (Spectra)** project.

#### Key Accomplishments:
1. **Complete Requirement Coverage:** Every one of the 37 requirements from `P03` has been expanded into measurable acceptance criteria, structured verification procedures, expected outcomes, and pass/fail rules.
2. **Ethical Verification Rigor:** By explicitly designating all verification activities as **Planned** and assigning **`TBD — Test Case Not Yet Assigned`**, the document prevents premature or fictitious claims of compliance.
3. **Actionable Technical Gap Registry:** Eleven specific engineering parameter gaps have been cataloged in Section 6, providing a clear roadmap for sensor selection, ICD finalization, and formal SRS freezing during Milestone 1.

#### Readiness and Next Steps:
With the baselining of `P03` (Numbered Requirements Register) and `P04` (Acceptance Criteria & Verification Plan), the requirements engineering foundation for Project Rudra-Tactical is complete. The engineering team is prepared to advance into **Milestone 1 Digital Twin modeling (Gazebo / PX4 SITL)** and subsequently formulate formal test cases for **Milestone 2 Hardware-in-the-Loop (HIL) benchtop integration**.
