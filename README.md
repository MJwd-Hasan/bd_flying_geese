# The Flying Geese: Can Bangladesh become a follower of the leading geese?

A comparative analysis of Bangladesh and Vietnam, alongside seven other Asian economies, using World Bank World Development Indicators (WDI) data.

**Paper:** [PDF](bangladesh_flying_geese.pdf) / [Markdown](bangladesh_flying_geese.md)  
**Author:** Mohammad Jawad Hasan, supervised by Prof. Dr. Israt Rayhan

## Repository layout

| Path | Purpose |
|---|---|
| `WDI.ipynb` | WDI-based analysis |
| `wdi_data.csv` | WDI extract for nine economies and 24 indicators; long-format values may use `..` for missing observations |
| `UNCTAD.ipynb`, `UNCTAD_data.csv`, `UNCTAD_series.csv` | Supplementary UNCTAD analysis and data |
| `export_import.ipynb` | Trade-focused analysis |
| `images/` | Figures used by the analysis and paper |
| `docs/` | Research and robustness notes |
| `Papers/` | Collected references |
| `WDI_analysis_audit.md` | Data validation, statistical-method, interpretation, and reproducibility audit |
| `requirements.txt` | Python dependencies |

Economies: Bangladesh, China, Indonesia, Japan, Korea (Rep.), Malaysia, Philippines, Singapore, and Viet Nam.

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
- Female population share is not a measure of female employment or labour-force participation.
- Correlation and lead–lag similarity do not prove that production was transferred from one country to another.

See [WDI analysis audit](WDI_analysis_audit.md) and the existing robustness notes before relying on headline results.

## Data source

The primary source is the World Bank's [World Development Indicators](https://databank.worldbank.org/source/world-development-indicators). In the paper, cite official indicator codes, observation periods, and retrieval dates. WDI provides data; theoretical mechanisms and causal claims require support from the literature and a defensible identification strategy.
