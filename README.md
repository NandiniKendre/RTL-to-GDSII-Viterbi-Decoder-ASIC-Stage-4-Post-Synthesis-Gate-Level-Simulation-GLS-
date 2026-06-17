# RTL-to-GDSII-Viterbi-Decoder-ASIC
# Stage 4: Post-Synthesis Gate-Level Simulation (GLS)

---

## Overview

This repository documents **Stage 4: Post-Synthesis Gate-Level Simulation (GLS)** of the complete RTL-to-GDSII ASIC implementation flow for a **K=7 Convolutional Encoder and Viterbi Decoder**.

Post-Synthesis Gate-Level Simulation is performed after Logic Synthesis to verify that the synthesized gate-level netlist maintains functional equivalence with the original RTL design. This stage validates the correctness of the synthesized design using standard cell models and ensures that no functional discrepancies have been introduced during synthesis.

The objective of this stage is to establish confidence in the synthesized netlist before proceeding to Physical Design stages such as Floorplanning, Placement, Clock Tree Synthesis, and Routing.

---

## Objectives

- Import synthesized gate-level netlist.
- Load standard cell library simulation models.
- Apply verification environment developed during RTL simulation.
- Verify functional equivalence between RTL and synthesized netlist.
- Validate Viterbi Decoder functionality at gate level.
- Generate simulation waveforms and verification reports.
- Detect synthesis-induced functional issues.
- Confirm design readiness for Physical Design implementation.

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

### Gate-Level Testbench

```text
tb_viterbi_gls.v
```

### Timing Constraints

```text
design.sdc
```

### Simulation Scripts

```text
run_gls.do
```

---

## Gate-Level Simulation Flow

### 1. Netlist Import

Imported the synthesized gate-level netlist generated during the Logic Synthesis stage into the simulation environment.

### 2. Library Loading

Loaded standard cell simulation models and technology libraries required for accurate gate-level verification.

### 3. Testbench Execution

Executed the gate-level netlist using the same verification environment utilized during RTL functional verification.

Verification included:

- Decoder output validation
- State transition verification
- Survivor path verification
- Path metric computation checks
- Functional correctness analysis

### 4. Waveform Analysis

Generated simulation waveforms and compared gate-level behavior with RTL simulation results.

### 5. Functional Equivalence Validation

Verified that the synthesized netlist produced identical outputs to the RTL design for all applied test vectors.

### 6. Design Verification

Confirmed:

- Correct decoder functionality
- Proper state machine operation
- Accurate decoded output generation
- Successful simulation completion

---

## Verification Methodology

The synthesized gate-level netlist was simulated using standard cell models and compared against the expected RTL behavior.

The verification process focused on:

- Functional equivalence validation
- Decoder output correctness
- State transition integrity
- Survivor path selection accuracy
- Simulation stability

All verification scenarios passed successfully without functional mismatches.

---

## Results

### Gate-Level Simulation

Gate-Level Simulation completed successfully.

The synthesized gate-level netlist exhibited behavior equivalent to the RTL design across all verification scenarios.

### Functional Equivalence

RTL and gate-level outputs matched successfully.

### Waveform Verification

Waveform analysis confirmed:

- Correct decoder operation
- Valid state transitions
- Accurate path metric updates
- Proper survivor path selection
- Expected decoded outputs

### Simulation Status

Simulation executed successfully without runtime errors or functional mismatches.

---

## Verification Status

| Check | Status |
|---------|---------|
| Netlist Import | ✅ Pass |
| Library Loading | ✅ Pass |
| Testbench Execution | ✅ Pass |
| Functional Verification | ✅ Pass |
| RTL vs GLS Comparison | ✅ Pass |
| Waveform Analysis | ✅ Pass |
| Simulation Completion | ✅ Pass |

---

## Repository Structure

```text
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
│   └── run_gls.do
│
├── Reports/
│   ├── simulation_report.rpt
│   ├── verification_report.rpt
│   └── equivalence_summary.rpt
│
├── Screenshots/
│   ├── gls_waveform.png
│   └── output_comparison.png
│
├── Logs/
│
└── README.md
```

---

## Simulation Environment

### Supported Simulators

- Siemens QuestaSim
- ModelSim
- Synopsys VCS
- Cadence Xcelium

### Standard Cell Libraries

- Nangate Open Cell Library
- Sky130 Standard Cell Library
- Foundry-Specific Standard Cell Libraries

---

## Deliverables

- Synthesized Gate-Level Netlist
- Standard Cell Simulation Models
- Gate-Level Testbench
- Simulation Scripts
- Functional Verification Reports
- Equivalence Validation Reports
- Simulation Logs
- Gate-Level Waveforms
- Verification Screenshots

---

## Key Learning Outcomes

- Gate-Level Netlist Verification
- Standard Cell-Based Simulation
- Post-Synthesis Verification Methodology
- Functional Equivalence Validation
- ASIC Verification Flow Integration
- Industry-Standard RTL-to-GDSII Design Practices
- Debugging Gate-Level Simulation Issues
- Pre-Physical Design Verification Techniques

---

## ASIC Flow Progress

```text
RTL Behavioral Simulation & Functional Verification     ✅ Completed

Logic Synthesis                                         ✅ Completed

Post-Synthesis LEC                                      ✅ Completed

Post-Synthesis Gate-Level Simulation (GLS)             ✅ Completed

Floorplanning                                           ⏳ Next Stage

Placement                                               ⏳ Pending

Clock Tree Synthesis (CTS)                              ⏳ Pending

Routing                                                 ⏳ Pending

Static Timing Analysis (STA)                            ⏳ Pending

Post-Layout Gate-Level Simulation                       ⏳ Pending

DRC Verification                                        ⏳ Pending

LVS Verification                                        ⏳ Pending

GDSII Generation                                        ⏳ Pending
```

---

## Tools Used

### Front-End Design

- Verilog HDL
- Functional Verification Environment

### Logic Synthesis

- Cadence Genus
- Synopsys Design Compiler

### Gate-Level Verification

- Siemens QuestaSim / ModelSim
- Synopsys VCS
- Cadence Xcelium

### Constraints

- Synopsys Design Constraints (SDC)

---

## Applications

The Viterbi Decoder is widely used in:

- Wireless Communication Systems
- Satellite Communication
- Digital Broadcasting
- Error Correction Coding
- FPGA-Based Communication Systems
- ASIC Communication Processors
- High-Reliability Data Transmission Systems

---

## Next Stage

### Stage 5: Floorplanning

The verified gate-level netlist will be imported into Cadence Innovus for Floorplanning, where chip dimensions, core area, utilization, IO placement, and power planning strategy will be established.

---

## Status

### ✅ Stage 4 Completed Successfully

The synthesized Viterbi Decoder gate-level netlist has been successfully verified through Post-Synthesis Gate-Level Simulation (GLS). Functional equivalence between the RTL design and synthesized netlist has been confirmed, and the design is ready to proceed to the Floorplanning stage of the ASIC implementation flow.

---

## Author

**Nandini Kendre**
