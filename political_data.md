# Political Institutions and Governance in Bangladesh: Comparative Evidence from DPI 2023

## 1. Scope and purpose

This note interprets the saved outputs in `pol_data.ipynb` in the `bd_flying_geese` project. It is a descriptive, comparative reading of the notebook's results, not an independent assessment of current politics and not a normative ranking of countries.

The notebook uses the Database of Political Institutions (DPI) 2023 CSV and filters for a set of Asian countries. The resulting analysis covers **15 countries from 1975 through 2023**:

Bangladesh, Bhutan, India, Indonesia, Japan, Malaysia, Maldives, Nepal, Pakistan, the Philippines, Singapore, Sri Lanka, Taiwan, Thailand, and Vietnam.

The displayed dataset contains **735 country-year observations** (15 countries × 49 years), which is consistent with a balanced 1975–2023 panel for those 15 countries. Although the filter expression also names China and South Korea, neither appears in the resulting country list or outputs. They are therefore not part of the comparisons below.

All numerical statements in this note are taken from the notebook's saved outputs. Interpretations are deliberately limited to what those outputs can support.

## 2. Executive summary

The outputs portray Bangladesh over 1975–2023 as a country with:

- a relatively short average tenure for the political-system variable used in the notebook (4.83 years), compared with several countries in the sample;
- a recorded **14 country-years under military rule**, with the notebook identifying 1976–1990 as the first-to-last year range;
- a recorded military chief serving as defence minister in **12 years**;
- a high reported frequency of governing-party control over all relevant legislative houses: 34 years, or 87.18% of the non-missing observations used for that calculation;
- five years flagged by the dataset's election-fraud/irregularity indicator, equivalent to 12.20% of the non-missing observations for that variable;
- a most-frequent municipal-election category of “No local elections” and the same category for state/province-level elections;
- no recorded years of state/province authority under the notebook's `author` indicator and no recorded years of autonomous regions under `auton`.

Taken together, these results suggest a history combining periods of military involvement, changes in executive leadership and governing parties, substantial governing-party legislative control, and limited subnational electoral/devolution indicators as coded in this dataset. They do **not**, by themselves, establish the quality of elections, the degree of civil liberty, the independence of institutions, or the overall democratic character of Bangladesh.

## 3. Political leadership and system continuity

### 3.1 Executive and governing-party tenure

The notebook reports the maximum observed executive tenure and maximum governing-party tenure within the period:

| Country | Maximum executive tenure (years) | Maximum governing-party tenure (years) |
|---|---:|---:|
| Bangladesh | 10 | 15 |
| Bhutan | 36 | Not available |
| India | 11 | 30 |
| Indonesia | 31 | 35 |
| Japan | 9 | 38 |
| Malaysia | 22 | 44 |
| Maldives | 30 | 5 |
| Nepal | 8 | 7 |
| Pakistan | 11 | 5 |
| Philippines | 21 | 10 |
| Singapore | 24 | 57 |
| Sri Lanka | 12 | 17 |
| Taiwan | 47 | 72 |
| Thailand | 9 | 6 |
| Vietnam | 12 | 72 |

Bangladesh's maximum executive tenure of 10 years is below the maximum reported for Bhutan, Indonesia, Malaysia, Maldives, the Philippines, Singapore, and Taiwan, and close to the values reported for India, Pakistan, Japan, and Thailand. The maximum governing-party tenure of 15 years is also below the longest values reported for several countries, including India, Indonesia, Japan, Malaysia, Singapore, Taiwan, and Vietnam.

The minimum executive tenure is one year in every country in the table. The notebook reports a minimum governing-party tenure of one year for Bangladesh and most other countries; Bhutan's value is missing, while Singapore and Vietnam have higher reported minima (9 and 24 years respectively).

These are **maximum and minimum observed runs**, not averages and not measures of political stability by themselves. A long governing-party tenure can occur under different institutional arrangements, and a shorter executive tenure does not automatically imply stronger democratic accountability.

### 3.2 Average tenure of the political-system variable

The notebook labels its `tensys` summary as the average and maximum tenure of “autocratic or democratic systems.” It reports:

| Country | Average system tenure (years) | Maximum system tenure (years) |
|---|---:|---:|
| Bangladesh | 4.83 | 15 |
| Bhutan | 16.51 | 36 |
| India | 20.82 | 38 |
| Indonesia | 13.63 | 31 |
| Japan | 23.08 | 47 |
| Malaysia | 7.06 | 18 |
| Maldives | 13.49 | 30 |
| Nepal | 5.35 | 15 |
| Pakistan | 6.14 | 15 |
| Philippines | 14.35 | 31 |
| Singapore | 11.41 | 24 |
| Sri Lanka | 15.29 | 34 |
| Taiwan | 10.51 | 47 |
| Thailand | 4.96 | 13 |
| Vietnam | 4.73 | 12 |

Bangladesh's reported average (4.83 years) is among the lowest in this comparison: only Vietnam (4.73) is lower, while Thailand is close (4.96). Nepal and Pakistan are also relatively low. By contrast, India and Japan have the highest reported averages in this table.

This supports a narrow conclusion: **the notebook's system-tenure measure changes more frequently, on average, in Bangladesh than in most of the selected countries**. It should not be translated into a direct democracy score. The notebook does not provide a separate, validated democracy index or enough explanation of the `tensys` coding in the displayed outputs to justify that stronger interpretation.

## 4. Elections and recorded irregularities

### 4.1 Election counts

The notebook reports the following total election counts for 1975–2023:

| Country | Legislative elections | Executive elections |
|---|---:|---:|
| Bangladesh | 9 | 3 |
| Bhutan | 4 | 0 |
| India | 12 | 0 |
| Indonesia | 10 | 4 |
| Japan | 17 | 0 |
| Malaysia | 11 | 0 |
| Maldives | 8 | 9 |
| Nepal | 9 | 0 |
| Pakistan | 10 | 0 |
| Philippines | 14 | 7 |
| Singapore | 11 | 3 |
| Sri Lanka | 8 | 8 |
| Taiwan | 9 | 7 |
| Thailand | 13 | 0 |
| Vietnam | 10 | 3 |

Bangladesh has nine recorded legislative elections and three recorded executive elections in the notebook. The cross-country variation in executive-election counts is substantial. This should be interpreted in light of each country's institutional design: the absence of a separately recorded executive election does not mean that a country held no elections, and the counts should not be treated as directly equivalent across parliamentary and presidential systems.

The notebook also reports the most frequent election month and the number of distinct months recorded. Bangladesh's most frequent legislative-election month is February (month 2), with seven distinct months recorded. For executive elections, June (month 6) is the most frequent month, with three distinct months recorded. These month summaries describe the stored dates; they do not assess whether election timing was regular, competitive, or constitutionally appropriate.

### 4.2 Election fraud, intimidation, or irregularities indicator

The notebook groups the `fraud` variable and labels it “Election Fraud, Candidate Intimidation, or Irregularities.” Its outputs are:

| Country | Recorded years flagged | Proportion of non-missing observations flagged |
|---|---:|---:|
| Bangladesh | 5 | 12.20% |
| Bhutan | 0 | 0.00% |
| India | 3 | 6.12% |
| Indonesia | 0 | 0.00% |
| Japan | 0 | 0.00% |
| Malaysia | 0 | 0.00% |
| Maldives | 0 | 0.00% |
| Nepal | 0 | 0.00% |
| Pakistan | 6 | 15.38% |
| Philippines | 14 | 31.11% |
| Singapore | 0 | 0.00% |
| Sri Lanka | 6 | 12.24% |
| Taiwan | 0 | 0.00% |
| Thailand | 7 | 16.28% |
| Vietnam | 0 | 0.00% |

Bangladesh has five country-years flagged by this indicator. This is lower than the counts and proportions reported for the Philippines, Thailand, Pakistan, and Sri Lanka, and higher than the recorded values for India and the countries with zero flagged observations.

The appropriate interpretation is that **the DPI variable, as processed in the notebook, flags five Bangladesh observations**. A zero in this table means no observation was flagged in the available data; it should not be read as proof that no electoral irregularities occurred. The indicator also combines several concepts in the notebook's label, so it cannot distinguish fraud from intimidation or other irregularities without a more detailed variable-level analysis.

## 5. Legislature, governing parties, and opposition

### 5.1 Governing-party control of legislative houses

The notebook reports the following number and proportion of years in which the executive party controlled all relevant houses:

| Country | Years with all-house control | Proportion of non-missing observations |
|---|---:|---:|
| Bangladesh | 34 | 87.18% |
| Bhutan | 0 | 0.00% |
| India | 23 | 46.94% |
| Indonesia | 25 | 51.02% |
| Japan | 20 | 40.82% |
| Malaysia | 45 | 91.84% |
| Maldives | 4 | 26.67% |
| Nepal | 7 | 16.67% |
| Pakistan | 0 | 0.00% |
| Philippines | 20 | 44.44% |
| Singapore | 49 | 100.00% |
| Sri Lanka | 34 | 69.39% |
| Taiwan | 41 | 83.67% |
| Thailand | 13 | 27.08% |
| Vietnam | 49 | 100.00% |

Bangladesh's 87.18% is high within this sample: it is below Singapore and Vietnam (both 100%) and Malaysia (91.84%), but above the other listed countries. The reported 34 years correspond to 87.18% of the **39 non-missing observations** used in the proportion calculation, not 87.18% of all 49 calendar years.

This result indicates that the governing party was coded as controlling all relevant legislative houses in a large share of the years for which the variable is available. It does not establish that the legislature lacked independence, that opposition parties were absent, or that every election producing those legislatures was uncompetitive. Those questions require additional indicators.

### 5.2 Government and opposition representation

The notebook reports average government and opposition seat counts and vote shares. For Bangladesh, the reported averages are:

- Average total legislative seats: **237.65**
- Average government seats: **177.63**
- Average opposition seats: **57.98**
- Average government-party vote share: **8.40**
- Average opposition-party vote share: **3.89**

The corresponding averages vary considerably across the comparison countries. For example, the notebook reports an average government vote-share value of 85.71 and an average opposition vote-share value of 0 for Vietnam, while Singapore's values are 66.70 and 15.24. India, Indonesia, Japan, and Sri Lanka show larger average opposition vote-share values than Bangladesh in the displayed table.

These figures should be treated cautiously. The notebook does not explain the scale, denominator, aggregation convention, or treatment of elections and non-election years for `numvote` and `oppvote`. In particular, the Bangladesh values (8.40 and 3.89) should **not** be interpreted as ordinary election vote percentages without verifying the DPI variable definitions and the construction of these fields. Seat counts and vote-share values are different measures and should not be compared as though they were on the same scale.

The notebook also reports an average majority-margin value of **0.729** for Bangladesh, compared with 0.462 for Pakistan, 0.580 for Thailand, 0.590 for India, 0.673 for Sri Lanka, and 0.966–0.968 for Singapore and Vietnam. The variable's precise interpretation and scale are not explained in the saved output; therefore, this is best reported as the notebook's calculated mean rather than as a definitive measure of electoral competitiveness.

### 5.3 Ruling-party turnover and orientation

The recorded Bangladesh executive-party labels are:

- Awami League (AL): 17 observations
- Bangladesh Nationalist Party (BNP): 13 observations
- Independent: 5 observations
- Bangladeshi Peasants (abbreviated in the output as “Bang. Peasnt”): appears in the unique-party list

The party-orientation output lists both **Right** and **Left** for Bangladesh. This indicates that the notebook's coded ruling-party observations include both orientations during the period. It does not mean that the country's entire political system can be assigned one stable ideological label.

The same output lists multiple ruling-party labels for India, Indonesia, Japan, Malaysia, Nepal, Pakistan, the Philippines, Sri Lanka, Taiwan, and Thailand, while Singapore is listed as PAP and Vietnam as CPV. These differences in the number of recorded party labels reflect the dataset's party coding over time; they are not, by themselves, a ranking of political pluralism.

The notebook's “Average Age of Parties” section does **not** calculate average party age. Its code groups party observations and reports `Count_Party_Age`, which is a count, not a mean of `partyage`. No conclusion about average party age should be drawn from that output.

## 6. Military involvement in politics

### 6.1 Years coded as military rule

The notebook reports the following sums of the `military` indicator:

| Country | Recorded military-rule years |
|---|---:|
| Bangladesh | 14 |
| Bhutan | 0 |
| India | 1 |
| Indonesia | 34 |
| Japan | 0 |
| Malaysia | 0 |
| Maldives | 0 |
| Nepal | 0 |
| Pakistan | 19 |
| Philippines | 5 |
| Singapore | 16 |
| Sri Lanka | 0 |
| Taiwan | 0 |
| Thailand | 25 |
| Vietnam | 5 |

Bangladesh's 14 flagged years are fewer than the values reported for Indonesia, Thailand, and Pakistan, but higher than the values reported for the Philippines, Vietnam, and India. The notebook identifies Bangladesh's first and last flagged years as 1976 and 1990.

The output also reports that a military chief was defence minister in **12 Bangladesh country-years**. This is a separate indicator from military rule: the two should not be conflated. The corresponding counts are 30 for Indonesia, 32 for Thailand, 49 for Vietnam, 13 for the Philippines, and 8 for Pakistan.

These results support the conclusion that military involvement is a significant historical feature in the Bangladesh observations, especially in the earlier part of the panel. They do not imply that every year between 1976 and 1990 was a military-rule year.

### 6.2 Important duration-calculation issue

The notebook's “Military Rule: Year to Year and Duration” calculation defines duration as `max(year) - min(year)`. This is a **calendar-year span**, not a count of flagged years and not an inclusive duration. It can also include unflagged gaps between the first and last flagged observations.

For Bangladesh, the output gives 1976–1990 and a difference of 14, while the sum of the `military` indicator is 14. The equality here does not prove that every year in that interval was coded as military rule. Other countries' outputs show that the span and indicator sum can differ substantially (for example, Indonesia: 34 flagged years versus a 1975–2014 span; Thailand: 25 versus 1978–2023).

Accordingly, this note uses the **sum of the military indicator** as the number of recorded military-rule years and reports first-to-last years only as a range. The notebook's `Duration` column should not be used as an exact duration measure without checking the year-by-year observations.

## 7. Regional authority, local elections, and autonomous regions

### 7.1 State/province authority

The notebook's `author` summary reports zero years for Bangladesh and Bhutan, while it reports 49 years for India, 39 for Malaysia, 39 for Nepal, 32 for the Philippines, and smaller recorded totals for Indonesia and Japan. Several countries do not appear in the printed table, indicating that the output does not provide a complete country-by-country comparison for this variable.

For Bangladesh, the result is that **no year is coded as having state/province authority over taxing, spending, or legislating** in the available observations. This is consistent with a centralized structure under the particular indicator used. It should not be generalized into a complete description of administrative decentralization: the notebook's output does not measure every form of local government authority or public-service devolution.

### 7.2 Autonomous regions

The notebook reports no years with an autonomous region for Bangladesh. It also reports zero for Bhutan, India, Japan, Malaysia, Maldives, Nepal, Singapore, Sri Lanka, Taiwan, Thailand, and Vietnam. Positive totals are reported for Indonesia (24 years), Pakistan (47 years), and the Philippines (34 years).

Thus, Bangladesh has no recorded autonomous-region years under the notebook's `auton` variable, unlike those three countries. This is a specific institutional indicator, not a measure of ethnic inclusion, regional inequality, or the strength of local administration.

### 7.3 Local elections

The most frequent municipal-government category for Bangladesh is **“No local elections.”** The same category is reported as the maximum municipal-election level. The state/province-level output also reports “No local elections” for Bangladesh.

Several comparison countries are coded as having locally elected municipal legislatures, and some as having both locally elected legislatures and executives. For state/province governments, India, Japan, Malaysia, Pakistan, the Philippines, and Sri Lanka have at least one locally elected level in the output, although the most frequent category and maximum category differ by country.

This is a notable difference in the notebook's coding of subnational electoral institutions. However, it must be read as the DPI categories returned by this particular extraction and aggregation. The notebook does not show the underlying year-by-year municipal and state observations, so this result should be checked against the source data's codebook before being presented as a definitive statement about the actual existence or conduct of local elections in Bangladesh.

## 8. What the comparison says about Bangladesh

Within this selected Asian-country panel, the notebook's results place Bangladesh in a mixed institutional profile:

1. **System-tenure measure:** Bangladesh has one of the lowest average values for `tensys` (4.83 years), suggesting more frequent changes in the coded system-tenure variable than in most comparison countries.
2. **Military involvement:** Fourteen years are flagged under the military-rule indicator, and the defence-minister/military-chief overlap is recorded in 12 years. This is less than the totals reported for Indonesia, Pakistan, and Thailand in some measures, but remains a substantial part of Bangladesh's historical record in the panel.
3. **Legislative concentration:** The executive party is coded as controlling all relevant houses in 34 years, or 87.18% of the non-missing observations. This is high relative to most of the comparison countries, though below Singapore, Vietnam, and Malaysia.
4. **Electoral irregularity indicator:** Five years are flagged for Bangladesh. The reported proportion (12.20%) is below the Philippines, Thailand, and Pakistan, and close to Sri Lanka. The indicator cannot establish the full extent or nature of electoral problems.
5. **Subnational institutions:** The notebook records no state/province authority years, no autonomous-region years, and “No local elections” as the municipal and state/province category for Bangladesh. These results point toward limited subnational authority and electoral representation under the variables used, but need verification against the original variable definitions and year-level data.

A neutral researcher would therefore describe Bangladesh, on the basis of these outputs, as having experienced **historical military involvement, relatively short average tenure in the notebook's system-tenure measure, strong governing-party legislative control in many observed years, and limited recorded subnational electoral/devolution indicators**. The outputs also show changes in ruling-party labels and both left- and right-oriented ruling-party classifications over the period.

This is a descriptive characterization, not a verdict on Bangladesh's political legitimacy or democratic quality. The notebook does not provide enough evidence to make claims about freedom of expression, judicial independence, civil liberties, media freedom, political violence, public trust, corruption, or the fairness of every election. It also does not provide a single comparable democracy score for all countries.

## 9. Data and interpretation limitations

The following limitations are important before using these results in a research paper or policy discussion:

- **Country coverage:** The resulting panel contains 15 countries, not every country named in the filter expression. China and South Korea do not appear in the output.
- **Time coverage:** The displayed observations cover 1975–2023. Conclusions should not be extended to years after 2023 or described as a snapshot of the present political situation.
- **Indicator coding:** The saved outputs do not reproduce the complete DPI codebook. Labels such as `military`, `fraud`, `author`, `auton`, `allhouse`, and `tensys` should be checked against the official definitions before stronger substantive claims are made.
- **Missing observations:** Some summaries use `dropna`, and their proportions therefore use only non-missing observations. A printed zero is not interchangeable with missing data.
- **Election-system comparability:** Executive-election counts are not directly comparable across parliamentary and presidential systems.
- **Vote-share calculations:** The scale and denominator for `numvote` and `oppvote` are not explained in the notebook output. Their reported means should not be treated as conventional vote percentages without validation.
- **Majority margin:** The notebook reports means and maxima for `maj`, but does not explain its scale or precise substantive meaning in the output.
- **Military-rule duration:** The first-to-last-year difference is not a valid count of flagged years where the indicator has gaps. Use the indicator sum for the count.
- **Party age:** The section labelled “Average Age of Parties” outputs counts, not average ages.
- **Religious affiliation:** The most-frequent `execrel` value is printed as 0 for every country. This is not sufficient evidence that all executives had no religious affiliation; it may represent a code for unavailable, unreported, or not-applicable information.
- **Local-election categories:** The municipal and state/province outputs should be checked against the DPI codebook and year-level records before making categorical claims about the actual conduct of local elections.
- **No causal inference:** These descriptive summaries do not establish that any one institutional feature caused economic performance, political stability, or development outcomes.

## 10. Recommended checks before further analysis

To strengthen the political-institutions component of the wider study:

1. Add a variable dictionary for every indicator used, including its original DPI definition, valid values, and missing-value codes.
2. Verify Bangladesh's year-by-year values for `military`, `defmin`, `fraud`, `allhouse`, `author`, `auton`, `muni`, and `state`.
3. Recalculate military-rule duration as the sum of the binary indicator, and separately identify contiguous episodes if episode duration is required.
4. Correct the party-age aggregation so it actually calculates a mean or median of `partyage` rather than a count.
5. Document the denominators and units for government/opposition vote-share variables and the majority-margin variable.
6. Report the number of non-missing observations beside every country-level proportion.
7. Consider separating parliamentary and presidential systems when comparing executive elections and executive tenure.
8. Keep conclusions explicitly bounded to 1975–2023 and to the 15 countries present in the processed panel.

---

**Research note:** This document is based exclusively on the saved outputs and calculations in `pol_data.ipynb`. It does not introduce external political events, news accounts, or independent country assessments. Where the notebook's outputs are ambiguous or potentially affected by coding choices, the uncertainty is stated rather than resolved through assumptions.


## 11. Updated EDA and hypothesis-led panel results

This section incorporates the subsequently saved outputs from the expanded EDA in `pol_data.ipynb`. It supplements the descriptive interpretation above and **supersedes any earlier preliminary panel-test figures**. The panel remains the same 15 countries and 735 country-year observations for 1975–2023. No WDI or economic variables are included.

### 11.1 Panel coverage and data quality

The expanded EDA confirms a balanced country-year structure: each of the 15 countries contributes 49 observations. However, variable-level coverage differs considerably:

| Variable | Non-missing observations | Missing (%) |
|---|---:|---:|
| `auton` | 733 | 0.3 |
| `execnat` | 732 | 0.4 |
| `yrsoffc` | 732 | 0.4 |
| `tenlong` | 732 | 0.4 |
| `tensys` | 732 | 0.4 |
| `military` | 732 | 0.4 |
| `tenshort` | 732 | 0.4 |
| `execrlc` | 731 | 0.5 |
| `checks` | 722 | 1.8 |
| `stabs` | 711 | 3.3 |
| `stabns` | 711 | 3.3 |
| `fraud` | 702 | 4.5 |
| `defmin` | 685 | 6.8 |
| `allhouse` | 662 | 9.9 |
| `govfrac` | 633 | 13.9 |
| `polariz` | 625 | 15.0 |
| `frac` | 624 | 15.1 |
| `maj` | 623 | 15.2 |
| `prtyin` | 566 | 23.0 |
| `oppfrac` | 522 | 29.0 |
| `author` | 291 | 60.4 |
| `herftot` | 59 | 92.0 |

The large missingness in `author` and especially `herftot` makes these variables weak candidates for a common-sample panel model without a careful missing-data strategy. The descriptive statistics and annual country plots in the notebook provide additional distributional and time-pattern checks; plotted lines are not interpolated across missing observations.

### 11.2 Ruling-party orientation in the valid ideology sample

Only valid `Left`, `Center`, and `Right` labels are treated as substantive ideology categories. The EDA's country-by-orientation table records Bangladesh as **4 Right observations and 1 Left observation**, with no Center observations. The valid ideology sample is uneven across countries: for example, Vietnam has 49 Left observations, Japan 36 Right and 2 Left, India 34 Left and 15 Right, and Taiwan 46 Right and 3 Left.

This distribution is a warning against treating the ideology variable as a complete, balanced country classification. In Bangladesh, the five valid observations are a very small basis for generalizing about the entire 1975–2023 period. The panel regressions' ideology estimates use 11 countries and around 308–319 observations depending on the outcome.

### 11.3 Test 1 — Ruling-party ideology and political outcomes

**Null hypothesis (H₀):** After controlling for country and year fixed effects, the Left and Center coefficients are jointly zero relative to Right orientation.

**Alternative hypothesis (H₁):** At least one orientation coefficient differs from zero.

The test uses two-way fixed-effects OLS with standard errors clustered by country. Only valid ideology labels are included. The updated saved results are:

| Political outcome | N | Countries | Joint Wald statistic | Joint p-value | Reject H₀ at 5%? |
|---|---:|---:|---:|---:|---|
| `tensys` | 319 | 11 | 25.1090 | <0.0001 | Yes |
| `yrsoffc` | 319 | 11 | 24.1154 | <0.0001 | Yes |
| `checks` | 313 | 11 | 26.7612 | <0.0001 | Yes |
| `stabs` | 308 | 11 | 3.7191 | 0.1557 | No |
| `polariz` | 313 | 11 | 11.6497 | 0.0030 | Yes |

The joint test detects an association between the ideology categories and four of the five political outcomes, but not `stabs`. The coefficient estimates are relative to the Right category. For example, the Center coefficient is negative and statistically significant for `tensys` (-4.3022, p = 0.0094) and `yrsoffc` (-1.2782, p < 0.0001). The Left coefficient is positive for `tensys` (2.7647, p = 0.0604) but does not reach the 5% threshold; it is positive and significant for `checks` (2.0108, p = 0.0001). These signs should not be given a substantive direction until the DPI scales and coding are verified.

The updated ideology result for `stabs` is **not significant** (p = 0.1557). This supersedes the earlier preliminary figure of 0.0549 that appeared in the first draft of the notebook analysis.

### 11.4 Test 2 — Military involvement, electoral irregularities, and legislative concentration

**Null hypothesis (H₀):** The coefficients on `military`, `fraud`, and `allhouse` are jointly zero after controlling for country and year fixed effects.

**Alternative hypothesis (H₁):** At least one of the three political indicators is associated with the outcome within the panel.

Updated two-way fixed-effects results:

| Political outcome | N | Countries | Joint Wald statistic | Joint p-value | Reject H₀ at 5%? |
|---|---:|---:|---:|---:|---|
| `tensys` | 652 | 15 | 9.6177 | 0.0221 | Yes |
| `yrsoffc` | 652 | 15 | 13.8804 | 0.0031 | Yes |
| `checks` | 644 | 15 | 12.7605 | 0.0052 | Yes |
| `stabs` | 641 | 15 | 32.3157 | <0.0001 | Yes |
| `polariz` | 548 | 15 | 21.9353 | 0.0001 | Yes |

The three predictors are jointly associated with all five outcomes at the 5% level in these saved models. This is a joint test: it does not imply that all three predictors are individually significant in every regression.

At the individual-coefficient level, `fraud` is significant for `yrsoffc` (coefficient 2.3718, p = 0.0066), `checks` (-1.1210, p = 0.0222), and `stabs` (-0.0683, p = 0.0015). `allhouse` is significant for `checks` (-1.2712, p = 0.0061) and `polariz` (-0.4892, p < 0.0001). The `military` coefficient does not reach the 5% threshold for any of these five outcomes in the reported regressions. Several other coefficients are close to, but do not cross, the conventional 5% threshold; they should not be described as statistically significant.

### 11.5 Test 3 — Within-country political deviations

**Null hypothesis (H₀):** The selected political predictors have no joint association with within-country changes in the DPI outcome after country and year fixed effects.

**Alternative hypothesis (H₁):** The predictors are jointly associated with at least one within-country political outcome.

The country fixed effects account for time-invariant differences between countries; year fixed effects account for common year shocks. Since the joint tests in Test 2 reject H₀ for all five outcomes, the saved results provide evidence that the selected political indicators covary with within-country deviations in each of the five measured political outcomes.

This does **not** mean every country experienced the same deviation, that the deviation had the same sign, or that these predictors caused it. The design estimates pooled within-country associations across the selected panel. Country-specific event analysis would be needed to identify which countries and years account for the pooled patterns.

### 11.6 Updated interpretation and candidate variables for the later WDI merge

The expanded EDA strengthens the case for retaining a small set of political indicators for subsequent economic analysis, but it does not yet show an economic effect. Based on the current political-only results:

- `execrlc` is a relevant ideology candidate, but Bangladesh has only five valid observations in the displayed orientation table and the ideology model covers 11 countries. This is a major coverage limitation.
- `fraud` and `allhouse` show individual associations with some political outcomes in the updated fixed-effects models.
- `military` is conceptually important and has high coverage, but its individual coefficients are not statistically significant at 5% in these five reported outcome models. Its joint contribution alongside the other predictors should not be mistaken for individual significance.
- `tensys`, `yrsoffc`, `checks`, `stabs`, and `polariz` are the current political outcomes used in the screening regressions. Whether any should become explanatory variables in an economic model depends on the research question and their validated codebook definitions.
- `herftot` and `author` have substantial missingness and should not be prioritized without addressing coverage.

Variable selection for the WDI merge should not be based on p-values alone. The next stage should verify each DPI definition and coding direction, assess within-country variation and multicollinearity, consider alternative model specifications, and define an economically meaningful outcome and lag structure before estimating political-economic relationships.

### 11.7 Inference and scope limitations

1. There are only 15 country clusters in the institutional models and 11 in the ideology models. Cluster-robust p-values with so few clusters are approximate; borderline results require particular caution.
2. The complete-case sample changes across outcomes, so sample sizes and country coverage must always accompany the results.
3. The `polariz` outcome has three observed categories (0, 1, 2); OLS is exploratory for this coded outcome. An ordinal or other suitable model should be considered as a robustness check.
4. The fixed-effects design controls for country-invariant characteristics and common year shocks, but not all time-varying confounders.
5. The reported associations are not causal effects. Reverse relationships and omitted time-varying factors remain possible.
6. No WDI variables have been merged. These tests do not answer whether political ideology or political institutions improve or harm economic performance.

**Updated research conclusion:** the saved political panel outputs show statistically significant within-country associations between the selected institutional indicators and all five tested political outcomes. The ideology tests are significant for four outcomes, with no statistically significant joint association for `stabs`. These findings identify candidate variables and political deviations for further study; they do not yet demonstrate political effects on economic performance.
