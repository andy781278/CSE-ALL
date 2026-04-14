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

### Key Problems
- Operations
	- There can't be complex operations, as that will make the compiler freak out, and we need the compiler to be reliable for the programmers to trust it and safely write and debug code
- Operands
- Instruction Format
	- we need to divide the instruction space into chunks
		- Opcode
		- fetch appropriate amount and specific Registers
		- leftover for whatever depending on the Opcode
	- Instruction Length
		- Fixed-length (MIPS)
			- 32 bits long only
				- not a lot, makes things hard
			- easy fetch and decode
			- simplify pipelining and parallelism
		- Variable-length (Intel)
			- multi-step fetch and decode
			- more flexible and compact instruction set
		- Hybrid (ARM)
			- middle ground

### MIPS Instruction Format (fixed)
![[Screen Shot 2026-04-08 at 5.25.18 PM.png]]
- How to load memory?
	- We put some literals into a register using immediate, and use that value as the address for the memory.
- Why specifically this way?
	- Historically, we did other stuff too, with varying results
![[Screen Shot 2026-04-08 at 6.01.31 PM.png]]

#### How to Implement MIPS
Every instruction specified in MIPS has a literal RTL translation. 
They all have this structure:
```
IR <- Mem[PC]
NPC <- PC + 4
...
PC <- NPC
```
First, Instruction Register takes in the next instruction from Instruction Memory.
We make a variable NPC, which is the next PC's address, which is this one add 4 bytes. 4 bytes is 32 bits, which is how long an instruction is. By adding 32 bits, we skip over that instruction, and reach the next one. Then, we put that back into PC, so they can read the next instruction on the next cycle.

