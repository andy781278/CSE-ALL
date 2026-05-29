Say we have data in $\mathbb{R}$, how do we find the center of the distribution?

1. Mean
2. Median
3. min + max / 2

Stability = How much the statistic depend on the sample?

$\alpha$ is stable if the distribution of $\alpha(x_1,...,x_n)$ is concentrated (has small variance)

**Bootstrap**: Given n samples s, generate s' using random sampling with replacement. Basically, split sample into many parts, pretending they're independent from each other. Then we will use these samples and see if they're very different from each other, that can tell you how stable it is.

How do we improve stability?

### Bootstrap Aggregation / Bagging

Generate trees using bootstrap samples, predict using the majority

### Random Forests

Given a data set S of n labeled points:
- For t=1 to T:
	- Choose n' points randomly with replacement from S
	- fit a decision tree $h_t$ to these points
		- At each node restrict one of k features chosen at random

Example settings:
- n'=n, k=\sqrt{d} for d dimensional data

Final predictor: majority vote of h1...hT

