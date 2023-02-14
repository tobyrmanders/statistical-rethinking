# Chapter 11: God Spiked the Integers

GLMs difficult to interpret because parameters not directly meaningful on prediction scale.

2 types of count models in this chapter:
- *BINOMIAL REGRESSION* : total for both categories known
- *POISSON REGRESSION* : count with unknown maximum
  poisson is special case of the binomial

## 11.1 Binomial Regression
Binomial distribution has maxent when outcome is binary and EV is stationary. 
2 types of binomial regression:
- *LOGISTIC REGRESSION* : data organized in single trial cases
- *AGGREGATED BINOMIAL REGRESSION* : individual trials aggregated together
Both use logit link.

REFRESH: Logit link. 
  logit function maps p to real value (-inf, +inf)
  logistic is inverse-logit

Binomial regression not guaranteed to produce MV normal posterior.

### 11.1.1 Logistic Regression: Prosocial Chimpanzees
When sampling from the model, can convert to outcome scale. 
"Flat" priors can represent counterintuitive extremes in a GLM. 
To compare parameters to each other, compute *CONTRASTS*. 
Experiment and hypothesis can inform complexity of the model, i.e. no L/R representation. 

### 11.1.2 Relative Risk and Absolute Deer
Relative effects represent proportional change in the odds of an outcome.
Proportional odds calculated by exponentiating a LR coefficient.

### 11.1.3 Aggregated Binomial
PSIS/WAIC very different for two models even though the posterior is the same.
Multiplication for n choose k term causes difference.

### 11.1.4 Aggregated Binomial: Grad School Admissions
Simpson's paradox: patterns that appear in groups disappoear when groups are aggregated.
- Changing the question to ask about avg gender difference *within a department* makes a big difference in inference. 
  - Department choice is a confound. It is an indirect path. Conditioning on department closes the path. 
    - Called *mediation* analysis
    - May unintentionally condition on a collider

## 11.2 Poisson Regression
- Results because mean ~ variance when p is very small
- Poisson dist parameterized by one param, lambda
- uses the log link

### 11.2.1 Oceanic tool complexity
- Model counts of unique tool types
- Poisson has very long tail, meaning very high mean if parameterized poorly
- Parameter values near boundary produce less overfitting
  - Overfitting risk depends both upon the model details and the sample composition
- Should use free intercept parameter of zero for this problem

### 11.2.2 Negative binomial (gamma-Poisson) models
- Negative binomial dist is combination of different poisson distributions

### 11.2.3 Example: Exposure and the Offset
- Can restructure the log link to incorporate exposure, tau, e.g. the amount of time

## 11.3 Multinomial and categorical models
- Two approaches: explicit vs. poisson likelihoods

### 11.3.1 Predictors matched to outcomes
### 11.3.2 Predictors matched to observations
### 11.3.3 Multinomial as a Poisson
