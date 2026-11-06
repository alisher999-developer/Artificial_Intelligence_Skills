---
name: product-management
description: Product management end to end - discovery, customer research, strategy and vision, roadmapping, prioritization, PRDs and specs, working with engineering and design, launch, metrics, and iteration. Use for product strategy, feature decisions, roadmaps, requirements, and product analytics.
---

# Product Management Skill

## Core Principles
1. **Solve real customer problems in ways that work for the business.** Value (users), viability (business), feasibility (tech), and usability (design) must all hold.
2. **Outcomes over outputs.** Measure impact (behavior change, business results), not features shipped.
3. **Problem before solution.** Fall in love with the problem; hold solutions loosely and test them.
4. **Discovery and delivery are continuous and parallel.** Always be talking to customers while shipping.
5. **Evidence over opinion.** Decide with data, research, and experiments - while acknowledging uncertainty.
6. **Focus.** Saying no is the job; fewer, better bets beat a long feature list.
7. **Influence without authority.** Align stakeholders through clarity, context, and trust.
8. **Ship, learn, iterate.** Small increments reduce risk and speed learning.
9. **Be ethical.** Respect user privacy, avoid manipulative design, consider unintended consequences.

## 1. Product Strategy

### Vision & Strategy Stack
- **Vision:** the long-term change you want to create for customers.
- **Strategy:** the choices about target customers, problems, differentiation, and business model ("where to play, how to win").
- **Goals/OKRs:** measurable outcomes for the next quarter/year, tied to company objectives.
- **Roadmap:** the sequence of bets intended to reach the goals.
- **Backlog/Delivery:** the work to execute.
Each layer should logically connect to the one above it.

### Define Target Customer & Value Proposition
- Segment by needs and context (jobs-to-be-done), not just demographics.
- **Value proposition canvas:** customer jobs, pains, gains <-> your products, pain relievers, gain creators.
- Positioning: for [segment] who [problem], our product is [category] that [benefit], unlike [alternatives].
- **Competitive and market analysis:** direct and indirect competitors, substitutes (including spreadsheets and "do nothing"), differentiation, pricing, trends.

### Business Model & Metrics
- Revenue model (subscription, usage-based, marketplace, ads, licensing), unit economics (CAC, LTV, margin, payback), moats (network effects, data, switching costs, brand).
- **North Star Metric:** one metric reflecting delivered customer value and linked to revenue (e.g., weekly active teams completing X); supported by input metrics (acquisition, activation, engagement, retention, monetization).

## 2. Discovery

### Customer Research
- **Interviews:** 5-10 per segment to find patterns; ask about past behavior and context ("Tell me about the last time you..."), not hypotheticals; avoid pitching or leading; dig for the "why" behind actions; record and synthesize.
- **Other methods:** surveys (for sizing and validation, not discovery), support/sales call analysis, usage analytics, session recordings, field observation, diary studies, customer advisory boards.
- **Synthesize:** affinity map; jobs-to-be-done statements ("When [situation], I want to [motivation], so I can [outcome]"); personas grounded in evidence; journey maps; opportunity solution tree.

### Opportunity Solution Tree (Teresa Torres)
Desired outcome -> Opportunities (customer needs/pains) -> Solutions -> Assumption tests. Compare and choose among several opportunities and solutions, not just the first idea.

### Validate Before Building
Test the riskiest assumptions first:
- **Desirability:** will customers want it? (interviews, landing page/smoke tests, fake-door tests, prototypes)
- **Usability:** can they use it? (prototype tests)
- **Feasibility:** can we build it? (tech spikes, engineer input early)
- **Viability:** does it work for the business? (pricing tests, unit economics, legal, support, go-to-market)
- Prototype fidelity matches the question: paper/clickable mockups -> concierge/Wizard-of-Oz MVP -> coded MVP -> beta.
- Define success criteria before testing (e.g., "at least 6 of 10 users complete task X unaided").

## 3. Prioritization

### Frameworks (use as aids, not oracles)
| Framework | Use |
|---|---|
| **RICE** | Reach x Impact x Confidence / Effort - compare many items |
| **ICE** | Impact x Confidence x Ease - quick scoring |
| **Value vs Effort (2x2)** | Quick wins, big bets, fill-ins, money pits |
| **MoSCoW** | Scope control for a release: Must, Should, Could, Won't |
| **Kano** | Basic needs, performance needs, delighters |
| **Weighted scoring** | Explicit criteria and weights tied to strategy |
| **Opportunity scoring** | Importance vs satisfaction gaps |
| **Cost of delay (WSJF)** | Prioritize by urgency and value over job size |
- Prioritize **problems/outcomes** first, then solutions.
- Consider: strategic alignment, customer impact, revenue/retention effect, risk reduction, technical debt/platform health, dependencies, effort, and learning value.
- Reserve capacity (e.g., 70% roadmap bets / 20% quality & debt / 10% exploration).
- Make trade-offs visible: what are we **not** doing and why? Maintain a transparent decision log.
- Handle requests: capture the underlying problem, log it, look for patterns; don't commit to a solution because one loud customer asked.

## 4. Roadmapping
- **Outcome-based roadmap (Now / Next / Later):** themes tied to goals with the problem to solve, success metrics, and confidence level; avoid precise dates for uncertain work.
- Distinguish: strategic roadmap (executives/board), product roadmap (teams), release plan (delivery dates with commitment levels).
- Include dependencies, risks, and capacity.
- Communicate in language each audience cares about: customers (what problems we're addressing), sales (positioning and timing ranges), executives (outcomes and investment).
- Review and update regularly; roadmaps are hypotheses, not promises.

## 5. Defining the Product: Requirements & Specs

### PRD (Product Requirements Document) - keep it concise and living
1. **Summary & context:** problem, who it affects, evidence (data, quotes), why now.
2. **Goals & non-goals:** success metrics with baseline and target; explicitly out of scope.
3. **Users & use cases / user stories** with acceptance criteria.
4. **Solution overview:** user flows, wireframes/design links, key behaviors, edge cases, error/empty states, permissions, accessibility, localization.
5. **Functional and non-functional requirements:** performance, security, privacy, compliance, reliability, scalability, analytics/instrumentation.
6. **Dependencies & risks:** technical, legal, operational, go-to-market.
7. **Rollout plan:** feature flags, phased release, beta, migration, support readiness, documentation.
8. **Open questions & decisions log.**
9. **Measurement plan:** events, dashboards, experiment design, review dates.

### User Stories & Acceptance Criteria
- "As a [persona], I want [capability] so that [benefit]."
- **INVEST:** Independent, Negotiable, Valuable, Estimable, Small, Testable.
- **Acceptance criteria** in Given/When/Then format; include negative paths.
- Slice work **vertically** (thin end-to-end slices delivering user value) rather than by technical layers.

### Working With Engineering & Design
- Involve them early in discovery (the "product trio": PM, designer, tech lead) so feasibility and usability shape the solution.
- Share context and the "why," not just the "what"; let teams propose solutions.
- Run effective rituals: backlog refinement, sprint planning, demos, retrospectives, design critiques, technical design reviews.
- Respect technical constraints; plan for tech debt, reliability, and security work; make trade-offs explicit.
- Be available and decisive: unblock questions quickly; avoid scope churn mid-sprint.

## 6. Launch & Go-to-Market
- **Launch tiers:** define scale (silent, beta, GA, major launch) and match effort.
- **Cross-functional readiness:** engineering (quality, rollout, rollback), support (training, macros, FAQs), sales (enablement, pricing, objections), marketing (positioning, messaging, content, channels), legal/security/privacy, documentation, analytics, customer success.
- **Rollout strategy:** internal dogfood -> beta -> staged percentage rollout with feature flags -> GA; define go/no-go criteria and a rollback plan.
- **Pricing & packaging:** value-based, aligned with customer segments and willingness to pay; test; keep simple.
- **Communication:** release notes, in-product announcements, emails, demos; tell the customer-benefit story.
- **Post-launch:** monitor health metrics and feedback daily at first; fix critical issues quickly; review against success metrics at 2, 4, 8 weeks.

## 7. Metrics & Analytics
- **Frameworks:** AARRR (Acquisition, Activation, Retention, Referral, Revenue); HEART (Happiness, Engagement, Adoption, Retention, Task success); input/output metric trees.
- **Key metrics:** activation rate, time-to-value, DAU/WAU/MAU and stickiness, feature adoption, retention cohorts, churn, NPS/CSAT, task success, conversion, ARPU, expansion, support tickets, performance/reliability.
- **Instrumentation:** define events and properties up front; naming conventions; verify data before launch.
- **Experimentation:** hypothesis ("We believe X will cause Y for Z; we'll know by metric M improving by N"), sample size, duration, guardrail metrics; avoid peeking and p-hacking; interpret results with context; follow up with qualitative research.
- Beware vanity metrics, Goodhart's law (when a measure becomes a target it stops being a good measure), and survivorship bias.

## 8. Product Lifecycle & Portfolio
- **Early stage:** find product-market fit - strong retention, organic demand, willingness to pay; stay narrow; talk to users constantly.
- **Growth:** scale acquisition, onboarding, monetization, and reliability; build repeatable systems.
- **Mature:** optimize, defend, expand segments, platform extensibility, reduce cost-to-serve; prune low-value features.
- **Decline/sunset:** communicate early, migrate customers, honor commitments.
- **Technical debt & platform:** treat as investment with measurable payoff (velocity, reliability).

## 9. Stakeholder Management & Communication
- Map stakeholders (executives, sales, support, legal, finance, engineering, customers); understand each one's goals and concerns.
- **Align early, avoid surprises:** share drafts, hear objections, document decisions.
- Use clear narrative: problem -> evidence -> options -> recommendation -> trade-offs -> ask.
- Saying no: acknowledge the need, explain trade-offs and priorities, offer alternatives or a timeline for revisiting.
- Regular updates: what shipped, what we learned, what's next, risks, help needed.

## 10. PM Career & Craft Habits
- Block time for customers every week; read raw feedback and data; keep a decision journal.
- Write clearly - concise docs, one-pagers, strategy memos.
- Own the outcome, not just the process; be curious, humble, and data-informed.
- Build technical literacy (APIs, data, architecture basics) and business literacy (P&L, pricing, GTM).

## Deliverable Templates
**One-page product brief:** Problem - Customer - Evidence - Outcome/metric - Proposed solution(s) - Risks/assumptions - Out of scope - Plan - Decision needed.
**Experiment card:** Hypothesis - Assumption tested - Method - Success criteria - Sample/timeline - Result - Decision.
**Launch checklist:** Quality & rollback - Instrumentation - Support readiness - Sales/CS enablement - Marketing assets - Legal/privacy/security - Docs - Pricing - Comms schedule - Success review dates.
**Release note:** Headline benefit - Who it's for - How to use - Link to docs.

## Common Mistakes
- Building features from the loudest request without validating the problem
- Treating the roadmap as a commitment of dates and features
- Prioritizing by HiPPO (highest-paid person's opinion) or gut alone
- Long specs nobody reads; no acceptance criteria; ignoring edge cases
- Skipping instrumentation, then being unable to learn
- Shipping big-bang launches instead of incremental releases
- Ignoring tech debt, reliability, and support cost
- Optimizing metrics that don't reflect customer value
- Not talking to customers; relying on sales anecdotes only
- Failing to kill unsuccessful features

## Checklist
- [ ] Customer, problem, and evidence clearly articulated
- [ ] Goals and success metrics defined with baselines
- [ ] Riskiest assumptions tested before major investment
- [ ] Prioritization transparent, linked to strategy, with trade-offs recorded
- [ ] Concise PRD/stories with acceptance criteria and edge cases
- [ ] Design, engineering, and stakeholders aligned early
- [ ] Instrumentation and measurement plan in place
- [ ] Phased rollout, support/sales readiness, and rollback plan
- [ ] Post-launch review and iteration or sunset decision
