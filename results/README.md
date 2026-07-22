# Committed result artifacts

Small **derived** outputs of the single pre-registered execution-replay run
(no raw OPRA data; the Databento license does not permit redistributing
quotes, and none of these files contain any).

| File | Contents |
|------|----------|
| `replay/replay_manifest.json` | Run provenance: code commit, UTC timestamp, SHA-256 of the 7.6M-row prediction dump and of every per-day contract extract the replay consumed (the prediction path is reduced to a basename; the file itself is not redistributed). |
| `replay/summary_main.csv` | The full summary grid: model x horizon x scope x theta x slippage x lambda-policy, with decision/gated/fillable counts, pass rates, gross and cost-adjusted means. |
| `replay/bootstrap_cis.csv` | Day-bootstrap (N=10,000) confidence intervals for the registered cells. |
| `replay/attribution_decomposition.csv` | The registered attribution decomposition (floating vs fixed-membership vs contract), overall and by liquidity slice. |
| `replay/summary_regime_15m.csv` | Regime breakdown of the primary cell (time of day, DTE, moneyness, liquidity). |
| `replay/summary_nonoverlap.csv` | Non-overlapping (per-cell cooldown) variant. |
| `replay/summary_delayed_entry.csv` | One-minute delayed-entry latency arm. |
| `replay/unfillable_report.csv`, `replay/unfillable_profiles.csv` | Exit-fillability validity diagnostics. |

Notebook [06](../notebooks/06_execution_aware_replay.ipynb) renders from
exactly these tables; every number in the memo's replay section can be
checked against them.

## Note on `git_dirty: true` in the manifest

The manifest's schema-v1 dirty flag was computed from the full
`git status --porcelain`, which counts **untracked** files. At run time the
untracked entries were the run's own outputs and the local data pulls (per-day
contract extracts, prediction dumps); the tracked source tree matched commit
`884ff426` exactly. Two facts a reviewer can check against the public record:
the adjudication commit `78c035d4` that followed the run touches only
`FINDINGS.md` (103 added lines, no code), and the pre-registered design/code
commits (`613a309f`, `bc1cf8da`, `884ff426`) predate the run. The manifest
writer now records tracked-file dirt separately from untracked counts
(schema v2) so future runs state this distinction machine-readably.
