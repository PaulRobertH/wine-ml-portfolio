
# Stage 3 – Macro-Driven Wine Return Forecasting

## 📌 Objective
The goal of this stage was to build a supervised machine learning model that uses macroeconomic indicators and structural features of the fine wine market to forecast 12-month forward returns of the Liv-ex 100 index. This forms the foundation for developing tactical investment strategies based on predictive signals.

---

## 🧠 Modelling Overview

- **Target Variable:** `wine_12m_ret` – 12-month forward return of the Liv-ex 100
- **Algorithm Used:** Random Forest Regressor (non-linear, interpretable)
- **Train/Test Split:** 75/25 split on a chronological basis (no shuffling)
- **Evaluation Metrics:** R² score and Mean Squared Error (MSE)

---

## 🧰 Input Features

| Category         | Features Included |
|------------------|-------------------|
| **Macro Data**   | US CPI (0, 3, 6, 12-month lags), US Interest Rate, Lagged US Interest Rate |
| **Wine Features**| Drawdown, Rolling 12M Volatility, Cumulative Price, Momentum Score |

All data was monthly and aligned between 2004–2024.

---

## 🔍 Key Insights

### 🔢 Feature Importance (Top 5)
1. **US CPI (Lag 0 & 12):** Inflation strongly influences future wine returns, especially around inflection points.
2. **Drawdown:** Periods of deep market stress are often followed by above-average returns.
3. **Rolling Volatility:** High volatility periods often correlate with poor forward returns.
4. **Lagged Interest Rates:** A tightening monetary regime depresses future wine price growth.
5. **Momentum:** Identifies entry/exit regimes and regime transitions.

---

## 📈 Model Results

- **R² (test set):** Moderate — useful for directional forecasting
- **MSE:** Low enough to produce reliable forecast bands
- **Residuals:** No major overfitting, stable generalisation

---

## 📊 Strategic Takeaways

- **Disinflationary periods (falling CPI) with market stress (drawdowns) = optimal entry points**
- **Macro forecasting is best used for regime classification**, not short-term timing.
- **Model enables us to rank forward-looking return environments** by attractiveness

---

## ⚠️ Limitations

- Non-causal: identifies patterns, not economic mechanisms
- Sensitive to macro data integrity
- Not a high-frequency signal — best suited for quarterly strategic positioning

---

## 📁 Outputs

- `3_macro_forecasting_model.ipynb`: Jupyter Notebook with model pipeline and plots
- `/docs/Stage_3_Macro_Forecasting_README.md`: This file
- Feature importance plot and actual vs predicted chart

---

## ✅ Next Step

Move to **Stage 4: Strategy Simulation and Backtesting**, where we turn predictive signals into portfolio allocation rules and evaluate their real-world performance.
