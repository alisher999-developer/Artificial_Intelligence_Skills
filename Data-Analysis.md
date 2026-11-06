---
name: data-analysis
description: Turn raw data into reliable, decision-ready insight - question framing, cleaning, exploration, statistics, visualization, and clear communication. Use for spreadsheets, CSVs, SQL results, dashboards, A/B tests, KPIs, and any "what does this data say?" request.
---

# Data Analysis Skill

## Core Principles
1. **Start with the question, not the data.** Define the decision the analysis supports and what answer would change it.
2. **Data quality first.** Every result inherits the flaws of its inputs. Validate before you analyze.
3. **Look before you model.** Plot and summarize before any test or model.
4. **Context makes numbers meaningful.** Compare to a baseline, a prior period, a benchmark, or a control.
5. **Be skeptical of surprising results.** First suspect a bug, a join error, or a definition problem.
6. **Reproducible by default.** Use scripts/queries, not manual edits; keep raw data untouched.
7. **Communicate the "so what."** Findings without a recommendation are trivia.

## Workflow
### 1. Frame
- Business question, decision-maker, deadline, success metric.
- Define metrics precisely (numerator, denominator, time window, filters, unit of analysis).
- Write hypotheses and what you'd expect to see if each is true.

### 2. Acquire & Understand
- Source, owner, refresh date, grain (what does one row represent?), key columns, known caveats.
- Check row count, column types, date range, and a data dictionary. Ask for one if missing.

### 3. Clean & Validate (log every change)
- **Duplicates:** exact and near-duplicate keys.
- **Missing values:** how many, where, why (random or systematic)? Drop, impute, or flag - state the choice.
- **Types & formats:** dates, currencies, units, text casing, whitespace, encodings, time zones.
- **Outliers:** investigate before removing; they are often real or an error worth reporting.
- **Consistency:** categories spelled differently, totals that don't sum, negative quantities, future dates.
- **Joins:** check row counts before and after; watch for fan-out (many-to-many) and dropped rows.
- **Reconcile** to a known total (finance ledger, official report) when possible.

### 4. Explore (EDA)
- Univariate: distributions, min/max, mean vs median, percentiles.
- Bivariate: correlations, group comparisons, cross-tabs, time trends.
- Segment: by cohort, channel, region, product, customer type. Averages hide segments (Simpson's paradox).
- Time: trend, seasonality, day-of-week effects, structural breaks, incomplete latest period.

### 5. Analyze
Match the method to the question:
| Question | Methods |
|---|---|
| What happened? | Descriptive stats, trends, breakdowns |
| Why did it happen? | Segmentation, decomposition (price/volume/mix), drill-down, cohort analysis |
| Do two groups differ? | t-test / Mann-Whitney, chi-square, confidence intervals, effect size |
| Did the change work? | A/B test, difference-in-differences, before/after with control |
| What drives Y? | Regression, feature importance, partial dependence (state limits) |
| What will happen? | Time-series forecast, regression, classification; validate out-of-sample |
| Who are similar? | Clustering, RFM segmentation |
| Where is the leak? | Funnel analysis, retention curves |

### 6. Validate
- Sanity-check magnitudes (Fermi estimate). Recompute one number a second way.
- Check sensitivity: do conclusions survive removing outliers, changing the date window, or changing the definition?
- Look for confounders, selection bias, survivorship bias, and look-ahead leakage.
- Separate **correlation from causation**; use causal language only with experimental or quasi-experimental design.

### 7. Communicate
- Lead with the answer; then evidence; then caveats; then recommendation and next steps.
- One chart per message; title states the insight; label axes and units; cite source and date.
- Quantify uncertainty (ranges, confidence intervals, sample size).
- Distinguish facts, inferences, and speculation.

## Statistics Essentials
- **Sample size matters.** Small groups produce noisy percentages - show n.
- **Statistical vs practical significance:** report effect size with CI, not only p-values.
- **Multiple comparisons:** more slices = more false positives; correct or pre-specify.
- **A/B tests:** pre-define metric, sample size, and duration; no peeking-and-stopping; check sample-ratio mismatch; consider novelty effects and segment interactions.
- **Averages:** use median for skewed data; show distribution.
- **Percent change vs percentage points;** CAGR for growth; weighted vs simple averages.
- **Base rates:** a 50% increase from 2 to 3 is not big.

## Visualization Rules
| Goal | Chart |
|---|---|
| Trend | Line |
| Compare categories | Sorted bar |
| Distribution | Histogram / box |
| Relationship | Scatter |
| Composition | Stacked bar (avoid pie beyond 3-5 slices) |
| Flow/steps | Funnel / waterfall |
- Zero-based bars; consistent scales; direct labels; muted colors with one highlight; no 3D or chart junk; color-blind-safe palettes.

## Tools Guidance
- **Excel/Sheets:** tables, named ranges, pivot tables, no hardcoded numbers in formulas, document assumptions.
- **SQL:** CTEs for readability, explicit joins, window functions for rankings/running totals, filter early, `EXPLAIN` for slow queries, never trust a join without checking counts.
- **Python (pandas/polars):** vectorize, avoid chained assignment, set seeds, notebooks for exploration and scripts for production, assert data expectations.
- **R:** tidyverse pipelines, tidy data principles.
- **BI tools:** certified metric definitions, single source of truth, performance-aware extracts.

## Report Template
1. **Answer / key finding** (1-2 sentences, with number)
2. **Why it matters / recommendation**
3. **Evidence** (3-5 charts or tables)
4. **Method & definitions** (short)
5. **Caveats & data quality notes**
6. **Next steps / open questions**

## Common Pitfalls
- Analyzing before defining the metric
- Silent join duplication; double-counting
- Comparing incomplete periods to full ones
- Cherry-picking time windows or segments
- Ignoring seasonality; trusting one noisy week
- Reporting means without distributions or n
- Overfitting; testing on training data
- Treating dashboards as truth without checking definitions
- Over-precision (e.g., 12.3456%) from noisy data

## Checklist
- [ ] Question, metric definitions, and decision stated
- [ ] Data source, grain, and date range understood
- [ ] Cleaning steps documented; joins verified
- [ ] Numbers reconciled and sanity-checked
- [ ] Comparisons have baselines; uncertainty shown
- [ ] Alternative explanations and biases considered
- [ ] Visuals are clear, labeled, and honest
- [ ] Clear recommendation and limitations
- [ ] Analysis reproducible (code/queries saved)
