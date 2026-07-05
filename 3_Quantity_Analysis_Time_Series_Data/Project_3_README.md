# Project 3 — Predictive Sales Forecasting (ARIMA)

## Why I Built This
Businesses that can't predict demand end up with too much stock or too little. I wanted to go beyond basic analysis and build an actual time series forecasting model — something that looks forward, not just backward. ARIMA was my first step into proper forecasting, and I applied it to 2 years of real sales data.

## Problem Type
Time Series Forecasting — predicting future sales quantity from historical patterns

## Business Questions
- What will daily sales look like over the next 30 days?
- Are there seasonal patterns in sales that a business should plan around?
- How accurately does ARIMA capture historical sales trends?

## Dataset
| Detail | Value |
|--------|-------|
| Source | Raw Data_Predictive Analysis.xlsx |
| Total Records | 40,563 |
| Total Features | 9 |
| Time Period | 01-Jan-2019 to 31-Dec-2020 |
| Daily Time Series | 731 days |
| Missing Values | Found in productListViews and productListClicks — filled |
| Duplicate Records | None found |

## Features Used
| Feature | Description |
|---------|-------------|
| OrderDate | Date of order — used as time index |
| ParentProductIdNew | Product identifier |
| ParentProductNew | Product name |
| ProductCategoryNew | Product category |
| ArtistNameNew | Artist/brand associated with product |
| Selling Price | Price per unit |
| productListViews | Number of times product was viewed |
| productListClicks | Number of times product was clicked |
| total_qty_sales | **Target variable** — units sold per day |

## Data Preprocessing
- Missing values filled in productListViews and productListClicks
- Duplicate records removed
- OrderDate converted to datetime and set as time series index
- Daily frequency assigned to create a proper time series
- Data aggregated to daily total sales for modelling

## Model — ARIMA (AutoRegressive Integrated Moving Average)

| Metric | Evaluated |
|--------|-----------|
| MAE | ✅ |
| MSE | ✅ |
| RMSE | ✅ |

## Key Findings
- Dataset covers a **two-year period (2019–2020)** — 731 daily data points
- Average sales quantity per record: **~14 units**
- Daily sales **fluctuate throughout** the period, indicating changing customer demand
- Monthly sales show **clear seasonal variations** across different months
- ARIMA successfully learned historical patterns and generated **30-day forecasts**
- Predicted sales remain **stable** after the initial forecast period

## Data Insights
- No duplicate records found in the dataset
- Missing values existed only in view and click columns — filled appropriately
- Seasonal demand variations suggest promotional or event-driven spikes
- The 731-day time series provides enough history for ARIMA to identify meaningful patterns

## Business Insights
- ARIMA forecasts can be directly used for **inventory planning** over the next 30 days
- Seasonal patterns identified in the data allow for **promotional calendar planning**
- Stable post-forecast predictions suggest demand is relatively predictable in the short term
- View and click data (productListViews, productListClicks) may hold additional signal for demand forecasting

## Recommendations
- **Update the model monthly** with new sales data to maintain forecast accuracy
- Compare ARIMA with **SARIMA, Facebook Prophet, and LSTM** for improved seasonal handling
- Use forecasts to **optimise purchasing decisions** — order more before predicted high-demand periods
- Build an **automated forecasting dashboard** that refreshes predictions weekly
- Forecast at **product and category level** for more granular inventory management

## Risks
- ARIMA relies on historical patterns — sudden market changes (pandemics, new competitors) will break forecasts
- Forecast accuracy decreases for long-term predictions beyond 30 days
- Missing business context (promotions, price changes) may reduce model quality
- ARIMA does not automatically adapt to structural breaks in the data

## ML / Statistical Concepts Applied
- Time series creation and frequency assignment
- ARIMA model training and parameter tuning
- 30-day future forecasting
- Model evaluation — MAE, MSE, RMSE
- Seasonal pattern analysis
- Visualisation of historical vs. forecasted sales

## Tools Used
`Python` · `pandas` · `numpy` · `matplotlib` · `statsmodels`
