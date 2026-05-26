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

> [!info] Analogy
> - In order to compare competency between two kingdoms, we need a royal translator ($f$) that takes a parchment from one Kingdom and translates it to the other. This way, we can compare them easier.
> - A translator only has to finish and not loop (computable) to be usable. Their usefulness is determined by how accurate they are in mapping one kingdom to the other.
> Here's how you prove competency:
> 1. Define the translator f
> 2. Argue f always finishes
> 3. Prove the iff - accepting parchments from A maps to accepting parchments from B. Unaccepting parchments from A maps to unaccepting parchments from B.

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