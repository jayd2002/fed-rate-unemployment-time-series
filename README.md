# Monetary Policy and U.S. Unemployment: A Distributed Lag Analysis

A time series analysis investigating how changes in the federal funds rate affect the U.S. unemployment rate. Uses a finite distributed lag model on 26 years of monthly FRED data (Jan 2000 – Jan 2026) to estimate the timing and magnitude of monetary policy transmission to the labor market.

## Key Findings

The overall model was statistically significant (F = 7.94, p < 0.001), explaining ~24.6% of the variance in monthly unemployment changes. However, individual lag coefficients were largely insignificant after Newey-West correction, with only the 7-month lag showing marginal significance (p = 0.09). The results suggest the relationship between rate changes and unemployment is more complex than a simple delayed effect — consistent with broader macroeconomic literature on the difficulty of isolating monetary policy transmission.

## Methodology

**Data:** Monthly observations from the Federal Reserve Economic Data (FRED) database pulled via R's `quantmod` package — effective federal funds rate (FEDFUNDS), civilian unemployment rate (UNRATE), and CPI (CPIAUCSL).

**Preprocessing:** Constructed the inflation rate as the log-difference of CPI. Assessed stationarity using ACF/PACF plots and Augmented Dickey-Fuller tests, then first-differenced the unemployment and federal funds rate series.

**Model:** Finite distributed lag (FDL) regression with 12 monthly lags of the differenced federal funds rate and contemporaneous inflation as a control. Lag length selected by evaluating AIC/BIC across K = 0–18.

**Diagnostics:** Durbin-Watson and Breusch-Godfrey tests for serial correlation, Breusch-Pagan test for heteroskedasticity (confirmed, p < 0.001), with Newey-West HAC standard errors applied for robust inference.

## Files

| File | Description |
|------|-------------|
| `Project_1_Code.Rmd` | R Markdown notebook with full analysis |
| `Project_1_Report.pdf` | Written report with methodology, results, and discussion |

## Tech Stack

R · quantmod · tidyverse · tseries · forecast · dynlm · lmtest · sandwich
