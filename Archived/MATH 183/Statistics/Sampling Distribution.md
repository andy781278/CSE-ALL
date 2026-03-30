You take samples $X_1,X_2,...,X_n$, n samples

these sample follow a random variable function that is unknown

We want to understand $\theta$, since it is some kind of unknown population parameter, we can estimate it via
$$\hat{\theta} \equiv \hat{\theta}(X_1,X_2,...,X_n)$$
from the samples we collect, $\hat{\theta}$ is the statistic

$\hat{p}$ represents the probability inferenced by the samples, represented by the hat, meaning unsure, but backed by the population.

It is impossible to know the true values you're looking for, so instead we give a range of values in which the true value p must be inside the range.

risk preference $\alpha$ specifies $\hat{p}_{\alpha,low}, \hat{p}_{\alpha,high}$

$$P(\hat{p}_{\alpha,low}\leq p \leq \hat{p}_{\alpha,high})=1-\alpha$$
p is fixed, but $\hat{p}_{\alpha,low}, \hat{p}_{\alpha,high}$ is not.