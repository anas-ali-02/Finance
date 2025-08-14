# Algorithmic Trading using Machine Learning

## Overview
This project implements and evaluates multiple algorithmic trading strategies using financial data, statistical models, and machine learning concepts. The primary goal is to explore different approaches for generating trading signals, assessing performance, and combining quantitative analysis with predictive modeling.

The strategies implemented include:
1. **Unsupervised Learning Trading Strategy** – Detects patterns and clusters in asset price movements without labeled outcomes.
2. **Twitter Sentiment Trading Strategy** – Uses sentiment data from social media to inform trading decisions.
3. **Intraday GARCH Trading Strategy** – Models market volatility to adapt trading positions based on risk.

---

## Data Sources
The project uses:
- **Market Data**: Historical price data from Yahoo Finance (`yfinance` library).
- **Twitter Data**: Sentiment scores, engagement metrics (likes, comments, impressions), and activity counts for specific stock tickers.
- **Technical Indicators**: Generated using `pandas_ta` to extract features like RSI, MACD, moving averages.

---

## Methodology

### 1. Data Collection
- Fetched historical OHLCV (Open, High, Low, Close, Volume) data for selected tickers.
- Loaded pre-computed Twitter sentiment metrics and engagement ratios.
- Merged market and sentiment datasets based on ticker and date.

**Why**: Combining price history with sentiment and engagement data can improve the predictive power of trading models.

---

### 2. Feature Engineering
- Created technical indicators using `pandas_ta` (e.g., RSI, MACD, Bollinger Bands).
- Normalized sentiment and engagement scores.
- Calculated returns and volatility.
- Generated lag features to capture short-term memory of the market.

**Why**: Features derived from both market data and sentiment help capture different aspects of price behavior — technical, psychological, and statistical.

---

### 3. Strategy 1: Unsupervised Learning
- Applied clustering algorithms (e.g., K-Means) on technical + sentiment features.
- Identified market regimes (e.g., bullish, bearish, sideways) from clusters.
- Backtested regime-based trading rules.

**Why**: Unsupervised learning reveals hidden patterns without needing predefined labels, useful when the “ground truth” for buy/sell is unknown.

---

### 4. Strategy 2: Twitter Sentiment Trading
- Used `twitterSentiment` scores to classify market mood (positive, neutral, negative).
- Created trading signals based on thresholds in sentiment and engagement ratios.
- Evaluated returns when following sentiment-driven signals.

**Why**: Social sentiment can move prices rapidly, especially in short-term trading, so integrating it can give a competitive edge.

---

### 5. Strategy 3: Intraday GARCH Volatility Strategy
- Applied GARCH models to intraday returns to estimate conditional volatility.
- Adjusted position sizes dynamically — larger positions in low volatility, smaller in high volatility periods.
- Measured strategy performance under different volatility regimes.

**Why**: Volatility modeling is crucial for managing risk and optimizing trade sizes.

---

### 6. Backtesting & Evaluation
- Simulated trades using historical data for each strategy.
- Calculated key metrics: Sharpe ratio, win rate, drawdown, cumulative returns.
- Compared performance of individual strategies and potential combined strategies.

---

## Key Takeaways
- **Multimodal features** (price + sentiment + volatility) can improve trading models.
- Unsupervised learning is useful for regime detection.
- Sentiment trading is sensitive to data quality and threshold settings.
- Volatility-adjusted trading helps control risk.

---

## Next Steps
- Replace pre-computed sentiment scores with raw NLP processing of tweets.
- Expand to more tickers and asset classes.
- Test ensemble strategies combining all three approaches.

