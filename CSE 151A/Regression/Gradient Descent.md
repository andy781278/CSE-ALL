Gradient Descent is good at finding local minima, like very slippery sledge going down the steepest direction they reach a dip, but that doesn't have to be the lowest dip, also no momentum, but otherwise it's the same.

To start, set $w_0=0$
For $t=0,1,2,...$ until convergence:
$$w_{t+1}=w_t+\eta\sum_{i=1}^ny^{(i)}x^{(i)}P(y^{(i)}|x^{(i)})$$