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

### Examples
$\alpha X \beta \rightarrow \alpha \gamma \beta$ where $\gamma,\alpha,\beta \in (V \cup \Sigma)^*, X \in V, (X \rightarrow \beta) \in R$
$S \rightarrow X_1 \rightarrow X_2 \rightarrow X_3 ... \rightarrow \alpha_n \in \Sigma^*$


to make: $aaabbb$
rule: $S \rightarrow aSb | \epsilon$
progression: $S \rightarrow aSb \rightarrow aaSbb \rightarrow aaaSbbb \rightarrow aaabbb$
Parse Tree: $S:(a,S:(a,S:(a,S:(\epsilon),b),b),b)$


$L=\{a^{n_1}ba^{n_2}b...ba^{n_k}|k\geq0,\forall i, n_i \geq 0, \exists i,j \ \  n_i \neq n_j\}$

$L_1=\{a^{n_1}ba^{n_2}|n_1=n_2\}$
$S_1\rightarrow aS_1a | b$

$L_2 = \{ a^{n_1}ba^{n_2}|n_1 < n_2 \}$
$S_2 \rightarrow S_2 a | aS_2 a | ba$

$L_3 = \{  a^{n_1}ba^{n_2}|n_1 > n_2\}$
$S_3 \rightarrow aS_2 | aS_2a|ab$

$L_4 = \{  a^{n_1}ba^{n_2}|n_1 \neq n_2\}$
$S_4 \rightarrow S_2|S_3$

$L=\{a^{n_1}ba^{n_2}b...ba^{n_k}|k\geq0,\forall i, n_i \geq 0, \exists i,j \ \  n_i \neq n_j\}$
$X=(a^*b)^*,Y=(ba^*)^*$
$S \rightarrow (a^*b)^* T (ba^*)^*$
$T \rightarrow aTa | Xa^* | a^*Y$

$S \rightarrow XT'Y$
$X \rightarrow \epsilon | X'X$
$X' \rightarrow b|aX'$
$Y \rightarrow \epsilon | YY'$
$Y' \rightarrow b|X'a$
$T \rightarrow aTa | bXAa | aAYb$
$A \rightarrow \epsilon | a A$
