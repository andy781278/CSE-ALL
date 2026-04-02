---
aliases:
  - DFA
---
Definition: A DFA is a 5-tuple $M = (Q,\Sigma,\delta,s,F)$ where:
- $Q$ is a finite set of states (vertices)
- $\Sigma$ is an alphabet (input)
- $\delta: Q \times \Sigma \rightarrow Q$, where $\delta(q,a) \in Q$, and it maps where the edges come from and go to (edges)
- $s$ is the start state
- $F \subseteq Q$ is called accepting states, where output is 1

The **computation** of DFA $M = (Q,\Sigma,\delta,s,F)$ on input $w \in \Sigma^*$ is the sequence $q_0, w_1, q_1, w_2, q_2, w_3, ..., w_n, q_n$ of $q_i \in Q$ and $w_i \in \Sigma$ such that
- $w=w_1 w_2 ... w_n$
- $q_0 = s$
- $q_{i+1}=\delta(q_i,w_{i+1})$
the computation is 
- accepting if $q_n \in F$
- rejecting if $q_n \notin F$

$\delta^*: Q \times \Sigma^* \rightarrow Q$
$\delta^*(q,\epsilon)=q$
$\delta^*(q,aw)=\delta^*(\delta(q,a)=q,w)$

$L(M) = \{w\in\Sigma^* | \delta^*(s,w)\in F\}$

Define computation mathematically
Similar to Finite State Machine
A graph where the vertices represent states, and the edges represent input.
you traverse through the graph from the given sequence of inputs, and then determine states where output is 1