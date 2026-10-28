# WDI notebook review: issues to resolve before interpreting results

This audit is a research-quality checklist for `WDI.ipynb` and `wdi_data.csv`. It is deliberately conservative: the CSV and notebook outputs must be inspected and rerun before any numeric claim is treated as verified.

## Priority findings

### 1. Keep the raw WDI extract immutable
- Load `wdi_data.csv` as the source extract and create a separate analysis dataframe.
- Record its shape, column names, country coverage, indicator coverage, year range, duplicate keys, and missingness before filtering.
- Preserve indicator codes and source metadata where present. Do not rely only on shortened indicator labels.
- Validate the expected panel key (country, year, indicator) before pivoting; report duplicate keys rather than silently dropping them.

### 2. Validate the panel before plotting or testing
- Parse year values explicitly and sort by country/year.
- Check for duplicate country-year-indicator rows and inconsistent country names (for example, “Korea, Rep.”).
- Distinguish genuine zero values from missing observations. Never replace missing WDI values with zero.
- Report the available years separately for each indicator and country. A common complete-case sample can be much shorter than the raw dataset.
- Make transformations explicit and reproducible; do not interpolate or forward-fill by default.

### 3. Revisit the time-series methods
- **Annual data do not have within-year seasonality.** Seasonal decomposition is not appropriate for annual WDI observations. Use a trend/cycle description only if justified, or analyse annual growth directly.
- **Chow tests require a pre-specified candidate break date** in the standard form. Testing many candidate years and reporting all rejections creates a multiple-testing problem. State the break date and hypothesis, and use a documented multiple-break procedure if the break date is unknown.
- **Zivot–Andrews is a unit-root test with one endogenous break**, not a general-purpose detector of every structural change. Report test statistic, selected break year, lag choice, deterministic specification, and critical-value comparison. Results are sensitive to short samples and missing years.
- **ADF and KPSS are complementary, not interchangeable.** State their null hypotheses and deterministic terms. Avoid treating one test alone as proof of stationarity.
- **Granger predictability is not structural causation.** Toda–Yamamoto and Dumitrescu–Hurlin tests need defensible lag selection, adequate time dimension, stable variable definitions, and diagnostics. Interpret results as predictive precedence, not proof that a policy or variable “caused” growth.
- Do not run time-series tests on series with unexamined gaps or silently unequal time spans.

### 4. Correct indicator interpretation
- The Net Trade Competitiveness Ratio can be written as
  `(exports_pct_gdp - imports_pct_gdp) / (exports_pct_gdp + imports_pct_gdp)`
  only if the numerator and denominator use the same trade concepts and units. If using total trade (% of GDP) as the denominator, document that identity and guard against a zero denominator. It is a normalized trade-balance measure, not a direct measure of productivity or endogenous growth.
- Gross capital formation and gross fixed capital formation are different indicators. Do not label one as the other.
- “Female population share” is not female labour-force participation, female employment, or women’s contribution to manufacturing. Use labour-market indicators for claims about women’s employment.
- High-technology exports (% of manufactured exports) is a composition measure, not the absolute scale or domestic value added of high-tech production. Pair it with other evidence and state its limitations.
- Manufacturing value added (% of GDP) can decline while manufacturing output grows if other sectors grow faster. Analyse levels, growth rates, and shares separately where data permit.
- FDI inflows (% of GDP) can be volatile and affected by denominator movements. Avoid interpreting correlation as a direct investment effect. Hong Kong SAR's inflows reach 58.5% of GDP and are an extreme outlier; check results with and without it.
- Medium and high-tech exports (% of manufactured exports) is a composition measure like the high-technology indicator, but a broader category. It has 35 annual observations (1990–2024) per economy, so it supports longer samples than the high-technology series (8–18 observations).
- Hong Kong SAR's manufacturing, industry, services and agriculture value-added series start in 2000 (25 observations). Panel tests that combine p-values across economies (for example Fisher-ADF) can be dominated by one short, steeply trending series; report them with and without Hong Kong.

### 5. Make comparisons defensible
- Use consistent definitions and common observation windows for Bangladesh, Viet Nam, and the selected Flying Geese economies.
- Plot each indicator with units and source indicator code. Avoid comparing indicators that use different denominators.
- Use levels for scale questions, growth rates for change, and GDP-normalized shares for relative importance. Explain why each is appropriate.
- Use lagged correlations as exploratory descriptions only. Test several lags with multiple-testing awareness, and avoid interpreting correlation as evidence of a “baton pass.”
- Consider whether country groupings and historical periods are theoretically justified rather than selected after viewing the charts.

### 6. Improve notebook structure and reproducibility
Recommended order for `WDI.ipynb`:
1. Research questions, hypotheses, country list, period, and indicator dictionary.
2. Imports and display settings.
3. Load the local CSV (with a helpful missing-file error).
4. Data audit: dimensions, dtypes, keys, coverage, missingness, duplicates.
5. Cleaning and a transparent long-to-wide transformation.
6. Indicator definitions and derived measures with unit checks.
7. Descriptive plots with consistent colours/labels and source codes.
8. Country comparisons using common time windows.
9. Statistical tests with assumptions, lag selection, diagnostics, and caveats.
10. Results table separating descriptive findings from inferential evidence.
11. Limitations and a reproducibility checklist.

Prefer small reusable functions for repeated plots and diagnostics. Each chart should have a title, units, readable legend, source indicator code, and explicit date range. Avoid suppressing warnings globally; fix or explain them instead.

## Minimum automated checks

Before analysis, verify:
- [ ] CSV is read successfully and its dimensions are printed.
- [ ] Expected country, year, indicator, and value fields exist (or are mapped explicitly).
- [ ] Year and value columns are correctly typed.
- [ ] No unexplained duplicate panel keys remain.
- [ ] Missingness and per-series coverage are reported.
- [ ] Derived ratios have denominator and unit checks.
- [ ] All plots use consistent units and clearly labelled periods.
- [ ] Tests report hypotheses, sample size, lag/specification, statistic, p-value, and caveat.
- [ ] Notebook executes from a clean kernel with the repository's relative file paths.

## Update note: extended extract

`wdi_data.csv` now contains Hong Kong SAR and the indicator Medium and high-tech exports, and starts in 1960. `export_import.ipynb` and `flying_geese_panel_eda.ipynb` were re-run with `ANALYSIS_START = 1976` so that results for the nine original economies remain identical to earlier versions. `WDI.ipynb` was not updated or re-run for this extract.

## Research claims that need re-validation

The companion draft contains strong claims about COVID-era breaks, cross-country correlations, FDI and manufacturing, high-tech exports, female employment, and causality. Treat those as provisional until the notebook is rerun end-to-end and the exact input series, sample windows, test specifications, and outputs are reproducible. In particular, a p-value alone does not establish economic importance or identify a policy mechanism.

## References and source discipline

The primary data source is the World Bank's [World Development Indicators](https://databank.worldbank.org/source/world-development-indicators). Cite each indicator by its official code and retrieval date in the final paper. Retain the project's existing literature references, but connect each theoretical claim to the specific source that supports it. Do not cite the WDI database as evidence for a causal mechanism; it is a data source, not a causal identification strategy.
