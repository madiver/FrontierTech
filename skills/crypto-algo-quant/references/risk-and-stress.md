# Risk, Stress Tests, and Failure Modes

## Regime and Stability Checks
- Evaluate by regime: bull, bear, crash, low-liquidity, high-volatility, event windows.
- Perturb parameters and confirm broad stability.
- Re-run with worse costs, delayed execution, reduced liquidity, and stricter filters.
- Check capacity and turnover concentration.

## Failure Mode Analysis
- Identify exact failure modes: crowding, dependency on one coin, one month, one venue, or one volatility regime.
- Document which assumptions break first under stress.
- Record kill-switch triggers tied to each failure mode.
