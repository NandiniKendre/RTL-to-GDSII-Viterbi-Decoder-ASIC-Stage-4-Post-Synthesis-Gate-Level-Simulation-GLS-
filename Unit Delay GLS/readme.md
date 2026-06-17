
# RTL-to-GDSII-Viterbi-Decoder-ASIC
# Stage 4.2: Unit Delay Gate-Level Simulation (GLS)

---

## Overview

This repository documents **Stage 4.2: Unit Delay Gate-Level Simulation (GLS)** of the RTL-to-GDSII ASIC implementation flow for a **K=7 Convolutional Encoder and Viterbi Decoder**.

Unit Delay Gate-Level Simulation is performed after Zero Delay GLS to introduce uniform propagation delays across all standard cells in the synthesized gate-level netlist. Unlike Zero Delay GLS, which focuses purely on functional verification, Unit Delay GLS incorporates basic timing behavior to expose delay-sensitive issues that may not be visible during functional simulation.

The objective of this stage is to validate the functionality of the synthesized design under timing-aware conditions, identify potential race conditions, glitches, simulation mismatches, and ensure robustness before proceeding to SDF-annotated verification and Physical Design stages.

---

## Objectives

- Import synthesized gate-level netlist.
- Load standard cell library simulation models.
- Apply unit delays to all standard cells.
- Verify functionality under timing-aware simulation.
- Identify race conditions and glitches.
- Validate decoder behavior with delayed signal propagation.
- Compare outputs against RTL and Zero Delay GLS results.
- Generate timing-aware waveforms and reports.
- Confirm readiness for SDF-Annotated GLS.

---

## Inputs

### Synthesized Gate-Level Netlist

```text
viterbi_decoder_synth.v
```

### Standard Cell Library Models

```text
stdcells.v
```

### Verification Testbench

```text
tb_viterbi_gls.v
```

### Timing Constraints

```text
design.sdc
```

### Unit Delay Configuration

```text
#1 Delay Applied to Standard Cells
```

---

## Unit Delay GLS Flow

### 1. Netlist Import

Imported the synthesized gate-level netlist generated during Logic Synthesis.

### 2. Library Loading

Loaded standard cell simulation models with uniform propagation delay behavior.

### 3. Unit Delay Application

Applied a fixed unit delay to all standard cells to emulate realistic signal propagation.

Characteristics:

- Uniform delay across all gates
- Simplified timing model
- Delay-aware verification
- Early timing behavior analysis

### 4. Testbench Execution

Executed the gate-level netlist using the verification environment developed during RTL verification.

Verification included:

- Decoder functionality
- State transition verification
- Survivor path verification
- Path metric calculations
- Output correctness validation

### 5. Waveform Analysis

Generated timing-aware simulation waveforms and analyzed signal transitions.

### 6. Output Comparison

Compared Unit Delay GLS outputs against:

- RTL Simulation Results
- Zero Delay GLS Results
- Expected Decoder Outputs

### 7. Verification Completion

Confirmed correct decoder operation under delayed signal propagation conditions.

---

## Verification Methodology

The synthesized gate-level netlist was simulated using a uniform delay model to emulate basic timing behavior.

The verification process focused on:

- Functional correctness
- Delay-sensitive behavior
- State machine stability
- Race condition detection
- Glitch analysis
- Output consistency

The decoder outputs were compared against expected RTL behavior to ensure functional equivalence despite the introduction of gate delays.

---

## Results

### Unit Delay Simulation

Unit Delay Gate-Level Simulation completed successfully.

### Functional Verification

The synthesized netlist maintained functional equivalence with the RTL design.

### Timing-Aware Verification

Verified:

- Correct signal propagation
- Stable state transitions
- Proper survivor path selection
- Accurate path metric updates
- Correct decoded output generation

### Glitch Analysis

No functional glitches impacting decoder operation were observed.

### Race Condition Analysis

No race conditions were detected during simulation.

---

## Verification Status

| Check | Status |
|---------|---------|
| Netlist Import | ✅ Pass |
| Library Loading | ✅ Pass |
| Unit Delay Application | ✅ Pass |
| Testbench Compilation | ✅ Pass |
| Unit Delay Simulation | ✅ Pass |
| Decoder Verification | ✅ Pass |
| Waveform Analysis | ✅ Pass |
| Functional Equivalence | ✅ Pass |

---

## Repository Structure

```text
Stage4.2_Unit_Delay_GLS/
│
├── Netlist/
│   └── viterbi_decoder_synth.v
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
│   └── run_unit_delay_gls.do
│
├── Reports/
│   ├── unit_delay_report.rpt
│   ├── waveform_analysis.rpt
│   ├── verification_summary.rpt
│   └── delay_impact_analysis.rpt
│
├── Waveforms/
│   └── unit_delay_gls_waveform.png
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

vsim tb_viterbi_gls

run -all
```

### Synopsys VCS

```bash
vcs \
stdcells.v \
viterbi_decoder_synth.v \
tb_viterbi_gls.v

./simv
```

### Cadence Xcelium

```bash
xrun \
stdcells.v \
viterbi_decoder_synth.v \
tb_viterbi_gls.v
```

---

## Deliverables

- Synthesized Gate-Level Netlist
- Standard Cell Library Models
- Unit Delay Simulation Environment
- Gate-Level Testbench
- Timing-Aware Waveforms
- Verification Reports
- Delay Impact Analysis Report
- Simulation Logs

---

## Delay Impact Analysis

The introduction of unit delays enables observation of:

- Signal arrival time differences
- Propagation delay effects
- Potential race conditions
- Glitch generation
- Delay-sensitive logic behavior

This stage provides an intermediate level of timing verification before performing full SDF-Annotated GLS.

---

## Key Learning Outcomes

- Unit Delay Gate-Level Verification
- Timing-Aware Functional Validation
- Race Condition Analysis
- Glitch Detection Techniques
- Gate-Level Debugging
- Delay Modeling Concepts
- ASIC Verification Flow Understanding

---

## ASIC Flow Progress

```text
RTL Behavioral Simulation & Functional Verification      ✅ Completed

Logic Synthesis                                          ✅ Completed

Post-Synthesis LEC                                       ✅ Completed

Zero Delay GLS                                           ✅ Completed

Unit Delay GLS                                           ✅ Completed

SDF Annotated GLS                                        ⏳ Next Stage

Floorplanning                                            ⏳ Pending

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

## Advantages of Unit Delay GLS

- Introduces timing awareness into verification
- Detects delay-sensitive issues
- Identifies potential race conditions
- Enables glitch analysis
- Improves confidence in synthesized netlist behavior
- Serves as a bridge between Zero Delay GLS and SDF GLS

---

## Limitations

Unit Delay GLS does not model:

- Actual cell propagation delays
- Process-specific timing characteristics
- Interconnect parasitics
- Setup and hold violations based on real timing data
- Post-layout timing effects

These effects will be verified in:

- Stage 4.3: SDF Annotated GLS

---

## Next Stage

### Stage 4.3: SDF Annotated Gate-Level Simulation

The synthesized Viterbi Decoder netlist will be simulated using back-annotated Standard Delay Format (SDF) timing information generated during synthesis. This stage will provide realistic timing verification using actual cell delays and timing paths.

---

## Status

### ✅ Stage 4.2 Completed Successfully

The synthesized Viterbi Decoder gate-level netlist has been successfully verified using Unit Delay Gate-Level Simulation. Functional correctness has been maintained under timing-aware conditions, and the design is ready for SDF-Annotated Gate-Level Simulation.

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
