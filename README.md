# Strategy Strength Classifier (Mini Meta-Model)

This project builds a simple machine learning classifier to predict whether a trading strategy-specifically, a moving average (MA) crossover-is likely to be profitable in the next few days, using rolling technical indicators as features.

---

## Objective

To train a classifier that learns from historical market conditions and predicts the expected profitability of a signal-based trading strategy.

---

## How It Works

1. **Data Source**: Historical SPY data from [Yahoo Finance](https://finance.yahoo.com/), via the `yfinance` API.
2. **Strategy**: 
   - Generate buy/sell signals using a **Moving Average Crossover** (short = 10 days, long = 50 days).
   - Label each signal as **+1 (profit)** or **-1 (loss)** depending on the price movement over the next 5 days.
3. **Features Extracted**:
   - **Rolling Volatility** (14-day std. dev of returns)
   - **RSI (14-day)** using Wilder’s smoothing
   - **10-Day Price Slope** (via linear regression)
   - **Volatility Regime** (quantile-based: low / medium / high)
4. **Model**:
   - Logistic Regression classifier
   - Trained on historical labeled signals
   - Evaluated using accuracy, precision, recall, and F1-score

---

## Results

- **Accuracy**: ~72% on the test set (2010–2024 SPY data)
- **Classifier behavior**: Effectively distinguishes between profitable and unprofitable signals
