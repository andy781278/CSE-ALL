Sampling at pixel center can be very inaccurate, and looks very bad

The issue is that when we sample real world signals, which are continuous, we turn it into discrete sample points in a computer, which cannot capture the continuous patterns, and it looks bad especially on low resolutions.

Also good for thin things like rods or sticks and fonts

## Super-Sampling Antialiasing (SSAA)
Further subdivide a pixel into many smaller pixels, and average all of their colors together to represent the region as a pixel. There are two ways of super sampling:

Nearest Neighbor
Bilinear Interpolation

