# Feature Engineering for Crypto OHLC Research

## Principles
- Construct only causal features from completed bars.
- Align all features to decision time; document lag/lead for each feature.
- Prefer vectorized or columnar operations over row-wise logic for large-scale research workloads.
- Use log returns for statistical modeling and simple returns for aggregation, reporting, and implementation checks.

## Minimum Feature Families
- Return structure: close-to-close, open-to-close, gap, multi-horizon lagged returns.
- Candle anatomy: body, wick ratios, close location value, range compression/expansion.
- Volatility/range: ATR, Parkinson/Garman-Klass style estimators when applicable, realized range, jump flags.
- Trend and reversal: moving-average spreads, breakout distance, rolling z-scores, channel position.
- Volume/liquidity proxies: relative volume, Amihud-style illiquidity proxies, turnover, range-per-volume.
- Intraday seasonal structure: hour-of-day, day-of-week, funding-window indicators, event-time proximity.
- Cross-asset context when allowed: BTC lead/lag, sector-relative strength, stablecoin stress proxies.

## Optional Advanced Features
- Event-driven bars (volume, dollar, imbalance, CUSUM) when time bars are demonstrably inadequate.
- Funding, basis, open interest, liquidations, order-flow, order-book imbalance, trade-sign imbalance.
- News or macro-calendar proximity features if they are timestamp-clean and available ex ante.
