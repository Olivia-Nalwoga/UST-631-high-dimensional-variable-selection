# High-Dimensional Variable Selection in NHANES Health Data

## 1. Research Question

Can a reduced subset of hematologic and demographic variables predict hemoglobin levels nearly as well as a full model that includes all available predictors?

This question matters because high-dimensional datasets often contain redundant or unstable variables. Understanding whether simpler models perform comparably can improve interpretability and reproducibility in statistical analysis.

---

## 2. Hypothesis

- **Null Hypothesis (H₀):**  
  A reduced model using selected predictors performs significantly worse than a full model using all available predictors.

- **Alternative Hypothesis (H₁):**  
  A reduced model using selected predictors achieves comparable predictive performance to the full model.

---

## 3. Data Description

- **Source:**  
  National Health and Nutrition Examination Survey (NHANES), accessed via a public GitHub repository:  
  https://github.com/simonaseno/NHANES

- **Unit of Analysis:**  
  Each observation represents a single NHANES participant.

- **Outcome Variable:**  
  Hemoglobin level (continuous laboratory measurement).

- **Predictor Variables:**  
  - Demographic variables (e.g., age, sex, education, income)  
  - Laboratory variables from the Complete Blood Count (CBC)

- **Data Handling:**  
  - Observations with missing values in the outcome or selected predictors were removed.
  - Numeric predictors were standardized prior to model fitting.

---

## 4. Methods

- A full predictive model was fit using all available predictors.
- A reduced model was fit using variable selection techniques.
- **Test statistic:** Difference in prediction error (e.g., mean squared error) between the full and reduced models.
- **Permutation test:** Used to simulate the null distribution by breaking the association between predictors and the outcome.
- **Bootstrap estimation:** Used to assess uncertainty and stability of selected predictors.
- **Why the CLT does not apply:**
  This analysis involves high-dimensional predictors and variable selection
  procedures that produce statistics with discrete and non-normal sampling
  distributions. Therefore, resampling-based methods are more appropriate than
  CLT-based inference.

---

## 5. Results

### Full Model Performance

A linear regression model using all available predictors achieved strong
predictive performance, with a test-set mean squared error (MSE) of
approximately **0.0049**. An observed-versus-predicted plot showed most points
closely aligned with the identity line, indicating that the full model fits the
data well and produces accurate predictions of hemoglobin levels.

### LASSO Variable Selection

LASSO identified a smaller and more interpretable subset of predictors, the reduced model achieved predictive performance comparable to the full model. 
The permutation test indicates that any observed difference in performance is not statistically significant, highlighting a trade-off between simplicity and interpretability without a clear loss in accuracy.

### Reduced Model Performance

A reduced linear regression model fit using only the LASSO-selected predictorsexhibited substantially worse predictive performance, with a test-set MSE ofapproximately **0.0233**. The observed difference in prediction error between thereduced and full models was **0.0184**, indicating a large loss in predictive
accuracy when using the reduced model.

### Permutation-Based Comparison

The permutation test produced a p-value of 0.143, which exceeds the 0.05 
significance level. Therefore, we fail to reject the null hypothesis that the 
observed difference in predictive performance between the reduced and full models 
could have occurred by chance.

This suggests that the reduced model does not exhibit a statistically significant 
loss in predictive accuracy relative to the full model.

Bootstrap analysis indicates that the full model’s test-set MSE is stable across 
resamples, suggesting that the model’s performance is not driven by sampling variability.


### Bootstrap Uncertainty Estimation

Bootstrap resampling of the training data produced a stable distribution of the
full model’s test-set MSE. The 95% bootstrap confidence interval for the full
model MSE was approximately **[0.00438, 0.00631]**, and the observed MSE fell well
within this interval. This suggests that the full model’s predictive performance
is reliable and not driven by random sampling variation.

---

## 6. Uncertainty Estimation

A total of 2,000 bootstrap resamples were used to assess uncertainty in model performance. The bootstrap distribution of the full model MSE was concentrated and slightly right-skewed, with limited variability. The narrow confidence interval indicates that uncertainty in predictive accuracy is small and primarily due to finite sample size rather than model instability.
Permutation-based reasoning further supported the conclusion that the observed performance gap between models reflects genuine structure in the data rather than chance variation.

---

## 7. Limitations

Potential limitations include:
- NHANES data are observational, limiting causal interpretation.
- Results may be sensitive to the specific predictors included and to the choice of regularization strength.
- NHANES sampling weights were not incorporated.
- Variable selection outcomes may vary under alternative modeling choices.

---

## 8. References

- National Health and Nutrition Examination Survey (NHANES):  
  https://wwwn.cdc.gov/nchs/nhanes/
- NHANES data repository used in this project:  
  https://github.com/simonaseno/NHANES
- Python scientific computing libraries (pandas, numpy, scikit-learn, matplotlib, seaborn)

---

## Conclusion

While LASSO identified a small and interpretable subset of predictors, the full
high-dimensional model provided substantially better predictive accuracy,
highlighting a clear trade-off between simplicity and performance.

---

## Repository Structure

```
UST-631-high-dimensional-variable-selection/
├── .gitignore        # Prevents committing data files
├── README.md         # Project documentation
├── analysis.ipynb    # Main analysis notebook
└── data/
    └── README.md     # Instructions for accessing data
```
