 #Probability
Used for **Ending Conditions** where a condition requires something to only stop when it succeeds for the first time

Let X be the number of tries until it succeeds for the first time, including the succeeding time
Let P() be function of probability of succeed
Let A be succeeding first try
Using [[Law of Total Expectation]], 
$$E(X) = E(X|A)P(A) + E(X|\overline A)P(\overline A)$$
$P(A)=p, P(\overline A)=1-p,E(X|A)=1,E(X|\overline A) = 1+E(X)$

#### $$E(X) = \frac{1}{p}$$

I'm not sure what this is:
$$\sum_{k=1}^\infty (1-p)^{k-1}p$$