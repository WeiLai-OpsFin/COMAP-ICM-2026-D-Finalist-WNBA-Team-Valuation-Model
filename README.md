# From Wins to Worth: WNBA Team Valuation Model

This repository contains a from-scratch Python reconstruction of a COMAP ICM 2026 Problem D Finalist project. The model links sports performance, attendance, ticket pricing, revenue, franchise valuation, and leverage decisions into one reproducible workflow.

## Competition Context

- Competition: COMAP Interdisciplinary Contest in Modeling, 2026
- Problem track: Problem D, sports-team valuation and decision modeling
- Result: Finalist
- Project type: team modeling project with a reproducible Python implementation

## My Contribution

My work in this public code release focuses on rebuilding the full analytical pipeline in Python, including data staging, game-level cleaning, Elo-based performance forecasting, attendance and pricing models, finance and valuation modules, decision comparison, scenario analysis, Monte Carlo simulation, and final business visualizations.

## Key Modeling Result

The decision module compares three strategy options: `NO_MOVE`, `SIGN_STAR`, and `TRADE_SUPERSTAR`. In the checked-in result snapshot, the model recommends `NO_MOVE` because it produces the highest decision score while maintaining the preferred leverage level.

| Action | Decision Score | Net Profit (M) | Valuation (M) | Leverage |
|---|---:|---:|---:|---:|
| NO_MOVE | 10.03 | 6.04 | 292.75 | 0.05 |
| SIGN_STAR | 6.49 | 1.83 | 337.10 | 0.05 |
| TRADE_SUPERSTAR | 4.48 | -0.44 | 355.04 | 0.05 |

Detailed result files are available in `results/02_business_outputs/`, especially:

- `recommended_strategy.csv`
- `decision_comparison_table.csv`
- `baseline_finance_summary.csv`

The main business charts are in `figures/03_business/`.

![Decision comparison: net profit](figures/03_business/decision_profit_comparison.png)

The main review entry points are the reproducible pipeline, the checked-in result tables, and the generated figures.

## Design Principle

The important design choice in this version is simple: the repository avoids hard-coding final competition outputs. Instead, it uses visible model-side assumptions, conservative rounded parameters, and a runnable pipeline so that the results can be regenerated from the checked-in seed data and configuration.

## How to Run

```bash
pip install -r requirements.txt
python -m src.run_all
```

To attempt online collection from public sources, run:

```bash
ONLINE_COLLECTION=1 python -m src.run_all
```

If online collection fails, the workflow still uses the raw/source-like offline snapshot in `data/00_seed/`, so the whole pipeline remains runnable.

## Folder Map

```text
config/                         model settings only, no reported result targets
data/00_seed/                   raw/source-like snapshot and assumption inputs
data/01_raw_downloaded/         staged raw inputs after collection step
data/02_interim/                cleaned game-level table
data/03_processed/              model predictions
src/                            all Python pipeline steps
results/                        generated tables
figures/                        generated plots
```

## Pipeline

1. `step00_collect.py` — collect/stage raw inputs
2. `step01_clean.py` — clean games, capacity, attendance, rest days
3. `step02_explore.py` — exploratory plots
4. `step03_elo.py` — rolling Elo model and future win forecast
5. `step04_attendance_pricing.py` — attendance model and dynamic ticket pricing
6. `step05_finance_valuation.py` — revenue, profit, valuation, leverage
7. `step06_optimization.py` — NO_MOVE / SIGN / TRADE comparison
8. `step07_scenarios.py` — interest, market expansion, injury scenarios
9. `step08_monte_carlo.py` — simulation from residual and business shocks
10. `step09_sensitivity.py` — one-factor sensitivity
11. `step10_business_plots.py` — final charts

## Clean-v2 Changes

This version improves the earlier no-leak package using only visible model-side choices:

- a rounded conservative roster-risk Elo adjustment;
- a rounded market revenue multiple instead of forcing valuation to a known output;
- an interest-rate discount factor for franchise valuation;
- season-level Monte Carlo aggregation instead of forcing simulation quantiles.
