
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
6. Find the rejection region, $|Z|>z_{\alpha/2}$ for two sided, $Z>z_a$ or $Z< -z_a$ for one sided
7. Compute $Z_{observed}$
8. Does Z fall in the rejection region? Make conclusion
9. Compute p-value

#### Extra Questions
1. Get $\beta$