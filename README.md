# Tourism Recovery Forecasting Analysis (New Zealand)

## Project Overview
This project analyzes **New Zealand's tourism recovery after COVID-19** using MBIE's Tourism Electronic Card Transaction (TECT) dataset.
It builds a **data-driven recovery index, momentum indicators, and time-series forecasts** to understand how different regions are recovering and to project short-term tourism spend trends.

The analysis goes beyond visualization by:
1. Benchmarking recovery agaisnt pre-Covid levels (2019=100),
2. Measuring regional momentum using YoY growth,
3. Forecasting future spend using **SARIMAX** seasonality,
4. Producing **policy- and business-relevant insights** for planning, marketing, and capacity management

**Problem Statement**
After COVID-19, policymakers and tourism stakeholders need to answer:
1. Which regions have **fully recovered** vs. are still lagging?
2. Which regions are **accelerating** vs. **cooling down**?
3. What does the **next 12 months** of tourism spend look like?
4. How reliable are short-term forecasts for planning budgets, infrastructure, and marketing?

**Objective:**
Build an analytical and forecasting framework to:
1. Track tourism recovery relative to 2019,
2. Compare regional performance and momentum,
3. Forecast short-term tourism spend with uncertainty bands,
4. Support evidence-based tourism and economic planning.

**Data Source & Pipeline**
**Data Source**
1. MBIE - Tourism Electronic Card Transactions (TECT) dataset
2. Granularity: Monthly tourism spend by region
3. Period: Pre-COVID → 2025
4. File used: Region-series.xlsx

**Data Pipeline**
MBIE TECT Excel
   ↓
Python (pandas, numpy)
   ↓
Cleaning & Standardisation
   - Standardise column names
   - Build proper monthly date index
   - Coerce spend to numeric
   - Handle missing values
   ↓
Feature Engineering
   - National & regional time series
   - Recovery Index (2019 = 100)
   - YoY % change (momentum)
   ↓
EDA & Visualisation
   - Trends, seasonality
   - Heatmaps of regional momentum
   ↓
Forecasting (SARIMAX)
   - Grid search over seasonal orders
   - Train/test split (last 12 months holdout)
   - RMSE & MAPE evaluation
   ↓
Final Forecasts
   - Refit on full history
   - 12-month outlook + 95% confidence intervals
   - Export forecasts to CSV

**Methodology / Analysis**
1. **Exploratory Data Analysis (EDA)
   - Visualized national and regional trends
   - Checked seasonality and structural breaks (COVID impact)
   - Inspected missing values and continuity
   - Compared pre- and post- COVID levels

2. **Recovery Index**
   - Normalised each series using:
     2019 average = 100

  - Interpreted values:
    100 = above pre-COVID levels
    <100 = below pre-COVID levels

    Built:
    National recovery index
    Regional recovery indices

3. **Momentum Analysis (YoY Growth)**
   - Computed **Year-on-Year % change**
     Built:
     Regional heatmap of last 12 months YoY growth
     6-month average YoY momentum ranking

     Used to identify:
     Accelerating regions
     Cooling or stagnating regions

4. **Forecasting Model**
   - Model: SARIMAX (Seasonal ARIMA with exogenous structure)
   - Seasonality: 12 months
   - Approach:
     Small grid search over (p,d,q) and (P,D,Q,12)
     Selected best model by AIC
     Holdout validation: last 12 months

   - Metrics:
    RMSE ~ 147
    MAPE ~ 3.8%

5. **Final Forecast**
   - Refit model on full history
   - Generated:
     12-month forecast
     95% confidence intervals

  **Business Questions Answered**
  1. Has NZ tourism **recovered to pre-COVID levels?
  2. Which regions are **leading vs lagging** the recovery?
  3. Which regions show **positive vs. negative momentum**?
  4. How stable is the recovery across regions?
  5. What is the **expected tourism spend trajectory** over the next 12 months?
  6. How much **uncertainty** exists around the forecast?

**KPIs Produced / Affected**
- **Recovery Index (2019=100)** by region and nationally
- **YoY Growth (%)** by region
- **6-month average momentum** by region
- **Forecasted monthly spend** (next 12 months)
- **Forecast accuracy metrics:**
  1. RMSE
  2. MAPE
- **Upper * lower confidence bounds** for planning risk

**Key Insights**
- National tourism spend has **recovered above 2019 levels**, indicating structural recovery.
- Some regions (e.g. Canterbury, Taranaki, Tasman) show **strong recovery levels**, but **momentum differs**.
- Several regions show **cooling YoY momentum**, despite being above pre-COVID levels - suggesting **normalisation rather than growth**.
- Auckland's spend shows:
  1. Clear COVID shock and recovery pattern
  2. Stable recent performance
  3. Moderate growth in the 12-month outlook with wide uncertainty bands
- Lagged values and seasonality dominate the dynamics, validating the SARIMAX approach

**Recommendations**
1. Policy & Planning
   - Focus investment and marketing on regions with **strong recovery but weakening momentum**
   - Support regions with **low recovery index and negative momentum**

2. **Tourism Strategy**
   - Use recovery index + momentum together (level ≠ growth)
   - Avoid assuming "recovered" means "growing"

3. **Forecast Usage**
   - Use **confidence bands** for risk-aware budgeting and capacity planning
   - Refit models quarterly as new data arrives

4. **Next Steps**
   - Extend to **multivariate models** (e.g. include macro indicators)
   - Build **scenario forecasts** (optimistic / baseline / downside)
  

**Key Outputs**
1. National Recovery Index Chart (2019 = 100)
2. Regional YoY momentum heatmap (last 12 months)
3. Regional recovery & momentum ranking table
4. Holdout forecast vs actual plot (Auckland)
5. 12-month forecast with confidence intervals
6. CSV export:
   - auckland_forecast_next12m.csv
  
**Tech Stack**
1. Python
2. pandas, numpy
3. matplotlib, seaborn
4. statsmodels (SARIMAX)
5. scikit-learn (metrics)
6. jupyter / colab

**How to Run**
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn

Open the notebook and run all cells:
Tourist Spend NZ.ipynb

Make sure Region-series.xlsx is in the same directory.

**Data Source**
- MBIE - Tourism Electronic Card Transactions (TECT)
  https://www.mbie.govt.nz


**Author- Imaya Kehelkaduwa (Analytics and Data Engineering Portfolio)**








