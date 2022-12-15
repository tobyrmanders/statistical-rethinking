# Chapter 7: Ulysses' Compass

- Confounding: non-causal models may do better on prediction; must decide for each task. 
- 2 approaches to avoid under/overfitting:
  - regularizing prior
  - information criteria or cross-validation

## 7.1 The problem with parameters
- R2 is "explained variance"
  - problem: adding parameters improves the value
  - meaning: how much of the variation in the training data does the model retrodict?

## 7.2 Entropy and accuracy
- to estimate out-of-sample deviance need to define a loss function

#### 7.2.1.2 Measuring accuracy
- data generative model maximizes the joint probability of the data
  - this is not necessarily the same as maximizing accuracy
  - `log scoring rule`: logarithm of the joint probability

### 7.2.2 Information and uncertainty
- `information`: the reduction in uncertainty due to a piece of knowledge
- `information entropy`: average log-probability of an event, H(p)


### 7.2.3 From entropy to accuracy
- `divergence`: additional uncertainty induced by using probabilities from one distribution to describe another distribution
- metric called `KL divergence`
- i.e. how far two distributions are apart from each other
- i.e. the average difference in log probability between target (p) and model (q)
- divergence can be used to compare models
- *OVERTHINKING*: divergence is the _additional entropy_ of using q, so difference between H(p) and H(p, q), the cross-entropy
  - directionality matters; mars->earth has larger divergence than earth->mars

### 7.2.4 Estimating divergence
- can use average log-probability from each model as an estimate of KL divergence
- must use the entire distribution of the posterior to calculate log-probability
  - i.e. average probability for each observation over the posterior
  - this is called the `log-pointwise predictive density`
- `deviance` is the lppd * -2 (smaller is better)

### 7.2.5 Scoring the right data
- problem: lppd gets better with more parameters

## 7.3 Regularization
- regularizing prior: a prior that restrains the posterior
- adaptive priors: multilevel models learn regularization strength from the data itself
- ridge regression lambda describes the narrowness of the prior

## 7.4 Predictive accuracy
- 2 strategies:
  - cross-validation
  - information criteria

### 7.4.1 Cross-validation
- LOOCV can be compute intesive
- Pareto-smoothed importance sampling cross-validation (PSIS) uses sample importance to estimate Eout

### 7.4.3 Comparint CV, PSIS, WAIC
- CV and PSIS have have higher variance; WAIC has higher bias

## 7.5 Model Comparison
- To compare models, don't use standard error, but standard error of their differences

### 7.5.1 Information criteria
- IC construct estimate of Eout KL divergence
- AIC is just a function of the number of degrees of freedom
- WAIC (widely applicable IC) works in more cases
  - penalty is the sum of varaince in log probabilities ofr each observation
  - pointwise, so has standard error




