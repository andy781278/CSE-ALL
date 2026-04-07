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