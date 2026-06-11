

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