We fit a line to a bunch of points

linear equation is $y=ax+b$, we need to find a and b

pick a line $(a,b)$ based on $(x^{(1)},y^{(1)}),...,(x^{(n)},y^{(n)}) \in \mathbb{R} \times \mathbb{R}$
- $x^{(i)}$ and $y^{(i)}$ are predictor and response variables

To do this, we need to minimize the mean square error (MSE)
$$MSE(a,b) = \frac{1}{n}\sum^n_{i=1}(y^{(i)}-(ax^{(i)}+b))^2$$
This is the loss function

we need to minimize this:
$$L(a,b) = \sum^n_{i=1}(y^{(i)}-(ax^{(i)}+b))^2$$

To minimize, we take partial derivatives of L with respect to a and b, and set them to 0.

$\frac{\partial L}{\partial a} = -2 \sum^n_{i=1} x^{(i)}(y^{(i)}-(ax^{(i)}+b))=0$

$\frac{\partial L}{\partial b} = -2\sum^n_{i=1}(y^{(i)}-ax^{(i)}-b))=0$

$\sum^n_{i=1}(y^{(i)}-ax^{(i)}-b))=0$

$\sum^n_{i=1}y^{(i)} - a\sum^n_{i=1}x^{(i)} - nb))=0$

solve for b:
$b = \frac{1}{n} \sum^n_{i=1}y^{(i)} - a \frac{1}{n} \sum^n_{i=1}x^{(i)}$

let $\bar x=\frac{1}{n} \sum^n_{i=1}x^{(i)}, \bar y=\frac{1}{n} \sum^n_{i=1}y^{(i)}$, then $b = \bar y - \bar ax$

then we find b by replacing b with $\bar y - \bar ax$ in the first equation

eventually we can isolate a:
$$a^* = \frac{\sum^n_{i=1} (x^{(i)}-\bar x)(y^{(i)}-\bar y )}{\sum^n_{i=1} (x^{(i)}-\bar x)^2}=\frac{cov(x,y)}{var(x)}$$
$$b^* = \bar y - \bar a^*x$$


### Multidimensional Linear Function
$f(x)=w_1x_1+w_2x_2+...+w_dx_d+b$
This is a linear combination function that maps $d$ predictor variables $x_1...x_d$ to a single response variable $y$. Instead of having a single a, we have w for each unique x. If we define $\vec w = (b,w_1,w_2,...,w_d)$ and $\vec x=(1,x_1,x_2,...,x_d)$, we can get rid of $b$ and make $f$ a dot product between $\vec w$ and $\vec x$, which is linear combination
$$f(x)=\vec w \cdot \vec x$$
$$MSE=\frac{1}{n}\sum^n_{i=1}(y^{(i)}-\vec{w}\cdot \vec{x})^2$$
$$MSE=\frac{1}{n}||\vec y - X\vec w ||^2$$
$$X=\begin{pmatrix} x_1^{(1)} & x_2^{(1)} & ... & x_{d+1}^{(1)}\\ &-x^{(2)}- \\ ... & ... & ... & ... \\ &-x^{(n)}- \end{pmatrix} \ \ \vec w=\begin{pmatrix} w_1 \\ w_2 \\ ... \\ w_{d+1} \end{pmatrix} \ \ \vec wX=\begin{pmatrix} \vec wx^{(1)} \\ \vec wx^{(2)} \\ ... \\ \vec wx^{(n)} \end{pmatrix}$$
$$y-\vec wX=\begin{pmatrix} y^{(1)}-\vec wx^{(1)} \\ y^{(2)}-\vec wx^{(2)} \\ ... \\ y^{(n)}-\vec wx^{(n)} \end{pmatrix}$$
$L(\vec w)=||y-X\vec w||_2^2$
compute the gradient($\nabla$) and set to 0
$\nabla L(\vec w)=(y-X\vec w)^T(y-X\vec w)$
$\nabla L(\vec w)=2X^T(y-X\vec w)=0$
$\nabla L(\vec w)=2X^Ty-2X^TX\vec w=0$
$\nabla L(\vec w)=X^Ty=X^TX\vec w$
$\vec w = (X^TX)^{-1}(X^Ty)$

### Generalized Behavior of Regression
The more the data, the better the prediction.
good case: $n\gg d$, error rate of training set = error rate of test set
bad case: $n\approx d$, not good
To get a better estimate, use n-fold cross validation
To improve the generalization error,
1. select subset of features
2. shrinkage

$L(w)=||y-X\vec w||^2+\lambda||w||^2$
to shrink the solution toward 0.
$\lambda$ - tuning parameter
$\lambda=0$: no shrinkage
$\lambda=\infty$: data is ignored