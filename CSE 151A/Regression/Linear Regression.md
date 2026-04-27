In regression, we fit a line to a bunch of points
For linear regression, this line needs to be defined by slope and y-intercept
linear equation is $y=ax+b$, we need to find a and b

pick a line $(a,b)$ based on $(x^{(1)},y^{(1)}),...,(x^{(n)},y^{(n)}) \in \mathbb{R} \times \mathbb{R}$
- $x^{(i)}$ and $y^{(i)}$ are predictor and response variables

To do this, we need to minimize the mean square error (MSE)
$$MSE(a,b) = \frac{1}{n}\sum^n_{i=1}(y^{(i)}-(ax^{(i)}+b))^2$$
> [!info] Title
> $y^{(i)}$ is the data y, and $ax^{(i)}+b$ is the predicted y from the regression line.
> We get their difference, which is their residual, then we square them to get rid of the negatives and also make bigger errors more impactful. Finally we add them all together to get the total amount of residuals, then divide by number of data points to get average residual per data point.
> But here's the thing, we don't need the $\frac{1}{n}$, it's redundant for our purposes, we'll be calculating using the same n data points for any $(a,b)$, so we can just get rid of that

$$L(a,b) = \sum^n_{i=1}(y^{(i)}-(ax^{(i)}+b))^2$$
To minimize, we take partial derivatives of L with respect to a and b, and set them to 0.

$\frac{\partial L}{\partial a} = -2 \sum^n_{i=1} x^{(i)}(y^{(i)}-(ax^{(i)}+b))=0$

$\frac{\partial L}{\partial b} = -2\sum^n_{i=1}(y^{(i)}-ax^{(i)}-b)=0$
$\sum^n_{i=1}(y^{(i)}-ax^{(i)}-b)=0$
$\sum^n_{i=1}y^{(i)} - a\sum^n_{i=1}x^{(i)} - nb=0$

$b = \frac{1}{n} \sum^n_{i=1}y^{(i)} - a \frac{1}{n} \sum^n_{i=1}x^{(i)}$

let $\bar x=\frac{1}{n} \sum^n_{i=1}x^{(i)}, \bar y=\frac{1}{n} \sum^n_{i=1}y^{(i)}$, which is convinently the mean of x and y

let $b = \bar y - a\bar x$

then we find b by replacing b with $\bar y - a\bar x$ in the first equation

eventually we can isolate a:
$$a^* = \frac{\sum^n_{i=1} (x^{(i)}-\bar x)(y^{(i)}-\bar y )}{\sum^n_{i=1} (x^{(i)}-\bar x)^2}=\frac{cov(x,y)}{var(x)}$$
$$b^* = \bar y - a^*\bar x$$


### Multidimensional Linear Function
$f(x)=w_1x_1+w_2x_2+...+w_dx_d+b$
This is a linear combination function that maps $d$ predictor variables $x_1...x_d$ to a single response variable $y$. Instead of having a single a, we have w for each unique x. If we define $\vec w = (b,w_1,w_2,...,w_d)$ and $\vec x=(1,x_1,x_2,...,x_d)$, we can get rid of $b$ and make $f$ a dot product between $\vec w$ and $\vec x$, which is linear combination
$$f(x)=\vec w \cdot \vec x$$
$$MSE=\frac{1}{n}\sum^n_{i=1}(y^{(i)}-\vec{w}\cdot \vec{x})^2$$
$$MSE=\frac{1}{n}||\vec y - X\vec w ||^2$$
$$X=\begin{pmatrix} x_1^{(1)} & x_2^{(1)} & ... & x_{d+1}^{(1)}\\ &-x^{(2)}- \\ ... & ... & ... & ... \\ &-x^{(n)}- \end{pmatrix} \ \ \vec w=\begin{pmatrix} w_1 \\ w_2 \\ ... \\ w_{d+1} \end{pmatrix} \ \ \vec wX=\begin{pmatrix} \vec wx^{(1)} \\ \vec wx^{(2)} \\ ... \\ \vec wx^{(n)} \end{pmatrix}$$
$$y-\vec wX=\begin{pmatrix} y^{(1)}-\vec wx^{(1)} \\ y^{(2)}-\vec wx^{(2)} \\ ... \\ y^{(n)}-\vec wx^{(n)} \end{pmatrix}$$

$$L(\vec w)=||y-X\vec w||_2^2$$

compute the gradient($\nabla$) and set to 0
$\nabla L(\vec w)=(y-X\vec w)^T(y-X\vec w)$
$\nabla L(\vec w)=2X^T(y-X\vec w)=0$
$\nabla L(\vec w)=2X^Ty-2X^TX\vec w=0$
$\nabla L(\vec w)=X^Ty=X^TX\vec w$

$$\vec w = (X^TX)^{-1}(X^Ty)$$

### Generalized Behavior of Regression
Now that we have a model, what about using it to predict future data points?
The equation can either perform well, or overfit, which is when it doesn't do well.
The more the data, the better the prediction.
- good case: $n\gg d$, error rate of training set = error rate of test set
- bad case: $n\approx d$, not good

To get a better estimate of error rate, use n-fold cross validation
- divide data set to k equal parts
- train a regressor (equation) on all data except that part, get the error
- average the error of all the regressors

To improve the generalization error:

#### Select Subset of Features
In some cases, only a small subset of the features actually have a relationship with the y. Therefore we can drop some and force the model to focus on what matters.

#### Shrinkage (Regularization)
Instead of removing features, we try to spot and penalize overfitting, which we can tell by seeing if the model has large a or b. The larger they are, the more aggressive they react to small variations in the data.

$\lambda$ - tuning parameter
$\lambda=0$: no shrinkage
$\lambda=\infty$: data is ignored

Select $\lambda$ using k-fold validation, choose the $\lambda$ that minimizes $L$

##### Ridge
$L(w)=||y-X\vec w||^2+\lambda||w||^2_2$

Adds $\lambda||w||^2_2$ to shrink the solution toward 0, but never reaches 0.
weights are evenly distributed across all features, so they all matter

##### Lasso
$L(w)=||y-X\vec w||^2+\lambda||w||_1$

Adds $\lambda||w||_1$ This can shrink the solution to 0, so it implements select subset of features automatically
Only a very small fraction of the features actually matter