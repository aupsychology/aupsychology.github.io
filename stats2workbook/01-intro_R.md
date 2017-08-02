



#Interactive Assignment 1: Introduction to R

The objectives of this lab is to learn the basics about using R. You will learn the following in this lab:

1. How to enter data into R by hand
2. How to do basic math functions
3. How to enter data into variables and data frames
4. How to do basic statistics on data frames, such as mean, median, mode
5. How to import data into R from csv files

This covers the learning objectives in Part 1: A, Understand the R language and how to use R to conduct basic math and statistical functions.

This lab is a review as an introduction to R. For more review, please read Chapter 4 of *Statistics: The Story of Data*. Before starting this lab, you need to install R and RStudio.

R is a command-line language, so all your commands are entered as text on the command line, called the "console". Try typing the following commands.


```r
1

3+4

x
```

If you type the things above, you should get output for the first two and an error for the third one. The error is because we haven't *defined* x or told R what x is.

When you see output, you may see a number in brackets, like if you type the output below:


```r
3*5
```

```
## [1] 15
```

For now, ignore the number in brackets. This is a way of telling which element is output. The number in brackets helps us if we have a long list of numbers, like if I type the following which lists the numbers 1 through 100. 


```r
1:100
```

```
##   [1]   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17
##  [18]  18  19  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34
##  [35]  35  36  37  38  39  40  41  42  43  44  45  46  47  48  49  50  51
##  [52]  52  53  54  55  56  57  58  59  60  61  62  63  64  65  66  67  68
##  [69]  69  70  71  72  73  74  75  76  77  78  79  80  81  82  83  84  85
##  [86]  86  87  88  89  90  91  92  93  94  95  96  97  98  99 100
```

The number in brackets tells me which value in the list is to the right of the number in brackets. So if I see, [20], I know that the number to the right is the 20th item in the list.

##Doing basic math in R

You can use R like a big calculator, using math notation. To add, use the plus key. To subtract, use the minus key. To multiply, use the asterisk key, and to divide, use the forward slash key. Exponents are used by the caret key. See below:


```r
3+7
4-11
4*21
18/3
2^2
```

Now in the space below, write how you would do the following:

11 times 22

&nbsp;

&nbsp;

&nbsp;

32 divided by 3

&nbsp;

&nbsp;

&nbsp;

11 minus 4

&nbsp;

&nbsp;

&nbsp;

Finally, R follows the basic order of operations, with information in parentheses done first, then exponents, then multiplication and division, followed last by addition and subtraction. So the following are different:


```r
3 + 11*5
```

```
## [1] 58
```

```r
(3+11)*5
```

```
## [1] 70
```
## Objects

The power of R though is that you can do a lot more than that. You can use things called **objects** which are, containers for data. An object can be anything from a single number to thousands and thousands of rows of data. Depending on what an object is holding, it can have different types. 

The simplest type of object is a variable. It is simply a letter or word that stands for a number. To make a variable you use the following (replacing the bracketed number with an actual number (like 42).

To assign a value to an object, we simply use equals, with the object on the left and the value to assign on the right.


```r
x = 1
```

When we assign something to an object, we don't get an output, since there is nothing for R to say. To see what an object says, we simply type the object.


```r
x
```

```
## [1] 1
```

The first type of object is called **numeric** and contains any number. Objects can also be **strings**, which are lists of text. They are entered by putting quotation marks around the data. Try typing the following.


```r
number = 4
name = "Michael"
day.of.week = "Tuesday"
question20 = 5
```

A third type of object is called a "logical" argument, and it has two choices: TRUE or FALSE (written in all caps). To shorten this, you can just use the letters T or F. Try the following:


```r
x = TRUE
y = F
```


We can also do math on objects, just like numbers.


```r
x = 3
y = 7
x*y
```

```
## [1] 21
```


Do the following in R and write your commands below:

1. Make an object that is named `name` as your first name and have that object be a string containing your first name.


&nbsp;

&nbsp;

&nbsp;


2. Make a second object that is called `age` and have it equal your age. Create a third object called `neighborage` and have that equal the age of the person sitting beside you. If you are alone, just make up a number.


&nbsp;

&nbsp;

&nbsp;


3. Add the objects `age` and `neighborage` together. What would you type?


&nbsp;

&nbsp;

&nbsp;


The power in R is that objects can have multiple values, called **lists**.  To make a list, we use the concantenate function `c()`. Type the following into R.



```r
x = c(1,3,5,7)
ages = c(19,22,37,41,18)
IQ = c(97, 132, 88, 101, 94, 107)
presidents = c("George","John","Thomas")
```

With lists, we can do functions which need more than one number, such as taking the sum of a list, the mean, and so forth. Try the functions below, which give the mean, the sum, and the standard deviation:


```r
mean(IQ)
sum(x)
sd(ages)
```

##Creating data frames

Lists are nice, but sometimes we want to hold a lot of organized data together, like a table. In R, these are called dataframes, and they have variables as separate columns with each row being an observation.

|Person|Name|Age|Worth|
|:-|:-|:-|:-|
|1|Alice|45|$5,000,000|
|2|Bob|39|$432,000|
|3|Cara|29|$87,000|
|4|David|66|$11,000|
|5|Ethan|54|$33,000|

Each row refers to a set of **observations**, which is a single person. Each column is a different set of data, or a **variable**.

Now we are going to make a dataframe. For example, I may want to make a dataframe with how many hours they slept and their number of items they got correct two different 25 question memory tasks.

|Name|Sex|Sleep|Memory Test 1|Memory Test 2|
|-|-|-|-|-|
|Zoe|Female|9|22|19|
|Yannick|Male|10|17|20|
|Xavier|Male|6|15|23|
|Wendy|Female|5|13|18|
|Vance|Male|5|10|8|

To do this, I have to make a list for each column and then combine them using the data.frame() command into the dataframe called "results". To do this, type the following (note I keep all the variable names in lower case; this is my convention but make sure you are consistent with capitalization):


```r
name = c("Zoe", "Yannick", "Xavier", "Wendy", "Vance")
sex = c("Female","Male","Male","Female","Male")
sleep = c(9,10,6,5,5)
memory1 = c(22,17,15,13,10)
memory2 = c(19,20,23,18,8)
results = data.frame(name,sex,sleep,memory1,memory2)
```

To see the dataframe, I would just type the dataframe's name, by using the View() command, which has a capital V

```r
View(results)
```
The View() command opens up a new window in the top right which lets me view the dataframe.

If we want to look at a single column, we would select it by first listing the data frame name, then a dollar sign, then the column name. To select the column for names, I would type:


```r
results$names
```

```
## NULL
```

We can do math to each of the columns. For instance, if I want to create a new column which is the sum of each of the three tests, I would type:


```r
results$memory.total = results$memory1 + results$memory2
```

Now I have created a new column called memory.total. Notice that I used a period in the middle of the column name to separate the words. This is something you can do to avoid using spaces. However, the column name shouldn't start or end with a period.

4. What would you type to select the memory.total column:

&nbsp;

&nbsp;

&nbsp;

5. How would you construct a column called memory.mean, which is the mean memory score for the two memory tests. Remember, you could just create this column by dividing the memory.total column by 2.

&nbsp;

&nbsp;

&nbsp;

##Part 2: inputting data from other sources.

For the second part of this assignment, we'll talk about how to input data into R using other programs. As mentioned in the reading, it's hard to put data into R manually, like what you just did with grades. So what we'll do is input data that has already been entered using another program. In this case, I have already entered the data into a spreadsheet and saved it using the name "lab1.csv". So please download this file off of Canvas and save it to your computer, preferably in the downloads folder.

Whenever I give you data to enter into R, I will also give you a key that tells you about each of the variables. When you make your own data (for a research methods project) it is a good idea to make your own key for when you share it with other people. Here is the key below. 

Variables: 
Person: person's name
Education: highest level of education completed: none, HS for high school, college for college, and graduate for graduate work
Sex: F for female, M for male
Test: type of test: Math or English
Score: score on a 50 question test

You can read this data into RStudio by going to the "Import Dataset" under the environment tab. Do this, loading the data into R with the variable name x. I like short variable names because they save typing

In the R terminal, type:

```r
x  = read.csv(file.choose())
```

This command should pop open a window that you can use to select the data you downloaded. Find the lab1.csv file you downloaded (probably in your downloads folder) and select it. This saves the data into R as a variable named x. To see what class of data it is, type `class(x)`

1. What class is x?

&nbsp;

&nbsp;

&nbsp;


To view the data in the RStudio viewer, type `View(x)` or you can click on X in the environment pane in R-studio (top right pane). Note that View has a capital V. On the top right, you should be able to see as summary of your workspace. This will tell you how many observations and how many variables are in your dataframe x.

2. How many observations are in x? How many variables?

&nbsp;

&nbsp;

&nbsp;


You can also find out how many rows and columns are in x by using the `nrow(x)` and `ncol(x)` command. Another command to find out the names of the columns is the `colnames(x)` command. 

3. What are the column names in dataframe x?

&nbsp;

&nbsp;

&nbsp;

An interesting thing about colnames is that you can use it to change the column names as well. Let's say we want to change the name of the Person to subject. Type the following to do this:


```r
colnames(x)[1] = "Subject"
```



This command changes the column name of the column specified with the brackets.

4. If you would want to change the name of the column called "Person" to "Name", how would you do that?

&nbsp;

&nbsp;

&nbsp;


Now we will review how to do summary statistics in R. The basic way to do this is by using the commands `mean()`, `median()`, and `sd()` for mean, median, and standard deviation. We have to give each of these commands a list of numbers. To calculate the mean scores, we would type:


```r
mean(x$Score)
```

5. What is the mean score? What is the median score?

&nbsp;

&nbsp;

&nbsp;


Often, when we are interested in data, we have to calculate what are called *aggregated* statistics. These are stats which are grouped by a different variable. One way to do this is to use the `describeBy()` function in the `psych` package. To install the psych package, type:


```r
install.packages('psych')
```

Once you've installed a package, you have to load a package by typing:


```r
library(psych)
```

Each time you start R again, you have to reload a package. You only have to install the package once, unless you have to reinstall R, for instance on a new computer.

Now that we've installed the `psych` package, we can use the `describeBy()` function. This function has two inputs, the first input is the variable you want to summarize and the second input is the variable that tells which group you want to use to group the data. For instance, if I want to see score broken up by gender, I would type:


```r
describeBy(x$Score, x$Sex)
```

6. How would you get the average score divided up by person, so that you get Alex's overall average, Bob's overall average, etc.


&nbsp;

&nbsp;

&nbsp;

7. How would I get the average score for each type of education?


&nbsp;

&nbsp;

&nbsp;



Sometimes I want to break up data by more than one variable. I can enter in multiple grouping variables by nesting them in the `list()` function, like this:


```r
describeBy(x$Score, list(x$Test, x$Sex))
```

Remember this because it may be useful for other data analysis.

##Terms and concepts to know:

After completing this lab, you should know what the following terms are:

*Objects
*Object classes: including numeric and string
*Lists
*Data frames, including observations and variables
*Packages

You should also be able to do the following skills. It is okay if you don't remember how to do them without looking them up.

*Understanding how to enter data into R using the c() command
*Understanding how vectors and data-frames work and how to select data from these
*Understanding what functions are in R, what arguments are, and how to use them.
*Understanding different data types in R
*Understanding what packages are, how to install and load them, and how to use them
*Knowing how to enter data into R from csv files and from Google sheets using the googlesheets package
*Knowing how to do basic summary statistics in R using the following: mean, median, mode, etc functions, using the describe function in the psych package

