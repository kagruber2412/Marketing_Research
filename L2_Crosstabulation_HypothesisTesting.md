---
title: "Cross tabulation, elementary hypothesis testing"
sidebar: toc
category: getting-started
order: 1
---

#  Objectives

* Conduct $\chi^2$ analyses and tests.
* Understand how to use cross tables in practice and be able to interpret the results of different associated statistics.
* Be able to identify situations where it is useful to test hypothesis related to differences as well as to understand the differences in use of parametric and nonparametric tests.
* Be able to conduct analysis of variance and know how to interpret the results.
* **`R`**: working with data frames, advanced graph annotations, add-on packages.

# Overview of univariate tests


## Student t-test for independent sample means

**Usage:**

* To examine if there is a **difference in means** between **two independent groups** (= observations are drawn from different populations, e.g. males and females, buyers and non-buyers, ...).

* Judges the difference between two group means relative to their variability:

$$ t = \frac{\bar{x}_1 - \bar{x}_2}{\sqrt{\frac{\sigma^2_1}{n_1} + \frac{\sigma^2_2}{n_2}}}, \ \ with \ df = n_1 + n_2 - 2$$
$$ t = \frac{effect \ size}{noise}$$

-> small differences + loads of variability: **hard to detect**

-> large differences + low variability: **easy to detect**

**Assumptions:**

* Interval scaled variables and two independent samples
* Normal distributed data in each group (two sample means)
* Equal group variances (one pooled variance)

**Example:** *human weight data*

Are males and females differing significantly within their body weight?

```
# We simulate 150 random observations for two samples from
# two different normal distributions
set.seed(1234)
female <- rnorm(150, 55, 10)   # mean=55, sd=10
male <- rnorm(150, 65, 8.5)    # mean=65, sd=8.5
sex <- rep(c("female", "male"), each=150)
wdata <- data.frame("group"=sex, "weight"=c(female,male))
head(wdata)

# calculate mean and standard deviation for the two samples
mean. <- tapply(wdata$weight, wdata$group, mean)
sd. <-  tapply(wdata$weight, wdata$group, sd)
rbind(mean., sd.)
```
