---
title: 'Reshaping data'
description: ""
---

## Wide format data (1/2)

```yaml
type: NormalExercise
key: 9dec5b91fb
xp: 100
```

People often find it easier to record their data in wide format. In this format, each different data variable is presented in a separate column. For instance, the following dataframe contains 6 different columns with information about `airquality` measurements.

```
> head(airquality)
  Ozone Solar.R Wind Temp Month Day
1    41     190  7.4   67     5   1
2    36     118  8.0   72     5   2
3    12     149 12.6   74     5   3
4    18     313 11.5   62     5   4
5    NA      NA 14.3   56     5   5
6    28      NA 14.9   66     5   6
```

However, you need long-format data much more commonly than wide-format, specially if you want to do data visualisations in R or Tableau.  

You can use the function `melt()` (from the package reshape2) to transform the data from wide format to long format.

`@instructions`
Apply the function `melt()` and store the output in a new object called `long`

`@hint`


`@pre_exercise_code`
```{r}
library('dplyr')
library('reshape2')
cars<-mtcars
```

`@sample_code`
```{r}
# Create the object 'long' reshaping airquality to long format
___ <- melt(___ , ___)

# Explore the first few records of 'long'
head(___)


# Explore the last few records of 'long'
tail(___)
```

`@solution`
```{r}

```

`@sct`
```{r}

```

---

## Wide format data (2/2)

```yaml
type: NormalExercise
key: d309d1712e
xp: 100
```

By default, `melt` assumes that all columns with numeric values are variables with values. Often this is what you want. However, in our previous example we may want to know the values of `ozone`, `solar.r`, `wind`, and `temp` for each `month` and `day`. We can do that with `melt` by telling it that we want `month` and `day` to be “ID variables”. ID variables are the variables that identify individual rows of data, and remain constant while the rest of the data is reshaped.

`@instructions`
Create a new variable called `by.date` in which `airquality` is transform into long format, but the columns `month` and `day` are kept as ID variables.

`@hint`


`@pre_exercise_code`
```{r}
library('dplyr')
library('reshape2')
cars <- mtcars
```

`@sample_code`
```{r}
# Create the object 'long' reshaping airquality to long format
___ <- melt(___ , id.vars = c("___" , "___"))

# Explore the first few records of 'by.date'
___(by.date)


# Explore the last few records of 'by.date'
tail(___)
```

`@solution`
```{r}

```

`@sct`
```{r}

```

---

## Long format data (1/2)

```yaml
type: NormalExercise
key: 613bdd1dea
xp: 100
```

In some occasions we need to transform our data from long- to wide-format. We can achieve that with the `dcast` function.

For instance, we can take the `by.date` variable that we just created (long-format airquality data) and cast it to recover the same format we started with.

`dcast` uses a formula to describe the shape of the data. The arguments on the left refer to the ID variables and the arguments on the right refer to the measured variables. 

```

dcast(by.date, month + day ~ variable)
```

In the previous formula, we told `dcast` that `Month` and `Day` are the ID variables (we want a column for each) and that `variable` describes the measured variables. Since there is only one remaining column, `dcast` will figure out that it contains the values themselves. We could explicitly declare this with `value.var`. (And in some cases it will be necessary to do so.)

`@instructions`
Apply the `dcast` function to the `by.date` object as shown in the previous formula and store it in a new variable called `original`

`@hint`


`@pre_exercise_code`
```{r}
library('dplyr')
library('reshape2')

```

`@sample_code`
```{r}
# Run the code below to create the by.date variable again
by.date <- melt(airquality, id.vars = c("Month", "Day"))

# Create object 'original' to recover the same format we started with
___ <- dcast(___, ___ + ___ ~ variable)

# Explore the first few records of 'original'
head(___)


```

`@solution`
```{r}

```

`@sct`
```{r}

```

---

## Long format data (2/2)

```yaml
type: NormalExercise
key: 9d8f450abc
xp: 100
```

Whereas going from wide- to long-format data is pretty straightforward, going from long- to wide-format data can take a bit more thought. It usually involves some head scratching and some trial and error for all but the simplest cases. 

To have a better understanding of the example in the previous section, have a look at the following illustration:

![](https://seananderson.ca/images/dcast-illustration.png)

The blue shading indicates ID variables that we want to represent individual rows. The red shading represents variable names that we want to swing into column names. The grey shading represents the data values that we want to fill in the cells with.

`@instructions`


`@hint`


`@pre_exercise_code`
```{r}

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

## Final Practice

```yaml
type: MultipleChoiceExercise
key: cf82633e3d
xp: 50
```

Using the `airquality`, find out what is the month of the year with more variability in `ozone` measures?

`@instructions`
- May (5)
- June (6)
- July (7)
- August (8)

`@hint`


`@pre_exercise_code`
```{r}
library(dplyr)
```

`@sct`
```{r}
msg1 <- "Incorrect. Please try again"
msg2 <- "Well done!" 
msg3 <- "Incorrect. Please try again"
msg4 <- "Incorrect. Please try again"

ex() %>% check_mc(correct = 2,
                  feedback_msgs = c(msg1, msg2, msg3, msg4))
```
