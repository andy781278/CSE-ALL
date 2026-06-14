Given a covariance matrix $\Sigma$, the Mahalanobis Distance from x to $\mu$ is
$$d_\Sigma(x,\mu)=\sqrt{(x-\mu)^T\Sigma^{-1}(x-\mu)}$$

This is better than Euclidean distance for machine learning because
- it puts directions of high variance at a lower weight
- it puts direction of low variance at a higher weight

$\Sigma^-1$ defines a metric on $\mathbb{R}^d$

The level sets $\{x:d\Sigma(x,\mu)=c\}$ are ellipsoids aligned with the eigenvectors of $\Sigma$

When $\Sigma=I_d$, Mahalanobis Distance = Euclidean distance

In the most common covariance case, where $\Sigma_1=\Sigma_2=\Sigma_3$, the decision boundary is the Mahalanobis distance to $\mu_1$ and $\mu_2$ satisfy a linear relation