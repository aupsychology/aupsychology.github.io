
# (PART) Part 1: Basic Concepts {-}

# Chapter 1: Statistical Stories

My main goal for this book is to help you to love statistics. If I'm unable to do that, at least I hope that you won't be afraid of statistics and possibly find them useful. The best way to start this goal is to give some interesting stories about how statistics can be used.

##Story 1: To catch a thief

The worst sin in behavioral science is to make up data. We spend a lot of time collecting our data and so we treat our numbers like they are honest bearers of truth. We turn concepts into numbers and our numbers might be biased, or have errors, or mistakes, but we trust that they aren't completely made up.

However, there can be a lot of profit in making up numbers. Just changing a few digits here and there can be the difference between profit and loss for a company. A researcher might put years of effort into a study and when they found out the study didn't work, changing a couple 3's to a 6 or a 7 could be the difference between a big publication and losing their job.

But how do you catch someone when they make up data? There's a secret: real data are less random-looking than fake data.

Truly random data aren't really that random-looking. Imagine a coin-flip, which has a 50% chance of being heads and a 50% chance of being tails. If you're making up the results of 100 coin flips, you may think that you would make up 50 heads and 50 tails. However, the chance that you would get exactly 50 heads and 50 tails is only 8%. Fifty heads and 50 tails is the most likely single outcome, but it's far more likely you would get more than 50 heads than getting 50 heads exactly.

When we make up our data, we have a tendency to avoid repeats, when repeats are actually quite common in real data. In writing this, I randomly flipped a coin 100 times (actually I had R do this for me). The first 4 results were heads, followed by a tails, followed by 6 heads. This does not seem random at all, right? In fact it's perfectly random. Made-up data has fewer repeats.

Even if we take these properties in account, there might be other properites of random data we fail to analyze. For instance, imagine you wanted to make up numbers for your tax return. You have to create lots of "deductions" that were not real. You assume the IRS won't audit you if your data looks random enough and so you create lots of expenses for things you did not buy. You make sure your data look random and are spread out. You're careful that you don't use the same number all the time, especially with the first digit. You might make up numbers like this: "\$36.20, \$55.38, \$72.22" and so forth.

However, even this random list of numbers wouldn't be random at all and it's very possible the IRS could catch up this list of made-up numbers because of a property called *Binford's Law*. Binford's Law is the observation that in naturally occuring lists of numbers, or data, the first digit fits a unique pattern. Lower digits, like 1 and 2, are much more common than higher digits, such as 8 or 9. In fact, in a large enough sample, you would expect 30% of the numbers to have 1 as a first digit and 47% to have a 1 or a 2. Conversely, little more than 15% of the numbers start with a 7, 8, or 9.

This fact has been used to develop software to flag possible instances of fraud in financial data (@nigrini1996taxpayer). If the numbers submitted do not fit this distribution, an auditing group or investigator may ask for more detailed documentation, which can either prove innocence or, more commonly, prove wrongdoing.

##Story 2: The quirks of what we don't see

What do you think the chance that two people in your class share the same birthday? If your statistics class has more than 23 people, then there is a greater than 50% chance this would be true. This seems very unlikely because the probabiliy that someone shares your birthday is very low. But of all the people in your class, that probability keeps increasing until it's very high.

In World War II, aircraft designers wanted to figure out where to put armor on bombers in order to increase survival. The technicians had noticed that bombers would come back with many holes on some parts of the plane but other parts would rarely have holes in them. So they came to the conclusion that some parts of the plane were more likely to be hit, and so those parts needed more armor.

Abraham Wald was a statistician who saw the problem the opposite way. When he was asked about this problem, he suggested putting extra armor on the parts of the plane that had no holes and to ignore the parts that had many holes.

The designers were confused, but what Wald was seeing was that there was an important variable missing from the designers' analysis. They only saw the planes that made it back to the runway safely. There were many more planes that never made it back. Though the designers couldn't see where those planes had been damaged, Wald assumed that they were damaged in precisely the places which were undamaged in the planes that survived.

If antiaircraft gunners are shooting at planes from far away, there's no way they could aim for specific parts of the plane. The parts of the plane that got hit was random. When certain parts of the plane that were really critical to flying, such as the nose, were damaged, the plane was likely to crash. Therefore, none of the planes that returned had damage to those areas. It looked like those areas were unlikely to be hit, but in reality, those areas were just as likely to be hit, and when those areas were hit, it led to catastropic consequences. [@Mangel1984]

Psychology shows us that we have biases in what we see. We don't pay attention to what is important, but we have a subconscious bias to think what we're paying attention to is more important than it really is. The key is to find the variables which are unseen.

##Story 3: What causes cancer

The headlines were alarming: "Bacon Causes Cancer", "A Bad Day for Bacon", and so forth. This was serious and sad news (unless you're a pig). A scientific article in a very prominent journal said that bacon caused cancer (@Bouvard2015), and based on this research, the World Health Organization classified bacon and other processed meats as a group 1 carcinogen. Other group 1 carcinogens include tobacco and plutonium. Reading the list of group 1 carcinogens is like reading a list of substances likely to be used in a spy movie, more than one's diet.

So is bacon as bad for you as smoking? Or plutonium? No, absolutely not! 

And for good reason. There are two related but separate ideas in statistics when we are trying to determine an effect: how sure we are an effect is true and how powerful is that effect. Substances classified as group 1 carcinogens are those which are strongly linked to increasing one's risk for cancer. We have strong evidence that bacon and other processed meats does increase one's risk for cancer. But how much does it increase one's risk?

These studies measured something called *relative risk* or how much one's risk increases when they do something compared to a person's risk when they do not do the behavior. A person who eats two slices of bacon a day will increase their risk of colorectal cancer by 15-20%. This sounds like a lot. But this does not factor in something called *absolute risk* which is how likely something is in the general population. Colorectal cancer is not too common, and only 5% of people will suffer from this. Eating this much bacon may raise your risk from 5% to 6%. [For more information, see this.](https://www.wired.com/2015/10/who-does-bacon-cause-cancer-sort-of-but-not-really/). 

Conversely, smoking may raise your relative risk of lung cancer over 1000%. Smokers are 15 to 20 times more likely to suffer from lung cancer than nonsmokers. Less than .5% or 5 in 1000 non-smokers will suffer from lung cancer, whereas between 15-20% of smokers who smoke for many years will suffer from lung cancer. In this case the high relative risk translates into a high absolute risk.

When people look at diet studies, they often look at relative risk. The examples might be: eating X increases your chance of some medical condition 33%. But these studes do not measure how likely the initial condition is. If a medical condition is very rare, then raising your risk even 100% may not be that big of a deal at all.

Another example is aspirin as a medicine to reduce heart attacks. Aspirin can reduce the risk of a first heart attack more than 20%. That sounds great, right? Should we all start taking aspirin? Not exactly. Heart attacks may be relatively common, but only in people who are more disposed to heart attacks. [One analysis](https://www.propublica.org/article/when-evidence-says-no-but-doctors-say-yes) suggested that if 1000 middle-aged women take aspirin daily for a decade, it would prevent 11 heart attacks. However 22 of those women would suffer major gastrointestinal bleeds that they wouldn't suffer otherwise. The takeaway is that aspirin can be very effective for those who are at high risk for heart disease, but probably not for everyone.

##Story 4: Simpson's Paradox

One of the most famous quirks of statistics was an analysis of graduate admission data that the University of California: Berkeley did in 1973. They found the following results:

|Gender|Applicants|Percent Admitted|
|------|----------|----------------|
|Men|8,442|44%|
|Women|4,321|35%|

This showed a clear pattern that women were less likely to be admitted than men and so the administration feared a lawsuit. However, these data were missing one important variable: men and women applied to different departments. If you look at the six largest departments, the following pattern emerges


|Department|Female Applicants|Percent Admitted|Male Applicants|Percent Admitted|
|----------|-----------------|----------------|---------------|----------------|
|A|108|82%|825|62%|
|B|25|68%|560|63%|
|C|593|34%|325|37%|
|D|375|35%|417|33%|
|E|393|24%|191|28%|
|F|341|7%|373|6%|

Looking at these data, it is clear there is no overall pattern of discrimiation. Instead, women are more likely to apply to departments with low admission rates, such as department E and F whereas men are more likely to apply to departments with higher admission rates, such as A and B. In male-dominated departments, women are more likely to be admitted than men whereas there is almost no difference.

Simpson's paradox occurs when data show different patterns depending on how they are broken down. Many times, patterns we see when we look at data in aggregate or all combined, disappear when we break the data down. 

## The takeaway

Data tells a story and it is our job to help the data tell the most accurate story possible. It's impossible to be perfect, but we can try to find out what the data are really saying. 

The important takeaways from these examples is that often it's what we can't see that is important and so we need to try to look deeper and find out why things are happening. To do this, we should make sure we look at what is there and try to think about other variables or factors that may not be present. 

