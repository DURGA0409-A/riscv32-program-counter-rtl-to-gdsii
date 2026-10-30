# riscv32-program-counter-rtl-to-gdsii
32-bit RISC-V Program Counter design using Verilog HDL, Cadence NCLaunch, Genus and Innovus with 180 nm CMOS technology.
# 32-bit RISC-V Program Counter – RTL to GDSII Implementation

## Project Overview

This project focuses on the RTL design, functional verification, logic synthesis, and physical implementation of a **32-bit RISC-V Program Counter (PC)** using Verilog HDL and Cadence EDA tools.

The design is implemented using **180 nm CMOS technology**, following the RTL-to-GDSII design flow.

The Program Counter is an essential component of a processor. It stores the address of the current instruction and determines the address of the next instruction during sequential execution, stalls, and branch or jump operations.

## Design Specifications

| Parameter | Description |
|---|---|
| Design | 32-bit RISC-V Program Counter |
| Architecture | RISC-V |
| Data width | 32 bits |
| Technology | 180 nm CMOS |
| HDL | Verilog |
| Clock | Positive-edge triggered |
| Reset | Synchronous, active-high |
| Simulation | Cadence NCLaunch |
| Synthesis | Cadence Genus |
| Physical Design | Cadence Innovus |
| Final Output | GDSII layout |

## Functional Features

The Program Counter supports the following operations:

1. **Reset:** Initializes the PC to `32'h00000000`.
2. **Sequential Execution:** Increments the PC by 4 for the next 32-bit instruction.
3. **Stall Control:** Holds the current PC value during a pipeline stall.
4. **Branch/Jump Selection:** Loads the target address when branch or jump control is enabled.

### PC Operation

| Control Condition | PC Operation |
|---|---|
| Reset = 1 | PC = 0 |
| Stall = 1 | PC holds its value |
| PC_src = 1 | PC = PC_target |
| Otherwise | PC = PC + 4 |

**Control priority:** Reset > Stall > Branch/Jump > Sequential Increment.

## RTL Architecture

The project contains three Verilog modules:

- `program_counter`: Implements the 32-bit Program Counter functionality.
- `riscv32_top`: Top-level module that instantiates the Program Counter.
- `tb_riscv32`: Testbench for functional verification.

The testbench is used only for simulation and is excluded from synthesis.

## RTL-to-GDSII Implementation Flow

```text
Verilog RTL Design
        |
        v
Functional Verification
   Cadence NCLaunch
        |
        v
Logic Synthesis
    Cadence Genus
        |
        v
Technology Mapping
        |
        v
Physical Design
   Cadence Innovus
        |
        v
Floorplanning
        |
        v
Placement
        |
        v
Clock Tree Synthesis
        |
        v
Routing
        |
        v
GDSII Layout Generation
```

## Tools and Technologies

- **Verilog HDL:** RTL coding and hardware description.
- **Cadence NCLaunch:** Functional simulation and verification.
- **Cadence Genus:** Logic synthesis and technology mapping.
- **Cadence Innovus:** Physical design and layout implementation.
- **180 nm CMOS:** Target semiconductor technology.

## Project Directory Structure

```text
RISCV32_Processor/
│
├── riscv32_pc_test.v
│
├── riscv32_pc_genus.tcl
│
├── riscv32_pc.sdc
│
├── run_pc_sim.sh
│
├── reports/
│   ├── area.rpt
│   ├── timing.rpt
│   └── power.rpt
│
├── netlist/
│   ├── riscv32_pc_netlist.v
│   └── riscv32_pc_netlist.sdc
│
└── layout/
    └── riscv32_pc.gds
```

*The directory structure shows the intended organization. Include only the files and reports actually generated in your repository.*

## Timing Constraints

The initial timing constraint uses a 10 ns clock period, corresponding to a 100 MHz target clock.

The SDC file defines:

- Clock period
- Input delays
- Output delays
- Input transition
- Output load

These are initial design constraints and should be reviewed against the actual implementation requirements.

## Verification

The testbench verifies the following operations:

- Synchronous reset
- Sequential PC increment
- Pipeline stall
- Branch target address selection
- Sequential execution after branch selection

### Expected Simulation Output

```text
RISC-V PROGRAM COUNTER TEST

Reset PC       = 00000000
Sequential PC  = 00000004
Sequential PC  = 00000008
Stalled PC     = 00000008
Branch PC      = 00000040
Next PC        = 00000044

TEST COMPLETED
```

## Implementation Status

- [x] Program Counter RTL design
- [x] Top-level module integration
- [x] Functional testbench development
- [x] Functional simulation
- [x] Genus synthesis
- [x] Innovus physical implementation
- [x] GDSII generation
- [ ] Integration with instruction memory
- [ ] Register file implementation
- [ ] ALU integration
- [ ] Pipeline register development
- [ ] Hazard detection and forwarding
- [ ] Complete five-stage RV32I processor integration

## Learning Outcomes

Through this implementation, I gained practical experience in:

- Understanding the RISC-V processor architecture.
- Designing sequential digital circuits using Verilog HDL.
- Developing and executing functional testbenches.
- Performing RTL synthesis and technology mapping.
- Understanding timing constraints using SDC.
- Exploring physical design using Cadence Innovus.
- Generating the final GDSII layout using 180 nm CMOS technology.

## Future Scope

The next phase of this project is to extend the Program Counter into a complete five-stage pipelined 32-bit RV32I processor consisting of:

1. Instruction Fetch (IF)
2. Instruction Decode (ID)
3. Execute (EX)
4. Memory Access (MEM)
5. Write Back (WB)

Additional modules will include the instruction memory, register file, ALU, immediate generator, control unit, hazard detection unit, forwarding unit, and pipeline registers.

## Author

**Durga Devi A**  
Assistant Professor, Department of Electronics and Communication Engineering  
Saveetha Engineering College

## Acknowledgement

This project represents a hands-on learning experience in digital VLSI design, processor architecture, and the Cadence RTL-to-GDSII implementation flow.

<img width="1359" height="688" alt="Screenshot 2026-10-30 083422" src="https://github.com/user-attachments/assets/c0944936-1f1c-4ff3-9218-d1964d3d13b9" />
<img width="1365" height="488" alt="Screenshot 2026-10-30 083434" src="https://github.com/user-attachments/assets/e154d522-5d58-4074-8bc6-58df63674dbd" />
<img width="1120" height="581" alt="Screenshot 2026-10-30 102122" src="https://github.com/user-attachments/assets/f68dddbf-4ceb-4f17-a18c-dda1cbcc3188" />
<img width="1365" height="691" alt="Screenshot 2026-10-30 104127" src="https://github.com/user-attachments/assets/29e4ab42-da56-4482-ba1f-0b22b7f768e7" />



