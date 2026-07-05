# Project 1 — Weather Temperature Prediction

## Why I Built This
Weather prediction affects daily decisions for millions of people. I wanted to explore whether something as simple as humidity can be used to predict temperature — and build my first regression model on a real large-scale weather dataset with 700K+ records.

## Problem Type
Regression — predicting a continuous numerical value (Temperature in °C)

## Business Questions
- Can humidity alone predict temperature with reasonable accuracy?
- What is the direction of the relationship between humidity and temperature?
- How accurate is a Linear Regression model on large-scale weather data?

## Dataset
| Detail | Value |
|--------|-------|
| Source | humidity.csv |
| Total Records | 697,513 |
| Total Columns | 6 |
| Missing Values | Removed |
| Duplicate Records | Removed |

## Features Used
| Feature | Role |
|---------|------|
| Humidity | Input feature |
| Temperature | Target variable |

## Train-Test Split
| Set | Records |
|-----|---------|
| Training (80%) | 558,010 |
| Testing (20%) | 139,503 |

## Model — Linear Regression

| Metric | Value |
|--------|-------|
| R² Score | 59.73% |
| Mean Absolute Error (MAE) | 2.75°C |
| Root Mean Squared Error (RMSE) | 4.10°C |
| Regression Coefficient | -0.2422 (negative) |

## Key Findings
- The final dataset contains **697,513 records** after removing duplicates — one of the largest datasets in this portfolio
- Average temperature in the dataset: **24.75°C**
- Average humidity: **48.35%**
- Humidity values range from **0% to 100%**
- The regression coefficient is **negative (-0.2422)** — temperature generally **decreases** as humidity increases
- R² of 59.73% means humidity alone explains about 60% of temperature variation — other weather factors account for the rest

## Data Insights
- Dataset contains 6 weather-related features
- Strong enough signal in humidity alone to build a working model
- Negative relationship between humidity and temperature confirmed statistically
- MAE of 2.75°C means predictions are within roughly 3 degrees on average

## Business Insights
- Humidity is a meaningful but not sufficient standalone predictor of temperature
- Adding more weather features (wind speed, pressure, cloud cover) would significantly improve accuracy
- A 60% R² on 700K records shows the linear relationship is real, not noise

## Recommendations
- Add additional weather variables (pressure, wind speed, dew point) to improve R² beyond 60%
- Try polynomial regression to capture non-linear humidity-temperature patterns
- Build a multi-feature weather model as a follow-up project
- Test model performance by season — the relationship may be stronger in summer vs. monsoon months

## Risks
- Single-feature model limits prediction accuracy
- Weather patterns are regional — model trained on one location may not generalise globally
- Extreme weather events (storms, heatwaves) may fall outside the model's learned range

## ML Concepts Applied
- Exploratory Data Analysis (EDA) on 700K+ records
- Data cleaning — missing values and duplicate removal
- Simple Linear Regression
- Model evaluation — MAE, MSE, RMSE, R² Score
- Regression coefficient interpretation

## Tools Used
`Python` · `pandas` · `numpy` · `matplotlib` · `scikit-learn`
