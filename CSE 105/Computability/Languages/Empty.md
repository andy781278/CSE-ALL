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