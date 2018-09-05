---
title: 'Reshaping data'
description: ""
---

## Wide format data (1/2)

```yaml
type: NormalExercise 
xp: 100 
key: 9dec5b91fb   
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
xp: 100 
key: d309d1712e   
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
___ <- melt(___ , id.variable=c("___" , "___"))

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
xp: 100 
key: 613bdd1dea   
```


In some occasions we need to transform our data from long- to wide-format. We can achieve that with the `dcast` function.

Let’s take the long-format airquality data and cast it into some different wide formats. To start with, we’ll recover the same format we started with and compare the two.

dcast uses a formula to describe the shape of the data. The arguments on the left refer to the ID variables and the arguments on the right refer to the measured variables. Coming up with the right formula can take some trial and error at first. So, if you’re stuck don’t feel bad about just experimenting with formulas. There are usually only so many ways you can write the formula.

Here, we need to tell dcast that month and day are the ID variables (we want a column for each) and that variable describes the measured variables. Since there is only one remaining column, dcast will figure out that it contains the values themselves. We could explicitly declare this with value.var. (And in some cases it will be necessary to do so.)


`@instructions`


`@hint`


`@pre_exercise_code`

```{r}
library('dplyr')
library('reshape2')
by.date <- melt(airquality , id.variable=c("month","day"))
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

## Long format data (2/2)

```yaml
type: NormalExercise 
xp: 100 
key: 9d8f450abc   
```


Whereas going from wide- to long-format data is pretty straightforward, going from long- to wide-format data can take a bit more thought. It usually involves some head scratching and some trial and error for all but the simplest cases. 

If it isn’t clear what happened in the previous example, then have a look at the following illustration:
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

## EXERCISE 1

```yaml
type: PureMultipleChoiceExercise 
xp: 50 
key: 0ee984a37a   
```





`@hint`


`@possible_answers`


`@feedback`


