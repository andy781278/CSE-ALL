Instead of the rasterization explained before, we use ray tracing, which involves iterating over every pixel, send a ray out from the camera point to the pixel center and beyond, seeing the triangles it hits, and choosing the closest one.

## How to find if ray intersects
Using Barycentric Coordinates
Moller-Trumbore Algorithm

For Triangles:
$\vec V_0b_0+\vec V_1b_1+\vec V_2b_2=\vec O+t\vec d$
$b_0+b_1+b_2=1$

Find $b_0, b_1, b_2$, and $t$

For Spheres:
$|\vec O + t \vec d-\vec x_c|^2=r^2$
Solve like a quadratic of t


## How do you make it fast?
Build a database of objects so you can access it fast when checking per pixel to see which one's closest

Subdivide the space

Subdivide the objects
- Group objects into boxes, if ray misses box, won't have to calculate anything in that box
- Build a tree of layers of boxes to subdivide the objects
- makes it O(logn) to traverse, bc you can throw away what you don't hit, eliminating half each time instead of 1
- To detect hitting box, do ray intersect plane 6 times for each of the 6 faces of the box
- actually, it doesn't have to be a box

