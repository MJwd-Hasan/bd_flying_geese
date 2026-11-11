# WDI notebook analysis: workflow, results, and interpretation

This note summarizes the analysis and saved outputs in [`WDI.ipynb`](./WDI.ipynb). The notebook reports ten economies, 25 WDI indicators, and 66 annual observations spanning 1960–2025. Country-indicator coverage is incomplete and varies; the notebook does not report a full coverage or missingness audit. The values below are transcribed from the notebook's embedded outputs, not independently recalculated in this document.

The notebook is an exploratory analysis. Several implementations and reporting gaps described below mean that its inferential results should be treated as provisional rather than as independently validated evidence.

## 0. Workflow

1. Load the long-format WDI extract and coerce indicator values to numeric.
2. Count the countries, years, and indicator codes; inspect a sample of the rows and calculate country-level summaries.
3. Pivot the data to one row per country-year and create trade-balance and net-trade-competitiveness measures.
4. Plot annual GDP growth and decade-average FDI, high-tech exports, and gross fixed capital formation.
5. Explore rolling correlations between manufacturing growth, population growth, and female population share for Bangladesh and Malaysia.
6. Compare Bangladesh's manufacturing and high-tech-export series with China, Korea (Rep.), and Viet Nam using rank correlations at lags of 0, 5, and 10 years.
7. Run a candidate-year Chow scan for Bangladesh, panel cross-section-dependence and unit-root procedures, Zivot–Andrews tests for three Bangladesh series, and panel Dumitrescu–Hurlin / Bangladesh Toda–Yamamoto tests.
8. Plot the net trade competitiveness ratio and trade balance for a subset of countries.
9. Interpret the results alongside the coverage, model, and indicator limitations below; do not treat correlation or predictive precedence as proof of the Flying Geese mechanism.

## 1. Basic EDA results

The saved output reports **10 countries**, **66 years**, and **25 indicator codes**. The intended country set is Bangladesh, China, Hong Kong SAR, Indonesia, Japan, Korea (Rep.), Malaysia, Philippines, Singapore, and Viet Nam. Although the calendar span is 1960–2025, not every country-indicator pair has observations for all 66 years.

The notebook's descriptive output ranks countries by median GDP per capita growth and also reports means. These are summaries over each country's available observations, not a balanced-panel comparison:

| Rank by median | Economy | Median growth (%) | Mean growth (%) | Maximum growth (%) |
|---:|---|---:|---:|---:|
| 1 | China | 7.43 | 6.63 | 16.05 |
| 2 | Korea, Rep. | 5.91 | 5.74 | 12.96 |
| 3 | Viet Nam | 5.24 | 4.96 | 7.73 |
| 4 | Singapore | 4.74 | 4.77 | 14.83 |
| 5 | Indonesia | 4.16 | 3.23 | 7.95 |
| 6 | Hong Kong SAR, China | 3.97 | 4.01 | 14.71 |
| 7 | Malaysia | 3.94 | 3.62 | 9.06 |
| 8 | Bangladesh | 3.01 | 2.46 | 7.76 |
| 9 | Philippines | 2.49 | 2.06 | 6.77 |
| 10 | Japan | 2.10 | 2.84 | 11.62 |

The five largest country-specific maximum FDI net inflows (% of GDP) in the notebook's output are Hong Kong SAR (58.52%), Singapore (32.26%), Viet Nam (11.94%), Malaysia (8.76%), and China (6.16%). These are maxima, not typical annual flows; FDI as a share of GDP is volatile and is not a direct measure of manufacturing investment.

## 2. Methodology, hypotheses, and reported test statistics

### Derived trade measures

The notebook defines the net trade competitiveness ratio (NTC) as:

$$
\mathrm{NTC}_{it} =
\frac{X_{it}-M_{it}}{T_{it}},
$$

where \(X\), \(M\), and \(T\) are exports, imports, and total trade, respectively, all expressed as a percentage of GDP for economy \(i\) in year \(t\). This is a normalized trade-balance measure. It is not a productivity, domestic-value-added, or causal-growth measure. The notebook plots the NTC but does not print a country-level NTC result table.

### Chow candidate-year test

For each candidate break year, the notebook estimates a pooled OLS model and separate pre-/post-break models. The dependent variable is GDP growth (annual %); regressors are gross fixed capital formation (% of GDP), trade balance (% of GDP), manufacturing value added (% of GDP), trade (% of GDP), and FDI net inflows (% of GDP), plus a constant. For \(N=N_1+N_2\) observations and \(k\) coefficients including the constant, the implemented statistic is:

$$
F =
\frac{[RSS_P-(RSS_1+RSS_2)]/k}
{(RSS_1+RSS_2)/(N_1+N_2-2k)}.
$$

- \(H_0\): the pre- and post-break coefficient vectors are equal.
- \(H_1\): at least one coefficient differs.

The scan evaluates Bangladesh break years 2005–2021 at \(\alpha=0.05\). Its saved decisions mark **2019 and 2020** as significant. The scan output does not preserve the corresponding F-statistics or p-values, and it emits a rank-deficiency warning. These are exploratory candidate-year results: no multiple-testing correction is applied, the candidate years are not a single pre-specified break, and small regimes can make the OLS statistic unreliable.

### Spearman rank correlations

The notebook reports Spearman's rank correlation \(\rho_s\) and its nominal p-value for Bangladesh paired with each comparison economy. The null is no monotonic association (\(\rho_s=0\)); the alternative is a non-zero association. For lag \(k\), the code pairs Bangladesh at year \(t\) with the peer's value at \(t-k\). Correlations are calculated on levels and are exploratory; no multiple-testing adjustment or sample size is shown.

**Manufacturing value added (% of GDP):**

| Peer value at \(t-k\) | Lag \(k\) | Spearman \(\rho_s\) | p-value |
|---|---:|---:|---:|
| China | 0 | -0.938 | <0.001 |
| China | 5 | -0.958 | <0.001 |
| China | 10 | -0.804 | 0.0016 |
| Korea, Rep. | 0 | 0.808 | <0.001 |
| Korea, Rep. | 5 | 0.846 | <0.001 |
| Korea, Rep. | 10 | 0.808 | <0.001 |
| Viet Nam | 0 | 0.871 | <0.001 |
| Viet Nam | 5 | 0.829 | <0.001 |
| Viet Nam | 10 | 0.609 | 0.0467 |

For high-technology exports (% of manufactured exports), every displayed comparison is not significant at 5%: China at lags 0/5 gives \(\rho_s=-0.152/0.314\), \(p=0.676/0.544\); Korea (Rep.) gives \(0.345/0.371\), \(p=0.328/0.468\); Viet Nam gives \(0.248/0.700\), \(p=0.489/0.188\). The lag-10 comparisons are not present in the saved output, consistent with very short and uneven coverage.

### Zivot–Andrews (ZA) unit-root test

The ZA test's null is a unit root; its alternative is stationarity around a deterministic component with one endogenous break. The notebook tests Bangladesh's manufacturing share, exports/GDP, and gross fixed capital formation/GDP under constant (`c`), trend (`t`), and constant-plus-trend (`ct`) specifications. Lags are selected by AIC. The table gives the saved statistic, p-value, selected break year, and 5% critical value:

| Series | Specification | ZA statistic | p-value | Selected break year | 5% critical value |
|---|---|---:|---:|---:|---:|
| Manufacturing value added (% GDP) | c | -3.949 | 0.383 | 1995 | -4.811 |
| Manufacturing value added (% GDP) | t | -3.076 | 0.610 | 1981 | -4.406 |
| Manufacturing value added (% GDP) | ct | -3.827 | 0.618 | 1972 | -5.073 |
| Exports (% GDP) | c | -2.684 | 0.970 | 1991 | -4.811 |
| Exports (% GDP) | t | -2.277 | 0.956 | 2013 | -4.406 |
| Exports (% GDP) | ct | -3.060 | 0.955 | 2004 | -5.073 |
| Gross fixed capital formation (% GDP) | c | -1.485 | 0.999 | 1995 | -4.811 |
| Gross fixed capital formation (% GDP) | t | -1.649 | 0.999 | 2019 | -4.406 |
| Gross fixed capital formation (% GDP) | ct | -1.781 | 0.999 | 2017 | -5.073 |

None of these specifications rejects a unit root at 5%. A selected break year is not, by itself, evidence of a statistically established structural break. The ZA input drops missing observations before testing and does not check whether the remaining years are consecutive; gaps can therefore be treated as adjacent observations.

### Panel cross-section dependence and unit-root outputs

For the reported Pesaran CD procedure, \(H_0\) is cross-sectional independence and \(H_1\) is dependence. The notebook's implementation applies a correlation-based statistic to raw panel series, with pairwise available sample sizes. Selected saved outputs are:

| Series | CD statistic | p-value |
|---|---:|---:|
| Manufacturing value added (% of GDP) | 9.688 | <0.001 |
| Trade balance (% of GDP) | 6.461 | <0.001 |
| NTC | 4.208 | <0.001 |
| Medium and high-tech exports (% manufactured exports) | 3.993 | <0.001 |
| High-technology exports (% manufactured exports) | 1.888 | 0.059 |

These are not a standard residual-based diagnostic as implemented in the notebook; the unbalanced coverage and raw trending levels further limit inference. Treat them as evidence that the cross-country series co-move, not as validated tests of residual dependence.

The notebook also prints IPS and CIPS-style panel unit-root results. Its stated null is a unit root; IPS combines individual ADF results and the CIPS-style statistic averages cross-section-augmented regressions. Its classification rule labels a series I(0) if either the IPS p-value is below 0.05 or the CIPS-style statistic is below -2.33; otherwise it checks the first differences with the same rule and labels the result I(1) or >I(1). Selected level statistics and the notebook's classifications are:

| Series | IPS W (level) | IPS p (level) | CIPS (level) | Notebook classification |
|---|---:|---:|---:|---|
| Manufacturing value added (% of GDP) | 0.049 | 0.520 | -1.928 | I(1) |
| GDP per capita growth (annual %) | -11.101 | <0.001 | -5.074 | I(0) |
| NTC | -4.486 | <0.001 | -2.723 | I(0) |
| Medium and high-tech exports (% manufactured exports) | -2.494 | 0.006 | -2.264 | I(0) |

The CIPS-like calculation is hand-coded, CIPS p-values/critical values are not printed, and the IPS statistic uses fixed moments with a normal approximation. The OR rule can label a series stationary when only one of the two procedures rejects. The IPS/CIPS classifications should therefore be re-run with a validated implementation before being used to determine a model specification.

### Dumitrescu–Hurlin panel and Toda–Yamamoto Bangladesh tests

For each country, the notebook estimates a one-lag equation of the form:

$$
y_{it}=\alpha_i+\gamma_i y_{i,t-1}+\beta_i x_{i,t-1}+\varepsilon_{it}.
$$

For Dumitrescu–Hurlin (DH), \(H_0\) is that \(x\) does not Granger-predict \(y\) for any panel member; the heterogeneous alternative allows predictive effects for some members. The reported \(\bar W\), standardized \(\tilde Z\), and panel p-value are from the notebook's implementation. For selected directions:

| Direction | DH \(\bar W\) | DH \(\tilde Z\) | Panel p-value |
|---|---:|---:|---:|
| FDI → manufacturing value added | 2.771 | 3.443 | 0.00058 |
| Manufacturing value added → FDI | 1.786 | 1.460 | 0.144 |
| Gross fixed capital formation → manufacturing value added | 2.110 | 2.134 | 0.0329 |
| Manufacturing value added → GDP per capita growth | 3.182 | 4.329 | 0.000015 |
| GDP per capita growth → manufacturing value added | 1.028 | -0.054 | 0.957 |
| High-tech exports → gross fixed capital formation | 3.229 | 3.152 | 0.00162 |

For Bangladesh, the notebook uses a one-lag Toda–Yamamoto-style augmented VAR with \(d_{\max}=1\) and tests the lagged \(x\) coefficient(s); \(H_0\) is no predictive effect from \(x\) to \(y\). Examples from its saved table:

| Bangladesh direction | Wald statistic | p-value |
|---|---:|---:|
| FDI → manufacturing value added | 0.050 | 0.823 |
| Manufacturing value added → GDP per capita growth | 4.054 | 0.0441 |
| High-tech exports → gross fixed capital formation | 23.938 | <0.001 |
| Exports → GDP per capita growth | 3.513 | 0.0609 |

The notebook does not report the country-specific sample size in this output. The high-tech series is visibly short, and the apparent high-tech-to-capital-formation result should not be relied on without reporting usable observations, checking lag adequacy, and reproducing the Toda–Yamamoto specification. DH/TY first drops missing rows and then constructs lags by row position; if a country series has calendar-year gaps, a one-row lag need not mean one year. DH/TY rejection indicates predictive precedence under the fitted model, not structural causation.

## 3. Execution process

The notebook reads the long-format CSV, converts `Value` to numeric (unparseable values become missing), converts `Time`, then pivots to country-year rows. The year conversion should be replaced with explicit integer-year parsing and validated before time-series tests. It creates plots and test outputs in sequence; saved results include a rank-deficiency warning for the Chow regression. Global warning suppression in the notebook can hide other diagnostics.

Run from the repository root after installing `requirements.txt`. To avoid overwriting the checked-in notebook while reproducing it:

```bash
python -m pip install -r requirements.txt
jupyter nbconvert --to notebook --execute WDI.ipynb --output WDI.executed.ipynb
```

The input expression in the notebook resolves to `WDI_data.csv`, while the tracked file is named `wdi_data.csv`. Windows commonly treats these names as equivalent; case-sensitive filesystems do not. Make the spelling consistent before expecting a portable run. The saved notebook output is not proof of a clean-kernel execution against a freshly audited file.

## 4. Results and discussion

- The available-series growth summaries place Bangladesh eighth of ten by median GDP per capita growth (3.01%), below Viet Nam (5.24%) and China (7.43%). This is descriptive and is not a controlled comparison because the underlying country samples may differ.
- Bangladesh manufacturing-share levels are strongly associated with peer-country levels: positive with Korea and Viet Nam, negative with China, including at the tested lags. These large rank correlations can be driven by common or opposing long-run trends; the notebook does not report first-difference correlations.
- The displayed high-tech-export correlations are not statistically significant at 5%, and the available samples are short. The notebook therefore supplies no strong inferential evidence of a Bangladesh–peer high-tech relationship.
- The ZA tests do not reject a unit root in any of the three Bangladesh indicators, despite returning candidate break dates. The plotted candidate dates must not be narrated as confirmed events.
- The DH panel results show statistically significant predictive links for several directions, while Bangladesh-specific results differ. For example, the panel FDI → manufacturing p-value is 0.00058 but Bangladesh's reported p-value is 0.823. This is not a contradiction: the panel statistic tests a heterogeneous regional hypothesis and does not imply the same relationship for Bangladesh.
- The Bangladesh high-tech exports → capital formation p-value is very small, but its short high-tech series and unreported sample size make it especially fragile. It should not be converted into a policy claim.
- The decade-average FDI/high-tech quadrant and NTC/trade-balance charts are descriptive. Their notebook cells do not produce a numerical result table or uncertainty estimates.

## 5. Interpretation

The notebook is consistent with differences in growth histories and with comovement among several regional indicators, but it does not demonstrate a sequential transfer of production from leading geese to Bangladesh. In particular:

- A correlation in level shares does not establish synchronization, temporal precedence, or production relocation.
- Granger-type tests do not identify structural causes, policy effects, or the mechanism of technology transfer.
- FDI inflows as a percentage of GDP do not identify manufacturing-specific investment or spillovers.
- High-tech exports as a share of manufactured exports measures export composition, not the level of high-tech output or domestic value added.
- Female population share is demographic composition, not female employment, labour-force participation, or manufacturing labour absorption. The notebook's demographic comparison is Bangladesh versus Malaysia, not Bangladesh versus Viet Nam.
- The notebook's annual observations have no within-year seasonal frequency. Seasonal decomposition is not an appropriate interpretation of annual data.
- NTC reflects a normalized trade balance. A negative value does not, by itself, prove weak productivity or that a country is inward-looking.

## 6. Comparison with Bangladesh

| Evidence in the notebook | Bangladesh | Comparator result | Careful reading |
|---|---:|---:|---|
| Median GDP per capita growth | 3.01% (mean 2.46%) | Viet Nam 5.24% (4.96%); China 7.43% (6.63%) | Bangladesh is lower in the available-sample summaries; samples are not shown to be balanced. |
| Manufacturing value-added share, Spearman levels | Reference series | Korea: \(\rho_s=0.808\) at lag 0; Viet Nam: 0.871; China: -0.938 | Strong level association; not evidence that Bangladesh follows or replaces any peer. |
| High-tech exports, Spearman levels | Reference series | All displayed China/Korea/Viet Nam comparisons have \(p>0.18\) | No significant rank association in the displayed short-sample tests. |
| Chow candidate scan | Nominal rejections at 2019 and 2020 | No comparison-country scan is summarized in this notebook output | The scan omits F/p values and is vulnerable to multiple testing and rank deficiency. |
| Bangladesh-specific FDI → manufacturing TY test | Wald 0.050; \(p=0.823\) | Regional DH panel: \(\bar W=2.771\), \(p=0.00058\) | A panel-level association does not establish a Bangladesh-specific effect. |
| Bangladesh high-tech exports → capital formation TY test | Wald 23.938; \(p<0.001\) | No comparable country-by-country estimates are reported | Short series and absent sample-size reporting make this result fragile. |

The notebook's country-level evidence therefore places Bangladesh below several comparators on available-sample median per-capita growth and shows different correlation and predictive-test results by variable. It does not provide a robust test of whether Bangladesh is following the same industrial sequence as Viet Nam, China, or Korea.

## 7. Conclusion

The WDI notebook is useful as an exploratory, reproducible starting point: it establishes broad coverage, summarizes growth, visualizes trade and investment indicators, and reports several time-series and panel statistics. Its saved outputs show lower median per-capita growth for Bangladesh than China and Viet Nam, substantial level correlations in manufacturing shares, no significant displayed high-tech rank correlations, and mixed panel-versus-Bangladesh predictive results.

The evidence is not sufficient to conclude that FDI, manufacturing, trade, or high-tech exports caused Bangladesh's growth outcomes, or that Bangladesh has entered a Flying Geese follower stage. Before relying on the inferential claims, standardize the CSV path and year parsing, report country-indicator coverage and sample sizes, expose all Chow statistics, adjust for multiple comparisons, validate the panel test implementations, and repeat the analysis on defensible common windows and stationary specifications.
