---
aliases:
  - psd
---
a property describing a symmetric matrix


### positive semidefinite (PSD)
matrix $M$ is positive semidefinite if:
$x^T M x\geq 0$ for all vectors $x$


#### Check is a matrix is PSD
A matrix M is only PSD if it can be written as $M=UU^T$ for some matrix U

> [!info] Any Covariance Matrix is PSD
> $Square \subset Symmetric \subset PSD$
> A is PSD iff $A+A^T$ is PSD


##### When is a Diagonal Matrix PSD?
$M=diag(a_1,a_2,...,a_d)$
$x^T M x = \sum_{i=1}^d a_ix_i^2 \geq 0$
all $a_i$ are nonnegative


##### is PSD closed under mult?
 If M is PSD, must cM be PSD for a constant c
c must be positive for this to be the case


##### is PSD closed under add?
If M,N are same size and PSD, is M+N PSD?
yes



### positive definite (PD)
matrix $M$ is positive definite if:
$x^T M x > 0$ for all vectors $x$