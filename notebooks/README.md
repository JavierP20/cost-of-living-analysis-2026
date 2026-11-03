# Data Cleaning Notebook

The repository includes [data_cleaning.ipynb](data_cleaning.ipynb), a pandas notebook used to prepare CPI, gasoline prices, and hourly wage data for economic analysis.

## Implemented steps

1. Read the three source CSVs from `../data/raw/`.
2. Rename fields and parse dates/numeric values.
3. Average weekly gasoline prices into monthly observations.
4. Join CPI, monthly gasoline prices, and average hourly wages on date.
5. Produce an analysis subset with complete observations.
6. Calculate 12-observation changes and a CPI-adjusted hourly wage index.
7. Export analysis CSVs to `../data/cleaned/`.

## Running it

Install `pandas` and Jupyter, start Jupyter **from this folder**, and run notebook cells in order. The notebook uses relative paths based on `Path("..")`; running it from another working directory may fail.

## Known issues to validate

- The notebook exports the full merged dataset as `cost_of_living_monthly_full.csv`, while the currently committed cleaned file is `cost_of_living_monthly_fully.csv`. Standardize the name and regenerate the file.
- The 12-row percentage changes are computed after filtering incomplete observations. Confirm uninterrupted monthly frequency before describing the results as year-over-year rates.
- Check gasoline resampling date conventions and source units/seasonal adjustments.
- Add reproducible dependency versions, data validation checks, and a clear execution date before claiming fully repeatable results.

The notebook is **implemented**, not merely planned; the dashboard and final quantitative conclusions are tracked separately in the [main README](../README.md).
