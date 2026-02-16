![[Pasted image 20260215214418.png]]

### Comparison of level-sensitive latch and edge-triggered flip flop
- For DFFs or similar FF things, only check the edge/instant of change, adjust, and keep that value until the next edge
- For level-sensitives like D latch, whenever Clk is 1, copy the value of D, then keep whatever level the D is at the moment Clk goes to 0, and keep that until Clk is 1 again, when you can start copying D.
![[Pasted image 20260215225300.png]]

![[SR Latch]]

![[D Latch]]

![[D Flip-Flop]]