Allows Abstractions to convert hardware architecture into software.
It is the agreed-upon interface between all the software that runs on the machine and the hardware that executes it
![[Screen Shot 2026-04-06 at 5.14.11 PM.png]]

Part of the architecture available to the programmers:
- Available Instructions
- Registers
- Instruction formats
- storage access, addressing modes
- exceptional conditions

### Instruction Execution Cycle
![[Screen Shot 2026-04-06 at 5.39.17 PM.png]]
We can speed up things through parallelism

### Parallelism
#### Superscalar Processor
Execute multiple times per cycle

#### Pipelining
each cycle does all of the steps of the cycle, each instruction is at a different yet unique step and no overlap yet you can use all of the cycle.
```
Cycle:  1    2    3    4    5    6    7
I1:     IF   ID   EX   MEM  WB
I2:          IF   ID   EX   MEM  WB
I3:               IF   ID   EX   MEM  WB
```

### Key Problems
- Operations
	- How many?
	- There can't be complex operations, as that will make the compiler freak out, and we need the compiler to be reliable for the programmers to trust it and safely write and debug code
- Operands
	- How many?
- Instruction Format
	- How define?
	- we need to divide the instruction space into chunks
		- Opcode
		- fetch appropriate amount and specific Registers
		- leftover for whatever depending on the Opcode

### Types of ISA
- Based on instruction length, we have two categories of ISAs: RISC and CISC
	- Reduced Instruction Set Computer RISC
	- Complex Instruction Set Computer CISC

#### RISC
We have different types of ISAs based on Instruction Length, each has some number of instruction formats, which categorizes the actions the processor can do
##### MIPS
- Fixed-length
	- 32 bits long only
- easy fetch and decode
- simplify pipelining and parallelism
##### RISC-V
- Variable-length 
	- Can be 16 bits or 32 bits
- multi-step fetch and decode
- more flexible and compact instruction set
##### ARM
- Hybrid
- middle ground

### RTL
Every instruction specified in RISC has a literal RTL translation. 
They all have this structure:
```
IR <- Mem[PC]
NPC <- PC + 4
...
PC <- NPC
```
First, Instruction Register takes in the next instruction from Instruction Memory.
We make a variable NPC, which is the next PC's address, which is this one add 4 bytes. 4 bytes is 32 bits, which is how long an instruction is. By adding 32 bits, we skip over that instruction, and reach the next one. Then, we put that back into PC, so they can read the next instruction on the next cycle.