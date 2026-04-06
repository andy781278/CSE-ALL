![[Pasted image 20260406000232.png]]
The learning process: Fit a probability distribution to each class (sequence of the same output)
To classify a new point: Which distribution does the new output belong to

Each example (sample data point) consists of two random variables
**Feature**: Random Variable X
**Label**: Random Variable Y

For each unique output (class) y, we have
- probability of that class y, called $\pi_y=P(Y=y)$ 
	- This gives the height of the distribution
- distribution of data in class y, called $P_y(x)=P(X=x|Y=y)$
	- This gives the location and width of the distribution

Overall Joint Distribution:
$$P(x,y)=P(X=x|Y=y)=P(Y=y)P(X=x|Y=y)=\pi_y P_y(x)$$

to classify a new x: pick the label y with the **largest** $P(x,y)$ or $\pi_y P_y(x)$

Dividing everything by $P(x)$ and using Baye's Formula,
$$P(Y=y|X=x)=\frac{P(Y=y)P(x|Y=y)}{P(x)}=\frac{\pi_yP_y(x)}{P(x)}$$

to get the $P_y(x)$, we use a gaussian distribution $N(\mu,\sigma^2)$ with mean $\mu$ and variance $\sigma^2$, it follows the density function
$$p(x)=\frac{1}{\sqrt{2\pi\sigma^2}}exp(-\frac{(x-\mu)^2}{2\sigma^2})$$

