# Out-of-Sample Forecasting of Exchange Rate Expectations

Expanding-window evaluation of four forecasting models for exchange-rate expectations at horizons h=3 and h=4:

- **Model 0** — naive random-walk benchmark
- **Model 1** — linear two-way fixed-effects panel regression
- **Model 2** — Elastic Net
- **Model 3** — XGBoost

Includes RMSE/MAE (overall and AE/EMDE subgroup) accuracy tables, Diebold–Mariano tests with the Harvey–Leybourne–Newbold small-sample correction, a Model Confidence Set (Hansen, Lunde & Nason 2011) via block bootstrap, and a SHAP importance stability diagnostic (Kendall's τ across rounds).

## Data

`oos_forecasting.ipynb` currently generates a **synthetic panel** (Section 1) with the exact column names, country count, and year range the underlying model expects, so the notebook runs end-to-end out of the box. To use real data, replace the Section 1 cell with a loader that produces a DataFrame with columns:

```
country, year, MP_Shock_Diff, GDP_Forecast_Diff, GDP_Forecast_Error,
CPI_Forecast_Diff, CPI_Forecast_Error, WUI_Shock_Diff, Debt_to_GDP, CBI,
y_h3, y_h4
```

Everything downstream is unaffected by the change.

## Setup

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook oos_forecasting.ipynb
```

## Structure

```
.
├── oos_forecasting.ipynb   # main notebook (Sections 1-9)
├── requirements.txt
└── README.md
```
