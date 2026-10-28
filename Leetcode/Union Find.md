uses DSDS concept

## group depends on one item
use a dictionary, key = dependent identifier, value = list of fit elements

## group depends on connections
a chain of dependency, a -> b -> c
need some O(1) way to check whether a connected item exists or was visited:
- connection via rule on values (x+1 or 2x): a set
- connection via edge/pairs: adjacency list, then explore or union find