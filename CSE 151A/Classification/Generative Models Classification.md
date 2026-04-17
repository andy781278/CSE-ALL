![[Pasted image 20260406000232.png]]
The learning process: Fit a probability distribution to each class (sequence of the same output)
To classify a new point: Which distribution does the new output belong to

Each example (sample data point) consists of two random variables
**Feature**: Random Variable X
**Label**: Random Variable Y

### 1 Variable Classification
![[Screen Shot 2026-04-09 at 5.13.17 PM.png]]
For each unique output (class) y, we have
- probability of that class y, called $\pi_y=P(Y=y)$ 
	- This gives the height of the distribution
- distribution of data in class y, called $P_y(x)=P(X=x|Y=y)$
	- This gives the location and width of the distribution

Overall Joint Distribution:
$$P(x,y)=P(X=x|Y=y)=P(Y=y)P(X=x|Y=y)=\pi_y P_y(x)$$

Dividing everything by $P(x)$ and using Baye's Formula,
$$P(Y=y|X=x)=\frac{P(Y=y)P(x|Y=y)}{P(x)}=\frac{\pi_yP_y(x)}{P(x)}$$

to get the $P_y(x)$, we use a gaussian distribution $N(\mu,\sigma^2)$ with mean $\mu$ and variance $\sigma^2$, it follows the density function
$$p(x)=\frac{1}{\sqrt{2\pi\sigma^2}}exp(-\frac{(x-\mu)^2}{2\sigma^2})$$

#### Classifying 1 Variable
to classify a new x: pick the label y with the **largest** $P(x,y)$ or $\pi_y P_y(x)$ or $P(x|y)P(y)$
- get $\pi_y$  or $P(y)$ by dividing the number of data with label y with the total data points
- get $P_y(x)$ or $P(x|y)$ by using the gaussian distribution density function.

### 2 Variable  Classification
![[Screen Shot 2026-04-09 at 5.13.39 PM.png]]
Now each class has:
- mean $(\mu_1,\mu_2) \in \mathbb{R}^2$ where $\mu_1=E(X_1)$ and  $\mu_2 = E(X_2)$
- covariance matrix $\Sigma = \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix}$
density function:
$$p(x_1,x_2)=\frac{1}{2\pi|\Sigma|^{1/2}}exp(-\frac{1}{2}\begin{bmatrix} x_1-\mu_1 \\ x_2-\mu_2 \end{bmatrix}^T \Sigma^{-1} \begin{bmatrix} x_1-\mu_1 \\ x_2-\mu_2 \end{bmatrix})$$
### Multivariable Classification
- mean: $\mu \in \mathbb{R}^d$
- covariance matrix: $d \times d$ matrix $\Sigma$
density function:
$$p(x)=\frac{1}{(2\pi)^{d/2}|\Sigma|^{\frac{1}{2}}}exp(-\frac{1}{2}(x-\mu)^T\Sigma^{-1}(x-\mu))$$
quadratic function of x:
$$\underset{ij}{\Sigma}S_{ij}(x_i-\mu_i)(x_j-\mu_j)=(x-\mu)^T \Sigma^{-1}(x-\mu)$$
#### Classifying Multivariable
to classify point x, pick the j that **maximizes** $\pi_j P_j(x)$ where
- $\pi_j$ is probability of a specific class $\pi_1,...,\pi_k$
- $P_j$ is the normal distribution of that class $P_1=N(\mu_1,\Sigma_1),...,P_k=N(\mu_k,\Sigma_k)$

equivalently, use the quadratic function
$$f_j(x)=log(\pi_j,P_j(x))$$
to classify point x, pick the largest $f_j(x)$

Special case: $\Sigma_1=...=\Sigma_k$, then the boundaries are linear