Two models for learning
1. Statistical setting
Train/Test data are drawn from the same dist. Any classifier consistent with data suffices; $risk \leq \epsilon$ after $(1/\epsilon)log|H|$ labeled points
2. Adversarial setting
data presented one at a time. Picking a consistent classifier can yield $O(T)$ regret at time T
3. Adversarial (halving)
regret at most $log|H|$ at any time T

#### Online Learning
At each time $t = 1,2,...$:
- Nature (adversary) selects $x_t\in \chi$
- Learner predicts (possibly randomized) $\hat y_t \in Y$ 
- Nature announces label  $y_t \in Y$
- Learner incurs loss $l(\hat y_t, y_t)$

Goal: do almost as well as the best single model in class H.
Regret at time T:
$$R_T=\sum_{t=1}^Tl(\hat y_t,y_t)-\underset{h\in H}{inf}\sum_{t=1}^Tl(h(x_+t),y_t)$$
Learning succeeds if $R_T=o(T)$

### Example: Perceptron
$\chi  = \mathbb{R}^d$, $Y=\{1,2,3,...,k\}$
- Linear scores
- Prediction
- Initialize $w_j=0$
- Repeat forever: get x; predict $\hat y$; get label y; if $\hat y \neq y$
	- for correct label $y:w_y\leftarrow w_y+x$
	- for predicted label $\hat y:w_{\hat y}\leftarrow w_{\hat y}-x$

#### Generalization Guarantee

![[Pasted image 20260603220010.png]]

![[Pasted image 20260603220057.png]]

$\sum_{j=1}^k w_j \cdot w_j^*\rightarrow x\cdot w_y^*-xw^*_{\hat y}\geq \gamma$

$\sum_{j=1}^k ||w_j||^2$ increases by at most $2R^2$ per mistake

![[Pasted image 20260603220855.png]]

### Separable Case
Suppose H contains a perfect classifier $h^*$ with $h^*(x)=y$ on all $(x,y)$

Suppose |Y|=2 and H is finite
**Halving Algorithm** at time t:
- $H_t\subseteq H$: classifiers consistent with $(x_1,y_1),...,(x_{t-1},y_{t-1})$
- Predict on x by majority vote of $\{h(x):h\in H_t\}$
Theorem: The halving algorithm makes at most $log_2 |H|$ mistakes in total

If we predict using the majority rule and make a mistake, then $|M|\geq \frac{P_t}{2}$
$P_{t+1}\leq\frac{P_t}{2},N=|P_0|=|H|$
Total number of mistakes $\leq log_2|H|$

### Non-separable Case
No expert is perfect, we don't know the # of mistakes of the best expert
![[Pasted image 20260603233028.png]]

