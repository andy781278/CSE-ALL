#Probability
To get the average/expected value, do the following:
1. List all possible outcomes (eg. winning $1, $3, $15. Win $5 if same color, lose $3 if different color)
2. Find the probability of each outcome
3. summation them together, for each, multiply them by the outcome, assuming that the outcome is a certain quantity.

You expect an average when doing a bunch of random events in a sample space. This is how you get the expected value when E is expected function that takes in a random variable that is retrievable by calling X on sample space S
$$E(X) = \sum_{s\in s} P(s)X(s)$$
$$=\sum_{r\in X(S)} P(X=r)r$$
Example:
Rolling 2d6, how to get average?
Each element is a calculation of the summation, P(X=r) gets you the probability of getting the value r (which is retrievable by dividing number of ways to get that val by the total possibilities), that is then multiplied by the value r itself
![[Screen Shot 2025-10-17 at 8.34.59 PM.png]]

Note that E follows the add and multiply axioms of a set, so you can do this: $E(X_1+X_2) = E(X_1) + E(X_2)$

##### Indicator Random Variables
Doesn't have to be this way, but you need to define a certain $X_i$ to be correct, or 1, in certain conditions that match your problem, and 0 otherwise.

$X_i = \left\{ \begin{array}{rcl} 1 & \mbox{if} & F_i = H & \mbox{and} & F_{i+1} = H\\ 0 & \mbox{otherwise}  \end{array}\right.$

An indicator random variable D means that the only values of D are 0 or 1
so what is E(D)? (average value of this var)
$0*P(X=0) + 1*P(X=1) = P(X=1)$

Problem Type:
Expected pairs of **consecutive** heads when fair coin flipped n times

Let's define $X_i=1$ if both ith and i+1th flips are heads, 0 otherwise
$$X=\sum_{i=1}^{n-1}X_i$$
Probability of 2 heads in a row is 1/4

$$E(X) = E(\sum_{i=1}^{n-1}X_i) = \sum_{i=1}^{n-1}E(X_i) = \sum_{i=1}^{n-1}P(X_i=1) = \sum_{i=1}^{n-1}\frac{1}{4} = \frac{n-1}{4}$$


Problem:
in a findMax type of fxn, what is the amount of times the max var is changed? Let's say that an array a length n is looped by i as marches through the array.

Let X be the number of times max var is changed.
$X_i = \left\{ \begin{array}{rcl} 1 & \mbox{if} & M & updates\\ 0 & \mbox{otherwise}  \end{array}\right.$
Problem:
Xi is 1 if you pick 2 balls with same color, else 0

P(X=1) = probability of picking 2 balls with same color.

Let's first find all possible ways you can pull out things, which is $\binom{4}{2}$, or 6, and only 2 ways to win, so 2/6 = 1/3 which is P(X=1).

In this case we are lucky, because there is only 1 other alternate result, which is when we don't get what we want, and that is 2/3.

Now we summation them with their result.

$5*1/3+(-3)(2/3)=-1/3$

So we lose 1/3 per game on average, and across 3 games, we win 3*-1/3 = -1

[[Linearity of Expectation]]

[[Conditional Expectation]]