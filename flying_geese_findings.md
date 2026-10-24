# Bangladesh and the Flying Geese hypothesis — findings from the supplied WDI panel

## Data and scope
The supplied `WDI_data.csv` has **10,800 rows**: 9 economies × 24 indicators × 50 years (1976–2025), in long format. It was analysed locally; no World Bank API calls were used. The high-technology export series has substantially shorter coverage than most other indicators.

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
- Only nine countries: country-clustered standard errors can be unreliable.
- Break scans are exploratory, not a pre-specified Chow test or validated multiple-break model.
- The CD statistic is explicitly approximate; do not cite it as a validated Pesaran CD test.
- ADF/KPSS are univariate diagnostics and are sensitive to trend/break specification.
- Correlations and fixed-effects associations are not causal effects.
- High-tech export coverage is sparse; multiple tests require adjusted p-values.

## Overall answer
**Bangladesh is partially consistent with industrial deepening and capital accumulation, but the current aggregate WDI evidence is insufficient to conclude that Bangladesh is following the Flying Geese sequence.**

The strongest evidence is the long-run rise in Bangladesh's manufacturing and industry shares and GFCF/GDP. Exports/GDP and trade/GDP also rose, but remain below Vietnam's exceptionally high trade integration. The high-tech export series is too sparse to support a strong upgrading claim.

The central Flying Geese mechanism—successive shifts in product-level comparative advantage and relocation of production/export categories—cannot be tested using aggregate WDI ratios alone. The next decisive step is HS product-level trade analysis using [UN Comtrade](https://comtradeplus.un.org/) or [CEPII BACI](https://www.cepii.fr/CEPII/en/bdd_modele/presentation.asp?id=37): calculate revealed comparative advantage (RCA), product entry/exit, export diversification and overlap between Bangladesh's export basket and those of earlier geese. [UNIDO INDSTAT](https://stat.unido.org/) can add manufacturing subsector output and employment.

## References
- Akamatsu, K. (1962). A historical pattern of economic growth in developing countries. *The Developing Economies*, 1(S1), 3–25.
- Dowling, M. & Cheang, C.T. (2000). Shifting comparative advantage in Asia: new tests of the flying geese model. *Journal of Asian Economics*, 11(4), 443–463.
- World Bank (2018). *The Future of Manufacturing-Led Development in East Asia*. https://documents1.worldbank.org/curated/en/116191523612461208/pdf/125189-PUB-PUBLIC-docdate-4-11-18.pdf
- World Bank, World Development Indicators. https://datatopics.worldbank.org/world-development-indicators/
