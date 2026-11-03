# U.S. Cost of Living Analysis | CPI, Wages & Gas Prices

**Data analysis portfolio project** | Python (pandas) · Time-series analysis · Power BI (dashboard work in progress)

## The business question

**Have hourly earnings kept pace with the changing cost of living in the United States?**

This project brings together three public U.S. economic series to examine inflation, wages, and fuel prices over time. Its purpose is to distinguish **nominal wage growth** from **purchasing power**, examine fuel-price volatility, and communicate what the data can and cannot establish.

> **Status:** The data-cleaning notebook and analysis-ready CSVs are published. The Power BI report, screenshots, and final evidence-based findings are **not yet included in this repository**. They will be added after validation. This README intentionally does not present unfinished work as complete.

## Questions explored

1. How has the Consumer Price Index changed year over year?
2. How have average hourly earnings changed over the same periods?
3. How do nominal wage growth and CPI inflation compare?
4. How have regular gasoline prices moved relative to general inflation?
5. Which patterns reflect short-term volatility, and which persist across longer windows?

## Data sources

Public time series downloaded from [FRED](https://fred.stlouisfed.org/):

| Series | FRED identifier | Frequency in source | Use |
|---|---|---|---|
| Consumer Price Index for All Urban Consumers, All Items | [CPIAUCSL](https://fred.stlouisfed.org/series/CPIAUCSL) | Monthly | General consumer price level |
| U.S. Regular All Formulations Retail Gasoline Prices | [GASREGW](https://fred.stlouisfed.org/series/GASREGW) | Weekly | Retail fuel price |
| Average Hourly Earnings, Production and Nonsupervisory Employees, Total Private | [AHETPI](https://fred.stlouisfed.org/series/AHETPI) | Monthly | A wage indicator, **not** an all-worker income measure |

The repository contains local extracts; check the original series pages for units, adjustments, updates, and revisions.

## What the published Python notebook does

The [data-cleaning notebook](notebooks/data_cleaning.ipynb):

1. Loads the three datasets from `data/raw/`.
2. Standardizes field names and converts dates and numeric columns.
3. Resamples weekly gas prices to a monthly **arithmetic mean**.
4. Left-joins monthly CPI, gasoline, and wage observations by date.
5. Creates an analysis subset with nonmissing values in all three series.
6. Calculates 12-observation percentage changes and a CPI-adjusted wage index.
7. Exports the merged and analysis-ready datasets to CSV.

**Calculation notes**

- `CPI YoY % = (CPI_t / CPI_(t-12) - 1) × 100`
- `Wage YoY % = (Wage_t / Wage_(t-12) - 1) × 100`
- `Gas YoY % = (Gas_t / Gas_(t-12) - 1) × 100`
- `Real wage index` is proportional to `hourly_wage / CPI`, rebased to 100 in the first valid analysis observation.

The exact real wage growth rate is `((1 + nominal_wage_growth) / (1 + CPI_inflation) - 1) × 100`. Subtracting CPI inflation from wage growth is only an approximation.

**Important validation item:** The current notebook calculates 12-row changes *after* filtering for complete observations. These are true 12-month changes only when the filtered series contains uninterrupted monthly rows. Before presenting results as YoY, validate monthly continuity or use a calendar-based 12-month join. Also verify the date convention used when resampling weekly gasoline observations.

## Repository layout

```text
.
├── README.md
├── data/
│   ├── raw/
│   │   ├── cpi.csv
│   │   ├── gas_prices.csv
│   │   └── hourly_wages.csv
│   ├── cleaned/
│   │   ├── cost_of_living_monthly_analysis.csv
│   │   └── cost_of_living_monthly_fully.csv
│   └── README.md
├── notebooks/
│   ├── data_cleaning.ipynb
│   └── README.md
└── exports/
    └── README.md
```

**Reproducibility:** The notebook uses relative paths assuming it is run from the `notebooks/` working directory. Its full-dataset export path currently spells the filename `cost_of_living_monthly_full.csv`, whereas the committed file is `cost_of_living_monthly_fully.csv`. Resolve this naming mismatch before claiming exact reproduction of the committed outputs.

## How to review

- [Inspect the Python notebook](notebooks/data_cleaning.ipynb)
- [Inspect the analysis-ready dataset](data/cleaned/cost_of_living_monthly_analysis.csv)
- [Inspect the source extracts](data/raw/)
- [Review the other economic dashboard](https://github.com/JavierP20/U.S.-Economic-Dashboard)

To execute the notebook locally, install Python, Jupyter, and pandas; start Jupyter with the working directory set to `notebooks/`. Rerun the cells in order after checking file paths and dependencies.

## Interpretation and limitations

- CPI measures a representative consumer price basket; it is not every household's personal cost of living.
- AHETPI covers production and nonsupervisory employees in the private sector, not all U.S. workers.
- A single national CPI series does not establish local or household-specific affordability.
- Nominal wages and gasoline prices can move together without one causing the other.
- Monthly averaging smooths weekly fuel-price swings and may hide shorter spikes.
- A purchasing-power comparison should align units, observation dates, seasonal adjustment, and population coverage.
- Public macroeconomic time series may be revised.

## Next milestones

- [ ] Validate complete monthly coverage and the 12-month change calculations.
- [ ] Resolve the cleaned full-dataset filename discrepancy.
- [ ] Publish the final Power BI file and legible page screenshots.
- [ ] Document DAX measures and the dashboard data model.
- [ ] Add **verified numeric findings**, time frames, and actionable interpretations.
- [ ] Include data-refresh date and a reproducible environment/requirements file.

---

**Portfolio:** [JavierP20](https://github.com/JavierP20) · [U.S. Economic Dashboard](https://github.com/JavierP20/U.S.-Economic-Dashboard)
