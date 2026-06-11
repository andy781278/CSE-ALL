
> [!info] Analogy
> King $L_x$ takes $<V>$ parchments where Lord V accepts villager $x$ as one of his subjects

$L_1=\{<M>|\text{M is a TM, }1\in L(M)\}$
$L_0=\{<M>|\text{M is a TM, }0\in L(M)\}$
$L_{01}=\{<M>|\text{M is a TM, }\{0,1\}\subseteq L(M)\}$

Q: Is $L_x$ in $D$? In $RE$? In $coRE$?

$P(<M>):$
```
If M is not a TM:
	P(<M>) Rejects
If Run M(0) Accepts:
	P(<M>) Accepts
```
With enough competence, only need to say $P(<M>)=M(0)$

$L(P)=L_0\rightarrow L_0\in RE$

$L_0 \leq_m A_{TM}$
$f(<M>)=<M,0>$
1. $<M>\in L_0\rightarrow f(M)\in A{TM}$
2. $<M>\notin L_0\rightarrow f(M)\notin A{TM}$

$A_{TM}\leq_m L_0$
$f(<M,w>)=<M'>$
$M'(x):$
```
If x=0:
	M(w)
else?:
	!M(<M>)
```

1. Assume $<M,w>\in A_{TM}$, M is a TM, $M(w)$ accept
$f(<M,w>)=<M'>\in L_0$? $M'$ is a TM, $M'(0)$?
$M'(0)=M(w)$ accepts, so $<M'>\in L_0$

Assume $<M,w>\notin A_{TM}$.
If M is not a TM then M' is not a TM and $<M'> \notin L_0$
M is a TM, $M(w)$ does not accept.
$<M'>\in L_0$?
$M'(0)=<(w)\neq accept$

$f(<M,w>)=<M'>$ where $M'(x)=M(w)$

| M(w)   | L(M')       |
| ------ | ----------- |
| Accept | $\Sigma^*$  |
| Reject | $\emptyset$ |
| Loop   | $\emptyset$ |
