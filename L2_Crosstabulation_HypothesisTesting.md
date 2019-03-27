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

### Check assumption 2: Normal distribution within both groups.

```
# a more advanced histogramm:

hist(female, col=adjustcolor("purple", 0.6), main="", breaks=15, border=NA, prob=TRUE, xlab="Body weight", ylim=c(0,0.06))

hist(male, col=adjustcolor("steelblue", 0.6), add=T, breaks=15, border=NA, prob=TRUE)

lines(density(female, n=150, cut=5)$x, density(female, n=150, cut=5)$y, lwd=4, col="purple")
lines(density(male, n=150, cut=5)$x, density(male, n=150, cut=5)$y, lwd=4, col="steelblue")

# add a legend to the plot
legend("topleft", legend=c("female","male"), fill=c("purple","steelblue"), border=NA, bty="n", cex=2)
```

## Excursus: Boxplot

* Graphical method for depicting groups of numerical data through their quartiles.
* The spacings between the different parts of the box indicate the degree of dispersion (spread) and skewness in the data, and shows outliers.
* The bottom and top of the box are always the first (25th) and third (75th) percentile, the band inside the box is always the second (50th) percentile (the median).
* The whiskers are represented as the extend of $1.5$ times the difference between the 25th and the 75th percentile.

```
boxplot(weight ~ sex, main="Boxplot: Body weight data", col=c("purple","steelblue"), data=wdata)
```

```
# adding information 1: boxplot with data mean
boxplot(weight ~ sex, main="Boxplot: Body weight data", col=c("purple","steelblue"), data=wdata)
# mean of female group
abline(h=tapply(wdata$weight, wdata$group, mean)[1], cex=3, lwd=3, col="red")
# mean of male group
abline(h=tapply(wdata$weight, wdata$group, mean)[2], cex=3, lwd=3, col="red", lty="dotted")

# adding information 2: boxplot with data points
boxplot(weight ~ sex, main="Boxplot: Body weight data", col=c("purple","steelblue"), data=wdata)
stripchart(weight ~ sex, vertical = TRUE, data = wdata, method = "jitter", jitter=0.05, add = TRUE, pch = 16, col = adjustcolor("grey40",0.4), cex=1.25)
```
