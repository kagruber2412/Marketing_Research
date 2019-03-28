---
title: "Cross tabulation, elementary hypothesis testing"
sidebar: toc
category: getting-started
order: 1
---

# Contents

* Conduct $\chi^2$ analyses and tests.
* Understand how to use cross tables in practice and be able to interpret the results of different associated statistics.

# Hypothesis testing

* Formulate $H_0$ \& $H_1$
* Choose the level of significance $\alpha$ (e.g. $\alpha = 0.05$)
* Select an appropriate test, based on assumptions about the properties of the underlying data (and grouping variables)
* Calculate a test statistic $T$
* Reject $H_0$ if $p(T) \leq \alpha$ or do not reject $H_0$ if $p(T) > \alpha$


## Formulation of the hypothesis

* A **null hypothesis ($H_0$)** is a statement of the status quo, one of no difference or no effect. If the null hypothesis is not rejected, no changes will be made.
* An **alternative hypothesis ($H_1$)** is one in which some difference or effect is expected. Accepting the alternative hypothesis will lead to changes in opinions or actions (= **research question**).

A null hypothesis may be rejected, but it can never be accepted based on a single test. The null hypothesis is formulated in such a way that its rejection leads to the acceptance of the desired conclusion.

*Example:*

* $H_0 = \bar{x}_{female} = \bar{x}_{male}$
* $H_1 = \bar{x}_{female} \neq \bar{x}_{male}$


## Choose significance level 

* **Type I error** (significance level, $\alpha$): occurs when the sample results lead to the rejection of the null hypothesis when it is in fact true (common values: $0.05$ or $0.01$).
* **Type II error** ($\beta$): occurs when, based on the sample results, the null hypothesis is not rejected when it is in fact false.
* **Test power** ($1 - \beta$): the probability of rejecting the null hypothesis when it is false.


## Test selection

* Select the appropriate test based on the measurement level of the variable being tested and test specific assumptions:
- measurement level of the variables (nominal, ordinal, interval/ratio)
- **independent** samples (two or more group comparisons on different observation units, also called *unpaired*) or 
**related** samples (two or more measurement points on the same observation units, also called *paired*)

* The test statistic measures how close the sample is to the null hypothesis and follows a certain distribution (e.g. normal, t, $\chi^2$,...)


## Accept/Reject


# Overview of univariate tests


# Nominal variables \& one sample

## $chi^2$ test

**Usage:**

* to compare a certain sample proportion of a **nominal** variable with an expected population proportion

**Example**: *Do the number of individuals or objects that fall in each category differ from the number you would expect?*
* **Case 1:** equal proportions
* **Case 2:** $\chi^2$ test of independence





