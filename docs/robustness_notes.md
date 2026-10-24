# Robustness notes

These checks were added to `export_import.ipynb` (cells marked **Robustness**). The original specifications are unchanged and still reproduce the paper's numbers; the checks show how much each result depends on specification choices. Nothing in the paper text was edited.

## What changes

| Result in the paper | Original notebook | Robustness check | Reading |
|---|---|---|---|
| Chow break in 2019 for Bangladesh (and Viet Nam) | p = 0.030 (Bangladesh) | The post-2019 regime has 7 observations for 6 parameters (1 residual d.o.f.). With at least 2k observations per regime the break disappears; it also fails Bonferroni | Fragile; the data cannot support a pandemic-specific break for Bangladesh. Viet Nam 2019 survives Bonferroni but has the same short-regime problem |
| Long runs of Chow breaks for Indonesia and Korea (1995-2008 or later) | Reported as pandemic-era effects | Persist under all three rules | Not pandemic effects: the runs start in 1995. An earlier shock (e.g. the 1997-98 crisis) is a more likely driver, worth checking |
| Zivot-Andrews breaks: exports 2004/2012, capital formation 2018-19 | Reported as structural breaks | Unit root is **not** rejected for exports (p = 0.39-0.54) or capital formation (p = 0.999) in any specification | Break dates are not confirmed. Only manufacturing VA (constant-only model, 2015) rejects at 5% |
| Strong Spearman links with Viet Nam (+) and China (-) in manufacturing share | rho = +0.87 / -0.94 in levels | On first differences rho = 0.06 / -0.05 (p > 0.5) | Levels correlation reflects shared trends, not co-movement |
| Dumitrescu-Hurlin: FDI -> manufacturing, p = 0.006 | Run on levels | On first differences p = 0.16 (Holm-adjusted levels p = 0.06) | Not robust to stationarising |
| Dumitrescu-Hurlin: manufacturing <-> exports, p < 0.001 | Run on levels | On first differences p = 0.17 and 0.44 | Not robust |
| Toda-Yamamoto, high-tech exports -> capital formation, p = 0.000 | Wald = 23.9 | Estimated on 8 observations (k = 1, d_max = 1, fixed lag) | Very small sample; treat as indicative only |

## Possible transcription issue

The paper reports p = 0.853 for the Bangladesh FDI -> manufacturing link. The notebook gives p = 0.827 for that direction; 0.853 matches the Wald statistic of the capital formation -> high-tech exports row. Worth re-checking against the table.

## Other observations

- The data start in 1976 (the paper says 1975).
- Bangladesh's gross fixed capital formation starts in 1980 (46 observations); Philippines and Viet Nam have the shortest series for several indicators (see the coverage table in the notebook).
- High-technology exports has only 10 observations for Bangladesh and 8-18 elsewhere.
- Bangladesh manufacturing value added jumps from about 16.8% to 20.4% of GDP between 2014 and 2015; it is worth checking whether this is a national-accounts revision rather than an economic shift.
- The integration-order rule (IPS/Fisher or CIPS) is crude: for example, high-tech exports comes out I(0) on very few country series, and the smoothed manufacturing series is I(0) while the raw series is I(1). The IPS W statistic uses fixed moments and is approximate; CIPS uses an approximate -2.33 cut-off.

## Bug fixes in the notebook

- `'Korea rep.'` (typo) silently dropped Korea from the net-trade and trade-balance plots; fixed to `'Korea, Rep.'` with a colour added to the palette.
- Nested same-quote f-strings required Python 3.12+; rewritten.
- Chow test: rank-deficient or too-small regimes produced a `SingularMatrixWarning` and unreliable F-values; they now return NaN.
- Year column was round-tripped through `datetime`; now kept as an integer.
- Leaked prompt text and merged text in two markdown cells removed; typos corrected; the IPS DOI corrected.
