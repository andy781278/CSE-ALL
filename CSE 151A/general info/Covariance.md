$$cov(X,Y)=E[(X-E(X))(Y-E(Y))]$$
$$cov(X,Y) = E[XY]-E[X]E[Y]$$
maximized when X=Y, which is when var(X)=Var(Y)=cov(X,Y)

in general, it is at most std(X)std(Y)

When X and Y are independent, cov(X,Y)=0
But when cov(X,Y)=0, X and Y are not necessarily independent

> [!NOTE]
> Covariance is a measure of the correlation between X and Y, except it's uninterpretable
> To interpret it, you divide them by std(X)std(Y) to get correlation r, which has a range of  [-1,1]
> When r=1, they move up together. When r=-1, they move opposite directions. When r=0, they have no correlation, but they might still be dependent (if the data points are in a perfect circle)

### Covariance Matrix
For a random vector $X=(X_1,...,X_d)^T$ with mean $\mu=E[X]$, the covariance matrix
$\sum \in \mathbb{R}^{d\times d}$ has entries
$$\sum_{ij} = cov(X_i,X_j)=E[(X_i-\mu_i)(X_j-\mu_j)]$$
Matrix Form (symmetric):
$$\Sigma_{ij}=E[(X-\mu)(X-\mu)^T]$$
The covariance matrix is positive semidefinite: for every $a \in R^d$,
$$a^T \Sigma a = Var(a^T X) \geq 0$$
since $a^TX$ is a scalar random variable (variance is non-negative)

