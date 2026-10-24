# Empirical status: Bangladesh and the Flying Geese hypothesis

## Bottom line
The current evidence is **partially consistent with industrial deepening and greater trade integration, but insufficient to establish that Bangladesh is following the Flying Geese sequence**. A stronger conclusion requires evidence of changing comparative advantage and production/export composition, not only a rising manufacturing share or exports/GDP.

## Evidence visible in the existing WDI notebook outputs
- The panel covers 9 economies and 1976–2025, with 24 indicators and 1,084 missing values among 10,800 country-indicator-year cells. Coverage is uneven.
- High-tech export observations are sparse: Bangladesh 10; China 18; Indonesia 15; Japan 18; Korea 18; Malaysia 16; Philippines 8; Singapore 18; Viet Nam 16. This indicator cannot carry a strong conclusion alone.
- Median GDP-per-capita growth in the cached sample is higher in China (7.63%), Korea (5.27%) and Viet Nam (5.24%) than Bangladesh (3.28%). This is context, not an FG test.
- Bangladesh's Chow scan flagged 2019 only under the unadjusted rule (F=2.698, p=0.0299); it does not survive the notebook's stricter regime-size/multiple-testing criteria. Do not call it a confirmed break.
- Bangladesh manufacturing-share Zivot–Andrews test rejects a unit root only under the intercept-break specification (p=0.0289; estimated break 2015). Trend and intercept-plus-trend specifications do not reject (p=0.114 and 0.151). The date is specification-sensitive.
- Strong level correlations between Bangladesh manufacturing share and Korea/Viet Nam largely weaken in first differences, indicating common trends can explain much of the level association.
- Earlier Granger panel results weaken after stationarisation and Holm correction. Manufacturing share → exports has stationarised p=0.169; exports → manufacturing share p=0.443. These do not support a robust predictive link.
- Cross-country dependence is substantial in several broad indicators (GDP constant-price CD≈39.52; exports/GDP CD≈16.90; both p<0.001 in the existing notebook). Panel methods must account for shared shocks, and implementation should be validated.

## Supported versus not established
**Supported:** trajectories differ across countries; Bangladesh has industrialized; the panel has missingness and cross-country dependence; some apparent correlations are trend-sensitive.

**Not established:** Bangladesh is receiving product lines shed by earlier geese; FDI causes upgrading; 2015/2019 is a definitive turning point; or the Flying Geese causal sequence holds for Bangladesh.

## Four priorities
1. Validate CD, unit-root and Granger implementations against validated econometric packages.
2. Use common country-year windows and report effective n for every result; never replace missing values with zero.
3. Treat high-tech export findings as exploratory due to sparse coverage.
4. Separate descriptive patterns from causal claims; fixed-effects and lagged associations are not causal identification.

## New reproducible notebook
The new notebook fetches WDI data from the public API at execution time and runs coverage checks, plots, common-window comparisons, trend tests with FDR correction, segmented break scans with Bonferroni correction, two-way fixed-effects associations, CD diagnostics, ADF/KPSS checks and lead-lag correlations with multiplicity correction. It has **not been executed in this environment** because network access to retrieve the full WDI data was unavailable; run it in Jupyter with internet access and preserve the resulting tables/data before treating those new tests as findings.

## References
- Akamatsu, K. (1962). A historical pattern of economic growth in developing countries. *The Developing Economies*, 1(S1), 3–25.
- Dowling, M. & Cheang, C.T. (2000). Shifting comparative advantage in Asia: new tests of the flying geese model. *Journal of Asian Economics*, 11(4), 443–463.
- World Bank (2018). *The Future of Manufacturing-Led Development in East Asia*. https://documents1.worldbank.org/curated/en/116191523612461208/pdf/125189-PUB-PUBLIC-docdate-4-11-18.pdf
- WDI manufacturing metadata: https://databank.worldbank.org/metadataglossary/world-development-indicators/series/NV.IND.MANF.ZS
- WDI API documentation: https://datahelpdesk.worldbank.org/knowledgebase/articles/889392-about-the-indicators-api-documentation
