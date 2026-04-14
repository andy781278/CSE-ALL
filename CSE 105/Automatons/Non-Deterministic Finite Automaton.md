---
aliases:
  - NFA
---
Definition: A NFA is a 5-tuple $M = (Q,\Sigma,\delta,s,F)$ where
- $\delta:Q\times\Sigma\rightarrow p(Q)$ instead of $Q$
- p() is the power set operation
- this means that the return type is a set of states rather than a single state, so you can occupy multiple states at once
- everything else is the same as DFA

A computation of NFA on input $w=w_1,..,w_n$ is a sequence of $q_0 w_1 q_1 ... w_n q_n$ where
1. $q_0=s$
2. $w_i=\Sigma\{\epsilon\}, w=w_1,...,w_n$
3. $q_{i+1}\in \delta(q_i,w_{i+1})$

### Matching to DFA
$\forall \ NFA \quad N=(Q,\Sigma,\delta,s,F), \ \exists M=(Q',\Sigma',\delta',s',F')$ such that $L(M)=L(N)$
- You can match every NFA to a corresponding DFA
	- matching means they have the same 
	- however, this means that the states in Q' shall be subsets of Q instead of a single element of Q, then you map according to where each element goes from the input

> [!abstract] Proof
> $Q'=p(Q)$, $\delta : Q \times \Sigma \rightarrow p(Q)$
> $\delta' : Q' \times \Sigma \rightarrow Q'$
> $\delta' : p(Q) \times \Sigma \rightarrow p(Q)$
> $s \subseteq Q$, $\delta'(s,a)= \cup_{q \in s} \delta(q,a)$
> $s'=\{s\}$
> $F'=\{s|s \cap F \neq \emptyset \}$

Using Epsilon-Closure Function, we can achieve it.

NFA: $(Q,\Sigma, \delta, s, F)$
DFA: $(p(Q),\Sigma,\delta',s',F')$
$F' = \{s \in Q, s \cap F \neq \emptyset\}$
$s'=\tilde{E}(\{s\})$
$\delta'(S,a)=\tilde{E}(\underset{q\in \tilde{E}(S)}{\cup} \underset{q\in S}{\delta}(q,a))$

Why would we translate NFA to DFA? So we can translate it back to RegEx
To do that, we need to translate it to GNFA first.