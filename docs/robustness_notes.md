# Robustness notes

These checks were added to `export_import.ipynb` (cells marked **Robustness**). The original specifications are unchanged and still reproduce the paper's numbers; the checks show how much each result depends on specification choices. The table below reports the **nine-economy** results; the section *Update: Hong Kong SAR and medium and high-tech exports* at the end shows what changed with ten economies.

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

*Update:* the notebook value (p = 0.827) is unchanged in the ten-economy run, and `bangladesh_flying_geese.md` now reports 0.827.

## Other observations

- The data start in 1976 (the paper said 1975; `bangladesh_flying_geese.md` now says 1976). The CSV itself now begins in 1960, but both notebooks keep the 1976–2025 window through `ANALYSIS_START = 1976`; setting it to 1960 would add 2,389 pre-1976 observations for the original nine economies and change their results.
- Bangladesh's gross fixed capital formation starts in 1980 (46 observations); Philippines and Viet Nam have the shortest series for several indicators (see the coverage table in the notebook).
- High-technology exports has only 10 observations for Bangladesh and 8-18 elsewhere.
- Bangladesh manufacturing value added jumps from about 16.8% to 20.4% of GDP between 2014 and 2015; it is worth checking whether this is a national-accounts revision rather than an economic shift.
- The integration-order rule (IPS/Fisher or CIPS) is crude: for example, high-tech exports comes out I(0) on very few country series, and the smoothed manufacturing series is I(0) while the raw series was I(1) in the nine-economy run (with Hong Kong the raw series is also labelled I(0); see the update section). The IPS W statistic uses fixed moments and is approximate; CIPS uses an approximate -2.33 cut-off.

## Bug fixes in the notebook

- `'Korea rep.'` (typo) silently dropped Korea from the net-trade and trade-balance plots; fixed to `'Korea, Rep.'` with a colour added to the palette.
- Nested same-quote f-strings required Python 3.12+; rewritten.
- Chow test: rank-deficient or too-small regimes produced a `SingularMatrixWarning` and unreliable F-values; they now return NaN.
- Year column was round-tripped through `datetime`; now kept as an integer.
- Leaked prompt text and merged text in two markdown cells removed; typos corrected; the IPS DOI corrected.

## Update: Hong Kong SAR and medium and high-tech exports

`export_import.ipynb` and `flying_geese_panel_eda.ipynb` were extended with Hong Kong SAR and *Medium and high-tech exports (% manufactured exports)* (`TX.MNF.TECH.ZS.UN`, 1990–2024 for every economy). Both were re-run end to end. **For the nine original economies every country-specific result reproduces exactly** (Chow scans, Spearman lead/lag, trends, break scans, ADF/KPSS, Zivot-Andrews, Bangladesh Toda-Yamamoto). Only panel-level and multiple-testing-adjusted statistics move.

| Result | Nine economies | Ten economies (with Hong Kong) | Reading |
|---|---|---|---|
| Chow breaks | Bangladesh 2019; Viet Nam 2019; long Indonesia/Korea runs, etc. | Unchanged; Hong Kong adds 2018 (p = 0.028) | Hong Kong's 2018 has 7 post-break years and fails the 2k and Bonferroni rules (only 12 candidate years because its manufacturing series starts in 2000) |
| Fisher-ADF, manufacturing share | p = 0.759 (I(1)) | p = 0.0004 (I(0)) | Driven by Hong Kong alone (its ADF p = 2.6e-8); excluding it returns 0.759. CIPS = −1.99 still does not reject at −2.33. The notebook's "Fisher or CIPS" rule is sensitive to one economy |
| DH, FDI → manufacturing | levels p = 0.006; differenced 0.161 | levels p = 0.016 (not differenced by the rule); differenced 0.176 | Holm-adjusted p = 0.20; not robust to differencing in either panel |
| DH, manufacturing → GDP per capita growth | levels 0.0295; differenced 0.771 | levels 0.0299 (not differenced by the rule); differenced 0.954 | Same pattern |
| DH, high-tech exports → capital formation | levels p = 0.002 | levels p = 0.0016 (Holm 0.023); stationarised 0.172 | Still not robust to stationarising; Bangladesh Toda-Yamamoto has 8 observations |
| DH, capital formation → medium/high-tech exports (new) | n/a | levels p < 0.001 (Holm 0.0001); stationarised 0.115 | Significant only on levels |
| DH, FDI → medium/high-tech exports (new) | n/a | p = 0.163 | Not significant |
| Bangladesh Toda-Yamamoto, medium/high-tech exports (new; n = 33) | n/a | FDI → MHT p = 0.057; GFCF → MHT p = 0.865; MHT → GFCF p = 0.994; MHT → FDI p = 0.573 | No predictive link; does not corroborate the 8-observation high-tech result |
| Pesaran CD (export_import) | exports, FDI, manufacturing significant | adds medium/high-tech exports 3.99 (p = 0.0001); high-tech exports 1.89 (p = 0.059); capital formation −0.79 (p = 0.43) | Cross-sectional dependence is present in most variables |
| Two-way FE, lagged FDI → manufacturing share | −0.229 (p = 0.002; n = 334) | −0.153 (p = 0.021; BH 0.042; n = 359) | Sensitive to Hong Kong; 10 clusters only |

### Further points

- **Integration-order rule.** The rule labels a series I(0) if the Fisher-ADF p-value is below 0.05 *or* CIPS is below −2.33. Fisher combination is dominated by a single very small p-value, which is what happens with Hong Kong. The same reclassification affects industry value added and manufacturing value added in constant US$, which are also now I(0). A more conservative rule (requiring both tests, or reporting results with and without Hong Kong) would keep manufacturing share I(1).
- **Medium and high-tech exports** is classed I(0) by Fisher-ADF (p = 0.0013) while CIPS (−2.26) does not reject. Treat the classification as borderline.
- **Cross-sectional dependence in the EDA notebook.** The approximate CD cell in `flying_geese_panel_eda.ipynb` uses N = number of years and T = number of economies (the reverse of the usual convention), so its statistic is understated (exports/GDP: 1.78 versus 20.07 in `export_import.ipynb`). Use the `export_import.ipynb` Pesaran CD.
- **Multiple testing.** The EDA trend family grew from 79 to 98 tests and lead/lag from 69 to 117, and the causality family from 14 to 18 directions, so BH- and Holm-adjusted p-values for existing rows can differ from earlier reports even though raw statistics are identical.
- **Hong Kong data limits.** Manufacturing, industry, services and agriculture value added start in 2000 (25 observations). FDI inflows reach 58.5% of GDP, so Kojima figures use a symmetric-log FDI axis.

