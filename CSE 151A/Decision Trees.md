![[Pasted image 20260527062541.png]]

### Classification
We need to classify some labels, we can do so comprehensibly by splitting the data into pure sets that contains only 1 label, then recursively purify the data until we can go down a decision tree and classify based on the decisions.

How to build?
Greedy Algorithm: Build it top down
- Start with single node containing all data points
- Repeat
	- Look at all current leaves and possible splits
	- choose the split that decreases the uncertainty in prediction the most

To do that, we need a way to measure uncertainty in prediction
There are 3 main ways to measure uncertainty:
Suppose there are k classes with probabilities $p_1,p_2,...,p_k$
![[Pasted image 20260527063300.png]]

Let's say u(S) is a function with input data set S that outputs you an uncertainty score
![[Pasted image 20260527063537.png]]

Then the new uncertainty is:
$$(u(S)-(p_L u(S_L)+p_R u(S_R)))\cdot |S|$$

where $u(S)$ is the uncertainty of S, $p_L u(S_L)+p_R u(S_R)$ is the uncertainty of the child nodes, and it's all scaled by S

A smaller $p_L u(S_L)+p_R u(S_R)$ means a better split, since the children have less uncertainty

Apparently finding the best split is very efficient

### Overfitting
If the data is too complicated, the decision tree is going to be very long, and it won't really capture any patterns, and is just memorizing the training data. Alternatively, the tree can be too sharp and ragged, and it fails to capture a more smooth pattern.

Usually, this is the downside to using Decision Trees, they're pretty good at everything else

Overfitting happens when (# decision nodes / # training example) that's too large

So how do we know when to stop branching so we don't overfit?
We do overfit, then we prune shitty splits, like a gardener cutting off rogue leaves to make the tree smaller but prettier

