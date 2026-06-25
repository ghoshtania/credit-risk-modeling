# Credit Risk Modeling — Lending Club

End-to-end credit risk modeling project on the Lending Club accepted-loans
dataset (2007–2018Q4, ~2.26M loans, 1.35M resolved after cleaning).

## Project Structure

- `data/` — data loading and preprocessing scripts
- `eda/` — exploratory data analysis and vintage analysis
- `features/` — WoE encoding, Information Value, feature engineering
- `pd_models/` — logistic regression scorecard, LightGBM, Cox survival model
- `lgd_ead/` — Loss Given Default and Exposure at Default modeling
- `stress_testing/` — macroeconomic stress scenarios
- `regulatory/` — IFRS 9 staging/ECL and Basel III IRB capital
- `portfolio/` — Gaussian copula Monte Carlo portfolio simulation
- `merton/` — Merton structural model applied to public company credit risk
- `ai_components/` — AI/LLM-related extensions
- `validation/` — full model validation suite and temporal backtest
- `report/` — bank-style model documentation report

## Models

| Model | Metric | Value |
|---|---|---|
| Logistic Regression Scorecard | AUC | 0.701 |
| LightGBM | AUC | 0.713 |
| LightGBM | Gini | 0.425 |
| LightGBM | KS | 0.309 |

## Key Findings

- Portfolio Expected Loss: $1.34B on $19.4B exposure (6.89% EL rate)
- Temporal backtest (2013–2016 train, 2018 test): AUC change +0.0013, PSI 0.025 — stable
- Basel III IRB capital: $1.27B (unexpected-loss buffer, additive to IFRS 9 provisions)
- Gaussian copula simulation: 99.9% VaR exceeds expected loss by >2.5x

## Known Limitations

This project documents several real data and methodological limitations
encountered during development, including a macro-sensitivity identification
problem, a dataset that does not extend past Q4 2018 (constraining the
temporal backtest), and a paused correlation-parameter calibration. See
`report/` for the full model documentation, which details each limitation
with its cause, impact, and resolution.
