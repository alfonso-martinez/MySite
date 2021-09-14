---
title: Testing the multivariate normal mean vector $\mathbf{\mu}$ when the covariance matrix $\mathbf{\Sigma}$ is known
description: 
---

Let $\mathbf{X} = \mathbf{X}_1, \ldots, \mathbf{X}_n \sim \mathcal{N}_p(\mathbf{\mu}, \mathbf{\Sigma})$ be an independent and identically distributed sample, where $n > p$ and $\mathbf{\Sigma}$ is known. We wish to test the hypothesis:
\begin{align}
H_0: \mathbf{\mu} = \mathbf{\mu}_0 \quad vs. \quad H_1: \mathbf{\mu} \neq \mathbf{\mu}_0.
\end{align}

It can be shown that the test statistic 
\begin{align}
  Q = n(\overline{\mathbf{X}} - \mathbf{\mu}_0)^{\top}(\mathbf{\Sigma})^{-1}(\overline{\mathbf{X}} - \mathbf{\mu}_0),
\end{align}
where $\overline{\mathbf{X}} = \mathbf{1}_n^{\top}\mathbf{X}$ and $\mathbf{1}_n$ is a $n \times 1$ vector of 1's, follows a $\chi^2$ distribution with $p$ degrees of freedom (denoted $\chi^2_p$). 

Here is a function that will compute $Q$ for us; we will reject $H_0$ with significance $\alpha$ if $Q \geq \_\alpha\chi^2_p$, where $\_\alpha\chi^2_p$ is the $100(1-\alpha)$ percentile of the $\chi^2_p$ distribution. 

```{r}
multivariate.location.test <- function(data, sigma, mu0, percentile){
  input.data <- as.matrix(data)
  
  nObs <- nrow(input.data)
  
  ones <- matrix(data = 1, nrow = nObs, ncol = 1)
  
  xbar <- matrix(data = (t(ones)%*%input.data)/nObs, 
                 nrow = ncol(input.data), ncol = 1)
  
  Q <- (t(xbar - mu0)%*%solve(sigma/nObs)%*%(xbar - mu0)) # (X - mu)'(Sigma/n)^-1(X - mu)
  critical.value <- round(qchisq(p = percentile, df = ncol(input.data)), ncol(input.data))
  
  if(Q > critical.value)
    conclusion <- "REJECT NULL"
  else 
    conclusion <- "FAIL TO REJECT NULL"
  
  print(paste0("Q is chi-square distributed with p = ", ncol(input.data), " degrees of freedom"))
  print((paste0("Percentile: ", (percentile*100))))
  print((paste0("Q = ", round(Q, 2), " and the critical value is ", 
                      critical.value)))
  print(paste0("Conclusion: ", conclusion))
}
```
