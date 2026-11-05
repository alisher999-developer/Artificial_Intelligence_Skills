---
name: financial-analytics
description: Perform rigorous financial analysis - statement analysis, ratios, valuation (DCF, comps), forecasting, unit economics, variance analysis, scenarios, and risk. Use for company analysis, investment research, budgeting, modeling, and business decisions involving numbers.
---

# Financial Analytics Skill

> **Important:** Provide analysis and education, not personalized investment, tax, or legal advice. State assumptions, show methods, give ranges, and note that the user should consult a licensed professional before acting. Never guarantee returns or predict markets with certainty.

## Core Principles
1. **Garbage in, garbage out.** Validate data before analyzing it.
2. **Current data must be looked up.** Prices, rates, multiples, filings, and guidance go stale - search and cite date and source.
3. **Every number needs context** - compared to what (history, peers, budget, benchmark)?
4. **Assumptions are the model.** Make them explicit, justified, and testable.
5. **Ranges beat point estimates.** Use scenarios and sensitivity analysis.
6. **Cash is fact; profit is opinion.** Always reconcile earnings to cash flow.
7. **Show the math** and make it reproducible. Check arithmetic by running it.

## Workflow
1. **Define the decision** - buy/sell, invest, price, budget, hire, raise capital, evaluate performance.
2. **Gather data** - primary sources: 10-K/10-Q/annual reports, earnings calls, investor presentations, central bank/statistical agency data, internal ledgers. Note period, currency, GAAP vs IFRS, restatements.
3. **Clean & validate** - consistent periods and units, one-offs identified, sums tie, balance sheet balances, no duplicates, outliers investigated.
4. **Analyze** - trends, ratios, drivers, peers.
5. **Model / value** - build forecast and valuation with scenarios.
6. **Stress-test** - sensitivities, downside case, what-would-have-to-be-true.
7. **Communicate** - conclusion first, evidence, risks, assumptions.

## Financial Statement Analysis
**Income statement:** revenue growth (organic vs M&A/FX), gross margin, operating margin, EBITDA/EBIT, net margin, effective tax rate, one-time items, stock-based comp, revenue recognition quality.
**Balance sheet:** liquidity, working capital, receivable/inventory build, debt maturity and covenants, off-balance-sheet items, goodwill/intangibles, leases, pension obligations.
**Cash flow:** operating cash flow vs net income, capex (maintenance vs growth), free cash flow, buybacks/dividends vs FCF, financing dependency.
**Tie the three statements together**: net income -> retained earnings; working-capital changes -> cash flow; capex -> PP&E; debt -> interest.

## Key Ratios (always interpret vs history & peers)
| Category | Ratios |
|---|---|
| Profitability | Gross/Operating/Net margin, ROE, ROA, ROIC, EBITDA margin |
| Liquidity | Current ratio, Quick ratio, Cash ratio |
| Leverage | Debt/Equity, Net Debt/EBITDA, Interest coverage (EBIT/Interest), Debt/Capital |
| Efficiency | Asset turnover, Inventory turnover, DSO, DIO, DPO, Cash conversion cycle |
| Growth | Revenue CAGR, EPS growth, FCF growth |
| Valuation | P/E, EV/EBITDA, EV/Sales, P/B, PEG, FCF yield, dividend yield |
| Cash quality | FCF/Net income, Accruals ratio, CFO/EBITDA |

**DuPont:** ROE = Net margin x Asset turnover x Equity multiplier - explains *why* ROE changes.

## Valuation
### DCF
- Forecast unlevered FCF = EBIT(1-t) + D&A - Capex - change in NWC, typically 5-10 years.
- Discount at WACC: E/(D+E)*Re + D/(D+E)*Rd*(1-t); cost of equity via CAPM = Rf + beta*(ERP).
- Terminal value: Gordon growth (g <= long-run nominal GDP, usually 2-3%) and/or exit multiple; cross-check each against the other.
- Enterprise value -> equity value: subtract net debt, minorities, preferred; add non-operating assets; divide by diluted shares.
- **Always:** show sensitivity table (WACC vs g, WACC vs exit multiple); report terminal value as % of EV (flag if > 75%); sanity-check implied multiples.

### Comparable Companies
- Select peers by business model, size, growth, margins, geography. Use consistent metrics (LTM/NTM, adjusted for one-offs).
- Use median, show range. Explain premiums/discounts.

### Precedent Transactions
- Control premium, synergies, timing/market conditions; treat as upper-bound reference.

### Other
- Sum-of-the-parts, LBO (for sponsor-style returns: IRR, MOIC), dividend discount, asset-based/liquidation, venture methods (use with caution).
- Triangulate with at least two methods; present a football-field range.

## Forecasting
- Driver-based (units x price, customers x ARPU, capacity x utilization) beats top-down growth guesses.
- Anchor to history, then justify changes. Check implied margins, reinvestment, and ROIC for realism.
- Build Base / Upside / Downside scenarios with explicit drivers and probabilities when reasonable.
- Backtest where possible; track forecast error (MAPE).
- Seasonality, FX, inflation, interest rates, and cyclicality should be modeled explicitly.

## Unit Economics & SaaS/Startup Metrics
CAC, LTV (gross-margin-adjusted), LTV/CAC (> 3 healthy), payback period, churn (logo & revenue), NRR/GRR, ARR/MRR bridge, gross margin, burn rate, runway, Rule of 40, magic number, contribution margin, cohort retention curves.

## Variance & Budget Analysis
- Actual vs Budget vs Prior Year: price/volume/mix/FX decomposition; fixed vs variable costs; one-offs vs run-rate.
- Explain *drivers* and *actions*, not just deltas. Flag materiality thresholds (e.g., > 5% and > $X).

## Risk Analysis
- Market risk: volatility, beta, Value-at-Risk (state method and confidence), drawdown, correlation.
- Credit, liquidity, interest-rate, FX, concentration, operational, regulatory risk.
- Sensitivity (one variable), scenario (multiple variables), stress (extreme but plausible), Monte Carlo (distribution of outcomes).
- Portfolio: diversification, risk-adjusted returns (Sharpe, Sortino), time horizon, liquidity needs.

## Time Value & Core Math Reminders
- PV = FV/(1+r)^n; NPV = sum of CF_t/(1+r)^t; IRR = rate where NPV = 0 (watch multiple IRRs, reinvestment assumption).
- Use real vs nominal consistently; after-tax cash flows; match discount rate to cash flow currency.
- CAGR = (End/Start)^(1/n) - 1. Percent change vs percentage points - don't confuse them.
- Compound rates: don't average percentages arithmetically; use geometric.

## Spreadsheet / Model Standards
- Separate **Inputs**, **Calculations**, **Outputs** (clear sheets/sections).
- Color convention: blue = inputs, black = formulas, green = links to other sheets.
- No hardcoded numbers inside formulas; one formula per row/column consistently.
- Built-in checks: balance sheet balances, cash ties, sums reconcile, error flags.
- Document sources and assumptions; version and date the model.
- Avoid circular references unless intentional; label units (000s, millions).
- Use scenario switches; build sensitivity tables.

## Red Flags (Quality of Earnings)
- Revenue growing faster than cash flow; rising receivables/DSO; inventory build-up
- Frequent "non-recurring" charges; aggressive non-GAAP adjustments
- Capitalizing costs that should be expensed; changes in depreciation/useful life
- Related-party transactions; complex structures; off-balance-sheet obligations
- Auditor changes/qualified opinions; restatements; late filings
- Debt maturing with weak coverage; covenant pressure
- Management compensation misaligned with long-term value

## Data & Sourcing Rules
- Look up current prices, rates, and filings; cite source and "as of" date.
- State fiscal year ends, currency, accounting standard, and whether figures are adjusted.
- Do not fabricate figures; if a number is unavailable, say so and provide a method to obtain/estimate it.
- Prefer filings and official statistics over aggregator sites; cross-check discrepancies.

## Output Format
1. **Bottom line** - conclusion and confidence (1-3 sentences)
2. **Key metrics table** (with period, peers/benchmark)
3. **Analysis** - drivers, trends, quality of earnings
4. **Valuation / forecast** - method, key assumptions, scenario range, sensitivity
5. **Risks & what would change the view**
6. **Assumptions & data sources** (with dates)
7. **Next steps / further diligence**
Charts when useful (trend lines, waterfall bridges, football field). Footer: "For informational purposes; not financial advice."

## Checklist
- [ ] Decision and time horizon defined
- [ ] Data validated and current (dated sources)
- [ ] Statements tie; one-offs normalized
- [ ] Ratios benchmarked to history and peers
- [ ] Cash flow reconciled with earnings
- [ ] Valuation triangulated; sensitivity shown
- [ ] Assumptions explicit and reasonable
- [ ] Downside and risks analyzed
- [ ] Arithmetic verified
- [ ] Disclaimer included; no guarantees
