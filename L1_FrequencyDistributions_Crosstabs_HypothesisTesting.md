---
title: "Frequency distribution, cross tabulation, elementary hypothesis testing"
sidebar: toc
category: getting-started
order: 1
---

# Contents

* Create descriptive statistics and graphs
* Calculate means and standard deviations of a distribution of observations
* Conduct $\chi^2$ analyses and tests
* Understand how to use cross tables in practice and be able to interpret the results of different associated statistics
* **`R`**: working with vector and matrix objects (indexing, numerical operations), simple graph annotations.

## Descriptive statistics

* to obtain an initial idea of the dataset
* to perform data cleaning
* to determine the most important characteristics of different variables in a dataset
* different for nominal/ordinal (discrete) and metric (continuous) data = **levels of measurement**

## Levels of measurement

### Discrete data

* **Nominal scale:** categories or qualitative classifications
  
  mathematical operations: $=$, $\neq$
  
  e.g.: male, female
  
  **`R`** data type: character, logical, factor


* **Ordinal scale:** sorted categories
  
  mathematical operations: $>$,$<$,$\geq$,$\leq$
  
  e.g.: **likert scale**: completely agree, mostly agree, mostly disagree, completely disagree (subclass of **rating scale**, sometimes treated as "pseudo-meteric")
  
  **`R`** data type: factor, numeric (integer)

### Continuous data

* **Interval scale:** scales with an arbitrary defined zero point
  
  mathematical operations: $+$, $-$
  
  e.g.: celsius scale, direction (measured in degrees from true or magnetic north), also sometimes rating scales (attitude and opinion scales)
  

* **Ratio scale:** possesses a meaningful zero value, most measurement in the physical sciences and engineering is done on ratio scales

  mathematical operations: $\star$,$\div$
  
  e.g.: kelvin scale, age, income, price, costs, sales revenue, sales volume, market share, ...
  
  **`R`** data type: numeric (double)


## Discrete variables: Example (1)


## Discrete variables: Example (2)

What were the most common words in Trump's tweets?


## Discrete variables: Frequency tables (1)

* to obtain a count of the number of responses associated with different values of **one** variable
* to indicate how scores of respondents are distributed over meaningful categories

**Example:** *Trump's twitter behavior*
5109 words obtained from tweets based on Trump's phones (during the presidential election campaign in 2016) had been categorized into 10 sentiments using the NRC Word-Emotion Association lexicon.

**Research question:** How is the word sentiment of tweets distributed?


## Discrete variables: Frequency tables (2)

* obtain how responses are distributed over the range of possible values (number and percentages for each response category)

```
# generate the data
name <- c("anger", "anticipation", "disgust", "fear",
            "joy", "negative", "positive", "sadness",
            "surprise", "trust")
dat <- c(rep(name[1],490), rep(name[2],428), rep(name[3],304),
         rep(name[4],403), rep(name[5],355), rep(name[6],820),
         rep(name[7],967), rep(name[8],450), rep(name[9],266),
         rep(name[10],626))
```
```
# inspect data
head(dat)
```
```
# obtain a frequency table
table(dat)
```



