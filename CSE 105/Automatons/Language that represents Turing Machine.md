$Regular Language \subset CFG \subset D \subset RE$
$RE=\{L(M)|\text{ M is a TM}\}$
$L(M)=\{w\in\Sigma^*|M(w)\text{ accepts}\}$

$L\in D: \text{ if }\exists \ TM \ M$
- $\forall w\in L, M(w)$ accepts
- $\forall w\notin L, M(w)$ rejects

### Collatz Conjecture
$\forall n\geq 1 : n\rightarrow\rightarrow\rightarrow\rightarrow\rightarrow....\rightarrow 1$

$f(n) = \begin{cases} \frac{n}{2} & \text{if n is even} \\ 3n+1 & \text{ if n is odd} \end{cases}$

Every n goes to 1 eventually

$L=\{w|\text{w=YES if CC is true, w=NO if cc is false}\}:\{YES\},\{NO\} \text{ is in D}$

$Collatz=\{<w>|w\in\mathbb{N},\exists n. f^n(w)=1\}\subseteq \Sigma^*$
$CC:\text{"Collatz=}\{<w> \in \mathbb{N}\}\text{"}$

$M(<w>)=$
```
while w != 1:
	if even(w) then w:=w/2
	else: w:=3w+1
return accept
```

- The language of this M is the sequence of numbers the algorithm went through to reach 1.
- There is no reject for this language
- Is M a decider?
	- If M is a decider, then that means Collatz is true, which is not proven to be, even though all cases do agree that it is true
	- no, it doesn't ever reject

$M'(<w>)=$
```
S={}
while w!=1:
	if w is in S, reject
	S:=S U {w}
	w:=f(w)
accept
```

- if your number repeats, you can reject
- there are still cases where it diverges and does not repeat
- L(M)=L(M')=Collatz
- Is M' a decider?
	- no, even if it rejects sometimes, it can't prove that 

- Is Collatz decidable?
	- good question, to prove that, we have to best centuries old mathematicians and prove that Collatz does work or it does not

Let's say $\text{Collatz}'=\{<w>|<w> \notin Collatz\}$

Theorem 1: $L\in RE \land \overline L\in RE$
              $\leftrightarrow L\in D, L\in caRE$

Theorem 2: $\exists L\notin RE$
$RE\cap caRE=D$

Proof 1: Assume $L\in RE, \overline L \in RE$
By def: $\exists M_1,M_2, L(M_1)=L, L(M_2)=\overline L$
want: $\exists M, \forall w\in L, M(w)=\text{accept}$
	    	   $\forall w\notin L, M(w)=\text{reject}$

$M(w)=$
```
a=M1(w)
if a=accept then accept
b=M2(w)
if b=accept then reject
```

$M(w)=$ for n=1,2,3....
- Run $M_1(w)$ for n steps
- if $M_1(w)$ accepts in n steps, then accepts
- Run $M_2(w)$ for n steps
- if $M_2(w)$ accepts in n steps, then reject

M decides L

### Diag
$Diag=\{<M>|\text{ M is a TM, }<M>\notin L(M)\}$

> [!info] Diag
> Diag is a language that accepts the encoding of a TM M, but only encodings that is not in the language of that M.
> 

Claim: $Diag$ is not recognizable, or $Diag \notin RE$
Proof: Assume $Diag \in RE$
By Def, $Diag=L(M)$ for some M(TM)
$w=<M>\in Diag \leftrightarrow <M> \notin Diag$

> [!info] $Diag \notin RE$
> Diag is not recognizable, as in there's no way to guarantee given a set of inputs they will be accepted correctly.
> It also means there's no TM that can represent the language.

### Mapping Reduction

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

### Acceptance
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

### $A_1,A_0$
$A_1=\{<M>|\text{M is a TM, }1\in L(M)\}$
$A_0=\{<M>|\text{M is a TM, }0\in L(M)\}$

$A_{01}=\{<M>|\text{M is a TM, }\{0,1\}\subseteq L(M)\}$

Prove this at home? Prove what tho, see its hardness?