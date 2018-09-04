---
title: 'Data Manipulations with Dplyr'
description: ""
---

## Insert exercise title here

```yaml
type: VideoExercise 
xp: 50 
key: 3769fa8b9b   
```

`@projector_key`
dd4e6085bd7725c658ebc41bb0ea17f0
---

## Selecting variables

```yaml
type: NormalExercise 
xp: 100 
key: 6987bd7422   
```


We can subset the columns (variables) that matter by using `select()`.

As an example, take the following call, that selects the variables `var1` and `var2` from the data frame `df`.

```

select(df, var1, var2)

```

You can also select columns based on the index of the column (position of the column). For instance, for selecting columns: one, three and five; you can use:

```

select(df, 1,3,5)
```

In addition, you can use `:` to select a range of variables and `-` to exclude some variables. For instance:

```

select(df, 1:4, -2)
```

`select()` does not change the data frame it is called on; you have to explicitly assign the result of `select()` to a variable (or object) to store the result.


`@instructions`
Using the dataframe `cars`, create an new variable called: `new.data` containing the range of columns from the first to the fifth column, excluding Horse Power (hp)

`@hint`
Use, select(name.of.your.dataframe ,  columns.to.be.selected)

`@pre_exercise_code`

```{r}
require('dplyr')
cars<-mtcars
```


`@sample_code`

```{r}
# Select first to fifth column excluding hp
new.data<- ____

# See the output of your code
head(____)
```


`@solution`

```{r}

```


`@sct`

```{r}

```


---

## Helper functions for variable selection

```yaml
type: NormalExercise 
xp: 100 
key: 6944788821   
```


`dplyr` comes with a set of helper functions that can help you select groups of variables inside a `select()` call. Some of the most important are:

- `starts_with("X"):` every name that starts with "X",
- `ends_with("X"):` every name that ends with "X",
- `contains("X"): `every name that contains "X",
- `matches("X"):` every name that matches "X", where "X" can be a regular expression,

Pay attention here: When you refer to columns directly inside select(), you don't use quotes. If you use the helper functions, you do use quotes.

For instance, to select from 'yourdata' only those columns containing the word "year" in their name, you can use:

```

select(yourdata, contains("year"))
```


`@instructions`
Create a new object called `variables` including only those columns from `cars` starting with the letter 'b'.

`@hint`


`@pre_exercise_code`

```{r}
require(dplyr)
cars<-mtcars
```


`@sample_code`

```{r}
# Subset columns starting with 'd' and store them in a new object called 'variables'.
___ <- ____
```


`@solution`

```{r}

```


`@sct`

```{r}

```


---

## Mutating  (creating)

```yaml
type: NormalExercise 
xp: 100 
key: 5815ff4cda   
```


`mutate()` creates new columns which are added to a copy of the dataset.

Take this example that adds a new column, z, which is the element-wise sum of the columns x and y, to the dataframe `df`:

```

mutate(df, z = x + y)
```

In the previous example, if there was a column already called `z`, R would replace the column values with the new calculation. Otherwise, a new column called `z` will be created with the calculation. 

You can also use `mutate()` to add multiple variables at once. Just place a comma between each variable that you define inside `mutate()`.

In the following example, a new variable `x` is directly reused to create the new variable `y`:

```

mutate(my_data, x = a + b, y = x + c)
```


`@instructions`
Create a new object called kilometres. The new object must contain all the data included in the dataframe `cars`, plus an additional column estimating the kilometres per gallon (kpg) consumed by each vehicles.  

One mile per gallon `(mpg)` is equivalent to 1.609 kpg.

`@hint`
Multiply the column mpg by 1.609 (`mpg * 1.609`)

`@pre_exercise_code`

```{r}
library('dplyr')
cars<- mtcars
```


`@sample_code`

```{r}
# Create a new object (kilometers) including an additional column calculating kilometres per gallog (kpg)
___ <- mutate( ___ , ___ )
```


`@solution`

```{r}
x<- "mazda"
```


`@sct`

```{r}
ex() %>% check_object("x") %>% check_contains("mazda")
```


---

## Filtering records

```yaml
type: MultipleChoiceExercise 
xp: 50 
key: d7c5a714bb   
```


`Filter()` can be used the subset records based on a given criteria. R comes with a set of logical operators that you can use inside `filter()`:

- `x < y`, TRUE if `x` is less than `y`
- `x <= y`, TRUE if `x` is less than or equal to `y`
- `x == y`, TRUE if `x` equals `y`
- `x != y`, TRUE if `x` does not equal `y`
- `x >= y`, TRUE if `x` is greater than or equal to `y`
-` x > y`, TRUE if `x` is greater than `y`
- `x %in% c(a, b, c)`, TRUE if x is in the vector c(a, b, c)

The following example filters `df` such that only the observations for which a is positive, are kept:

```

filter(df, a > 0)
```

By using the function `filter()` please determine how many vehicles weight more than 3 tons (`wt`), and have only 4 cylinders (`cyl`)


`@instructions`
- 2 cars.
- 3 cars.
- 1 car.

`@hint`


`@pre_exercise_code`

```{r}
library('dplyr')
cars<- mtcars
```


`@sct`

```{r}
msg1 <- "Well done!" 
msg2 <- "Incorrect. Please try again"
msg3 <- "Incorrect. Please try again"

ex() %>% check_mc(correct = 1,
                  feedback_msgs = c(msg1, msg2, msg3))
```


---

## Combining tests using boolean operators

```yaml
type: NormalExercise 
xp: 100 
key: a4256ea51e   
```


R also comes with a set of 'boolean operators' that you can use to combine multiple conditions. Examples of these are: `&` (and), `| `(or), and `! `(not). For instance, to filter in a table `df` the records with positive values in column 'a' and values equal to 'yes' in column b you can use: 

```

filter(df, a > 0 & b == 'yes')
```

Another handy function is: `is.na()`. This example keeps the observations in df for which the variable x is not NA:

```

filter(df, !is.na(x))
```


`@instructions`
Filter the vehicles from `data` weighting more than two tons (`wt` column), excluding those with 8 cylinders `(cyl)`.

`@hint`


`@pre_exercise_code`

```{r}
library(dplyr)
cars<- mtcars
```


`@sample_code`

```{r}

```


`@solution`

```{r}

```


`@sct`

```{r}

```


---

## Piping operator

```yaml
type: NormalExercise 
xp: 100 
key: 8f7a96ad99   
```


The Pipe operator `%>%` allows you to pipe the output from one function to the input of another function. Instead of nesting functions (reading from the inside to the outside), the idea of piping is to read the functions from left to right. Have a look at the following two examples that are completely equivalent: 

```{r , include=TRUE}
# EXAMPLE 1: Inefficient method
new.df<- select(df, mpg, wt)
new.df<- filter(new.df, mpg >16)
new.df<- head(new.df)

# EXAMPLE 2: Using Piping operator
new.df<- select(df, mpg, wt) %>% filter(mpg >16) %>% head()
```

Note that the Example 2, can also be rewritten positioning the dataframe `df` that you want to manipulate at the beginning of the expression. This is a common practice to make the code more intuitive for the reader.

```
new.df<- df %>% select(mpg, wt) %>% filter(mpg >16) %>% head()
```


`@instructions`
Create a new object called 'weight' containing only the weight column `wt`, and excluding those cars with a weight lower than 2 tons

`@hint`


`@pre_exercise_code`

```{r}
library('dplyr')
data<- mtcars
```


`@sample_code`

```{r}
# Store in a new object the weight column including only cars of more than 2 tons. 
weight<- ___
```


`@solution`

```{r}

```


`@sct`

```{r}

```


---

## Reordering your data (arrange)

```yaml
type: NormalExercise 
xp: 100 
key: 18fa35aea6   
```


To arrange (or re-order) rows by a particular column, you can list the name of the column you want to arrange the rows by. 

For instance, to re-ordering the `data` based on the column Miles per Gallon (mpg) you can do:

```
data %>% arrange(mpg)
```

You can also re-order your data based on multiple columns (e.g. first by miles per gallon, then by weight)

```
data %>% arrange(mpg, wt)
```

By default, arrange() arranges the rows from smallest to largest. You can reverse this behavior with the desc() function. arrange() will reorder the rows from largest to smallest values of a variable if you wrap the variable name in desc() before passing it to arrange().

```

data %>% arrange(desc(mpg))
```


`@instructions`
Arrange `data` in a new object called cylinders, so that vehicles with the same number of cylinder `(cyl)` appear next to each other. In addition, heavier cars should appear before lighter cars.

`@hint`


`@pre_exercise_code`

```{r}
library('dplyr')

data<-mtcars
```


`@sample_code`

```{r}

```


`@solution`

```{r}
#top
```


`@sct`

```{r}

```


---

## Summarising data

```yaml
type: MultipleChoiceExercise 
xp: 50 
key: d07a8068a7   
```


The `summarise()` function will create summary statistics (e.g. mean) for a given column in your dataframe. For instance, you can use the following code to estimate the average and standard deviation of the vehicles' weight: 

```

> cars %>% summarise(avg_wt = mean(wt), sd_wt = sd(wt))
```

Note in the previous code that `avg_wt` and `sd_wt` are just the names that were given to those calculations, but any other name could have been used.  

Apart from `mean`, some examples of aggregating functions that you can call from summarise() are:

- min(x) - minimum.
- max(x) - maximum.
- mean(x) - mean.
- median(x) - median.
- quantile(x, p) - pth quantile.
- sd(x) - standard deviation.
- n_distinct() - number of distinct values.

Now, using the `summarise()` function determine how many different type of cars the dataframe contains based on the number of `gears`. Also, estimate the average Miles per Gallons (`mpg`) of all th icles in the data set.


`@instructions`
- 3 different type of cars based on the number of gears and 22.13 mpg in average.
- 2 different type of cars based on the number of gears and 21.60 mpg in average.
- 3 different type of cars based on the number of gears and 20.09 mpg in average.

`@hint`


`@pre_exercise_code`

```{r}
library('dplyr')
cars<-mtcars
```


`@sct`

```{r}
msg1 <- "Incorrect. Please try again"
msg2 <- "Incorrect. Please try again"
msg3 <- "Well done!" 

ex() %>% check_mc(correct = 3,
                  feedback_msgs = c(msg1, msg2, msg3))
```


---

## Group operations

```yaml
type: MultipleChoiceExercise 
xp: 50 
key: 364aaa0539   
```


The `group_by()` verb allows you to split the dataframe by some variable (e.g. number of cylinders), and then apply summarising statistics for the different groups separately

For instance, to compare the average weight (`wt`) of cars with different type of transmission (`am`), you can use the following code:

```

cars %>% group_by(am) %>% summarise(mean(wt)) 
```

Your challenge now is to combine `group_by()` and `summarise()` to find out how many gears (`gear`) have the vehicles with the highest average petrol consumption (`mpg`).


`@instructions`
- 3 gears.
- 4 gears.
- 5 gears.

`@hint`


`@pre_exercise_code`

```{r}
library('dplyr')
cars<-mtcars
```


`@sct`

```{r}
msg1 <- "Incorrect. Please try again"
msg2 <- "That's correct, cars with 4 gears have the highest average mpg (24.5)"
msg3 <- "Incorrect. Please try again" 

ex() %>% check_mc(correct = 2,
                  feedback_msgs = c(msg1, msg2, msg3))
```


