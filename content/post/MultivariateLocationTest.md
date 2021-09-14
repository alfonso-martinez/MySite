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
where $\overline{\mathbf{X}} = \mathbf{1}^{\top}\mathbf{X}$ and $\mathbf{1}$ is a $m \times 1$ vector of 1's, follows a $\chi^2$ distribution with $p$ degrees of freedom (denoted $\chi^2_p$). 
