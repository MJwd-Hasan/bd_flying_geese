# Bangladesh and the Flying Geese hypothesis — findings from the supplied WDI panel

## Data and scope
The supplied `wdi_data.csv` has **16,500 rows**: 10 economies × 25 indicators × 66 years (1960–2025), in long format. The notebooks analyse the **1976–2025 window** (`ANALYSIS_START = 1976`; 12,500 rows = 10 × 25 × 50), so results for the nine original economies remain comparable with earlier versions of this report. It was analysed locally; no World Bank API calls were used.

The latest update added **Hong Kong SAR** and the indicator **Medium and high-tech exports (% of manufactured exports)**. The high-technology export series has substantially shorter coverage than most other indicators (8–18 observations per economy); the medium and high-tech series has 35 (1990–2024) for every economy. Hong Kong's manufacturing, industry, services and agriculture value-added series start in 2000 (25 observations). Both notebooks were re-run end to end for the update; for the nine original economies every country-specific result reproduces exactly, and only multiple-testing-adjusted and panel-level statistics change because the number of tests and the panel grew.

## Main findings

### 1. Industrial structure
- Bangladesh's manufacturing value added rose from **9.28% of GDP in 1976 to 22.44% in 2025** (+13.16 percentage points). Spearman time-trend correlation: **0.871** (n=50; p<0.001).
- Bangladesh's industry value added rose from **14.45% of GDP in 1976 to 34.03% in 2025** (+19.58 points; rho=0.966, n=50, p<0.001).
- Korea's manufacturing share rose from 21.29% to 27.43% over 1976–2025 (rho=0.699, p<0.001).
- Vietnam's manufacturing share rose from 18.82% in 2005 to 24.53% in 2025 (rho=0.923, n=21, p<0.001). Its series starts much later, so endpoint comparisons are not like-for-like.
- China's manufacturing share in this extract is available only for 2004–2025 (22 observations), declining from 31.51% to 24.73%. Do not infer a 1976–2025 decline from this incomplete series.

**Interpretation:** evidence supports industrial deepening in Bangladesh, consistent with one broad feature of industrialisation, but this does not establish the Flying Geese mechanism.

### 2. Trade integration
- Bangladesh exports of goods and services rose from **4.75% of GDP (1976) to 11.12% (2025)** (+6.37 points; rho=0.761, n=50, p<0.001).
- Bangladesh trade (% GDP) rose from **22.38% to 27.95%** (+5.57 points; rho=0.736, n=50, p<0.001).
- Vietnam exports/GDP rose from 6.62% in 1986 to 98.24% in 2025; trade/GDP rose from 23.22% to 190.34%. This indicates much deeper measured external integration, although exports/GDP can exceed 100% and is not domestic value added.
- Korea exports/GDP rose from 25.04% to 45.76%; Malaysia from 51.82% to 70.97% (1976–2025).
- Bangladesh imports/GDP moved from 17.64% to 16.83% between 1976 and 2025 despite a positive overall monotonic rank association (rho=0.639); endpoints and monotonic trend can differ in a non-monotonic series.

**Interpretation:** Bangladesh's trade integration rose, but its latest ratio remains far below Vietnam, Korea and Malaysia. Aggregate WDI data do not show whether Bangladesh is taking over specific product lines from earlier industrialisers.

### 3. Investment
- Bangladesh gross fixed capital formation rose from **14.44% of GDP in 1980 to 28.54% in 2025** (+14.10 points; rho=0.964, n=46, p<0.001).
- Bangladesh FDI net inflows rose from **0.05% of GDP in 1976 to 0.39% in 2025** (rho=0.725, n=50, p<0.001), compared with Vietnam at 4.27% and Malaysia at 4.58% in 2025.
- Korea FDI/GDP rose from 0.27% to 0.84%; China’s series in this extract begins in 1979.
- FDI inflows are not equivalent to productive investment, technology transfer or spillovers. GFCF is a broader capital-accumulation measure.

**Interpretation:** GFCF supports a capital-accumulation story. FDI alone does not establish that foreign investment caused Bangladesh's industrial upgrading.

### 4. High-technology exports: serious coverage limitation
- Bangladesh has only **10 observations (2008–2018)**, from 0.44% to 0.54% of manufactured exports; trend correlation is not significant (rho=0.285, p=0.425).
- Vietnam's available observations rise from 8.84% in 2008 to 44.26% in 2023 (n=16; rho=0.971, p<0.001). Korea and Malaysia have longer coverage.
- The indicator is the high-tech share of manufactured exports, not domestic technology content or local value added. Bangladesh’s sparse coverage makes comparison weak.

### 5. Hong Kong SAR (added)
- Manufacturing value added fell from **4.59% of GDP in 2000 to 0.93% in 2024** (rho = −0.993, n = 25, p < 0.001); industry value added fell from 12.08% to 6.17% (rho = −0.845).
- Exports/GDP rose from **89.44% (1976) to 199.76% (2025)** (rho = 0.896); trade/GDP from 168.20% to 396.65%. Its net trade competitiveness ratio is within −0.017 to 0.063 (positive in 44 of 50 years).
- FDI net inflows rose from 1.98% of GDP (1976) to **28.31% (2025)**, peaking at 58.52%; gross fixed capital formation fell from 20.66% to 16.94% (rho = −0.638). Decade-average FDI is 21.9–35.6% of GDP since the 2000s, versus below 7% for every other plotted economy.
- High-technology exports rose from 21.62% (2007) to 75.57% (2024) (n = 18; rho = 0.686, p = 0.002). Medium and high-tech exports were 40.97% in 1990 and 38.75% in 2024 with no significant trend (rho = −0.182, p = 0.30).
- Against Bangladesh over 2000–2024, Hong Kong's manufacturing share changed by −3.66 points while Bangladesh's changed by +7.86.

**Interpretation:** Hong Kong is a contrast case (a trade and services centre with a manufacturing share below 1% of GDP), not a manufacturing follower. Its FDI inflows are an outlier, so Kojima figures use a symmetric-log FDI axis. Its high-tech and medium/high-tech shares describe export composition, not domestic production.

### 6. Medium and high-tech exports (added)
- Bangladesh: **2.41% (1990) to 2.71% (2024)**, range 1.77–5.93%, rho = −0.518 (p = 0.0015; BH-adjusted 0.0023). ADF rejects a unit root in levels (p = 0.006; KPSS p = 0.10).
- Vietnam 16.38% to 59.50% (rho = 0.980); China 28.40% to 63.35% (rho = 0.963); Korea 51.10% to 75.71% (rho = 0.718); Indonesia 12.21% to 33.11% (rho = 0.547); Philippines 38.52% to 77.66% (rho = 0.394, BH p = 0.026). Malaysia (53.25% to 66.77%), Singapore (62.18% to 75.60%) and Hong Kong show no significant trend; Japan declines slightly (83.09% to 80.89%, rho = −0.732).
- Lead/lag with Bangladesh: level correlations with China, Korea and Vietnam are negative at lags 0 and 5 (−0.39 to −0.58), but on annual changes all are insignificant (|rho| ≤ 0.19, p ≥ 0.29). Hong Kong at lag 10 is the only significant positive level correlation (0.64, BH p = 0.002), again insignificant in changes (0.10).
- Exploratory break scan: Bangladesh has a candidate break in 2009 (Bonferroni-adjusted p < 0.001; 20 pre- and 15 post-break years). Many other economies show candidate breaks too, so this is not evidence of a policy effect.
- Kojima quadrant (FDI vs this share; figure `images/fig_kojima_medhightech.png`, decade means over years with both observed): Bangladesh stays at FDI 0.1–1.1% of GDP and a share of 2.2–4.3% in every decade; Vietnam rises from 17.1% to 58.5% with FDI of 4.3–6.8%; China passes 50% in the 2000s; Malaysia and Japan are above 50% throughout (Japan with FDI below 0.8% of GDP); Hong Kong has the largest FDI but a share of 34–42%.

**Interpretation:** this is the most reliable evidence in the study on Bangladesh's export composition, because the sample is 35 years rather than 10. It shows no upgrading, but it does not identify why, and FDI is neither necessary (Japan) nor sufficient (Hong Kong) in the descriptive picture.

### 7. Effect of adding Hong Kong on earlier results
- Chow scan (export_import): Hong Kong has one nominal break (2018, p = 0.028), which fails the 2k-observations-per-regime rule (7 post-break years) and Bonferroni. The nine original economies' break lists are identical.
- Panel unit roots: Hong Kong alone moves the Fisher-ADF test for manufacturing share from p = 0.759 to 0.0004 (its ADF p = 2.6e-8), so the notebook's integration-order rule now labels the series I(0) although CIPS (−1.99) does not reject. The FDI → manufacturing and manufacturing → GDP-per-capita-growth Dumitrescu-Hurlin pairs are therefore no longer differenced. On first differences they are still insignificant (p = 0.176 and 0.954; nine economies 0.161 and 0.771).
- Dumitrescu-Hurlin on levels: FDI → manufacturing p = 0.006 (nine economies) to 0.016 (ten); not significant after Holm adjustment in either case.
- Two-way fixed effects (EDA notebook; 10 clusters, n = 359): the coefficient on lagged FDI in the manufacturing-share equation is −0.153 (p = 0.021, BH 0.042), versus −0.229 (p = 0.002, n = 334) with nine economies; the coefficient on lagged exports is 0.084 (BH 0.009). These are associations with very few clusters.
- Multiple-testing families grew (EDA trend and lead/lag tests: 79 to 98 trends; 69 to 117 lead/lag tests), so BH-adjusted p-values for existing rows changed even though raw statistics did not.

## Statistical work included in the notebook
1. Data integrity, missingness and coverage audit.
2. Time-series graphs for industrial structure, trade and investment.
3. Common-window endpoint comparisons with effective sample sizes.
4. Spearman trend tests with Benjamini–Hochberg false-discovery-rate adjustment.
5. Exploratory segmented-trend break scans with minimum regime sizes and Bonferroni adjustment across candidate dates within each series.
6. Two-way country/year fixed-effects associations using lagged predictors and country-clustered standard errors.
7. ADF and KPSS tests for levels and first differences.
8. A rough cross-country dependence diagnostic.
9. Lead/lag correlations with multiple-testing adjustment.

## Limitations
- Only ten economies: country-clustered standard errors can be unreliable.
- Hong Kong's value-added series start in 2000, so every test that uses them has a short sample for Hong Kong, and its FDI inflows are an extreme outlier.
- A single economy can change a panel classification (see section 7); report panel results with and without Hong Kong.
- Break scans are exploratory, not a pre-specified Chow test or validated multiple-break model.
- The CD statistic in the EDA notebook is explicitly approximate; do not cite it as a validated Pesaran CD test. In addition, that cell assigns `N,T = w.shape` on a year-by-economy matrix, so N is the number of years and T the number of economies, the reverse of the usual convention, and the statistic is understated (for exports/GDP it reports 1.78, versus 20.07 from the Pesaran CD test in `export_import.ipynb`). Use the `export_import.ipynb` statistic instead.
- ADF/KPSS are univariate diagnostics and are sensitive to trend/break specification.
- Correlations and fixed-effects associations are not causal effects.
- High-tech export coverage is sparse; multiple tests require adjusted p-values.

## Reading the supplementary export/import notebook

`export_import.ipynb` was extended in the update: it now includes Hong Kong SAR, the medium and high-tech export series (coverage, Spearman lead/lag, Pesaran CD, IPS/CIPS), a second Kojima figure, and four additional causality directions (18 in total, Holm-adjusted together). Its results are exploratory and should not be described as independently validated evidence. Aggregate exports and imports help describe external integration and trade-balance pressure; they cannot, on their own, identify product-level comparative-advantage shifts or prove that Bangladesh inherited production from an earlier industrialiser.

For the Flying Geese mechanism, a stronger test would use consistent HS-level bilateral trade data to calculate revealed comparative advantage (RCA), product entry/exit, export diversification and export-basket overlap across Bangladesh and the comparison economies. If interpreting time-series plots or ACF/PACF diagnostics in the panel notebook, each country's annual series must be analysed separately: concatenating countries would create artificial transitions between unrelated economies. ACF/PACF patterns are diagnostic clues about serial dependence, not proof of causality or a standalone basis for forecasting.

## Overall answer
**Bangladesh is partially consistent with industrial deepening and capital accumulation, but the current aggregate WDI evidence is insufficient to conclude that Bangladesh is following the Flying Geese sequence.**

The update (Hong Kong SAR and medium and high-tech exports) does not change this answer. The new 35-observation series shows Bangladesh's medium and high-tech export share at 2.41% in 1990 and 2.71% in 2024, against 59.50% for Vietnam and 63.35% for China in 2024, which strengthens the point that export upgrading is not visible. The strongest evidence is the long-run rise in Bangladesh's manufacturing and industry shares and GFCF/GDP. Exports/GDP and trade/GDP also rose, but remain below Vietnam's exceptionally high trade integration. The high-tech export series is too sparse to support a strong upgrading claim.

The central Flying Geese mechanism—successive shifts in product-level comparative advantage and relocation of production/export categories—cannot be tested using aggregate WDI ratios alone. The next decisive step is HS product-level trade analysis using [UN Comtrade](https://comtradeplus.un.org/) or [CEPII BACI](https://www.cepii.fr/CEPII/en/bdd_modele/presentation.asp?id=37): calculate revealed comparative advantage (RCA), product entry/exit, export diversification and overlap between Bangladesh's export basket and those of earlier geese. [UNIDO INDSTAT](https://stat.unido.org/) can add manufacturing subsector output and employment.

## References
- Akamatsu, K. (1962). A historical pattern of economic growth in developing countries. *The Developing Economies*, 1(S1), 3–25.
- Dowling, M. & Cheang, C.T. (2000). Shifting comparative advantage in Asia: new tests of the flying geese model. *Journal of Asian Economics*, 11(4), 443–463.
- World Bank (2018). *The Future of Manufacturing-Led Development in East Asia*. https://documents1.worldbank.org/curated/en/116191523612461208/pdf/125189-PUB-PUBLIC-docdate-4-11-18.pdf
- World Bank, World Development Indicators. https://datatopics.worldbank.org/world-development-indicators/
