
#Free Assignment 1: Reviewing R

Free assignments are assignments where I give you a data source and ask a series of questions about it with minimal guidance. You should use what you've learned in the interactive assignments to complete these assignments.

In this assignment, we will review the principles in Interactive Assignment 1 and Interactive Assignment 2. You can feel free to look back in those assignments to figure out how to answer these questions.

For this assignment, we are going to look at data from a study examining how mentalizing, or trying to figure out what another person is thinking, affects face memory. The idea of this study is that if you mentalize more about a person, then you will remember their face better.

One way to study memory is by giving people a list of items to remember (in this case faces), and then testing them later by showing them the faces they saw before (the previously seen faces) along with new faces they have not seen before. Then what we do is ask people to indicate whether the face is a face they have seen before or a new face that they have never seen before. 

During this testing period, people have to make one of four choices. They have to say they are very confident they have seen the face before, somewhat confident they have seen the face before, somewhat confident that the face is new and they haven't seen it before, and very confident that the face is new and they haven't seen it before.

To test our hypothesis, we had participants see a face presented with an adjective and the people had to answer a question of how much they thought that adjective fit the person pictured. For instance,the adjective might be "excited" and they would answer how much they thought "excited" fit the person pictured. Afterward, the participants had to complete a memory test where the people they saw were mixed with people they had never seen before. The idea was that when a person was paired with a complex mental state adjective, that required more mentalizing, the person was more likely to be remembered than when they were presented with a basic mental state adjective which required less mentalizing.

The data for this study are available as the FA1memdata.csv file. The first step is to import that data using the `read.csv()` command. Import the data to the data frame named "d" Once you import it, you should see the dataframe in your environment. It has 81 observations of 14 variables.




This dataframe has several variables. You can see the variable names by clicking the data frame in the "Environment" window in the top right. Here is a guide to what the variables mean.

* Subject: Subject number
* Age: Participant Age
* Sex: Participant Sex
* novelACC: accuracy for novel items (faces in the memory test which were not seen before)
* seenACC: accuracy for seen items (faces in the memory test which were previously seen)
* overallACC: accuracy for all faces.
* ComplexHCH and BasicHCH: High confidence hits for faces shown with complex adjectives and basic adjectives respectively. A high confidence hit is when a person sees a face they have seen before and answers that they are very confident they saw that face before.
* ComplexLCH and BasicLCH: Low confidence hits for faces shown with complex adjectives and basic adjectives respectively. A low confidence hit is when a person sees a face that they have already seen and says they are only somewhat sure they have seen that face before.
* ComplexLCM and BasicLCM: Low confidence misses for faces shown with complex adjectives and basic adjectives respectively: A low confidence miss is when a person sees a face they have previously seen before and says that they are somewhat confident that they *did not* see that face previously.
* ComplexHCM and BasicHCM: High confidence misses for faces shown with complex adjectives and basic adjectives respectively. A high confidence miss is when a person sees a face they have previously seen before and says they are very confident they did not see that person before.

Our theory is that memory for faces presented with complex adjectives will be better than memory for faces presented with basic adjectives. Therefore we expect the following:

1. Complex HCH will be higher than Basic HCH - since high confidence hits is the strongest form of memory.
2. Complex LCH may be higher than Basic LCH - low confidence hits is a weaker form of memory, so this might be the case
3. Basic LCM will be higher than Complex LCM - misses reflect faces that were forgotten, so we expect fewer faces are forgotten when paired with complex adjectives
4. Basic HCM will be highter than Complex HCM - high confidence misses are rare, but they should be more likely when a face is paired with a basic adjective.

##Basic descriptive statistics

Using the psych package, create basic descriptive statistics to create a table to answer the following question

1. Mean and standard deviation for all variables (except Subject and Sex)
&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

2. Use the describeBy function to evalulate the means and standard deviations for the novelACC, seenACC, and overallACC variable for males and females separately, using Sex as a grouping variable. Create a table to report your answers below:

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


1. Mean and standard deviation for all variables (except Subject and Sex)
&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

3. Using a t-test, see whether there are any differences between males and females in their scores in the novelACC, seenACC, and overallACC variable. Report the t-values using APA formatting below:


1. Mean and standard deviation for all variables (except Subject and Sex)
&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

4. Now we are going to test the main hypotheses of interest. Examine whether there is a significant difference between ComplexHCH and BasicHCH. This will be a paired-samples t-test, so you will type the following into R:


```r
t.test(d$ComplexHCH, d$BasicHCH, paired = TRUE)
```

Is there a significant difference? Which variable has a higher mean? Do the results support the researchers' hypothesis?

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

5. Now do the following for the LCH, LCM, and HCM variables. Are there any significant differences between the basic and complex adjectives for each of these situations? Report the t-values and p-values below


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

6. When looking at all the results, do these results support the theory that memory is stronger for faces presented with complex adjectives than for faces presented with basic mental state adjectives? Why or why not? You should use your answers to the questions above in order to answer these questions.


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
