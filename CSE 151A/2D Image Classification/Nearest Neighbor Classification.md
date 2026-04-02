Given image of digit, how can computer know what it is

We give it a training set, and we expect it to learn via examples

We let $x^1,x^2,...,x^k$ be input, and $y^1,y^2,...,y^l$ be output

### Method 1: Use it all
given an image, we find the nearest neighbor $x^i$, which is somewhere in the input, then return the output: $y^i$.
- We decompose a 2d image into an array of values, each representing a pixel.
- For each pixel $x^i$, we compare to our input $z^i$, and we sum the distance between them all together
- The algorithm will never make a mistake, bc its goal is to find the nearest neighbor, not identify the correct solution
	- This is an issue
### Method 2: Separate Tests
Instead, we separate the data into smaller test sets
- Test error = fraction of test points incorrectly identified
We have 3% test error with Nearest Neighbor (90% by random)

### Method 3: Better Distance Function
Euclidean distance: $|x-x|_2 = \sqrt{\sum_{i=1}^{m} (x_i-z_i)^2}$

but let's have a more generalized formula:
$|x-x|_p = (\sum_{i=1}^{m} |x_i-z_i|^p)^{\frac{1}{p}}$

there are special cases as d is at $d=1$ and $d=\infty$

- $p=2$: normal euclidean distance
- $p=1$: $\sum_{i=1}^{m} |x_i-z_i|$
- $p=\infty$: $\text{max}_i \; |x_i-z_i|$

Try to measure distance independent of translations, rotations (tangent distance) (1%)
Then try to acknowledge natural shape deformations, (shape context) (0.6%)

### Method 4: K Nearest Neighbors
Instead of looking at just 1 neighbor, we look at k nearest neighbors, and we find the highest frequency output, and choose that one
- As k increases, it plateaus, then becomes ineffective, the peak is around k=3

Is that the best k? How do we know?
We must run tests with k from 1 to some large number every time we make a new model
####  Cross Validation
##### Leave-1-out
Make a subset called validation set, run tests and find the k with lowest test error with that set, then use that k for the rest of the data
##### 10-fold
We divide the data into 10 parts, and for each part, use kNN with the rest of the data set, find its error $e^i$, then find the average of $e^i$ over all 10 calculations. We do this with k from 1 to large number, and find the k with lowest e overall.

### Run Time
Run time is O(n), too slow
let's make it faster
#### k-d trees
For data set S in $R^d$
- Pick coordinate i from 1 to d
- compute v = median of all the data points
- split S into two halves, one smaller than v, one bigger
- recurse on the two halves
Then, we have two types of search
##### Defeatist search
Route q to a leaf cell and return the NN in that cell. This might not be the true NN
##### Comprehensive search
grow the search region to other cells that cannot be ruled out using the triangle inequality

