2. Provide a formal description and state diagram for a DFA over the alphabet $\Sigma = \{a, b\}$ that accepts the language
L = {w | w contains an even number of a’s and at least one b}

DFA $M = (Q,\Sigma,\delta,s,F)$ satisfies L
- $Q: \{even,odd,evenb,oddb\}$
- $\Sigma: \{a,b\}$
- $\delta:$

|     | even | odd   | evenb | oddb  |
| --- | ---- | ----- | ----- | ----- |
| a   | odd  | even  | oddb  | evenb |
| b   | oddb | evenb | oddb  | evenb |
- $s=even$
- $F \subseteq \{evenb\}$

7. Consider the regular expressions $R = (a ∪ b)^*$ and $S = (a^*b)^*$. Determine if L(R) is a subset, superset, or equal to L(S). Prove your answer.
$L(R)$ is a superset of $L(S)$, since you have to have a b in S, but not so in R.
$a\in L(R), a\notin L(S)$.
