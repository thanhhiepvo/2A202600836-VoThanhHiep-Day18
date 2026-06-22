# Screenshot guide (what to capture)

You only need screenshots that show the **printed outputs** / **computed metrics** inside the notebooks (NB1–NB4). After executing notebooks, open the notebook in Jupyter and screenshot the relevant sections.

## NB1 — `01_delta_basics.ipynb`
- Show `_delta_log/` transaction log exists.
- Show the schema enforcement blocked the bad write (`age="thirty"`).
- Show `schema_mode="merge"` added the `tier` column.
- (Optional) DuckDB query output with `tier` groups (premium + NULL).

## NB2 — `02_optimize_zorder.ipynb`
- Screenshot either:
  - **Speedup** result: `Speedup: 10.0×`, OR
  - **Files-pruned ratio** result: `Files-pruned ratio: 55.0×`
- Also screenshot the file-count reduction line:
  - `File reduction: 200 → 55`

## NB3 — `03_time_travel.ipynb`
- Screenshot the `history()` output **after** `restore()`:
  - Must include `v 4  RESTORE`
- Screenshot:
  - `Rows with score<0 after restore: 0`

## NB4 — `04_medallion.ipynb`
- Screenshot:
  - `Bronze rows: 200,000`
  - `Silver rows: 190,052  (Bronze 200,000 → dedup dropped 9,948)`
- Screenshot Gold deliverable metrics:
  - `Distinct dates: 8 (target ≥ 7)`
  - `Distinct models: 3`
  - `Total Gold rows: 24`

