# Electricity Demand Forecasting: A Hybrid Approach using SARIMA and Gradient Boosting  

##  Overview  
This project focuses on **forecasting electricity demand** using a hybrid modeling approach that combines **statistical time series analysis (SARIMA)** and **machine learning (Gradient Boosting Regressor)**.  
The aim is to improve both **short-term and long-term forecasting accuracy**, supporting **grid management, energy planning**, and **policy-making**.  

The study utilizes electricity production and demand data spanning **1985 to 2025**, obtained from publicly available Kaggle datasets.  

---

##  Objectives  
- Develop a **data-driven forecasting pipeline** for electricity demand.  
- Compare classical (SARIMA) and machine learning (Gradient Boosting) models.  
- Forecast electricity demand for both **hourly (short-term)** and **monthly (long-term)** horizons.  
- Identify **seasonal, daily, and weekly consumption patterns**.  

---

##  Dataset Description  

Three datasets were sourced from **Kaggle** and merged to form a unified time series:  

| Dataset | Duration | Source |
|----------|-----------|--------|
| **IND_Demand (2019–2025)** | Monthly electricity demand | [FancifulCrow – Kaggle](https://www.kaggle.com/datasets/fancifulcrow/collection-of-time-series) |
| **Electric Production (1985–2017)** | Historical generation data | [kandij – Kaggle](https://www.kaggle.com/datasets/kandij/electric-production) |
| **Hourly Load Data India (2019–2025)** | Hourly consumption data | [shubhamvashisht – Kaggle](https://www.kaggle.com/datasets/shubhamvashisht/hourly-load-india-electrical-load-forecasting) |

A missing gap between **2018 data points** was imputed using **seasonal interpolation** to maintain temporal consistency.

---

##  Methodology  

### 1. Data Preprocessing  
- Merged datasets to form a continuous time series (1985–2025).  
- Filled missing values via **seasonal interpolation**.  
- Created new **time-based features**:
  - Hour of day, day of week, month of year  
  - Lag features (Lag-24, Lag-168)  
  - Rolling averages for trend detection  

### 2. Long-Term Forecasting — SARIMA  
- Modeled monthly demand using **SARIMA(1,1,1)(1,1,1)[12]**.  
- Determined parameters using **ACF/PACF** plots and **AIC/BIC** metrics.  
- Conducted residual diagnostics:
  - **Ljung-Box test** (autocorrelation)
  - **Jarque–Bera test** (normality)
- Produced forecasts for 2025–2026.  

### 3. Short-Term Forecasting — Gradient Boosting  
- Trained a **Gradient Boosting Regressor (GBR)** using engineered hourly features.  
- Performed **recursive 24-hour forecasts** for grid management.  
- Evaluated model performance using **Root Mean Squared Error (RMSE)** = **3956.11**.  

---

##  Results  

| Model | Forecast Type | RMSE | Key Insights |
|--------|----------------|------|---------------|
| **SARIMA(1,1,1)(1,1,1)[12]** | Monthly | — | Captures long-term trend and annual seasonality. |
| **Gradient Boosting Regressor** | Hourly | **3956.11** | Captures short-term fluctuations and diurnal cycles. |

###  Key Visualizations  
- **Daily Profile — Average Demand by Hour**  
- **Weekly Profile — Average Demand by Day of Week**  
- **SARIMA Forecast vs Actual Monthly Demand**  
- **24-Hour Gradient Boosting Forecast**

---

##  Insights  
- **Hybrid modeling** improves both short-term and long-term prediction accuracy.  
- **Feature engineering** (lags + cyclical encodings) significantly boosts model performance.  
- **Gradient Boosting** adapts better to non-linear and seasonal load patterns.  

---

##  Future Work  
- Incorporate **weather, temperature, and holiday** variables as external regressors.  
- Experiment with **XGBoost, LightGBM, Prophet, LSTM, and Temporal CNNs**.  
- Extend modeling to **supply-side forecasting** (solar, wind, hydro).  
- Develop **real-time adaptive models** for continuous learning from live grid data.  

---

##  Citation  
If you use this project or its data combination in your research, please cite:  
> Aliasgar Abbas Ringnodwala, *Electricity Demand Forecasting: A Hybrid Approach using SARIMA and Gradient Boosting*, RV Institute of Technology and Management, 2025.  

---

##  References  
- [FancifulCrow – IND_Demand Dataset (Kaggle)](https://www.kaggle.com/datasets/fancifulcrow/collection-of-time-series)  
- [kandij – Electric Production Dataset (Kaggle)](https://www.kaggle.com/datasets/kandij/electric-production)  
- [shubhamvashisht – Hourly Load India Dataset (Kaggle)](https://www.kaggle.com/datasets/shubhamvashisht/hourly-load-india-electrical-load-forecasting)  
- Hyndman, R.J., & Athanasopoulos, G. (2021). *Forecasting: Principles and Practice*.  
- Friedman, J. H. (2001). *Greedy Function Approximation: A Gradient Boosting Machine*. *Annals of Statistics*, 29(5), 1189–1232.  

---

##  Author  
**Aliasgar Abbas Ringnodwala**  
Department of Computer Science and Engineering  
RV Institute of Technology and Management, Bangalore, India  
[aliasgarabbas42@gmail.com](mailto:aliasgarabbas42@gmail.com)  
