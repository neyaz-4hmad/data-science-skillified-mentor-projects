# Project 2 — Credit Card Fraud Detection

## Why I Built This
Financial fraud costs banks and customers billions every year. What makes this problem interesting — and hard — is that fraud transactions are extremely rare compared to normal ones. I wanted to build a model on a real, heavily imbalanced dataset and understand what precision, recall, and F1 score actually mean in a life-or-death business context like fraud detection.

## Problem Type
Binary Classification — Normal Transaction (0) vs Fraud Transaction (1)

## Business Questions
- Can a machine learning model detect fraudulent transactions with high accuracy?
- How do we balance catching fraud (Recall) vs. avoiding false alarms (Precision)?
- What are the risks of a model that misses fraud cases?

## Dataset
| Detail | Value |
|--------|-------|
| Source | creditcard.csv (Kaggle — Credit Card Fraud Detection) |
| Total Records | 283,726 |
| Total Columns | 31 |
| Missing Values | Removed |
| Duplicate Records | Removed |
| Class Imbalance | Highly imbalanced — very few fraud transactions |

## Features Used
| Feature | Description |
|---------|-------------|
| Time | Seconds elapsed since first transaction |
| V1 – V28 | PCA-transformed anonymised features |
| Amount | Transaction amount |
| Class | Target — 0 = Normal, 1 = Fraud |

## Data Download
Dataset downloaded directly from Kaggle using **KaggleHub API** with `getpass()` for secure token authentication — no hardcoded credentials.

## Train-Test Split
| Set | Records |
|-----|---------|
| Training (80%) | 226,980 |
| Testing (20%) | 56,746 |

## Model — Logistic Regression

| Metric | Value |
|--------|-------|
| Accuracy Score | **99.92%** |
| Precision Score | 86.11% |
| Recall Score | 65.26% |
| F1 Score | 74.25% |

## Confusion Matrix Results
| Outcome | Count |
|---------|-------|
| Normal transactions correctly classified | ✅ Almost all |
| Normal transactions wrongly flagged as fraud | ❌ Only 10 |
| Fraud transactions correctly detected | ✅ Majority |
| Fraud transactions missed | ❌ 33 |

## Key Findings
- Model achieved **99.92% accuracy** — excellent overall classification
- **Precision of 86.11%** — when the model flags fraud, it's right 86% of the time
- **Recall of 65.26%** — the model catches about 65% of actual fraud cases, missing ~35%
- Only **10 normal transactions** were incorrectly flagged as fraud (false positives)
- **33 fraud transactions were missed** — these represent real financial risk
- Dataset is **highly imbalanced** — fraud cases are a tiny fraction of total transactions

## Surprising Finding
99.92% accuracy sounds perfect — but in fraud detection, the 33 missed fraud cases matter far more than the accuracy number. This is why Recall and F1 Score are the real metrics that count, not just accuracy. This project taught me to look beyond the headline number.

## Business Insights
- The model is suitable for basic fraud detection but misses 35% of fraud cases — too high for production use
- False positives (flagging normal transactions as fraud) are low — good for customer experience
- Class imbalance is the core challenge — the model has seen very few fraud examples to learn from
- Real-time deployment would need a much higher Recall rate to be financially safe

## Recommendations
- Apply **data balancing techniques** (SMOTE, undersampling) to improve Recall on fraud cases
- Compare Logistic Regression with **Random Forest, XGBoost, LightGBM** for better fraud detection
- Add **feature scaling** to improve Logistic Regression convergence
- Deploy with a **confidence threshold** — flag transactions above a certain fraud probability for manual review
- **Retrain the model regularly** as fraud patterns evolve over time

## Risks
- 33 missed fraud transactions could lead to direct financial losses
- Recall of 65.26% is too low for a production fraud system
- Fraud patterns change over time — a static model loses effectiveness
- Class imbalance means the model is biased toward predicting normal transactions

## ML Concepts Applied
- Kaggle API integration with secure token authentication
- Binary classification on heavily imbalanced data
- Logistic Regression
- Model evaluation — Accuracy, Precision, Recall, F1 Score
- Confusion matrix analysis and interpretation

## Tools Used
`Python` · `pandas` · `numpy` · `matplotlib` · `scikit-learn` · `kagglehub`
