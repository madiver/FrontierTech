# Discovery and Model Search

## Logging and Search Discipline
- Log every tested rule family, parameter grid, feature family, and model variant.
- Track all materially different hypotheses to control data snooping.

## Regime Handling
- Search across regimes, but do not mix regime selection with final performance claims.
- Prefer parameter regions with wide stability over single-point optima.

## Interpretability and Leakage Controls
- Use anomaly detection, motif discovery, and clustering only if interpretability and leakage controls are explicit.
- Document which patterns are exploratory vs deployment-ready.
