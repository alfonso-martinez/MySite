---
title: Exploring the Psychometric Properties of the Satisfaction with Life Scale with Item Response Theory
subtitle: 
summary:
authors:
- admin
tags: []
categories: []
date: "2019-02-05T00:00:00Z"
lastMod: "2019-09-05T00:00:00Z"
featured: true
draft: false

image:
  placement: 2
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: "center"
  preview_only: false
 
projects: []
---
Item response theory (IRT) is a powerful multivariate modeling technique for the analysis of binary and ordinal response data. Under the item response framework, the observed variables are assumed to be a function of an underlying latent variable $\theta \in \mathbb{R}$ (which is unobserved), and the goal of IRT is to infer the characteristics of $\theta$ based on the observed responses.

In this blog post an application of item response models appropriate for ordinal resposnse data, also known as polytomous item response models, are discussed. Several models, including the graded response model (GRM), the nominal response model (NRM), and the partial credit model (PCM) are briefly introduced and compared via an empirical application to the Satisfaction of Life Scale (SWLS; Diener et al. 1985). First, an overview of the SWLS is presented, along with a historical overview of its development, functional purpose, characteristics, and recent work that has utilized the scale. Then, an overview of item response theory, with an emphasis on polytomous item response models. Topics discussed include model specification, evaluating model fit, and interpreting the results obtained. This blog post is designed to function as a guide for those who are interested in fitting polytomous item response models to their data. 

# The Satisfaction with Life Scale

The Satisfaction with Life Scale (SWLS) was originally developed by Diener,
Emmons, Larsen, and Griffin (1985) as a brief assessment of an individual’s general sense
of satisfaction with his/her life. According to Google Scholar, it has been cited over 25,000
times, making it one of the more popular assessments of cognitive or psychological
subjective well-being. The scale was originally developed by generating a pool of
approximately 50 items related to life satisfaction and well-being. Using factor analytic
techniques, Diener et al. identified 10 items with high loadings on a single common factor
later interpreted as global evaluations of a person’s life. After eliminating items with
redundancies, the scale was further reduced from 10 items to five items. The final scale
consists of 5 items that are responded to with a 7-point Likert scale (1 = strongly disagree
to 7 = strongly agree). Studies has shown that the SWLS has high internal consistency, as
indicated by Coefficient $\alpha$. Reported $\alpha$ values in the literature range between .79 to .89. 

Previous research has found that the SWLS is 


# Item Response Theory
The ordinal nature of the SWLS makes it an ideal candidate to be analyzed with item response theory. Item response theory is a 


# Data

Data for this project comes from a project undertaken in 2019. In the original project, two versions of
the SWLS were created and participants were randomly assigned to receive one version.
One version of the SWLS was the original scale and in the second version of the SWLS, the
response labels for categories 2 through 6 were left blank. The research question in my
undergraduate thesis was to compare the two versions and determine if the two versions of
the scale produced significantly different results. For this project, however, I ignored this
difference and combined responses from all participants. Thus, the SWLS dataset I
analyzed in this project came from n = 656 participants (77% female). Internal consistency
($\alpha$ = .879) was relatively high and inline with reported values in the literature.

![item 1 CCC](https://github.com/alfonso-martinez/MySite/raw/master/content/post/MyFolder/item1CCC.png) ![item 2 CCC](https://github.com/alfonso-martinez/MySite/raw/master/content/post/MyFolder/item2CCC.png)
![item 3 CCC](https://github.com/alfonso-martinez/MySite/raw/master/content/post/MyFolder/item3CCC.png) ![item 4 CCC](https://github.com/alfonso-martinez/MySite/raw/master/content/post/MyFolder/item4CCC.png)
![Category Characteristic Curve (CCC) for Item 5 of the SWLS.](https://github.com/alfonso-martinez/MySite/raw/master/content/post/MyFolder/item5CCC.png)


# Model Specification: Which Model Should I Use to Fit the Data?

The first step in analyzing the SWLS data was to specify an item response model
that could appropriately handle the ordinal nature of the SWLS. Because multiple
response scores are possible for a given item, dichotomous item response models are not
appropriate for this type of data. This includes the three parameter logistic model and its
simpler forms (i.e. 2-PL and 1-PL/Rasch model).

Clearly then, a polytomous item response model is needed. There are several
polytomous item response models that I considered. These included the nominal response
model (NRM), graded response model (GRM), partial credit model (PCM), and rating scale model (RSM). The models mainly differ in the assumptions they make and the constraints they place on certain parameters. For instance, the ...

I conducted a “mini literature review” where I read and learned the basics of each model and types of
data that they can successfully model. Based on this review, I selected the graded response
model (GRM) because it can handle ordinal categories (the nominal response model
cannot) and, in my opinion, offered the most flexibility (the rating scale model requires
that the difficulty parameter of the items be the same distance apart).
The rating scale model, proposed by Fumiko Samejima, is a polytomous item
response model used to model data with polytomous (ordinal) response categories. The
rating scale model has the mathematical form
  $$\lambda + \lambda = 2\lambda$$,
where $i$ denotes individual $i$, $j$ denotes item $j$, $\theta$ represents the latent trait, $x_{ij}$ represents
individual $i$’s score on item $j$, $b_{x_{ij}}$ is the item-specific location parameter and represents the
point along the $\theta$ scale at which the probability of an endorsement equals 0.5, $a_j$ is an item
specific discrimination parameter, and $D$ is a scaling factor sometimes set to $D = 1.7$.
More information about the graded response model can be found in Samejima (1997).

# Methods

The R package `ltm` was used to fit the graded response model to the SWLS data.
The ltm package is a latent trait modeling package with many functions; it can be used to
fit dichotomous and polytomous response models, provides model fit indices such as
goodness-of-fit statistics, supports test equating, and more. Estimation of the graded
response model is done via marginal maximum likelihood, and two variations of the GRM
are supported in ltm. One variation is a constrained GRM and the second variation is an
unconstrained GRM. The former fits a GRM but imposes a constraint on the
discrimination parameter such that the discrimination estimates are the same across all
items. The unconstrained GRM does not make this restriction and allows each item to
have its own discrimination estimate.
I fit both the constrained and unconstrained GRMs and found that, via a likelihood
ratio test, that the unconstrained model had significantly better fit than the constrained
model. Thus, all subsequent analyses and figures were done using the unconstrained model.

# Results and Discussion

Below are the estimated difficulty and discrimination estimates for each item of the
SWLS from the unconstrained graded response model. Each row beginning with SWLS1
represents item j (j = 1, . . . , 5) with each column beginning with Extrmt1 presents the
point on the $\tha scale where an individual with estimated ability, ˆ, has 50% probability of
endorsing that particular category.
For instance, consider the value 0.340 corresponding to SWLS3 and Extrmt5. This
point is the estimated  value at which a respondent has a 50% probability of endorsing a
category less than or equal to 5, for item 3. Similar interpretations can be made about the
remaining cells in the matrix. In addition, the right most column, Dscrmn, provides the
discrimination values for each item. Notice that, because I specified the unconstrained
model, these values are all item-specific and vary from item to item.

To provide a visual representation of the data, Figure 1 provides category
characteristic curves for items 1 through 5 of the SWLS, Figure 2 provides item
information curves and the test information curve, and Figure 3 provides operation
characteristic curves for items 1 through 5 of the SWLS, respectively.
This goal of this project was to fit polytomous response models to the Satisfaction
with Life Scale. Several models were considered, however the graded response model
appeared to be the best model based on the type of data it can model, its flexibility
relative to other models, and simplistic interpretation of results.
In addition, two versions of the graded response model were considered. One version
imposes a restriction on the discrimation parameters such that they are equal across items,
that is aj = a for all j = 1, . . . , 5. The unconstrained model does not impose this
restriction and allows each item to have its own difficulty parameter. The Likelihood ratio
test (LRT) indicated that the unconstrained model had significantly better fit than the
constrained model.

Examining Figure 2, we can see that item 3 of the SWLS provided the most
information. This result makes intuitive sense given that item 3 is very direct in its
phrasing (“I am satisfied with my life”). Overall, the test provides satisfactory test
information, especially between  values of -2 and 2, as shown in Figure 2b. This is a very
interesting result given that the scale is only 5 items and was not developed using item
response theory techniques. Overall, these results provide compelling evidence for the
utility and practicality of the SWLS, especially for researchers and practitioners interested
in using the scale as a proxy for individuals’ well-being.

![Item Information Curves](https://github.com/alfonso-martinez/MySite/raw/master/content/post/MyFolder/ItemInfoCurves.png)
![Test Information Curve](https://github.com/alfonso-martinez/MySite/raw/master/content/post/MyFolder/TestInfoCurve.png)

