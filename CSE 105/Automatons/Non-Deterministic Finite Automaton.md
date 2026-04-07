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