Finding a frequent item (more than half) in a list with O(1) space and O(n) time

If counter is 0, assign a new candidate and inc

if the next guy is candidate, inc

if the next guy is not candidate, dec

The candidate at the end is the majority if there is one. If there isn't one, or not guaranteed, then you do a 2nd pass and check to see if that candidate is indeed occuring >n/2 times.

