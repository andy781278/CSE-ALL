---
aliases:
  - CFG
---
CFG is a tuple $(V,\Sigma,s,R)$ where
- $V,\Sigma$ are finite sets
- $s \in V$
- $R\subseteq V \times (V \cup \Sigma)^*$

$\alpha X \beta \rightarrow \alpha Y \beta$ where $Y,\alpha,\beta \in (V \cup \Sigma)^*, X \in V, (X \rightarrow \beta) \in R$
$S \rightarrow X_1 \rightarrow X_2 \rightarrow X_3 ... \rightarrow \alpha_n \in \Sigma^*$

aaabbb
$s \rightarrow asb \rightarrow aasbb \rightarrow aaasbbb \rightarrow aaabbb$
Prase Tree:
$s:(a,s:(a,s:(a,s:(\Sigma),b),b),b)$
