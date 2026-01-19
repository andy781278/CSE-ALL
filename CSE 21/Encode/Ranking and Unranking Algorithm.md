#Encode 
If we order the bit strings in a particular way, we can use a ranking algorithm that converts bit strings into a position, and unranking algorithm that converts a position back to the bit string

##### Ranking Algorithm
Rank(x: binary string, n: length, k: length of 1s):
	Case 1: x starts with 0, x=0x'
		In this case, x is among the first $\binom{n-1}{k}$ strings. (first half)
		return Rank(x',n-1,k)
	Case 2: x start with 1, x=1x'
		In this case, x is after $\binom{n-1}{k}$, (2nd half)
		return $\binom{n-1}{k}$ + Rank(x',n-1,k-1)
Hint: ![[Pascal's Identity#^fa69ab]]

Shortcut:
![[Pasted image 20251124145310.png]]

##### Unranking Algorithm
Unrank(d: position of the data, integer between 0 and$\binom{n}{k}$, n, k):
	If n=0:
		return empty
	If d<$\binom{n-1}{k}$:
		return $0 \circ Unrank(d,n-1,k)$
	else:
		return $1 \circ Unrank(d - \binom{n-1}{k},n-1,k-1)$
Hint: $\circ$ is concatenation

Shortcut:
![[Pasted image 20251124151419.png]]
![[Pasted image 20251124151534.png]]
