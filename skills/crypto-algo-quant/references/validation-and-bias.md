# Validation, Leakage, and Inference

## Validation Design
- Use chronological train/validation/test splits.
- Add purging and embargo whenever labels or holding windows overlap.
- Prefer walk-forward evaluation; use combinatorial or repeated purged schemes when comparing many variants.
- Lock preprocessing on train only, then apply unchanged to validation/test.
- Preserve a final untouched test window whenever feasible.

## Forward-Looking Bias Checklist
- Enforce t+1 usage for all features.
- Shift labels strictly forward.
- Use as-of joins only.
- Purge overlapping observations and embargo adjacent windows.
- Use completed bars only; never leak partial-bar information.
- Prevent cross-venue future leakage.
- Fit transforms on train only.
- Validate on multiple walk-forward windows.
- Run a time-shuffle or label-shuffle leakage sanity check and confirm performance collapses.
- Document the timestamp lineage of every feature and label.

## Statistical Inference and Multiple Testing
- Control for multiple testing when searching many rules or models.
- Report uncertainty around Sharpe, hit rate, drawdown, and turnover-adjusted returns.
- Quantify overfitting risk with explicit diagnostics rather than narrative reassurance.
- Compare candidate models against benchmarks with formal predictive-ability tests when possible.

## Leakage and Negative Controls
- Add leakage tests, shuffled-label sanity checks, and negative controls.
- Re-run with delayed execution, worse costs, and reduced liquidity to probe sensitivity.
- Treat any unexplained OOS jumps as a leakage hypothesis until disproven.
