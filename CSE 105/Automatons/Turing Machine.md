### $$(Q,\Sigma,\Gamma,\delta,s,q_s,q_a,q_r)$$
$\{\sqcup\} \cup \Sigma \subseteq \Gamma$
$q_s,q_a,q_r \in Q$
$\delta: Q\times\Gamma\rightarrow Q\times\Gamma\times\{L,R\}$
$Conf=Q\times\Gamma^*\times\Gamma^*$
$Init(w)=(q_s,\epsilon,w)$
> [!info] Self Explanation
> A turing machine has states, transitions between states, and a tape.
> - states and transitions function as normal
> - the tape can be moved left or right each transition, transitions are defined by the symbol you're on, and you overwrite that symbol when you leave.


$f:\Sigma^*\rightarrow\Sigma^*$ is TM-computable if $\exists \ TM \ M$
$(q_s,w)\rightarrow...\rightarrow(q_a/q_r,w'), w'=f(w)$
> [!info] Self Explanation
> Function f is computable if there exists a TM s.t. given w on tape, it always halts on f(w) on tape at the end, i.e. it doesn't loop.
> 1. starts with w on tape
> 2. always halts / no loops
> 3. outputs f(w) when it halts


$L(M)$ is the set of strings $w\in\Sigma^*$ such that $M(w)$ accepts
$L=L(M)$ is TM-recognizable
> [!info] Self Explanation
> L is recognizable if the TM it represents accepts everything in L. It's not obligated to reject.
> Confirms membership, but can't confirm non-membership


$M$ is a decider if $\forall w\in\Sigma^*$, $M(w)$ terminates.
$L=L(M)$ where $M$ is a decider. $L$ is TM-decidable
> [!info] Self Explanation
> L is decidable if the TM it represents accepts everything in L and rejects everything not in L and infinite loops.
> We can get a definite answer on membership or non-membership for any string in $\Sigma^*$


### Emptiness Problem
Given a DFA M, determine if $L(M)=\emptyset$
$E_{DFA}=\{<M>|\text{ M is a DFA, and }L(M)=\emptyset\}$
$E_{REX}=\{<R>|\text{ R is regex, such that }L(R)\neq\emptyset\}$
Is $E_{REX}$ TM-recognizable?

1. On input $<R>$, check if R is systematically valid Regex. If the check fails then REJECT
2. Proceed by cases by induction on the structure of R:
	1. If $R=\epsilon$, then REJECT
	2. if $R=a$, then REJECT
	3. if $R=\emptyset$, then ACCEPT
	4. if $R=R_1\cup R_2$ then $b_i=R_i\in E_{REX}$, compute recursively, output $b_1\cap b_2$
	5. if $R=R_1\cdot R_2$ then  $b_i=R_i\in E_{REX}$, compute recursively, output $b_1 \cup b_2$
	6. if $R=(R')^*$ then REJECT, since $*$ gives you $\epsilon$

$L(M_{EREX})=E_{REX}$, so $E_{REX}$ is recognizable
$M_{EREX}$ is a decider, so $E_{REX}$ is decidable.

Is $E_{DFA}$ decidable?
Let $T(<M>)$ be:
1. Checks that M is a DFA, if not , then REJECT
2. transform M into an equivalent REX R using the method from Chapter 1
3. Run $M_{EREX}(R)$


