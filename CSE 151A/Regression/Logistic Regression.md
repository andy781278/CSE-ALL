For classifying binary outputs. This isn't really a regression, more of a classification, since the end result is a prediction of either one or the other. But the internal process does use a linear function to determine the prediction.

Given a set of data points $(x,y), x\in \mathbb{R}$ and $y \in \{-1,1\}$
return a classifier that also gives probability $P(y=1|x)$

This classifier is the probability of choosing output 1 given the data point. Now if this probability is 50% or more, it's safe to say that the best course of action is to make those regions guess output 1 for all future data points. And for less than 50%, the output would be -1.

We'll need to squish our familiar $\vec w\cdot \vec x$ from linear regression, where $\vec w = \{b,x_1,x_2,...,x_n\}$

We'll need the sigmoid function, or the squashing function to squash the function into a probability shape.
$s(z)=\frac{1}{1+e^{-z}}$
![[Pasted image 20260426202621.png]]
Model:
$$P(y=1|x)=\frac{1}{1+e^{-(\vec w\cdot \vec x)}}$$
Theoretically, most of the y=-1 data points would be to the left of the y=0.5, and most of the y=1 data points would be to the right. If we find where that middle is, we find our classifier.

More generalized:
$$P_{\vec w}(y=y|x)=\frac{1}{1+e^{-y(\vec w\cdot \vec x)}}$$

How do we use this?
pick the $w\in\mathbb{R}^d$ and $b\in\mathbb{R}$ that maximizes:
$$\prod_{i=1}^nP(y^{(i)}|x^{(i)})$$
$$\prod_{i=1}^n\frac{1}{1+e^{-y(\vec w\cdot \vec x)}}$$
or minimizes:
$$L(\vec w)=\sum^{n}_{i=1}ln(1+e^{-y^{(i)}(\vec w\cdot x^{(i)})})$$

Unlike linear regression, it is super hard to minimize the loss function, because if you take the gradient, you're gonna get a non-linear function of w that can't be isolated algebraically. Therefore, there is no closed form solution for $\vec w$.

Instead, we'll use optimization, we'll use gradient descent. It works because logistic regression only has 1 minima, like a parabola.

To start, set $w_0=0$
For $t=0,1,2,...$ until convergence:
$$w_{t+1}=w_t-\eta\nabla(\sum_{i=1}^n-logP(y^{(i)}|x^{(i)}))$$
where $\eta$ is the step size

### Example
sort reviews into good or bad review
Bag-of-words: vectoral representation of text sentences
- $x=(x_1,x_2,...,x_{|V|})$
- where $x_i$ is the number of times the ith word appears in the sentence
Code positive as +1 and negative as -1.
![[Pasted image 20260426224046.png]]
Final test error: 0.21
