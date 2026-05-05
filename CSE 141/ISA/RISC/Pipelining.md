We divide the ISA into 5 stages, each taking 1 cycle to reach the next

Instruction Fetch -> Instruction Decode -> Execute -> Memory -> Write Back
IF -> ID -> EX -> MEM -> WB

![[Screen Shot 2026-05-04 at 5.24.43 PM.png]]

Pipelining means to load a new instruction per cycle, since the instruction goes through this 5-stage process, each stage can contain a separate instruction. As long as it doesn't overlap, it should be fine, and you get to process at 5 times the speed as before.

But pipelining comes with hazards.

![[Hazard]]