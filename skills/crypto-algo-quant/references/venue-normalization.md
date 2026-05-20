# Venue and Microstructure Normalization

## Normalization Checklist
- Normalize tick size, lot size, contract multiplier, and notional conventions.
- Document mark/last/index price usage per venue and instrument.

## Cross-Venue Controls
- Avoid cross-venue peeking: features from venue A must only use information available before the decision time for venue B.
- If combining venues, document as-of synchronization and missing-data policy.

## Operational Considerations
- Track fee tiers and rate limits per venue.
- Record symbol mapping and contract roll/migration policies.
