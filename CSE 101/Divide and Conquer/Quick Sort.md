similar to quick select from selection.

```
function QuickSort(a1,...,an):
	if n==1: return a1;
	pick random pivot ai
	partition list into SL, Sv, SR based on ai
	L = QuickSort(SL)
	R = QuickSort(SR)
	return L*Sv*R
```


### Run Time
Similar to QuickSelect, it's random, so it depends on if you get lucky or not
Best case, pick median, and it's O(nlogn)
Worst case, pick max/min, and it's O(n^2)

