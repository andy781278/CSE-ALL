$Regular Language \subset CFG \subset D \subset RE$

### Computable
$f:\Sigma^*\rightarrow\Sigma^*$ is TM-computable if $\exists \ TM \ M$
$(q_s,w)\rightarrow...\rightarrow(q_a/q_r,w'), w'=f(w)$
> [!info] Self Explanation
> Function f is computable if there exists a TM s.t. given w on tape, it always halts on f(w) on tape at the end, i.e. it doesn't loop.
> 1. starts with w on tape
> 2. always halts / no loops
> 3. outputs f(w) when it halts

### Recognizable
$L(M)$ is the set of strings $w\in\Sigma^*$ such that $M(w)$ accepts
$L=L(M)$ is TM-recognizable
> [!info] Self Explanation
>-  L is recognizable if the TM it represents accepts everything in L. It's not obligated to reject.
> - Confirms membership, but can't confirm non-membership
> - 

$RE=\{L(M)|\text{ M is a TM}\}$
$L(M)=\{w\in\Sigma^*|M(w)\text{ accepts}\}$

### Decidable
$M$ is a decider if $\forall w\in\Sigma^*$, $M(w)$ terminates.
$L=L(M)$ where $M$ is a decider. $L$ is TM-decidable
> [!info] Self Explanation
>-  L is decidable if the TM it represents accepts everything in L and rejects everything not in L and infinite loops.
> - We can get a definite answer on membership or non-membership for any string in $\Sigma^*$
> - Based on HALT, any L that requires information from within TM $M$ that can only be answered via simulation, not just based on the encoding $<M>$, is not decidable.

$L\in D: \text{ if }\exists \ TM \ M$
- $\forall w\in L, M(w)$ accepts
- $\forall w\notin L, M(w)$ rejects