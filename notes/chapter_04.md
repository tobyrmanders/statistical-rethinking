# Chapter 4

## 4.1

### 4.1.1

- Normal distributions emerge from "any process that adds together random values from the same distribution."
- Concept: the most likely sum of this addition will be the one where all the values cancel each other out. 

### 4.1.2
- Multiplication can also produce a normal because the multiplication of small numbers is approximately the same as addition, e.g. 1.1^2 ~ 1.1x2. 
- Applies to "small deviates."

### 4.1.3
- Multiplication of large  deviates can also produce normals on the log scale, since adding logs is equivalent to multiplying the original numbers.

### 4.1.4
Justifications for using normal distributions are:
= Ontological 
  - The world is made up of Gaussians because there are many processes with added random fluctuation. Gaussians fail to identify microprocesses, but reliably model the outcome. 
- Epistemological
  - Gaussians represent a state of ignorance. In effect, a confession that we can only summarize the mean and variance, and nothing else. 
  - Assuming a measure has finite variance, the Gaussian shape is realizable in the largest number of ways. It is the least informative assumption to make. 
  - Premised on information theory and maximum entropy. 
- RETHINKING: Many natural processes have heavier tails than a Gaussian. 

#### Terminology
- Discrete probability distributions are called *probability mass functions*. 
- Continuous probability distributions are called *probability density functions*. 
- *Probability density* is the rate of change of the cumulative probability. 
- Areas under the probability density are *probability masses*. 

## 4.2

- *data* = observations
- *parameters* = unobservable variables
- Each variable is defined either in terms of other variable or in terms of a probability distribution. 
- Combination of all variables and their distributions defines *joint generative model*

### 4.2.1 

- In conventional model notation, first line describes likelihood function; others describe parameter
- ~ indicates stochasticity -- i.e. variable maps onto a distribution

## 4.3
- Goal of linear regression is to rank posterior plausibilities of each combination of parameters, mu and sigma
- Estimate is entire distribution, not a single point.
- Posterior is distribution of distributions.

### 4.3.2
- Warning: Choosing distribution based on how the data look is data snooping. Gaussian is a fine selection without justification d/t epistemological justification earlier in the chapter. 
- RETHINKING: IID -- indepedent and identically distributed means each sample is independent and comes from the same distribution. Rarely true, but only describes the small world probability.  
  - Related: *exchangeable* values are those which can be reordered. de Finetti's theorem states exchangeable values can be approximated by mixtures of i.i.d. distributions.
  - MCMC exploits the fact that non-i.i.d. samples may alter sequence, but often do not alter the overall distribution. 
- Check priors but plotting them and performing a prior predictive simulation. 
- Non-gaussian prior is okay. 
- Priors are less important the more data you have. Bayes allows maximal use of available data given sensible priors with data impoverished scenarios.
- OVERTHINKING: Posterior distribution definition now includes product in the numerator because of multiple measurements in observations. 
  - Bayes' theorem also has to account for multiple priors. They are multiplied in the numberator and the denominator.

### 4.3.3
- Grid approximation. Quadratic approximation will be more practical in real world and subsequent chapters.

### 4.3.4
- In order to sample combinations of multiple parameters, need to first sample rows in proportion to the combination plausibility, then pull out the parameters from the row.
- Summarize *marginal posterior densities* by looking at each parameter (other parameter(s)) marginalized out. 
- OVERTHINKING: Posterior is not always gaussian in shape. If gaussian prior and gaussian likelihood -- you'll always have a gaussian posterior. However, non-Gaussian standard deviation can lead to abuse of quadratic approximation. Standard deviation often has a long right tail due to positive constraint.

### 4.3.5
- Quadratic approximation climbs the posterior to find MAP, then estimates quadratic curvature at MAP to produce whole posterior distribution.
- "Because it is prime."
- The prior for mu strongly affects the posterior for sigma.

### 4.3.6
- To sample from the quadratic approximation posterior, use the *variance-covariance matrix*. Can be factored into two elements:
  - vector of variances for the parameters
  - correlation matrix between parameters
- correlation matrix should have 1 in the diagonal. other numbers indicate strength of relationship between parameters.
- Sampling posterior is now sampling vector of values from multivariate gaussian

## 4.4
- RETHINKING: *regression* = use of predictor variables to model outcome variables
 
### 4.4.1
- Posterior distribution ranks the plausibility of combinations of parameter values

#### 4.4.1.1
- Add index to mathematical notation to indicate variable depends on the row of the data
  - mu no longer a parameter to be estimated, but depends on other params. 
  - mu deterministic

#### 4.4.1.2
- Some analyses are such that no amount of data makes the prior irrelevant
- RETHINKING: There is no single correct prior. 
  - Priors should encode states of information BEFORE seeing data. 
  - Judge your priors against general knowledge, not the sample.

### 4.4.3
- Once you've fit the model, it can only report posterior distribution.
- Plotting posteriors is critical to interpretation.
- RETHINKING: Posterior probabilities  of parameter values describe the relative compatibility of different states of the world with the data, according to the model.

#### 4.4.3.1
- Lack of covariance between parameters results from centering

#### 4.4.3.4
- Procedure for getting CI for every predictor value:
  - Take quadratic approximation, sample from posterior, compute posterior for every case in the data, summarize posterior for each predictor value
- Pseudo-empirical approach is more straightforward than the analytical approach
- RETHINKING: Interpret the regression line as saying "Conditional on the assumption that height and  weight are related by a straight line, then this is the most plausible line, and these are its plausible bounds."

#### 4.4.3.4
- For any unique weight value, you sample from a Gaussian distribution with the correct mean µ for that weight, using the correct  value of σ sampled from the same posterior distribution. If you do this for every sample  from the posterior, for every weight value of interest, you end up with a collection of simulated heights that embody the uncertainty in the posterior as well as the uncertainty in the  Gaussian distribution of heights.
- RETHINKING: posterior predictive simulation blends together uncertainty about the parameters and uncertainty in sampling.

## 4.5
- Two methods for building curves from linear regression: polynomial regression, b-splines

### 4.5.1
- Polynomial:
  - Standardization even more important than linear models
- RETHINKING: *linear* = target variable is a linear function of any single parameter

### 4.5.2
- *spline* = a smooth function build out of smaller fucntions. "B" stands for basis/component.
- The short explanation of B-splines is that  they divide the full range of some predictor variable, like year, into parts. Then they assign  a parameter to each part. These parameters are gradually turned on and off in a way that  makes their sum into a fancy, wiggly curve.
- Polynomial degree determines how basis functions combine to produce the spline
- Exponential distribution can be thought of as containing no more information than an average deviation

### 4.5.3
- A class of models called generalized additive models (GAMs) focuses on predicting an outcome using smooth functions of predictor variables




