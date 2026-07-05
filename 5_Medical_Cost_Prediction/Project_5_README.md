# Project 5 — Medical Insurance Cost Prediction (Linear Regression)

## Why I Built This
Medical insurance costs are a major financial concern for most people — but few understand what actually drives them. I picked this dataset because it has a mix of numeric and categorical features, which gave me a chance to apply Label Encoding and explore a real-world prediction problem. The result surprised me — smoking status dominated everything else.

## Problem Type
Regression — predicting a continuous numerical value (Medical Insurance Charges in $)

## Business Questions
- Which customer characteristics most influence medical insurance charges?
- How accurately can we predict insurance cost from age, BMI, smoking status, and region?
- How much more do smokers pay compared to non-smokers?

## Dataset
| Detail | Value |
|--------|-------|
| Source | insurance.csv |
| Total Records | 1,337 |
| Total Columns | 7 (6 input + 1 target) |
| Missing Values | None |
| Duplicate Records | 1 (identified and removed) |

## Features Used
| Feature | Type | Encoding |
|---------|------|----------|
| age | Numeric | None |
| sex | Categorical | Label Encoded |
| bmi | Numeric | None |
| children | Numeric | None |
| smoker | Categorical | Label Encoded — **strongest predictor** |
| region | Categorical | Label Encoded |
| **charges** | Numeric | **Target variable** |

## Key Statistics
| Metric | Value |
|--------|-------|
| Average Insurance Charge | ~$13,270 |
| Minimum Charge | ~$1,122 |
| Maximum Charge | ~$63,770 |
| Charge Range | 56× spread between lowest and highest |

## Train-Test Split
| Set | Records |
|-----|---------|
| Training (80%) | 1,069 |
| Testing (20%) | 268 |

## Model — Linear Regression

| Metric | Value |
|--------|-------|
| Training R² Score | 0.7297 |
| Testing R² Score | **0.8068** |
| Average Prediction Error (MAE) | $4,182.35 |
| Maximum Prediction Error | $24,052.35 |

## Key Findings
- **Smoker status is the single strongest predictor** of insurance charges — by a large margin
- Smokers consistently appear in the high-charge bracket regardless of age or BMI
- **Age** has a moderate positive relationship — older customers pay more on average
- **BMI** has a weak positive relationship — weaker than expected
- **Most customers are non-smokers** in this dataset
- The **Southeast region** has the highest customer count
- Charges range from ~$1,122 to ~$63,770 — a **56× spread**, showing extreme variance between low and high risk customers

## Surprising Finding
BMI's relationship with charges was much weaker than I expected. Most people assume weight is the dominant health cost driver — but in this dataset, **smoking alone** creates a cost gap that overshadows all other features combined. Even a young, low-BMI smoker pays dramatically more than an older non-smoker.

## Business Insights
- Insurance companies should heavily weight **smoking status** in pricing models — it's the dominant cost driver
- **Age-based pricing is justified** — moderate positive correlation confirmed
- BMI's relatively weak influence suggests lifestyle factors beyond weight matter more
- Regional variation exists but is not a primary cost driver

## Recommendations
- Offer **significant premium discounts to non-smokers** to attract lower-risk customers
- Build **smoking cessation incentive programmes** — reducing smoker count directly reduces high-cost claims
- Segment customers by smoker/non-smoker first, then apply age and BMI adjustments
- Collect additional features (exercise habits, pre-existing conditions, diet) to push R² above 0.85
- Try **Random Forest or Gradient Boosting** to capture non-linear relationships BMI may have with charges

## Risks
- Linear Regression may miss non-linear interactions (e.g. obese + smoker combined effect)
- Maximum prediction error of $24,052 is significant — some individual cases are poorly predicted
- Dataset is US-based — relationships may differ in Indian or other healthcare markets
- Testing R² (0.8068) is higher than Training R² (0.7297) — suggests the test set may be slightly easier; monitor on new data

## ML Concepts Applied
- Exploratory Data Analysis (EDA)
- Label Encoding for categorical features (sex, smoker, region)
- Correlation analysis — identifying dominant predictors
- Train-test split (80/20)
- Linear Regression
- Model evaluation — MAE, MSE, RMSE, R² Score, MAPE
- Actual vs. Predicted charges visualisation

## Tools Used
`Python` · `pandas` · `numpy` · `matplotlib` · `scikit-learn`
