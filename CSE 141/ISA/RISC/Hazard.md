A Hazard is a situation that prevents starting the next instruction in the next cycle

### Structure Hazard
- A required resource is busy
- Conflict for use of a resource
- A single component can only accommodate a single instruction at once, so if multiple instructions require it at the same time, then it wouldn't work
#### Example
For a MIPS pipeline with shared data/instruction memory, two instructions would need information from the same memory, load/store from data memory requires access, while loading from instruction memory needs constant access. Therefore we need to stall for that cycle, causing a bubble. This is why they're separate.

### Data Hazard
- Need to wait for previous instruction to complete its data read/write
#### Example
- r-type 1 and r-type 2
	- r type 2 needs a register that's the result of r type 1, which hasn't been updated yet by the time r-type 2 reaches the stage where it needs the data
	- Can be forwarded
- Load-Use
	- Sometimes you literally can't forward because the data literally does not exist yet, because it has to be loaded out of the memory, for example, so you stall and wait for the data to exist, then you can forward it.
	- Must be stalled
- Code Scheduling to avoid stalls
	- You can rearrange some instructions without changing the program, but will give the instructions more room so that data arrives before it's needed.

### Control Hazard
- Deciding on control actions like branch or jump depending on previous instruction
- Branch determines flow of control
	- Fetching next instruction depends on branch outcome
	- Pipeline can't always fetch the correct instruction
- Use Branch Prediction
	- put the instructions after the branch as if there was no branch, assuming it does not go through. If it does, flush out all the instructions, which means just making the instructions no-ops, and make them do nothing, and just let them pass.

### Forwarding
When you recently calculated the result to write back into a register $r in WB stage that you need in previous active stages, you can wire it back directly to them instead of having them retrieve them 