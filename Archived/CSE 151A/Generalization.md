How do we know if the classifier does good on the training set, it will do good on any tests as well? There's an underlying distribution P that everything follows, how can we find P and have the classifier do good at it?

First out of all, if there's enough data points, then the distribution we make is probably P. The training error also approximately equals to the true error.


3 ways to draw $(x,y)$ from P:
1. Both together: pick (x,y) from P
2. Label first:  y first, then pick x from class conditional x|y
3. Instance first: pick x from its marginal, then pick y from y|x


### Bayes' Optimality

![[Pasted image 20260603182340.png]]
There's a threshold where the predictions are divided up, the distribution will overlap each other, so errors are if the point is from beyond the threshold


### Nonparametric methods to achieve Bayes-optimality
Nonparametric - not using a parameter, so things like Nearest Neighbor, where you can process the data immediately and get a result. Unlike others where you would need an extra variable and find the best value for that variable first before starting.
![[Pasted image 20260603183008.png]]

![[Pasted image 20260603183333.png]]

1NN doesn't converge to Bayes
 The rate of convergence depends on dist D

### Parametric methods to achieve Bayes-optimality

![[Pasted image 20260603183547.png]]
We only have $\hat R$ gathered from data, we're trying to see if its good enough

![[Pasted image 20260603183900.png]]

![[Pasted image 20260603205846.png]]
