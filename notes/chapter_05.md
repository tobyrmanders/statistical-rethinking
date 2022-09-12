# Chapter 5

## 5.1

### 5.1.5

#### 5.1.5.1 Predictor Residual Plots
- predictor residual = prediction error when all other variables are used to model a predictor of interest

#### 5.1.5.2 Posterior Predictive Plots
- two uses: posterior check against real data, and error analysis

#### 5.1.5.3 Counterfactual Plots
- show the causaul implications of the model for any possible values of predictor variables
- simplest use: change one variable at a time and see the result
- counterfactual plots change the dag to eliminate causal influence of other variables on the predictor

## 5.2 Masked Relationship
- for neocortex example, multiple dags c/w data, because all dags have the *same conditional independencies*
- known as *markov equivalence* set
- must use domain intuition to eliminate unreasonable dags

## 5.3 Categorical Variables
- discreteness, unordered 

### 5.3.1 Binary
- two options, indicator variable or index variable

### 5.3.2 Many Categories
- index variable is simpler and priors are easier unless you have priors about contrasts
- RETHINKING: if you want to show difference between two parameters, must compute the *contrast*

## 5.4 Summary
- Multiple regression asks the value of each predictor once you account for all the others
- Does not tell causal information, which requires additional assumptions





