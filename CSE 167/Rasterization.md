![[joe.png]]For storing triangle meshes, we stored points in 3d coordinates and faces given 3 vertices
![[Screen Shot 2026-10-16 at 12.22.21 PM.png]]

1. Clip triangle
2. divide the vertices by -z
3. render the triangle

As long as the three dot products are all pos or neg, the point is inside the triangle
![[Screen Shot 2026-10-16 at 12.27.32 PM.png]]


To detect which triangle is drawn over others, we need barycentric coordinates

![[Screen Shot 2026-10-16 at 12.33.23 PM.png]]

We calculate b as area of the smaller triangle over the larger one

![[joe.png]]

p is inside the triangle if b0, b1, and b2 is between 0 and 1 inclusive

![[Screen Shot 2026-10-16 at 12.40.35 PM.png]]

$$Z=b_0p_0.z+b_1p_1.z+b_2p_2.z$$
$$v=b_0v_0+b_1v_1+b_2v_2$$
![[Screen Shot 2026-10-16 at 12.45.06 PM.png]]


![[Screen Shot 2026-10-16 at 12.51.52 PM.png]]

### Speeding Up

Only test pixels inside the bounding box of the triangle

Occlusion culling: Skip triangles that is completely covered by another

Frustum culling: Skip triangles too far from the camera

### Hardware Rasterization
We've been making a program to use the GPU directly, but we can write a program that can utilize fixed more efficient GPU graphics pipeline to do things faster.
Today, hardware ras serves as a fast default environment that works efficiently in most cases
![[Screen Shot 2026-10-16 at 2.07.34 PM.png]]

![[Screen Shot 2026-10-16 at 2.49.12 PM.png]]

