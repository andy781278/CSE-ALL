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
- Branches
	- Some branches needs its registers by ID, so if it's dependent on previous instructions to finish executing/write backing, we stall until that information is available
- Code Scheduling to avoid stalls
	- You can rearrange some instructions without changing the program, but will give the instructions more room so that data arrives before it's needed.

### Control Hazard
- Deciding on control actions like branch or jump depending on previous instruction
- Branch determines flow of control
	- Fetching next instruction depends on branch outcome
	- Pipeline can't always fetch the correct instruction
- Use Stall
	- You can stall until after you determined the outcome of the branch to fetch the next instruction 
#### Branch Prediction
- Branch Dependency
	- A safe instruction is one that produces the correct outcome regardless of whether or not the branch is taken.
	- If an instruction after the branch is dependent on the outcome of the branch, it is not safe, 
- Branch-Not-Taken
	- put the instructions after the branch as if there was no branch, assuming it does not go through.
	- If it does, flush out all the instructions, which means just making the instructions no-ops, and make them do nothing, and just let them pass.
	- This way, in case the branch is not taken, we can forgo the stall, but if the branch is taken, we do pretty much stall that whole time, but it is better than having stalls the whole way.
- There are better ones, like Static Branch Prediction and Dynamic Branch Prediction, but those aren't really specific

### Stalling
Force control values in ID/EX register to be 0, those control values include everything that it passes to, so it is everything, but these specifically is enough:
- reg_write
- mem_write
- pc_select

### Forwarding
When you recently calculated the result to write back into a register $r in WB stage that you need in previous active stages, you can wire it back directly to them instead of having them retrieve them 