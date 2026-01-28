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
