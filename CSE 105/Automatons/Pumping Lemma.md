---
aliases:
  - PL
---
Used to prove if a language is regular or not
![[Pumping Lemma.excalidraw]]

> [!abstract] Pumping Lemma
> $\forall$ Reg Lang $L$, $\exists p$ such that $\forall w \in L$,  $(|w| \geq p) \rightarrow \exists x,y,z$ such that the following is true:
> 
> 0. $w=xyz$
> 1. $y \neq \epsilon$
> 2. $|xy| \leq p$
> 3. $\forall i \geq 0, xy^iz \in L$
> 
> Let $M:(Q,\Sigma,\delta,s,F)$ be a DFA such that $L(M)=L$ (M is regular)
> Let $p=|Q|$ (p be number of states). Let $w \in L$ and assume $|w| \geq p = |Q|$ (w is the input, assume there are more inputs than there are states, so there has to be at least 1 loop somewhere)
> $q_0 = s  \overset{w_1}{\rightarrow} q_1 \overset{w_2}{\rightarrow} q_2 ... \overset{w_r}{\rightarrow} q_r \rightarrow ... \rightarrow q_{|w|} \in F$
> $\exists i < j \leq p, q_i = q_j$ (there are two states, pi and pj, that are equal, and i<j) (so a loop)
> $x=w[1...i], y=[i+1,...,j], z=[j+1,...,|w|]$ (y is the loop, x is before, z is after)
> 
> Using Induction:
> - Base Case: i=0
> 	- $\delta^*(s,xz)=\delta^*(\delta^*(s,x),z)=\delta^*(q_i,z)=\delta^*(q_j,z)=f \in L$
> - Induction: i+1
> 	- $\delta^*(s,xy^{i+1}z)=\delta^*(\delta^*(s,x),yy^iz)=\delta^*(\delta^*(q_i,y),y^iz)=\delta^*(q_i,y^iz)=f \in F$

> [!info] Self Explanation
> As long as L is a regular language, then there has to be a p somewhere such that all w that is longer or same length as p has to be made up of some x, y, z, that satisfies the following:
> xyz makes up w
> y is not empty
> |xy| is shorter or equal to p
> $xy^*z$ for an indeterminate amount of y is in the language L, which means it satisfies the condition of L

$|xy|\leq |Q|$
$y \neq \epsilon$
$w = xyz \in L$

$\delta^*(s,x)=q$
$\delta^*(q,y)=q$
$\delta^*(q,z)=f \in F$

$\forall i \geq 0, xy^iz \in L$
$\delta^*(s,xy^iz) = \delta^*(\delta^*(s,x) ,y^iz)$
$=\delta^*(q,z)=f\in L(i=0)$
$=\delta^*(q,yy^{i-1}z) =\delta^*(\delta^*(q,y) ,y^{i-1}z)=\delta^*(q,y^{i-1}z)=f\in F$

### How to use it
Claim: $L_{nn}$ is not regular
Proof by Contradiction: Assume $L_{nn}$ is regular
so by PL, $\exists p$ such that requirements 1,2,3 in the PL are satisfied
Let $w=a^pb^p\in L, |w|=2p\geq p$
$\exists x,y,z, w=xyz$
1. $y \neq \epsilon \rightarrow |y|\neq 0$ (as long as we can attribute some input to y, anything, like a or b, even just once, this is satisfied)
2. $|xy| \leq p \rightarrow x=a^{|x|}, y=a^{|y|}, z=a^{p-|x|-|y|}b^p$ (xy is less than p because they did not take all of a, there's still some a left over in z, and p is same length as a, so you can say $|xy| \leq p$)
3. $i=0, xz=a^{|x|}a^{p-|x|-|y|}b^p = a^{p-|y|}b^p\notin L$ (to disprove you just need 1 case to fail, this case fails) (y is missing because i=0) (we mathematically proved that for i=0, this expression is not in L, because a and b are different length, $p-y<p$ because $y>0$.)

Claim: $L_\neq=\{w \in \{a,b\}^* \text{ | w contains the same \# of a's as b's} \}$
Proof by Contradiction: Assume $L_\neq$ is regular
$L(a^*b^*)$ is regular (aaaabbbbbbb) (abb)(b)(a)()
$L_\neq \cap L(a^*b^*)=L_{nn}$ is regular because intersection is closed under regular languages. (this gets rid of the different orientations like 0101, and just keeps the 0011, the orientations where a precedes b)
This creates a contradiction because we know $L_{nn}$ is not regular.
Therefore $L_\neq$ is not regular