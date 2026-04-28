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

