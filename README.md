# Econometric Analysis & Forecasting of Remittance Inflows in Nepal (1993–2024)

This repository contains an end-to-end macroeconomic data analytics and time-series forecasting project evaluating remittance inflow trends, their structural relationship with economic growth (GDP), and out-of-sample forecasting through 2028.

---

## 📌 Project Overview

- **Time Horizon:** 1993 – 2024 (Historical) | 2025 – 2028 (Out-of-Sample Forecast)
- **Primary Domain:** Macroeconomics, Time Series Analysis, Machine Learning
- **Core Indicators Evaluated:**
  - Remittance Inflows (USD / Log-transformed)
  - Gross Domestic Product (GDP / Log-transformed)
  - Remittance Share as % of GDP
  - Gross Fixed Capital Formation (GFCF)
  - Exchange Rate (NPR/USD)
  - Inflation Rate
  - Trade Openness
  - Labor Force Participation

---

## 🛠 Methodology & Analytical Pipeline

1. **Data Preprocessing & Cleaning:**
   - Filtered dataset to exclude 2025 entry anomalies (evaluating stable 1993–2024 window).
   - Computed natural logarithms (`log_Remittance`, `log_GDP`, etc.) to measure elasticity coefficients.
   - Calculated `Remittance_share_GDP` to assess macroeconomic dependence.

2. **Econometric Diagnostics & OLS Regression:**
   - **Augmented Dickey-Fuller (ADF) Test:** Evaluated time-series stationarity and unit root properties.
   - **Ordinary Least Squares (OLS) Model:** Quantified multi-variable explanatory relationships between macroeconomic drivers and remittance inflows.

3. **Predictive Modeling & Out-of-Sample Forecasting:**
   - **Train/Test Split:** 1993–2019 (27 years) training period vs. 2020–2024 (5 years) evaluation period.
   - **ARIMA(1,1,1):** Classical autoregressive integrated moving average model for linear time-series momentum.
   - **Random Forest Regressor:** Machine learning non-linear baseline using macroeconomic covariates.

---

## 📊 Key Findings & Results

### 1. Model Evaluation Metrics (2020–2024 Test Horizon)

| Model | MAE | RMSE | MAPE |
| :--- | :--- | :--- | :--- |
| **ARIMA(1,1,1)** | **$0.685B** | **$0.781B** | **7.09%** |
| **Random Forest Regressor** | $2.033B | $2.441B | 19.79% |

* **Conclusion:** ARIMA(1,1,1) significantly outperformed Random Forest, achieving high forecast accuracy (**7.09% MAPE**). Time-series autoregressive models are better suited for capturing long-term trending macroeconomic series than tree-based models, which cannot extrapolate beyond historic bounds.

### 2. Out-of-Sample Remittance Forecast (2025–2028)

| Year | Projected Remittance Inflow (Billion USD) |
| :---: | :---: |
| **2025** | **$11.81 B** |
| **2026** | **$12.37 B** |
| **2027** | **$12.90 B** |
| **2028** | **$13.43 B** |

---

## 📂 Repository Structure

```text
.
├── data/
│   └── finaaal_dataset.xlsx         # Historical dataset (1993–2024)
├── outputs/
│   ├── remittance_vs_gdp.png        # Historical trend visual
│   └── remittance_forecast.png     # Predictive model comparison chart
├── main.py                          # Consolidated Python executable pipeline
├── README.md                        # Documentation
└── requirements.txt                 # Dependencies
