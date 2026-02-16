Set Reset Latch. Always outputs the last input. Stores one bit of state (Q)

Set: Make output 1 $(S=1,R=0,Q=1)$
Reset: Make output 0 $(S=0,R=1,Q=0)$
Hold: Keep data stores $(S=0,R=0,Q=Q_{previous})$

If you press both at the same time, it is very sad and not good. We will spend a lot of time trying to figure out how to stop both S and R from being turned on at the same time.
![[Pasted image 20260215180859.png]]![[Pasted image 20260215181303.png]]

### Avoiding S=1 and R=1

In order to try and avoid a scenario where S=1 and R=1, we will implement another input C as clock. S and R are only changeable when C is 1.
![[Pasted image 20260215181748.png]]

When C=0 or when clock is off, then the circuit will be as if its S=0 R=0, or it will hold its signal. When C=1, signal is allowed to pass through. This essentially locks the circuit to only change when the C=1.

![[Clock]]

This way, we can change our S and R whenever the clock is in a low state or C=0, this change will not alter the circuit, so when it comes online again, we will hopefully have changed our S and R completely so no error happens.





