$$x''(t)=f(x(t),x'(t),t)$$
acceleration $x''$ is deterministic function of position $x$, velocity $x'$, and time $t$
This is an ordinary differential equation

$x(t) = -4.9t^2+v_0t+x_0$
is a closed form solution of the ODE, with initial values of $x''(t)=-9.8, x'(0)=v_0,x(0)=x_0$

We'll use a numerical ODE solver for these types of problems

Take this:
$x'(t)=v(t), v'(t)=-9.8$
we can rearrange this to:
$x_{n+1}=x_n+\triangle_tv_n$
$v_{n+1}=v_n-\triangle_t9.8$
this is called the Euler Method

![[Pasted image 20261122193000.png]]

