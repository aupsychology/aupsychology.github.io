---
title: "Making Decisions With Statistics"
output: html_notebook
---

#Making Decisions with Statistics



In this chapter we will discuss how we use statistics and numbers to make decisions. Before we can talk about the techniques we use for these tests, we need to discuss the idea of **decision theory** or a branch of science and math that discusses how we make decisions based on what we know.

In this chapter, you will learn:

1. How do we use statistics to make decisions? This will include discussing the basics of decision theory and how we determine accuracy.
2. The idea of null hypothesis testing, which allows us to combine statistics and probability to make decisions about the validity of a hypothesis based on how likely the hypothesis is.
3. The idea of effect sizes, or how strong an effect is. This is different than the probability that a hypothesis is true.

##Basics of Decision Theory

You've made a lot of choices in your life. Some of those were good (like taking this class) and some choices were bad. You may not have used statistics specifically when you are making these decisions, but the idea of statistics plays a role in how you decide what you will do.

We do this in science too. When we want to decide which conclusion to make, we are making a decision based on the evidence. This occurs in almost any field of science, including psychology. 

Here is one example: When I am writing this chapter, fidget spinners have become all the rage, the popular toy of the moment. When you read this, it is very likely that fidget spinners will be a forgotten memory, so I should explain what they are. They are little disc-shaped toys that have ball bearings in the middle of them so that a person can hold the middle of the toy pinched between their thumb and forefinger, and spin the rest of the toy. 

One reason people like fidget spinners is because they claim the spinners can help them pay attention, especially if a person has ADHD. This is a claim. There may be good reasons to believe this claim is true. People who support this claim say that the low levels of background noise provided by fidget spinners helps people to focus. Also, many people like to do movements to help them pay attention. There's even real psychological evidence that doodling helps some people remember material from a lecture @andrade2010does.

However, there may be good reasons to believe this claim is false. As a professional curmudgeon, I find the claim that spinning little toys will make people perform better sounds incredibly absurd.

The point of statistics is that we collect data to test this claim and make an accurate decision about whether fidget spinners help people pay attention. By using statistics, we can help overcome some of our natural biases which may make us more likely to either believe things without evidence or disbelieve things despite compelling evidence.

In order to make decisions with data, we have to first consider what we mean by accuracy or determining how good we are at making the right decision. Accuracy may seem like a simple concept but it can be very confusing. At its simplest, accuracy is measuring the percent of times I make the right decision. For instance, I have 100 questions and I get 90 right, I have 90% accuracy. However, accuracy alone can give some counter-intuitive results.

Imagine I have two metal detector machines which are designed to go off whenever someone carries metal into a building. One metal detector is working and 95% of the time it detects metal when someone is carrying metal and 95% of the time it doesn’t detect metal when a person is not carrying metal. This means, 5% of the time, it misses metal that a person has and 5% of the time, it falsely says a person has metal when they don’t have metal. The second metal detector is is unplugged but no one knows this. So it never detects metal in any case and always says there is no metal present.

In this example, 1000 people walk through each metal detector and 5 of them are carrying knives. The first metal detector would catch all 5 people who are carrying knives, and of the 995 people who are not carrying knives, it would falsely say that 50 of them are carrying knives on average (5% of 995 is 50). So using the formula above, it has an accuracy of 95% or $\frac{950}{1000}$.

The second metal detector lets all 5 people who are carrying knives get through. But because it’s unplugged, it correctly lets all 995 people who are not carrying knives through. Its accuracy is $\frac{995}{1000}$, or 99.5%. In this case, the metal detector which is unplugged has higher accuracy than the metal detector which is on and has 95% accuracy. How can that be?

This is because accuracy has two components: the ability to detect something which is true or present and the ability to rule out something which is false or not present.

Signal detection theory is a theory that was developed to evaluate accuracy. In the 1930s and 1940s, the invention of radar made it possible to detect whether planes were in the distance, even when they couldn’t be seen. However, radar wasn’t perfect. There is noise in radar and other things, such as birds or weather phenomena could mimic what looked like a plane. The operators of radar had to test whether their radar worked by evaluating the accuracy of radar in different situations.

Signal detection theory breaks accuracy into two factors. The first factor is the absolute truth, whether something is present or absent whereas the second factor is our decision, whether we decide it is present or decide something is absent. Each of these two factors leads to four different situations, each depending on two factors. If we say something is present and it is actually present, this is a hit. If we say something is absent and it is actually absent, this is a correct rejection. However, if we say something is present and it is really absent, this is a false alarm, also called a false positive, whereas if we say something is absent but it is really present, it is a miss, or also called a false negative.

||We say object is present|We say object is absent|
|-|-|-|
|Object is present|Hit|False Negative (miss)|
|Object is absent|False Positive (false alarm)|Correct Rejection|

Another example is the fable of the boy who cried wolf. In this fable, there is a shepherd boy who is watching sheep and is supposed to cry if he sees a wolf. He cries out that a wolf is coming, even though he does not see a wolf. This would be a false positive, saying something is true when it is really false. However, after several false positives, the boy cries when he actually sees a wolf, which would be a hit. Unfortunately, in the fable, the townspeople were so tired of the boy’s cries that they ignored this cry. In that case, the townspeople would be committing a false negative, since they concluded the wolf was absent when the wolf was really present.
	
The reason this is important is because various tests or decision criteria vary in their ability to either detect something that is present or rule out something that is not present. This leads to two important calculations: false positive rate and false negative rate. The false positive rate is the proportion of all negative results that yield false positive. It is calculated as:

$$ \text{False Positive Rate} = \frac{\text{Number of False Positives}}{\text{Number of False Positives + Number of Correct Rejections}}$$

False negative rate is the reverse of this, the number of False Negatives when the results are positive (or true). It is calculated as:

$$ \text{False Negative Rate} = \frac{\text{Number of False Negatives}}{\text{Number of False Negatives + Number of Hits}}$$

False positive rate and false negative rates often reflect a tradeoff. This is especially the case in medical screenings, which are simple tests used to screen for the possibility of a disease. One example of this are mammograms, which are x-rays used to detect breast cancer. If a radiologist sees an abnormality on a mammogram, they have to decide whether to suggest additional testing, such as a biopsy which is a test with very high accuracy. If the abnormality is cancerous, additional testing is obviously a good thing. The radiologist may then decide to make sure that they suggest additional screening any time something is abnormal, because they do not want to have a false negative result and miss a cancer which is present. This would lead to a very low false negative rate since there would be very few false negatives when cancer is present (hits and false negatives).

But there is a tradeoff. The lower the false negative rate, the higher the false positive rate. Recommending biopsies and additional screenings any time there is even a slight abnormality will cause more false positives and a higher false positive rate. This may not seem like a big deal because we might think that missing a cancer which is present is much worse than a false positive. However, biopsies have side effects and complications, they cost a lot of money, and false positives cause a lot of worry. If you have ever been told you have an abnormal test result, you know how worrisome this may be. At a certain point, the cost of false positives outweighs the risk of a false negative.

In science, we have to make this tradeoff. If we only require a little bit of evidence to believe a hypothesis is true, we have a higher risk of false positives, and a lower risk of false negatives. This is called a **liberal** threshold However, if we require a lot of evidence to believe a hypothesis is true, we have a higher risk of false negatives and a lower risk of false positives. This is a **conservative** threshold.

For instance, if I have a liberal threshold, I may be more inclined to believe that fidget spinners help people concentrate. I would only require a little bit of statistical evidence to make that decision. I would have a higher risk of a false positive, believing that fidget spinners work when they don't work. 

On the other hand, I might have a conservative threshold and be less inclined to believe that fidget spinners help people concentrate. As a professional curmudgeon, this is my general perspective. In this case, I require a lot of evidence to change my belief. I have less of a chance of a false positive, but more of a chance of a false negative.

This kind of a tradeoff is what we will talk about in the next section.

## Null Hypothesis Testing 

Signal detection theory is a great analogue for how we make decisions in statistics. We always have uncertainty in our data but we want to know specific answers. Did our experiment work? Does watching violent TV cause kids to be more aggressive? Will taking a multivitamin every day improve health? Is studying in smaller chunks of time better than studying in one large chunk of time?

Many of our theoretical questions come down to yes/no answers about truth. However, statistics is only based on probability. If I run a study and find out that children who watched violent TV are more violent than children who did not watch violent TV, it could be the case that there is no difference in violence and I just happened to sample particularly violent children in the violent TV watching group and particularly nonviolent children in the no violent TV group.

Statistics is all about uncertainty, but at what point do we make decisions?
<!-- don't like this example, so may change later -->

Many statisticians in the mid 20th century tried to answer this problem by using the idea of null hypothesis testing. What these statisticians developed was a technique where we evaluated a pair of hypotheses and chose one based on the evidence.

We’ll talk about this through an example. A friend of yours says that he has gone to the future and has come back with knowledge about the future, a book that says the winner of a series of horse races. He wants to make a lot of money betting on horse races, but he doesn’t have any money to get started (probably because going to the future costs a lot of money). He says that if you give him money, he will tell you who will win and you both can make a fortune betting on these races.

Now, for good reason, you’re skeptical. But he says: come with me to the track and I’ll prove it to you. He looks in his book and he says that Chester will win the first race. And Chester wins the first race. Then he says Longfellow’s Pride will win the second race. And he’s right again. So now he says: do you trust me?

What’s your answer? Now based on what you know about probability, he could just be getting lucky. There might be a 20% chance he got the first race right just by guessing. And there might be a 20% chance he got the second race right by chance. Combined, that’s a 4% chance to get both right (20% * 20%). But if he keeps getting answers right, then it becomes less likely he’s getting lucky and more likely he’s telling the truth.

Null hypothesis testing sets up these questions with two hypotheses: the null hypothesis and the alternative hypothesis. These hypotheses are mutually exclusive, which means one has to be right and the other has to be wrong. Both can’t be true and neither can’t be true.

The null hypothesis generally asserts there is no relationship between two variables, or there is no special effects, there is no difference between two groups, or there is nothing abnormal about a situation. It is our baseline in science because science is skeptical and as scientists, we try to believe that nothing is true until proven otherwise. The alternative hypothesis is the opposite: it asserts the relationship we want to test. Since it is mutually exclusive with the null hypothesis, it asserts that there is a relationship between the variables or that there is a correlation or that something is present.

In our example above, the null hypothesis would be at its simplest: there is no relationship between the horses your friend picks and the horses who actually win. The alternative hypothesis would be: there is a relationship between the horses your friend picks and the ones who actually win. This is better than stating this a different way, such as saying a null hypothesis: your friend did not go to the future and an alternative being your friend did go to the future, because there are several other reasons your friend might be right about the horses, such as knowing secret information about which horses are better.

Good null and alternative hypotheses are specifically testable with statistics. The first set of hypotheses I listed above can be tested with probability. We can calculate the probability the horses your friend picked would win by chance alone. If that probability is somewhat low, you might think it’s a coincidence. But if the probability is very low, then we would conclude it’s likely your friend did go to the future.

Null and alternative hypotheses allow us to do statistical tests and make decisions based on the results of those tests. When we do statistical tests, we are finding out the probability that we would get the results we get if the null hypothesis is true. If that probability is high, we retain the null hypothesis because we do not have sufficient evidence to reject the null hypothesis. However, if that probability is low, we reject the null hypothesis because it becomes increasingly unlikely that the null hypothesis is true. When we reject the null hypothesis, we say that an effect is a significant effect.

This requires us to set a threshold where we consider the probability low enough to reject the null hypothesis. This is called the alpha level, and is traditionally set at .05, or 5%. If it is less than a 5% chance we would get our results if the null hypothesis is true, then we reject the null hypothesis. The alpha level is very similar to the false positive rate we talked about earlier.

Here is an example: your friend comes back to you and says he has a six-sided die that will usually land on 3. He says you can take this die and use it to win money betting on the results. He rolls the die eighteen times and 8 times it lands on 3. To use null hypothesis testing to evaluate this, we would do the following:

1. We set up null and alternative hypotheses. In this case, the null hypothesis would be that the die is no more likely to land on 3 than predicted by chance alone (that is, 3 is just as likely as any other number). In this case, the chance the die would land on 3 is 1/6. The alternative hypothesis would be the opposite of this: the die is more likely to land on 3 than would be predicted by chance alone.
2. Your friend runs the test and we find out the chance we would get the results we got or more extreme results if the null hypothesis is true. If there is a 1 in 6 chance of rolling a 3, there is a 5 in 1000 (.0053) chance that we would get 7 or more rolls of 3 in 18 rolls. When we do this, we don’t calculate the probability that we would just get 7 rolls because we are interested in outcomes that are more extreme than the outcome we’re interested in.
3. So we conclude there is a 5 in 1000 chance that this outcome would occur if the null hypothesis is true. If we use the alpha level of .05, we would reject the null hypothesis since it is less than 5% likely we would get these results if the null hypothesis is true.

There is one important distinction about hypothesis testing we must make. The probability we calculate is the chance we would get these results if the null hypothesis is correct. But, the opposite of the probability we calculate is not the chance the alternative hypothesis is correct. So in the example above, it is true that there is a 5 in 1000 chance that we would get those results if the null hypothesis is true, but it is not true that there is a 995 in 1000 chance that the alternative hypothesis is correct.

For instance, let’s go back to the example with the time-traveling friend. We calculate there is a 3% chance the null hypothesis is true, that the friend’s picks are not associated with the horses which actually win. That doesn’t mean there is a 97% chance that he is telling the truth about time traveling. Since the chance your friend went back into time is so remotely low (like one in a billion or more), it’s much more likely that he’s just getting lucky.

When we do null hypothesis testing, there are four possibilities, which reflect the same ideas we talked about in the last section. These are listed in the table below. If we reject the null hypothesis and the null is false, we made the right decision. However if we reject the null and the null is true, we have made a false alarm. In null hypothesis testing, this is called a Type I error. If we retain the null hypothesis and the null is true, we made the right decision. However, if we retain the null and the null is false, we have missed finding the truth. In null hypothesis testing, this is called a Type II error.

Type I and Type II errors depend on the type of testing we make and represent a tradeoff in accuracy. We set the chance of making a Type I error by using our alpha level. If we set a 5 percent chance for our alpha level, we are setting a 5 percent chance of making a Type I error if the null hypothesis is true. However, if we are more concerned about making a Type I error and want to be extra careful, we might reduce the probability that we require to reject the null hypothesis.

It is harder to calculate the probability of a Type II error because that depends on the magnitude of the effect. This addresses a concept called effect size, which we will talk about in the next section.

## Effect sizes

Null hypothesis testing is a good approach for making decisions but it has a lot of limitations. It has so many limitations that many people don’t use this approach any more. In fact, when I started to write this book, I was going to remove this approach and talk about other ways of doing statistical testing. However, it was only when doing this that I began to appreciate null hypothesis testing again.
	
Null hypothesis testing allows us to make a dichotomous yes/no decision. But many effects are more than yes/no decisions. For instance, I want to see if 5 minutes of guided meditation every morning would reduce people’s stress levels. I assign people randomly into two groups, one group which does guided meditation every morning and another group which spends 5 minutes doing whatever they want. Then I examine their stress levels.

In this case, the null hypothesis at its simplest would be that there is no difference between the two groups. The alternative hypothesis would be that there is a difference between the two groups. Imagine if you did a study and rejected the null hypothesis, concluding there is a difference between the two groups. You would say that you are confident that meditation helps to reduce stress. However, there’s an important factor missing here: how much does meditation reduce stress?

This is a concept called effect size and is separate, but related to the decision we talked about above. An effect size is a measure of how big an effect is. It answers the question: if I do X, how strong of an effect will X have. In the above example, it is a measure of how strong of an effect does meditation have on reducing stress. Does meditation reduce stress a little bit, or does it reduce stress a lot?

Effect sizes are related to our certainty of decisions, but they are not the same thing. In many cases it is easier to find bigger effects, but this isn’t true in all cases. So we might come up with situations like this: We can be 99.9% sure that meditation reduces stress, but does it matter if meditation only reduces stress a tiny bit?

Imagine we have two diets to treat blood pressure and we want to see if they actually work. After testing these using an experiment, we are 99.9% sure that people on diet 1 reduce their blood pressure. But on average, the diet only makes their blood pressure go down 2 points. However, we are only 95% sure diet 2 reduces blood pressure, but we found out on average diet 2 made their blood pressure go down 10 points. Which diet is better?

This is an open-ended question which is hard to answer but the point I want to make here is that how certain we are about the truth is not the same as how strong effects are. In medical literature, scientists often talk about clinically significant effects. This is a measure of the practical importance of an effect. A significant effect, like as mentioned in the last section, says we rejected the null hypothesis. However, rejecting the null hypothesis only tells us that we are sure something happened. It does not tell us that what happened was enough of an effect that it matters in the real world.

Giving someone a drug or a treatment has a cost. Knowing whether the benefit of that treatment is worth the cost is more than just evaluating whether we know the treatment makes a benefit. This is what is measured by effect sizes. In future chapters, we’ll learn how to calculate effect sizes as an additional piece of data to evaluate along with hypothesis testing.

## Summary

In this chapter, we covered ideas involving decision theory, null hypothesis testing, and effect sizes. After reading this chapter, you should know the following:

1. What is meant by hits, correct rejections, false positives, and false negatives. You should be able to calculate false positive rate and false negative rate and know what it means that there is a tradeoff between false positive rate and false negative rate
2. What is null hypothesis testing and how do we set up null and alternative hypotheses. Know specifically we are testing the probability we collect our data given that the null hypothesis is true
3. Know what it means to reject or retain a null hypothesis and how this relates to alpha and our p-value we calculate
4. Know some of the weaknesses of null hypothesis testing and what effect sizes are


