# Basic ANOVA

Straightforward way of telling whether the value of a variable differs systematically among groups. It has some fairly stringent hypotheses that need to be satisfied. But if those hypotheses are satisfied, it's a strong simple analysis method.

It tests the equality of means among three or more groups of values.
Requirements for this test: 
* Independent samples for each group
* Same quantity for the groups
* Normally distributed populations
* Equal variance

Applications of this test: 
* rental costs in different markets
* health outcomes
* systolic blood pressure
* etc

## Notation
groups are named g_1 to g_k, whre k >= 3. 
If k = 1 or 2 this could be substituted for a t-test. 
Var = sigma^2, equal for all groups
mean_i to mean_k, where they may or not be different.
y_i_j is the jth observation of group g_1
the sum of all of the n's sub i's is n. So the total number of observations across all the groups is n.

And our null hypothesis is that the distribution assumptions hold mean_1 = mean_2 = ...mean_k. 
We have independent normally distributed samples from groups 1 through k. 
variance is constant. And the null hypothesis is that all of the means are, in fact, equal.

In here, mean means sample mean.
SSE = Sum of Squared Errors within groups = sum of i = 1 to k of (sum of j = 1 to n_i of (y_i_j - mean_i)^2)
Basically, substract the mean of each group to each element in the group, add that, then do that for each group and add those. 

SSA = Sum of Squared Errors between groups = sum of i = 1 to k of (sum of j = 1 to n_i of (mean_i - mean)^2) = sum from i = 1 to k of (mean_i - mean)^2 * n_i = mean of all measurements thrown in together. 

OK, so big idea is that under the null hypothesis, SSE captures the within group variance, how much bouncing around, around the group mean individual measurements from the group will have. Whereas SSA captures the variance of the group means. So the group means under the null hypothesis are means of k samples each of size n sub i of a population with mean mu and variance sigma.

We know that how to analyze the variability of a sample mean compared to the variability of individual measurements. So the sample means will typically under the null hypothesis be even closer to mus than the individual measurements. So bottom line, the relationship between the size, the amount of variation captured by SSE and SSA is manageable.

If the group means are different, SSA captures the variance between the group means. So each y sub i bar is going to be close to its mu sub i. And the differences between the y sub i bars will be larger than you'd figure if they were all sample means from populations with the same underlying true mean. The larger the difference is between the mu sub i, the larger that SSA is going to be, those sample means are going to be spread out relative to the overall mean.

So it's called ANOVA from sort of acronym Analysis Of Variance. The test statistic for the ANOVA is that SSA, the group mean, sum of squares divided by k minus 1. Remember k is the number of groups. That's your numerator. And the denominator is SSE, the within group, sum of squares divided by n minus k, the number of total observations minus the number of groups.

Under the null hypothesis, it turns out that this statistic f has an F-distribution with the numerator degrees of freedom equal to this k minus 1 here and the denominator degrees of freedom equal to n minus k. It's not obvious that that's actually the correct distribution, that this is, in fact, an F-distribution with these degrees of freedom. But I think you can get a feel that this is plausible, that we have sums of squares of normal distributions. And with a little linear algebra, you could work it out that they're independent normal distributions and get the right degrees of freedom.

In any case given this distribution, the p-value for the ANOVA is the probability that a sample from this F-distribution with degrees of freedom k minus 1 and n minus k actually comes out greater than or equal to f, the probability of getting basically such a large numerator if the means were actually equal.

ANOVA is actually fairly robust against non-normality, especially for large samples. So there is a tendency not to look at normality all that closely. But for a non-parametric version of the sorts of questions addressed by a one-way ANOVA, you can use the Kruskal-Wallis test if your distribution assumptions are really problematic.