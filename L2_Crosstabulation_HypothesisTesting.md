---
title: "Cross tabulation, elementary hypothesis testing"
sidebar: toc
category: getting-started
order: 1
---

# Contents

* Conduct &chi;<sup>2</sup> analyses and tests.
* Understand how to use cross tables in practice and be able to interpret the results of different associated statistics.

# Hypothesis testing

<p align="center">
   <img src="https://github.com/kagruber2412/Marketing_Research/blob/master/Assets/random.png">         
</p>

1. Formulate H<sub>0</sub> \& H<sub>1</sub>
2. Select an appropriate test, based on assumptions about the properties of the underlying data
3. Choose the critical value &alpha;
4. Calculate a test statistic T
5. Reject H<sub>0</sub> if p(T) &le; &alpha; or do not reject H<sub>0</sub> if p(T) > &alpha;


## 1. Formulate H<sub>0</sub> \& H<sub>1</sub>

* A **null hypothesis (H<sub>0</sub>)** is a statement of the status quo, one of no difference or no effect. If the null hypothesis is not rejected, no changes will be made.
* An **alternative hypothesis (H<sub>1</sub>)** is one in which some difference or effect is expected. Accepting the alternative hypothesis will lead to changes in opinions or actions (= **research question**).

A null hypothesis may be rejected, but it can never be accepted based on a single test. The null hypothesis is formulated in such a way that its rejection leads to the acceptance of the desired conclusion.

*Example:*

* H<sub>0</sub> = mean<sub>(female)</sub> = mean<sub>(male)</sub>
* H<sub>1</sub> = mean<sub>(female)</sub> &ne; mean<sub>(male)</sub>


## 2. Select the statistical test

Select an appropriate statistical test based on assumptions about...
1. the **measurement level** of the variable being tested (nominal, ordinal, interval/ratio)
2. **independent** samples (two or more group comparisons on different observation units, also called *unpaired*) or 
**related** samples (two or more measurement points on the same observation units, also called *paired*)

<p align="center">
<img src="https://github.com/kagruber2412/Marketing_Research/blob/master/Assets/Summary_Tests.png">
</p>


## 3. Choose the critical value &alpha;

* **Type I error** (**false positive**): Drawing a sample from a population involves the possibility that the observed effect ocurred due to sampling error. (i.e., H<sub>0</sub> is true in the underlying population but based on the sample results H<sub>0</sub> is rejected). A test's probability of making a type I error is denoted by **&alpha;**.
* **Type II error** (**&beta;**): H<sub>1</sub> is true in the underlying population. Based on the sample results  H<sub>0</sub> is not rejected.
* **Test power** (**1 - &beta;**): the probability of correctly rejecting the null hypothesis.

<!--
To minimize the possibility of wrongly rejecting the null hypothesis common values for &alpha; are 0.05 or 0.01.

Statistical tests always involve a trade-off between:

the acceptable level of false positives (in which a non-match is declared to be a match) and
the acceptable level of false negatives (in which an actual match is not detected).
A threshold value can be varied to make the test more restrictive or more sensitive, with the more restrictive tests increasing the risk of rejecting true positives, and the more sensitive tests increasing the risk of accepting false positives.

the p-value of a result, p, is the probability of obtaining a result at least as extreme, given that the null hypothesis were true.
-->

<p align="center">
<img src="https://github.com/kagruber2412/Marketing_Research/blob/master/Assets/significance.png" width="350" height="350">
</p>

<p align="center">
<img src="https://github.com/kagruber2412/Marketing_Research/blob/master/Assets/hypothesis1.png" width="350" height="350">
</p>


## 4 & 5. Accept/Reject

* The test statistic follows a certain distribution (e.g. normal, t, &chi;<sup>2</sup>,...)

<p align="center">
<img src="https://github.com/kagruber2412/Marketing_Research/blob/master/Assets/hypothesis.png" width="700" height="350">
</p>

* The test statistic measures how close the sample is to the null hypothesis

<p align="center">
<img src="https://github.com/kagruber2412/Marketing_Research/blob/master/Assets/hypothesis2.png" width="350" height="350"> <img src="https://github.com/kagruber2412/Marketing_Research/blob/master/Assets/hypothesis3.png" width="350" height="350">
</p>


# Nominal variables \& one sample

## &chi;<sup>2</sup> test

**Usage:**

* To compare a certain sample proportion of a **nominal** variable with an expected population proportion.

### Case 1: Equal proportions

* Tests the null hypothesis stating that the frequency distribution of certain events observed in a sample is consistent with a particular theoretical distribution.

**Example:** *Trump's twitter behavior (cont.)*

4901 words obtained from tweets based on Trump's **Android** phone (during the presidential election campaign in 2016) had been categorized into 10 sentiments using the NRC Word-Emotion Association lexicon.

```
# generate the data
name <- c("anger", "anticipation", "disgust", "fear","joy", "negative", "positive", "sadness","surprise", "trust")
dat <- c(rep(name[1],490), rep(name[2],428), rep(name[3],304),rep(name[4],403), rep(name[5],355), rep(name[6],820),
         rep(name[7],967), rep(name[8],450), rep(name[9],266),rep(name[10],626))
```

**Research question:** Is the sentiment of words equally distributed? or is there any sentiment that is overrepresented?

* H<sub>0</sub>: all sentiments (= categories) are equal (uniform distributed)
* H<sub>1</sub>: at least one sentiment differs (is more/less frequent)

We are testing the deviations of the `observed` values from the `expected` values.

```
# calculate absolute values (frequencies)
observed <- table(dat)
```

Under H<sub>0</sub> you would expect a proportion of 1/10 for all categories -> 1/10 * N = 1/10 * 3197 = 319.7 observations per category.

```
# devide the number of observations by the number of categories (i.e., all categories being equally likely)
expected <- sum(table(dat))/10
```

```
# compare the observed to the expected value
residuum <- observed - expected
cbind(observed, expected, residuum)
```

```
# calculate the test stastistic
sum(residuum^2)/(expected)
```

```
# plot chi-square distribution
x <- rchisq(1000, 9)
hist(x, prob=TRUE, main="Chi^2 distribution with 9 degrees of freedom", xlab="")
curve(dchisq(x, df=9), col="red", lwd=2, add=TRUE )

# the corresponding 95%-quantile 
# (= for a significance level of 5%) we would be here
abline(v=qchisq(1-0.05, 9), col="red", lty="dotted", lwd=2)
# our test statistic is here 549.4091

# calculate area under the chi-square distribution 
# curve (= p-value)
1 - pchisq(549.4091, 9)
```

```
# fast: use built-in function:
chisq.test(table(dat))
```

**Interpretation:**

H<sub>0</sub> (i.e., the 10 sentiments are distributed uniformly) is **rejected** (p < .001). Words with a positve/negative classified sentiment are more frequent!


### Case 2: Test of independence

* Examines the relationship between two independent, nominal variables.
* **independence**: the occurrence of one does not affect the probability of the other (= no additional information about one variable can be extracted from the other). Examples: tossing a coin, measuring peoples height,...

**Example:** *Trump's twitter behaviour (cont.)*

Overall, we have 628 tweets from the iPhone, and 762 tweets from the Android. We can also see a difference involves sharing links or pictures in tweets.

```
dat <- matrix(c(10,543,423,199), ncol=2, byrow=T)
rownames(dat) <- c("Android","iPhone")
colnames(dat) <- c("picture/link","No picture/link")
dat

# make a staked barplot
barplot(dat, col=c("steelblue","grey40"))

# Obviously tweets from the iPhone are more likely to contain either a picture or a link.
```

**Research question:** Is there an association between content (w/o picture or link) of the tweet and the device used (Samsung Galaxy vs. iPhone)?

* H<sub>0</sub>: the device used (rows) is independent of the content (columns).
* H<sub>1</sub>: the device used is not independent of the content.
 

```
# add information (row and column sums)
addmargins(dat)

# to get conditional information devide either by row or by column sums

# condition on column information:
prop.table(dat, 2)*100 

# make a staked barplot again (using conditional information)
barplot(prop.table(dat, 2)*100, col=c("steelblue","grey40"))

# we have no space for a legend, so we force the bars to be side by side
barplot(prop.table(dat, 2)*100, col=c("steelblue","grey40"), beside=TRUE, legend=TRUE)
```

```
chisq.test(dat)
```

**Interpretation:**

H<sub>0</sub> is **rejected** (p < .001). Tweets from the iPhone are significantly more likely to contain either a picture or a link.

<img src="https://github.com/kagruber2412/Marketing_Research/blob/master/Assets/solution.PNG">
