$$ E: Q \rightarrow p(Q)$$
$$E(q) = \{q' \in Q | \exists \text{ path } q \overset{\epsilon^*}{\rightarrow}  q'\}$$

$E(q)$ takes in a state returns a subset of every state reachable from q, including q itself

$$\tilde{E}: p(Q) \rightarrow p(Q)$$
$$\tilde{E}(S)=\underset{q \in S}{\cup} E(q)$$
$\tilde{E}(S)$ takes in a set of states and unions the $E(q)$ of every state in that $S$.


Used for NFA -> DFA transformations