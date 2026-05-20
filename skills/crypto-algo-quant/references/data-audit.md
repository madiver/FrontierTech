# Data Audit Checklist (OHLCV)

## Integrity and Alignment
- Check missing/duplicate candles.
- Confirm timestamp monotonicity.
- Verify timezone consistency and session conventions.
- Validate bar-completion rules.
- Ensure alignment across venues for merged datasets.

## Anomalies and Artifacts
- Detect stale bars and zero-volume bars.
- Identify split/merge artifacts.
- Flag outlier prints with documented thresholds.

## Contract and Venue Metadata
- Audit contract metadata changes and symbol migrations.
- Verify funding history completeness where relevant.
- Include delisted/dead markets when available to reduce survivorship bias.

## Quantify Data Quality
- Report missingness rates, anomaly counts, and per-venue coverage.
