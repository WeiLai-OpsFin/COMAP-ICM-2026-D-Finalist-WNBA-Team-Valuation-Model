# COMAP ICM 2026 Problem D — WNBA Team Valuation Model

**Award:** Finalist Award  
**Competition:** COMAP Interdisciplinary Contest in Modeling 2026  
**Problem:** Problem D

This repository is a clean Python workflow reconstruction based on our COMAP ICM 2026 Problem D project. The project connects sports team performance, attendance demand, ticket revenue, profit, valuation, and leverage decisions into one modeling pipeline.

## Modeling Chain

```text
team performance -> attendance demand -> ticket revenue -> profit and cash flow -> team valuation -> leverage decision
```

## Main Components

- Elo rating and win probability model
- Injury shock simulation
- Attendance demand prediction
- Dynamic ticket pricing
- Revenue, profit, cash-flow, and valuation model
- Debt and leverage decision framework
- NO_MOVE / SIGN / TRADE strategy comparison
- Scenario analysis
- Monte Carlo simulation
- Sensitivity analysis and visualization

## How to Run

```bash
pip install -r requirements.txt
python -m src.run_all
```

## Reproducibility Note

The original competition-time code was not fully preserved. This repository rebuilds the modeling process in a transparent Python pipeline. The project is intended as a clean reconstruction of the workflow, not an official perfect reproduction of every original numeric output.

## Disclaimer

This project is for academic and educational purposes. It is not affiliated with COMAP, the WNBA, or any professional sports organization.
