
# 📈 Momentum Regime Modelling Plan

This notebook sets up the third stage of our fine wine ML research pipeline: identifying and classifying *momentum regimes* in the Liv-ex 100 using historical price patterns, drawdowns, and predictive machine learning tools.

---

## 🔄 Objectives

- Detect structural changes in wine price momentum
- Tag high vs low momentum periods (bull/bear modes)
- Use drawdown, rolling returns, and reversal detection to:
  - Train classification models
  - Predict upcoming momentum shifts
  - Inform entry/exit timing strategies

---

## 🛠️ Tools To Be Applied

### 📊 Feature Engineering
- Rolling return (3M, 6M, 12M)
- Rolling standard deviation (volatility)
- Drawdown % and recovery length
- Price-to-CPI gap
- Rebased spread to CPI or other macro (Z-score)

### ⚙️ Machine Learning Models
- **Random Forest Classifier**: label momentum states
- **Gradient Boosted Trees**: model regime transitions
- **Logistic Regression**: CPI reversion trigger
- **Hidden Markov Models (HMM)**: detect unobserved wine market states

---

## 🔍 Data Requirements
- Cleaned, monthly Liv-ex 100 returns
- Corresponding macro features:
  - US CPI YoY change
  - Interest rate level
  - FX volatility (e.g. GBP/USD)
  - S&P500 or NASDAQ as risk proxy

---

## 📌 Outputs
- Binary labels: `High Momentum`, `Low Momentum`, `Reversal Risk`
- Regime classification charts overlaid on wine index
- Predictive feature importance chart (from RF or GBM)
- Alert logic for entry signals based on past pattern recurrence

---

## 🧠 Strategic Use
- Use output signals for **tactical allocation**
- Overlay with macro regime from EDA stage (inflation + rates)
- Combine momentum regime with **wine-CPI reversion gap** to filter high-conviction entry points

➡️ Next stage: `4_prediction_model.ipynb`
