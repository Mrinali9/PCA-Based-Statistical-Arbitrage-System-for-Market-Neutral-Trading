# PCA-Based-Statistical-Arbitrage-System-for-Market-Neutral-Trading
Overview

This project implements a market-neutral statistical arbitrage (pair trading) strategy using Principal Component Analysis (PCA) to extract latent risk factors from multi-asset equity returns.
By neutralizing common market exposure and exploiting mean-reversion in residual returns, the strategy generates systematic long/short signals with controlled risk.

The goal is to demonstrate a research-grade pipeline combining linear algebra, time-series modeling, and backtesting—aligned with real-world quantitative trading practices.

Methodology
1. Data Processing

Collected and aligned daily price data for a basket of correlated equities.

Computed normalized log returns and rolling correlation matrices.

Used rolling windows to avoid look-ahead bias and adapt to regime changes.

2. Factor Extraction via PCA

Applied eigen-decomposition to the rolling correlation matrix.

Identified dominant eigenvectors representing common market factors.

Constructed eigen-portfolios to isolate systematic risk.

3. Residual Modeling & Signal Generation

Neutralized factor exposure to obtain idiosyncratic residual returns.

Modeled residuals using AR(1) / Ornstein–Uhlenbeck (OU) dynamics, capturing mean-reversion behavior.

Generated trading signals using standardized z-scores:

Long positions on negative deviations

Short positions on positive deviations

4. Portfolio Construction

Built dollar-neutral long/short portfolios with risk-normalized position sizing.

Maintained market neutrality throughout the backtest.

Included realistic execution assumptions and rolling recalibration.

5. Backtesting & Evaluation

The strategy was evaluated over 3+ years of daily data using standard risk metrics:

Annualized Return (APR): ~44%

Sharpe Ratio: ≈ 1.19

Cumulative Return: ~176%

Maximum Drawdown: ~31%

Benchmark: BANKNIFTY

Performance metrics indicate strong risk-adjusted returns without excessive overfitting.

Key Results

Successfully extracted latent correlation structures using PCA.

Residuals exhibited statistically significant mean-reversion.

Market-neutral construction reduced directional exposure.

Strategy outperformed the benchmark on a risk-adjusted basis.

Tech Stack

Language: Python

Libraries: NumPy, pandas, scikit-learn, matplotlib, seaborn

Techniques: PCA, AR(1)/OU modeling, rolling backtests, portfolio analytics

Project Structure
├── data/                 # Raw and processed market data
├── notebooks/            # Research and backtesting notebooks
├── src/                  # Core strategy and utility functions
├── results/              # Performance metrics and plots
└── README.md

Future Improvements

Incorporate transaction costs and turnover constraints

Extend to intraday data and higher-frequency signals

Replace PCA with dynamic factor models

Add volatility-scaled position sizing
