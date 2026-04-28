# Interim Report

Date: 2026-04-26
Project: Climate Challenge Week 0
Client / Business Context: Climate analytics stakeholder seeking evidence to compare weather patterns across the five assigned countries and use the results for planning, prioritization, and reporting.
Project Scope: Ethiopia plus the four other countries specified in the assignment brief.

## 1) Task 1 Summary (Git and Environment Setup)

### Git setup and workflow
- Created and worked on feature branch: `eda-ethiopia`.
- Used a branch-based workflow for notebook and analysis updates.
- Pushed branch updates to remote (`origin/eda-ethiopia`) for collaboration and review.

### Python environment setup
- Activated the project virtual environment (`venv`) and used it as the notebook kernel.
- Installed the missing dependency (`scipy`) required for Z-score outlier detection.
- Verified the core analysis libraries are available and import correctly:
  - pandas
  - numpy
  - matplotlib
  - seaborn
  - scipy

### CI setup status
- CI workflow exists under `.github/workflows/ci.yml`.
- Current trigger is push to `main` only; pushes to `eda-ethiopia` do not automatically run CI unless merged or the workflow trigger is expanded.

## 2) Task 2 Summary (Data Profiling and Cleaning for Ethiopia)

### What was done for the Ethiopia slice
- Loaded the Ethiopia dataset with `pd.read_csv("ethiopia.csv")` and added `Country = "Ethiopia"`.
- Built a proper `date` column from `YEAR` + `DOY` and extracted `Month` for seasonal analysis.
- Replaced NASA sentinel values (`-999`) with `np.nan` before profiling.
- Checked for duplicate rows and duplicate `YEAR`/`DOY` keys, then removed duplicates.
- Generated summary statistics and missing-value counts/percentages for the numeric variables.
- Flagged missingness above 5% for review; the current Ethiopia run did not surface problematic missingness.
- Computed Z-scores for the required weather variables and counted potential outliers.
- Kept extreme climate values by default unless they are physically implausible.
- Dropped rows with more than 30% missing values and forward-filled the core weather variables.
- Exported the cleaned Ethiopia file to `data/ethiopia_clean.csv`.

### EDA outputs already drafted for Ethiopia
- Monthly average `T2M` with warmest/coolest month annotations.
- Monthly total `PRECTOTCORR` with peak rainy-month annotations.
- Correlation heatmap for the numeric variables.
- Scatter plots for `T2M vs RH2M` and `T2M_RANGE vs WS2M`.
- Rainfall distribution view with a skewness check and log-transformed histogram.
- Bubble chart using `T2M` and `RH2M`, with bubble size mapped to `PRECTOTCORR`.

## 3) Broader Multi-Country Scope

The final submission is not just an Ethiopia EDA. The business question is comparative: identify how climate patterns differ across the five assigned countries, then use those differences to support cross-country interpretation and decision-making.

That means the remaining work should standardize the same profiling, cleaning, and EDA process across all five countries so the outputs are directly comparable. Ethiopia is the first completed country slice; the next step is to repeat the same logic for the other four assigned countries and then combine the results into a consistent cross-country view.

## 4) Roadmap For Task 3

Task 3 should focus on turning the single-country workflow into a reusable multi-country pipeline:

1. Apply the same ingestion, date construction, sentinel replacement, duplicate checks, and missing-value handling to each of the five country datasets.
2. Standardize column names, data types, and derived fields so the country outputs share a common schema.
3. Save one cleaned file per country and then create a combined clean dataset for cross-country comparison.
4. Compare each country on the same set of indicators: temperature level, temperature range, rainfall seasonality, humidity, wind behavior, missingness, and outlier profile.
5. Add a concise written interpretation for each country and a summary comparison across the full five-country set.

## 5) Bonus Task Plan

The bonus work should build on the cleaned multi-country dataset and move from EDA to synthesis:

1. Produce a comparative summary table across all five countries with the key climate indicators and data-quality notes.
2. Create side-by-side visualizations so the countries can be compared on the same scales.
3. Highlight the strongest similarities, the clearest differences, and any country-specific anomalies that matter to the business question.
4. Turn the comparison into a short recommendation section that explains which countries look most similar, which are climate outliers, and what that means for planning or prioritization.

## 6) Governance And Submission Hygiene

- Keep generated CSV outputs out of version control (`data/` and `*.csv` ignored).
- Ensure the notebook contains written interpretations for each major output section.
- Re-run the notebook end to end before submission to confirm reproducibility.
- After Task 3 is complete, update the report so it reflects the full five-country comparison rather than only the Ethiopia slice.
