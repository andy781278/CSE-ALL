Gradient Descent is good at finding local minima, like very slippery sledge going down the steepest direction they reach a dip, but that doesn't have to be the lowest dip, also no momentum, but otherwise it's the same.

$w_0=0,t=0$
 $\text{while } \nabla L(w_t) \not\approx 0:$
- $w_{t+1}=w_t-\eta_t\nabla L(w_t)$
- $t=t+1$

where $\eta_t$ is the step size at time $t$
- if $\eta_t$ is too small, it will be very slow, and not much progress
- if $\eta_t$ is too big, then it will overshoot, and diverge

> [!info] In order words
> pick an arbitrary $w$, and repeat until w converges: find w' close to w such that the Loss function of w' is lower, then set w to w'.
> We use the derivative to pick the direction of where this w' is
> We use the gradient to find w' for more than 1 variable cases

How do we pick $\eta_t$?
#### Line Search
$\eta_t=\underset{\alpha > 0}{argmin} \ L(w_t-\alpha\nabla L(w_t))$
pick the $\alpha$ that gives the lowest Loss function output, and that's the step size


### Gradient Descent
$w_{t+1}=w_t-\eta_t\sum_{i=1}^n\nabla l(w_t;x^{(i)},y^{(i)})$

### Stochastic Gradient Descent
update the $w$ based on just 1 point instead of using the entire data set.
$w^{(t+1)}=w^{(t)}-\eta_tg^{(t)}$
where $g^{(t)}=\nabla l(x_t,y_t;w^{(t)})$
Different variants to SGD:

#### Momentum
Accumulate gradients. For $g^{(t)}$ as above, and $v^{(0)}=0$
$$v^{(t)}=\mu v^{(t-1)}+\eta_t g^{(t)}$$
$$w^{(t+1)}=w^{(t)}-v^{(t)}$$
#### AdaGrad
Different learning rate for each parameter, automatically tuned
$$w_j^{(t+1)}=w_j^{(t)}-\frac{\eta}{\sqrt{\sum_{t'<t}(g_j^{(t')})^2+\epsilon}}g_j^{(t)}$$


### Mini-batch Stochastic Gradient Descent
Instead of a single point at a time, we get a subset batch B and use B data for a single w at once, this is because modern GPUs are better at parallel computing
$w_{t+1}=w_t-\eta_t\sum_{(x,y)\in B}\nabla l(w_t;x,y)$

