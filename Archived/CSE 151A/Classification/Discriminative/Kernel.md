Kernel is a label for functions that satisfies Mercer's condition, or that they're a PSD Gram's matrix. They measures similarity between two data points

What if we want to classify binary outputs like Linear Classifier, but the boundary can be fulfilled with a non-linear shape?

We use Basis Expansion
### Basis Expansion
Turns non-linear function into linear at a different dimension.
Embed data in a higher dimensional feature space.

Squares:
$x=(x_1,x_2,...,x_d)\rightarrow\phi(x)=(x_1,...,x_d,x_1^2,...,x_d^2,x_1x_2,x_2x_3,....,x_{d-1}x_d)$

Different for different functions I suppose

##### Perceptron Algorithm: Higher Dimension
**Primal:**
- initialize w=0 and b=0
- While some $y(w \cdot \phi(x) + b)\leq 0$:
	- $w=w+y\phi(x)$
	- $b=b+y$

Problem: Way too many dimensions.
Solution:
1. w is always a linear combination of $\phi(x^{(i)})$

$w=\sum_{j=1}^n\alpha_jy_jy^{(j)}\phi(x^{(j)})$

represent w in dual form: $\alpha=(\alpha_1,...,\alpha_n)$

2. Compute $w\cdot\phi(x)$ using dual representations

$w\cdot\phi(x)=\sum_{j=1}^n\alpha_jy^{(j)}(\phi(x^{(j)})\cdot \phi(x))$

3. Compute $\phi(x)\phi(z)$ without ever writing out either of them

**Dual:** $w=\sum_{j=1}^n\alpha_jy_jy^{(j)}\phi(x^{(j)})$
- initialize $\alpha$=0 and b=0
- While some $y(\sum_j \alpha_jy^{(j)}\phi(x^{(j)})\phi(x^{(i)}) + b)\leq 0$:
	- $\alpha_i=\alpha_i+1$
	- $b=b+y$

To classify a new point $sign(\sum_j \alpha_jy^{(j)}\phi(x^{(j)})\phi(x^{(i)}) + b)$

### Example
$x=(x_1,x_2),\phi(x)=(1,\sqrt{2}x_1,\sqrt{2}x_2,x_1^2,x_2^2,\sqrt{2}x_1x_2)$

What is $\phi(x)\phi(z)$?

$\phi(x)=(1,\sqrt{2}x_1,\sqrt{2}x_2,x_1^2,x_2^2,\sqrt{2}x_1x_2)$
$\phi(z)=(1,\sqrt{2}z_1,\sqrt{2}z_2,z_1^2,z_2^2,\sqrt{2}z_1z_2)$

$\phi(x)\phi(z)=1+2x_1z_1+2x_2z_2+x_1^2z_1^2+x_2^2z_2^2+2x_1x_2z_1z_2$

$\phi(x)\phi(z)=(1+x\cdot z)^2$

This reduces the time it takes to compute back to the original dimension.

### Kernel SVM
We never explicitely construct $\phi(x)$
We instead use the kernel function $k(x,z)=\phi(x)\cdot\phi(z)$
We can think of $k$ as a measure of simialrizty between x and z

1. Define a similarity function $k(x,z)$
2. Learning: Solve the Dual Problem
$$\underset{a\in \mathbb{R}^n}{max} \sum_{i=1}^n a_i - \frac{1}{2}\sum_{i,j=1}^n a_ia_jy^{(i)}y^{(j)}k(x^{(i)},x^{(j)}))$$
such that $\sum_{i=1}^n a_i y^{(i)}=0, 0\leq \alpha_i \leq C$

3. Classification: Given a new point, classify as:
$sign(\sum_j \alpha_jy^{(j)}k(x^{(i)},x) + b)$

**Dual with K:**
- initialize $\alpha$=0 and b=0
- While some $y(\sum_j \alpha_jy^{(j)}k(x^{(j)},x^{(i)}) + b)\leq 0$:
	- $\alpha_i=\alpha_i+1$
	- $b=b+y$

To classify a new point $sign(\sum_j \alpha_jy^{(j)}k(x^{(j)},x^{(i)}) + b)$

Thein final classifier is a similarity-weighted note
$F(x)=\alpha_1y^{(1)}k(x^{(1)},x)+...+\alpha_ny^{(n)}k(x^{(n)},x)+b$

### Generality
kernel function follows some $k(x,z)=\phi(x)\cdot\phi(z)$, but you don't have to define $\phi$, you don't have to compute $\phi$ either.

**Mercer's Condition**: As long as your similarity matrix K is PSD for any set of points, there is guaranteed to exist some $\phi$, meaning you don't have to know or define or use it.

The similarity matrix K, also known as the Gram matrix, that has to be PSD:
$K_{ij}=k(x^{(i)},x^{(j)})$

So  as long as K is PSD, we can say that $k(x,z)=\phi(x)\cdot\phi(z)$

any K that comes from a valid kernel is PSD:
$\mathbf{y}^\top K \mathbf{y} = \mathbf{y}^\top \Phi \Phi^\top \mathbf{y} = (\Phi^\top \mathbf{y})^\top (\Phi^\top \mathbf{y}) = \|\Phi^\top \mathbf{y}\|^2 \geq 0$

### RBF Kernel
Also known as Gaussian Kernel

$k(x,z)=e^{-|x-z|^2/s^2}$
where s is an adjustable parameter

This looks like a gaussian, or a bell curve

As s increase and approaches infinity, the curve gets flatter and flatter until it's 1 at all points
As s decrease and approaches 0, the curve gets sharper until it's only 1 at x-z.

Generally, more data means less s, since more data makes you more certain, meaning a more complex, wiggly, and certain decision boundary.