# Chapter 13: Models with Memory

- Want to learn about clusters while learning about the population of clusters.
- Distribution across population becomes prior for each element.

- Benefits of multilevel models :
  - better handles repeat sampling
  - better handles imbalanced sampling
    - automatically estimates uncertainty per cluster
  - better handles variation
  - helps avoid arbitrary transformations like averaging 

- Downsides:
  - can be difficult to understand

- synonyms: hierarchical, mixed effects

## 13.1 Multilevel Tadpoles
- example: tadpole survival in different tanks
- *varying interepts* model: simplest kind of varying effects model
  - prior over intercept that is common to all clusters
- prior for avg tank and the stdev of tanks are *hyperparameters*
  - their priors are *hyperpriors*

- OVERTHINKING: quadratic approximation no longer works
  - quap hill climbs with static approximations of each parameter

- watanabe-akaike information criterion (WAIC): 
  - avg log-likelihood function over the posterior
  - # of effective parameters

- multilevel model has fewer effective params than the fixed model despite additional population params

- *shrinkage*: cluster estimates are shrunk toward the center of the data
- *pooling*: each tank provides info that can be used for all other tanks

- OVERTHINKING: estimating population variance can require more informative hyperpriors for small cluster numbers
  - long tails on the exponential variance estimates can interplay with floor and ceiling effects to make impossible values seem plausible -- can be fixed with half normal

## 13.2 Varying effects and underfitting/overfitting trade-off
- complete pooling underfits (variance low, bias high)
- no pooling underfits (variance high, bias low)
- varying effect model edge is greatest when clusters have small data

### 13.2.5
- partially pooled model is better on avg in the long run
- regularization is adaptive: small ponds get heavier dose

## 13.3 Multiple cluster types
- cross-classification = data structure that includes multiple levels non-subsetting
- global mean param bar alpha is used instead of cluster-specific means because they are combined into the same linear model
- presenting both models (with and without block) is better than selecting a model
  - to select a model, would want to test the conditional independencies

## 13.4 Divergent transitions and non-centered priors
- something about energy flow and particles
- decrease learning rate

## 13.5 Multilevel posterior predictions
- tools for inspecting multilevel models
  - model checking
  - counterfactual predictions
  - information criteria
- posterior predictions can be calculated for the average actor (cluster) or marginal of actor (clusters)
  - both useful for different interpretations
- in binomial models, floor and ceiling effects make all parameters interact

## 13.5.3 Post-stratification
- post-stratification: reweight each slice of the model by outside data
- when combined with multilevel models: *MRP: multilevel regression and post-stratification*
- does not work when the outcome of interest causes the selection bias


## 13.5 Multilevel posterior predictions
