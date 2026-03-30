Next step: Add a D latch. D latch is a representation of S and R in a single input. If D=0, Q=0. If D=1, Q=1. This is only the case when the clock is high, which is when changing S or R is not happening. When clock is low, change is allowed to happen, since C won't let it through anyways.

![[Pasted image 20260215213031.png]]

11 still happens because of the NOT gate for D which has a delay of 2CR. That delay makes it so that when D changes, for a brief moment, D' would still be at 1 because the new signal hasn't arrived yet. So very briefly 11. This is probably fine.

Actual Problem: The change of the state of the bit memory still depends on the level of the input (0 or 1), not on time (when clock changes cycle)