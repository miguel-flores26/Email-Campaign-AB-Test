# Analysis Plan: Hillstrom Email Campaign Experiment

## Business question
Should the retailer send a merchandise email campaign, which version (men's or women's), and to which customers?

## Design
- 3 arms, randomized: Men's Email, Women's Email, No Email (control)
- Unit: customer. Outcomes measured over 2 weeks after send.

## Metrics
- Primary: conversion (purchase within 2 weeks)
- Secondary: visit (site visit), spend (dollars per customer)
- Guardrail: none available in data (unsubscribes would be a guardrail in practice)

## Hypotheses (for each email vs. control)
- H0: conversion rate equals control
- H1: conversion rate differs from control (two-sided)

## Tests
- Conversion, visit: two-proportion z-test, 95% CI on difference
- Spend: bootstrap CI (10,000 resamples) due to zero-inflated, skewed distribution
- Multiple comparisons: 2 primary comparisons, Bonferroni-adjusted alpha = 0.025 each

## Validity checks (run before analysis)
- Sample ratio mismatch: chi-square test vs. expected 1/3 split
- Covariate balance across arms for all pre-treatment variables

## Segment analysis
Exploratory only, not used for primary decision. 
Segments: newbie, channel, zip_code, purchase history (mens/womens).

## Decision rules
- Send an email if its conversion lift is statistically significant and positive at adjusted alpha.
- If not significant, report as inconclusive with the CI, not as "no effect."
- Targeting recommendations from segments require replication before being treated as confirmed.
