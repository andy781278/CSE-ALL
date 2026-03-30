# $$ X \textasciitilde N(\mu,\sigma^2)$$
A random variable $X \textasciitilde N(\mu,\sigma^2)$ is said to follow a normal distribution where 𝜇 is the **mean** and 𝜎 is the **standard deviation**. Its probability density function (PDF) is given by

$$f_X(x)=\frac{1}{\sqrt{2\pi\sigma^2}}exp(-\frac{1}{2}(\frac{x-\mu}{\sigma}))^2$$
$$supp(X)=R$$
$$E(X)=\mu$$


$$Var(X)=\sigma^2$$
$$Var(X_1,X_2,...,X_n) | \hat{\sigma}^2 = \frac{1}{n-1}\sum_{i=1}^n (X_i-\overline X)^2$$

$$CDF: F_Z(x)=P(Z\leq x)=\Phi$$
Let $X \textasciitilde N(\mu _X,\sigma_X^2)$,$Y\textasciitilde N(\mu_Y,\sigma_Y^2)$, and $X \perp Y$, then for all $a,b \in R$
$$aX+bY \textasciitilde N(a\mu_X,b\mu_Y,a^2\sigma_X^2+b^2\sigma_Y^2)$$

$$aX \textasciitilde N(a\mu_X , a^2\sigma_X^2)$$
$$aX+b\textasciitilde N(a\mu_X+b,a^2\sigma_X^2)$$
