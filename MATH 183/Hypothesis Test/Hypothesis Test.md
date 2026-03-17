
You find out whether you reject the Null Hypothesis in favor of the Alternative Hypothesis, or you are not sure (unable to reject Null Hypothesis)

Accepting the $H_a$ means you have sufficient evidence favor of it

##### Null Hypothesis ($H_0$)
- encapsulates the universe

##### Alternative Hypothesis ($H_a$)
- captures the main claim we want to investigate


### Prerequisites
1. They must be made about the same parameter
2. They must include only population parameters
	1. no statistics with the little hats, i.e. $\hat\mu$
3. Mutually Exclusive, they can't overlap in territory
4. $H_0$ must be smaller than $H_a$
5. $H_0$ must be an equality
6. $H_a$ must be an inequality
7. Exhaustive, together, $H_a$ and $H_0$ must cover all the possibilities


### Problem Template
1. State assumptions
	1. Distribution for data, are samples independent, is n large enough for CLT
2. Identify population parameter $\theta$ and sample estimate $\hat\theta$
3. Write $H_0$ and $H_a$
4. Find sampling distribution under $H_0$, use CLT to get $\hat\theta\sim N(a,b)$
5. Turn $\hat\theta$ into a Z statistic, following N(0,1)
	1. Z statistic describes how many stand errors the sample result is from $H_0$
	2. $Z=\frac{\hat\theta-\theta_0}{SE}$
6. Find the rejection region
	1. everything not in CI
	2. $\bar X > \mu_0 + z_\alpha * SE$ $[\mu_0 + z_\alpha * SE,\infty)$ left tail lower
	3. $\bar X < \mu_0 - z_\alpha * SE$ $[-\infty, \mu_0 - z_\alpha * SE)$ right tail upper
	4. $\bar X < \mu_0 - z_{\alpha/2} * SE$ or $\bar X > \mu_0 + z_{\alpha/2} * SE$
7. Compute $Z_{observed}$
8. Does Z fall in the rejection region? Make conclusion
9. Compute p-value
	1. p-value is the probability of seeing a Z at least as extreme as the observed Z, assuming $H_0$.
	2. p-value is also the percentage of total area after Z
	3. p-value depends on right tail, left tail, or two tail
		1. right tail: $P(Z>Z_{observed})$
		2. left tail: $P(Z<Z_{observed})$
		3. two tail: $2P(Z>Z_{observed})$
	4. If p<a, reject $H_0$
	5. a larger p-value means more area covered
#### Extra Questions
1. Get $\beta$
2. Get power
	1. $\text{Power} = P\left(Z > z_{\alpha} - \frac{\theta_1 - \theta_0}{\text{SE}(\hat\theta)}\right)$
	2. $n \geq \frac{\sigma^2 (q_\alpha + q_\beta)^2}{\delta^2}$