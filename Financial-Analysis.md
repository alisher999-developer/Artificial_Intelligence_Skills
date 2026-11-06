---
name: financial-analysis
description: Corporate finance and FP&A skill - budgeting, forecasting, variance analysis, cash flow management, investment appraisal (NPV/IRR/payback), break-even and pricing economics, working capital, and management reporting. Use for business finance decisions, budgets, board/finance reporting, and capital-allocation questions.
---

# Financial Analysis Skill (FP&A & Corporate Finance)

> Companion to a markets/valuation-focused financial-analytics skill. This one centers on **running the finances of a business**: planning, controlling, and deciding where to invest. Provide analysis and education, not personalized tax, legal, or investment advice; state assumptions and recommend a qualified professional for formal decisions.

## Core Principles
1. **Cash is king.** Profit matters, but liquidity keeps a company alive. Always connect P&L to cash.
2. **Decisions use incremental, forward-looking cash flows.** Ignore sunk costs; include opportunity costs and working capital.
3. **Drivers over line items.** Model the operational levers (volume, price, headcount, conversion), not just spreadsheets of totals.
4. **Ranges and scenarios.** Replace single-point forecasts with base/upside/downside and sensitivities.
5. **Consistency and traceability.** Definitions, periods, and sources documented; numbers reconcile to the ledger.
6. **Insight over reporting.** Explain *why* numbers moved and *what to do*.
7. **Materiality.** Spend effort where it moves the answer.

## Core Statements - Know How They Connect
- **P&L:** Revenue -> Gross profit -> EBITDA -> EBIT -> Net income.
- **Balance sheet:** Assets = Liabilities + Equity.
- **Cash flow:** Operating (net income + non-cash items +/- working capital) + Investing (capex, acquisitions) + Financing (debt, equity, dividends) = change in cash.
- **Links:** Net income -> retained earnings; capex -> fixed assets and depreciation; receivables/inventory/payables -> working capital -> operating cash flow; debt -> interest expense.
- Accrual vs cash accounting: recognize revenue and cost when earned/incurred; track timing differences.

## 1. Budgeting & Forecasting

### Annual Budget (Plan)
1. Start from strategy and targets (growth, margin, investment priorities).
2. Build the **revenue model** from drivers: customers x price x frequency; pipeline x win rate x deal size; capacity x utilization.
3. **Cost model:** COGS (variable), direct labor, S&M, R&D, G&A; separate fixed, semi-variable, and variable; headcount plan (start date, loaded cost, ramp).
4. **Capex and depreciation** schedule.
5. **Working capital:** DSO, DIO, DPO assumptions.
6. **Financing:** debt service, interest, equity, covenants.
7. Integrate into a three-statement model; check balance and cash ties.
8. Review top-down targets vs bottom-up build; reconcile gaps with explicit actions.
9. Approve, load, and set owners per budget line.

### Rolling Forecast
- Update monthly/quarterly (12-18 months ahead) with latest actuals; focus on key drivers; compare to budget and prior forecast; track forecast accuracy (MAPE/bias).
- **Zero-based budgeting:** justify every cost from scratch - use selectively (high-spend or bloated areas).
- **Scenario planning:** base, downside (revenue shock, cost inflation), upside; define triggers and pre-agreed contingency actions.

## 2. Variance Analysis
- Compare **Actual vs Budget vs Forecast vs Prior Year**, in absolute and %, with favorable/unfavorable labels.
- Decompose revenue variance: **Price, Volume, Mix, FX**. Cost variance: **rate (price) vs usage (efficiency)**; headcount vs salary level; timing vs permanent.
- Separate **one-offs/timing** from **run-rate** changes.
- Set materiality thresholds (e.g., > 5% and > $X).
- Commentary formula: **What moved -> Why (root cause) -> Is it permanent or timing? -> Impact on full-year outlook -> Action/owner.**
- Bridge/waterfall chart from budget to actual (or prior year to current).

## 3. Cash Flow & Liquidity Management
- **13-week cash flow forecast** (direct method: receipts and disbursements) updated weekly; plus a longer-term indirect forecast.
- **Working capital levers:**
  - DSO down: invoicing accuracy, terms, collections process, early-pay discounts.
  - DIO down: demand planning, safety stock tuning, SKU rationalization.
  - DPO up (responsibly): negotiate terms, payment run optimization without harming suppliers.
  - Cash conversion cycle = DSO + DIO - DPO.
- **Burn rate & runway** (startups): net burn per month; runway = cash / net burn; trigger decisions at 12/9/6 months.
- Liquidity buffers; covenant headroom; credit facilities; FX and interest-rate exposure.
- Cash is not profit: watch growth consuming cash (receivables/inventory build), capex, debt repayments, tax timing.

## 4. Investment Appraisal (Capital Budgeting)
**Method:** estimate incremental after-tax cash flows (including working capital changes and terminal/salvage value), discount at a risk-appropriate rate (WACC or project hurdle rate).
- **NPV** = sum of CF_t / (1 + r)^t - initial investment. Accept if NPV > 0; the best primary criterion.
- **IRR:** rate making NPV = 0; compare to the hurdle rate. Caveats: multiple IRRs with unconventional cash flows; reinvestment assumption; misleading for mutually exclusive projects of different scale - use NPV or MIRR.
- **Payback / discounted payback:** liquidity and risk lens; ignores cash flows after payback.
- **Profitability index** = PV of inflows / investment (capital rationing).
- **Equivalent annual annuity** to compare projects with different lives.
- Include: tax effects, depreciation tax shields, inflation consistency (real vs nominal), financing costs excluded from cash flows (captured in the discount rate), cannibalization, and opportunity cost.
- **Sensitivity and scenario analysis:** which assumptions swing NPV most? Breakeven values; Monte Carlo when inputs are uncertain.
- **Real options:** value flexibility (defer, expand, abandon) when relevant.
- **Lease vs buy, make vs buy, replace vs repair:** compare incremental after-tax cash flows or equivalent annual cost.

## 5. Unit Economics, Break-Even & Pricing
- **Contribution margin** = price - variable cost per unit. **Break-even units** = fixed costs / contribution margin per unit; margin of safety = (actual - break-even) / actual; operating leverage = contribution margin / operating profit.
- **Customer economics:** CAC, LTV (margin-adjusted), LTV/CAC, payback; cohort retention and revenue curves.
- **Pricing analysis:** cost-plus floor, competitor benchmarks, value-based ceiling; price elasticity; discount impact (a 10% price cut needs a much larger volume increase to preserve profit - compute it).
- **Product/customer profitability:** allocate costs sensibly (activity-based costing for overhead-heavy businesses); identify unprofitable segments.
- **Mix and capacity:** profit per constrained resource (e.g., per machine hour).

## 6. Capital Structure & Cost of Capital (essentials)
- WACC = E/V x Re + D/V x Rd x (1 - t); Re via CAPM: Rf + beta x ERP (plus size/specific premium if justified).
- Debt vs equity trade-offs: tax shield, financial distress risk, flexibility, covenants, dilution.
- Key leverage/coverage metrics: Net debt/EBITDA, interest coverage (EBIT/interest), fixed-charge coverage, debt service coverage (DSCR).
- Dividend/buyback policy depends on FCF, growth needs, and leverage targets.

## 7. KPI Dashboard (choose the vital few)
| Area | Examples |
|---|---|
| Growth | Revenue growth, bookings, ARR/MRR, new customers |
| Profitability | Gross margin, EBITDA margin, operating margin, contribution margin |
| Efficiency | Opex % revenue, revenue per employee, utilization, CAC payback |
| Cash & liquidity | Operating cash flow, free cash flow, cash balance, runway, CCC |
| Returns | ROIC, ROCE, ROE |
| Risk | Leverage, covenant headroom, customer concentration |
Each KPI: definition, formula, owner, target, frequency, data source.

## 8. Management & Board Reporting
- **Structure:** headline (1-3 sentences: performance vs plan, outlook, ask) -> KPI table -> P&L summary with variance -> cash and balance sheet -> forecast update -> risks/opportunities -> decisions needed.
- Use charts for trends and bridges; table for detail; commentary for insight.
- Reconcile to the general ledger; flag estimates, accruals, and data limitations.
- Consistent definitions of adjusted/non-GAAP metrics; reconcile to GAAP/IFRS when presented externally.

## 9. Month-End & Controls Awareness
- Close checklist: cut-off, accruals and prepayments, reconciliations (bank, AR/AP, intercompany), revenue recognition, depreciation, review of unusual entries, flux (variance) review.
- Internal controls: segregation of duties, approvals, audit trail, access limits.
- Fraud red flags: round-number entries, unusual vendors, missing documentation, override of controls.

## 10. Modeling Standards
- Separate **Inputs / Calculations / Outputs**; consistent formulas across rows; no hardcodes in formulas; color convention (blue inputs, black formulas); units labeled; checks (balance sheet balances, cash ties, sums reconcile); version control and change log; scenario selector; documented assumptions with sources and dates.
- Test the model: extreme inputs, sign checks, independent recalculation of key totals.

## Worked Mini-Examples (method reminders)
- **Discount trade-off:** Price $100, variable cost $60 (contribution $40). A 10% discount -> contribution $30. To keep total contribution constant, volume must rise by 40/30 - 1 = **33%**.
- **NPV quick:** Invest $100k; inflows $40k for 4 years at 10%: PV = 40 x 3.170 = $126.8k -> NPV = +$26.8k.
- **Runway:** Cash $600k, net burn $50k/month -> 12 months.
Always verify arithmetic by calculation before presenting.

## Common Mistakes
- Treating profit as cash; ignoring working capital and capex
- Including sunk costs or ignoring opportunity costs
- Mixing nominal cash flows with real discount rates
- Single-scenario budgets with hidden assumptions
- Hockey-stick revenue with flat costs; headcount cost without ramp or benefits load
- Variance reports that list numbers but not causes or actions
- Choosing projects by IRR alone
- Inconsistent metric definitions between teams

## Output Format
1. **Bottom line** and recommendation (with confidence)
2. **Key numbers** (table with period, comparison, variance)
3. **Drivers & analysis** (why numbers moved / what the model shows)
4. **Scenarios & sensitivities**
5. **Risks, assumptions, and data sources (with dates)**
6. **Actions, owners, and decisions required**
Footer: "For informational purposes; not financial, tax, or legal advice."

## Checklist
- [ ] Decision and horizon clear; metrics defined
- [ ] Data reconciled to source; periods and units consistent
- [ ] Three statements link; cash flow reconciled to profit
- [ ] Driver-based forecast with scenarios and sensitivities
- [ ] Incremental, after-tax, discounted cash flows for investments
- [ ] Variances explained (price/volume/mix, timing vs run-rate) with actions
- [ ] Liquidity, covenants, and risk reviewed
- [ ] Arithmetic verified; assumptions documented
- [ ] Clear recommendation and next steps
