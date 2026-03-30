---
aliases:
  - HLSM
---
A better FSM
- Handles multi-bit data storage
- data storage
- if statements
- comparisons
- multi-bit data input
- multi-bit data output

Guidelines:
- Only do what's necessary
- One operation per state

HLSMs are split into states and edges, states is where you do something, action, and edge is to check something, condition
- conditions:
	- comparison
		- addr with input a,b for a-b, not gate on b and carry=1
		- MSB=1 means a<b, vise versa.
	- check input 1 or 0
- actions:
	- assigning variables
		- make them beforehand: (register)
			- assigning values to them (ld)
			- resetting them (clr)
	- clearing variables
	- send output 1 or 0