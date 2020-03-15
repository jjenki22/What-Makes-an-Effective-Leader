
## What Makes An Effective Leader?

Why are some managers better than others? Are there any general behaviors or characteristics that help a leader be perceived as more effective? The data I use in this analysis was given to me by Seth Berry and originates from a large survey of employees and their direct manager. In this dataset, each leader provided self-ratings and their direct subordinates provided rating about the leader. This is reflected by the `Rater` variable.  The data is structured the following way:

The *forceful* scale contains the following subscales: takes charge, declares, pushes

The *enabling* scale contains the following subscales: empowers, listens, supports

The *strategic* scale contains the following subscales: direction, growth, innovation

The *operational* scale contains the following subscales: execution, efficiency, order 

### Libraries Used in This Proejct:

```{r}
library(tidyverse)
library(pwr)
library(ggplot2)
library(MASS)
load("teamPerc.rdata")
teamPerc_1 <- teamPerc
```

### Three Hypotheses:

Hypotheses 1:

  - Leaders with more years of experience will have a higher effect rating than leaders with less years of experience.

  - If we compare the effect ratings of leaders with more years of experience with leaders with less years of experience, then we will see that leaders with more years of experience will have a higher effect rating.

  - h0: 
  
    - The effect rating for leaders with more years of experience = The effect rating for leaders with less years of experience

  - h1: 

    - The effect rating for leaders with more years of experience > The effect rating for leaders with less years of experience
  
Hypothesis 2:

  - Leaders who follow up with their employees (lvi40) will have a higher effect rating than leaders who do not follow up with their employees

  - If we compare the effect ratings of leaders who follow up with their employees with leaders who do not, then we will see that leaders who follow up with their employees have a higher effect rating.

  - h0: 
  
    - The effect rating for leaders who follow up with their employees = The effect rating for leaders who do not follow up with their employees

  - h1: 

    - The effect rating for leaders who follow up with their employees > The effect rating for leaders who do not follow up with their employees

Hypothesis 3: 

  - Leaders who are deemed forceful will have a lower effect rating than leaders who are not deemed forceful.

  - If we compare the effect ratings of leaders, who are deemed forceful with their employees with leaders who are not, then we will see that leaders who are forceful with their employees have a lower effect rating.

  - h0: 
  
    - The effect rating for leaders who are forceful with their employees = The effect rating for leaders who are not forceful with their employees

  - h1: 

    - The effect rating for leaders who are forceful with their employees < The effect rating for leaders who are not forceful with their employees

### Power Analysis:

Before I built any models, I decided to conduct an *a prior* power analysis and determine the sample size needed. The $f^2$ value can be calculated based on the following formula:

$$f^2 = \frac{R^2_{adjusted}}{1 - R^2_{adjusted}}$$
