We want to classify binary outputs, $\{-1,1\}$, and we're given a linear line in $\mathbb{R}^d$

$w\in\mathbb{R}^d, b\in\mathbb{R}$
Decision Boundary: $w\cdot x+b=0$
On point x, predict label $sign(wx+b)$, or whether the output of the linear function is positive or negative

Classifier is correct if output $>0$

What about loss function?
Let's say that if output > 0, then loss is 0
but otherwise, $L_{w^i}(x^i)=y(w^ix^i)$

we use stochastic gradient descent to find the minimum loss, we called this the perceptron algorithm

### Perceptron Algorithm
- initialize w=0 and b=0
- Keep cycling through training data (x,y):
	- if $y(wx+b\leq 0)$ or point misclassified:
		- w=w+yx
		- b=b+y

If the training data is separable, then the perceptron can easily find a linear classifier with zero training error, it will converge within a finite number of steps, the number of iterations can be bounded in terms of the margin, roughly, a measure of the space between the two classes
![[Pasted image 20260507021842.png]]

##### Dual Form:
- initialize a=0 and b=0
- Keep cycling through training data $(x^{(i)},y^{(i)})$:
	- if point misclassified:
		- $a_i=a_i+1$
		- $b=b+y^{(i)}$

#### Multiple Classes
So far, we have been doing binary classification with +1 or -1, based on the sign of the w after we're done training it

Now suppose we have k classes $y=\{1,2,..,.k\}$
each class with their own linear function, highest value wins:
$w_1\cdot x + b_1, w_2\cdot x + b_2, ..., w_k\cdot x + b_k$

**Setting**: $\mathcal{X} = \mathbb{R}^d$ and $\mathcal{Y} = \{1, 2, \ldots, k\}$

**Model**: $w_1, \ldots, w_k \in \mathbb{R}^d$ and $b_1, \ldots, b_k \in \mathbb{R}$

**Prediction**: On instance $x$, predict label $\arg\max_j (w_j \cdot x + b_j)$

**Learning**: Given training set $(x^{(1)}, y^{(1)}), \ldots, (x^{(n)}, y^{(n)})$:
```
init w1=...=wk=0, b1=...=bk=0
while some training point is misclassified:
	for correct label y:
		wy=wy+x
		by=by+1
	for predicted label py: 
		wpy=wpy-x
		bpy=bpy-1
```


### Support Vector Machine (SVM) (Maximal Margin Separator)
Given training data $(x^{(1)},y^{(1)}),...,(x^{(n)},y^{(n)})\in \mathbb{R}^d\times\{-1,+1\}$
Find $w\in\mathbb{R}^d$ and $b\in\mathbb{R}$ such that:
$y^{(1)}(wx^{(i)})\geq 1$ for all $i$
we wan to maximize the margin $\gamma$, can show $\gamma=1/||w||$
equivalently: find w with the smallest norm $||w||$ such that $\forall (x,y): t(wx+b)\geq1$

We want to maximize the margin because that gives us better predictions against unseen data

![[Pasted image 20260507033435.png]]

Maximum-margin Linear Classifier or the hard-margin support vector machine
as long as the data is linearly separable
$$(PRIMAL)\underset{w\in\mathbb{R}^d,b\in\mathbb{R}}{min}||w||^2$$
such that $y^{(i)}(wx^{(i)}+b)\geq1$ for all i from 1 to n

- This is a convex optimization problem
	- Convex objective function
	- Linear constraints

##### Support Vectors
Support vectors are training points exactly on the margin
$w=\sum_{i=1}^n \alpha_i y^{(i)}x^{(i)}$ is a function of just the support vectors

##### Non-separable
This version allows each data point $x^{(i)}$ some slack $\xi_i$
$$(PRIMAL)\underset{w\in\mathbb{R}^d,b\in\mathbb{R},\xi\in\mathbb{R}^d}{min}||w||^2+C\sum_{i=1}^n\xi_i$$
such that $y^{(i)}(wx^{(i)}+b)\geq1-\xi_i$ for all i from 1 to n, $\xi\geq 0$
![[Pasted image 20260507035112.png]]

$\xi^{(i)} = \max(0, 1 - y^{(i)}(w \cdot x^{(i)} + b))$

Parameter C manages tradeoff between margin and slack
- The more the margin, the more confident/accurate the model
- The more the slack, the more you tolerate misclassified points to enlarge the margin.

High C -> Stricter Model -> Tighter Margin, less tolerance for misclassification
Low C -> Looser Model -> Wider Margin, more tolerance more misclassification

To find the best C, test it with a logarithmic range to find the lowest error. We can also use 5-fold cross validation

#### Dual Form

Complementary slackness: At optimality, $w=\sum_i \alpha_i y^{(i)}x^{(i)}$ and $a_i\geq 0 \rightarrow y^{(i)}(wx^{(i)}+b)=1$

$$(DUAL) \ \underset{a\in \mathbb{R}^n}{max} \sum_{i=1}^n a_i - \frac{1}{2}\sum_{i,j=1}^n a_ia_jy^{(i)}y^{(j)}(x^{(i)}x^{(j)}))$$
such that $\sum_{i=1}^n a_i y^{(i)}=0, a\geq 0$

##### Non-separable
$$(DUAL) \ \underset{a\in \mathbb{R}^n}{max} \sum_{i=1}^n a_i - \frac{1}{2}\sum_{i,j=1}^n a_ia_jy^{(i)}y^{(j)}(x^{(i)}x^{(j)}))$$
such that $\sum_{i=1}^n a_i y^{(i)}=0, 0\leq \alpha_i \leq C$
At optimality, $w^*=\sum_{i=1}^na_i^*y_ix_i$
$0<\alpha_i<C \rightarrow y^{(i)}(wx^{(i)}+b)=1$
$\alpha_i=C \rightarrow y^{(i)}(wx^{(i)}+b)=1-\xi_i$

### Comparison with Linear Programming

|            | LP                | SVM                                  |
| ---------- | ----------------- | ------------------------------------ |
| Objective  | $C^Tx$            | $\|w\|^2$                            |
| Constraint | linear $Ax\leq b$ | linear $y^{(i)}(wx^{(i)}+b)\geq 1$   |
| Variable   | $x\geq 0$         | $w\in \mathbb{R}^d, b\in \mathbb{R}$ |


For a soft-margin SVM, 3 types of example data points at optimum

**Non-support Vectors**
$\xi_i=0,\eta_i>0$

**Support Vectors**
$\xi_i=0,\eta_i=0$

**Violating**
$\xi_i>0,\eta_i=0$

#### Multiclass
Model: $w_1, \ldots, w_k \in \mathbb{R}^d$ and $b_1, \ldots, b_k \in \mathbb{R}$

Prediction: On instance $x$, predict label $\arg\max_j (w_j \cdot x + b_j)$

Learning. Given training set $(x^{(1)}, y^{(1)}), \ldots, (x^{(n)}, y^{(n)})$:

$$\min_{w_1, \ldots, w_k \in \mathbb{R}^d,\, b_1, \ldots, b_k \in \mathbb{R},\, \xi \in \mathbb{R}^n} \sum_{j=1}^{k} \|w_j\|^2 + C \sum_{i=1}^{n} \xi_i$$
$$w_{y^{(i)}} \cdot x^{(i)} + b_{y^{(i)}} - w_y \cdot x^{(i)} - b_y \geq 1 - \xi_i \quad \text{for all } i, \text{ all } y \neq y^{(i)}$$
$$\xi \geq 0$$
