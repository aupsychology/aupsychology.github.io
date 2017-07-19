---
title: "Two Mean Claims"
output: html_notebook
---

#Two Mean Claims

In this section, you will learn:

1. What a two-group mean claim is and how to test it
2. Know the difference between an independent and paired samples (dependent) t-test and when to use each of them
3. How to calculate a paired samples (dependent) t-test and independent samples t-test by hand
4. How to calculate each of these t-tests using R

##What are we testing with two-mean claims?

Many hypotheses in research use the same premise: is the mean of one group different from the mean of another group? This occurs in a diverse number of situations. For instance, you may wonder if a low-fat diet leads to more weight loss than a low-carb diet. Or you might ask whether anxious individuals' mean level of anxiety is lower after taking a medicine than before taking a medicine. This might also involve testing whether people are more honest when they think they are being watched than when they think they are not being watched.

The experimental method in science involves making a hypothesis and testing that hypothesis. In many cases we are testing whether one group is different than another group. Often this logic involves taking a sample of individuals, randomly assigning those people to two groups, and then treating those groups in different ways. The idea about this is that the two groups are equal in every way except the one factor we want to measure.

A classic way of doing this is by having one group be a *control group* which does not get a manipulation and then having an *experimental group* which does receive a manipulation. For instance, one group might receive a drug whereas the other group receives a placebo that does not contain the drug. Another way of doing this is having two different groups which get two different kinds of manipulations.

Here’s an example. There is a theory that the color red might make people feel more threatened because it is a “hot” color. Based on this, a scientist may develop the theory that comments written in red will seem more negative than comments written in blue. To test this idea, the experimenter takes 100 participants and  then has them give a speech. After the speech, the experimenter gives each person the same feedback, with some positive attributes and some negative attribues. The only difference is that 50 people get the feedback written in red ink and 50 get the feedback written in blue ink. Then the experimenter asks the participants to rate on a 10 point scale “how negative or positive does this feedback seem”? with a 1 rating meaning very negative, 5 being neither negative or positive, and 10 indicating very positive.

In this example, the experimenter wants to see if the participants rate the feedback more negatively, giving a lower rating, when it is red. The experimenter takes the average rating for the 50 participants reading the feedback in red and the average rating of the 50 participants reading the feedback in blue. The reason the researcher takes the average is that in both of the conditions there may be people who rate the feedback as very positive, just because those people are naturally biased to see anything more positively. Likewise, there are some people who rate the feedback very negatively in both conditions for the opposite reason; they see everything as very negative, regardless of color.  By using the mean of 50 participants, those individual differences will cancel out since by randomly assigning people to each group, we should have a relatively equal number of positive and negative people in each group.

Imagine the researcher finds out that the 50 people rating the feedback in red has a mean rating of 4 out of 10 and the 50 people rating the feedback in blue has a mean rating of 5. Does that mean the experimenter’s idea worked?

You may be thinking that this might just have happened by chance. For some reason it just so happened that the people in the red group rated the feedback as more negative than the people in the blue group, not because of the color of the ink but due to random chance that people who were more likely to rate feedback as more negative happened to be assigned to the red group. Just as there is a chance I can flip a coin and get heads 20 times in a row, there’s a chance this could happen as well. However, the lower this chance is, the more likely the effect is due to my hypothesis; there is something different with reading feedback written in red versus feedback written in blue.

This is the idea of testing two-group hypothses. We can apply null hypothesis testing to these questions if we think of this in terms of populations. When we select two groups and do an experiment to treat those groups differently, we are trying to create two populations. That means, when people are in group A, they should be fundamentally different than group B. The logic is that if our experiment is working, it would take people who are in one population in the beginning and then make them two different populations. In the example above, if the color of feedback affects how people respond to the feedback, people reading feedback written in red should be a different population than those who read feedback written in blue. If color does not matter, than the red group should be no different than the blue group.

When I have two groups, I set up a null hypothesis that the two groups are part of the same population. This implies that the thing that I argue makes those two groups different does not matter or is so irrelevant that it would not make the two groups different populations. Conversely, the alternative hypothesis is that the two groups are not part of the same population. Now this can be for one of two reasons. It can be that the manipulation I did, such as printing the feedback in red or blue ink makes the groups different. Or it could be that something else I am not aware of, called a confound, makes the two groups different. For instance, I may have had a bad experimental design where I smiled when I gave people the feedback in blue whereas I frowned when I gave people the feedback written in red. In that case, the two groups are from a different population, but for reasons different than what I was aware of.

| Two-group hypotheses   | Hypothesis                                         | This implies:                                                                                                          |
|------------------------|----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Null hypothesis        | The two groups are part of the same population     | The thing I think makes the two groups different is irrelevant or does not make the groups different.                |
| Alternative hypothesis | The two groups are not part of the same population | The thing I think makes the two groups different (or something else I am not aware of) makes the two groups different. |

There are two types of two-group hypotheses. In one case, we are measuring two groups  that are independent of each other. Group A is not related to Group B. In this case, there are different people in group A versus group B. This is called an independent sample and will be the foundation of an independent samples t-test we will discuss in section C.

However, it may be the case that I have the same participants and measure them twice. Imagine if I wanted to test whether a 60 minute lecture on self-esteem increases people’s performance in a class. I could measure their performance on an exam before the lecture and then an exam after the lecture. In this case, the same participants are measured twice. This is called a paired samples or dependent samples t-test and will be discussed in section B.

##Paired Samples T-test

I saw a study once that suggested that eating chocolate can help you lose weight. This sounded like an exciting study, but it turns out the entire study was fabricated as a way to demonstrate problems with the scientific process and science journalism. However, the idea still might be true.

If we wanted to test whether eating chocolate would help you lose weight, or any other diet-related hypothesis, we might design an experiment like this: We take a group of people, measure their weight, have them eat the new diet we wanted to test for a period of time, and then measure their weight again. We could take 50 people, have them eat normally but eat a bar of chocolate each day, and weigh them again after 4 weeks.

This is a kind of design called a **pre-test/post-test design**. It involves taking a group of people, testing them before doing an experiment, doing the experiment, and testing the people after the experiment. It is a very powerful design because we can control for many extraneous factors which might be different in each group. Since the same people are being measured twice, we can ensure that each group has the same personality and other factors which might vary if we have two groups with two different sets of people. However, many designs cannot be done using a pre-test/post-test design. For instance, it would be difficult to do the red versus blue colored feedback experiment discussed in the last section, since we are interested in feelings after getting feedback. It would not make sense to receive feedback in blue ink, rate your feelings, and then repeat the study and receive the same feedback in red ink.

When doing a pre-test/post-test design, the null hypothesis is that the pre-test observations and the post-test observations are from the same population, which suggests nothing has changed during the period between the pre-test and post-test. If chocolate does nothing for weight loss, there should be no difference between pre-test and post-test designs. Some people would have an increase of weight, some would have a decrease, and some would have no change. There would be no mean change in the difference. Conversely, the alternative hypothesis is that the pre-test and post-test are from different populations, which indicates that something changed between the pre-test and post-test.

The test used to examine pre-test/post-test designs is the paired samples (or dependent samples) t-test. The paired-samples t-test is a variant of the one-sample t-test we  discussed in the last module. In the last module, we discussed that the one-sample t-test tests whether a sample is different from a population mean. 

The paired-samples t-test extends this logic by using difference scores. If we take the difference between the post-test and pre-test for each individual, we will create difference scores. In the instance of the chocolate weight loss study, we would take each individual’s post-diet weight minus their pre-diet weight. This would give us a difference score for each individual.

With these difference scores, we can start to examine our hypothesis. If chocolate does not affect weight, the difference scores should have a mean close to zero. Some people’s weight might go up, some people’s weight might go down, and some people would stay the same. However, if chocolate does affect weight, the difference scores should be different from zero. If chocolate helps people lose weight, then most people would see a negative difference score (lower weight after the diet). The opposite could be true, where chocolate would actually increase weight, because it is chocolate after all. In that case, most of the difference scores would be positive with higher post-diet weight. In either case, the difference scores are different from zero.

The paired-samples t-test takes difference scores and then does a one-sample t-test comparing the difference from zero. As mentioned above, the null hypothesis is that there should be no difference between the pre-test and post-test samples. This is the same thing as saying the difference scores should be zero. The paired-samples t-test essentially is dividing the mean difference by the standard error of the difference. Remember the t-test formula is as follows.

$$t = \frac{\bar{X} - \mu}{\frac{s}{\sqrt{n}}}$$

In the case of the paired-samples t-test, we take the difference between the post-test and the pre-test and generate the following, with the mean of the differences and the standard deviation of the differences.

$$t = \frac{\bar{X}_\text{diff} - 0}{SE} \text{   where   } SE = \frac{s_\text{diff}}{\sqrt{n}} $$
This gives us a t-statistic with degrees of freedom equaling n – 1, or the number of participants minus 1. If we had 50 people do the diet study, this would be 49 degrees of freedom, even though we have 100 observations (50 observations before the diet and 50 observations after the diet).

Imagine I did this study where I had 12 people do the diet study discussed above and got the results listed in the table below.

| Before Diet | After Diet         | Difference |
|-------------|--------------------|------------|
| 191         | 183                | -8         |
| 188         | 175                | -13        |
| 200         | 204                | 4          |
| 180         | 176                | -4         |
| 185         | 184                | -1         |
| 174         | 170                | -4         |
| 155         | 136                | -19        |
| 164         | 159                | -5         |
| 128         | 126                | -2         |
| 225         | 215                | -10        |
| 211         | 213                | 2          |
| 233         | 218                | -15        |
|             | Mean               | -6.25      |
|             | Standard Deviation | 6.95603    |

Notice in this example, I take the weight after the diet minus the weight before the diet, and then take the mean and the standard deviation of those difference scores. Then I take those numbers and do a one-sample t-test using those difference scores. 

$$t = \frac{6.25 - 0}{\frac{6.95}{\sqrt{12}}} = -3.125 $$

A couple of notes here: If the post-test is smaller than the pre-test, t will be negative. However, convention usually dictates that t-values are reported as positive, and since the t-distribution is symmetrical this does not change our results. When finding the p-value in R, the value for t must be positive. Second, there are 12 pairs of individuals, so we have 11 degrees of freedom.

Using the command in the last chapter, we can find out the p-value of getting a t-value of 3.125 or more extreme by the following:


```r
(1 - pt(3.125, 11))*2
```

```
## [1] 0.009663434
```

This $p=.009$, which indicates there is a .009 chance (.9%) chance that  these  results would have occurred if the null hypothesis is true, that is if there is no difference between pre-test and post-test. Thus, we would reject the null hypothesis.

##Independent Samples T-test

If we have two groups that are independent, that is, the two groups are not the same individuals, we can do an independent samples t-test. The formula for this test is the same t-test formula, but it has a few important tweaks.

We’ll use an example from the psychology of numbers for this study. A researcher may have the idea that people think underestimate how big something is if the numbers presented use fewer digits. For instance, \$4 million may seem like less money than \$4,000,000. The researcher believes that because people often see large money values like \$2.4 trillion as written as numbers with words rather than as only digits (e.g. $2,400,000,000,000), they may not appreciate how big it is.

The researcher has participants read a news article about Social Security and how the Social Security program will be facing a \$1 billion dollar shortfall. One group of participants reads the number as \$1 billion whereas the other group reads the number as \$1,000,000,000. After reading the article, participants rate on a 7 point scale how much of a problem they think the Social Security shortfall is. The researcher predicts the participants will think it is a bigger problem in the condition where the number is presented as only digits.

In this case, there are two groups of participants and each participant is only in one group. This is called a crossed design, because a given participant is only in one group. To analyze the differences between the groups, we would do an independent samples t-test.

Before we get started, we’ll use a few definitions. The groups are arbitrarily assigned. One group is called group 1 and the other is called group 2. Each group has a mean and a standard deviation. The null hypothesis is that the two groups come from the same population and means that the mean of group 1 is equal to the mean of group 2. The alternative is that the two groups are from two different populations and that the mean of group 1 is different from the mean of group 2. Again, since groups are assigned arbitrarily, it will not matter if it is a negative t-statistic or a positive t-statistic. Finally, the two groups do not need an equal number of people, as we’ll see below.

The basic t-test formula for independent samples t-tests is this:

$$t = \frac{\bar{x}_1 - \bar{x}_2}{SE}$$

Generally, standard error is the standard deviation divided by the square root of n. However, in an independent-samples t-test, we have two standard deviations, one for each group. If I had my experiment above, I would have the standard deviation for the group that read the story with the number expressed as words versus the group that read the story with the number expressed as digits. To calculate the standard error for the t-test, I have to somehow combine the two standard deviations into a “pooled” standard deviation. Standard deviations cannot be averaged together, so I use a more complex formula for this.

$$s_p = \sqrt{\frac{(n_1-1)s_{X_1}^2+(n_2-1)s_{X_2}^2}{n_1+n_2-2}}$$
This formula creates the pooled standard deviation. It is long because it weights each standard deviation based on the number of people in each sample. Since each group may have a different number of observations, we have to multiply the standard deviation of each group separately. 

Combining this to the other formula, we get this formula for an independent samples t-test.

$$t = \frac{\bar {X}_1 - \bar{X}_2}{s_p \cdot \sqrt{\frac{1}{n_1}+\frac{1}{n_2}}}$$

These formulas are complicated but if you have the right numbers, calculating a t-test by hand is simple, just plugging the correct numbers in the correct spots.

Here is how we do it:

1. Take each group, label one group “Group 1” and one group “Group 2”. Whichever one you pick as group 1 or 2 is arbitrary, but I generally assign the group I expect to have a larger mean as group 1 and the group I expect to have a smaller mean as group 2. Then set up the null and alternative hypotheses.
2. Find the following for each group: n (number of samples), , (that sample mean) and s (that sample standard deviation. In the formulas, which group each sample reflects is indicated with a subscript.
3. Plug the sample standard deviations and n into the pooled standard deviation formula to get the pooled standard deviation (sx1x2)
4. Plug the rest of the numbers into the equation to get t.
5. Find the degrees of freedom, which is n1 + n2 – 2 (total number of observations in both groups minus 2)
5. Use the following command in R to get the p value, given you have the t-value and degrees of freedom: `(1-pt(t, df))*2`

I’ll work through an example here. Imagine I wanted to see whether students in a traditional seated class or in an online class learned more material. I give both groups of students a final exam and use their scores on this exam for my dependent variable. I will give you the mean and standard deviations for this example:

|             | Seated class | Online class |
|-------------|--------------|--------------|
| Sample mean | 82           | 75           |
| Sample SD   | 9            | 13           |
| n           | 21           | 33           |

Let’s go through the steps:

1. Assign groups and set up null and alternative hypotheses. I will assign seated class to group 1 and online class as group 2. The null hypothesis is that the two groups are from the same population implying there are no differences between the two groups. The alternative hypothesis is that the two groups are from different populations, implying the two groups are from the same population.

2. Calculate means, SDs, and n for each group. Done. If you need more help with this, consult the module on summary statistics.

3. Find the pooled SD. Here is how that may work:

$$s_p = \sqrt{\frac{(21-1)9^2+(33-1)13^2}{21+33-2}}$$

$$s_p = \sqrt{\frac{20 \cdot 81 +32 \cdot 169}{52}} = 11.6$$

Step 4: plugging this in the t formula:

$$t = \frac{82-75}{11.6 \cdot \sqrt{\frac{1}{21}+\frac{1}{33}}} = 2.23$$

Step 5: Find degrees of freedom. These are equal to the total number of observations minus 2. In this case it is 52.

Step 6, find out the P value associated with T. To calculate this, we would type the following into R: 


```r
(1-pt(2.23, 52))*2
```

```
## [1] 0.03008958
```

This gives us a $p = .030$. This is below the generally accepted $\alpha = .05$, so we would reject the null hypothesis and conclude the groups are different. Given that the mean for the seated class is higher than the mean for the online class, we would conclude that the seated class performed significantly better on the exam. Whether that was due to the seated versus online nature of the classes or due to another confound is a question for research design.

##Effect sizes

When we investigate hypotheses using null hypotheses testing, we are examining how likely our data are given the null hypothesis is true. When used in a two-sample hypothesis, this is generally saying whether the two groups are the same or different. Generally this is because we want to say whether the characteristic that makes the two groups different, or the independent variable, causes a change in the dependent variable. This characteristic might be two different types of diet, or two different types of classes, or examining differences between girls and boys. 

This approach tells us how sure we are that there is a difference between the group but it says nothing about an important question: whether there is a small difference between the groups or a large difference between the groups.

Here’s an example: research shows that a diet where a person reduces their sodium intake may reduce one’s blood pressure. In this case, the null hypothesis is that those who have the low-sodium diet are from the same population as the group who does not have a low-sodium diet. The alternative hypothesis is that the two groups are not from the same population, which suggests that  one group has a lower blood pressure than the other group.

When I use null hypothesis testing, I will either reject or retain the null hypothesis, which helps me to answer the question of: does having a low-sodium diet help me to reduce blood pressure? However, this ignores a related question which may be of interest: how much does a low sodium diet reduce blood pressure?

This is the idea of effect size, as we discussed in Module 7. Effect sizes in two group hypotheses can be represented by the difference between the groups. One way of measuring effect size is by using a concept called Cohen’s D. Conceptually, Cohen’s D is a measure of the difference between two groups in terms of standard deviations. A Cohen’s D of 1 means that the two groups are one standard deviation apart.

To calculate this, you can use the following formula, assuming you have t, based on Rosenthal & Rosnow (1984):

$$d = \frac{2t}{\sqrt{df}}$$

$$d = \frac{2 \cdot 2.23}{\sqrt{52}} = .52$$

Cohen suggested the following criteria to evaluate D:

| Effect size       | Type of effect |
|-------------------|----------------|
| d < .3            | Small          |
| d > .3 and d < .7 | Medium         |
| d > .7            | Large          |

What this means is that if the difference between two groups is less than .3 standard deviations, the effect was small and generally not interesting. If the effect is between .3 and .7 standard deviations, the effect is a medium effect, which may be interesting

##The logic of t-tests and experimental design

One important element of designing experiments is designing our experiments so that they work. If we are testing whether there is a difference between two groups, we want to do our best to find a difference if a difference exists between the two groups. Using a t-test, there are three important elements you can do to make sure your experiment has the best chance of working.

This is a concept called **statistical power** or the ability to find an effect if one is present. We want to make sure our designs are as powerful as possible. To have more powerful designs, we want to make t-statistics bigger, because the bigger the t-statistic, the smaller the p-value and the more likely we reject the null hypothesis. How do we make the t-statistic bigger?

As noted in the section above, the t-test formula is:

$$t = \frac{\bar{x}_1 - \bar{x}_2}{SE}$$

We can describe this another way:

$$t = \frac{\text{Effect}}{\text{Error}}$$

The effect is the difference between the two groups. We've measured this in terms of effect size. If we want to find an effect, we want to make the effect as strong as possible. This means making the difference between the two groups as clear as possible. From a research point of view, we want to make the characteristic that divides the two groups as obvious as possible.

The second characterisic is error. To make t bigger, we want to make the error smaller. Error is measured by $\frac{s}{\sqrt{n}}$ and there are two ways to make this smaller. First, we can reduce $s$ or the standard deviation. This is done by making our experiment as controlled as possible. The last way is by increasing $n$. Bigger $n$ leads to bigger t-statistics and make it more likely that an effect is significant.

What does this mean to you? When designing an experiment, do the following:
1. Make your effect as big as possible. Make it as clear as possible what you are testing. For instance, if you are testing the effect of red ink versus blue ink, make sure the participants see a lot of red ink and a lot of blue ink. Sometimes a manipulation has to be subtle so that participants don't catch on to the experiment, but making manipulations as obvious as possible helps make experiments more likely to work
2. Reduce error. Try to make sure you reduce as many sources of error as you can.
3. Use large sample sizes. Try to use as many people as you can in order to test an experiment. Generally, you should have at least 30 participants in a study, unless you have a strong reason not to.

##Doing two-sample t-tests in R

T-tests in R are very simple and use the same `t.test()` command we used for one-sample t-tests. There are two ways of doing this, depending on how you set up your data. Imagine I have a dataframe that looks like the following:

| GroupA | GroupB |
|--------|--------|
| 1      | 3      |
| 3      | 4      |
| 5      | 8      |
| 6      | 2      |
| 2      | 13     |
| 3      | 15     |

I could put this into R using the following notation:


```r
GroupA = c(1,3,5,6,2,3)
GroupB = c(3,4,8,2,13,15)
d = data.frame(GroupA,GroupB)
```

To do a t-test comparing the groups, I would use the t-test command. If my data are set up where I am comparing two different columns, I would do the following commands. However, I have to tell R if it is a paired-samples or independent samples t-test. In the commands below, assume I have two vectors or columns, one named A and one named B.

For the paired samples t-test:

```r
t.test(A, B, paired = T)
```

For the independent samples t-test:

```r
t.test(A, B, paired = F) 
```

In the example given here, if I wanted to do a paired samples t-test, I would type:


```r
t.test(d$GroupA, d$GroupB, paired = T)
```

And if I wanted to do an independent samples t-test, I would type:

```r
t.test(d$GroupA, d$GroupB, paired = F)
```

If I do this, (for the paired samples t-test), I will get the following output:


```
## 
## 	Paired t-test
## 
## data:  d$GroupA and d$GroupB
## t = -1.652, df = 5, p-value = 0.1594
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  -10.64999   2.31666
## sample estimates:
## mean of the differences 
##               -4.166667
```

##Summary

After doing this chapter, you should be able to know and/or do the following:

1. Know what two-sample mean claims are and when to do them. Also know what the difference is between a paired and independent-samples t-test.
2. Know how to apply null hypothesis testing to two-sample mean claims
3. Know how to calculate a two-sample t-test by hand, whether it is a paired or independent-samples test.
4. Know some ways to increase t-statistics in order to make experiments more powerful
5. Know how to calculate two-sample t-tests in R.
