# Short-Horizon Options-Surface Forecasting

Forecasting short-horizon implied-volatility surface dynamics for SPY options,
built on Databento OPRA consolidated quote data.

> **Status: work in progress.** The memo and notebooks are being prepared for
> publication.

## What's here

| Path | Contents |
|------|----------|
| [`memo/`](memo/) | Research memo (LaTeX source + PDF) — the headline write-up: question, pre-registered expectations, results, and what changed along the way. |
| [`notebooks/`](notebooks/) | Supporting analysis notebooks (sanitised, runnable against the included data extracts). |

## The short version

- **Data**: one month of SPY option quotes (Databento OPRA CMBP-1), built into
  arbitrage-checked volatility-surface states on a 15-minute grid.
- **Task**: predict surface moves at short horizons; evaluate against a
  persistence baseline with execution-aware (spread-adjusted) metrics.
- **Approach**: pre-registered expectations before each experiment round;
  results reported as registered, including the negative ones.

Read the [memo](memo/memo.pdf) for the full story.
