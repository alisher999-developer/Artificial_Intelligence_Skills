---
name: project-management
description: Plan, run, and close projects - scope, WBS, schedules, estimates, budgets, risks, stakeholders, agile and waterfall delivery, status reporting, and retrospectives. Use for project plans, roadmaps, sprint planning, risk registers, status reports, and rescuing troubled projects.
---

# Project Management Skill

## Core Principles
1. **Clarity of outcome.** A project exists to deliver a specific result by a date within constraints. Define "done" in measurable terms.
2. **Scope, time, cost, quality, and risk are linked.** Change one and the others move - make trade-offs explicit.
3. **Plan enough, not too much.** Detail near-term work; keep far-term work coarse and revisit.
4. **Surface bad news early.** Risks and delays are cheapest to handle when discovered early.
5. **People deliver projects.** Clear roles, communication, and motivated teams matter more than tools.
6. **Single accountable owner for every task and decision.**
7. **Inspect and adapt.** Review actuals vs plan regularly and adjust.
8. **Choose the method that fits the work.** Predictable work -> plan-driven; uncertain work -> iterative/agile; many cases -> hybrid.

## Phase 1 - Initiate
- **Business case:** problem/opportunity, benefits, cost, alternatives, strategic fit.
- **Project charter (1-2 pages):** objectives, scope in/out, deliverables, success criteria, milestones, budget, constraints, assumptions, key risks, sponsor, project manager, team, stakeholders, approval.
- **Stakeholder analysis:** power/interest grid; for each: needs, expectations, influence, current vs desired support, engagement plan.
- **Roles:** use RACI (Responsible, Accountable, Consulted, Informed) - exactly one **A** per item.
- Define the **governance**: decision rights, steering committee, escalation path, change control.

## Phase 2 - Plan

### Scope
- Write requirements with acceptance criteria. Distinguish must-have / should-have / could-have / won't-have (MoSCoW).
- **WBS (Work Breakdown Structure):** decompose deliverables into work packages (about 8-80 hours each). Plan by deliverable, not activity.
- Document what's **out of scope** and the **change control** process.

### Schedule
- List tasks -> sequence dependencies (finish-to-start, etc.) -> estimate -> assign -> identify the **critical path** (longest chain; zero float).
- Milestones: measurable checkpoints, not activities.
- Include buffers deliberately (contingency on critical-path or at project level), plus holidays, leave, and handoffs.
- Techniques: Gantt, network diagram, rolling-wave planning, kanban flow, release roadmap.

### Estimating
- Use multiple methods: analogous (past projects), parametric (units x rate), bottom-up (sum of tasks), three-point (PERT: (O + 4M + P) / 6), team-based (planning poker, T-shirt sizes, story points).
- Estimate with ranges and state confidence; track estimate accuracy over time.
- Beware optimism bias, anchoring, and the planning fallacy; add contingency for uncertainty and unknowns.
- Estimates come from the people doing the work.

### Budget
- Cost baseline: labor, vendors, tools, licenses, travel, training, contingency (risk-based), management reserve.
- Track committed vs actual vs forecast; cash-flow timing.

### Quality
- Define quality standards, acceptance tests, review/testing activities, and "definition of done."

### Resources
- Resource plan and loading chart; avoid sustained over-allocation (above ~80-85% utilization for planned work); identify skill gaps; plan onboarding.

### Communication Plan
- Who needs what information, how often, in what format, from whom (e.g., weekly status to sponsor, daily stand-up for team, monthly steering).

### Risk Management
1. **Identify:** brainstorming, assumptions review, pre-mortem, lessons learned, checklists, dependency scan.
2. **Assess:** probability x impact (1-5 scale) -> priority score; note proximity and detectability.
3. **Respond:** **Avoid, Mitigate, Transfer, Accept** (threats); **Exploit, Enhance, Share, Accept** (opportunities). Define triggers and contingency plans.
4. **Monitor:** review in every status cycle; retire, escalate, or add risks.
**Risk register columns:** ID, description (cause -> event -> impact), probability, impact, score, owner, response, trigger, status.
Also keep an **Assumptions log**, **Issues log** (risks that happened), **Dependencies log**, and **Decision log**.

## Phase 3 - Execute & Control

### Rhythm
- Kickoff meeting: goals, scope, roles, ways of working, plan.
- Weekly: status review, risk/issue review, upcoming milestones, decisions needed.
- Keep meetings purposeful: agenda, owners, decisions, action items with dates.

### Tracking & Metrics
- **Schedule:** planned vs actual milestones, % complete (use objective measures), critical path health, burn-up/burn-down, velocity, cycle time, throughput.
- **Cost:** budget vs actual vs forecast; **Earned Value Management:** PV, EV, AC -> SPI = EV/PV, CPI = EV/AC, EAC = BAC/CPI, VAC = BAC - EAC. SPI/CPI < 1 = behind/over budget.
- **Quality:** defects, rework, test pass rates, acceptance results.
- **Risk:** top risks, trend; **Stakeholder** sentiment; **Team** workload and morale.
- Use **RAG status** with defined thresholds and an explanation, not a mood. Don't hide Amber; Red must have a recovery plan and an ask.

### Change Control
- Any change to scope/schedule/cost goes through: request -> impact analysis (scope, time, cost, risk, quality) -> decision by the authorized approver -> update baseline and communicate.
- Protect against scope creep with a visible change log; say "yes, and here's the impact."

### Managing People & Stakeholders
- Set clear expectations, give context ("why"), remove blockers, protect the team from churn.
- Address conflict early, focus on interests and facts; escalate with options and a recommendation.
- Give regular, specific feedback; recognize contributions.
- Manage upward: no surprises, bring solutions, make decisions easy.

## Delivery Methods

### Waterfall / Predictive
Best when requirements are stable and change is costly (construction, regulated, hardware): Requirements -> Design -> Build -> Test -> Deploy -> Operate, with stage gates.

### Agile (Scrum)
- Roles: Product Owner (what/why, backlog priority), Scrum Master (process coach), Developers/team (how).
- Events: Sprint (1-4 weeks), Sprint Planning, Daily Scrum (15 min), Sprint Review (demo and feedback), Retrospective.
- Artifacts: Product Backlog, Sprint Backlog, Increment; **Definition of Done**.
- User stories: "As a [user], I want [capability] so that [benefit]" with acceptance criteria (INVEST: Independent, Negotiable, Valuable, Estimable, Small, Testable).
- Forecast with velocity ranges; keep sprints stable; refine the backlog continuously.

### Kanban
- Visualize workflow, **limit work in progress (WIP)**, manage flow (cycle time, throughput), make policies explicit, improve continuously. Great for support/ops and continuous work.

### Hybrid
- Plan-driven governance and budget + agile execution; fix dates/budget/outcomes, flex scope within the backlog.

### Product Roadmaps
- Outcome-oriented (Now / Next / Later), linked to goals and customer problems, not a fixed list of features with dates unless required.

## Phase 4 - Close
- Verify deliverables against acceptance criteria; obtain formal sign-off.
- Transition to operations: documentation, training, handover, support model, warranty.
- Release resources; close contracts and finances; archive records.
- **Lessons learned / retrospective:** what went well, what didn't, root causes, specific actions with owners.
- Benefits realization review after go-live: were the business-case benefits achieved?
- Celebrate and thank the team.

## Status Report Template
```
Project: <name>   Period: <dates>   Overall: GREEN/AMBER/RED
Summary: 2-3 sentences on where we are and what matters most.
Progress: milestones achieved / upcoming (with dates)
Schedule: on plan / variance and cause   Budget: spent vs forecast
Top risks & issues: description - owner - action - date
Decisions / help needed: what, from whom, by when
Next period priorities
```

## Troubled Project Recovery
1. Stop and assess: re-baseline facts (scope, status, true remaining effort, team health).
2. Confirm objectives and non-negotiables with the sponsor.
3. Reduce scope to the minimum viable outcome; defer extras.
4. Fix the root causes (unclear requirements, unrealistic estimates, resourcing, dependencies, decision latency).
5. Re-plan with realistic estimates and short feedback loops; increase transparency and cadence.
6. Communicate honestly with stakeholders; rebuild trust with early, small wins.

## Common Failure Causes
- Unclear goals or constantly shifting scope; no change control
- Optimistic estimates; no contingency
- Weak sponsor/stakeholder engagement; unclear decision rights
- Underestimated dependencies and integration work
- Overloaded teams and multitasking
- Late bad news; status that hides problems
- No owner for risks and actions
- Skipping retrospectives so mistakes repeat

## Checklist
- [ ] Charter with objectives, scope in/out, success criteria, sponsor
- [ ] Stakeholders mapped; RACI agreed
- [ ] WBS, schedule with critical path, and estimates with ranges
- [ ] Budget baseline with contingency
- [ ] Risk register with owners and responses; logs for issues, assumptions, decisions
- [ ] Communication plan and regular status rhythm
- [ ] Change control process in use
- [ ] Metrics (SPI/CPI or velocity/cycle time) tracked; honest RAG status
- [ ] Acceptance, handover, and lessons learned completed
