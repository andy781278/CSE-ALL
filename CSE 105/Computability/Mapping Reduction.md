> [!info] Analogy
> Measurement of the competency of a King ($\leq_m$)
> $A\leq_m B$ means King $A$ has less or equal competence or than King $B$
> A more competent King are better than making decisions and not stall
> A Recognizer King is less competent than a Decider King
> A Non-Recognizer King is less competent than a Recognizer King

$Diag=\{<M>|\text{ M is a TM, }<M>\notin L(M)\}$
$Diag\leq_m HALT=\{<M>|\text{M is a TM, }M(\epsilon)\text{ does not loop}\}$
$Diag\leq_m E_{TM}=\{<M>|\text{M is a TM, }L(M)=\emptyset\}$

> [!info] $\leq_m$
> $\leq_m$ means mapping reduction 
> $A\leq_m B$ means A mapping reduces to B, or A is no harder than B
> Hardness goes on a scale from least to most hard:
> Decidable $\rightarrow$ Recognizable $\rightarrow$ Not-Recognizable
> If B is in RE, and A mr to B, then A is either in D or RE, not in NRE
> 
> Prove $A\leq_m B$:
> To prove mapping reduction, we have to create a **computable** mapping function f s.t.
> $w\in A \leftrightarrow f(w)\in B$
> Then we have to prove that the function we create satisfies the following:
> - If $w\in A$, then $f(w)\in B$
> - If $w\notin A$, then $f(w)\notin B$

then $Diag\in RE\leftarrow$ if $E_{TM}\in RE$
$M'(w)=M(f(w)),L(M)=E{TM}$
$L(M')=Diag$

$P:L(P)=HALT$
$P(w):$ 
```
check if w=<M> for some TM M.
If the check fails then return reject
run M(e)
return accept
```

Claim: $\exists$ no mapping reduction from Diag to HALT
$\neg(Diag\leq_m HALT)$

$DiagR=\{<M>|\text{M is a TM, }<M>^R\notin L(M)\}$
$Diag\leq_m DiagR$

$f(<M>)=<M>^R$

$<M>\in Diag \rightarrow f(<M>)\in DiagR \rightarrow <M>^R \notin DiagR$

$g(<M>)=<M'>$ where $M'(w)=M(w^R)$