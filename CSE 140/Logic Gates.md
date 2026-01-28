
Buffer - amplify power, like Minecraft

##### NOT Gate

| Input | P   | N   | Output | Delay |
| ----- | --- | --- | ------ | ----- |
| 0     | ON  | OFF | 1      | 2CR   |
| 1     | OFF | ON  | 0      | 2CR   |
##### NAND Gate

| Input (A B) | P1  | P2  | N1  | N2  | Output | Delay |
| ----------- | --- | --- | --- | --- | ------ | ----- |
| 0 0         | ON  | ON  | OFF | OFF | 1      | CR    |
| 0 1         | ON  | OFF | OFF | ON  | 1      | 2CR   |
| 1 0         | OFF | ON  | ON  | OFF | 1      | 2CR   |
| 1 1         | OFF | OFF | ON  | ON  | 0      | 4CR   |
##### AND Gate

| Input (A B) | P1  | P2  | N1  | N2  | X   | P   | N   | Output (Y) | Delay X | Delay Y | Total Delay |
| ----------- | --- | --- | --- | --- | --- | --- | --- | ---------- | ------- | ------- | ----------- |
| 0 0         | ON  | ON  | OFF | OFF | 1   | OFF | ON  | 0          | CR      | 2CR     | 3CR         |
| 0 1         | ON  | OFF | OFF | ON  | 1   | OFF | ON  | 0          | 2CR     | 2CR     | 4CR         |
| 1 0         | OFF | ON  | ON  | OFF | 1   | OFF | ON  | 0          | 2CR     | 2CR     | 4CR         |
| 1 1         | OFF | OFF | ON  | ON  | 0   | ON  | OFF | 1          | 4CR     | 2CR     | 6CR         |


##### Transmission Gate

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
