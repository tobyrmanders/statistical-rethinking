# Chapter 12: Monsters and Mixtures

- *Over-dispersion* - count data with unmeasured sources of variation
- *Zero-inflation* - mix of binary event with ordinary Poisson/binomial
- *Ordered categorical* - categorical outcomes with fixed ordering

## 12.1 Over-dispersed counts

- When counts are more variable than a pure process. 
- *Dispersion* the variance of a variable
- When variance exceeds expected value after conditioning on all predictor variables, implies there is an omitted variable
- *Continuous mixture* model is attached to distribution of observations rather than observations
- GLMMs easier to use than continuous mixtures because they are more flexible

### 12.1.1 Beta-binomial

- Model that learns the distribution of success probabilities as a beta dist. 
  - Two parameters, p and theta
    - When theta == 2, flat; >2 peaked
    - can ensure theta >= 2 by adding 2 to an exponential dist in the model 
- Beta Binomial model is not confounded by the admissions problem, because
  - each combination of department and gender has its own intercept

### 12.1.2 Negative-binomial or gamma-poisson
- Assumes each observation has its own rate
- Estimates shape of gamma dist to describe the rates across cases
- Predictors change the shape of the distribution, not the expected value of each obs
- Equivalent to the beta binomial model's beta dist of success rates above
- In poisson dist, variance == mean
- Adds parameter phi, must be positive, controls the variance
- Gamma poisson overfits less due to variance in the mean rate
- Don't use WAIC/PSIS


## 12.2 Zero-inflated outcomes
- Mixture models appropriate when there are different causes for the same observation
- In effect, mixture models use more than one likelihood for the same outcome variable

### 12.2.1 Example: Zero-inflated Poisson
- DGP now has binomial process of whether a count is observed
- Example: monks drink instead of work on some days
- Two linear models combined to produce a poisson dist with two params, p and lambda

## 12.3 Ordered categorical outcomes (*ORDERED LOGISTIC MODELS*)
- Differences between values not necessarily equal
- *CUMULATIVE LINK* - cumulative probability of a value is the probability of that value or any smaller value 

### 12.3.3 Adding predictor variables
- Define log-cumulative-odds of each k as sum of its intercept and a linear model
- Subtracting the linear model makes it so that a positive coefficient means higher outcome value

## 12.4 Ordered categorical predictors
- Each step in ordered predictor comes with incremental effect on the outcome
- Want to infer the incremental effects
- *Dirichlet distribution* -- multivariate extension of the beta distribution
- *Simplex constraint* - vector that sums to one
