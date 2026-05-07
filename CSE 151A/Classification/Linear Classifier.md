We want to classify binary outputs, $\{-1,1\}$, and we're given a linear line in $\mathbb{R}^d$

$w\in\mathbb{R}^d, b\in\mathbb{R}$
Decision Boundary: $w\cdot x+b=0$
On point x, predict label $sign(wx+b)$, or whether the output of the linear function is positive or negative

Classifier is correct if output $>0$

What about loss function?
Let's say that if output > 0, then loss is 0
but otherwise, $L_{w^i}(x^i)=y(w^ix^i)$

we use stochastic gradient descent to find the minimum loss, we called this the perceptron algorithm

##### Perceptron Algorithm
- initialize w=0 and b=0
- Keep cycling through training data (x,y):
	- if $y(wx+b\leq 0)$ or point misclassified:
		- w=w+yx
		- b=b+y

If the training data is separable, then the perceptron can easily find a linear classifier with zero training error, it will converge within a finite number of steps, the number of iterations can be bounded in terms of the margin, roughly, a measure of the space between the two classes
![[Pasted image 20260507021842.png]]

##### Maximal Margin Separator
Given training data $(x^{(1)},y^{(1)}),...,(x^{(n)},y^{(n)})\in \mathbb{R}^d\times\{-1,+1\}$
Find $w\in\mathbb{R}^d$ and $b\in\mathbb{R}$ such that:
$y^{(1)}(wx^{(i)})\geq 1$ for all $i$
we wan to maximize the margin $\gamma$, can show $\gamma=1/||w||$
equivalently: find w wiht the smallest norm $||w||$ such that $\forall (x,y): t(wx+b)\geq1$

We want to maximize the margin because that gives us better predictions against unseen data

![[Pasted image 20260507033435.png]]

Maximum-margin Linear Classifier or the hard-margin support vector machine
as long as the data is linearly separable
$$\underset{w\in\mathbb{R}^d,b\in\mathbb{R}}{min}||w||^2$$
such that $y^{(i)}(wx^{(i)}+b)\geq1$ for all i from 1 to n

##### Support Vectors
Support vectors are training points exactly on the margin
$w=\sum_{i=1}^n \alpha_i y^{(i)}x^{(i)}$ is a function of just the support vectors

##### Non-separable
This version allows each data point $x^{(i)}$ some slack $\xi_i$
$$\underset{w\in\mathbb{R}^d,b\in\mathbb{R},\xi\in\mathbb{R}^d}{min}||w||^2+C\sum_{i=1}^n\xi_i$$
such that $y^{(i)}(wx^{(i)}+b)\geq1-\xi_i$ for all i from 1 to n, $\xi\geq 0$
![[Pasted image 20260507035112.png]]

Parameter C manages tradeoff between margin and slack
- The more the margin, the more confident/accurate the model
- The more the slack, the more you tolerate misclassified points to enlarge the margin.

The more the C, the stricter the model, so lower C is more lenient to errors, so margin will grow.

To find the best C, test it with a logarithmic range to find the lowest error. We can also use 5-fold cross validation