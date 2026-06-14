Given a set of linear constraints, how to find the best possible outcome?

You can either maximize or minimize the outcome. The original problem is called the Primal, and you can flip the desired outcome from min to max, or vise versa, to change it to Dual.

Dual has the inverse input/output, and is similar to transposing a matrix.

### Primal
$\underset{x_1,x_2\geq 0}{max} \ 3x_1+2x_2$

Active Constraint:
$x_1+x_1 \leq 4$
$2x_1+x_2 \leq 5$
Inactive Constraint:
$3x_1+3_2 \leq 20$

#### Matrix Form
$max \ c^T x \ s.t. \ Ax\leq b, x\geq 0$
where:
$A=\begin{bmatrix} 1 & 1 \\ 2 & 1 \end{bmatrix}, b=\begin{bmatrix} 4 \\ 5 \end{bmatrix}, c=\begin{bmatrix} 3 \\ 2 \end{bmatrix}$

![[Pasted image 20260526000310.png]]
Solution: $(1,3)$

The inactive constraint is not used.

We can add slack to the constraints:
$x_1+x_1+s_1 = 4$
$2x_1+x_2+s_2 =5$
$3x_1+3_2+s_3 = 20$
Slack Variable is 0 iff constraint is active

### Dual
$\underset{y_1,y_2,y_3\geq 0}{min} \ 4y_1+5y_2+20y_3$

Active Constraints:
$y_1+2y_2+3y_3\geq 3$
$y_1+y_2+3y_3 \geq 2$

#### Matrix Form
$min \ b^T y \ s.t. \ A^Ty\leq c, y\geq 0$
$c^Tx \leq (A^Ty)^T x = y^T Ax \leq y^T b = b^T y$

We can add slack to the constraints:
$y_1+2y_2+3y_3 + z_1 = 3$
$y_1+y_2+3y_3 + z_2 = 2$

$s_i=b_i-a_i^Tx \geq 0$
$z_i=(A^T y)_j -c_j \geq 0$


$y^*=(1,1,0)$

**Weak Duality**: (Holds for any feasible points)
$c^Tx \leq b^T y$

**Strong Duality**: ($x^*,y^*$ optimal do exist)
$c^Tx^* =b^T y^*$

or if there exists some optimum $w^*$ where the $p^*=q^*$

Slackness at optimum is complementary
if $y^*_i > 0$ then $s_i=0$
if $x^*_i > 0$ then $z_i=0$
$y^*_i s_i=0$
$x^*_i z_i=0$

Meaning if slack is 0, then the stars are not 0.
If the stars are zero, then slack is not 0.

Support vectors that are on the boundary have slack 0, and $\alpha_i$ not 0. If they're not on the boundary, then slack is not 0, and $\alpha_i$ is 0.

$w^*=\sum_{i=1}^na_i^*y_ix_i$

Removing non-support vectors does not change w.

 $\alpha_i^*(y^{(i)}(wx^{(i)}+b)-1)=0$

### Farkas Theorem
For Feasibility
Exactly one of the following holds:
1. $\exists x\geq 0, \ s.t. \ Ax\leq b$
2. $\exists y\geq0 \ s.t. \ A^Ty\geq 0, b^Ty<0$

$min \ b^T y \ s.t. \ A^Ty\leq c, y\geq 0$ is satisfied by $y=0$
$y_i \geq 0$ for each primal inequality $\sum_j A_{ij}x_j\leq b_i$

The existence of y s.t. $A^Ty\geq 0$ and $b^Ty<0$ proves that there is no feasible point x in primary