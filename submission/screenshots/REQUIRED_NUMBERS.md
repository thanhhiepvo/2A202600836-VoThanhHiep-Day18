## Confirmed outputs (from the executed notebooks)

### NB1 — Delta basics
- Schema evolution: `schema_mode="merge"` adds `tier`
- DuckDB check: `tier=premium` count `1`, `tier=NULL` count `3`

### NB2 — OPTIMIZE + ZORDER
- Speedup: `10.0×` (target ≥ `3×`)
- Files-pruned ratio: `55.0×` (target ≥ `10×`)
- File reduction: `200 → 55`

### NB3 — Time travel + MERGE + RESTORE
- `Rows with score<0 after restore: 0`
- Final `history()` includes restore as `v 4  RESTORE`
- Total versions: `5` (target ≥ `5`)

### NB4 — Medallion Bronze → Silver → Gold
- Bronze rows: `200,000`
- Silver rows: `190,052` (dedup dropped `9,948`)
- Gold:
  - Distinct dates: `8` (target ≥ `7`)
  - Distinct models: `3`
  - Total Gold rows: `24` (dates × models)

