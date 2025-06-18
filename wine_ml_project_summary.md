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

Thanks for exploring this repo! 🍷
