
### Boosting
We have many classifiers, can we combine them to get the best classifier? Or at least get a better one than all the individual ones

#### Weak Learner
a Weak Classifier is one that is marginally better than random guessing. A learning algorithm that can consistently generate such classifiers are called weak learners.

$(x_1,y_1,w_1),(x_2,y_2,w_2),...$

$$err_w(h)=\sum_{i=1}^n w_i L(h(x_i)\neq y_i) \leq \frac{1}{2}-\epsilon$$

```
Initialize all points equal weight w
Repeat for t=1,2,...:
	Feed weighted data set to the weak learner, get back a week calssifier ht
	Reweight data to put more emphasis on points that ht gets wrong
combine all these hts linearly
```

### AdaBoost
Data set $(x^{(1)},y^{(1)}),...,(x^{(n)},y^{(n)})$, labels $y^{(i)}\in \{-1,+1\}$

- Initialize $D_1(i)=1/n$ for all $i=1,2,...,n$
- For $t=1,2,...,T$:
	- Give $D_t$ to weak learner, get back some $h_t:X\rightarrow [-1,1]$
	- Compute $h_t$'s margin of correctness:
$$r_t=\sum_{i=1}^n D_t(i) y^{(i)}h_t(x^{(i)})\in[-1,1]$$
$$\alpha_t=\frac{1}{2}ln\frac{1+r_t}{1-r_t}$$
	- Update weights: $D_{t+1}(i) \propto D_t(i) exp(-\alpha_t y^{(i)}h_t(x^{(i)}))$
- Final classifier: $H(x)=sign(\sum_{t=1}^T \alpha_t h_t(x))$

![[AdaboostToWeakClassifier.excalidraw]]

If on each round t, weak learner returns $h_t$ whose error on the time-t weighted data distribution is $\leq 1/2-\gamma$
Then after T rounds, the training error of the combined rule:
$$H(x)=sign(\sum_{t=1}^T\alpha_t h_t(x))$$
is at most $e^{-\gamma^2T/2}$

This is basically saying that error will decrease exponentially as long as the weak learner is doing its job.

But training error is not testing error, which is what we want. Although training error goes down, at a certain point it will start to overfit, and cause testing error to grow. That is what we thought was true, but it actually doesn't happen. It instead keeps dropping, although at a slower rate than training error.

Boosting looks for the linear classifier f that minimizes the exponential loss
$$\frac{1}{n}\sum_{i=1}^n e^{-y^{(i)}f(x^{(i)})}$$
