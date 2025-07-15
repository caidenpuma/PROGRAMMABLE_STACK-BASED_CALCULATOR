# PROGRAMMABLE_STACK-BASED_CALCULATOR
Verilog-based programmable stack-based calculator (postfix calculator) designed as part of ENGN1640 Design of Computing Systems at Brown University.


## Project Overview

The calculator:
- Handles 8-bit integer arithmetic using a stack of 10 elements.
- Supports five instructions: `push value`, `add`, `sub`, `mult`, and `halt`.
- Detects arithmetic overflow for addition and subtraction.
- Displays the result on a 7-segment hex display.
- Includes ROM for instruction storage, an ALU for computation, and a testbench for simulation.

**Example Programs Implemented:**
- Example A: `8 - 5 * 3`
- Example B: `5 + ((1 + 2) * 4) – 3`

See `lab04_report.pdf` for full architecture, instruction encoding, RTL diagrams, and simulation results.

---

## Repository Contents

- `lab04.qar` — Quartus archive of the full project (all Verilog source code and constraints).
- `lab04_report.pdf` — Detailed project report with design description, simulation waveforms, logic utilization, and optimizations.
- `Assignment_04_Instructions.pdf` — Original assignment prompt for context.
- `LICENSE` — Add a license if you want to clarify usage (e.g., MIT License).

---

## How to Open

1. Download and unzip the repo or clone it.
2. Open Quartus Prime and use `Project -> Restore Archive` to open `lab04.qar`.
3. Run Analysis & Synthesis, compile, and simulate using the included testbench.
4. View waveform results in ModelSim or the Quartus waveform editor.

---

## Features Implemented

- Instruction Set: Custom 8-bit instruction format for push, arithmetic operations, and halt.
- ALU: Handles addition, subtraction (with overflow detection), multiplication.
- Display Logic: Converts stack output to BCD for 7-segment displays.
- Testbench: Verifies examples A & B and checks correctness via waveform simulation.

---

## Technologies Used

- Quartus Prime
- Verilog HDL
- ModelSim
- FPGA development board (tested on DE10-Lite)
