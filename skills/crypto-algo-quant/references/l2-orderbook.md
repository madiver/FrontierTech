# Level 2 / Order Book (LOB) Research Module

## When to Use L2 Analysis
- The hypothesis involves short-horizon price formation (seconds to minutes).
- The strategy depends on execution quality, liquidity, or microstructure effects.
- The user is exploring order flow, imbalance, or market-making behavior.
- The goal includes taker timing, maker defense, or execution optimization.

## When NOT to Use L2
- The horizon is multi-hour or longer without clear microstructure linkage.
- Only OHLCV data is available.
- The user cannot model latency, fees, and execution realistically.
- The research question is purely directional without execution constraints.

## Required Inputs (L2-Specific)
1. Confirm order book depth: number of levels (top 10, 50, full book).
2. Confirm update frequency: snapshot vs event-driven (tick-level preferred).
3. Confirm order events: additions, cancellations, executions (if available).
4. Confirm trade prints: aggressor side, size, timestamp alignment.
5. Confirm venue specifics: matching engine behavior, batching, timestamp resolution.
6. Confirm latency assumptions: data delay, decision delay, execution delay.
7. Confirm queue visibility: queue position vs aggregate depth only.

## L2 Feature Engineering
Core microstructure features:
- Order Book Imbalance (OBI): OBI = (sum Q_bid - sum Q_ask) / (sum Q_bid + sum Q_ask) at multiple depths.
- Queue imbalance (top of book): imbalance at best bid/ask to anticipate short moves.
- Microprice or weighted mid: volume-weighted mid that incorporates imbalance.
- Spread dynamics: spread level, changes, and regime classification.
- Depth shape: slope, convexity, and liquidity concentration across levels.
- Order Flow Imbalance (OFI): net change in bid/ask volume due to new orders, cancellations, and executions.

Advanced features (optional):
- Multi-level imbalance vectors for deep book structure.
- Cancellation rates and order-book decay metrics.
- Trade-flow imbalance (aggressive buy vs sell flow).
- Book pressure velocity (rate of imbalance change).
- Liquidity gaps or voids.
- Hidden-liquidity proxies (repeated refilling behavior).

## Labeling and Prediction Targets (L2 Context)
- Use event-time or short fixed horizons (next tick, next N trades, next 1-10 seconds).
- Avoid long-horizon labels; L2 signal decays rapidly.
- Prefer mid-price change, direction of next move, or short-horizon return buckets.
- Align labels strictly after feature timestamps to prevent leakage.

## Validation Requirements (Stricter for L2)
- Use event-time splitting, not just clock-time.
- Enforce purging and embargo for overlapping horizons.
- Test across volatility and liquidity regimes and times of day.
- Evaluate stability across venues if applicable.

## Execution Modeling (Mandatory for L2)
L2-based strategies are invalid without execution realism.

Must include:
- Queue position assumptions for passive orders.
- Fill probability modeling.
- Partial fills and cancellations.
- Latency sensitivity (decision plus exchange).
- Slippage relative to depth consumed.
- Fee tier assumptions.

Optional but recommended:
- Adverse selection modeling (post-fill drift).
- Maker vs taker decision logic.
- Dynamic order placement (join, step ahead, cross).

## Strategy Archetypes Enabled by L2
1. Ultra-short-horizon taker models using imbalance and flow to predict next move.
2. Execution optimization via liquidity timing and depth-aware logic.
3. Maker or market-making defense against toxic flow and adverse selection.
4. Regime switching between maker and taker modes.

## Failure Modes (Critical)
- Signal decay: predictive power exists only at very short horizons.
- Latency arbitrage: slower systems lose the edge.
- Spoofing or fake liquidity: large orders that cancel quickly.
- Exchange artifacts: batching, timestamp rounding, stale updates.
- Overfitting microstructure noise.

## Required Stress Tests (L2)
- Add artificial latency and confirm the edge persists.
- Increase slippage assumptions and re-evaluate profitability.
- Remove top-of-book features and verify robustness.
- Shuffle order flow and confirm signal collapse.
- Test during crashes, thin liquidity, and high volatility.

## Interpretation Rules
- Treat L2 signals as mechanical pressure indicators, not sentiment.
- Do not assume visible liquidity is real.
- Prioritize consistency across regimes and venues over peak performance.
- If the edge only exists before costs or latency, reject it.
