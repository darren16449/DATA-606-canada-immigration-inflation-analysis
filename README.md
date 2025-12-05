# Immigration and Inflation in Canada (2010–2025)

This repository contains my capstone project analyzing whether **immigration meaningfully influences inflation** across Canadian provinces from **2010 to 2025**.

Using data from **Statistics Canada**, I build a provincial quarterly panel and test the relationship between immigration, housing supply, and inflation using both traditional econometric models and modern machine learning methods.

---

## Project Overview

**Research question:**  
> Does immigration significantly and consistently drive inflation across Canadian provinces, or are **interest rates and housing supply** the dominant forces?

**Key steps:**

1. **Data Collection & Integration**
   - CPI components (All-items, Shelter, Energy, etc.)
   - Population estimates
   - Immigration and Non-Permanent Residents (NPR)
   - Housing starts / supply
   - Interprovincial migration
   - Bank of Canada policy rate  
   All datasets are merged into a single provincial quarterly panel using `province + quarter_date`.

2. **EDA & Feature Engineering**
   - YoY growth rates for population, immigration, NPR, and housing starts
   - Per-capita metrics (immigrants per 10k, NPR per 10k, housing starts per 10k)
   - **Pressure ratio**: newcomers per new housing unit
   - Lagged features (2-quarter and 4-quarter lags) to capture delayed economic effects

3. **Modeling Frameworks**
   - Linear Regression (baseline)
   - Lasso & Ridge Regression (regularised linear models)
   - XGBoost Regressor (nonlinear tree-based model)
   - ARIMAX (time-series with exogenous variables)
   - VARMAX (multivariate system: All-items, immigration, housing, interest rates)

---

## Main Findings (Short Version)

- Immigration-related features often improve **training R²**, but **test R² remains negative** across almost all provinces and models.
- **Interest rates** show the strongest and most stable relationship with inflation (correlation ≈ 0.7), far stronger than migration variables.
- **Shelter inflation** shows only moderate correlation with immigration, suggesting migration adds some demand pressure but is **not a primary driver**.
- **Post-2020 NPR surges and policy shocks** introduce structural breaks that most models cannot generalize across.
- Overall, there is **no robust evidence** that immigration is a significant, stable predictor of inflation in Canada.

---

## Repository Structure

```text
.
├─ notebooks/
│  ├─ 01_data_loading_and_cleaning.ipynb
│  ├─ 02_eda_feature_engineering_modeling.ipynb
├─ data/
│  └─ README.md        # instructions for obtaining StatsCan data
├─ figs/               # (optional) exported plots for the report / slides
├─ README.md
└─ .gitignore

