
#Interactive Assignment 3: The tidyverse

This assignment explores the use of the "tidyverse", or a set of R packages designed to import, format, and analyze data in "tidy" formats. 

In this lab, we will:

1. How to use `filter()` to select part of your data
2. How to arrange and select data using the `arrange()` and `select()` funtions
3. How to use `mutate()` to make new columns in a dataframe.

To start with the tidyverse, you need to install the package 'tidyverse', which is a collection of useful packages used to analyze data. Do the following to install it:


```r
install.packages('tidyverse')
```

Then load the tidyverse package with the following:


```r
library('tidyverse')
```

For this assignment, you are going to work through Chapter 5.1-5.5 of R for Data Science. It is available at this link: http://r4ds.had.co.nz/transform.html

Read the chapter at the attached link and then answer the questions that are below when you get to them. Place your answers on this sheet by writing down the code or commands you would do in order to solve these problems.

If you're ambitious, you can work through sections 5.6 and 5.7 on your own.


1. Find all flights that:

* Had an arrival delay of two or more hours
* Flew to Houston (IAH or HOU)
* Were operated by United, American, or Delta
* Departed in summer (July, August, and September)
* Arrived more than two hours late, but didn’t leave late



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



2. Another useful dplyr filtering helper is `between()`. What does it do? Can you use it to simplify the code needed to answer the previous challenges?

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


3. How many flights have a missing dep_time? What other variables are missing? What might these rows represent?

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


*Section 2: arrange*

4. How could you use `arrange()` to sort all missing values to the start? (Hint: use `is.na()`).

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


5. Sort flights to find the most delayed flights. Find the flights that left earliest.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


*Section 3: select*

6. Brainstorm as many ways as possible to select dep_time, dep_delay, arr_time, and arr_delay from flights.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


7. What happens if you include the name of a variable multiple times in a `select()` call?

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


8. What does the `one_of()` function do? Why might it be helpful in conjunction with this vector?

`vars <- c("year", "month", "day", "dep_delay", "arr_delay")`

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


*Section 4: Mutate*

9. Currently dep_time and sched_dep_time are convenient to look at, but hard to compute with because they’re not really continuous numbers. Convert them to a more convenient representation of number of minutes since midnight.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


10. Compare air_time with arr_time - dep_time. What do you expect to see? What do you see? What do you need to do to fix it?

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


11. Compare dep_time, sched_dep_time, and dep_delay. How would you expect those three numbers to be related?


&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;


