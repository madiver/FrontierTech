# Strategy Specification Template

## Scope
- Universe and trading schedule.
- Signal formula and lag conventions.

## Execution Rules
- Entry, sizing, scaling, exit, stop, timeout, and cancel rules.
- Execution policy: market/passive/sliced/VWAP/TWAP/participation-based.

## Risk Limits and Controls
- Max leverage, max daily loss, max concurrent positions, max exposure by coin/sector/venue.
- Kill switches: data gap, spread blowout, venue outage, abnormal funding, depeg, slippage breach.

## Monitoring and Maintenance
- Monitoring metrics and alerting thresholds.
- Re-training or re-calibration cadence.
