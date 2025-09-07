# Tourism-Recovery-Forecasting-Analysis

## BUSINESS GOAL
To understand New Zealand's tourism recovery after Covid-19 and forecast regional trends.

## DATA
**Source**: MBIE's Tourism Electronic Card Transactions (TECT) dataset
**Granularity**: Monthly spend by region
**Period**: Pre-COVID to 2025
**Transformations**:
- Normalised 2019 average = **100** (Recovery Index)
- Computed **Year-on-Year % change** for momentum tracking
- Built both **national series** and **regional panels**

## Methodology
**Exploratory Data Analysis (EDA)**
- Trend and seasonality visualisation
- Missing value checks and interpolation

**Recovery Index**
- Benchmarking agaisnt 2019 to measure "return to normal"

**Momentum Analysis**
- YoY % change by region to show accelerating vs cooling regions
- Heatmaps to highlight hotspots of growth/decline

**Forecasting Model**
- **SARIMAX** with 12-month seasonality
- Small grid search for orders minimising AIC
- Train/test split: last 12 months held out for validation

**Validation Metrics**
- RMSE (Root Mean Squared Error)
- MAPE (Mean Absolute Percentage Error)

**Forecast Output**
- Refit on all available data
- 12-month forecasts with 95% confidence bands
- Exported forecasts as CSV

## Key Outputs
- Recovery index trends for each region
- YoY momentum heatmap
- 12-month regional forecasts
- National-level forecast benchmark

## References
- MBIE TECT dataset: https://www.mbie.govt.nz/?utm_source=chatgpt.com
- Statsmodels SARIMAX Documentation
- Pmdarima Auto-ARIMA
