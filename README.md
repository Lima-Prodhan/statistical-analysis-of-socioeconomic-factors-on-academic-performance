# Impact of Socioeconomic Factors on Student Academic Performance

Statistics for Data Science | East West University  

## Project overview

This project explores the relationship between parental education and student academic performance (exam scores) using Python-based statistical analysis. It includes exploratory data analysis (EDA), data visualization, hypothesis testing, confidence interval estimation, bootstrap resampling, regression modeling and statistical robustness checks to examine math, reading and writing scores.
The analysis uses pandas, NumPy, Matplotlib, Seaborn, SciPy and scikit-learn to identify patterns, evaluate statistical significance and investigate factors associated with students’ mathematics performance.

> **Scope note:** The notebook tests one parental-education indicator (`some college`) against all other parental-education categories and uses reading and writing scores as regression predictors. It does not model all socioeconomic factors.

## Dataset

The notebook loads `StudentsPerformance.csv` from `/content/StudentsPerformance.csv` (Google Colab). It is downloaded from the [Kaggle Students Performance in Exams dataset](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams).

The dataset shows **1,000 records and 8 columns**: gender, race/ethnicity, parental level of education, lunch, test preparation course, math score, reading score, and writing score. The notebook's missing-value check reports no null values for the CSV.

## Methods in the notebook

- Missing-value check and `dropna()` preprocessing.
- Standardization of math, reading and writing scores using `StandardScaler`.
- One-hot encoding of categorical variables.
- Descriptive statistics, correlation heatmap, boxplot and mean-score plot.
- Independent-samples t-test on the encoded `parental level of education_some college` indicator.
- A t-based 95% confidence interval for the encoded “some college” group.
- Linear regression using the “some college” indicator, reading score and writing score to predict standardized math score.
- Levene's test, residual plots and a bootstrap confidence interval for the overall standardized math-score mean.

## Results

| Analysis | Result | Interpretation |
|---|---:|---|
| Independent t-test | t = 1.1715; p = 0.2417 | Not statistically significant at α = 0.05 for the notebook's implemented grouping (`some college` vs. all other categories). |
| t-based 95% CI | (-0.0552, 0.1924) | CI for the mean of standardized math scores in the “some college” group, not a difference between all parental-education groups. |
| Levene's test | statistic = 2.6455; p = 0.1042 | Does not reject equal variances at α = 0.05 for the same two groups. |
| Regression coefficient: parental level of education_some college | 0.0862 | Coefficient on standardized variables. |
| Regression coefficient: reading score | 0.5591 | Coefficient on standardized variables. |
| Regression coefficient: writing score | 0.2673 | Coefficient on standardized variables. |
| Bootstrap 95% CI | (-0.06, 0.06) | CI for the overall standardized math-score mean from the run; it is not an estimate of the parental-education effect. |


**95% confidence intervals for all six parental-education categories in original score units:**

| Parental level of education | 95% CI for mean math score |
|---|---:|
| Associate's Degree | (65.89, 69.87) |
| Bachelor's Degree | (66.69, 72.09) |
| High School | (60.10, 64.17) |
| Master's Degree | (65.88, 73.61) |
| Some College | (65.27, 68.99) |
| Some High School | (61.17, 65.83) |


## Limitations

1. The notebook uses a parental-education indicator and does not incorporate the `lunch` field or other socioeconomic measures into its tested model.
2. The t-test does not compare all parental-education groups independently; it compares “some college” against all other categories combined.
3. This is a descriptive and inferential analysis of an observational education dataset. Associations should not be interpreted as causal effects/relationships.
4. The notebook does not report test-set R², RMSE or another predictive-performance score.
