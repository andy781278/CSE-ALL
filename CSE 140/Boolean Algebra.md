![[Pasted image 20260127030755.png]]
$B*(B+C)=B, B+(B*C)=B$, Covering/Absorption
$(B*C)+(B*\overline C)=B, (B+C)*(B+\overline C)=B$, Combining
$(A*B)+(B*C)+(A'*C)=A*B+A'*C$, Consensus

Definitions:
**Complement** - variable with a bar over it or '
A', B', C'

**Literal** - variables or its complement
A, A', B, B', C, C'

**Implicant** - product of literals
ABC, AC, B'C'

**Implicate** - sum of literals
(A+B+C), (A+B), (B+C)

**Minterm** - product that includes all input variables
ABC, A'B'C', A'B'C, AB'C', AB'C

Maxterm - sum that includes all input variables
(A+B+C), (A+B'+C), (A'+B'+C')

### Canonical Form
standard form that consists of the sum of minterms (or maxterms)
#### Sum-Of-Products (SOP)
Canonical Forms obtained from looking at when the output is 1. AND the input Literals together then OR the Implicants.
Use for very few ones
$F(A,B,C)=\sum m(0,2,4) = \Pi M(1,3)$
$F'(A,B,C)=\sum m(1,3) = \Pi M(0,2,4)$
#### Product-Of-Sums (POS)
implements "zeros" of a function, which means you look at when the output is 0. OR the input Literals together then AND the Implicants. For this mode, 0 means original, 1 means complement. Do everything the other way.
Use for very few zeros
$F(A,B,C)=\Pi M(0,2,4)=\sum m(1,3)$
$F'(A,B,C)=\Pi M(1,3)=\sum m(0,2,4)$
### Minimal Form
the shortest form

Method to optimize circuits:
1. Boolean Algebra Axioms and Theorems
2. K-Maps

### Boolean Cubes
Visualization technique for applying the uniting theorem
n input variables = n dimensions for cube

### K-Maps