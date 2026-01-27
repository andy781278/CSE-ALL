
Complementary Metal Oxide Semiconductor (CMOS) Switches
Metal - Conductor
Oxide - Insulator
Silicon - Semiconductor
Source/Drain - Semiconductor with impurities

negative Metal Oxide Semiconductor (nMOS)
- negative charge go through the source, gets pulled by the positive charge in the gate, but can't get to it because of the oxide, making it a capacitor.
- negative charge going through Semiconductors generate small resistance.

- If you put negative charge in the gate instead of positive, then positive charge gets stuck between the source and drain, then it neutralizes with anything coming from source.
- This makes an open circuit, since no current flows, with infinite resistance.

- pass logic 1 to the gate, nMOS turns on.
- pass logic 0 to the gate, nMOS turns off.

- Passes 0s well

positive Metal Oxide Semiconductor (pMOS)
- Completely opposite to nMOS, but everything else works the same
- pass logic 1 to the gate, pMOS turns off.
- pass logic 0 to the gate, pMOS turns on.

- Passes 1s well

NOT Gate:
p on top, n on bot
Delay: 2CR

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
Z - disconnected, neither 0 or 1

| A   | EN  | N   | P   | B   |
| --- | --- | --- | --- | --- |
| A   | 0   | OFF | OFF | Z   |
| A   | 1   | ON  | ON  | A   |

##### Practice:

| A   | B   | A'  | PA  | PB  | NA  | NB  | X   | Y   | Delay |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | ----- |
| 0   | 0   | 1   | OFF | ON  | ON  | OFF | 1   | 0   | 2RC   |
| 0   | 1   | 1   | OFF | OFF | ON  | ON  | 0   | 1   | 4RC   |
| 1   | 0   | 0   | ON  | ON  | OFF | OFF | 1   | 0   | RC    |
| 1   | 1   | 0   | ON  | OFF | OFF | ON  | 1   | 0   | 2RC   |
$Y=\overline AB$

Y = (A'+C')(A+B')(A+C')

(A' AND B')' = A OR B
(A AND B)' = A' OR B'

(A'+C')(A+B')(A+C')
(A'+C')(A+C')(A+B')
C'(A+B')
NOT(C) AND (NOT A NOR B)

(A and B)'
(A' OR B')'
A' NOR B'

A,B => A',B'

C NOR (NOT A NOR B)'
C NOR NOT (NOT A NOR B)

(ACD + A(C'+D') + B)(A'+B)=B
(A(CD +C'+D')) + B)(A'+B) Distributive
(A(CD +(CD)')) + B)(A'+B) De Morgan's
(A1+B)(A'+B) Complements
(A+B)(A'+B) Identity
(B+A)(B+A') Commutativity
B Combining

ABCD+ABCD'+A'B(A'+C)=B(C+A')
B(ACD+ACD'+A'(A'+C)) Distributive
B(ACD+ACD'+A') Absorption
B(AC(D+D')+A') Distributive
B(AC1+A') Complement
B(AC+A') Identity
B(A'+AC) Commutativity
B(A'(1)+AC) Identity
B(A'(A+A')+AC) Inverse
B(A'A+A'A'+AC) Distributive
B(A'A+A'+AC) Inverse
B(0+A'+AC) Inverse
B(A'+AC) Identity

Not takes 2 transistors
AND OR takes 6 transistors
I assume NAND and NOR takes 4 then
XOR? IDK
(A'C'+B'C')(A'+B)
C'(A'+B')(A'+B)
C'A'
(C+A)'