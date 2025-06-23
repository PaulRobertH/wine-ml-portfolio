# 📦 Wine Market Forecasting ML

Welcome to the Wine Market Forecasting project. This repository applies data science and machine learning to understand and predict the performance of fine wine indices, particularly the **Liv-ex 100**, using macroeconomic indicators like **inflation, interest rates, and equity markets**.

---

## 🔍 Project Overview

### 🎯 Objective
To model, visualise, and forecast fine wine market trends using macroeconomic data and machine learning models for tactical allocation, risk regime awareness, and cycle-based investing.

### 🧰 Key Tools & Techniques
- Python (pandas, sklearn, matplotlib, seaborn)
- Random Forest (classification + regression)
- Time-series feature engineering
- Rolling correlation, macro spreads, drawdowns
- Visual insights and ML-based prediction zones

---

## 🗂️ Repository Structure

```
wine-forecasting-ml/
├── README.md                     # This file
├── notebooks/
│   ├── 1_eda_correlation.ipynb     # EDA + rolling correlations
│   ├── 2_macro_feature_engineering.ipynb  # Lag creation, spreads, volatility
│   └── 3_momentum_regime_model.ipynb      # Random Forest: reversal prediction
├── data/
│   ├── merged_df.csv               # Merged macro + wine dataset
│   └── raw/                        # Optional raw macro/wine input files
├── reports/
│   ├── wine_ml_project_summary.md         # Full strategy + roadmap
│   ├── eda_correlation_summary.md         # Notebook 1: what we explored
│   └── momentum_regime_model.md           # Model build + insight
└── requirements.txt               # Package list (optional)
```

---

## 📊 Key Results
- Visualised correlation between CPI and Liv-ex 100
- Modelled impact of interest rates on wine returns
- Detected reversal regimes using Random Forests
- Created probability-driven entry signals (0.6+ = high reversal risk)

---

## 🚀 How to Run
1. Clone the repo
2. Install requirements with `pip install -r requirements.txt`
3. Open notebooks in `notebooks/`
4. Read through `reports/` for documentation

---

## 👨‍🔬 Author & Purpose
Built as part of a wine macro forecasting and ML analysis capstone project — integrating real financial data with machine learning for insight-driven investing.

---

## 📌 Next Stage
- Backtesting allocation strategies
- Expanding to other Liv-ex indices
- Streamlit/Gradio UI deployment
- Integration with wine pricing APIs

---
# 📘 Liv-ex Fine Wine ML Pipeline: Progress Report & Roadmap

## ✅ STAGE 1–2: Setup, Cleaning, Alignment (Complete)

### 1. Data Sources Ingested
We pulled and cleaned data from:

- 📈 **Liv-ex 100 Index** (fine wine price proxy)
- 💵 **Macro indicators**: CPI, FX (GBP/USD, EUR), commodities (Oil, Gold), interest rates (US10Y, UK10Y)
- 🧮 **Monthly frequency** aligned using `Plot_Date`

### 2. Cleaning Steps
- Standardised all date formats
- Forward/back filled missing values
- Merged into a master DataFrame: `merged_df`
- Synced start from **Jan 2003 → Present (2025)**


## ✅ STAGE 3: Exploratory & Correlation Analysis (Complete)

### 🔍 Correlation Insights
- **Rolling 12-month correlations** between wine and macro factors (inflation, oil, FX, etc.)
- **Rebased comparison charts** for relative performance
- Key finding: **Wine has recently decoupled from inflation trends** — potential opportunity


## ✅ STAGE 4: Market Cycle Tagging & Analysis (Complete)

### 📉 Peak & Trough Detection
- Used `scipy.signal.find_peaks` on Liv-ex 100
- Tagged **local highs and lows**

### 📊 Cycle Labeling
Each timestamp labeled as one of:

- `Accumulation` (post-trough)
- `Bull Market`
- `Distribution` (post-peak)
- `Bear Market`

### 🔄 Phase Logic
- Defined based on **moving average structure** and proximity to extrema
- Stored in `phase` column

### 📈 Cycle Statistics Summary

| Metric             | Value        |
|--------------------|--------------|
| Avg Bull Duration  | ~23.2 months |
| Avg Bear Duration  | ~15.5 months |
| Avg Bull Return    | +34.97%      |
| Avg Bear Return    | −18.66%      |
| Last Trough        | ~2020-01     |
| Last Peak (ATH)    | ~2022-09     |
| Current Phase      | Bear (2025)  |
| Projected Bull Restart | ~2024-08-01 |

### 🖼️ Final Cycle Chart Includes
- Liv-ex 100 price series
- 50-day & 200-day moving averages
- Peak and trough markers
- Market phase shading (bull, bear, etc.)
- Fibonacci retracement (from 2015 low to 2022 ATH)
- **Projected ML-based cycle reversal marker**

### ✅ Output Data Saved
- `livex_cycle_data.csv`: Full chart with phase labels
- `livex_cycle_summary.csv`: Stats for ML training

---

## 🔜 STAGE 5: Feature Engineering for ML (Next)

We now prepare **features (X)** and **targets (y)** for ML forecasting.

### 🎯 Targets
- `next_6m_return` → Regression target
- `cycle_phase` → Classification label

### 🧠 Feature Set (`X`)
| Feature              | Description                              |
|----------------------|------------------------------------------|
| wine_12m_return      | 12M trailing return                      |
| wine_12m_volatility  | Std deviation over past 12 months        |
| price_above_12m_MA   | Boolean if price > 12M moving average    |
| cpi_yoy              | Year-on-year inflation rate              |
| oil_price_change     | Monthly % change in oil price            |
| fx_3m_lagged         | GBP/USD 3-month lagged return            |
| interest_rate_change | Δ in 10Y government bond yields          |

Will be exported as:
- `X_features.csv`
- `y_labels.csv`

---

## 🔮 STAGE 6+: Machine Learning & Forecasting

| Stage | Goal                                                   |
|-------|--------------------------------------------------------|
| 6     | Train models (XGBoost, Logistic Regression, etc.)     |
| 7     | Use Gaussian Process Regression for cycle forecasting |
| 8     | Evaluate metrics (ROC, MAE, F1 Score, etc.)           |
| 9     | Build dashboards (Streamlit, Jupyter widgets, etc.)   |

---

Let me know if you need the `.md`, `.txt`, or `.pdf` exported — I can generate and save the file instantly for GitHub or documentation.



Thanks for exploring this repo! 🍷
