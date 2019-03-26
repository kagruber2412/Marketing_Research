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



