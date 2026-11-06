---
name: workflow-automation
description: Identify, design, build, and maintain automated workflows - process mapping, automation candidates, no-code/low-code (Zapier, Make, n8n, Power Automate), scripts, APIs and webhooks, error handling, security, monitoring, and AI-assisted steps. Use for automating repetitive tasks, integrations, approvals, reporting, and data pipelines.
---

# Workflow Automation Skill

## Core Principles
1. **Understand the process before automating it.** Automating a bad process just produces bad results faster. Simplify and fix first.
2. **Automate the right things.** High frequency, rule-based, error-prone, time-consuming, and stable tasks pay back fastest.
3. **Start small, prove value, expand.** Pilot one workflow end to end, measure, then scale.
4. **Humans stay in the loop where judgment, risk, or exceptions matter.** Design clear handoffs and approvals.
5. **Design for failure.** Every automation must handle errors, retries, duplicates, and bad input gracefully and visibly.
6. **Secure by default.** Least-privilege credentials, secret storage, data minimization, audit logs.
7. **Make it observable and maintainable.** Logs, alerts, documentation, owners, version control.
8. **Measure ROI.** Time saved, error reduction, cycle time, cost, and satisfaction - not "it's cool."

## Step 1 - Find Automation Candidates
**Signals:** copy-paste between systems, repeated emails/reports, manual data entry, approvals that wait in inboxes, status updates, file renaming/moving, syncing records, alerts, onboarding checklists, invoice processing, lead routing, report generation.
**Score each candidate (1-5):**
| Factor | Question |
|---|---|
| Frequency | How often does it run? |
| Time per run | Minutes saved x frequency |
| Error cost | What does a mistake cost? |
| Rule clarity | Can the logic be written down? |
| Stability | Will the process and systems change soon? |
| Data availability | Are inputs structured and accessible (API/export/database)? |
| Risk/compliance | Are approvals, privacy, or audit required? |
**Priority** = (time saved + error reduction + strategic value) / (build effort + maintenance + risk). Estimate payback: build+maintenance hours vs hours saved per month.

## Step 2 - Map the Current Process
- Define: trigger, inputs, steps, decision points, outputs, actors, systems, exceptions, volumes, SLAs.
- Draw a **swimlane or flowchart** (start -> steps -> decisions -> end). Interview the people who do the work.
- Capture the **happy path** and the **top 5 exceptions** (missing data, duplicates, rejections, timeouts, out-of-hours).
- Eliminate steps (ESIA: Eliminate, Simplify, Integrate, Automate) before automating.
- Define the **desired future state** and success metrics.

## Step 3 - Choose the Approach
| Need | Good fit |
|---|---|
| Simple app-to-app triggers/actions | Zapier, Make, IFTTT, Power Automate, native integrations (Slack, Gmail, Sheets workflows) |
| Complex branching, self-hosting, data control | n8n, Node-RED, Temporal, Airflow/Prefect (for data pipelines) |
| Enterprise processes & approvals | Power Automate, ServiceNow, Workato, Camunda, Pega |
| Data transformation & pipelines | SQL/dbt, Python, Airflow, cloud functions, ETL/ELT tools |
| UI-only legacy systems | RPA (UiPath, Automation Anywhere, Power Automate Desktop) - fragile; prefer APIs where possible |
| Custom logic or scale | Scripts/services (Python, Node, Bash), serverless (AWS Lambda, Cloud Functions), cron/schedulers |
| Spreadsheet/Docs automation | Apps Script, Office Scripts, VBA (maintain carefully), formulas |
| Language/understanding steps | AI/LLM step for classification, extraction, summarization, drafting - with validation and human review |
- Prefer **API/native integrations** over screen-scraping/RPA; prefer **no-code** for simple flows, **code** when logic, scale, or reliability demand it.
- Consider cost per run/task, rate limits, vendor lock-in, data residency, and team skills.

## Step 4 - Design the Workflow
**Building blocks:** Trigger (event, schedule, webhook, form, email) -> Filter/conditions -> Actions (create, update, send, transform) -> Branches -> Loops -> Wait/delay -> Human approval -> Output/notification.

**Design rules**
- One workflow = one clear purpose; break big ones into modular sub-workflows.
- **Idempotency:** running twice must not create duplicates (use unique keys, "upsert," check-before-create).
- **Validate inputs** (required fields, formats, ranges) at the start; fail fast with a clear message.
- **Data mapping:** document field-to-field mappings, types, time zones, encodings, and units.
- **Naming & structure:** descriptive step names; consistent naming; annotated logic; keep configuration (IDs, thresholds, recipients) in one place, not hard-coded across steps.
- **Concurrency & ordering:** handle simultaneous triggers, rate limits, batching, and pagination.
- **Time:** schedule in a defined time zone; handle DST; avoid peak hours for heavy jobs.
- **Human-in-the-loop:** approval steps with clear context, deadlines, reminders, escalation, and an audit record; define what happens on timeout.
- **Fallbacks:** manual path when automation is down; kill switch/pause control.

## Step 5 - Error Handling & Reliability
- **Retries** with exponential backoff and jitter for transient errors (429/5xx/network); no retries for validation errors (4xx) - route to a review queue.
- **Dead-letter / exception queue:** failed items are stored with error and payload for review and replay.
- **Alerts:** notify the owner (Slack/email/pager) on failure thresholds with run link and context; avoid alert fatigue (aggregate, severity levels).
- **Timeouts & circuit breakers** to prevent runaway loops; limit loop iterations and spend (especially with paid APIs or AI calls).
- **Transactions & compensation:** if step 4 fails after step 3 wrote data, roll back or flag partial state.
- **Reconciliation:** periodic checks that source and destination match (counts, totals).
- **Rate limits/quotas:** monitor and queue.

## Step 6 - Security, Privacy & Compliance
- Store secrets in the platform's vault/secret manager - never in plain text steps, sheets, or code repos; rotate regularly.
- **Least privilege:** dedicated service accounts/API scopes; avoid using a person's credentials for production flows.
- Validate and sign webhooks (HMAC/secret tokens); restrict IPs where possible; use HTTPS.
- **Data minimization:** pass only needed fields; mask or avoid logging PII/credentials; follow retention rules.
- Respect compliance (GDPR/CCPA, HIPAA, SOX, PCI): know where data flows, vendor DPAs, regional storage.
- **Audit trail:** who/what/when for changes and for sensitive actions; change approval for production workflows.
- Be careful with email/messaging automations: consent, opt-outs, rate limits, and anti-spam rules.
- AI steps: protect against prompt injection from untrusted inputs (emails, web content); constrain tool permissions; validate outputs before acting; keep a human approval for irreversible actions (payments, deletions, external messages).

## Step 7 - Build, Test, Deploy
1. **Build in a dev/sandbox environment** with test data - never first-test on production records.
2. **Test cases:** happy path, empty/missing fields, duplicates, very large/small inputs, special characters/unicode, time zones, API failures/timeouts, permission errors, high volume.
3. **Dry-run/shadow mode:** run alongside the manual process and compare results before switching.
4. **Pilot** with a small group or low-risk subset; collect feedback.
5. **Deploy** with versioning, a rollback plan, and a communication note to affected users.
6. **Document:** purpose, owner, trigger, steps, mappings, dependencies, credentials used (names, not secrets), error handling, runbook for common failures.

## Step 8 - Monitor & Maintain
- Dashboards/logs: run counts, success rate, failures, latency, queue depth, cost.
- Alert on anomalies (zero runs when volume is expected, sudden spikes, repeated failures).
- Owner and backup owner; periodic review (quarterly): still needed? still correct? permissions current? API changes/deprecations?
- Handle schema and API changes; subscribe to vendor changelogs.
- Retire unused workflows; avoid "zombie automations."
- Track ROI against the baseline; share wins.

## Common Patterns & Recipes
- **Lead routing:** form -> enrich -> score -> assign owner (round-robin) -> CRM record -> Slack notification -> SLA timer.
- **Approval flow:** request form -> route by amount/department -> approver notification -> reminders -> decision logged -> downstream action -> requester notified.
- **Invoice/document processing:** email/attachment -> OCR/extraction -> validation -> human review for low-confidence -> post to accounting -> archive with metadata.
- **Reporting:** schedule -> query data -> transform -> populate sheet/dashboard -> send summary -> flag anomalies.
- **Onboarding:** new hire event -> create accounts -> assign tasks/training -> send welcome -> manager checklist -> reminders.
- **Data sync:** source change webhook -> map fields -> upsert -> log -> reconcile nightly.
- **Support triage:** ticket -> classify (rules/AI) -> prioritize -> assign -> auto-reply with knowledge-base link -> escalate on SLA risk.
- **Monitoring/ops:** health check -> threshold -> alert -> auto-remediate safe actions -> incident ticket.

## Scripting Quick Rules
- Use a language your team can maintain; keep scripts small, idempotent, and parameterized; read config from env vars.
- Log with timestamps and correlation IDs; exit codes meaningful; handle partial failures.
- Version control; code review; tests for core logic; dependency pinning; scheduled via cron/CI/orchestrator with alerting.
- Prefer official SDKs/APIs, respect rate limits and terms of service.

## Change Management & Adoption
- Involve the people who do the work; explain the benefit; train and support; address job-security concerns honestly by emphasizing higher-value work.
- Provide an easy way to report issues and request changes.
- Don't automate away the visibility people need - keep dashboards and notifications meaningful.

## Common Mistakes
- Automating an undefined or unstable process
- No error handling or alerting ("silent failures")
- Creating duplicates because workflows aren't idempotent
- Hard-coded secrets and shared personal credentials
- Over-complex mega-workflows nobody understands
- No owner, no documentation, no review cycle
- Skipping tests on realistic data; going live without a rollback
- Fully autonomous high-risk actions without approval or limits
- Ignoring maintenance cost and vendor/API changes

## Checklist
- [ ] Process mapped, simplified, and success metrics defined
- [ ] Candidate scored; ROI/payback estimated
- [ ] Right tool chosen (API/native > RPA; no-code vs code justified)
- [ ] Idempotent, modular design with input validation
- [ ] Retries, dead-letter queue, alerts, and kill switch in place
- [ ] Secrets in a vault; least-privilege; PII minimized; audit trail
- [ ] Tested on realistic and failure cases; piloted; rollback plan
- [ ] Documented with owner, runbook, and review schedule
- [ ] Monitoring and ROI tracking live
