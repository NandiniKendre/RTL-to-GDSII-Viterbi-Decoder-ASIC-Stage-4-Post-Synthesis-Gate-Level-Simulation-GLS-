# RTL-to-GDSII-Viterbi-Decoder-ASIC
# Stage 4.3: SDF Annotated Gate-Level Simulation (GLS)

---

## Overview

This repository documents **Stage 4.3: SDF Annotated Gate-Level Simulation (GLS)** of the RTL-to-GDSII ASIC implementation flow for a **K=7 Convolutional Encoder and Viterbi Decoder**.

SDF Annotated Gate-Level Simulation is the most advanced form of post-synthesis verification and serves as the final verification step before entering Physical Design. In this stage, actual timing information generated during Logic Synthesis is back-annotated onto the synthesized gate-level netlist using a **Standard Delay Format (SDF)** file.

Unlike Zero Delay GLS and Unit Delay GLS, SDF GLS models realistic propagation delays for every standard cell and timing path within the design. This enables verification of both functional correctness and timing behavior under realistic operating conditions.

The objective of this stage is to validate that the synthesized Viterbi Decoder operates correctly with actual timing delays and satisfies timing requirements prior to Floorplanning and Physical Design implementation.

---

## Objectives

- Import synthesized gate-level netlist.
- Load standard cell simulation models.
- Back-annotate synthesis-generated SDF timing data.
- Perform timing-aware gate-level simulation.
- Verify functionality under realistic propagation delays.
- Detect setup and hold timing violations.
- Validate decoder behavior using actual cell delays.
- Analyze timing paths and signal propagation.
- Generate timing-aware waveforms and reports.
- Confirm design readiness for Physical Design.

---

## Inputs

### Synthesized Gate-Level Netlist

```text
viterbi_decoder_synth.v
```

### Standard Delay Format (SDF)

```text
viterbi_decoder.sdf
```

### Standard Cell Library Models

```text
stdcells.v
```

### Gate-Level Testbench

```text
tb_viterbi_gls.v
```

### Timing Constraints

```text
design.sdc
```

---

## SDF Annotated GLS Flow

### 1. Netlist Import

Imported the synthesized gate-level netlist generated during Logic Synthesis.

### 2. Library Loading

Loaded standard cell simulation models required for timing-aware gate-level verification.

### 3. SDF Back Annotation

Applied synthesis-generated Standard Delay Format (SDF) timing information to the gate-level netlist.

The SDF file contains:

- Cell propagation delays
- Timing arc information
- Path delays
- Interconnect timing data
- Setup timing information
- Hold timing information

### 4. Testbench Execution

Executed the synthesized netlist using the gate-level verification environment.

Verification included:

- Decoder output validation
- State transition verification
- Survivor path verification
- Path metric calculations
- Functional correctness analysis

### 5. Timing Verification

Analyzed:

- Signal propagation delays
- Critical timing paths
- Setup timing requirements
- Hold timing requirements
- Clock-to-output delays

### 6. Waveform Analysis

Generated and analyzed timing-accurate simulation waveforms.

### 7. Verification Completion

Confirmed correct decoder functionality under realistic timing conditions.

---

## Verification Methodology

The synthesized Viterbi Decoder netlist was simulated with SDF back annotation to model actual timing behavior derived from synthesis.

Verification focused on:

- Functional equivalence
- Timing-aware operation
- Setup violation detection
- Hold violation detection
- Critical path validation
- Decoder correctness
- State machine integrity

The gate-level outputs were compared against expected RTL results while accounting for realistic propagation delays.

---

## Results

### SDF Annotated Simulation

SDF Annotated Gate-Level Simulation completed successfully.

### Functional Verification

The synthesized gate-level netlist maintained functional equivalence with the RTL design.

### Timing Verification

Verified:

- Correct propagation of timing information
- Stable state transitions
- Accurate survivor path selection
- Proper path metric updates
- Correct decoded output generation

### Setup/Hold Analysis

Timing checks were performed using SDF timing data.

### Waveform Verification

Timing-aware waveforms confirmed proper decoder operation under realistic delay conditions.

---

## Timing Analysis Summary

| Timing Check | Status |
|-------------|---------|
| Setup Analysis | ✅ Pass |
| Hold Analysis | ✅ Pass |
| Clock Propagation | ✅ Pass |
| Signal Propagation | ✅ Pass |
| Timing Consistency | ✅ Pass |

---

## Verification Status

| Check | Status |
|---------|---------|
| Netlist Import | ✅ Pass |
| Library Loading | ✅ Pass |
| SDF Back Annotation | ✅ Pass |
| Testbench Compilation | ✅ Pass |
| SDF Simulation | ✅ Pass |
| Functional Verification | ✅ Pass |
| Setup Timing Verification | ✅ Pass |
| Hold Timing Verification | ✅ Pass |
| Waveform Analysis | ✅ Pass |
| Functional Equivalence | ✅ Pass |

---

## Repository Structure

```text
Stage4.3_SDF_Annotated_GLS/
│
├── Netlist/
│   └── viterbi_decoder_synth.v
│
├── SDF/
│   └── viterbi_decoder.sdf
│
├── Libraries/
│   └── stdcells.v
│
├── Constraints/
│   └── design.sdc
│
├── Testbench/
│   └── tb_viterbi_gls.v
│
├── Scripts/
│   └── run_sdf_gls.do
│
├── Reports/
│   ├── sdf_simulation_report.rpt
│   ├── timing_report.rpt
│   ├── setup_hold_report.rpt
│   ├── verification_summary.rpt
│   └── critical_path_report.rpt
│
├── Waveforms/
│   ├── sdf_gls_waveform.png
│   └── timing_analysis_waveform.png
│
├── Logs/
│
└── README.md
```

---

## Simulation Commands

### ModelSim / QuestaSim

```tcl
vlog stdcells.v
vlog viterbi_decoder_synth.v
vlog tb_viterbi_gls.v

vsim -sdfmax /tb_viterbi_gls/DUT=viterbi_decoder.sdf tb_viterbi_gls

run -all
```

### Synopsys VCS

```bash
vcs \
stdcells.v \
viterbi_decoder_synth.v \
tb_viterbi_gls.v

./simv +sdf_verbose
```

### Cadence Xcelium

```bash
xrun \
stdcells.v \
viterbi_decoder_synth.v \
tb_viterbi_gls.v \
-sdf_cmd_file sdf.cmd
```

---

## Deliverables

- Synthesized Gate-Level Netlist
- Standard Delay Format (SDF) File
- Standard Cell Library Models
- Gate-Level Testbench
- Timing-Aware Simulation Scripts
- SDF Verification Reports
- Setup/Hold Timing Reports
- Critical Path Analysis Reports
- Simulation Logs
- Timing-Aware Waveforms

---

## Timing Checks Performed

### Setup Timing Verification

Validated that all sequential elements receive data before the required setup window.

### Hold Timing Verification

Validated that data remains stable after the active clock edge.

### Clock Path Verification

Verified clock propagation through synthesized timing paths.

### Critical Path Analysis

Analyzed longest timing paths affecting overall design performance.

### Signal Integrity Verification

Observed timing behavior across all major decoder datapaths.

---

## Key Learning Outcomes

- SDF Back Annotation
- Timing-Aware Gate-Level Simulation
- Setup and Hold Verification
- Critical Path Analysis
- ASIC Timing Verification Methodology
- Standard Cell Timing Modeling
- Functional and Timing Correlation
- Industry RTL-to-GDSII Verification Flow

---

## ASIC Flow Progress

```text
RTL Behavioral Simulation & Functional Verification      ✅ Completed

Logic Synthesis                                          ✅ Completed

Post-Synthesis LEC                                       ✅ Completed

Zero Delay GLS                                           ✅ Completed

Unit Delay GLS                                           ✅ Completed

SDF Annotated GLS                                        ✅ Completed

Floorplanning                                            ⏳ Next Stage

Placement                                                ⏳ Pending

Clock Tree Synthesis (CTS)                               ⏳ Pending

Routing                                                  ⏳ Pending

Static Timing Analysis (STA)                             ⏳ Pending

Post-Layout GLS                                          ⏳ Pending

DRC Verification                                         ⏳ Pending

LVS Verification                                         ⏳ Pending

GDSII Generation                                         ⏳ Pending
```

---

## Advantages of SDF Annotated GLS

- Most realistic pre-layout timing verification
- Models actual synthesis-generated delays
- Detects setup and hold violations
- Verifies critical timing paths
- Improves confidence before Physical Design
- Enables accurate timing-aware debugging
- Industry-standard ASIC verification methodology

---

## Importance in ASIC Design Flow

SDF Annotated GLS is a critical verification milestone because it bridges the gap between functional verification and physical implementation.

By incorporating realistic timing information into simulation, designers can identify timing-related issues early, reducing risk during Floorplanning, Placement, Clock Tree Synthesis, Routing, and Signoff stages.

---

## Next Stage

### Stage 5: Floorplanning

The verified synthesized Viterbi Decoder netlist will be imported into Cadence Innovus for Floorplanning. This stage will define die size, core dimensions, utilization targets, IO placement strategy, and prepare the design for Placement and Physical Optimization.

---

## Status

### ✅ Stage 4.3 Completed Successfully

The synthesized Viterbi Decoder gate-level netlist has been successfully verified using SDF Annotated Gate-Level Simulation. Functional correctness and timing behavior have been validated using synthesis-generated delay information, and the design is ready to proceed to the Floorplanning stage of the ASIC implementation flow.

---

## Author

**Nandini Kendre**

Senior Research Fellow – C2S Program (MeitY)  
FPGA / ASIC Design Engineer

### Domains

- Digital VLSI Design
- ASIC Physical Design
- FPGA Prototyping
- Communication Systems
- Hardware Acceleration
- RTL-to-GDSII Implementation Flow

---

## License

This project is intended for educational, research, and ASIC design learning purposes.
