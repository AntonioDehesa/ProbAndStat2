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

# Pseudoreplication (non-independence)

## Split plot

So a standard ANOVA assumes independence of all of the observations. And in an experimental design, you'll assign each unit randomly to a treatment in order to draw causal inferences. Sometimes this isn't possible. As a reference problem, consider an experiment designed to study the effects of three different classroom strategies and two different types of instructional software on student outcomes for content presented during one week. But-- and this seems fairly reasonable-- you're not able to randomize assignment of students to classrooms.

So you'd come in. You have three different classroom strategies. You assign pre-existing classrooms of students to different classroom strategies. And then you can assign instructional software randomly to students regardless of their classroom. But the principals kind of object if you want to start moving students around. So you plan a statistical analysis of the results that'll examine the statistical significance of the effect of the interaction, classroom strategy, how the classroom strategy and the instructional software play together, the differences due to instructional software, and the differences in classroom strategy in learning outcomes.

So a split plot design is an experimental design to address this situation. The effects of multiple factors are studied at different levels of aggregation of the smallest experimental unit. In their reference example, this would be the students. And we're looking at classroom-level factors, where students are aggregated into classrooms, and student-level factors.

In a standard factorial analysis, the levels of each factor are randomized at the level of the smallest experimental unit. You take in 30 patients and randomly assign 10 to treatment A, 10 to treatment B, and 10 to treatment C. In a situation in which this isn't possible or practical, you may be able to address the need to keep blocks of your smallest experimental unit together using a split plot design.

So for example, as we talked about, you want to study school, classroom, and student-level factors in education. You want to study epigenetic effects at the level of parents and the level of their multiple offspring. So it's going to be tricky to randomly assign offspring to parents.

In agricultural settings, some agricultural manipulations may need to be applied at different scales. So those scales are the plots in split plot. That's where the method originated. So it doesn't make much sense to irrigate one square meter differently from the neighbor square meter. So irrigation treatments would have to be applied at a fairly large scale, planting type, soil cultivation. Just practical considerations may affect the scale at which these treatments can be applied.

And another example would be to compare team level and individual factors for athletes and training at different locations. So you could assign treatments to teams, but coaches would probably object if you tried to assign athletes randomly to teams.

So let's look at the agricultural example in a little more detail. Suppose we're wanting to study the effects of irrigation, planting density, and fertilizer on yield. And let's assume that plot size requirements in descending order are-- that you can vary irrigation only over quite large areas, but that density of planting can be varied on smaller areas, and that just as a consideration of the machines used to plant the crop, you can plant in a different density in a smaller area; then you have to irrigate differently. And then let's suppose that fertilizer can be applied in yet smaller areas and still have distinct treatments from area to area.

So we select plots for the experiment, split them into separate irrigation regions. So each plot is just divided in two. One part gets one irrigation treatment. The other gets another irrigation treatment. Each irrigation sub-plot, treatment 1 or treatment 2, is divided into sub-sub-plots, which will be planted with different densities. These can be assigned randomly within irrigation plot. And each irrigation density sub-sub-plot is split into sub-sub-sub-plots, each of which is randomly assigned to a fertilizer treatment.

So big picture, to carry out this design, order the treatments by decreasing levels of the aggregation required, so largest grouping, next largest, next largest, down to your individual unit of analysis. Identify the nested groupings for the levels of aggregation, and randomize the treatments at the appropriate levels of aggregation.

I think this works better with the picture. So suppose we have four fields, four plots. And we're going to apply two irrigation levels. These are supposed to be the same size plot, by the way. We're going to apply to irrigation levels. Randomly assign one and two, maybe two, one. Just flip a coin which plot gets which treatment. And so now we have our irrigation levels assigned.

Each irrigation level is split into three density levels. And then within an irrigation plot level, you can randomly assign densities. They just happened randomly to be an order. So each irrigation plot will receive each of the density treatments, but which density treatment goes into which sub-sub-plot is randomized.

And now, once you've got the density levels assigned, you'll split each of these. I suppose I could use one line there. You'll split each of these into, I think, where it's sub-sub-sub-plots now, and randomly assign fertilizer treatments to each of these. And this assignment of fertilizer treatment is happening in all of these sub-sub-sub-- sub-sub-sub plots. And that gives you your experimental design. So you're aggregating within the plot level appropriate to the treatment.

So due to the data dependencies, just straight up multi-factor ANOVA without the split plot computation that we're going to talk about may violate our assumptions of independence when we get to the unit of analysis. So for example, student outcomes in the same classroom and same school may be similar to one another in unmeasured ways. So thinking of those student measurements within a classroom as independent disregards the problems with the heating in one classroom versus another. So there may be dependencies among students within a classroom that we aren't measuring. And that violates the assumption of independence in ANOVA.

In an epigenetics study, the offspring of the same parents may be similar to one another in ways that we aren't measuring, in ways that aren't just associated with the treatment. In agriculture, nearby sub-sub-sub-plots may be more similar to one another than distant sub-sub-sub-plots, using microclimate issues. In athletics, athletes on the same team and athletes in the same location will share features, will share-- I don't want to call them factors, because the factors are the ones we're analyzing, the ones we're accounting for-- but will share characteristics, may well share characteristics other than the ones we're analyzing.

So the analysis approach that we're going to take to account for this dependence of measurements at the smallest unit of analysis, when we're looking at the larger units of analysis, are actually conceptually to work at multiple levels. For example, our irrigation units will be the subplots. So we're only going to have as many irrigation units as we have treatments times original plots. Density units are the sub-sub-plots that are planted with different densities. And we'll aggregate observations at the sub-sub-plot level to analyze density. And the fertilizer units are the sub-sub-sub-plots.

This is conceptually very straightforward if our experimental design is balanced-- that is, if the groups at each level of aggregation have the same subgroup structures and counts. So each tuple of grouping variables has the same number of the smallest experimental unit. For example, each school has six participating classrooms within each school. Two classrooms use each strategy. So we don't have one school with seven classrooms and others with six.

We don't have different numbers of classrooms within a particular school. Each school has six participating classrooms. Within each school, two classrooms use each strategy. Each classroom has 20 students. Within each classroom, 10 students use each type of instructional software. So our design is very uniform. This makes it simple to analyze and instructive to consider the analysis that we do, even in this simple case, to get concepts that'll carry over to more complicated cases.

So the procedure is to analyze at the higher level of aggregation by correcting out the effects yet higher and averaging over the smallest units. So in our agricultural example, to study irrigation, we'd correct the observations for plot. One plot just seems to have a higher yield overall than another. We'll correct that out. And then we'll average over all the sub-sub-plot measurements.

For density, we'll correct out for plot and irrigation effects and, again, average over the sub-sub-plots. For fertilizer, we correct out the plot, irrigation, and density effects and then average over the sub-sub-plots, the smallest units. And some group similarities are subtracted out as we descend in the groups.

ANOVA for balanced design is a useful conceptual guide. ANOVA for unbalanced design actually lacks consensus about how it's performed. And multiple regression is good alternative to ANOVA for an unbalanced experimental or observational design.

There is a challenge that's left after completing a split plot ANOVA, or any ANOVA, for that matter. And that is, if the null is rejected, which factors actually differ significantly? And that has to be addressed by other methods.

