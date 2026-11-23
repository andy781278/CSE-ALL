We have 2 particles that we want to try and maintain their distance to rest length l

Goal: Minimize potential energy $U(x)$ where $F=-\frac{dU}{dx}$

So force minimizes potential energy, and we want the force to go in a direction that minimizes potential energy

We can use the spring equation

### $U(x_0)=\frac{1}{2}k(|x_0-x_1|-l)^2$

### $F_0=-k(|x_0-x_1-l|)\frac{x_0-x_1}{|x_0-x_1|}$


Behavior:
When dist > l, pull
When dist < l, push


### Rope
We can link up a bunch of points in a row, and lock the first one (make mass inf), and now we have a rope
- Increasing k makes the force harder and less stable (need damp/friction?)
	- Eventually, when k goes to infinity, we have a hard constraint
	- $|x_0-x_1|=l$

### Cloth
2d rope, but we have more different kinds of forces:
- structure force, OG adjacent neighbors
- shearing force, for diagonal neighbors
- bending force, for neighbors 1 point over
![[Pasted image 20261122200213.png]]

### Position Based Dynamics
