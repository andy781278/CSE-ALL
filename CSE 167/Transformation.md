![[Screen Shot 2026-10-02 at 2.05.56 PM.png]]


### Linear Transformation
$f(p)$ is a linear function
- It's easier to analyze and well understood, established way to compute inverses
- expressive
- non-linear can be broken down into many small linear transformations
- scaling, rotation, shearing, reflection, translation

how to compute:
1. write down the new basis in terms of the old basis
$v=2i, w=i+j$
2. substitute 
$2v+w=2(2i)+(i+j)=5i+j$

Any linear transformation can be written as a matrix
$v=2i,w=i+j$
  v       w
$\begin{bmatrix} 2 && 1 \\ 0 && 1 \end{bmatrix}$

$\begin{bmatrix} 2 && 1 \\ 0 && 1 \end{bmatrix} \begin{bmatrix} x \\ y\end{bmatrix}=\begin{bmatrix} 2x+y\\ y\end{bmatrix}$

##### Common 2D Linear Transformations
Scaling:
### $\begin{bmatrix} s_x && 0 \\ 0 && s_y\end{bmatrix}$

x Shearing:
### $\begin{bmatrix} 1 && \lambda_x \\ 0 && 1\end{bmatrix}$

Rotation:
### $\begin{bmatrix} cos\theta && -sin\theta \\ sin\theta && cos\theta\end{bmatrix}$

Translation:
### $\begin{bmatrix} x' \\ y'\end{bmatrix}=\begin{bmatrix} x \\ y\end{bmatrix}+\begin{bmatrix} t_x \\ t_y\end{bmatrix}$

Affine Transformation:
### $\begin{bmatrix} x' \\ y' \\ 1\end{bmatrix}\begin{bmatrix} a && b && t_x \\ c && d && t_y \\ 0 && 0 && 1\end{bmatrix}\begin{bmatrix} x\\y\\1\end{bmatrix}$
                              1 for point, 0 for vector

### Animation
Animation is just interpolating the translation parameters from one key frame to another

Linear Interpolation:
$\square_x (1-t)+\square_y t$
