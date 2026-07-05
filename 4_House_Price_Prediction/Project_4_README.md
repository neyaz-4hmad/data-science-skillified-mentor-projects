# Project 4 — House Price Prediction (Linear Regression)

## Why I Built This
Real estate pricing feels like a mystery to most buyers — why does one house cost twice as much as a similar one nearby? I wanted to find out if machine learning can learn this relationship from data. This project is a clean, end-to-end regression model that goes from raw housing data to price predictions with near-perfect accuracy.

## Problem Type
Regression — predicting a continuous numerical value (House Price)

## Business Questions
- Which features have the strongest influence on house price?
- How accurately can we predict house prices from size, location, age, and bedrooms?
- Does the model generalise well to unseen houses, or does it overfit?

## Dataset
| Detail | Value |
|--------|-------|
| Source | Housing_data.csv |
| Total Records | 500 |
| Total Features | 5 (4 input + 1 target) |
| Missing Values | None |
| Duplicate Records | None |

## Features Used
| Feature | Relationship with Price |
|---------|------------------------|
| Size | Strongest positive correlation |
| Bedrooms | Weak positive relationship |
| Location_Index | Moderate positive relationship |
| Age | Slight negative relationship |
| **Price** | **Target variable** |

## Key Statistics
| Metric | Value |
|--------|-------|
| House Price Range | ~307,000 to ~1,348,000 |
| Average House Price | ~844,406 |

## Train-Test Split
| Set | Records |
|-----|---------|
| Training (80%) | 400 |
| Testing (20%) | 100 |

## Model — Linear Regression

| Metric | Value |
|--------|-------|
| Training R² Score | **0.9980** |
| Testing R² Score | **0.9977** |
| Average Prediction Error (MAE) | 10,733.11 |

## Key Findings
- House **Size** is the dominant feature — the strongest positive predictor of price
- **Location Index** has a moderate positive effect — better locations command higher prices
- **Age** has a slight negative relationship — older houses tend to be slightly cheaper
- **Bedrooms** have a weak positive effect — bedroom count alone doesn't drive price much
- Training and Testing R² are nearly identical (0.998 vs 0.997) — **no overfitting**
- Average prediction error of ~10,733 is low given the price range of 300K–1.3M

## Surprising Finding
Bedrooms had a weaker impact on price than expected. Size and location together almost entirely explain the price — suggesting that buyers in this dataset care more about total space and area than the number of rooms.

## Business Insights
- Size and location are the two biggest pricing levers — developers should focus here
- The model can serve as a **fair market value estimator** for new property listings
- Near-perfect R² (0.9977) means this model is reliable for its feature set
- Age adds only marginal negative drag — well-maintained older properties may still command good prices

## Recommendations
- Use this model as a **base pricing tool** for property valuation
- Collect additional features (floor count, parking, amenities, proximity to schools) to further improve real-world applicability
- Test the model on properties outside the training range to check generalisation
- Retrain periodically as real estate market prices change

## Risks
- Small dataset (500 records) — may not generalise to all markets
- Only 4 features — real-world house prices depend on many more variables
- Linear model may not capture non-linear relationships (e.g. premium jumps in specific locations)
- Model is location-specific — not transferable to different cities without retraining

## ML Concepts Applied
- Exploratory Data Analysis (EDA)
- Correlation matrix and heatmap visualisation
- Feature selection and interpretation
- Train-test split (80/20)
- Linear Regression
- Model evaluation — MAE, MSE, RMSE, R² Score
- Actual vs. Predicted price visualisation

## Tools Used
`Python` · `pandas` · `numpy` · `matplotlib` · `scikit-learn`
