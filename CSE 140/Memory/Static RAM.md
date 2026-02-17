---
aliases:
  - SRAM
---
Static Random Access Memory

Static stands for as long as you have power there, the value will stay and will not decay or dissipate into nothing. As opposed to Dynamic RAM which will disappear eventually, you would have to refresh it to keep it there

The "load" and "remember" switches are each just 1 nmos transistor, instead of the traditional transmission gates that uses both nmos and pmos transistors. This is because there's only 2 not gates in the circuit, which means you don't need to be as percise/extreme in cutting off signal, and that this is the only time when this is commonly used, and you would need two transistors for other scenarios. 

This means SRAM has 6T
![[Pasted image 20260215175927.png]]