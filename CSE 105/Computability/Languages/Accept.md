$A_{TM}=\{<M,w>|\text{M is a TM, w is a string, }w\in L(M)\}$

$A_{TM}\in RE$?

$P(x):$
```
Pase x=<M,w>
If parsing fails, then reject
Run M(w)
```

$HALT\leq_m A_{TM}$

$f(<M>)\rightarrow <M',w>$ where $M'(x)=M(x);ACCEPT$, $w=\epsilon$
1. $<M>\in HALT \rightarrow f(<M>)=<M,\epsilon>\in A_{TM}$ INCORRECT
2. $<M>\notin HALT \rightarrow f(<M>)=<M,\epsilon>\notin A_{TM}$ CORRECT