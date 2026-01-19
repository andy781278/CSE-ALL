Given two sorted lists, determine if they are disjoint:
$a[1],a[2],...,a[n]$
$b[1],b[2],...,b[n]$

Disjoint($(a[1],a[2],...,a[n]),(b[1],b[2],...,b[n])$)
	for i:=1 to n
		if BinarySearch(b,a[i]!=0) then return FALSE
	return true

$O(nlog(n))$

Better way:
Disjoint($(a[1],a[2],...,a[n]),(b[1],b[2],...,b[n])$)
	j=1
	for i:=1 to n
		if $a[i]==b[j]$
			return false
		while a[i]>b[j] and j<=n
			j++
	return true

$O(n^2)$
But wait, the worse case scenario is actually 2n, since the indices never reset, and just incremented independently.

So, don't assume and check carefully