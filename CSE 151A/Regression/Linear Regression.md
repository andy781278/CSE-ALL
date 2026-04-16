We fit a line to a bunch of points

linear equation is $y=mx+b$, we need to find m and b

pick a line $(a,b)$ based on $(x^(1),y^(1)),...,(x^{(n)},y^{(n)}) \in \mathbb{R} \times \mathbb{R}$
- $x^{(i)}$ and $y^{(i)}$ are predictor and reponse variables

minimize the mean square error (MSE)
$$MSE(a,b) = \frac{1}{n}\Sigma^n_{i=1}(y^{(i)}-(ax^{(i)}+b))^2$$
This is the loss function

we need to minimize this:
$$L(a,b) = \Sigma^n_{i=1}(y^{(i)}-(ax^{(i)}+b))^2$$

Take partial derivatives of L in respect to a and b, and set them to 0.

$\frac{\partial L}{\partial a} = -2 \Sigma^n_{i=1} x^{(i)}(y^{(i)}-(ax^{(i)}+b))=0$

$\frac{\partial L}{\partial b} = -2\Sigma^n_{i=1}(y^{(i)}-ax^{(i)}-b))=0$

$\Sigma^n_{i=1}(y^{(i)}-ax^{(i)}-b))=0$

$\Sigma^n_{i=1}y^{(i)} - a\Sigma^n_{i=1}x^{(i)} - nb))=0$

solve for b:
$b = \frac{1}{n} \Sigma^n_{i=1}y^{(i)} - a \frac{1}{n} \Sigma^n_{i=1}x^{(i)}$

let $\bar x=\frac{1}{n} \Sigma^n_{i=1}x^{(i)}, \bar y=\frac{1}{n} \Sigma^n_{i=1}y^{(i)}$, then $b = \bar y - \bar ax$

then we find b by replacing b with $\bar y - \bar ax$ in the first equation

eventually we can isolate a:
$$a^* = \frac{\Sigma^n_{i=1} (x^{(i)}-\bar x)(y^{(i)}-\bar y )}{\Sigma^n_{i=1} (x^{(i)}-\bar x)^2}$$
$$b^* = \bar y - \bar a^*x$$
