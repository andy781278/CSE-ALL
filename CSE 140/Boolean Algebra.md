### Laws
![[Pasted image 20260127030755.png]]
$B*(B+C)=B, B+(B*C)=B$, Covering/Absorption
$(B*C)+(B*\overline C)=B, (B+C)*(B+\overline C)=B$, Combining
$(A*B)+(B*C)+(A'*C)=A*B+A'*C$, Consensus

### Definitions
**Complement** - variable with a bar over it or '
A', B', C'

**Literal** - variables or its complement
A, A', B, B', C, C'

**Implicant** - product of literals
ABC, AC, B'C'
used as a single term in K-map Boolean function representations

**Prime Implicant** - implicant that can't be combined with another to form a bigger implicant with less variables

**Essential Prime Implicant** - prime implicants that is essential if it is the only one that covers an element of the ON set

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
- Visualization technique for applying the uniting theorem
- Geometric equivalence to a Boolean expression
- n input variables = n dimensions for cube
- Color in the vertex (turn it on) when the function of the inputs of the dimension is 1
- Easiest to identify variables that don't matter
- You can combine faces to collapse a dimension when it doesn't affect the outcome
### K-Maps
Visualization similar to Boolean Cubes

##### 2 variables
![[Pasted image 20260127214715.png]]
Grouping Methods:
- 0-cube: cancels nothing, yields 2 literals
- 1-cube: box a rectangle across a column or row, yields 1 literal
- 2-cube: box the whole thing, yields constant 1

##### 3 variables
![[Pasted image 20260127214308.png]]
Grouping Methods:
- 0-cube: 3 literals
- 1-cube: 2x1/1x2 rectangle, can wrap around horizontally, 2 literals
- 2-cube: 2x2/4x1 rectangle, wrap around, 1 literal
- 3-cube: constant 1

##### 4 variables
![[Pasted image 20260127215407.png]]
Grouping Methods:
- 0-cube: 4 literals
- 1-cube: 2x1/1x2 rectangle, can wrap around horizontally, 3 literals
- 2-cube: 2x2/4x1 rectangle, wrap around, warp 4 corners, 2 literal
- 3-cube: 4x2/2x4 rectangle, wrap around, 1 literal
- 4-cube: constant
### Don't Cares
a possible output that is neither 0 or 1, but X, which stands for don't care. For scenarios when:
- output doesn't matter
- output is not definite

### Completely Specifying Boolean Functions
To completely specify, you need to make sure there's enough info to rebuild the truth table, you'll have to provide two of the following three possibilities:
- When output is 1
- When output is 0
- When output is X
The missing output can only be 1 thing because we know there is only 1 thing left

