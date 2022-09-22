# Chapter 6
- *Berkson's paradox aka selection distortion effect* : selection induces negative correlation
  - inside multiple regression, called *collider bias*


## 6.1 Multicollinearity
- All variables will appear not to be associated with target.


### 6.1.1 Leg Example
- Sum of two values is what is correlated with the mean

### 6.1.2 Milk Example
- Lactose and fat give same information about calories, but with opposite correlation direction
- *It is not the correlations, but the conditional associations, that cause the issue.*
- *NON_IDENTIFIABILITY* : the larger family of problems fitting models
  - When it is impossible to estimate parameters due to data or model
- Compare posterior with the prior to check for non-identifiability

## 6.2 Post-Treatment Bias
- *omitted variable bias* vs *included variable bias*
- *post_treatment bia* is example of included variable bias
  - Means including outcomes upstream in the model

### 6.2.1-2 Fungus Examples
- Post-treatment variable masks the treatment
- *d-separation* = directional separation, i.e. conditional independencies
  - post-treatment variable can also create false positive
- *RETHINKING* : model selection via information criteria does not resolve bias discussed, because prediction and causal inference are different tasks

## 6.3 Collider Bias
- variable with multiple arrows pointing to it in a DAG is a collider
  - colliders create statistical but not necessarily causal associations

### 6.3.1 Marriage Example

### 6.3.2 Haunted DAG
- Unmeasured variables can make measured ones colliders
- *Simpson's paradox* : addition of another predictor can reverse the direction of association of another predictor and the target

## 6.4 Confronting Confounding
- Manipulation removes the confounding.
- Conditioning on the confounder also removes the path. "shutting the backdoor"
- 4 types of confounds:
  - fork, pipe, collider, descendant
- 4 steps to decide which variables to include in your model
  1. list routes from x to y
  2. classify routes as open or closed
  3. classify routes as backdoor
  4. close backdoors

