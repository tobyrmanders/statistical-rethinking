# Chapter 8: Conditional Manatees
- Manatee injuries and RAF bomber scars are both misleading due to conditioning. 
- The model is a crude device that allows the target to be conditional of predictors
- In **interaction** or **moderation**, the importance of a predictor is conditional of the data. 
- Simplest interaction is a linear interaction, where parameters are modeled as linearly related. 
- Multilevel models model vary the predictor importance, but also estimate the distribution of the varied predictor performance.

## 8.1 Building an Interaction
- DAGs do not display interactions; they only show that there is a function, e.g. f(R, C)
- Do not split the data for your categorical variable:
  - Shared parameters have to be learned separately
  - You cannot directly evaluate probability statements about the splitting variable
  - You can't use PSIS/WAIC if the models don't use the same data
  - The model cannot "borrow" information ala multilevel adaptive regularization

### 8.1.1 Making a rugged model
- Rescaling variables makes prior selection easier
  - Preserve 0 as meaningful if it's desired
- *RETHINKING*: The example in the text didn't "require" the prior workshopping d/t sufficient data and a simple model.

### 8.1.2 Indicator variables bad
- Indicator variable will add uncertainty for one of your categories
- *Posterior contrast*: Sample the difference between two parameters if you want to show difference.

### 8.1.3 Interactions work
- Reminder: WAIC shows predictive performance, not causal validity

## 8.2 Symmetry of Interactions
- Buridan's ass: an ass will starve if it cannot decide between two equidistant food sources
- Interaction models likely have equally valid (to the model) interpretations
- The nonobvious interpretation may yield an interesting insight, e.g. continent only matters for low ruggedness

## 8.3 Continuous Interactions
- Interactions are difficult to interpret because the relationships between parameters depend upon other parameters
- Multiple bivariate plots, holding one variable constant, is a solution

### 8.3.2 Model definitino
- Give a linear function to the slope for one variable that depends upon another variable to introduce a continuous interaction
- This results in an extra term, V1 * V2 with a new interaction parameter B12
- *RETHINKING*: The interaction parameter is actually symmetric w.r.t. the two variables at play. 

### 8.3.3 Plotting posteriors
- Triptych: fix one parameter and plot the other bivariates

