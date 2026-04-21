---
aliases:
  - CFG
---
CFG is a tuple $(V,\Sigma,S,R)$ where
- $V,\Sigma$ are finite sets
	- $V$ is a set of variables 
	- $\Sigma$ is the alphabet
- $S \in V$
	- Start variable
- $R\subseteq V \times (V \cup \Sigma)^*$
	- set of rules, each in the form $A\rightarrow w, A \in V, w \in (V \cup \Sigma)^*$

Example
$\alpha X \beta \rightarrow \alpha \gamma \beta$ where $\gamma,\alpha,\beta \in (V \cup \Sigma)^*, X \in V, (X \rightarrow \beta) \in R$
$S \rightarrow X_1 \rightarrow X_2 \rightarrow X_3 ... \rightarrow \alpha_n \in \Sigma^*$

Example
to make: $aaabbb$
rule: $s \rightarrow asb | \epsilon$
progression: $s \rightarrow asb \rightarrow aasbb \rightarrow aaasbbb \rightarrow aaabbb$
Prase Tree: $s:(a,s:(a,s:(a,s:(\Sigma),b),b),b)$
