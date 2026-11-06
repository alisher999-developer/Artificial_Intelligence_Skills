---
name: workflow-design
description: Design effective workflows and business processes before automating them - process discovery and mapping (BPMN, swimlanes, SIPOC), roles and handoffs, decision rules, state machines, SLAs, exceptions, human-in-the-loop and AI-agent steps, orchestration patterns, and continuous improvement. Use to design, redesign, document, or simplify any multi-step process.
---

# Workflow Design Skill

> Companion to the workflow-automation and automation skills. **This one is about designing the right process**; automation is about implementing it. Design first.

## Core Principles
1. **Outcome-first.** Define what the workflow must deliver, for whom, how fast, and at what quality.
2. **Simplify before you systematize.** Eliminate steps, handoffs, and approvals that don't add value.
3. **One owner per workflow, one owner per step.** Ambiguous accountability creates delays.
4. **Make state visible.** Everyone can see what's in progress, where it's stuck, and what happens next.
5. **Design for the exceptions.** The happy path is 20% of the design; the other 80% is edge cases, errors, and rework.
6. **Minimize handoffs and waiting.** Most elapsed time is queue time, not work time.
7. **Put judgment where it belongs.** Rules and routine to systems; ambiguity, empathy, and high-stakes decisions to people (with AI assist).
8. **Measure and improve.** A workflow without metrics can't get better.
9. **Fit the people.** Design with the people who do the work, not just for them.

## Step 1 - Define Purpose & Scope
- **Goal/outcome** (e.g., "approve vendor invoices within 3 business days with <1% error").
- **Boundaries:** trigger (start event) and end state(s); what's in and out of scope.
- **Customers & stakeholders:** who receives the output; who is affected; who approves; compliance owners.
- **Constraints:** policy/regulatory, systems, budget, volume, seasonality, skills.
- **Success metrics:** cycle time, throughput, quality/error rate, cost per transaction, SLA adherence, satisfaction, rework rate.

## Step 2 - Discover the Current Process ("as-is")
- Observe and interview the doers (not just managers); sample real cases including exceptions; collect volumes, timings, systems, and pain points.
- **SIPOC** (Suppliers, Inputs, Process (5-7 high-level steps), Outputs, Customers) for a one-page overview.
- Capture for each step: actor/role, action, inputs, outputs, system/tool, decision rules, time (touch time vs wait time), error types, and variation.
- Identify the **gap between documented and actual** process (workarounds, shadow spreadsheets).
- **Value-stream map:** value-added vs non-value-added vs necessary-but-non-value-added; process cycle efficiency = touch time / total lead time.

## Step 3 - Diagnose Problems
Look for the classic wastes (TIMWOODS + digital):
- **T**ransport/handoffs, **I**nventory/backlogs, **M**otion/switching tools, **W**aiting for approvals/info, **O**verproduction, **O**verprocessing/redundant checks, **D**efects/rework, **S**kills underused; plus duplicate data entry, unclear requirements, excessive approvals, and information hunting.
- Tools: 5 Whys, fishbone, Pareto of failure causes, bottleneck analysis (Theory of Constraints), queue/aging reports, volume x variability analysis.
- Quantify the biggest sources of delay and error before redesigning.

## Step 4 - Design the Future Process ("to-be")

### Design Heuristics (ESIA)
**Eliminate** non-value steps -> **Simplify** what remains -> **Integrate** systems and data -> **Automate** the routine.
- Parallelize independent steps; sequence only true dependencies.
- Reduce handoffs: give one person/team end-to-end responsibility where possible ("case ownership").
- Move decisions to the lowest competent level; replace blanket approvals with **risk-based thresholds** (auto-approve low risk; review high risk).
- Capture data once, at the source, validated at entry (right first time); pass structured data, not attachments.
- Standardize the common 80%; handle the long tail via an exception path.
- **Pull** rather than push where it reduces queues (work-in-progress limits, Kanban).
- Front-load checks that prevent downstream rework (eligibility, completeness, validation).

### Define Each Step (a step card)
- Name (verb + noun), owner/role, trigger/entry criteria, inputs, instructions/rules, tools, outputs/exit criteria, SLA, escalation path, and the "definition of done."

### Decision Logic
- Write rules explicitly as **decision tables** (conditions -> outcomes), with owners and effective dates; avoid hidden tribal rules.
- Separate **rule-based** (deterministic) decisions from **judgment-based** ones; note the data each needs.
- Define thresholds, delegated authority, and conflict-of-interest/segregation-of-duties rules.

### State Model
Represent the case lifecycle as a **state machine**: states (e.g., Draft -> Submitted -> In Review -> Needs Info -> Approved/Rejected -> Fulfilled -> Closed), allowed transitions, who/what triggers each, and entry/exit conditions. Prevent illegal transitions; make "stuck" states visible; include cancel/reopen.

### SLAs & Timers
- Target time per step and end-to-end; business-hours vs calendar; reminders, escalations, and auto-actions at defined thresholds; clear handling for pauses (waiting on customer).

### Exceptions & Error Paths
- Enumerate: missing/invalid information, duplicates, rejections, disputes, system outages, fraud/risk flags, urgent/priority cases, rework loops, cancellations, late changes.
- For each: detection, who handles it, how it's recorded, how it returns to the main flow, and how it's prevented in the future.
- Include a manual fallback (business continuity) and a way to reprocess failed items.

### Roles & Handoffs
- RACI per step; backup coverage; clear handoff content (what the next person needs, in a standard format); acknowledge-receipt rules; avoid "ownerless" queues.

### Human + AI + System Design
Decide who does each step: **System (deterministic)**, **AI assist (draft/classify/extract/summarize/recommend)**, **Human (judgment, accountability, empathy)**.
- AI steps: define inputs, expected output format, confidence thresholds, validation checks, fallback to human review on low confidence or high risk, audit trail, and feedback loop to improve.
- Keep humans accountable for decisions with material consequences; show the evidence and the AI rationale to the reviewer; sample and audit AI-handled cases.
- Protect privacy and treat untrusted content as data, not instructions.

## Step 5 - Notation & Documentation
- **Swimlane diagram** (lanes = roles/systems; steps left to right) is the workhorse; **BPMN 2.0** for formal modeling (events, tasks, gateways, sub-processes).
- Keep diagrams to one page; use sub-processes for detail; consistent naming (verb + object); show decision gateways with labeled outcomes; mark SLAs, systems, and exceptions.
- Supporting docs: SIPOC, step cards/SOP (standard operating procedure), decision tables, RACI, data dictionary/forms, KPIs, risk & control matrix.
- Version and date all process documents; name an owner and review cadence.
- Write SOPs in plain language with screenshots/checklists; keep them short and findable.

## Step 6 - Orchestration Patterns
| Pattern | Use |
|---|---|
| **Sequential** | Steps depend on previous outputs |
| **Parallel (fork/join)** | Independent tasks; join when all (or N of M) complete |
| **Conditional/branching** | Route by rules (value, risk, type) |
| **Approval chain / quorum** | Sequential or parallel approvers; thresholds |
| **Loop / rework** | Return for fixes with limits to prevent infinite cycles |
| **Event-driven** | React to events/messages rather than polling |
| **Scheduled/batch** | Time-based runs (reports, reconciliations) |
| **Saga / compensation** | Long transactions across systems with undo steps |
| **Human task + timer** | Wait for a person with reminders and escalation |
| **Sub-process / reuse** | Common modules (e.g., identity check) |
| **Dead-letter/exception queue** | Park failures for review and replay |
- Prefer **idempotent** steps and unique case IDs so retries don't duplicate work.
- Keep the process definition (what and when) separate from step implementations (how).

## Step 7 - Pilot, Implement, Transition
1. **Walk through** the design with the people who do the work using real cases (including nasty exceptions).
2. **Simulate** volumes and bottlenecks (simple queue math or spreadsheet) to check capacity.
3. **Pilot** with a limited scope; compare to baseline metrics; gather feedback.
4. **Train** and provide quick-reference guides; assign super-users.
5. **Roll out** in phases with a rollback option; communicate what changes, why, and who to ask.
6. **Hand over ownership**, dashboards, and a review schedule.

## Step 8 - Measure & Improve
- **Metrics:** cycle time and lead time (median and 90th percentile), throughput, work-in-progress and aging, first-pass yield/error rate, rework %, SLA compliance, cost per case, automation/straight-through rate, backlog, customer/employee satisfaction.
- Dashboards with drill-down to stuck cases; weekly ops review; monthly improvement review.
- Continuous improvement: PDCA (Plan-Do-Check-Act); Kaizen events; root-cause analysis of top defect types; retire steps that no longer add value.
- Watch for drift: workarounds reappearing, exceptions becoming normal (redesign the standard path), rules out of date.

## Controls, Risk & Compliance Built In
- Segregation of duties; approvals proportional to risk; audit trail of who did what, when, and why; retention rules; access by role; data privacy; evidence capture at the point of work rather than after the fact.
- Test controls (e.g., sampling) and document control owners.

## Design Patterns for Common Workflows
- **Intake & triage:** structured form -> validation -> auto-categorize -> route/prioritize -> acknowledge requester -> SLA timer.
- **Approval:** threshold-based routing, delegation when away, reminder/escalation, decision with reason, audit log.
- **Onboarding (customer/employee/vendor):** checklist of parallel tracks (accounts, compliance, training, intro), milestones, owner per track, completion gate.
- **Order-to-cash / procure-to-pay:** three-way match (PO/receipt/invoice), tolerance rules, exception queue, payment run.
- **Request fulfillment:** catalog -> eligibility -> approval -> provisioning -> confirmation -> closure survey.
- **Incident/issue management:** detect -> classify -> assign -> mitigate -> resolve -> review.
- **Content/creative review:** brief -> draft -> parallel reviews -> consolidated feedback -> revision -> final approval -> publish.

## Common Mistakes
- Automating the as-is mess instead of redesigning
- Designing only the happy path; no exception handling
- Excess approvals "just in case"; rubber-stamp reviews
- Unclear ownership; ownerless queues; silent handoffs by email
- Diagrams too detailed to read or too vague to use
- Designing in a conference room without the people doing the work
- No SLAs, no metrics, no feedback loop
- Rules living in people's heads rather than in decision tables
- Over-engineering for rare cases; forgetting change management
- AI steps with no confidence thresholds, validation, or human fallback

## Checklist
- [ ] Goal, trigger, end states, and metrics defined
- [ ] As-is observed with real cases; waste and bottlenecks quantified
- [ ] To-be eliminates/simplifies before automating; handoffs minimized
- [ ] Step cards, decision tables, RACI, and state model defined
- [ ] Exception paths, SLAs, escalations, and fallbacks designed
- [ ] Human vs system vs AI roles explicit; controls and audit trail included
- [ ] Walkthrough, pilot, and training completed
- [ ] Dashboard, owner, and improvement cadence in place
