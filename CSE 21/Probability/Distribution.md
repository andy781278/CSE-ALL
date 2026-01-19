#Probability
this in probability means a function
$$p:S \rightarrow [0,1]$$
($[0,1]$ means a range from 0 to 1 inclusive)

And it has to have the following property:
$$\sum_{a\in S}p(a)=1$$
Some distribution is uniform,
[[Uniform Distribution]]
each outcome has the same possibility.
Since there are |S| outcome and and sum of all outcomes is 1, each outcome's probability is $\frac{1}{S}$
We are probably only using this one
Conditional probability are when probability of an outcome is defined by an equation, then integrals are required (I kinda want that but ok)

If your sample space S has [[Uniform Distribution]], then for any event E, p(E) is:
$$p(E) = \frac{|E|}{|S|}$$
This basically means that you divide the number of elements in E by the total elements

Example:
4 digit string **selected uniformly at random** (counting problem) has the property that no two consecutive digits are the same.
- 4 digit numbers have $10^4$ elements
- no two consecutive digits are the same means that if the first digit can be anything, the one after it has 1 less number, and the one after that regains the one lost from the 1st digit, so it is 10 9 9 9 = $\frac{7290}{10000}=0.729$
Example:
4 digit string **selected uniformly at random** in increasing order probability
- 0123, 1234, 2345, ... 6789
- 7 outcomes, 7/10000
- okay, that was wrong, bc 0134 is possible, it doesn't have to be consecutive.
- Then |E| is $\binom{10}{4}$ because 10 digits, you choose 4 of them. This means no repeats and you can automatically arrange that in increasing order

What's the probability that 4 digit strings in non-decreasing order? could be the same
stars and bars problem
4 knights (4 digits), 10 castles (10 int choices), 13 choose 9.

[[Binomial Distribution]]

[[Geometric Distribution]]