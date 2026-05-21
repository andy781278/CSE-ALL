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