	Exponential Distribution

# Continuous
$$
PDF: f_X(x)=\begin{cases}
\lambda e^{-\lambda x} & \text{if } x \geq 0 \\
0 & \text{otherwise}
\end{cases}
$$
where $\lambda > 0$ is called the **rate parameter**

$$supp(X)=[0,\infty)=\{x:x\geq0\}$$
$$CDF: F_X(x)=P(X\leq x)=\begin{cases}
1- e^{-\lambda x} & \text{if } x \geq 0 \\
0 & x<0
\end{cases}$$
$$E(X)=\frac{1}{\lambda}$$
$$Var(X)=\frac{1}{\lambda^2}$$
