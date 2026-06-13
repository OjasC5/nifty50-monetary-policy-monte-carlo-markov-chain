# Nifty 50 Monetary Policy MCMC

**Monetary Policy Regimes and Equity Market Dynamics in India:
A Markov Chain Monte Carlo Approach**

Independent research project | Ojas Chopra | Grade 12, CBSE | 2024–25

---

## Overview

This project builds a probabilistic forecasting framework that models
the relationship between RBI monetary policy regimes and Nifty 50
return distributions. Rather than predicting a single price path, the
framework generates a distribution of plausible market outcomes
conditioned on the current policy environment.

Three monetary policy regimes are identified — Easing, Neutral, and
Tightening — using a rolling-average classification of the RBI Repo
Rate. A first-order Markov chain models transitions between regimes.
A Monte Carlo simulation engine, conditioned on regime-specific return
distributions, generates 1,000 price paths over a 12-month horizon.

---

## Key Results

- Transition matrix diagonal entries exceed 0.90 for all three
  regimes, confirming strong policy persistence
- Zero observed direct Easing ↔ Tightening transitions — the Neutral
  regime acts as a mandatory intermediate buffer
- Likelihood Ratio homogeneity test (LR = 2.846, p = 0.828) validates
  stationarity of the transition matrix
- Out-of-sample terminal forecast error: 2.64% over a 3-year test
  window (Jan 2023 – Dec 2025)
- Realised Nifty 50 trajectory remained within the 90% prediction
  interval for all 36 months of the test period

---

## Methodology

| Step | Description |
|------|-------------|
| Regime Classification | Repo Gap = RepoRate(t) − MA12(t); thresholds ±25 bps |
| Transition Matrix | MLE frequency estimation from monthly regime sequence |
| Return Distributions | Regime-conditional mean and std dev of log returns |
| Monte Carlo Engine | 1,000 simulated paths; 5th–95th percentile prediction bands |
| Validation | Train: 2010–2022 / Test: 2023–2025, no look-ahead |
| Statistical Tests | LR homogeneity, ANOVA, Kruskal-Wallis, threshold sensitivity |

---

## Data Sources

- **Nifty 50:** National Stock Exchange of India —
  nseindia.com
- **Repo Rate:** RBI Database on Indian Economy (DBIE) —
  dbie.rbi.org.in

---

## Dependencies
python >= 3.8

numpy

pandas

matplotlib

scipy

Install with:
```bash
pip install numpy pandas matplotlib scipy
```

---

## Limitations

The framework has three known limitations that motivate future work:

1. Returns are drawn from normal distributions within each regime,
   despite observed negative skew and excess kurtosis — tail risk
   estimates are likely optimistic
2. The Tightening regime has only 28 observations; transition
   probability estimates carry meaningful parameter uncertainty not
   yet quantified via bootstrapping
3. No Markov order test comparing first-order to second-order
   specification

---

## Full Paper

Available on request.

---

*Part of an ongoing research project. Updates in progress.*
