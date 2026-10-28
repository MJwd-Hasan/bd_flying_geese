# The Flying Geese: Can Bangladesh become a follower of the leading geese?

A comparative analysis of Bangladesh and Vietnam, alongside eight other Asian economies (including Hong Kong SAR), using World Bank World Development Indicators (WDI) data.

**Paper:** [PDF](bangladesh_flying_geese.pdf) / [Markdown](bangladesh_flying_geese.md)  
**Author:** Mohammad Jawad Hasan, supervised by Prof. Dr. Israt Rayhan

## Repository layout

| Path | Purpose |
|---|---|
| `WDI.ipynb` | Earlier WDI-based analysis. Not updated or re-run for the ten-economy extract; it reads `WDI_data.csv` (capitalised), which does not match the file name on case-sensitive systems |
| `wdi_data.csv` | WDI extract for ten economies and 25 indicators, 1960–2025; long-format values may use `..` for missing observations. The notebooks analyse 1976–2025 (`ANALYSIS_START = 1976`) |
| `UNCTAD.ipynb`, `UNCTAD_data.csv`, `UNCTAD_series.csv` | Supplementary UNCTAD analysis and data |
| `export_import.ipynb` | Trade-focused analysis: Chow and Zivot-Andrews breaks, Spearman lead/lag, Kojima FDI-upgrading quadrants (high-tech and medium/high-tech exports), panel unit-root, cross-section dependence and causality tests |
| `flying_geese_panel_eda.ipynb` | Panel descriptive analysis: coverage, trends, break scans, fixed effects, stationarity and lead/lag |
| `flying_geese_findings.md` | Summary of findings from the panel notebook, including Hong Kong and medium/high-tech exports |
| `images/` | Figures used by the analysis and paper |
| `docs/` | Research and robustness notes |
| `Papers/` | Collected references |
| `WDI_analysis_audit.md` | Data validation, statistical-method, interpretation, and reproducibility audit |
| `requirements.txt` | Python dependencies |

Economies: Bangladesh, China, Hong Kong SAR, Indonesia, Japan, Korea (Rep.), Malaysia, Philippines, Singapore, and Viet Nam.

### Latest update: Hong Kong SAR and medium and high-tech exports

The dataset gained Hong Kong SAR and the indicator *Medium and high-tech exports (% of manufactured exports)* (`TX.MNF.TECH.ZS.UN`, 1990–2024 for every economy). Both notebooks were extended and re-run; results for the nine original economies reproduce exactly, while panel-level statistics now include Hong Kong. New or changed figures: `fig_kojima_medhightech.png` (new), and `fig_kojima_hightech`, `fig_kojima_gcf`, `fig_spearman_heatmap`, `fig_ntc`, `fig_trade_balance` and `fig_causality_network` (now include Hong Kong and, where relevant, the new variable; the Kojima figures use a symmetric-log FDI axis because Hong Kong's FDI inflows are an outlier). See `docs/robustness_notes.md` for what changed and why, in particular that Hong Kong alone changes the panel unit-root classification of manufacturing value added.

## Reproduce

Run notebooks from the repository root so relative paths resolve correctly. Install dependencies first:

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
```

Then execute the notebook you want to reproduce, for example:

```bash
jupyter nbconvert --to notebook --execute --inplace WDI.ipynb
```

Execution may take time, and all results should be checked against the current input data and notebook outputs before being cited.

## Research question and workflow

The project investigates whether the development paths of Bangladesh and Vietnam, compared with selected East Asian economies, are consistent with the Flying Geese Paradigm and its proposed movement from importing to domestic production and exporting.

Recommended workflow:

1. Audit country and indicator coverage, data types, missing values, duplicate keys, and year ranges.
2. Verify indicator codes and derived-variable formulas.
3. Compare trends over common observation windows and clearly label units.
4. Check assumptions and sample length before time-series tests.
5. Report statistical results with specifications, sample sizes, and limitations.
6. Separate descriptive patterns and predictive relationships from causal claims.

## Important interpretation cautions

- Annual WDI observations do not contain within-year seasonality, so seasonal decomposition is not appropriate for annual series.
- Chow tests, endogenous-break tests, and unit-root tests answer different questions; detected breaks are not explanations by themselves.
- Granger-type tests assess predictive precedence under a specified model. They do not independently establish structural causality or policy effectiveness.
- Manufacturing value added (% of GDP), high-technology exports (% of manufactured exports), and FDI inflows (% of GDP) measure different concepts and have different limitations.
- Medium and high-tech exports (% of manufactured exports) is a broader category than high-tech exports and, like it, describes export composition, not domestic value added. Hong Kong's FDI inflows (up to 58.5% of GDP) are an outlier and should not be read as manufacturing investment.
- Female population share is not a measure of female employment or labour-force participation.
- Correlation and lead–lag similarity do not prove that production was transferred from one country to another.

See [WDI analysis audit](WDI_analysis_audit.md) and the existing robustness notes before relying on headline results.

## Data source

The primary source is the World Bank's [World Development Indicators](https://databank.worldbank.org/source/world-development-indicators). In the paper, cite official indicator codes, observation periods, and retrieval dates. WDI provides data; theoretical mechanisms and causal claims require support from the literature and a defensible identification strategy.
