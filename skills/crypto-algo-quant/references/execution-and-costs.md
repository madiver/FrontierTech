# Execution and Cost Modeling

## Minimum Cost Stack
- Maker/taker fees or fee schedule assumptions.
- Bid-ask spread and slippage.
- Partial fills, missed fills, and latency assumptions.
- Funding, borrow, or carry costs where relevant.
- Participation caps tied to observed volume/liquidity.
- Tick-size rounding, minimum notional, and leverage/liquidation constraints.

## Advanced Execution Realism
- Queue-position assumptions for passive orders.
- Mark/index/last-price differences for trigger logic and liquidation logic.
- Exchange outages, rate limits, rejected orders, and stale data handling.
- Cross-venue transfer or collateral constraints if the strategy spans venues.
