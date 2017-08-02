
#Interactive Assignment 2: Reviewing Inferential Statistics

In this lab, we will review how to do t-tests and correlations in R. This lab assumes that you have covered the theory behind these tests in a previous class.

After completing this lab, you should be able to:

1. Import data into R from Google Sheets using the gsheet package
2. Know how to conduct a t-test in R and interpret the output
3. Know how to conduct a correlation in R and interpret the output.

In this lab, we will use some data that some students collected for a research project previously. In this project, the researchers gave students a 

First we are going to import the data. In this case, the data were entered on Google Sheets. To import data straight from Google Sheets, we can use the `gsheet` package. To install this package, we would type:


```r
install.packages(gsheet)
```

And to load the package, we would type:


```r
library(gsheet)
```

Now to load the package, we have to use this link. You can paste in this link and then type the command below.


```r
link = 'https://docs.google.com/spreadsheets/d/1zZjEhkT4ROACTM4YsW1LTNn8al_scyu9l4_Qkzqvsew/edit?usp=sharing'
d = gsheet2tbl(link)
```

Whenever you share data, you should always include a guide that tells people what each variable is and what the variables represent. In this case, the variables are named as follows:

Participant: a participant number
E: extraversion score
A: agreeableness score
C: conscientiousness score
N: Neuroticism score
O: Openness score
Gender: gender coded F and M
Age: participant age
Conformity: their score on a survey about how much they would conform
RATING: a participant's rating to the question "how much do I think I conform to others' behaviors"
SelfEsteem: a score on a self-esteem inventory with higher scores indicating more self-esteem

##Part 1: Summary Statistics

We are going to use the `describe()` and `describeBy` functions in the `psych` package to first look at some summary statistics. You can see more about these functions in the last assignment. First, we'll load the psych package.


```r
library('psych')
```

In the psych package, you can use the `describe` function to get a summary about a variable, with several summary statistics. For instance, to look at a summary of the extraversion variable, we would type:


```r
describe(d$E)
```

```
##    vars  n  mean   sd median trimmed  mad min max range  skew kurtosis
## X1    1 60 25.67 7.16     26   25.67 9.64  10  40    30 -0.01    -0.94
##      se
## X1 0.92
```

Notice that this tells us the mean for extraversion is 25.67 with a standard deviation of 7.16. It also gives us the median, minimum, maximum, and other statistics.

1. Use the describe function to find the mean and standard deviation of the other 4 personality tests (agreeableness, conscientiousness, neuroticism, and openness, along with the Conformity variable). Create a table below with the means and standard deviations of each of these variables.


&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

###Examining Gender Differences Using T-tests

Now we are going to see if there are any differences between male and female participants in their scores on the personality inventories and in conformity. To conduct t-tests, we can use the `t-test()` function in R. 

There are two ways to do t-tests in R. The first way is to give R two different variables as two different arguments. For instance, if we wanted to compare to see whether extraversion is higher than neuroticism, we would type the below code.


```r
t.test(d$N, d$E)
```

However, comparing how high extraversion is to neuroticism doesn't make sense. We want to compare a single personality trait with another variable that tells us which gender a person is. To do that, we have to enter data  different way. 

This function has one input, but it has two variables divided with a tilde. The first variable is the dependent variable and the other is the the grouping variable that tells what category an observation is in. The independent variable must have exactly 2 levels, because a t-test only compares 2 groups. This makes the `Gender` variable a good candidate.

To do a t-test for the Extraversion variable with Gender as an independent variable we would type:


```r
t.test(d$E~d$Gender)
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  d$E by d$Gender
## t = 0.20057, df = 25.11, p-value = 0.8426
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  -3.740950  4.548403
## sample estimates:
## mean in group F mean in group M 
##        25.76087        25.35714
```

This is the output you should get with this test. The second line of the output is the one you are most interested in. This tells us the t value, the degrees of freedom (abbreviated df), and the p value. The degrees of freedom is a corrected value, so it is often a decimal.

The 95% confidence interval is on the 5th line, and the last line has the mean of the variable for each group. Notice in this case that the group F for female is very close to the value for group M, for male, which is why this t-test is not significant.

2.  Using this function, do a t-test for the other 4 personality variables and conformity. Report your t-value and p-value for each of the tests below, using APA formatting: *t*(df) = tvalue, *p* = pvalue.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


###Correlation with R

The researchers were interested in whether there was a correlation between the personality variables and conformity. To test whether a correlation is present, we can use the `cor.test()` function in R. This function requires two input variables, which will be correlated. To see the correlation between Extraversion and Conformity, we would type:


```r
cor.test(d$E, d$Conformity)
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  d$E and d$Conformity
## t = 1.2445, df = 58, p-value = 0.2183
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  -0.09660536  0.39886592
## sample estimates:
##       cor 
## 0.1612755
```

The last number gives us the correlation. The significance of the correlation is listed as a p-value in the second row, along with the degrees of freedom. In this case, we have a small and insignificant correlation between Extraversion and Conformity, *r*(58) = .16, *p* = .21.

3.  Using the correlation function, examine if there are any correlations between the other 4 personality variables and conformity. Report your r-value and p-value for each of the tests below, using APA formatting.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

4. Using the `cor.test()` function, examine if there are any correlations between SelfEsteem and conformity? 

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

5. Is the Conformity variable correlated with the RATING variable? How so?

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


