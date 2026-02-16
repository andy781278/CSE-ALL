---
aliases:
  - DFF
  - D-FF
  - Data Flip Flop
  - Data Flip-Flop
---
Best thing we can think of: Put two D latches together and put a NOT on clock (Clk).

Process (Rising Edge FF):
NOT gate is connected to the master, updates slave on rising edge
1. master takes in D when Clk is at 0, and feeds it into the slave simultaneously
2. slave accepts master's Q (Qm) when Clk goes from 0 to 1. It then can change outputs
3. master is locked in after Clk reaches 1, so it won't change anymore.

Process (Falling Edge FF):
https://www.falstad.com/circuit/e-masterslaveff.html
NOT gate is connected to the slave, updates slave on falling edge
1. master takes in D when Clk is at 1, and feeds it into the slave simultaneously
2. slave accepts master's Q (Qm) when Clk goes from 1 to 0. It then can change outputs
3. master is locked in after Clk reaches 0, so it won't change anymore.

![[Pasted image 20260215221553.png]]
![[Pasted image 20260215224600.png]]
### Characteristic Equation
![[Pasted image 20260215224454.png]]

### Enabled D-FFs
Only takes in D when EN is enabled.
![[Pasted image 20260215224826.png]]

### Additional Shit
You can add more stuff to the DFF to make it more convinent, like a Reset and Set function to make D 0 or 1.
![[Pasted image 20260215225503.png]]