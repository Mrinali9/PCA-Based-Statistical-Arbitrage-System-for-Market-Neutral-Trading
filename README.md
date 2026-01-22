# PCA-Based-Statistical-Arbitrage-System-for-Market-Neutral-Trading

## Overview
This project implements a **market-neutral statistical arbitrage (pair trading) strategy** using **Principal Component Analysis (PCA)** to extract latent risk factors from multi-asset equity returns.  
By neutralizing common market exposure and exploiting **mean-reversion in residual returns**, the strategy generates systematic long/short signals with controlled risk.

The project is designed as a **research-grade quantitative pipeline**, reflecting industry-style factor modeling, signal generation, and backtesting workflows.

---

## Methodology

### 1. Data Processing
- Collected and aligned **daily price data** for a basket of correlated equities  
- Computed **normalized log returns** and rolling correlation matrices  
- Used **rolling windows** to prevent look-ahead bias and adapt to regime changes  

### 2. Factor Extraction via PCA
- Performed **eigen-decomposition** on rolling correlation matrices  
- Identified dominant eigenvectors representing **systematic market factors**  
- Constructed **eigen-portfolios** to isolate and neutralize common risk  

### 3. Residual Modeling & Signal Generation
- Removed factor exposure to obtain **idiosyncratic residual returns**  
- Modeled residuals using **AR(1) / Ornstein–Uhlenbeck (OU) dynamics**  
- Generated trading signals via **z-score normalization**:
  - Long on negative deviations  
  - Short on positive deviations  

### 4. Portfolio Construction
- Built **dollar-neutral long/short portfolios**  
- Applied **risk-normalized position sizing**  
- Maintained strict **market neutrality** throughout the backtest  
- Used rolling recalibration for stability  

### 5. Backtesting & Evaluation
Backtested over **3+ years of daily data** using standard performance metrics:

- **Annualized Return (APR):** ~44%  
- **Sharpe Ratio:** ≈ 1.19  
- **Cumulative Return:** ~176%  
- **Maximum Drawdown:** ~31%  
- **Benchmark:** BANKNIFTY  

Results indicate strong **risk-adjusted performance** with controlled downside risk.

---

## Key Results
- Extracted **latent correlation structures** using PCA  
- Residual returns showed **statistically significant mean reversion**  
- Market-neutral construction reduced directional exposure  
- Strategy outperformed the benchmark on a **risk-adjusted basis**

---

## Tech Stack
- **Language:** Python  
- **Libraries:** NumPy, pandas, scikit-learn, matplotlib, seaborn  
- **Techniques:** PCA, AR(1)/OU modeling, rolling backtests, portfolio analytics  

---

---

## Future Improvements
- Incorporate **transaction costs** and turnover constraints  
- Extend to **intraday or higher-frequency data**  
- Replace PCA with **dynamic or nonlinear factor models**  
- Add **volatility-scaled and risk-parity position sizing**

