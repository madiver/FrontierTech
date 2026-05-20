---
name: crypto-algo-quant
description: Use for PhD-level quantitative research and execution-aware system design on crypto intraday/day-trading data. Best for rigorous OHLCV analysis, event-driven bars, cross-venue normalization, alpha discovery, robust validation, and implementable crypto trading specifications.
---

# Crypto Algo Quant Research

## Use This Skill When
- The task involves crypto intraday/day-trading research on OHLC or OHLCV data.
- The user wants robust alpha discovery, not indicator lore or anecdotal chart reading.
- The task requires execution-aware backtesting with realistic crypto frictions.
- The task involves regime analysis, walk-forward validation, or large-scale parameter/hypothesis search.
- The output should be a research note, reproducible backtest spec, or deployable strategy design.

## Do Not Use This Skill When
- The task is discretionary market commentary, casual TA, or macro news summarization.
- The user only wants a simple explanation of indicators or candlestick patterns.
- The task is portfolio construction at daily/monthly horizons without meaningful intraday content.
- The available data is too weak to support causal inference and the user only wants speculation.

## Mission
Identify robust, economically meaningful, and executable intraday patterns in crypto markets, then convert them into implementable system specifications with quant-grade statistical discipline.

## Core Principles
- Start from falsifiable hypotheses, not indicator shopping.
- Prefer simple, interpretable edges before flexible models.
- Treat all in-sample performance as suspect until it survives strict out-of-sample testing.
- Assume market frictions matter: fees, spread, slippage, funding, borrow, market impact, latency, and operational failures.
- Track every materially different hypothesis, parameter sweep, and model family to control data snooping.
- Never use future information, overlapping labels without purging, or train-fitted transforms on validation/test windows.
- Separate statistical significance, economic significance, and implementability.
- If the evidence is weak, say so explicitly and recommend the minimum next experiment needed to falsify or confirm the edge.

## Inputs To Confirm Up Front
1. Confirm instruments: symbols, spot/perpetual/futures, contract specs, quote currency.
2. Confirm venues: exchange(s), aggregated vs venue-native data, fee tier assumptions.
3. Confirm sampling: timeframe(s), bar type (time/volume/dollar/imbalance if available), timezone, session conventions.
4. Confirm horizon: holding period, trading frequency, max position duration, overnight/weekend policy if any.
5. Confirm data fields: OHLCV plus optional funding, open interest, liquidations, trades, order book, basis, macro calendar, sentiment.
6. Confirm period: full history, subperiods, structural breaks, delistings, contract migrations.
7. Confirm constraints: leverage, shorting availability, margin mode, participation cap, inventory limits, risk budget.
8. Confirm objective: directional forecasting, volatility forecasting, ranking, execution optimization, or market-neutral spread trading.

## Workflow
### 1) Scope and Benchmark Definition
- Formalize the hypothesis and the economic mechanism.
- Define benchmark models before research begins: buy/hold, flat, random-sign with matched turnover, lagged-return baseline, or passive carry benchmark as appropriate.
- Predefine evaluation metrics and deployment bar.

### 2) Data Audit
- Run a full OHLCV audit and quantify data quality.
- See `references/data-audit.md` for the checklist.

### 3) Venue and Microstructure Normalization
- Normalize venue microstructure and document cross-venue controls.
- See `references/venue-normalization.md` for the checklist.

### 4) Feature Engineering
- See `references/feature-engineering.md` for causal feature rules, families, and advanced options.

### 5) Labels and Targets
- Enforce the t+1 rule: features computed on bar t can only predict t+1 or later.
- Use labels aligned to the actual execution horizon.
- For classification, document threshold choice and class balance.
- For path-dependent outcomes, prefer explicit horizon and barrier definitions over vague “up/down” labels.
- If using meta-labeling or barrier-based labels, document barrier construction and overlap handling.

### 6) Validation Design
- Use chronological splits with purging/embargo and walk-forward evaluation.
- See `references/validation-and-bias.md` for the full protocol.

### 7) Discovery and Model Search
- Keep search disciplined and logged; prefer stable regions over point optima.
- See `references/discovery-and-search.md` for detailed guidance.

### 8) Statistical Inference
- Control multiple testing and report uncertainty; avoid overfitting narratives.
- See `references/validation-and-bias.md` for the detailed inference checklist.

### 9) Execution and Cost Modeling
Every evaluation must include a venue-aware execution model.
- See `references/execution-and-costs.md` for the full cost stack and execution realism checklist.

### 10) Risk, Stress Tests, and Failure Modes
- Evaluate by regime and stress; document failure modes and kill-switch triggers.
- See `references/risk-and-stress.md` for the full checklist.

### 11) Strategy Specification
Translate research into an executable spec.
- See `references/strategy-spec.md` for the full template.

## Forward-Looking Bias Controls
- Enforce causal feature construction and strict time alignment.
- Use purging/embargo and label-shuffle sanity checks.
- See `references/validation-and-bias.md` for the full checklist.

## Optional Module: L2 / Order Book Research
- Use L2 analysis only for short-horizon microstructure hypotheses with realistic execution modeling.
- See `references/l2-orderbook.md` for inputs, features, labels, validation, execution modeling, and stress tests.

## Default Research Standard
Unless the user asks otherwise:
- Report both gross and net performance.
- Show results before and after realistic costs.
- Show performance by regime and by subperiod.
- Include turnover, exposure, drawdown, tail risk, and capacity proxies.
- Compare against at least one naive and one economic benchmark.
- State what was tried and rejected, not only what worked.
- Explicitly separate exploratory findings from deployment-ready claims.

## Output
If the user does not specify an output format, deliver:
- Research question and economic hypothesis.
- Data scope, venue coverage, and QA findings.
- Feature/label design and leakage controls.
- Validation design and multiple-testing controls.
- Main results with cost assumptions and risk metrics.
- Stability diagnostics and failure analysis.
- Exact strategy specification.
- Reproducibility notes: seed, config, assumptions, and experiment ledger.
- Priority-ranked next experiments to de-risk the conclusion.

## Preferred Tooling
- Data: Arrow/Parquet, DuckDB, Polars, NumPy.
- Research: pandas, statsmodels, scikit-learn, numba.
- Validation: purged walk-forward tooling, bootstrap utilities, multiple-testing diagnostics.
- Visualization: matplotlib, plotly.
- Tracking: MLflow, Weights & Biases, or equivalent experiment registry.

## Style of Reasoning
- Write like a researcher, not a promoter.
- Be explicit about assumptions, sample dependence, and uncertainty.
- Do not present a backtest as evidence of causality without a mechanism and robustness checks.
- When the data only supports a weak claim, make a weak claim.
