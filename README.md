# Diagnosing Broken Confidence Intervals

## Objective

I examined why confidence intervals can look reasonable while failing to measure uncertainty correctly.

## Methodology

- I bootstrapped median age using 32,561 Adult Census observations and checked the BCa warning.
- I measured coverage for mean and median intervals in 400 lognormal experiments with 50 observations each.
- I compared worker and firm resampling using wages from 25 firms with 40 workers each, then checked coverage over 200 panels.
- I imported percentile, independent-observation and cluster bootstrap functions from `src/bootstrap_utils.py`.
- I revised an AI coverage-function prompt to specify consecutive integer seeds and compared its results with the existing simulation.
- I completed the optional variance-swap exercise, Bayesian-bootstrap comparison and moving-block bootstrap challenge.

## Key Findings

- Every age resample had median 37, giving a bootstrap SE of 0.000000. BCa returned nan with warnings because the statistic did not move in the jackknife calculation.
- Mean coverage was 92.5% for the parametric interval and 92.0% for the percentile bootstrap.
- Median coverage was 66.75% for the mean-based parametric interval and 92.75% for the median bootstrap. The mean-based interval targeted the wrong quantity.
- Resampling whole firms produced an interval 5.7 times as wide as resampling workers. Coverage improved from 19.5% to 91.0%, still below the nominal 95%.
- My revised coverage function matched both Diagnosis 3 results exactly: 19.5% and 91.0%.
- Swapping the firm and worker standard deviations reduced the width ratio to 2.3.
- The Bayesian and frequentist intervals for positive capital gains were similar at n = 500.
- On the persistent time series, the moving-block interval had width 0.797, compared with 0.307 for independent-period resampling.

## Files

- `lab_ch07_diagnostic.ipynb`: my answers, code and executed outputs.
- `src/bootstrap_utils.py`: the supplied bootstrap module used in the lab.

## AI use

I used Claude to help write the documentation and explanations. I used my own Python code alongside the code supplied in the lab.Claude did not generate any Python code for the work I submitted.
