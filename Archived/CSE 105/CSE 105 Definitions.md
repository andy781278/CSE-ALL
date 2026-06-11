This course is about solving problems.

We need to know:
- what makes problems easy/hard?
- are there unsolvable problems?
- what makes a problem a computation problem?

All problems comes in the form of:
Input: String -> Output: 1/0
Solutions: Algorithms

### Definitions
- String: finite sequence of symbols
- Alphabet($\Sigma$): finite set of possible symbols
- Language/L(a): set of strings over some input of type Regular Expression (Regex) (denoted by R)
	- $L(a)=\{a\}$
	- $L(R_1 \cup R_2)=L(R_1)\cup L(R_2)$
	- $L(R_1 \cdot R_2)=\{w_1 w_2 | w_1 \in L(R_1), w_2 \in L(R_2)\}$
	- $L(R_1^*)=\{w_1,w_2,...,w_k | k\geq 0, \forall i, w_i \in L(R_1)\}$
	- $L_1 \subseteq L_2 \subseteq \Sigma^*$
- Length of string: absolute value function (|abc|)
- $R^*$ = set of all possible combinations over $R$
	- this has infinite size, since there is no limit of the amount of strings
	- can be nothing, since empty set is also a possible combination
	- basically: optional infinite symbols of every possible thing

### Examples
$\Sigma=\{a,b\}$
$R=(a(a\cup b)^* b) \cup (b(a \cup b)^*a)$
All strings over alphabet a,b that begins and ends with different symbols

$\Sigma=\{a,b\}$
$R=(a(a\cup b)^* a) \cup (b(a \cup b)^*b)\cup a \cup b$
All strings over alphabet a,b that begins and ends with same symbols
- Prof interpretation does not include $\epsilon$, since an empty string does not have symbols, so it doesn't begin and end with the same symbols

