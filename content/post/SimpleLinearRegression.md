---
title: The Simple Linear Regression Model
description: 
---

# Introduction to and Assumptions of the Model
In this post, we consider the simple linear regression model with a single covariate (predictor variable). The model is given as
$$y_i = \beta_0 + \beta_1 x_i + \epsilon_i \quad i = 1, \ldots, n$$
where $(y_i, x_i)$ is the response-covariate pair for the $i$th observation, and $\epsilon_i$ is the random error. In general, the linear regression model is capable of handling multiple covariates, however, for simplicity we restrict the present discussion to the case where only one covariate is included in the model. The linear regression model is useful for modeling the relationship between response $y$ and covariate $x$. Some questions that may be answered within the linear regression framework include:
  1. Can we predict $y$ from $x$? If so, how well can we do so and to what extent do these predictions make sense?
  2. Can we establish a (linear) relationship between $y$ and $x$?
  3. If $x$ is related to $y$, how much of the variation does $x$ explain?
For the purposes of this post, we will use the Real Estate Valuation Dataset [(obtained from the UCI Machine Learning Repository)](https://archive.ics.uci.edu/ml/datasets/Real+estate+valuation+data+set) and we will attempt to describe the relationship between the house prices ($y$) and number of convenience stores surrounding the house ($x$). More information about the dataset can be found at the page linked above.

## Assumptions of the Model
Before conducting a regression analysis, it is important to understand the assumptions of the linear regression model. A few standard assumptions include:
  1. The covariates $x_i$ are assumed to be known. In other words, they have been measured and collected as part of some data collection process. An implicit assumption is that the covariates were measured without error. In other words, the covariate was measured precisely and exactly. 
  2. The expected value of the random error $\epsilon_i$ is assumed to be 0; i.e., $E(\epsilon_i) = 0 \quad i = 1, \ldots, n$, where $E(\cdot)$ is the expectation operator. Note that this assumption implies that $$E(y_i) = \beta_0 + \beta_1 x_i, \quad i = 1, \ldots, n.$$
  3. The variance of the random errors is assumed to be constant across all observations. In symbols, $$V(\epsilon_i) = \sigma^2$$ for all $i = 1, \ldots, n.$ Alternatively, this assumption implies that all observations have the same level of precision. 
  4. The final assumption is that any two random error terms coming from different observations (say $\epsilon_i$ and $\epsilon_{i^\prime}$ are independent. This assumption implies that the covariance between $\epsilon_i$ and $\epsilon_{i^\prime}$ is zero, i.e., $Cov(\epsilon_i, \epsilon_{i^\prime}) = 0$ for $i \neq {i^\prime}.$

Let $\mu_i = \beta_0 + \beta_1 x_i$. Under the assumptions described above, the simple linear regression model implies that the response variable $y_i$ is drawn from a normal distribution characterized by mean $\mu_i$ and variance $\sigma^2$. In symbols, $$y_i \sim N(\mu_i, \sigma^2) \quad i = 1, \ldots, n$$ or equivalently, 
$$y_i \sim N(\beta_0 + \beta1 x_i, \sigma^2) \quad i = 1, \ldots, n$$
