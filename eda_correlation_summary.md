
## 📊 EDA & Correlation Analysis Summary: Wine vs Macro Assets

This document summarises the full exploratory data analysis (EDA) and correlation work completed in `2_eda_and_correlations.ipynb`, which visually and statistically evaluates the relationship between fine wine indices and macroeconomic indicators like CPI, interest rates, FX, commodities, and equity markets.

---

### 📁 Dataset Contents
We merged monthly time series from:
- **Wine Indices**:
  - Liv-ex 100
  - Liv-ex 1000
  - Burgundy 150
  - Champagne 50
  - Bordeaux Legends 40
  - California 50
  - Rhone 100
  - Italy 100
  - Investables Index
- **Macro Variables**:
  - **Inflation**: US CPI (YoY and monthly)
  - **Interest Rates**: US Fed Funds Rate (target rate proxy)
  - **Commodities**: Crude Oil, Gold, Cocoa
  - **Currencies**: GBP/USD, EUR/USD, GBP/JPY
  - **Equities**: S&P 500 Futures, NASDAQ, Hang Seng
  - **Dollar Index**: DXY

---

### 🔍 Key EDA Tasks Completed

#### 1. ✅ Data Cleaning
- Monthly datetime index aligned across all datasets
- Forward-fill/back-fill for missing values
- Dropped columns with excessive nulls (e.g., incomplete Liv-ex subseries)

#### 2. 🔗 Correlation Matrix (Wine ↔ Macro)
- Full Pearson correlation matrix between all wine indices and macro variables
- Plotted via heatmap

**Findings:**
- Wine vs Macro: Weak short-term correlation overall
- Slight positive correlation with Gold and S&P 500
- Negligible link with CPI, FX, or interest rates at monthly level

#### 3. 🔄 Inter-Wine Index Correlations
- Correlation matrix among all Liv-ex indices
- Key insight: **very high internal correlation** (0.85–0.98)
- Burgundy 150 and Investables show highest cohesion with Liv-ex 100
- Italy 100 and Rhone 100 sometimes diverge in early periods

📌 **Conclusion**: Diversification within wine indices is limited. Wine market acts in synchrony, especially in bull cycles.

#### 4. 📈 Rolling Correlation (12M)
- Rolling correlation (12-month window) between Liv-ex 100 and each other index
- Overlaid to highlight structural changes in co-movement

**Visual Trends:**
- Bull markets show tightly converged correlations (~0.95)
- Corrections (e.g. 2014–2016) show divergence, especially Champagne and Rhone
- Indicates phase shift or regional variation in wine demand/performance

#### 5. 📉 Wine vs CPI Spread & Reversion
- Rebased CPI and Liv-ex 100 to 100 (starting 2003)
- Computed `Wine - CPI` spread over time
- Plotted divergence and potential reversion signals

**Observed Insights:**
- Wine typically outpaces CPI in bull periods (2006–2011, 2020–2022)
- Wine underperformed CPI during rate-driven inflation shock (2022–2023)
- Long periods of mean-reversion suggest tactical entry points

#### 6. 📊 Interest Rate Regime Analysis
- Segmented periods by average Fed Funds rate:
  - **Low**: <1%
  - **Mid**: 1–3%
  - **High**: >3%
- Calculated average wine returns and CAGR by regime

**Results:**
- CAGR highest during **low rate regimes** (~7.8%)
- Mid-rate periods show wine stagnation
- High-rate environments compress returns (and increase downside risk)

---

### 🧮 Statistical & ML Tools Applied

#### 📐 Statistical Methods
- Pearson correlation matrix (static + rolling)
- Rolling windows (12-month) for trend stability
- Rebased cumulative returns (Wine, CPI, S&P, Gold)
- Drawdown inspection via visual deltas (Wine vs Macro)
- Regime segmentation using thresholds (Interest Rates, CPI)

#### 🤖 Machine Learning & Predictive Tools Referenced or Used
- **Random Forest Regression**: Used later for Liv-ex return prediction
- **Random Forest Classifier**: Used for wine momentum shift classification (in model notebook)
- **Momentum reversal detection** (binary classification)
- **Wine-CPI reversion probability model** (logistic or threshold-based overlay)

---

### 🖼️ Visual Summary (Suggested Graphs to Embed)
> Upload to `reports/images/` and reference in .md:

- `rolling_corr_livex100_vs_others.png`: Rolling correlation to all wine sub-indices
- `wine_vs_cpi_rebased.png`: Cumulative comparison of CPI vs Liv-ex 100
- `wine_minus_cpi_spread.png`: Divergence & gap model vs CPI
- `wine_rate_regime_cagr.png`: CAGR by interest rate bands
- `wine_macro_corr_matrix.png`: Heatmap of wine ↔ macro correlation

---

### 💡 Strategic Interpretations

- **Wine indices are tightly correlated internally**, meaning diversification must come from external macro overlay, not cross-index blending.
- **Rebasing vs CPI reveals persistent cycles** of over/underperformance. These offer timing signals for accumulation.
- **Interest rate regimes affect wine returns** materially — most notably, performance deteriorates in mid-to-high rate cycles.
- Macro correlations alone don’t predict wine short-term moves, but they **modulate the return envelope** in sustained macro trends.

---

### 📍Recommendations for Modelling & Dashboard
- Label periods of wine-CPI gap > 1.0 for potential tactical entries
- Use inter-index correlation to classify volatility or synchrony regimes
- Integrate CPI reversion gap as signal input into portfolio weights
- Expand macro labels to include inflation quartiles, FX shock periods

---

This EDA and correlation layer directly informed:
- Our reversion overlays
- Feature sets for predictive models
- Tactical entry signal logic and momentum regime classification

➡️ Next notebook: `3_momentum_regime_model.ipynb`
