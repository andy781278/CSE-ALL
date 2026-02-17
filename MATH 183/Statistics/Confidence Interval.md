Given data $X_1,X_2,...,X_n$ observed iid from a unknown distribution $D(\theta)$

Let $\hat{\theta} \equiv \hat{\theta}(X_1,X_2,...,X_n)$ be the sampling distribution

For $\alpha \in (0,1)$, the $(1-\alpha)$ confidence interval is given by $C(\alpha,\theta)$

$$C(\alpha, \theta)=[l_\alpha,u_\alpha]$$
where l and u are low and high points,

$1-\alpha$ is the confidence level


Example: Bin(n,p)
![[Screen Shot 2026-02-12 at 2.41.42 PM.png]]
![[Screen Shot 2026-02-12 at 2.45.29 PM.png]]
![[Screen Shot 2026-02-12 at 2.46.12 PM.png]]
![[Screen Shot 2026-02-12 at 2.46.35 PM.png]]
We find la and ua with a calculator online


$$CI(\alpha,\theta)=[\hat{\theta}+q_{1-\alpha /2}* SE(\hat{\theta}),\hat{\theta}+q_{\alpha /2}* SE(\hat{\theta}]$$
$$CI(\alpha,\theta)=[\hat{\theta}-q_{\alpha/2}* SE(\hat{\theta}),\hat{\theta}+q_{\alpha /2}* SE(\hat{\theta}]$$
$$CI(0.05,p)=\hat{p} \pm 1.96* SE(\hat{p})$$

![[Screen Shot 2026-02-12 at 3.06.24 PM.png]]