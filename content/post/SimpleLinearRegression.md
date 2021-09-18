---
title: The Simple Linear Regression Model
description: 
---

# Introduction to and Assumptions of the Model
In this post, we consider the simple linear regression model with a single covariate (predictor variable). The model is given as
$$y_i = \beta_0 + \beta_1 x_i + \epsilon_i \quad i = 1, \ldots, n$$
where $(y_i, x_i)$ is the response-covariate pair for the $i$th observation. In general, the linear regression model is capable of handling multiple covariates, however, for simplicity we restrict the present discussion to the case where only one covariate is included in the model. The linear regression model is useful for modeling the relationship between response $y$ and covariate $x$. Some questions that may be answered within the linear regression framework include:
  1. Can we predict $y$ from $x$? If so, how well can we do so and to what extent do these predictions make sense?
  2. Can we establish a (linear) relationship between $y$ and $x$?
  3. If $x$ is related to $y$, how much of the variation does $x$ explain?
For the purposes of this post, we will use the Real Estate Valuation Dataset [(obtained from the UCI Machine Learning Repository)](https://archive.ics.uci.edu/ml/datasets/Real+estate+valuation+data+set) and we will attempt to describe the relationship between the house prices ($y$) and number of convenience stores surrounding the house ($x$).


## Assumptions of the Model

