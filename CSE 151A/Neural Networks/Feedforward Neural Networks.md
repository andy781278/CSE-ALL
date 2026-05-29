![[Pasted image 20260528173420.png]]

Each hidden node is computed from a linear combination of its parents (input)
$h=\sigma(w_1z_1+w_2z_2+...+w_mz_m+b)$
$\sigma$ is a nonlinear activation function
$\sigma(u) = \begin{cases} u & \text{if u }\geq 0 \\ 0 & \text{otherwise} \end{cases}$

There are many activation functions:
![[Pasted image 20260528173847.png]]

The more hidden layers we have, the more complicated functions we can describe.

Complexity of NN is defined by:
1. Width: number of input units
2. number of units in each hidden layer
3. density of connection, two layers of width n
	- dense = $O(n^2)$ connections
	- sparse = $O(n)$ connections

Let $f:\mathbb{R}^d\rightarrow\mathbb{R}$ be any continuous function
There is a NN with one hidden layer that approximates f arbitrarily well
- You can either have 1 very dense layer, or multiple moderate layers

### Training via Backpropagation
Say we have k labels and W as parameter so of the net
For any input x, net computes probabilities of each label
$P_W(label=j|x)$
Loss function / cross-entropy:
$L(W)=-\sum_{i=1}^nlnP_W(y^{(i)}|x^{(i)})$

We're now going to try and minimize this Loss function. Remember that convex makes it easier to find minimum of L, since we can use gradient descent.

Actually, we don't have to worry about it, since local minima is good enough.

![[Pasted image 20260528180335.png]]
![[Pasted image 20260528180427.png]]

