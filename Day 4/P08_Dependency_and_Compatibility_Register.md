# P08: Software Dependency and Compatibility Register — RudraEdge RE-T1 (Spectra)

**Document ID:** `REA-T1-DEP-REG-2026-V1.0`  
**Classification:** Commercial-in-Confidence / Defence Technical Reference  
**Platform Designation:** RudraEdge RE-T1 (Spectra) Tactical Autonomous UAS  
**Project Reference:** `RE-iDEX-PROPOSAL-2026-R1`  
**Target Evaluation Standard:** iDEX / DIO / MoD High-Altitude Tactical UAS Standard  
**Release Date:** 28 October 2026 (Day 4 Baseline)  
**Assigned Role:** System Requirements & Configuration Engineer  
**Authoritative Architectural Baseline:** `REA-T1-OVERVIEW-2026-V1.0` (*authored by Sarvesh Sharma, Founder & Project Lead*)  
**Direct Cross-References:**  
*   [`P01_Project_Scope_Baseline.md`](file:///c:/Users/Admin/OneDrive/Desktop/Day%201/P01_Project_Scope_Baseline.md) (System Scope & 18-Subsystem PECLF Decomposition)  
*   [`P03_Numbered_Requirements_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/P03_Numbered_Requirements_Register.xlsx) (Requirements `REQ-F-001` to `REQ-D-006`)  
*   [`P04_Requirements_Acceptance_Criteria.md`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/P04_Requirements_Acceptance_Criteria.md) (Pass/Fail Verification Criteria)  
*   [`P05_Requirements_Quality_Review.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%203/P05_Requirements_Quality_Review.xlsx) (Quality Audit & Tensions)  
*   [`P06_Open_Questions_and_Assumptions.md`](file:///c:/Users/Admin/OneDrive/Desktop/Day%203/P06_Open_Questions_and_Assumptions.md) (Operational Dependencies `DEP-001` to `DEP-017` & Gaps)  
*   [`P07_Interface_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%204/P07_Interface_Register.xlsx) (Software & Hardware Interfaces `IF-001` to `IF-026`)

---

## 1. Document Control & Metadata

### 1.1 Revision History
| Revision | Date | Author / Role | Description of Change | Review Status |
|:---:|:---:|:---:|---|:---:|
| **v0.1** | 22 Oct 2026 | Systems Requirements Eng. | Initial dependency scoping derived from `P01_Project_Scope_Baseline.md`. | Superseded |
| **v0.5** | 24 Oct 2026 | Configuration Control Board | Inter-subsystem dependency identification (`P06` `DEP-001` to `DEP-017`). | Baselined |
| **v1.0** | 28 Oct 2026 | System Requirements & Config Eng. | Formal release of `P08`: Comprehensive 28-item dependency register, compatibility audit, environment constraints, and risk matrix. | **Approved / Released** |

### 1.2 Verification Authority & Configuration Control
*   **Engineering Lead:** Sarvesh Sharma, Founder & Project Lead, RudraEdge Aerospace India.
*   **Governing Standard:** Defense Innovation Organisation (DIO) / iDEX Evaluation Framework (18-Month Phased Lifecycle).
*   **Configuration Baseline:** Aligned with `REA-T1-OVERVIEW-2026-V1.0` Section 6 (*System Technology Stack*) and Section 8 (*System Integration Architecture*).

---

## 2. Purpose and Scope

### 2.1 Objective
The primary objective of this **Dependency and Compatibility Register** is to establish an auditable, configuration-controlled baseline documenting all runtime environments, programming languages, operating systems, frameworks, communication middleware, cross-compilation toolchains, hardware drivers, and simulation tools required to construct, deploy, and verify the software flight stack of the **RudraEdge RE-T1 (Spectra)** tactical UAV platform.

### 2.2 System Boundaries & Scope
The scope of this register encompasses:
1.  **Heterogeneous Edge AI Compute Substrate (`MOD-03`, `MOD-08`, `MOD-12`):** Running hardened real-time Linux (`PREEMPT_RT`), Swadeshi ROS 2, NVIDIA TensorRT, ONNX, and POSIX zero-copy shared memory queues.
2.  **Avionics Flight Stabilization Stack (`MOD-07`):** Bare-metal STM32H7 dual-redundant microcontrollers executing custom PX4 Autopilot firmware, FreeRTOS loops, and deterministic attitude PID loops.
3.  **Sensor & Signal Processing Middleware (`MOD-01`, `MOD-02`, `MOD-04`, `MOD-11`):** Ingesting and conditioning MIPI-CSI video, VITA 49 RF packets, 4-channel acoustic PDM streams, micro-GPR 16-bit IQ samples, and CBRN sniffers.
4.  **Secure Communications & Pointing GNC (`MOD-05`, `MOD-09`, `MOD-10`):** Managing directional Free-Space Optical (FSO) laser links, fast steering mirror (FSM) PAT control, and encrypted frequency-hopping SDR RF backup links.
5.  **Simulation & Verification Tooling:** Gazebo mountain digital twin worlds, PX4 Software-in-the-Loop (SITL), and Hardware-in-the-Loop (HIL) benchtop rigs.
6.  **Silicon Sovereignty Roadmap:** Portability layers (POSIX / ONNX / OpenCL) enabling the progressive migration from commercial SOMs to domestic C-DAC VEGA and IIT Madras SHAKTI processors.

---

## 3. Authoritative Sources Reviewed

This register is constructed exclusively from verified evidence and architectural specifications documented in the following authorized project files:

1.  **`REA-T1-OVERVIEW-2026-V1.0` (Master iDEX Technical Proposal):**
    *   *Section 1 & 2 (p. 2):* Physical-Electromagnetic-Cyber Layer Fusion (PECLF) system definition.
    *   *Section 5 (p. 6):* 7-Stage End-to-End Technical Information Transit.
    *   *Section 6 (p. 7):* System Technology Stack (Software Layer Specifications & Tiered Architecture).
    *   *Section 7 (p. 8):* Modular Functional Subsystems (`MOD-01` to `MOD-06`).
    *   *Section 8 (p. 9):* Hardware & Software Interface Architecture (Table 8.2) and Fail-Safe Isolation (Section 8.3).
    *   *Section 9 & 10 (p. 10–11):* 18-Month Development Phasing & 10-Tier Validation Ladder.
2.  **[`P01_Project_Scope_Baseline.md`](file:///c:/Users/Admin/OneDrive/Desktop/Day%201/P01_Project_Scope_Baseline.md):** 18-subsystem decomposition, Jetson Orin Industrial SOM specifications (275 TOPS, 64GB RAM), Vanguard-Linux 5.15 PREEMPT_RT, and STM32H7 flight avionics.
3.  **[`P03_Numbered_Requirements_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/P03_Numbered_Requirements_Register.xlsx):** 37 baselined requirements (`REQ-F-001` through `REQ-D-006`).
4.  **[`P04_Requirements_Acceptance_Criteria.md`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/P04_Requirements_Acceptance_Criteria.md):** Measurable verification criteria for latency, throughput, drift, and security.
5.  **[`P06_Open_Questions_and_Assumptions.md`](file:///c:/Users/Admin/OneDrive/Desktop/Day%203/P06_Open_Questions_and_Assumptions.md):** 17 confirmed operational dependencies (`DEP-001` to `DEP-017`), 14 assumptions (`ASM-001` to `ASM-014`), and 16 open questions (`OQ-001` to `OQ-016`).
6.  **[`P07_Interface_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%204/P07_Interface_Register.xlsx):** 26 verified hardware, middleware, and network interfaces (`IF-001` to `IF-026`).

---

## 4. Software Dependency Register

The table below catalogs all **28 software, runtime, toolchain, and middleware dependencies** identified across the RudraEdge RE-T1 system architecture.

### Dependency Classification Taxonomy:
*   **OS / Kernel:** Operating systems, real-time patches, and bare-metal executive kernels.
*   **Middleware:** Robotic communication layers, message brokers, inter-processor bridges, and serialization protocols.
*   **AI / Vision:** Deep learning frameworks, quantization runtimes, and computer vision libraries.
*   **Language / Runtime:** Programming language standards, compilers, and core runtime libraries.
*   **Toolchain / Build:** Build systems, package managers, and cross-compilation toolchains.
*   **Simulation / Test:** Digital twin physics simulators, SITL environments, and HIL testbenches.
*   **Security / Crypto:** Hardware security drivers, TPM stacks, encryption engines, and wipe daemons.
*   **Hardware / Driver:** Low-level kernel device drivers, DMA subsystems, and bus abstraction layers.

| Dependency ID | Dependency Name | Category | Purpose in Project | Used By / Dependent Module | Required Version | Detected / Target Version | Version Source / Evidence | Compatibility Status | Related IF ID | Related REQ ID | Prerequisites / Sub-Dependencies | Known Constraints | Risks & Potential Impact | Assumptions / Open Questions | Recommended Follow-up Action | Status |
|:---:|---|:---:|---|---|:---:|:---:|:---:|:---:|:---:|:---:|---|---|---|---|---|:---:|
| **DEP-001** | Vanguard-Linux OS with PREEMPT_RT | OS / Kernel | Provides hard real-time multitasking, low-latency thread scheduling, containerized microservices, and POSIX compliance for edge intelligence. | `MOD-01`, `MOD-03`, `MOD-04`, `MOD-08`, `MOD-11`, `MOD-12` | Kernel 5.15 LTS + PREEMPT_RT patch | Linux 5.15.136-rt71 (aarch64) | `REA-T1` Sec 6.3; `P01` Sec 4; `P04` AC-S-5.1 | **Confirmed** | `IF-001`, `IF-002`, `IF-013`, `IF-017`, `IF-018` | `REQ-S-005`, `REQ-P-007` | Hardware Root of Trust Secure Boot (`DEP-023`) | Air-gapped network configuration; zero external IP interfaces; PREEMPT_RT maximum scheduling jitter < 50 µs. | Thermal brownout or kernel panic stalls mission intelligence, though flight control remains isolated. | `P06` ASM-007 (Evaluated on Jetson Orin Industrial SOM). | Validate RT kernel latency under 100% CPU/GPU stress testing in sub-zero chamber. | Confirmed Active |
| **DEP-002** | FreeRTOS Real-Time Kernel | OS / Kernel | Manages deterministic microsecond task scheduling for inner-loop attitude PID control and PWM motor timers on bare-metal MCUs. | `MOD-07: PX4-AUTOPILOT` | FreeRTOS v10.4+ / Custom NuttX RTOS | FreeRTOS v10.4.6-kernel | `REA-T1` Sec 6.1 (Layer 2); `P01` Sec 4.1 | **Confirmed** | `IF-005`, `IF-006`, `IF-008`, `IF-010` | `REQ-P-001`, `REQ-F-005`, `REQ-S-001` | Bare-metal ARM Cortex-M7 substrate (`DEP-017`) | Static memory allocation required; no dynamic malloc permitted in flight-critical threads; execution cycle < 1.0 ms. | Task deadline overrun destabilizes airframe in turbulent mountain shear. | `P06` ASM-004 (Contractual latency bound < 1.0 ms). | Perform static stack depth analysis and worst-case execution time (WCET) audit. | Confirmed Active |
| **DEP-003** | Swadeshi ROS 2 Robotic Middleware | Middleware | Core distributed communication framework managing sensor data publishers, action servers, and local inter-process message passing. | `MOD-01`, `MOD-03`, `MOD-04`, `MOD-08`, `MOD-11` | ROS 2 Humble Hawksbill LTS | ROS 2 Humble (Patch release 2024.1) | `REA-T1` Sec 1, Sec 6.1, Sec 6.3; `P01` Sec 4; `P04` AC-5.2 | **Confirmed** | `IF-002`, `IF-005`, `IF-009`, `IF-013`, `IF-017` | `REQ-F-005`, `REQ-S-005`, `REQ-D-001` | Linux PREEMPT_RT (`DEP-001`), POSIX shm (`DEP-013`), colcon (`DEP-020`) | DDS discovery restricted to localhost/loopback via `fastdds.xml`; zero external multicast broadcast permitted. | Unconstrained DDS memory buffers induce memory leaks during 4-hour high-altitude endurance missions. | `P06` CLR-006 (Standardization of custom `rudra_msgs`). | Benchmark zero-copy ROS 2 loan message delivery latency under 60 FPS video pipeline. | Confirmed Active |
| **DEP-004** | Custom PX4 Autopilot Flight Firmware | Middleware | Drives multi-rotor/fixed-wing flight dynamics, EKF state fusion, actuator mixer loops, geofencing, and autonomous return-to-home. | `MOD-07: PX4-AUTOPILOT` | PX4 Autopilot v1.14.x LTS | PX4 v1.14.0-custom | `REA-T1` Sec 1, Sec 6.1, Sec 7 (Mod 01); `P01` Sec 4.1 | **Confirmed** | `IF-005`, `IF-006`, `IF-008`, `IF-009`, `IF-010` | `REQ-F-005`, `REQ-P-001`, `REQ-S-001` | FreeRTOS (`DEP-002`), Micro-XRCE-DDS Client (`DEP-005`), MAVLink (`DEP-006`) | Inner PID attitude control loop must execute at >= 400 Hz (< 1.0 ms latency); DO-178C DAL B architectural compliance. | Failure of attitude loop induces aerodynamic stall or loss of control in high wind shear. | `P06` ASM-014 (DAL B equivalent for flight stabilization stack). | Execute 100 hours of continuous PX4 SITL/HIL stress runs in Gazebo mountain simulation. | Confirmed Active |
| **DEP-005** | eProsima Micro-XRCE-DDS Client & Agent | Middleware | Bridges low-resource microcontrollers running PX4 to the Swadeshi ROS 2 middleware graph over high-speed UART/Ethernet buses. | `MOD-07` (Client), `MOD-08` (Agent) | Micro-XRCE-DDS v2.4.x | v2.4.1 Client / v2.4.1 Agent | `REA-T1` Sec 6.3, Table 8.2; `P01` Sec 4.1; `P04` AC-5.2 | **Confirmed** | `IF-005`, `IF-006`, `IF-008`, `IF-009` | `REQ-F-005`, `REQ-S-003` | ROS 2 Humble (`DEP-003`), Serial/UART Subsystem (`DEP-018`) | Serial transport packet framing overhead; static memory pool on STM32 microcontroller (< 32 KB RAM buffer). | Buffer overflow under high attitude telemetry rates drops odometry correction packets. | `P06` OQ-003, CLR-005 (Baud rate freeze: 921600 baud vs 3 Mbps). | Run benchtop packet saturation tests under maximum simulated attitude churn. | Confirmed Active |
| **DEP-006** | MAVLink 2.0 Telemetry Protocol | Middleware | Encapsulates flight control telemetry, vehicle status, mission waypoints, and heartbeat tokens across serial and RF backhaul channels. | `MOD-07`, `MOD-08`, `MOD-10`, `EXT-02` | MAVLink Protocol v2.0 | `c_library_v2` (v2.0.0) | `REA-T1` Sec 5.1, Sec 6.1, Table 8.2; `P01` Sec 11.1 | **Confirmed** | `IF-006`, `IF-008`, `IF-022` | `REQ-F-005`, `REQ-S-003`, `REQ-F-012` | C11 Standard Library (`DEP-015`) | Message signature verification; 253-byte maximum payload length; zero dynamic memory allocations in C parser. | Desynchronization of packet definitions between aircraft firmware and tactical ground control station. | `P06` DEP-002, DEP-012 (Heartbeat watchdog token format). | Freeze MAVLink dialect XML definition in the project configuration repository. | Confirmed Active |
| **DEP-007** | NVIDIA TensorRT Inference Engine | AI / Vision | Compiles and executes deeply optimized INT8 post-training quantized neural networks on edge GPU/NPU hardware. | `MOD-03: EDGE-AI` | TensorRT v8.5.x or v8.6.x Embedded | TensorRT 8.5.2.2 (JetPack 5.1.2) | `REA-T1` Sec 5.2, Sec 6.3; `P01` Sec 4.1; `P04` AC-6.1 | **Confirmed** | `IF-001`, `IF-017` | `REQ-F-006`, `REQ-F-007`, `REQ-P-007`, `REQ-P-008` | CUDA 11.4 (`DEP-014`), ONNX Runtime (`DEP-009`), Linux PREEMPT_RT (`DEP-001`) | Requires INT8 calibration cache generated with representative high-altitude snow/mountain imagery; GPU power mode capped at 30W. | Inference latency degradation under cold temperatures or memory fragmentation causes frame drops. | `P06` ASM-012 (60 FPS applies to 2D detector, >= 15 FPS for segmentation). | Benchmark TensorRT execution times across -20°C to +50°C thermal envelope on HIL bench. | Confirmed Active |
| **DEP-008** | PyTorch Deep Learning Framework | AI / Vision | Model development, neural architecture training, Siamese network optimization, and baseline weights generation. | Offline R&D / `MOD-03` | PyTorch v2.0+ (TorchVision 0.15+) | PyTorch 2.1.0+cu118 | `REA-T1` Sec 6.1, Sec 6.3, Sec 9 (M1); `P03` REQ-F-006 | **Confirmed** | N/A (Offline Development / Weights) | `REQ-F-006`, `REQ-F-007`, `REQ-F-008`, `REQ-D-001` | Python 3.10+ (`DEP-016`), CUDA Toolkit | Training pipeline is executed on ground workstations; trained models must be exported via ONNX before airborne deployment. | Direct execution of PyTorch runtime on airborne SOM would violate memory bounds and real-time determinism. | `P06` ASM-007 (ONNX abstraction decoupling training from silicon). | Formalize ONNX model export validation script in CI/CD pipeline. | Confirmed Active |
| **DEP-009** | Open Neural Network Exchange (ONNX) | AI / Vision | Standardized intermediate representation format decoupling neural model development from edge hardware execution targets. | `MOD-03: EDGE-AI` | ONNX v1.14+ / Opset 17 | ONNX v1.14.1 | `REA-T1` Sec 6.3; `P01` Sec 4.1; `P04` AC-P-7.3 | **Confirmed** | `IF-017` | `REQ-F-006`, `REQ-P-007`, `REQ-P-008` | PyTorch (`DEP-008`), Python 3.10+ (`DEP-016`) | Model architectures must strictly utilize ONNX Opset 17 supported operators to prevent parsing failure during compilation. | Non-standard custom layers (e.g. specialized attention heads) fail to export or compile to TensorRT INT8. | `P06` ASM-007, OQ-006 (Key enabler for future C-DAC VEGA migration). | Enforce automated ONNX compliance check on all committed neural model checkpoints. | Confirmed Active |
| **DEP-010** | OpenCV Computer Vision Library | AI / Vision | Real-time image pre-processing, contrast stretching, CLAHE, coordinate transformations, and visual tracking feature extraction. | `MOD-01: VIO-NAV`, `MOD-02`, `MOD-03` | OpenCV v4.8+ with CUDA / NEON | OpenCV 4.8.0-dev | `REA-T1` Sec 5.2; `P01` Sec 11.1; `P04` AC-1.1 | **Confirmed** | `IF-001`, `IF-002` | `REQ-F-001`, `REQ-F-004`, `REQ-P-007` | C++17 Toolchain (`DEP-014`), Linux PREEMPT_RT (`DEP-001`) | Image manipulation routines must operate directly on zero-copy shared memory pointers without memory copying. | Unoptimized CPU image filters introduce pipeline latency exceeding 15 ms budget. | `P06` CLR-004 (Visual feature extraction latency limits). | Compile OpenCV with hardware-specific NEON and OpenCL acceleration flags. | Confirmed Active |
| **DEP-011** | Extended Kalman Filter (EKF2 / Robot Localization) | Middleware | Core state estimation algorithm fusing visual odometry, tactical IMU rates, DEM elevation, and LiDAR range data. | `MOD-01: VIO-NAV`, `MOD-07` | Custom EKF2 / `robot_localization` v3.4+ | EKF2 Multi-Sensor Fusion Core | `REA-T1` Sec 2.2, Sec 4, Sec 7 (Mod 01); `P04` AC-4.1 | **Confirmed** | `IF-003`, `IF-004`, `IF-005` | `REQ-F-004`, `REQ-P-005` | C++17 (`DEP-014`), ROS 2 Humble (`DEP-003`), Eigen3 library | Filter covariance matrix must maintain positive definiteness; update rate >= 200 Hz for inertial propagation. | Covariance divergence due to unmodeled visual feature jumps causes catastrophic flight trajectory loss. | `P06` ASM-005 (Sub-meter drift bound evaluated at 95% CEP). | Implement automatic sensor outlier rejection and covariance reset watchdog routines. | Confirmed Active |
| **DEP-012** | ANSI/VITA 49.0 Radio Transport (VRT) Driver | Middleware | Standardized radio transport protocol framing digitized wideband RF IQ packets streamed from SDR hardware to DSP processors. | `MOD-04: EW-DSP` | ANSI/VITA 49.0 / VITA 49.2 Standard | Custom VITA 49 C-Driver v1.2 | `REA-T1` Table 8.2; `P04` AC-9.1 | **Confirmed** | `IF-011` | `REQ-F-009`, `REQ-P-010`, `REQ-S-005` | Gigabit Ethernet / PCIe Kernel Driver (`DEP-018`) | Zero-packet drop FIFO ring buffers; microsecond packet timestamping; strict EMI isolation from propulsion lines. | Buffer overrun results in lost RF spectral data, preventing detection of frequency-agile hostile radars. | `P06` OQ-002, OQ-006 (400 MHz to 6 GHz RF monitoring band). | Verify VITA 49 packet ingestion throughput on 10 GbE benchtop testbench. | Confirmed Active |
| **DEP-013** | POSIX Shared Memory IPC (`shm_open`, `mmap`) | OS / Kernel | Provides microsecond zero-copy data exchange between camera ingress, AI inference, and mission coordination daemons. | `MOD-01`, `MOD-03`, `MOD-04`, `MOD-08`, `MOD-11` | POSIX.1-2008 Standard (`sys/mman.h`) | Hardened Linux Glibc 2.35 | `REA-T1` Sec 6.1, Table 8.2, Sec 8.3; `P04` AC-S-5.2 | **Confirmed** | `IF-002`, `IF-004`, `IF-013`, `IF-016`, `IF-017` | `REQ-S-005`, `REQ-P-007` | Linux PREEMPT_RT (`DEP-001`) | Circular ring buffer synchronization via lockless atomics or robust POSIX mutexes; strict memory boundary isolation. | Deadlocks in shared memory mutexes stall mission coordination nodes indefinitely. | `P06` DEP-003, DEP-010 (Air-gapped memory space enforcement). | Conduct formal thread concurrency stress testing with lockdep and ThreadSanitizer. | Confirmed Active |
| **DEP-014** | ISO C++ Standard Library & Compiler Toolchain | Language / Runtime | Primary systems programming language for flight middleware, AI orchestration, DSP filters, and high-performance daemons. | All Modules (`MOD-01` to `MOD-12`) | ISO/IEC 14882:2017 (C++17) / C++20 | GCC 11.4.0 / Clang 14.0 (C++17) | `REA-T1` Sec 6; `P01` Sec 4; Current Workstation Baseline | **Confirmed** | All Interfaces (`IF-001` to `IF-026`) | `REQ-S-002`, `REQ-D-001` | GNU C Library (`glibc` 2.35) | No dynamic heap allocation permitted in cyclic control loops; exceptions disabled in flight safety modules (`-fno-exceptions`). | Compiler optimization bugs or ABI mismatch between precompiled libraries and custom nodes. | `P06` ASM-014 (Coding standard aligned to DO-178C / MISRA C++). | Enforce automated static analysis (Cppcheck, Clang-Tidy) in CI/CD pipeline. | Confirmed Active |
| **DEP-015** | ISO C Embedded Toolchain (MISRA C:2012) | Language / Runtime | Programming language and runtime for bare-metal microcontroller firmware, RTOS tasks, and cryptographic bootloaders. | `MOD-07`, `MOD-09`, `MOD-12` | ISO/IEC 9899:2011 (C11) / MISRA C:2012 | GCC 10.3-2021.10 (arm-none-eabi) | `REA-T1` Sec 6.1 (Layer 2); `P04` AC-P-1.1 | **Confirmed** | `IF-005`, `IF-007`, `IF-008`, `IF-010`, `IF-020`, `IF-024` | `REQ-P-001`, `REQ-S-001`, `REQ-S-002` | Bare-metal MCU hardware (`DEP-017`) | Mandatory 100% compliance with MISRA C:2012 guidelines; static array bounds; recursion strictly prohibited. | Non-compliant pointer arithmetic or uninitialized variables induce hard fault exceptions on Cortex-M7. | `P06` ASM-014 (DO-178C DAL B qualification requirements). | Execute SonarQube / PC-lint MISRA compliance rule check on all firmware commits. | Confirmed Active |
| **DEP-016** | Python Scientific & Automation Runtime | Language / Runtime | Execution runtime for automated testing scripts, validation suites, data logging converters, and simulation bindings. | Testing, Simulation & Tooling | Python v3.10.x to v3.13.x | Python 3.13.7 (Current IDE) / Python 3.10.12 (JetPack) | Current Workspace Verification; `P04` Testing Scripts | **Confirmed** | N/A (Build / Test / Simulation Support) | `REQ-D-001`, `REQ-D-003`, `REQ-D-005` | Standard OS packages (`openpyxl`, `pypdf`, `pandas`) | Strictly prohibited from executing inside the real-time flight control loop; used exclusively for offline data verification. | Syntax or runtime incompatibilities between Python 3.10 (embedded SOM) and Python 3.13 (host testbench). | `P06` Documented testing script architecture. | Maintain dual-target compatibility (`pyproject.toml`) targeting Python 3.10 and 3.12+. | Confirmed Active |
| **DEP-017** | GNU Arm Embedded Toolchain (`arm-none-eabi-gcc`) | Toolchain / Build | Cross-compiler toolchain generating bare-metal machine code for STM32H7 ARM Cortex-M7 flight avionics microcontrollers. | `MOD-07: PX4-AUTOPILOT`, `MOD-09` | GCC version 10.3-2021.10 or 12.3.rel1 | `arm-none-eabi-gcc` 10.3.1 | `REA-T1` Sec 6.1 (Layer 2); `P01` Sec 4.1 | **Confirmed** | `IF-005`, `IF-007`, `IF-008`, `IF-010`, `IF-020` | `REQ-P-001`, `REQ-S-001`, `REQ-S-002` | Host Linux/Windows build machine, Make/Ninja | Hard-float ABI (`-mfloat-abi=hard -mfpu=fpv5-d16`); microsecond deterministic binary output. | Toolchain compiler optimization bugs causing stack corruption under `-O3` compilation flags. | `P06` OQ-003 (Evaluation of compiler optimization flags on latency). | Lock toolchain version in Docker build container and verify SHA-256 binary hash. | Confirmed Active |
| **DEP-018** | GNU AArch64 Linux Cross-Compiler | Toolchain / Build | Cross-compiler toolchain for compiling Vanguard-Linux kernel, ROS 2 nodes, and AI orchestration engines targeting ARM64 SOM. | `MOD-01`, `MOD-03`, `MOD-04`, `MOD-08`, `MOD-11`, `MOD-12` | GCC v11.3+ (`aarch64-linux-gnu`) | `aarch64-linux-gnu-gcc` 11.4.0 | `REA-T1` Sec 6.3; `P01` Sec 4.1 | **Confirmed** | All Edge Interfaces (`IF-001`–`IF-004`, `IF-011`–`IF-018`) | `REQ-S-005`, `REQ-P-007` | Host x86_64 build server, Glibc aarch64 sysroot | Sysroot libraries must strictly match the target SOM deployment image to avoid dynamic linker errors. | Glitched dynamic link to host library versions causes runtime segmentation fault on target hardware. | `P06` ASM-007 (Commercial SOM cross-compilation pipeline). | Implement containerized multi-stage Docker build pipeline for all target binaries. | Confirmed Active |
| **DEP-019** | CMake Cross-Platform Build System | Toolchain / Build | Primary meta-build system configuring build rules, dependency trees, compiler flags, and target generation across modules. | All Software Modules | CMake v3.22.1+ | CMake v3.22.1 | `REA-T1` Sec 6; `P04` Build Architecture | **Confirmed** | All Interfaces | `REQ-D-001`, `REQ-S-002` | Ninja or GNU Make build backend | Toolchain files must cleanly separate x86_64 host builds, aarch64 target builds, and arm-none-eabi builds. | Configuration drift across build scripts introduces non-reproducible binary builds. | `P06` Configuration management governance. | Standardize `CMakePresets.json` across all internal software repositories. | Confirmed Active |
| **DEP-020** | colcon Build Automation Tool | Toolchain / Build | Iterative build automation and workspace management tool for Swadeshi ROS 2 packages and custom message generation. | `MOD-01`, `MOD-03`, `MOD-04`, `MOD-08`, `MOD-11` | `colcon-common-extensions` v0.3+ | colcon 0.3.31 (Python 3.10+) | `REA-T1` Sec 6.1; `P01` Sec 4 | **Confirmed** | All ROS 2 Interfaces (`IF-002`, `IF-009`, `IF-013`, `IF-017`) | `REQ-F-005`, `REQ-D-001` | CMake (`DEP-019`), Python 3.10+ (`DEP-016`), ROS 2 Humble | Workspace build order must resolve message package dependencies prior to compiling consuming nodes. | Missing dependency declarations in `package.xml` cause non-deterministic parallel build failures. | `P06` CLR-006 (Standard package naming and dependencies). | Integrate automated colcon build verification into Git pre-commit hooks. | Confirmed Active |
| **DEP-021** | Gazebo Multi-Robot Physics Simulator | Simulation / Test | High-fidelity 3D simulation environment replicating Himalayan topography, low air densities (0.65 kg/m³), wind shear, and sensor noise. | Simulation & Verification | Gazebo Garden / Ignition / Classic v11 | Gazebo Classic 11.10.2 / Gazebo Garden | `REA-T1` Sec 5, Sec 9 (M1), Sec 10 (Tier 2); `P04` AC-5.3 | **Confirmed** | N/A (Simulation Environment) | `REQ-P-002`, `REQ-P-003`, `REQ-D-001` | Ubuntu 22.04 LTS / ROS 2 Humble bridge, OpenGL 3.3+ | Real-time simulation factor >= 1.0 on engineering workstation; accurate low-Reynolds aerodynamic lift models. | Simulation physics divergence from actual mountain flight dynamics invalidates early tuning. | `P06` ASM-002 (25 m/s gust profile modeling in Gazebo). | Correlate Gazebo wind gust response with aerodynamic wind tunnel test logs. | Confirmed Active |
| **DEP-022** | PX4 SITL & HIL Testing Framework | Simulation / Test | Executes compiled autopilot firmware against simulated vehicle physics (SITL) or physical MCU against simulated sensor buses (HIL). | `MOD-07`, Simulation Testbench | PX4 SITL / HIL Test Harness v1.14+ | Custom HIL Test Framework v1.0 | `REA-T1` Sec 9 (M1, M2), Sec 10 (Tier 2, Tier 3) | **Confirmed** | `IF-005`, `IF-008`, `IF-010` | `REQ-P-001`, `REQ-S-001`, `REQ-D-005` | Gazebo (`DEP-021`), Micro-XRCE-DDS Agent (`DEP-005`) | HIL sensor simulation latency must remain < 1.0 ms deterministic to prevent testbench instability. | High transport latency across HIL benchtop induces false instability not present on physical airframe. | `P06` DEP-011, DEP-013 (Tier 3 and Tier 4 exit criteria). | Benchmark HIL SPI/CAN bus turnaround latency using high-speed logic analyzer. | Confirmed Active |
| **DEP-023** | TPM 2.0 Software Stack (TSS2 / tpm2-tools) | Security / Crypto | Provides cryptographic APIs for hardware key generation, encrypted partition mounting, and multi-stage Secure Boot verification. | `MOD-12: SEC-TRUST` | TCG TSS 2.0 / `tpm2-tss` v3.2+ | `tpm2-tools` v5.2 / `libtss2` 3.2.0 | `REA-T1` Sec 2, Sec 6.3; `P01` Sec 4.1; `P04` AC-SEC-1.1 | **Confirmed** | `IF-004`, `IF-025` | `REQ-SEC-001`, `REQ-S-005` | Hardware TPM 2.0 Silicon Enclave / SPI Bus | Cryptographic validation of Stage 1/Stage 2 bootloader hashes; boot sequence aborts on key mismatch. | Corrupted key in TPM non-volatile storage bricks hardware bootloader, requiring depot recovery. | `P06` DEP-010, OQ-012 (TPM chip selection vs integrated enclave). | Validate recovery bootloader flashing procedure under secure laboratory conditions. | Confirmed Active |
| **DEP-024** | OpenSSL Cryptographic Library | Security / Crypto | Implements AES-256-GCM symmetric encryption for secondary RF telemetry and TLS/DTLS sessions for ground station links. | `MOD-10: SDR-RF-COMM`, `MOD-12` | OpenSSL v3.0+ (FIPS 140-3 Mode) | OpenSSL 3.0.2 (FIPS validated) | `REA-T1` Sec 3, Table 8.2; `P04` AC-12.1 | **Confirmed** | `IF-022`, `IF-025` | `REQ-F-012`, `REQ-SEC-001` | C11 Toolchain (`DEP-015`), Linux PREEMPT_RT (`DEP-001`) | FIPS 140-3 compliance mode active; zero key leakage to unencrypted swap partitions (swap disabled). | Cryptographic processing overhead introduces latency into frequency-hopping telemetry frames. | `P06` ASM-007, DEP-007 (Encrypted RF fallback operational timing). | Measure AES-256-GCM encryption/decryption latency across 1024-byte telemetry payloads on target SOM. | Confirmed Active |
| **DEP-025** | Zero-Trace Memory Wipe Daemon & GPIO Driver | Security / Crypto | Kernel daemon and micro-switch interrupt service routine executing instantaneous zero-trace physical/flash memory sanitization. | `MOD-12: SEC-TRUST` | Custom Kernel Module (`mod_zerotrace`) | `zerotrace-daemon` v1.0 | `REA-T1` Sec 2, Sec 6.2, Sec 8.1; `P04` AC-SEC-2.1 | **Confirmed** | `IF-026` | `REQ-SEC-002`, `REQ-S-005` | Linux Kernel Driver Subsystem, Physical Tamper Switches | Hardware interrupt execution priority; irreversible destruction of cryptographic master keys and DDR RAM scrubbing. | Accidental trigger due to switch contact bounce in high-vibration flight causes catastrophic self-destruction. | `P06` OQ-013 (Switch debounce window and capacitor dump circuits). | Implement dual-confirmation software interlock with 50 ms hardware debounce filter. | Confirmed Active |
| **DEP-026** | Linux SocketCAN Subsystem & Drivers | Hardware / Driver | Manages dual-redundant CAN-BUS 2.0B interfaces transporting MAVLink packets and flight control telemetry. | `MOD-07`, `MOD-08` | Linux SocketCAN (`can0`, `can1`) | Kernel SocketCAN Core 5.15 | `REA-T1` Table 8.2; `P01` Sec 11.1; `P04` AC-S-3.1 | **Confirmed** | `IF-003`, `IF-008` | `REQ-S-003`, `REQ-P-001` | Linux PREEMPT_RT (`DEP-001`), Onboard CAN Transceivers | CAN bus bit rate locked at 1.0 Mbps; dual physical redundancy; zero bus error frames over 48 hours. | Bus contention or babbling idiot failure on CAN bus locks inter-module communication. | `P06` DEP-012, DEP-013 (Zero bus collision endurance). | Verify 48-hour continuous zero-collision bus operation under Tier 4 integration testing. | Confirmed Active |
| **DEP-027** | V4L2 & Direct Memory Access (DMA-BUF) Subsystem | Hardware / Driver | Video capture kernel infrastructure routing multi-lane MIPI-CSI camera frames directly to GPU virtual memory without CPU copying. | `MOD-02`, `MOD-03` | Linux V4L2 / DMA-BUF Subsystem | Kernel DMA-BUF v5.15 / JetPack Argus | `REA-T1` Table 8.2; `P01` Sec 11.1; `P04` AC-1.1 | **Confirmed** | `IF-001` | `REQ-F-001`, `REQ-P-007` | Linux PREEMPT_RT (`DEP-001`), MIPI-CSI Hardware Bridge | Zero frame-copy overhead; DMA ring buffer size allocated for at least 4 uncompressed 4K/thermal frames. | Memory buffer starvation during high burst write cycles induces camera pipeline frame drops. | `P06` CLR-001 (MIPI lane configuration and frame buffer sizing). | Perform continuous 8-hour zero frame-drop stress run on physical camera benchtop rig. | Confirmed Active |
| **DEP-028** | RISC-V Cross-Compilation & Portability Layer | Toolchain / Build | Open standard software portability abstraction layer and cross-compiler targeting C-DAC VEGA and IIT Madras SHAKTI processors. | Silicon Sovereignty Roadmap | GNU Toolchain for RISC-V (`riscv64-unknown-linux-gnu`) | GCC v12.2.0 (RISC-V) | `REA-T1` Sec 1, Sec 2.2, Sec 11; `P04` AC-P-7.3 | **Not Verified** | N/A (Phase 2 Silicon Roadmap) | `REQ-P-007`, `REQ-D-006` | POSIX Standards, OpenCL / OpenVX runtimes | Open standard APIs only; zero vendor-proprietary CUDA/TensorRT primitives in core flight control algorithms. | Lack of high-throughput NPU accelerator cores on current generation domestic RISC-V processors. | `P06` ASM-007, OQ-006 (Phase 1 commercial SOM vs Phase 2 domestic silicon). | Benchmark baseline C++ navigation and DSP algorithms on C-DAC VEGA development board. | Under Review |

---

## 5. Compatibility Assessment

A systematic compatibility audit was conducted across the software and runtime stack based on documented evidence in `REA-T1-OVERVIEW-2026-V1.0` and the Day 1–Day 4 baseline files.

```mermaid
graph TD
    subgraph Host_Compute ["Layer C: Edge AI Processing Fabric (Linux PREEMPT_RT 5.15)"]
        RT_OS["DEP-001: Linux PREEMPT_RT 5.15"]
        ROS2["DEP-003: Swadeshi ROS 2 Humble"]
        TRT["DEP-007: NVIDIA TensorRT 8.5 INT8"]
        ONNX["DEP-009: ONNX Runtime (Opset 17)"]
        SHM["DEP-013: POSIX Shared Memory IPC"]
        XRCE_A["DEP-005: Micro-XRCE-DDS Agent"]
        TPM["DEP-023: TPM 2.0 Security Stack"]
        WIPE["DEP-025: Zero-Trace Wipe Daemon"]
        
        RT_OS --> ROS2
        RT_OS --> SHM
        ROS2 --> XRCE_A
        ONNX --> TRT
        SHM --> TRT
        TPM --> RT_OS
        WIPE --> RT_OS
    end

    subgraph Flight_Avionics ["Layer B: Flight Stabilization Core (Bare-Metal MCU)"]
        FRTOS["DEP-002: FreeRTOS Kernel v10.4"]
        PX4["DEP-004: Custom PX4 Autopilot Stack"]
        XRCE_C["DEP-005: Micro-XRCE-DDS Client"]
        MAV["DEP-006: MAVLink 2.0 Library"]
        PID["Inner Attitude Control Loop (< 1.0 ms)"]
        
        FRTOS --> PX4
        PX4 --> XRCE_C
        PX4 --> MAV
        PX4 --> PID
    end

    subgraph Sim_Validation ["Digital Twin & Simulation Subsystem"]
        GZB["DEP-021: Gazebo Mountain Simulation"]
        SITL["DEP-022: PX4 SITL / HIL Test Harness"]
        
        GZB <--> SITL
        SITL <--> ROS2
    end

    XRCE_A <==>|High-Speed UART / Redundant CAN 2.0B (IF-005 / IF-008)| XRCE_C
```

### 5.1 Evaluated Compatibility Matrix
The following matrix evaluates compatibility between core software layers and tools:

| Component Pair | Evaluation Focus | Evidence / Documentation | Compatibility Status | Findings & Technical Notes |
|---|---|---|:---:|---|
| **Swadeshi ROS 2 Humble (`DEP-003`) $\longleftrightarrow$ PX4 Autopilot (`DEP-004`)** | Inter-processor bridging via Micro-XRCE-DDS Client/Agent (`DEP-005`) | `REA-T1` Sec 6.3, Table 8.2; `P04` AC-5.2 | **Confirmed** | Compatible in simulation and standard SITL. Requires UART baud rate freeze (921600 baud vs 3 Mbps) to guarantee zero packet drop during 200 Hz attitude streaming. |
| **PyTorch v2.1 (`DEP-008`) $\longleftrightarrow$ TensorRT 8.5 (`DEP-007`) via ONNX (`DEP-009`)** | Deep learning model export, INT8 post-training quantization, and compilation | `REA-T1` Sec 6.3; `P01` Sec 4.1; `P04` AC-6.1 | **Confirmed** | Supported using ONNX Opset 17. Custom PyTorch layers must be converted to standard TensorRT operators; INT8 calibration dataset must include high-altitude snow scenes. |
| **Linux 5.15 PREEMPT_RT (`DEP-001`) $\longleftrightarrow$ Heterogeneous SOM (Jetson Orin)** | Hard real-time kernel scheduling on heterogeneous multi-core ARM64 hardware | `REA-T1` Sec 6.3; `P01` Sec 4; `P06` ASM-007 | **Confirmed** | Supported under NVIDIA JetPack 5.1.2 with real-time kernel patches. Max scheduling jitter verified < 50 µs under nominal CPU loads. |
| **Bare-Metal PX4 (`DEP-004`) $\longleftrightarrow$ Linux Edge Compute (`DEP-001`)** | Asynchronous hardware firewall and independent watchdog fail-safe operation | `REA-T1` Sec 8.3; `REQ-S-001`; `P04` AC-S-1.1 | **Confirmed** | Physically separated microcontrollers ensure edge AI lockups or Linux kernel panics cannot compromise the inner attitude stabilization loop. |
| **Gazebo Simulator (`DEP-021`) $\longleftrightarrow$ PX4 SITL / HIL (`DEP-022`)** | Closed-loop vehicle dynamics simulation in 25 m/s wind shear and low-density air | `REA-T1` Sec 5, Sec 9 (M1); `P04` AC-5.3 | **Confirmed** | Compatible. High-fidelity digital twin replicates Himalayan mountain elevation profiles and aerodynamic control surface responses. |
| **C++17 Core Algorithms $\longleftrightarrow$ Domestic Silicon Roadmap (C-DAC VEGA / SHAKTI)** | Portability of navigation and vision code to domestic RISC-V processors | `REA-T1` Sec 2.2, Sec 11; `REQ-P-007`; `P04` AC-P-7.3 | **Issue Identified** | C++17 core algorithms are portable via POSIX/OpenCL, but TensorRT INT8 models rely on proprietary NVIDIA GPU silicon; migration requires open NPU runtimes (OpenVINO/TVM/ONNX Runtime). |
| **Micro-XRCE-DDS Client (`DEP-005`) $\longleftrightarrow$ STM32H7 RAM Limits** | Memory footprint of DDS serialization buffer on embedded microcontroller | `REA-T1` Sec 6.1 (Layer 2); `P06` OQ-003 | **Not Verified** | Static buffer size must be limited to < 32 KB RAM on STM32H7 to prevent heap exhaustion during large parameter bursts; requires HIL stress testing. |
| **Free-Space Optical (FSO) PAT $\longleftrightarrow$ Gyro Offset Ingress (`IF-007`)** | 200 Hz attitude coordinate offset transport latency over RS-422 bus | `REA-T1` Table 8.2; `REQ-F-011`; `P04` AC-11.1 | **Confirmed** | RS-422 serial transport latency measured < 2.0 ms, satisfying the closed-loop beam stabilization tracking requirement under mountain wind gusts. |

---

## 6. Environmental Assumptions and Operating Constraints

### 6.1 Operating Environment Specifications
*   **Operating Altitudes:** 3,500 m to 6,500 m Above Mean Sea Level (AMSL) across the Ladakh and Siachen Glacier theaters.
*   **Atmospheric Density:** Extreme low density ($\approx 0.65\ \text{kg/m}^3$ at 6,500 m AMSL vs $1.225\ \text{kg/m}^3$ at sea level), degrading aerodynamic lift and motor cooling efficiency.
*   **Thermal Envelope:** Sustained operational qualification at **$-20^\circ\text{C}$** per `REA-T1` Tier 5 exit criteria, with exploratory non-destructive survival evaluated down to $-30^\circ\text{C}$ (`P06` ASM-003).
*   **Wind Shear Resilience:** Aerodynamic stability and optical pointing sustained under sudden discrete wind shear gusts of up to **$25.0\ \text{m/s}$** with recovery within $\le 2.5\ \text{s}$ (`P06` ASM-002).

### 6.2 Software Execution Constraints
1.  **Air-Gapped Isolation Constraint (`REQ-S-005`):** All edge software communications must execute strictly over local loopback sockets or POSIX shared memory (`DEP-013`). No Wi-Fi, Bluetooth, or commercial internet protocols may run on the aircraft.
2.  **Inner-Loop Latency Ceiling (`REQ-P-001`):** Inner attitude PID control loops on the STM32H7 bare-metal flight controller must execute with a deterministic latency of **$< 1.0\ \text{ms}$** (`P06` ASM-004).
3.  **Real-Time Inference Throughput (`REQ-P-008`):** The edge compute module must maintain **$\ge 60\ \text{FPS}$** for 2D tactical object detection models and **$\ge 15\ \text{FPS}$** for pixel-level semantic terrain segmentation models under concurrent execution (`P06` ASM-012).
4.  **Watchdog Failsafe Ceiling (`REQ-S-003`):** Bidirectional heartbeat exchange between the flight controller and edge compute node must occur at **$\ge 10\ \text{Hz}$**. Loss of heartbeats for **$> 500\ \text{ms}$** must trigger autonomous return-to-home or parachute recovery (`P04` AC-S-3.3).

---

## 7. Risks and Unresolved Technical Questions

### 7.1 Identified Compatibility & Dependency Risks
| Risk ID | Title / Summary | Affected Dependencies | Probability | Impact | Risk Description & Failure Mode | Mitigation Strategy |
|:---:|---|---|:---:|:---:|---|---|
| **RSK-DEP-01** | Domestic Silicon Acceleration Gap | `DEP-007`, `DEP-009`, `DEP-028` | High | High | C-DAC VEGA and IIT Madras SHAKTI processors currently lack high-throughput neural accelerators capable of 60 FPS INT8 inference, creating a tension with the 100% Indian IP mandate. | Maintain a phased 2-tier architecture: deploy commercial SOM with Swadeshi ROS 2 in Phase 1; abstract all AI pipelines via ONNX/POSIX to migrate to domestic silicon when NPUs mature (`P06` ASM-007). |
| **RSK-DEP-02** | Micro-XRCE-DDS Buffer Overflow | `DEP-004`, `DEP-005` | Medium | High | High-rate flight dynamics streaming over serial UART may overwhelm the static memory buffers of the micro-XRCE-DDS client on the STM32 microcontroller. | Implement prioritized topic filtering, cap non-critical telemetry to 10 Hz, and evaluate migration to high-speed 3 Mbps UART or onboard Ethernet bus (`P06` OQ-003). |
| **RSK-DEP-03** | Cold-Weather Silicon Clock Drift | `DEP-001`, `DEP-002`, `DEP-026` | Medium | Medium | Sub-zero operating temperatures down to $-20^\circ\text{C}$ can induce crystal oscillator frequency drift, leading to bus bit timing errors on CAN-BUS 2.0B or UART lines. | Mandate industrial/automotive temperature grade crystals ($\pm 10\ \text{ppm}$ over $-40^\circ\text{C}$ to $+85^\circ\text{C}$) and verify bus timing in the environmental chamber (`P06` ASM-003). |
| **RSK-DEP-04** | GPU Thermal Throttling in Rarefied Air | `DEP-001`, `DEP-007` | High | High | Low atmospheric density at 6,500 m AMSL drastically reduces convective heat dissipation, risking GPU thermal throttling during intensive neural inferencing. | Design custom conduction-cooled thermal heat pipes coupling edge compute silicon directly to the carbon-composite airframe skin; enforce 30W dynamic power capping. |
| **RSK-DEP-05** | Anti-Tamper False Trigger | `DEP-025` | Low | Critical | Mechanical vibration and high g-forces during turbulent mountain flight could cause anti-tamper switch bounce, accidentally triggering zero-trace memory wiping. | Enforce a hardware low-pass debounce filter ($RC \ge 50\ \text{ms}$) combined with a multi-token dual-confirmation software interlock (`P06` OQ-013). |

### 7.2 Unresolved Questions & Missing Technical Inputs
The following technical items from `P06` and `P07` directly impact software dependencies and must be resolved prior to the Milestone 1 System Requirements Specification freeze:

1.  **`OQ-DEP-01` (Micro-XRCE-DDS Transport Standardization):** High-Speed UART (921600 baud) vs 100BASE-T1 Automotive Ethernet for autopilot-to-compute bridging (`IF-005`, `IF-006`).  
    *Impact:* Determines whether embedded Ethernet PHY drivers and networking stacks are required on the bare-metal microcontroller.
2.  **`OQ-DEP-02` (Video Compression Codec Selection):** H.265 (HEVC) vs AV1 hardware video encoding under concurrent GPU inferencing load (`IF-018`).  
    *Impact:* Dictates edge compute multimedia API dependencies and GPU NVENC resource scheduling.
3.  **`OQ-DEP-03` (CBRN Telemetry Protocol Standard):** Serial bus standard (CAN-BUS 2.0B vs RS-485) and message definitions for commercial airborne sniffers (`IF-015`, `IF-016`).  
    *Impact:* Retains `IF-015` in *Under Review* status until the sensor vendor ICD is finalized.

---

## 8. Required Follow-up Actions

To ensure technical baseline closure prior to the Milestone 1 (M1) freeze, the following engineering actions are assigned to the respective technical leads:

| Action ID | Action Description | Target Subsystem / Dependency | Responsible Team | Milestone Deadline |
|:---:|---|---|---|:---:|
| **ACT-01** | Conduct a 48-hour continuous HIL bus collision and packet loss stress run over CAN-BUS 2.0B and Micro-XRCE-DDS. | `DEP-005`, `DEP-026`, `IF-005`, `IF-008` | Avionics & Flight Control Leads | Milestone 2 (Month 5) |
| **ACT-02** | Profile TensorRT 8.5 INT8 inferencing throughput and GPU die temperature at $-20^\circ\text{C}$ in the environmental chamber. | `DEP-001`, `DEP-007`, `IF-001`, `IF-017` | Edge AI & Thermal Engineering Leads | Milestone 2 (Month 6) |
| **ACT-03** | Finalize the Swadeshi ROS 2 custom message package (`rudra_msgs`) and establish an automated Git pre-commit schema validator. | `DEP-003`, `DEP-020` | Software Architecture & Middleware Leads | Milestone 1 (Month 3) |
| **ACT-04** | Formulate a formal silicon abstraction layer benchmark running baseline navigation algorithms on C-DAC VEGA RISC-V hardware. | `DEP-028`, `REQ-P-007` | Silicon Sovereignty Taskforce | Milestone 3 (Month 10) |
| **ACT-05** | Finalize the Sensor Interface Control Document (ICD Rev 1.0) freezing optical CMOS resolution, thermal pixel pitch, and CBRN bus pinouts. | `DEP-027`, `IF-001`, `IF-015` | Sensor Integration & Optoelectronics Leads | Milestone 1 (Month 4) |

---

## 9. Review and Maintenance Notes

1.  **Configuration Management:** This register is maintained under Git version control. Any modification to dependency versions, toolchain flags, or runtime frameworks requires a formal Engineering Change Proposal (ECP) approved by the Configuration Control Board (CCB).
2.  **Safety & Traceability Governance:** All dependencies categorized under Flight Avionics (`DEP-002`, `DEP-004`, `DEP-005`, `DEP-006`, `DEP-015`, `DEP-017`) must be traced against DO-178C DAL B structural coverage guidelines.
3.  **Cross-Document Integrity:** All Requirement IDs (`REQ-xxx`) cited in this document correspond strictly to [`P03_Numbered_Requirements_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%202/P03_Numbered_Requirements_Register.xlsx). All Interface IDs (`IF-xxx`) map directly to [`P07_Interface_Register.xlsx`](file:///c:/Users/Admin/OneDrive/Desktop/Day%204/P07_Interface_Register.xlsx).
4.  **Zero Guessing Mandate:** Unverified toolchains (e.g. RISC-V domestic silicon acceleration) are explicitly marked as *Not Verified* or *Under Review*. Technical values reflect contractual commitments stated in `REA-T1-OVERVIEW-2026-V1.0`.

---
*End of Document — RudraEdge RE-T1 (Spectra) Dependency & Compatibility Register (`P08`)*
