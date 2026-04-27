# High-Dimensional Variable Selection in NHANES Health Data

## 1. Research Question

Can a reduced subset of health-related variables predict hemoglobin levels almost as well as a full, high-dimensional set of predictors?

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
  In accordance with course guidelines, data files are **not committed** to this repository.  
  Any filtering, cleaning, or transformation steps are documented in the analysis notebook.

---

## 4. Methods

- A full predictive model is fit using all available predictors.
- A reduced model is fit using variable selection techniques.
- **Test statistic:** Difference in predictive performance between the full and reduced models.
- **Permutation test:** Used to simulate the null distribution by breaking the association between predictors and the outcome.
- **Bootstrap estimation:** Used to assess uncertainty and stability of selected predictors.
- The Central Limit Theorem does not apply directly to variable selection stability metrics, motivating the use of resampling methods.

---

## 5. Results

*(To be completed after analysis)*

This section will include:
- Summary statistics and key visualizations
- Observed test statistic and permutation-based p-value
- Bootstrap confidence intervals for relevant metrics

---

## 6. Uncertainty Estimation

*(To be completed after analysis)*

This section will discuss:
- Number of permutation and bootstrap resamples used
- Shapes of the resampling distributions
- Interpretation of interval estimates and variability in selected predictors

---

## 7. Limitations

Potential limitations include:
- Missing data in some laboratory or demographic variables
- Assumptions inherent in the modeling approach
- Sensitivity of variable selection results to resampling variability

---

## 8. References

- National Health and Nutrition Examination Survey (NHANES):  
  https://wwwn.cdc.gov/nchs/nhanes/
- NHANES data repository used in this project:  
  https://github.com/simonaseno/NHANES
- Python scientific computing libraries (e.g., pandas, numpy, scikit-learn)

---

## Repository Structure

UST-631-high-dimensional-variable-selection/
├── .gitignore        # Prevents committing data files
├── README.md         # Project documentation
├── analysis.ipynb    # Main analysis notebook
└── data/
    └── README.md     # Instructions for accessing data
