---
title: "Claims with more than two means"
output: pdf_document
---

#Claims With More Than Two Means: ANOVA

The t-test is a powerful way of testing whether two groups are different. However, one limitation of this test is we might have experiments or data where we have more than two groups. For instance, I knew some researchers who wanted to see whether firstborn children prefer romantic partners with different birth order personalities. They set up their data where firstborn children rated how romantically interested they would be in a person who had a firstborn personality, a middle child personality, a youngest child personality, or an only child personality. So they had four groups of participants, one who saw each of the personalities.

They wanted to test the hypothesis that firstborn children would prefer firstborn personalities differently than they preferred middle child, youngest child, and only child personalities. If they wanted to use t-tests to do this test, they would have to do many t-tests, one where they compared each group to every other group. They would compare the group who read first-born personalities to the group who read middle child to the group who read last child, and the middle child to the last child, and so on. That's a lot of comparisons.

If I want to test every group against every other group, I would have 6 t-tests. One problem we discussed with any statistical test is the possibility of a Type-1 error, or a false positive, where we falsely conclude there is a difference between the two groups when in fact there are not. We set the alpha value to correct for that. For instance, if we set $\alpha = .05$, we are setting a 5% chance of a Type-1 error. However, if we do multiple tests, the chance of making an error increases.

This is a concept called **family-wise error**. Family-wise error is the idea that if we test several different statistical analyses, the chance we have a false finding increases. If you do n t-tests, the chance of a family-wise error is equal to $1-\alpha^n$. In this case, it equals: $$\mathit{FWE} = 1- .05^6 = .265$$ There is over a 25% chance that  we would find one group being different from another group, even if there are no differences between all the groups.

One way we can correct for family-wise error is by changing alpha. If we wanted to make sure  we only have a 5% chance of making an error and want to do 6 t-tests, we can lower alpha accordingly so that the overall error rate is .05. If we want to set the chance of one false-positive at a probability of $\alpha$ with n tests, we can get a new value for alpha we will call p and use that as our new alpha value by using the formula: $$p = 1- \sqrt[n]{(1 - \alpha)}$$. So if we wanted to make sure we have an overall error rate of .05, we would do: $$p = 1-\sqrt[6]{1-.05} = .008$$ In this case, we would set an overall alpha of .008 as our cutoff value as to whether to reject or retain the null hypothesis.

This approach is very conservative (increasing the chance of a miss or type-2 error) and there are other alternatives to set up the p-value that are not as conservative.

We can correct for this by doing what is called an **omnibus test** or a test where we examine all the possible hypotheses at once in one test. The most common of this is a test called the ANalysis Of VAriance, or ANOVA. The ANOVA is a test where we test whether there are any differences between groups. In ANOVA, the null hypothesis testing with n groups is  $\bar{x}_1 = \bar{x}_2 = \bar{x}_3 = \ldots\ = \bar{x}_n$. Essentially, this states that all of the sample means come from the same population. Since the alternative hypothesis is the inverse of the null hypothesis, that means the alternative hypothesis is *at least one sample mean is from a different population*. So if there are 3 groups, the null hypothesis would be $\bar{x}_1 = \bar{x}_2 = \bar{x}_3$. The alternative hypothesis is that at least one group is different. That could mean $\bar{x}_1 \neq \bar{x}_2 = \bar{x}_3$ or $\bar{x}_1 = \bar{x}_2 \neq \bar{x}_3$ or $\bar{x}_1 \neq \bar{x}_2 = \bar{x}_3$ or $\bar{x}_1 \neq \bar{x}_2 \neq \bar{x}_3$ or any other combination in which at least one mean is not equal to another mean. So if an ANOVA is significant, all we can conclude is that at least one mean is not different from the other means. This is a limitation we will have to keep in mind. 

ANOVA stands for ANalysis Of VAriance. The idea of ANOVA is a comparison of two kinds of variance, the within-group variance and the between-group variance. Within-group variance is conceptually a measure of how much each group varies from its mean. Between-group variance is a conceptual measure of how much each mean varies from the overall mean, called the **grand mean**. The idea is if the between-group variance is higher than the within-group variance, this implies that at least one of the group means is different from the rest.

<!--need to insert figure here -->

Imagine the following examples. In the first example, you have three groups all drawn from the same population, which would be the case if the null hypothesis is true. Notice that each group has its own mean and variance. The means are not exactly the same, but the difference between the group means, marked by vertical lines, is very close relative to the variance within each group.

In the second example, the groups are from different populations with different means. Notice the groups are much more spread out and the group means are spread further, relative to the variance within the groups. In this example, it's clear at least one, if not more, of the group means are different from one another.

ANOVA captures this by measuring a quantity called the **F-ratio** which is a statistic like the t-value or z-value you have calculated already. The F-ratio is a measure of the between-groups variance divided by the within-groups variance. If $F = 1$, the between-groups variance is equal to the within-groups variance, and this indicates the groups are very likely from the same population. However, as the between-groups variance increases relative to the within-groups variance, F will increase. If there is twice as much between-groups variance than within-groups variance, $F = 2$, and so on.

As we will discuss below, we will use $F$ to find a p-value that allows us to test the probability we would get the data we got if the null hypothesis is true. Like with T-tests, if that $p < \alpha$, we would reject the null hypothesis. If not, we retain the null hypothesis.

##How to do an ANOVA

As we mentioned in an earlier chapter, one way to measure variance is the concept of sums of squares, which is defined for each observation $x_{i}$ in $1 \ldots\ n$ as $\mathit{SS} = \sum (x_{i} - \bar{x})^2$. Essentially, this is the each observation minus the group mean squared, summed up. When we have data in one group, sums of squares is a simple concept. However, in ANOVA, we have two or more groups which may or may not be from the same population. So we can take this idea of sums of squares and create three different types of sums of squares.

Before talking about this, there are some terms and concepts to describe. When doing an ANOVA, the data consist of $n$ observations are divided in $k$ groups. The mean of each group are called the **group means** and is referred to as: $\bar{x}_{k}$. As mentioned above, the mean of all the data is called the grand mean and is referred to as: $\bar{x}_{g}$.

The sums of squares correspond to each of these groups. The sums of squares within is a measure of how much each observation deviates from its own group mean. The sums of squares between is a measure of how  much each group mean deviates from the grand mean. Sums of squares total are a measure of how much each individual observation deviates from the grand mean. Because of this, sums of squares total equals sums of squares between plus sums of squares within.

###Calculating Sums of Squares Between

Sums of squares between can be calculated by using the following formula. $$\sum n_k(\bar{x}_{k} - \bar{x}_{g}  )^2$$. For each group, we take that group's mean minus the grand mean, and then square that number. Then we multiply it by the number of observations in the group. We do this for each group and then we add those numbers up.

###Calculating Sums of Squares Within

Sums of squares within can be calculated by the following formula. $$\sum(x_{i} - \bar{x}_{k}  )^2$$ Essentially, we are taking the each observation minus its group mean, squaring that number, and then adding all of the resulting numbers up. 

###Calculating Sums of Squares Total

Sums of squares total can be calculated by the following formula, which is very similar to sums of squares within $$\sum(x_{i} - \bar{x}_{g}  )^2$$ Essentially, we are taking the each observation minus *the grand mean*, squaring that number, and then adding all of the resulting numbers up. 

Remember that sums of squares total equals sums of squares between plus sums of squares within. Because of that, we can check to make sure we calculated  this correctly.

| Type of Sums of Squares | Symbol | Formula     |
|-------------------------|--------|-------------|
| Sums of Squares Between | $\mathit{SS}_{B}$|$\sum n_k(\bar{x}_{k} - \bar{x}_{g}  )^2$|
| Sums of Squares Within | $\mathit{SS}_{W}$|$\sum(x_{i} - \bar{x}_{k}  )^2$|
| Sums of Squares Total | $\mathit{SS}_{T}$|$\sum(x_{i} - \bar{x}_{g}  )^2$|

## Calculating the rest

Sums of squares is only the beginning. What we want to find is a ratio that compares between-group variance to within-group variance. Since the number of observations in a group is important, we need to get the *mean* of the sums of squares. This quantity is called **mean squares** and is found by taking sums of squares and dividing by degrees of freedom.

Degrees of freedom is a bit complicated in ANOVA. The overall degrees of freedom are the same as in a t-test, namely $\mathit{df}_{T} = n-1$. However, these degrees of freedom can be split into degrees of freedom between and degrees of freedom within. Degrees of freedom between are calculated by $\mathit{df}_{B} = k-1$ which is the number of groups minus 1. Degrees of freedom within are calculated by $\mathit{df}_{W} = n-k$, which is the number of observations minus the number of groups.  These two quantities add up to the total degrees of freedom:  $\mathit{df}_{B} + \mathit{df}_{W} = \mathit{df}_{T}$.

With sums of squares, we can calculate mean squares, which are simply $\frac{\mathit{SS}}{\mathit{df}}$. We only calculate mean squares between as $\frac{\mathit{SS}_{B}}{\mathit{df}_{B}}$ and mean squares within as $\frac{\mathit{SS}_{W}}{\mathit{df}_{W}}$.

The final step is calculating the F-ratio, which we will discuss later. This is calculated as $\frac{\mathit{MS}_{B}}{\mathit{MS}_{W}}$. We use the F-ratio to find the p-value that will test the probability that we would get the data we got if the null hypothesis is true.

##Doing an example

Imagine we have the following situation. I want to test whether the color words are printed in affects how well they are remembered. Each group received a list of 15 words to remember and I analyzed how many correct words they wrote down in a recall task where they wrote down which words they remembered. The only difference between the groups was that one group received a list of words written in red, another group received a list written in black, and a third group received a list written in blue. These are the data:

|Participant|Group|Score|
|-|-|-|
|1|red|9|
|2|red|10|
|3|red|12|
|4|red|11|
|5|red|13|
|6|blue|7|
|7|blue|9|
|8|blue|6|
|9|blue|8|
|10|blue|5|
|11|black|4|
|12|black|8|
|13|black|6|
|14|black|5|
|15|black|7|
|mean|red|11|
|mean|blue|7|
|mean|black|6|
|mean|grand|8|


###The null and alternative hypothesis

The first step is to set up the null and alternative hypothesis. The null hypothesis is that all the group means are from the same population. This would imply that color has no effect on what is remembered. The alternative hypothesis is that at least one group mean is from a different population.

When doing an experiment, we may have  

###Calculating Sums of Squares

To calculate sums of squares between, we take each group mean minus the grand mean, squaring the result, and then multiplying by the number in the group. See the formula below: $$ 5*(11-8)^2 + 5*(7-8)^2 + 5*(6-8)^2 = 70 $$.

To calculate sums of squares  within, we would take each number minus its group mean, square it, and then sum up all the results. This would look like the following table, where I calculate the score minus the group mean in the fourth column and then that number squared  in the fifth column. To calculate  the sums of squares within, we add up the last column, getting $\mathit{SS}_{t} = 30$..

|Participant|Group|Score|$(x_{i} - \bar{x}_{k}  )$|$x_{i} - \bar{x}_{k}  )^2$|
|-|-|-|-|-|
|1|red|9|-2|4|
|2|red|10|-1|1|
|3|red|12|1|1|
|4|red|11|0|0|
|5|red|13|2|4|
|6|blue|7|0|0|
|7|blue|9|2|4|
|8|blue|6|-1|1|
|9|blue|8|1|1|
|10|blue|5|-2|4|
|11|black|4|-2|4|
|12|black|8|2|4|
|13|black|6|0|0|
|14|black|5|-1|1|
|15|black|7|1|1|


To calculate sums of squares total, we would use the same procedure for sums of squares within, but instead of taking each score minus the group mean, we do each score minus the grand mean. See the table below:

|Participant|Group|Score|$(x_{i} - \bar{x}_{g}  )$|$x_{i} - \bar{x}_{g}  )^2$|
|-|-|-|-|-|
|1|red|9|1|1|
|2|red|10|2|4|
|3|red|12|4|16|
|4|red|11|3|9|
|5|red|13|5|25|
|6|blue|7|-1|1|
|7|blue|9|1|1|
|8|blue|6|-2|4|
|9|blue|8|0|0|
|10|blue|5|-3|9|
|11|black|4|-4|16|
|12|black|8|0|0|
|13|black|6|2|4|
|14|black|5|-3|9|
|15|black|7|-1|1|


If we add up the last column, we get $\mathit{SS}_{T} = 100$. Since $\mathit{SS}_{B} + \mathit{SS}_{W} = \mathit{SS}_{T}$, we can check our work. Indeed we find $70 + 30 = 100$. 

###Calculating Degrees of Freedom and Mean Squares

The second step is degrees of freedom. In this experiment, we have 15 observations and 3 groups. We calculate overall degrees of freedom as $\mathit{df}_{T} = n-1 = 15-1 = 14$. Degrees of freedom between are calculated by $\mathit{df}_{B} = k-1 = 3-1 = 2$ Degrees of freedom within are calculated by $\mathit{df}_{W} = n-k = 15 - 3 =12$, which is the number of observations minus the number of groups.  

At this point, we are getting a lot of numbers. It's useful to build up an ANOVA table to report all these numbers and to keep us sane. We would have the following numbers:

|Variance|SS|df|
|-|-|-|
|Between|70|2|
|Within|30|12|
|Total|100|14|


As mentioned above, mean squares are $\frac{\mathit{SS}}{\mathit{df}}$. We can calculate these in our table and expand it. Notice, I only do this for between and within group variance, since it is meaningless for total variance.

|Group|SS|df|MS|
|-|-|-|-|
|Between|70|2|35|
|Within|30|12|2.5|
|Total|100|14||

The last step is calculating F, which is $\frac{\mathit{MS}_{B}}{\mathit{MS}_{W}}$. I add F to the table on the top row.

|Group|SS|df|MS|F|
|-|-|-|-|-|
|Between|70|2|35|14|
|Within|30|12|2.5||
|Total|100|14|||.

In this case, we get an $F = 14$, which indicates we have conceptually 14 times as much between-group variance as within-group variance. This is quite high, so we should expect to reject the null hypothesis. To find  out the probability we would get an F-value of F or greater, if our null hypothesis is true, we can use the following R command. In this case, we have to give the command the F value we received marked as F, and the two different types of degrees of freedom, first the between-group degrees of freedom marked as dfB and the within-groups degrees of freedom marked as dfW.


```r
1- pf(F,dfB,dfW)
```

In our case, we would type:


```r
1-pf(14,2,12)
```

```
## [1] 0.000729
```

As noted above, this gives us a value of $F = .00073$. This  is much less than the traditionally assigned alpha value of $\alpha = .05$ and we would reject the null hypothesis.

##ANOVA in R

Conducting ANOVAs in R is very easy, as long as you have your data set up correctly. This is one case where it is very important to have data imported in "tidy" format. As noted in the chapter on R, tidy format means that each column contains a variable and each row contains an individual with related observations.

When doing an ANOVA, we need two variables. The first is the independent variable and that tells us which group a subject is in. The second variable is the dependent variable and this tells us what the value is for each person.

For instance, if we take our table from the example above, the column labeled "Group" is the independent variable and the column labeled "Score" is the dependent variable.

|Participant|Group|Score|
|-|-|-|
|1|red|9|
|2|red|10|
|3|red|12|
|4|red|11|
|5|red|13|
|6|blue|7|
|7|blue|9|
|8|blue|6|
|9|blue|8|
|10|blue|5|
|11|black|4|
|12|black|8|
|13|black|6|
|14|black|5|
|15|black|7|

To do an ANOVA in R, we have to first enter the data into R. Below is how to do this by hand, but as you can see, it may be easier to do this using a spreadsheet program and import the data into R.


```r
Group = c("red","red","red","red","red","blue","blue","blue","blue","blue","black","black","black","black","black")
Score = c(9,10,12,11,13,7,9,6,8,5,4,8,6,5,7)
d = data.frame(Group,Score)
```

This imports the data and puts it into a dataframe named "d". You can view this dataframe by typing `View(d)`.

Now to do the ANOVA, we have to use the `aov()` command, which stands for Analysis Of Variance. To do this, we need 3 parts:

1. The dependent variable
2. The independent variable
3. The data frame

The dependent variable and the independent variable are separated with a tilde \~. 

Now we type the command. In this case, we need two commands. the first one does the ANOVA and saves it as an object named x and then the second command does the `summary()` command using the object named x.


```r
x = aov(Score~Group, data = d)
summary(x)
```

```
##             Df Sum Sq Mean Sq F value   Pr(>F)    
## Group        2     70    35.0      14 0.000729 ***
## Residuals   12     30     2.5                     
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

This gives us the between degrees of freedom and sums of squares in the row listed with the name of the independent variable. In this case that row is named "Group". Then the row below gives us the within degrees of freedom, sums of squares, and mean squares. The last two columns are the F-value and the p-value associated with the F value. In this case, we get the same p-value as before.

##Summary

After reading this chapter, you should know or be able to do the following:

1. Understand why multiple comparisons leads to increased type 1 error and what we can do about this
2. Know what is being compared in ANOVA, specifically within-group and between-group variance through the F-ratio
3. Know how to conduct an ANOVA by hand and in R, calculating the sums of squares, degrees of freedom, mean squares, F-ratio, and p-value.
4. Know how to interpret an ANOVA, including what the null and alternative hypothesis is as well as how to know whether to reject or retain the null hypothesis.
