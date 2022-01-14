---
title: "Enabling Computer Adaptive Assessments for Slider-Bar Item Types with the Three-Part Beta Measurement Model"
date: 2022-01-10
publishDate: 
authors: ["Alfonso J. Martinez", "Jonathan Templin", "Catherine E. Mintz", "Tyler Hicks", "Jesse Pace"]
publication_types: ["2"]
abstract: "Psychometric models are widely used to model latent variables based on observed item responses. Online survey tools have created an increased interest in alternatives to discrete rating scales for latent constructs. Among these are continuous rating scales (CRS), which provide more information by allowing for a more precise continuous response as compared to discrete rating scales. A popular example of a CRS item type is the slider-bar, common in online surveys to indicate agreement with an item prompt. The possibility of more information, however, depends on two key factors: (1) the way respondents use the slider-bars to answer questions (e.g., finding a precise numeric response vs. sliding the bar to one extreme) and (2) the measurement model used for analysis. Traditional normal-theory factor models are likely to be inappropriate for slider-scale data because (1) such data are often highly skewed with a higher concentration of responses at the tails of the response range and when (2) response distributions display patterns of mixed skewness (Olsson, 1979). Moreover, normal-theory factor models cannot be used within a computerized adaptive testing (CAT) framework due to a constant latent trait information function.

To address modeling limitations, we introduce an item response model (IRM) for modeling continuous, bounded, and skewed item response data: the three-part Beta (3PB) model. The 3PB model combines a beta distribution, which accommodates bounded and skewed data, and a Bernoulli distribution, which models responses at the boundary points. The continuous responses are modeled via a beta IRM while the discrete responses are modeled via a 2-parameter logistic IRM. We derive the information function of the 3PB model and show that, like IRT models, the 3PB model has a non-constant information function appropriate for CAT, allowing for the possibility of shortening surveys without loss of information.

We analyzed 1,002 responses obtained from the Self-Determination Inventory (SDI; Shogren et al., 2020), a 21-item slider-bar assessment, using Bayesian estimation via Stan. We then incorporated the 3PB model into an adaptive algorithm, where we examined (via simulation) how the latent trait estimates differ if the SDI is administered adaptively. Three values of the latent variable ($θ$) were investigated: $θ∈{−2,0,2}$. The EAP estimated item parameters of the 3PB model were used to determine the item information for each item. For each value of $θ$, we simulated responses from 750 respondents. We examined the mean and standard deviation of the posterior distribution of $θ$ after each successive simulated item response. The adaptive survey provided comparable ability estimates to estimates obtained from the full-length assessment with a shorter number of items."
featured: true
image:
  preview_only: true
publication: "*Multivariate Behavioral Research*"
url_pdf: "https://www.tandfonline.com/doi/full/10.1080/00273171.2021.2011696?src="
doi: "10.1080/00273171.2021.2011696"
---
