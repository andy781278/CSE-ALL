Registers are a series of DFFs connected by input and goes to output, all  connected to a Clk, and all the same type (rising edge or falling edge). These data al load in at once, making this a parallel register.

![[Pasted image 20260216152439.png]]

### Shift Register
A kind of register that loads in bits one at a time per cycle, each register takes in the one before it, and gives the one it has to the one after it. The first register takes in input and propagates.
![[Pasted image 20260216152829.png]]

Usage:
- Random number generator
	- Generates Quasi-Random patterns using seeds
- Password Detector
	- AND normal and NOT signals so only specific bit patterns is allowed


### Universal Shift Register
Has the ability to shift left, right, reset, keep, or load parallel depending on the input bits.
![[Pasted image 20260216153209.png]]

### LFSR (Linear Feedback Shift Register)
Linear - simple linear gates
Feedback - looping through itself
Shift - shifting the registers
Register - it's a register
![[Pasted image 20260216153606.png]]