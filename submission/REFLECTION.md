# Reflection — Vo Thanh Hiep

The anti-pattern my team is most at risk of is **small-file explosion** — letting streaming or micro-batch writes pile up tiny Parquet files without regular `OPTIMIZE` / compaction.

We often focus on getting data into Bronze quickly and defer maintenance. That works until queries slow down and nobody knows why. In this lab, NB2 made the cost visible: before optimization we had ~200 files; after `compact()` + `z_order()` we dropped to ~55 files, with **10.0× speedup** and a **55.0× files-pruned ratio**. Without a scheduled compaction job, we would likely ship a “working” pipeline that quietly fails on latency SLAs. The fix is operational discipline: treat file layout as part of the data contract, not an afterthought.
