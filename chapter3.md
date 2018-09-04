---
title: 'Reshaping data'
description: ""
---

## Wide format data

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


`@hint`


`@pre_exercise_code`

```{r}
library('dplyr')
library('reshape2')
cars<-mtcars
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


