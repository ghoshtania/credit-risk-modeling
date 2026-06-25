# Credit Risk Modeling — Lending Club

End-to-end credit risk modeling project on the Lending Club accepted-loans
dataset (2007–2018Q4, ~2.26M loans, 1.35M resolved after cleaning).

## Project Structure

| Folder | Contents |
|---|---|
| `eda/` | Data loading, leakage removal, missing values, EDA, vintage analysis |
| `features/` | WoE encoding and Information Value feature engineering |
| `pd_models/` | Logistic scorecard, LightGBM, Kaplan-Meier, Cox, transition matrix |
| `lgd_ead/` | Loss Given Default and Exposure at Default modeling |
| `stress_testing/` | FRED macro integration, time-varying Cox, stress scenarios |
| `regulatory/` | IFRS 9 staging/ECL and Basel III IRB capital |
| `portfolio/` | Gaussian copula calibration and Monte Carlo simulation |
| `merton/` | Merton structural model and Distance-to-Default time series |
| `validation/` | Full validation suite and out-of-time temporal backtest |
| `report/` | Bank-style model documentation report |
| `credit_risk_modeling_full.ipynb` | The complete project in a single notebook (reference copy) |

## Models

| Model | AUC | Gini | KS |
|---|---|---|---|
| Logistic Regression Scorecard | 0.701 | 0.402 | 0.291 |
| LightGBM | 0.713 | 0.425 | 0.309 |

## Key Findings

- Portfolio Expected Loss: $1.34B on $19.4B exposure (6.89% EL rate)
- Temporal backtest (2013–2016 train, 2018 test): AUC change +0.0013, PSI 0.025 — stable
- Basel III IRB capital: $1.27B (unexpected-loss buffer, additive to IFRS 9 provisions)
- Gaussian copula simulation: 99.9% VaR exceeds expected loss by >2.5x
- Merton model on 19 public companies: ~30x gap in mean implied PD between investment-grade and high-yield groups

## Known Limitations

This project documents several real data and methodological limitations
encountered during development — most notably that the dataset does not
extend past Q4 2018 (constraining the temporal backtest's ability to test
against COVID-era stress), and an identification problem that prevented
reliably estimating macro sensitivity directly from the data. See
`report/` and the relevant notebooks for full detail on each finding,
including its cause, impact, and resolution.
