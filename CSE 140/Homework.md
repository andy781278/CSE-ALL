##### HW1

| A   | B   | A'  | PA  | PB  | NA  | NB  | X   | Y   | Delay |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | ----- |
| 0   | 0   | 1   | OFF | ON  | ON  | OFF | 1   | 0   | 2RC   |
| 0   | 1   | 1   | OFF | OFF | ON  | ON  | 0   | 1   | 4RC   |
| 1   | 0   | 0   | ON  | ON  | OFF | OFF | 1   | 0   | RC    |
| 1   | 1   | 0   | ON  | OFF | OFF | ON  | 1   | 0   | 2RC   |
|     |     |     |     |     |     |     |     |     |       |
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

##### HW2

| CD\AB | 00    | 01    | 11  | 10  |
| ----- | ----- | ----- | --- | --- |
| 00    | 0     | 0     | 0   | 0   |
| 01    | ==1== | ==1== | 1   | 0   |
| 11    | ==1== | ==1== | 1   | 1   |
| 10    | 0     | 0     | 0   | 0   |
$\overline A D$, $BD$, $CD$

$\overline A D + BD + CD$

$D(\overline  A + B + C)$

Z(0,0,C)=1
Z(0,1,C)=C'
Z(1,0,C)=C
Z(1,1,C)=C'

| C\AB | 00  | 01  | 11  | 10  |
| ---- | --- | --- | --- | --- |
| 0    | 1   | 1   | 1   | 0   |
| 1    | 1   | 0   | 0   | 1   |
$\overline{AB}+B\overline{C}+\overline B C$

| C\AE | 00  | 01  | 11  | 10  |
| ---- | --- | --- | --- | --- |
| 0    | 0   | 0   | 1   | 0   |
| 1    | 1   | 0   | 1   | 1   |
$(A +\overline E)(C+E)$

| C\BD | 00  | 01  | 11  | 10  |
| ---- | --- | --- | --- | --- |
| 0    | 0   | 0   | 0   | 1   |
| 1    | 0   | 1   | 1   | 1   |
$B\overline D + CD$


| Decimal | Thermometer |
| ------- | ----------- |
| 0       | 00 0 0 0 00 |
| 1       | 00 0 0 0 01 |
| 2       | 00 0 0 0 11 |
| 3       | 00 0 0 1 11 |
| 4       | 00 0 1 1 11 |
| 5       | 00 1 1 1 11 |
| 6       | 01 1 1 1 11 |
| 7       | 11 1 1 1 11 |

| g0\g2g1 t2 | 00  | 01  | 11  | 10  |
| ---------- | --- | --- | --- | --- |
| 0          | 0   | 0   | 1   | 0   |
| 1          | 1   | 1   | 1   | 1   |
|            |     |     |     |     |
| g0\g2g1 t4 | 00  | 01  | 11  | 10  |
| 0          | 0   | 0   | 0   | 0   |
| 1          | 0   | 1   | 1   | 1   |
$t_2=g_0+g_1g_2$
$t_4 = g_0g_1+g_0g_2$

##### Test 1
4+8+18=30T

| C\AB | 00  | 01  | 11  | 10  |
| ---- | --- | --- | --- | --- |
| 0    | 1   | 1   | 1   | 1   |
| 1    | 1   | 1   | 0   | 1   |
$=\overline A + \overline C + \overline B$
$=\overline{\overline{(\overline A + \overline C + \overline B)}}$
$=\overline{ABC}$

| A/B | 0   | 1   |
| --- | --- | --- |
| 0   | 0   | 1   |
| 1   | 1   | 0   |
|     |     |     |
|     |     |     |


##### HW3

| X        | 0    | 1    | 2    | 3    | -4   | -3   | -2   | -1   |
| -------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| X2X1X0   | 000  | 001  | 010  | 011  | 100  | 101  | 110  | 111  |
| Y        | 0    | 2    | 4    | 6    | -8   | -7   | -5   | -3   |
| Y3Y2Y1Y0 | 0000 | 0010 | 0100 | 0110 | 1000 | 1001 | 1011 | 1101 |

Y3: 100+101+110+111
Y2: 010+011+111
Y1: 001+011+110
Y0: 101+110+111

Cout has to be 0 for output to be non-zero
nor gate: only on when everything's off
0 0 1
0 1 0
1 0 0
1 1 0

So only on if everything's off, including carry, then output is 1

| Cin | F4  | F3  | F2  | F1  | F0  | Function |
| --- | --- | --- | --- | --- | --- | -------- |
| 0   | 1   | 1   | 1   | 1   | 1   | A<B      |
| 1   | 1   | 0   | 1   | 0   | 1   | A-B      |
| 1   | 1   | 1   | 1   | 0   | 1   | !(A==B)  |
| 0   | 1   | 0   | 1   | 0   | 0   | A+B      |
| X   | 1   | 0   | 0   | 0   | 0   | A\|B     |
| 0   | 1   | 0   | 1   | 0   | 1   | A-B-1    |
| 0   | 0   | 1   | 0   | 0   | 1   | B==-1    |

Nand
0 0 1
0 1 1
1 0 1
1 1 0

| A   | B   | Q(t) | Q(t+d)  | States  |
| --- | --- | ---- | ------- | ------- |
| 0   | 0   | 0    | 0       | Reset   |
| 0   | 0   | 1    | Invalid | Invalid |
| 0   | 1   | 0    | 0       | Hold    |
| 0   | 1   | 1    | 1       | Hold    |
| 1   | 0   | 0    | 1       | Set     |
| 1   | 0   | 1    | Invalid | Invalid |
| 1   | 1   | 0    | 1       | Set     |
| 1   | 1   | 1    | 1       | Hold    |

| Q\AB | 00  | 01  | 11  | 10  |
| ---- | --- | --- | --- | --- |
| 0    | 0   | 0   | 1   | 1   |
| 1    | X   | 1   | 1   | X   |

| Q1  | Q2  | Input | Q1N | Q2N | Y   |
| --- | --- | ----- | --- | --- | --- |
| 0   | 0   | 0     | 0   | 0   | 0   |
| 0   | 0   | 1     | 1   | 0   | 0   |
| 0   | 1   | 0     | 0   | 0   | 1   |
| 0   | 1   | 1     | 0   | 0   | 0   |
| 1   | 0   | 0     | 0   | 1   | 0   |
| 1   | 0   | 1     | 1   | 1   | 0   |
| 1   | 1   | 0     | 0   | 1   | 1   |
| 1   | 1   | 1     | 0   | 1   | 0   |

Q1N = xQ2'
Q2N = Q1

##### HW4

Cin=1
a=1
b=1
sum=1

| OUT(t)   | t+1  | t+2  | t+3  | t+4  | t+5  |      |      |      |
| -------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 1101     | 1110 | 1111 |      |      |      |      |      |      |
| OUT(t)   | 1111 | 0001 | 1010 | 1011 | 1100 | 1101 | 0110 | 0111 |
| OUT(t+1) | 1110 | 0010 | 0100 | 0111 | 1000 | 1010 | 1100 | 1111 |

| G0 UP\G2 G1 | 00  | 01  | 10  | 11  |
| ----------- | --- | --- | --- | --- |
| 00          | 0   | 1   | 1   | 0   |
| 01          | 1   | 0   | 0   | 1   |
| 10          | 0   | 1   | 1   | 0   |
| 11          | 1   | 0   | 0   | 1   |

| G0 UP\G2 G1 | 00  | 01  | 11  | 10  |
| ----------- | --- | --- | --- | --- |
| 00          | 0   | 1   | 0   | 1   |
| 01          | 1   | 0   | 1   | 0   |
| 11          | 1   | 0   | 1   | 0   |
| 10          | 0   | 1   | 0   | 1   |


|     | Next State X=0 | Next State X=1 |
| --- | -------------- | -------------- |
| S0  | S0,0           | S1,0           |
| 1   | S2,0           | S1,0           |
| 2   | S0,0           | S3,0           |
| 3   | S2,0           | S4,0           |
| 4   | S2,1           | S1,1           |


| ID  | S   | X   | NS  | Z   |
| --- | --- | --- | --- | --- |
| 0   | 000 | 0   | 000 | 0   |
| 1   | 000 | 1   | 001 | 0   |
| 2   | 001 | 0   | 010 | 0   |
| 3   | 001 | 1   | 001 | 0   |
| 4   | 010 | 0   | 000 | 0   |
| 5   | 010 | 1   | 011 | 0   |
| 6   | 011 | 0   | 010 | 0   |
| 7   | 011 | 1   | 100 | 0   |
| 8   | 100 | 0   | 010 | 1   |
| 9   | 100 | 1   | 001 | 1   |
| 10  |     |     |     |     |

| S0 X\S2 S1 | 00  | 01  | 11  | 10  |
| ---------- | --- | --- | --- | --- |
| 00         | 0   | 0   | X   | 0   |
| 01         | 0   | 0   | X   | 0   |
| 11         | 0   | 1   | X   | X   |
| 10         | 0   | 0   | X   | X   |
S2(t+1)=S1S0X

Z = S0(t) (A+B)
S1(t+1) = A S0(t)' S1(t)'
S0(t+1) = S0(t)(A+B)+ B S1(t)

A is 1, goto 10
### 00
S1(t+1) = A
S0(t+1) = 0

A B
0 0 = 00
0 1 = 00
1 0 = 10
1 1 = 10

A or B then (goto 10 and output true)
### 01
Z = A OR B
S1(t+1) = 0
S0(t+1) = A OR B

A B
0 0 = 00 0
0 1 = 10 1
1 0 = 10 1
1 1 = 10 1

B is 1, goto 01
### 10
Z = 0
S1(t+1) = 0
S0(t+1) = B

A B
0 0 = 00
0 1 = 01
1 0 = 00
1 1 = 01

A or B then (goto 01, output true)
### 11
Z = A+B
S1(t+1) = 0
S0(t+1) = A+B

A B
0 0 = 00 0
0 1 = 01 1
1 0 = 01 1
1 1 = 01 1

If the pattern is A=1, then B=1, then A or B, then true
At that point, go back to 10.

##### HW 5

$T_{min} = t_{pcq}+t_{setup}+...$
$T_{min} = 30+20+...$
1. 30+25
2. 25+25
1 wins, so 55.
$T_{min} = 30+20+55=105 ps$
$F_{max}=1/105ps=9.5 GHz$

$t_{hold}<20+(10)-t_{skew}$
$30<30-t_{skew}$
$t_{skew}<0$

$T_c \geq t_{pcq}+(t_{pd}...)+t_{setup}$
$T_c \geq 60+(40)+15$
$T_c \geq 115ps$

$110<25-t_{skew}$

$t_{skew}< -85$
80/27=3
65/27=3

27*3+40+15+60=196
1/196*1000=5.1GHz

$110<25+(5+3*27)-t_{skew}$
$t_{skew}<25+(5+3*27)-110$
$t_{skew}<1$

HW 6

![[Pasted image 20260310225021.png]]

$T_c \geq t_{pcq}+t_{pd}+t_{setup}+t_{skew}$
$T_c \geq 75+...$
$T_c \geq 191ps$

$t_{hold} < t_{ccq}+t_{cd}-t_{skew}$
$60 < t_{cd}$
60/8=7.5 round up to 8

| CD\AB | 00  | 01  | 11  | 10  |
| ----- | --- | --- | --- | --- |
| 00    | 0   | 0   | 0   | 0   |
| 01    | 0   | 0   | 0   | 0   |
| 11    | 0   | 1   | 1   | 1   |
| 10    | 0   | 1   | 1   | 0   |
BC+ACD