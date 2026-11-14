# Political Institutions and Economic Growth: Bangladesh–Vietnam Comparison

## 1. Scope and source files

This report supersedes the earlier preliminary interpretations of `pol_data.ipynb`. It is based on a fresh, clean-kernel execution using the Library copy of **DPI 2023 CSV Version.csv** and the supplied WDI extract `wdi_data(3).csv`.

- DPI selection: 15 countries, 1975–2023; 735 country-year rows; 49 observations per country; no duplicate country-year keys.
- WDI extract: 10 economies and 25 indicators in long format.
- DPI–WDI intersection: 7 countries and 343 country-year rows (7 × 49): Bangladesh, Indonesia, Japan, Malaysia, Philippines, Singapore and Vietnam.
- Bangladesh–Vietnam GDP-per-capita growth comparison: 1985–2023, 39 paired years. The WDI growth series is not available for Vietnam in the earlier years of the DPI panel.

The original 15-country political panel is retained for political EDA. Economic panel models necessarily use only the seven countries with WDI observations. The conclusions are limited to 1975–2023 (and to 1985–2023 when using GDP-per-capita growth for the Bangladesh–Vietnam comparison).

## 2. Important DPI coding rules

The DPI unit is one country-year. Most variables refer to the situation on 1 January; `LEGELEC` and `EXELEC` report whether an election took place during the year. For general numeric fields, a blank means no information and `-999`/`NA` means not applicable. Binary variables ordinarily use 1 = yes and 0 = no, but documented exceptions must be respected.

The following corrections are essential:

- `MILITARY` means **the chief executive is a military officer**. It is not a general indicator of military rule.
- `DEFMIN` asks whether the defence minister is a military officer.
- `FRAUD` is a source-based indicator of serious electoral irregularity/intimidation. A zero is not proof of a fair election: irregularities are only coded when mentioned in sources, and false negatives are possible. The code can persist from the most recent election until a fair election.
- `ALLHOUSE` means the executive party has an absolute majority in all relevant lawmaking houses.
- `CHECKS` is a codebook-defined count of veto players. It is not a simple democracy, political quality or governance score.
- `AUTON` has a special convention: **no information is recorded as zero**. Consequently, Bangladesh and Vietnam's all-zero AUTON observations cannot be interpreted as definitive evidence that autonomous regions were absent.
- `MUNI` and `STATE` use 0/1/2 categories: neither local executive nor legislature elected; legislature elected but executive appointed; both elected. Blank means no information or no evidence. A blank must not be recoded as 0.
- `AUTHOR` identifies whether states/provinces have authority over taxation, spending or legislation. Missing data must not be interpreted as no authority.
- `EXECRLC = 0` is not one of the valid Left/Center/Right ideology classes; it denotes no information or no classifiable economic platform.
- `EXECREL = 0` means “otherwise” under DPI's religion coding; it does not establish that an executive had no religious affiliation.
- `MAJ` is the government’s **share of legislative seats**, `NUMGOV / (NUMGOV + NUMOPP + NUMUL)`, a 0–1 fraction. It is not a vote margin.
- `PARTYAGE` is already the annual average age of the first government party, second government party and first opposition party, or the known subset. Country-level mean and median should aggregate this variable, not count its nonmissing values.
- `NUMVOTE` and `OPPVOTE` are labelled government/opposition vote shares, but the relevant codebook definitions do not provide a sufficiently transparent denominator/unit formula. Their raw scale is audited, but the means are not treated as validated conventional vote percentages.

The notebook includes a variable dictionary for every DPI indicator it uses and a WDI series dictionary for all 25 supplied World Development Indicators.

## 3. Bangladesh annual verification

The Bangladesh table in the reproduced notebook gives every year from 1975 through 2023 for `military`, `defmin`, `fraud`, `allhouse`, `author`, `auton`, `muni` and `state`, alongside the original source tokens. Blank and `-999` remain distinct in the raw audit.

### 3.1 Corrected binary denominators, 1975–2023

| DPI field | Positive observations | Valid binary observations | Positive share among valid |
|---|---:|---:|---:|
| `MILITARY` | 14 | 47 | 29.8% |
| `DEFMIN` | 12 | 44 | 27.3% |
| `FRAUD` | 5 | 41 | 12.2% |
| `ALLHOUSE` | 34 | 39 | 87.2% |
| `AUTHOR` | 0 | 39 | 0.0% |

The denominator excludes both blank and not-applicable values and includes only valid 0/1 observations. It is shown explicitly so the percentages are not mistaken for shares of all 49 panel years.

`AUTON` is recorded as zero in all 49 Bangladesh years, but its special missing-information convention means the all-zero series cannot be interpreted as a proven absence of autonomous regions.

### 3.2 Military indicator: episode correction

Bangladesh has **14 positive `MILITARY` years**, grouped into two contiguous episodes:

| Episode | Start | End | Flagged years |
|---|---:|---:|---:|
| 1 | 1976 | 1981 | 6 |
| 2 | 1983 | 1990 | 8 |
| **Total** |  |  | **14** |

The year 1982 is not flagged, so 1976–1990 is not one continuous episode. `max(year) - min(year)` would return a calendar span, not the number of positive observations; the notebook now reports the sum and the separate contiguous runs. The variable describes military-officer status of the chief executive, not military rule as a constitutional regime.

### 3.3 Local government, subnational authority and party age

For Bangladesh across 1975–2023:

- `MUNI`: 32 years “No local elections”, 6 “Legislature locally elected”, 3 “Legislature and executive locally elected”, and 8 blank years.
- `STATE`: 43 years “No local elections” and 6 blank years.
- `AUTHOR`: 39 observed zero values and 10 unavailable years.
- `PARTYAGE`: 35 nonmissing annual values; mean 31.57 years and median 29.33 years.

The `PARTYAGE` values are already annual averages across the relevant government/opposition parties. The corrected country summary calculates the mean/median across available years and reports its nonmissing count.

## 4. Bangladesh–Vietnam institutional comparison, 1985–2023

This common period is used because Vietnam's GDP-per-capita growth series starts in 1985 in the supplied WDI extract.

| Indicator | Bangladesh | Vietnam | Comparability note |
|---|---:|---:|---|
| Chief executive military officer | 6/37 valid (16.2%) | 5/39 (12.8%) | `MILITARY` is officer status, not a military-rule indicator |
| Defence minister military officer | 6/37 (16.2%) | 39/39 (100%) | A different office; do not conflate with `MILITARY` |
| Election irregularity flag | 5/38 (13.2%) | 0/39 | Zero means no irregularity recorded in the DPI sources, not proof of no irregularities |
| Executive party controls all relevant houses | 30/35 (85.7%) | 39/39 (100%) | Both are high on this measure |
| State/province authority (`AUTHOR`) | 0/39 | 0 valid observations | Not comparable; Vietnam has no observed values |
| `AUTON` | 39 zeros | 39 zeros | Not evidence of confirmed absence; DPI uses 0 for no information |
| `PARTYAGE` annual mean | 32.89 years (n=32) | 53.00 years (n=39) | Average age of the relevant parties, not executive tenure |
| System category | 30 parliamentary; 7 presidential; 2 not applicable | 39 assembly-elected president | Raw executive-election totals should not be compared without system context |

Other descriptive differences: Bangladesh's `CHECKS` averages 2.85 in the common period, whereas Vietnam's is 1.00. This is a veto-player count built from electoral and institutional rules; it is not a direct score of democratic quality or good governance. Bangladesh's `MUNI` values are 30 “No local elections”, 6 “Legislature locally elected”, and 3 “Legislature and executive locally elected”; Vietnam's are 11 “No local elections” and 28 “Legislature and executive locally elected”. For `STATE`, Bangladesh has 39 “No local elections”; Vietnam has 36 “No local elections” and 3 “Legislature and executive locally elected”. These are DPI's subnational-government codings, not an independent audit of every local election.

Executive-election indicators are stratified by country and `SYSTEM` in the notebook. The dataset includes parliamentary, presidential and assembly-elected-president systems. The latter is not simply a parliamentary or presidential subtype for interpreting executive election counts.

## 5. Economic performance: Bangladesh versus Vietnam

The primary outcome is WDI `NY.GDP.PCAP.KD.ZG` (GDP per-capita growth, annual %). The pair comparison is based on the 39 paired years 1985–2023.

| Measure | Bangladesh | Vietnam |
|---|---:|---:|
| Mean GDP per-capita growth, 1985–2023 | 3.8481% | 4.8625% |
| GDP per capita, 1985 (constant 2015 US$) | 438.38 | 603.98 |
| GDP per capita, 2023 (constant 2015 US$) | 1,885.38 | 3,772.36 |

The annual paired difference (Bangladesh minus Vietnam) is **−1.0145 percentage points**. A regression of that annual difference on a constant with Newey–West HAC standard errors (2 lags) gives SE = 0.4746, p = 0.0326 and 95% CI [−1.9447, −0.0843], N = 39. The Bangladesh/Vietnam GDP-per-capita level ratio falls from about 0.726 in 1985 to 0.500 in 2023. Thus the income-per-capita gap widened in this WDI extract.

This is strong descriptive evidence of a growth differential, but it does not identify its causes.

## 6. Econometric results

### 6.1 Main two-way fixed-effects model

The main specification is:

\[
g_{it} = \beta_1 MILITARY_{i,t-1} +
\beta_2 FRAUD_{i,t-1} +
\beta_3 ALLHOUSE_{i,t-1} +
\alpha_i + \lambda_t + \varepsilon_{it}
\]

where `g` is annual GDP-per-capita growth in percentage points, `α` are country fixed effects and `λ` are year fixed effects. Political predictors are lagged one year. Inference uses Driscoll–Kraay standard errors with a 2-year bandwidth.

- N = 268 country-years; 7 countries; 39 years.
- R² = 0.5379.
- Joint test for the three political predictors: Wald χ² = 11.05; corresponding F(3,38) = 3.685, p = 0.0201.

| Lagged predictor | Coefficient (percentage points) | DK SE | p-value | 95% CI |
|---|---:|---:|---:|---:|
| `MILITARY` | −0.0101 | 0.6763 | 0.9882 | [−1.3792, 1.3590] |
| `FRAUD` | −1.4967 | 0.8127 | 0.0733 | [−3.1419, 0.1484] |
| `ALLHOUSE` | −1.2426 | 0.5574 | 0.0318 | [−2.3710, −0.1142] |

The only individual coefficient below 5% in this main specification is `ALLHOUSE`: years following a recorded executive-party majority are conditionally associated with about 1.24 percentage points lower GDP-per-capita growth, holding country and year effects constant. This is an association, not an estimated causal treatment effect. `MILITARY` has an essentially zero estimate with a very wide interval; `FRAUD` is negative but not significant at 5%.

### 6.2 Sensitivity specifications

| Specification | N | Predictor | Coefficient | DK p-value |
|---|---:|---|---:|---:|
| Add lagged GFCF, trade and FDI | 241 | `ALLHOUSE` | −0.9291 | 0.2463 |
| Replace `ALLHOUSE` with `CHECKS` | 269 | `CHECKS` | +0.3094 | 0.3097 |
| Dynamic FE (add lagged GDPpc growth) | 267 | `ALLHOUSE` | −0.9524 | 0.0737 |
| First difference of GDPpc growth | 267 | `ALLHOUSE` | −0.1243 | 0.8111 |

In the macro-control sensitivity, lagged military p = 0.6108 and lagged fraud p = 0.4732. In the dynamic FE model, lagged GDP-per-capita growth is positive and significant (coefficient 0.2582, p = 0.0229). In the first-difference model, no political coefficient is significant. GFCF, trade and FDI may be transmission mechanisms rather than pre-treatment confounders, so the macro-control specification is a channel/sensitivity test and not the preferred total-effect model. Its smaller sample (241 observations) is also material.

The `ALLHOUSE` association in the main model weakens when the specification changes. The first-difference result is close to zero and statistically insignificant. That pattern does not justify claiming that legislative majority control reduces growth.

### 6.3 Traditional panel specification tests

For panel specification tests, a balanced common sample has 7 countries and 34 common year waves between 1988 and 2023 (1985–1987 and 2008–2009 are dropped because not all countries have complete model observations).

| Test | Statistic | p-value | Interpretation at 5% |
|---|---:|---:|---|
| Country FE vs pooled OLS | F(6,227) = 4.5617 | 0.0002 | Reject pooled model without country effects |
| Breusch–Pagan LM random-intercept test | χ²(1) = 14.9265 | 0.0001 | Evidence of a panel-level random component |
| Mundlak country-mean terms jointly zero | χ²(3) = 17.0397 | 0.0007 | Reject RE exogeneity; prefer FE |

The Mundlak correlated-random-effects test is used as the Hausman-style diagnostic. It tests whether country means of the time-varying political regressors jointly matter in a random-intercept model; rejection is evidence against the random-effects orthogonality assumption. The notebook does not report a numerically invalid/non-positive-definite conventional FE–RE covariance-difference statistic.

### 6.4 Stationarity and cross-sectional dependence

Country-level GDP-per-capita growth ADF/KPSS tests over 1985–2023 indicate nonstationarity for Bangladesh in levels (ADF p = 0.5828; KPSS p = 0.0100), while Vietnam's level series rejects the ADF unit-root null (p = 0.0099) and does not reject KPSS stationarity at the 10% table boundary (p = 0.1000). Bangladesh's first difference is stationary in these checks (ADF p < 0.001; KPSS p = 0.1000). The notebook reports all seven country tests.

A Pesaran-style CD statistic on the balanced 7-country growth panel is 9.5267 (p < 0.001), with mean pairwise correlation 0.3329. Cross-sectional independence is therefore implausible. DK standard errors help address common dependence, but seven countries are still a very small cross-section.

### 6.5 Exploratory country-level Granger tests

These tests examine predictive temporal precedence, not structural causality. They use one lag and the longest contiguous non-missing series. Bangladesh uses first-differenced GDP-per-capita growth; Vietnam uses growth in levels because the stationarity checks support those respective transformations.

- Bangladesh: military → differenced growth p = 0.8637; fraud → differenced growth p = 0.4143; allhouse → differenced growth p = 0.4962; checks → differenced growth p = 0.8402. The reverse direction is significant for military (growth → military p = 0.0164) and fraud (growth → fraud p = 0.0003), which is compatible with political coding reacting to economic/political conditions, but does not prove reverse causation.
- Vietnam: military → growth p = 0.2630; growth → military p = 0.3010. `FRAUD`, `ALLHOUSE` and `CHECKS` are constant over the 39 years in the tested sample, so no Granger test can be estimated for these variables.

Since different growth transformations are used across the two countries, the Bangladesh and Vietnam Granger p-values are not directly comparable. The results do not show that the tested political indicators reliably predict growth in the chosen specifications.

## 7. What can and cannot be concluded

**Supported by this analysis**
1. Vietnam had higher average GDP-per-capita growth than Bangladesh during 1985–2023 in the supplied WDI extract, and its GDP-per-capita lead widened.
2. In the seven-country two-way FE model, the three lagged political indicators are jointly associated with GDP-per-capita growth, while `ALLHOUSE` has a negative individual coefficient in the main specification.
3. That `ALLHOUSE` coefficient is sensitive to model specification; it is not significant in the macro-control, dynamic and first-difference robustness models.
4. The selected country panel exhibits strong cross-sectional dependence, requiring caution with conventional inference.

**Not established**
- That politics is the certain, sole or dominant reason for Bangladesh's slower growth.
- That `MILITARY`, `FRAUD`, `ALLHOUSE`, `CHECKS` or any single DPI indicator has a structural causal effect on growth.
- That zero `AUTON` or `FRAUD` values prove no autonomous regions or no election irregularities.
- That vote-share means are conventional percentages with a known denominator.
- That local election categories independently verify actual local election conduct.

A stronger causal design would need a theoretically defensible source of exogenous institutional variation, a natural experiment or credible instrument, and additional evidence on investment quality, industrial/export transformation, education and skills, infrastructure, state capacity, conflict legacies, demographic structure and global economic exposure. These are plausible competing channels to investigate—not conclusions generated by the present model.

## 8. Reproducibility outputs

Running `pol_data.ipynb` creates an `outputs/` directory containing:
- processed seven-country DPI–WDI merged panel;
- Bangladesh annual political audit with raw source codes;
- military-officer episode table;
- country-level binary event counts, valid denominators and proportions;
- party-age summaries;
- executive-election counts stratified by system;
- vote-share/majority audit;
- DPI and WDI variable dictionaries;
- main model, panel specification, stationarity and Granger result tables.

The notebook imports raw DPI values as strings first, preserves blank vs `-999` in the audit, and masks both `-999` and `-999.0` numerically before estimation.

## References

- Cruz, C., Keefer, P., Scartascini, C., & Simpser, A. (2026). *The Database of Political Institutions (DPI): 2023*. Inter-American Development Bank. [Dataset and metadata](https://data.iadb.org/dataset/the-database-of-political-institutions-dpi-2023).
- Cruz, C., Keefer, P., Scartascini, C., & Simpser, A. (2025). *Codebook, Database of Political Institutions 2025*. Inter-American Development Bank Research Department. Available from the [official DPI 2023 dataset page](https://data.iadb.org/dataset/the-database-of-political-institutions-dpi-2023).
- World Bank. *World Development Indicators*. The exact supplied WDI CSV is used by the notebook.