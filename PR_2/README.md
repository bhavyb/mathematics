# Derivable Judgement: A Statistical Decision-Making Model

A statistical decision-making project applying inferential statistics to a public-health dataset (1000 records) to determine which factors — smoking, age, gender, lifestyle — significantly affect disease occurrence (Diabetes, Hypertension).


## 🎯 Objective

To apply inferential statistics — hypothesis testing, confidence intervals, z-test, t-test, chi-square test, ANOVA, and correlation/covariance analysis — to health records data in order to derive data-backed judgements about factors influencing disease occurrence.

## 📘 Part A Explanation — Theoretical Foundation

Part A (`Part_A_Theory_Notes.pdf`)

1. **Inferential statistics** — how conclusions about a whole population can be drawn from a smaller sample, which is the core idea behind every test performed in Part B.
2. **Hypothesis testing** — the formal H₀/H₁ framework used to test claims (e.g., "does smoking affect diabetes?") against sample evidence rather than opinion.
3. **Confidence interval & critical value** — how a range of plausible values for a population parameter is calculated, and the cutoff point used to decide significance.
4. **p-value** — the probability of seeing the observed result if H₀ were true; the smaller it is, the less compatible the data is with H₀.
5. **Type I vs Type II errors** — the two ways a test decision can go wrong (false positive vs false negative), and why both matter when interpreting results.
6. **z-test, t-test, chi-square test, ANOVA** — brief descriptions of the four test types used later in Part B, and when each applies (sample size, data type, number of groups).
7. **Covariance** — direction of the relationship between two numeric variables.
8. **Correlation** — standardized strength and direction of that relationship, used in Part B to relate Age and BMI.

Together, these definitions justify every method choice made in Part B — e.g., using chi-square because smoking and diabetes are both categorical, or ANOVA because age has more than two groups.

## 📗 Part B Explanation — Data Analysis & Testing

Part B (`Part_B.ipynb`) applies the Part A concepts directly to `health_records.csv`:

- **Data loading & inspection** — the dataset is loaded, checked for shape, types, and missing values (none found), confirming it's clean enough for testing.
- **Hypotheses formulated** — two (extendable to three, see note above) testable claims are stated up front, so every subsequent test has a clear purpose rather than being run arbitrarily.
- **Confidence intervals** — 95% CIs are computed for six numeric variables (age, weight, BMI, blood pressure, cholesterol, glucose), giving a plausible range for each true population mean.
- **Critical value & p-value walkthrough** — using BMI split by gender as a worked example, the notebook shows both the critical-value method and the p-value method, and confirms they agree (Fail to Reject H₀).
- **z-test/t-test** — since the sample size is large (n ≥ 30), a z-test is used to formally compare mean BMI between males and females.
- **Chi-square test** — tests whether smoking status and diabetes diagnosis are independent or associated, directly answering Hypothesis 1.
- **ANOVA** — tests whether diabetes rate differs significantly across the five age groups, directly answering Hypothesis 2.
- **Covariance & correlation** — quantifies how Age and BMI move together, both in raw units (covariance) and standardized strength (correlation).
- **Result & interpretation** — every test ends with an explicit Accept/Reject H₀ decision and a one-line plain-English interpretation, so the statistical output is never left unexplained.


## 🧪 Hypotheses Tested

1. **H₀:** Smoking status has no effect on Diabetes prevalence. **H₁:** Smoking status affects Diabetes prevalence. → Tested via **chi-square test**.
2. **H₀:** Diabetes rate does not differ significantly across age groups. **H₁:** It does. → Tested via **one-way ANOVA**.
3. **H₀:** Mean BMI does not differ between males and females. **H₁:** It does. → Tested via **critical value / z-test**.


## 📈 Key Findings

| Test | Statistic | p-value | Decision |
|---|---|---|---|
| Confidence Intervals (age, weight, BMI, BP, cholesterol, glucose) | — | — | 95% CIs computed for all 6 variables |
| Critical value / Z-test — BMI: Male vs Female | Z = -0.4950 | 0.6206 | **Fail to Reject H₀** — no significant BMI difference by gender |
| Chi-square — Smoking vs Diabetes | χ² = 20.8283 (df=2) | < 0.0001 | **Reject H₀** — smoking and diabetes are significantly associated |
| ANOVA — Diabetes rate across Age Groups | F = 4.5213 | 0.0013 | **Reject H₀** — diabetes rate differs significantly by age group |
| Covariance / Correlation — Age vs BMI | Cov = 14.36, r = 0.2235 | — | Weak positive relationship |

**Conclusion:** Smoking status and age group are significantly associated with disease occurrence in this dataset, while gender shows no significant effect on BMI. Age and BMI show a statistically significant but weak positive correlation. Full working and interpretation is in `Part_B.ipynb`.
