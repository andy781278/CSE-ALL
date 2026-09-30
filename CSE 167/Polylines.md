just a line that can bend and can form shapes

## Shape Color
### Point in polyline test
To be able to tell if a point is enclosed in a polyline shape, we raycast that point to any direction, and case:
- Odd: in
- Even: out

#### Non-zero rule
But if the polyline intersects themselves, then new rule, we ray cast with direction of line drawn in mind:
- let n=0
- intersect a line going up: n += 1
- intersect a line going down: n -= 1
- if n=0 then out, else in

### Check if ray hits line
mathematically a ray can be a vector:
$$q+(a,b)s \ \ \text{for} \ s>0$$
where q is the origin point of raycast, (a,b) is the vector

and the line is:
$$p_0+t(p_1-p_0) \ \ \text{for} \ 0\leq t \leq 1$$
where the line goes from $p_0$ to $p_1$, and the t determines where along the line the point of intersection is

Then we equal them and solve for s and t:
$$q+(a,b)s = p_0+t(p_1-p_0) \ \ \text{for} \ s>0,0\leq t \leq 1$$

Corner Case:
When a ray hits a vertices/corner, it hits two lines at once
solution: make every line a different z level, and on intersections, the higher one counts and the lower one does not.

## Stroke Color
We now have to figure out whether or not a point is in a stroke so we can color it, we can do that by using vector math to figure out the distance between the point and the line perpendicularly, and if it's smaller than what we want, we fill it in.

## Curves

in a straight line:
$$p(t)=p_0(1-t)+p_1 t,t\in [0,1]$$
### Bezier Curve
Use 3 points: $p_0,p_1,p_2$
let $p_{01}$ be a point between $p_0$ and $p_1$: $p_{01}(t)=p_0(1-t)+p_1 t$
let $p_{12}$ be a point between $p_1$ and $p_2$: $p_{01}(t)=p_0(1-t)+p_1 t$
let $p(t)=p_{01}(1-t)+p_{12}t$
Expanding, we get:
$$p(t)=(1-t)^2p_0+2(1-t)tp_{1}+t^2p_2$$

### How do we find fill stroke of a curve
$$t^*=argmin_{t\in[0,1]} ||p-f(t)||^2$$
$$d=||f(t^*)-p||$$
where $f(t)$ is the equation of the curve
$t^*$ is the t of the curve that will give you the closest point
d is the distance between that point to our point

For quadratic:
$$t^*=argmin_{t\in [0,1]} \ at^4+bt^3+ct^2+dt+e$$
To solve, set derivative to 0 and isolate t