---
aliases:
  - FSM
---
Variables:
- Set of states
- Set of inputs
- Set of outputs
- Initial State
- Set of transitions
	- Only one can be true at a time

FSM represents:
- State diagram
- State table

Interpretation:
- A graph
	- vertices are unique states the circuit can be in
	- Edges are transitions that move a circuit from one state to another
	- A vertex can only traverse through one edge at a time
	- Input and Output are dependent on if its a Moore or Mealy state machine, but they generally don't contribute to the graph itself, but to how one would traverse through the vertices.

![[Pasted image 20260216155123.png]]

![[Mealy and Moore Machines]]

# FSM => Circuit
From FSM, we can devolve it into a circuit through some work.
### State Diagram => State Table with State Assignment
Through the diagram, you make a table with each row being a unique state, then you put an input for each column, and for each cell, you put the next state from following the column input, and then put the output. 
![[Pasted image 20260216161614.png]]
### State Table => Excitation Table
Then, you transform the states into binary.
![[Pasted image 20260216161823.png]]

### Excitation Table => K-Map
After that, you put all possible input + binary state combinations together, and make a K-Map for each bit of next state, and another for output.
![[Pasted image 20260216162157.png]]
![[Pasted image 20260216162242.png]]
### K-Map => Circuit
Find the prime implicants and get the circuit equation, then simplify it, then implement it.
![[Pasted image 20260216162418.png]]

