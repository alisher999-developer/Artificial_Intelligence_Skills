---
name: science-research
description: Apply the scientific method and rigorous research practice - hypothesis formation, experimental design, statistics, reading and appraising papers, literature reviews, reproducibility, scientific writing, and communicating uncertainty. Use for any science, engineering, medical-literature, or data-driven research question.
---

# Science Research Skill

## Core Principles
1. **Falsifiability.** A good hypothesis can be proven wrong. Seek to disprove, not confirm.
2. **Evidence proportional to the claim.** Extraordinary claims require extraordinary evidence.
3. **Separate observation, inference, and speculation** - and label each.
4. **Uncertainty is information.** Report effect sizes with confidence intervals, not just "significant."
5. **Correlation is not causation** - causal claims require design (randomization, natural experiments, causal inference) plus mechanism and consistency.
6. **Reproducibility is the standard.** Methods, data, and code must allow others to repeat the work.
7. **Consensus over single studies.** Weigh the whole body of evidence; one paper rarely settles anything.
8. **Check current literature.** Fields move quickly - search for recent reviews and updates rather than relying on memory.
9. **Integrity above all.** No fabrication, no cherry-picking, full disclosure of limits and conflicts.

## The Research Cycle
1. **Observe / identify a gap** - what is unexplained or untested?
2. **Review literature** - what is known, what methods exist, what are the controversies?
3. **Formulate a precise question and hypothesis** (see below).
4. **Design the study** - methods, controls, sample, measures, analysis plan *before* seeing data.
5. **Collect data** with quality control and documentation.
6. **Analyze** per the pre-specified plan; label exploratory analyses as exploratory.
7. **Interpret** - alternative explanations, limitations, generalizability.
8. **Communicate** - paper, report, talk; share data/code.
9. **Replicate / iterate.**

## Formulating Questions & Hypotheses
- Use **PICO** (Population, Intervention, Comparator, Outcome) for clinical/behavioral questions; **PECO** for exposures.
- State **null (H0)** and **alternative (H1)** hypotheses; specify the direction, the measure, and the expected effect size.
- Define variables operationally (how exactly measured). Identify independent, dependent, confounding, mediating, and moderating variables.
- Good questions are specific, measurable, feasible, and important (FINER criteria: Feasible, Interesting, Novel, Ethical, Relevant).

## Experimental Design
- **Control groups** (placebo, sham, active, historical - state which and why).
- **Randomization** to remove selection bias; **blinding** (single/double/triple) to remove observer and participant bias.
- **Replication:** biological and technical replicates; know the unit of analysis (avoid pseudoreplication).
- **Sample size / power analysis** before collecting data: specify alpha (usually 0.05), power (>= 80%), and the smallest effect size of interest.
- **Confound control:** matching, stratification, blocking, covariate adjustment, crossover designs.
- **Measurement validity & reliability:** calibrated instruments, validated scales, inter-rater reliability, positive/negative controls.
- **Pre-registration** of hypotheses and analysis plan for confirmatory work.
- **Design types:** randomized controlled trial; cohort; case-control; cross-sectional; quasi-experimental (difference-in-differences, regression discontinuity, instrumental variables); simulation/computational; field observation.
- **Ethics:** institutional review (IRB/ethics committee), informed consent, animal welfare (3Rs: Replace, Reduce, Refine), data privacy, biosafety.

## Statistics - Essentials
- Describe first: plots, distributions, outliers, missing data, summary statistics (mean/SD or median/IQR).
- Match test to data: t-test/ANOVA (parametric), Mann-Whitney/Kruskal-Wallis (non-parametric), chi-square/Fisher (categorical), regression (relationships, adjustment), survival analysis (time-to-event), mixed models (clustered/repeated data).
- Check assumptions (normality, equal variance, independence, linearity); use robust or non-parametric methods when violated.
- **Report effect sizes + 95% CIs**, not just p-values. A p-value is *not* the probability the hypothesis is true.
- **Multiple comparisons:** correct (Bonferroni, Holm, FDR/Benjamini-Hochberg).
- **Avoid p-hacking, HARKing, optional stopping, and garden of forking paths.** Pre-specify; disclose all analyses run.
- Statistical significance != practical/clinical significance.
- Beware **regression to the mean, Simpson's paradox, survivorship bias, ecological fallacy, base-rate neglect.**
- Bayesian methods: state priors, report posterior intervals, run sensitivity to priors.
- Handle missing data deliberately (MCAR/MAR/MNAR; multiple imputation), not silently.
- Use code, set seeds, and version-control analyses.

## Evidence Hierarchy (generally, not rigid)
1. Systematic reviews / meta-analyses of high-quality RCTs
2. Randomized controlled trials
3. Prospective cohort studies
4. Case-control / retrospective cohort
5. Cross-sectional, case series
6. Case reports, mechanistic reasoning, expert opinion
Plus: animal and in-vitro studies inform mechanisms but don't establish human effects. Quality matters more than label - a poor RCT can be less informative than a strong cohort.

## Reading & Appraising a Paper
**Order:** title -> abstract -> figures/tables -> methods -> results -> discussion -> limitations -> references.
Ask:
- **Question:** clear and important? Hypotheses pre-specified?
- **Design:** appropriate controls, randomization, blinding? Sample size/power adequate?
- **Measures:** valid, reliable, objective? Primary outcome pre-defined?
- **Analysis:** right tests? multiple-comparison correction? missing data handled? effect sizes and CIs shown?
- **Results vs conclusions:** do the data actually support the claims? Any overreach (causal language from correlational data)?
- **Bias & confounding:** selection, measurement, attrition, publication, funding/conflicts of interest.
- **External validity:** who/what does this generalize to?
- **Reproducibility:** data/code available? Preregistered? Replicated by others?
- **Credibility:** peer-reviewed? Retracted/corrected? Journal quality (check predatory journals)? Preprint status?
Use tools like CONSORT (RCTs), STROBE (observational), PRISMA (reviews), ARRIVE (animal studies), GRADE (certainty of evidence), risk-of-bias tools (RoB 2, ROBINS-I).

## Literature Review / Systematic Review
1. Define the question (PICO) and inclusion/exclusion criteria.
2. Search multiple databases (PubMed, Web of Science, Scopus, arXiv/bioRxiv/medRxiv as appropriate, Google Scholar), using controlled vocabulary (MeSH) + keywords + Boolean operators; document the strategy and date.
3. Screen titles/abstracts, then full texts (ideally two independent reviewers); track a PRISMA flow diagram.
4. Extract data in a standard form; assess risk of bias.
5. Synthesize: narrative and/or meta-analysis (effect-size pooling, heterogeneity I^2, publication-bias checks such as funnel plots).
6. Grade certainty of evidence; state gaps and implications.
- Citation chaining: follow references backward and forward; find the most recent reviews first.

## Quantitative Sanity Checks
- **Dimensional analysis & units** on every calculation; carry units through.
- **Order-of-magnitude (Fermi) estimates** to catch absurd results.
- **Significant figures** reflect measurement precision.
- Propagate uncertainty (error propagation / Monte Carlo).
- Check limiting cases and conservation laws (mass, energy, charge).
- Compare results with known benchmarks/literature values.
- Recompute with an independent method or code.

## Reproducibility & Data Management
- Keep a lab notebook / analysis log; record parameters, versions, instruments, dates.
- Raw data immutable; scripted, version-controlled processing pipeline; fixed random seeds; environment files (requirements/conda/Docker).
- FAIR data: Findable, Accessible, Interoperable, Reusable; deposit in repositories (Zenodo, OSF, Dryad, GenBank, etc.).
- Share protocols, materials, and code; document with README and data dictionary.

## Scientific Writing (IMRaD)
- **Title:** specific, informative. **Abstract:** background, aim, methods, key results (with numbers), conclusion.
- **Introduction:** broad context -> gap -> objective/hypothesis (funnel).
- **Methods:** enough detail to replicate; materials, participants, procedures, statistics, ethics approvals.
- **Results:** report findings without interpretation; figures/tables that stand alone with clear captions; effect sizes and CIs; report null and negative results.
- **Discussion:** summarize main findings; compare with literature; mechanisms; limitations; implications; future work. Don't overstate.
- **References:** accurate and complete; cite primary sources; use a reference manager.
- Write clearly: short sentences, active voice where possible, defined terms, consistent units (SI), figures designed for readability and color-blind accessibility.
- Authorship per ICMJE/CRediT; disclose funding and conflicts.

## Peer Review (as reviewer or self-review)
Assess significance, novelty, validity of methods, support for conclusions, clarity, ethics, and data availability. Give constructive, specific, evidence-based comments, separating major concerns from minor points; recommend accept / minor / major / reject with justification.

## Communicating Science
- Lead with the finding and why it matters; use analogies and visuals.
- State confidence honestly: "strong evidence," "suggests," "preliminary," "no evidence of effect" (not the same as "evidence of no effect").
- Distinguish established science, emerging evidence, and hypotheses.
- Avoid hype; correct misconceptions without condescension; give absolute as well as relative risks.
- Cite sources; provide uncertainty ranges.

## Discipline Pointers
- **Medicine/Biology:** clinical vs statistical significance, absolute vs relative risk, NNT, biological plausibility, dose-response, model-organism limitations, confounding by indication.
- **Physics/Chemistry/Engineering:** calibration, systematic vs random error, error budgets, first-principles checks, simulation validation and verification.
- **Social science:** construct validity, sampling frame, WEIRD-sample generalization, causal identification strategy, replication crisis awareness.
- **Computer science/ML:** train/validation/test separation, leakage, baselines, ablations, multiple seeds and variance, compute/data disclosure, benchmark contamination.
- **Environmental/Earth science:** scale, spatial and temporal autocorrelation, model uncertainty and ensembles, attribution methods.

## Safety & Responsibility
- Help with understanding, analysis, and safe, legitimate study design. Do not provide protocols or technical uplift for creating weapons, pathogens, toxins, or other hazardous agents.
- For medical or health questions, give evidence-based information and encourage consultation with qualified professionals; do not diagnose individuals.
- Follow dual-use and biosafety norms; respect ethical review requirements.

## Red Flags in Claims & Studies
- No control group; tiny samples; single-center or single-study "breakthrough"
- Cherry-picked outcomes; unexplained subgroup findings; post-hoc hypotheses
- Causal language from observational data
- Conflicts of interest not disclosed; predatory journals; paper-mill signs
- Irreproducible, unavailable data; unusually perfect results
- Press release or headline stronger than the paper's abstract

## Checklist
- [ ] Clear, falsifiable question and hypothesis
- [ ] Design includes controls, randomization/blinding, adequate power
- [ ] Analysis plan pre-specified; assumptions checked; effect sizes with CIs reported
- [ ] Multiple comparisons addressed; exploratory results labeled
- [ ] Alternative explanations and limitations discussed
- [ ] Current literature and systematic reviews consulted
- [ ] Units, magnitudes, and calculations sanity-checked
- [ ] Data, code, and methods documented for reproducibility
- [ ] Claims proportional to the evidence; uncertainty communicated
- [ ] Ethics, conflicts of interest, and safety considered
