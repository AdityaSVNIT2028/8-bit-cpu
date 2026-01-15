# 8-bit CPU

This repository contains an educational 8-bit CPU design (RTL, microarchitecture notes, and supporting materials). The CPU implements a simple instruction set architecture (ISA) and is built bottom-up from ISA to microarchitecture and then to registers, counters, and combinational/sequential circuits.

## Design flow

![Design flow](images/design_flow.png)

The design follows a classic top-down flow:
- Instruction Set Architecture (ISA): Define the instruction formats, supported operations, register file layout, addressing modes, and the programmer-visible behavior.
- Microarchitecture: Map the ISA to datapath components (ALU, registers, multiplexers) and control (finite-state machine or microcoded control).
- Registers & Counters: Implement the register file, program counter, instruction register, and any other state elements required by the microarchitecture.
- Combinational & Sequential Circuits: Implement the ALU, shifters, decoders, and the sequential logic that ties the components together.

## Instruction cycle

![Instruction cycle](images/instruction_cycle.png)

The CPU executes instructions using the classic Fetch–Decode–Execute cycle:

1. Fetch
   - Read the instruction from memory at the address held by the Program Counter (PC).
   - Increment the PC (or update it according to control logic for jumps/branches).

2. Decode
   - Decode the fetched instruction to determine the operation, source/destination registers, immediate fields, and addressing mode.
   - Generate control signals for the datapath (select ALU operation, select register file read/write, memory access signals, etc.).

3. Execute
   - Perform the operation on the datapath: ALU computation, memory read/write, register writeback, or PC update for control flow instructions.
   - Update status flags if any (zero, carry, etc.).