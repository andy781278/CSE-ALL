Given a graph with n vertices labeled v0...vn-1, starting v0, maybe negative edge weights, return true if negative cycle otherwise return the shortest distance from v0 to all other vertices

how to detect negative cycles?
If you run t up to n then if there is a negative cycle, then you will see improvements between iterations t=n-1 to t=n

i.e. for all 0<=i<=n-1: B[i,n-1]=B[i,n]=B[i,n+1]...

if no negative cycles, values will never improve after t gets bigger than n-1
so if there is an i such that B[i,n-1]!=B[i,n] then there is a negative cycle


```
BFDP(G,v0):
	B[0,0]=0
	B[i,0]=inf for all i!=0
	for t=1 to n:
		For 1 = 0 to n-1:
			B[i,t]=min(B(j,t-1)+w(vj,vi)) for all vertices j
	for i=0 to n-1:
		if B[i,n-1]!=B[i,n]
			return true (negative cycle)
	return [B[0,n],B[1,n],...B[n-1,n]]
```

O(|V||E|)
O(n(n+m))