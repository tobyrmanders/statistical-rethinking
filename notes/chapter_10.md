# Chapter 10: Big Entropy and the Generalized Linear Model

Entropy: there are more ways for things to be messy than ordered.

Entropy provides guiding principles for building a model:
- Dist with the biggest entropy is the least informative.
- Nature produces high entropy distribution. 
- It works.

**GLM**: A framework for building linear models that replaces a parameter of the likelihood function with a linear model. Does not need to be Gaussian. 

**RETHINKING**: Bayesian posterior maximizes entropy (smallest cross-entropy) among all distributions consistent with constraints and data. 


## 10.1 Maximum entropy
- Average log-probability is the measure of uncertainty, information entropy H(p)


**Maximum Entropy Distribution** - the dstribution that can happen in the greatest number of ways, aka the most plausible distirbution.

### 10.1.1 Gaussian
- As spread out as possible for a fixed variance. 

### 10.1.2 Binomial
- Largest entropy, given constraint of expected value
- If there are only two unordered outcomes and the rate is assumed constant, binomial spreads probability out as evenly as possible


## 10.2 Generalized Linear Models
- Introducing the link function

**RETHINKING** *histomancy* is the art of divining a likelihood function from a histogram. This is difficult because you want to know about the residuals, not the aggregate data. 


### 10.2.1 Meet the family
Exponential family of distributions are all maximum entropy for some set of constraints.

- Normal
    outcome distribution associated with linear regression
    identity link
- Binomial
    outcome distribution associated with logistic regression
    logit link/logistic link
- Exponential distribution -- non-negative
    distance and duration, displacement in time or space
    survival and event history
- Gamma distribution -- non-negative
    distance and duration
    peak above zero
    combination of two exponential events
    maximum entropy for dists with same mean and avg logarithm
    survival and even history
- Poisson distribution -- counts
    special case of binomial
    when p is very small and n is very large, converges
    events in an interval of time
    log link


**RETHINKING** in Bayesian statistics, likelihoods are priors for the data, conditioned on paramters


### 10.2.2 Link functions
No regression coefficient produces a constant change on the outcome. 

- LOGIT LINK
    logistic function or inverse-logit
    compress to range(0,1), probability
- LOG LINK
    exponential scaling of the outcome with the predictor variable

### 10.2.3 Omitted variable bias
### 10.2.4 Absolute and relative differences
### 10.2.5 GMLs and Information Criteria



