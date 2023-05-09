# Chapter 14: Adventures in Covariance

- *Varying effects* strategy - pooling for any batch of parameters with an exchangeable index, i.e. values have no true ordering
- Pooling across parameter types allows learning about covariance

## 14.1 Varying slopes by construction

- **RETHINKING** - Practically, mv Gaussian is one of few multivariate distributions that are easy to work with. Epistemologically, if all we can say is mean, variance, and covariance, mv Gaussian is the max ent distribution.
- **OVERTHINKING** - Covariance is "the difference between the average product and the product of the averages"

### 14.1.3
- *Misspecified* - the model is not the same as the DGP
- **RETHINKING** - "And  always remember that Bayesian inference does not depend upon data-generating assumptions, such  as the likelihood, being true. Non-Bayesian approaches may depend upon sampling distributions for  their inferences, but this is not the case for a Bayesian model. In a Bayesian model, a likelihood is a  prior for the data, and inference about parameters can be surprisingly insensitive to its details."
- Correlation matrix R (rho) also needs a prior
  - In R: LKJcorr()
  - Regularizing prior for correlation matrices

- *Covariance vs. Correlation* - covariance and correlation both measure degree to which variables move together, but covariance depends on the scale of the variables. correlation is standardized to [-1, 1]. S = D * R * D, where D is the covariance matrix, D is the diagonal matrix of standard deviations
- Pooling happens within intercepts, within slopes, and between intercepts and slopes, thanks to the multivariate gaussian. Together, the variances and correlation define a MV Gaussian prior for the varying effects, an adaptively regularizing prior for both intercepts and slopes. 


## 14.2 Advanced Varying Slopes
- Non-centered parameterization improves MCMC sampling
- Less variation across groups results in more shrinkage (i.e. stronger regularization)

## 14.3 Instruments and causal designs
- What can you do when you can't exclude non-causal paths in your regress?

### 14.3.1 Instrumental variables
- *Instrumental variable* - a variable that acts like a natural experiment on the exposure variable. Satisfies three constraints:
  - independent of backdoor confounder
  - not independent of exposure variable
  - has effect on the target only through the exposure variable (the *exclusion restriction*)
- How do you use an instrument?
  - Cannot just add it as a predictor. Conditioning on the exposure variable opens a backdoor from your instrument, causing it to become a *bias amplifier*

