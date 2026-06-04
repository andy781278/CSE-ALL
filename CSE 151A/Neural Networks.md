Feed Forward Neural Networks
![[Pasted image 20260528173420.png]]

Each hidden node is computed from a linear combination of its parents (input)
$h=\sigma(w_1z_1+w_2z_2+...+w_mz_m+b)$
$\sigma$ is a nonlinear activation function

There are many activation functions:
![[Pasted image 20260528173847.png]]

The more hidden layers we have, the more complicated functions we can describe.

Complexity of NN is defined by:
1. Width: number of input units
2. number of units in each hidden layer
3. density of connection, two layers of width n
	- dense = $O(n^2)$ connections
	- sparse = $O(n)$ connections

> [!info] How to know how much of each is needed
> Input: Dimension or however much input input
> Output: how many info do you need, or how ever much output
> Hidden layers: each is a new line/curve, more means more precise/curvy, less makes it flatter, overdoing it makes it worse

Let $f:\mathbb{R}^d\rightarrow\mathbb{R}$ be any continuous function
There is a NN with one hidden layer that approximates f arbitrarily well
- You can either have 1 very dense layer, or multiple moderate layers

### Training via Backpropagation
Say we have k labels and W as parameter so of the net
For any input x, net computes probabilities of each label using SoftMax
$\text{softmax}(\mathbf{y})_i = \frac{e^{y_i}}{\sum_{j=1}^{K} e^{y_j}}=P_W(y / label=i|x)$

Loss function / cross-entropy:
$L(W)=-\sum_{i=1}^nlnP_W(y^{(i)}|x^{(i)})$

We're now going to try and minimize this Loss function. Remember that convex makes it easier to find minimum of L, since we can use gradient descent.

Actually, we don't have to worry about it, since local minima is good enough.

![[Pasted image 20260528180335.png]]
![[Pasted image 20260528180427.png]]

The first pass through the layers from input to output gives you the output, then we go backwards, called Back Propagation, so we can see all the errors to find the loss.


 The distribution of inputs to a particular layer of the net can change dramatically during training: Internal Covariate Shift. To mitigate this, we normalize the input:
 - Compute man $m_i^{(B)}$ and variance $v_i^{(B)}$ of each $x_i$ in the mini-batch
 - replace $x_i$ by
$$x_i'=\frac{x_i-m_i^{(B)}}{\sqrt{v_i^{(B)}+\epsilon}}$$
before feeding it into the next layer. This $x_i'$ has mean 0 and variance around 1. The $\epsilon$ is in case the variance is 0 and it's dividing by 0, it can be any padding.

