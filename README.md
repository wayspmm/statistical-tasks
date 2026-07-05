# statistical-inference

Three end-to-end statistical inference case studies on real data:
hypothesis testing, Bayesian estimation and confidence intervals —
each with theory, simulation and a decision on real data.

## Projects

### 1. [Anomaly detection via Benford's law](benford-anomaly-detection/benford.ipynb)
Most-powerful **Neyman–Pearson test** for detecting fabricated numerical data:
$H_0$ — first digits follow Benford's law vs $H_1$ — uniform digits (fraud model).

- test statistic built directly from the log-likelihood ratio
- critical threshold and **power estimated by Monte Carlo** (actual type-I error matches nominal α = 0.05)
- power curve vs sample size: uniform "fakes" are caught almost surely at n ≈ 100–200
- applied to real data: world GDP figures (World Bank Open Data) — not rejected

The same pipeline applies to transaction audit and anti-fraud screening.

### 2. [Bayesian shrinkage: the Efron–Morris problem](bayesian-shrinkage/efron_morris.ipynb)
Classic 1970 baseball dataset: predict each player's true batting ability from
45 early at-bats.

- conjugate **Beta-Binomial model**; posterior mean as a shrinkage estimator toward the league average
- shrinkage cuts total squared prediction error several-fold vs the naive MLE (the James–Stein effect)
- prior strength κ as an explicit bias–variance dial; SSE(κ) curve
- equal-tailed **credible intervals**; posterior mean vs median under different losses

Same mechanics as CTR smoothing for new ads, ratings with few reviews, and mean-target encoding in ML.

### 3. [Confidence intervals: earthquake b-value](confidence-intervals/earthquakes.ipynb)
Gutenberg–Richter law: magnitudes above the completeness threshold are exponential.

- MLE for the b-value; **asymptotic vs exact (Gamma-pivot) confidence intervals**
- a case where asymptotic normality **fails at any n**: the completeness threshold
  M_c, whose MLE error is exponential — the symmetric interval systematically
  undercovers and even includes logically impossible values
- Poisson intensity of the event flow
- **Monte Carlo coverage check** of every interval as the final referee

## Data

Place the CSV files in `data/` (all from open sources):

| file | contents | source |
|---|---|---|
| `benford_data.csv` | world GDP by country-year; city populations | World Bank Open Data |
| `baseball.csv` | Efron–Morris 1970 dataset, 18 players | classic public dataset |
| `earthquakes.csv` | earthquake catalog (time, magnitude) | USGS |

## Setup

```bash
pip install -r requirements.txt
jupyter notebook
```
