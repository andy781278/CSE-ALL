##### Transmission Gate
Lets current pass through if EN is on

| A   | EN  | N   | P   | B   |
| --- | --- | --- | --- | --- |
| A   | 0   | OFF | OFF | Z   |
| A   | 1   | ON  | ON  | A   |

##### Tristate Buffer
used in tristate bus, for sending/reading different parts of the computer

| E   | A   | Y   |
| --- | --- | --- |
| 0   | 0   | Z   |
| 0   | 1   | Z   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |
^046151

##### Multiplexer
Selects 1 out of N bits to connect to the output

| S   | $D_1$ | $D_0$ | Y   |
| --- | ----- | ----- | --- |
| 0   | 0     | 0     | 0   |
| 0   | 0     | 1     | 1   |
| 0   | 1     | 0     | 0   |
| 0   | 1     | 1     | 1   |
| 1   | 0     | 0     | 0   |
| 1   | 0     | 1     | 0   |
| 1   | 1     | 0     | 1   |
| 1   | 1     | 1     | 1   |

| S   | Y     |
| --- | ----- |
| 0   | $D_0$ |
| 1   | $D_1$ |
Using a kmap to get a POS would use up 20T, but using the pass gate method gets you only 6T.

##### Encoder
turns input signal into binary (encodes it)

##### Decoder
Decision maker, based on combination of inputs, enable one output
- Used to decode memory address to memory location
- Make a tree of decoders to find something in a large memory

##### Ripple-Carry Adder
Chain adders together, each carry connected to the next digit until the very end
- Disadvantage: slow
- Linear time delay

##### Carry-Lookahead Adder
Because Ripple-Carry is so slow (it has to go through every number linearly), we can pre-generate the carry using math.
- For the ith add in a row
	- $Sum = A_i \textasciicircum B_i \textasciicircum C_i$
	- $C_{i+1}=A_i B_i + C_i (A_i \textasciicircum B_i)$
	- $C_{i+1}=G_i + C_i P_i$

##### Subtractor
$A+\overline B$
Detects if overflow via checking if the input sign bit (most significant) is different from the cout bit
![[Pasted image 20260215162430.png]]

##### Equator
Could be an XNOR implementation, or it could be a subtractor implementation
![[Pasted image 20260215163000.png]]

##### Less Than
[N-1] is the sign bit, which in a subtractor, when its positive, that means A<B, which means that when A+-B, B is bigger, so the bit flips, which means A<B.
![[Pasted image 20260215164825.png]]

##### Shifters

**Logical Shifter** - shifts left or right and fills empty space with 0's
EX: 11001 >> 2 - 00110

**Arithmetic Shifter** - shifts left or right and filsl empty space with the old most significant bit
Ex: 11001 >> 2 - 11110

**Rotator** - rotates the bit in a circle
Ex: 11001 >> 2 - 01110
![[Pasted image 20260215173805.png]]

