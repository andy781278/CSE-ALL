![[Pasted image 20260406000232.png]]
The learning process: Fit a probability distribution to each class (sequence of the same output)
To classify a new point: Which distribution does the new output belong to

Each example (sample data point) consists of two random variables
**Feature**: Random Variable X
**Label**: Random Variable Y

For each unique output (class) y, we have
- probability of that class y, called $\pi_y=P(Y=y)$ 
- distribution of data in class y, called $P_y(x)=P(X=x|Y=y)$

Overall Joint Distribution:
$$P(x,y)=P(X=x|Y=y)=P(Y=y)P(X=x|Y=y)=\pi_y P_y(x)$$

to classify a new x: pick the label y with the largest P(x,y), so loop the x over all classes of y, $y_i$, and find the largest $P(x,y_i)$ as $y_i$ goes across all classes of y

Dividing everything by $P(x)$ and using Baye's Formula,
$$P(Y=y|X=x)=\frac{P(Y=y)P(x|Y=y)}{P(x)}=\frac{\pi_yP_y(x)}{P(x)}$$

