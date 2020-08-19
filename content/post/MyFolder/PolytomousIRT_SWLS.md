---
title: An Application of Polytomous Item Response Models to the Satisfaction with Life Scale
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
hhj


![png](./"myCFA.png")

In this blog post, we will be going over an application of polytomous item response models (specifically, the Graded Response Model) to the Satisfaction with Life Scale. The structure of this report mirrors that of the presentation I gave on May 4, 2020 to the class, but contains a bit more information. I begin by introducing the Satisfaction with Life Scale and providing a brief historical overview of its development, functional purpose, characteristics, and recent work that has utilized the scale. I then briefly describe my data, where it came from, and how it was used in this project. I then transition to matters related to item response theory, particularly model specification and how I arrived at the model I ended up using to fit my data. Lastly, I describe and interpret the results I obtained and provide graphics of the results. The end of the report contains the R syntax I used to obtain all analyses and results.

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
indicated by Coefficient . Reported  values in the literature range between .79 to .89.

# My SWLS Data


Data for this project comes from my undergraduate thesis completed as an
undergrad at California State University, Fresno. In the original project, two versions of
the SWLS were created and participants were randomly assigned to receive one version.
One version of the SWLS was the original scale and in the second version of the SWLS, the
response labels for categories 2 through 6 were left blank. The research question in my
undergraduate thesis was to compare the two versions and determine if the two versions of
the scale produced significantly different results. For this project, however, I ignored this
difference and combined responses from all participants. Thus, the SWLS dataset I
analyzed in this project came from n = 656 participants (77% female). Internal consistency
( = .879) was relatively high and on-par with reported values in the literature.


# Model Specification: Which Model Should I Use to Fit the Data?

The first step in analyzing the SWLS data was to specify an item response model
that could appropriately handle the ordinal nature of the SWLS. Because multiple
response scores are possible for a given item, dichotomous item response models are not
appropriate for this type of data. This includes the three parameter logistic model and its
simpler forms (i.e. 2-PL and 1-PL/Rasch model).
Clearly then, a polytomous item response model is needed. There are several
polytomous item response models that I considered. These included the nominal response
model, graded response model, partial credit model, and rating scale model. I conducted a
“mini literature review” where I read and learned the basics of each model and types of
data that they can successfully model. Based on this review, I selected the graded response
model (GRM) because it can handle ordinal categories (the nominal response model
cannot) and, in my opinion, offered the most flexibility (the rating scale model requires
that the difficulty parameter of the items be the same distance apart).
The rating scale model, proposed by Fumiko Samejima, is a polytomous item
response model used to model data with polytomous (ordinal) response categories. The
rating scale model has the mathematical form
  $$lambda + \ambda = 2\lambda$$,
where $i$ denotes individual $i$, $j$ denotes item $j$, $\theta$ represents the latent trait, $x_{ij}$ represents
individual $i$’s score on item $j$, $b_{x_{ij}}$ is the item-specific location parameter and represents the
point along the $\theta$ scale at which the probability of an endorsement equals 0.5, $a_j$ is an item
specific discrimination parameter, and $D$ is a scaling factor sometimes set to $D = 1.7$.
More information about the graded response model can be found in Samejima (1997).

# Methods


The R package ltm was used to fit the graded response model to the SWLS data.
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
point on the  scale where an individual with estimated ability, ˆ, has 50% probability of
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


Here is the greek letter lambda ($\lambda$). Here is beta $\beta$. Selecting the preceding developments, we are now ready to state the posterior distribution for all the unknowns:
\begin{align*}
	p(\Xi, \kappa, \Phi, \tau, \Lambda, \Psi \mid \mathbf{x}) &\propto p(\mathbf{x} \mid \Xi, \kappa, \Phi, \tau, \Lambda, \Psi) p(\Xi, \kappa, \Phi, \tau, \Lambda, \Psi) \\
	&= p(\mathbf{x} \mid \Xi, \tau, \Lambda, \Psi) p(\Xi \mid \kappa, \Phi) p(\kappa) p(\Phi) p(\tau) p(\Lambda) p(\Psi) \\
	&= \prod_{i = 1}^{n} \prod_{j = 1}^{J} \prod_{m = 1}^{M} p(x_{ij} \mid \xi_i, \tau_j, \lambda_j, \psi_{ij}) p(\xi_i \mid \kappa, \Phi) p(\kappa_m) p(\Phi) p(\tau_j) p(\lambda_{jm}) p(\psi_{jj}), 
	\intertext{where}
	x_{ij} \mid \xi_i, \tau_j, \lambda_j, \psi_{ij} &\sim N(\tau_j + \xi_i \lambda_j^\prime, \psi_{jj}) \mbox{ for } i = 1, \ldots, n, \ j, \ldots, J, \\
	\xi_i \mid \kappa, \Phi &\sim N(\kappa, \Phi) \mbox{ for } i = 1, \ldots, n, \\
	\kappa_m &\sim N(\mu_{\kappa}, \sigma_{\kappa}^2) \mbox{ for } m = 1, \ldots, M, \\
	\Phi &\sim \mbox{Inv-Wishart}(\Phi_0, d), \\
	\tau_j &\sim N(\mu_{\tau}, \sigma_{\tau}^2) \mbox{ for } j = 1, \ldots, J, \\
	\lambda_{jm} &\sim N(\mu_{\lambda}, \sigma_{\lambda}^2) \mbox{ for } j = 1, \ldots, J, \ m = 1, \ldots, M, 
	\intertext{and}
	\psi_{jj} &\sim \mbox{Inv-Gamma}(\frac{\nu_{\psi}}{2}, \frac{\nu_{\psi} \psi_0}{2}) \mbox{ for } j = 1, \ldots, J.
\end{align*}

Data come from my undergraduate honors thesis where I recorded the responses to the Satisfaction with Life Scale. The SWLS is a scale designed to measured global cognitive evaluations of ones view of their life. There were a total of 656 respondents and the SWLS consists of the following 5 items:
	\begin{enumerate}
		\item In most ways my life is close to my ideal. 
		\item The conditions of my life are excellent.
		\item I am satisfied with my life.
		\item So far I have gotten the important things I want in life.
		\item If I could live my life over, I would change almost nothing.
	\end{enumerate}
Estimation was carried out on R using MCMC Metropolis Hastings Algorithm.

 I’m creating a macro and need some text for testing purposes.

* I’m trying to learn more about some feature of Microsoft Word and don’t want to practice on a real document.

Microsoft Word 97, 98, 2000, and 2001 include an undocumented feature that generates all of the sample text I need. Maybe you’ll find it helpful too. To use it, type the following line into a Word document and press the ENTER key:

=Rand(1,1)

Word will insert the following text into your document:

The quick brown fox jumps over the lazy dog.

(As you probably know, this sentence includes every letter in the alphabet and is sometimes used for typing practice.)

Need more than one sentence? You can specify how many sentences you need by changing the last number in the Rand statement. For example, if you needed five sentences, you could type this–

=Rand(1,5)

–which would produce this:

The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog.

Need more than one paragraph? You can specify how many paragraphs you need by changing the first number in the Rand statement. For example, if you needed two paragraphs (with five sentences in each one), you could type this–

=Rand(2,5)

–which would produce this:

The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog.

The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog. The quick brown fox jumps over the lazy dog.

In other words, the first number specifies the number of paragraphs you want to insert; the second number specifies the number of sentences you want to include in those paragraphs.