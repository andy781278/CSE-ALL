![[Pasted image 20260506035705.png]]

A function $f:\mathbb{R}^d \rightarrow \mathbb{R}$ is convex if $\forall a,b \in \mathbb{R}^d$ and $0<\theta<1$
$$f(\theta a + (1-\theta)b)\leq\theta f(a)+(1-\theta)f(b)$$

> [!info] 
> For any two points a and b, everything between them must be under the line between them

it is strictly convex if strict inequality holds for all $a\neq b$
concave and convex are negatives


### 1 Dimension
in 1D, we can check by seeing if double derivative function is $\geq 0$ everywhere

### d Dimension
the derivative in d Dimension is a d-dimensional vector called the gradient or $\nabla$, and the second derivative is a $d\times d$ matrix called the hessian or $\nabla^2$ or $H$.

Convex if second derivative matrix is always positive semidefinite


### Example
$f(x)=||x||^2$
$\nabla f = 2\vec x$ 
$H(f)=2I$

$f(z)=(\vec u \cdot \vec z)^2$
$\vec u\in\mathbb{R}^d$
$\nabla f = [2uuz_1,2uuz_2,...,2uuz_d]=2u_i (\vec u \cdot \vec z)$ 
$H(f)=2UU^T=2u_iu_i$

Linear Regression
$L(\vec w)=||X\vec w-y||_2^2=(y-X\vec w)^T(y-X\vec w)$
$\nabla L(\vec w)=-2X^T(y-X\vec w)=2X^TX\vec w-2X^Ty$
$H(L)=2X^TX$
H is PSD because $w^T2X^TXw=2(Xw)^T(Xw)=||X_w||^2_2\geq 0$

Logistic Regression
$L(\vec w)=\sum^{n}_{i=1}ln(1+e^{-y^{(i)}(\vec w\cdot x^{(i)})})$
$\nabla L(\vec w)=-\sum^{n}_{i=1}\frac{y^ix^i}{1+e^{y^{i}w^Tx^{i}}}$
define $g_i(t)=-\frac{y^i}{1+e^{-t}}, t_i=y^iw^Tx^i$
$\nabla L_i=g(t_i)x^i$
$\nabla^2 L_i(w)=g'_i(t_i)x^i(yx^i)^T=(y^i)^2\frac{e^{t_i}}{(1+e^{t_i})^2}x^i(x^i)^T$
$\nabla^2 L_i(w)=\sum_{i=1}^n\frac{e^{y^iw^Tx_i}}{(1+e^{y^iw^Tx^i})^2}x^i(x^i)^T$
$d_i=\frac{e^{y^iw^Tx_i}}{(1+e^{y^iw^Tx^i})^2}$
$D=diag(d_1,d_2,...,d_d)$
$\nabla^2 L(w)=X^TD(w)X$
$U^TX^TDXU=\sum_{i=1}^n d_i (x^i)^T(x^i)$
