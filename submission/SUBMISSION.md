# Day 18 Lab Submission — Vo Thanh Hiep (2A202600836)

**Path:** Lightweight (`deltalake` + DuckDB + Polars)  
**Repo:** `thanhhiepvo/2A202600836-VoThanhHiep-Day18`

## Deliverables

| Item | Location | Status |
|---|---|---|
| NB1 — Delta basics | `notebooks/01_delta_basics.py` | ✅ |
| NB2 — OPTIMIZE + Z-order | `notebooks/02_optimize_zorder.py` | ✅ |
| NB3 — Time travel + MERGE | `notebooks/03_time_travel.py` | ✅ |
| NB4 — Medallion pipeline | `notebooks/04_medallion.py` | ✅ |
| Screenshots | `submission/screenshots/` | ✅ |
| Reflection (≤ 200 words) | `submission/REFLECTION.md` | ✅ |
| `_delta_log/` evidence | `submission/screenshots/delta_log_tree.txt` + `delta_log_sample.json` | ✅ |

## Screenshot → rubric mapping

| Screenshot | Rubric criteria covered |
|---|---|
| `Screenshot_notebook1.png` | Delta table + schema enforcement + `tier` via `schema_mode="merge"` |
| `Screenshot_notebook2.png` | Small-file fix: speedup **10.0×** (≥ 3×) and files-pruned **55.0×** (≥ 10×) |
| `Screenshot_notebook3.png` | `history()` ≥ 5 versions incl. RESTORE; `score < 0` count = 0 after restore |
| `Screenshot_notebook4.png` | Bronze→Silver→Gold; **8 dates × 3 models**; Silver < Bronze dedup |
| `delta_log_tree.txt` | `_delta_log/` visible on local filesystem (Bronze/Silver/Gold layout) |
| `delta_log_sample.json` | Sample transaction-log JSON from NB1 (`users_delta`) |

## Key numbers (verified)

- **NB1:** `tier` column added; DuckDB shows `premium` (1) + `NULL` (3)
- **NB2:** Files 200 → 55; speedup 10.0×; files-pruned 55.0×
- **NB3:** MERGE 100K in < 1 s; RESTORE in < 1 s; 5 versions in history
- **NB4:** Bronze 200,000 → Silver 190,052 (dedup −9,948); Gold 24 rows (8 dates × 3 models)

## Reproduce

```bash
make setup && make smoke
make data
# Run notebooks 01–04 (Kernel → Restart & Run All in Jupyter)
```
