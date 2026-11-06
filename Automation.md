---
name: automation
description: Engineer reliable automation - scripts and scheduled jobs, CI/CD pipelines, infrastructure and IT automation, APIs/webhooks/event-driven integrations, RPA, data pipelines, testing, secrets, idempotency, observability, and maintenance. Use for building, hardening, and operating automated systems end to end.
---

# Automation Skill (Engineering & Operations)

> Companion to **workflow-design** (decide *what* the process should be) and **workflow-automation** (no-code/low-code platforms and candidate selection). This skill covers **how to build and run automation reliably**: code, schedulers, pipelines, integrations, and operations.

## Core Principles
1. **Automate what is understood, stable, and repeated.** Manual first, document second, automate third.
2. **Idempotent and re-runnable.** Running a job twice should produce the same end state, not duplicates or damage.
3. **Fail loudly, recover gracefully.** Silent failures are the worst kind; every failure should be visible, diagnosable, and recoverable.
4. **Small, composable, testable units.** Many simple scripts/steps beat one giant monolith.
5. **Configuration over hard-coding; secrets never in code.**
6. **Least privilege and blast-radius control.** Automation runs with power - constrain it.
7. **Observability is part of the build.** Logs, metrics, and alerts ship with the automation.
8. **Treat automation as software.** Version control, review, tests, documentation, owners.
9. **Humans stay in control of risky actions.** Dry-run, approvals, and kill switches.
10. **Automate the automation's upkeep** - dependency updates, certificate/credential rotation, drift detection.

## Step 1 - Decide What to Automate (quick scoring)
- Frequency x time per run x error cost x stability x clarity of rules. Estimate payback: (build + maintain hours) vs (hours saved).
- Prefer official APIs, webhooks, and CLIs over UI scraping. Use RPA only when no API exists, and isolate it as fragile.
- Define success: time saved, error reduction, throughput, uptime, cost.

## Step 2 - Pick the Right Tool
| Need | Options |
|---|---|
| One-off or small local tasks | Shell (Bash/PowerShell), Python, Node |
| Scheduled jobs | cron, systemd timers, Windows Task Scheduler, Kubernetes CronJob, cloud schedulers (EventBridge, Cloud Scheduler), GitHub Actions `schedule` |
| CI/CD | GitHub Actions, GitLab CI, Jenkins, CircleCI, Azure DevOps, Argo, Tekton |
| Infrastructure & config | Terraform/OpenTofu, Pulumi, CloudFormation/Bicep, Ansible, Packer, Kubernetes manifests/Helm/GitOps (Argo CD, Flux) |
| Event-driven/serverless | AWS Lambda, Azure Functions, Cloud Functions/Run, queues (SQS, Pub/Sub, RabbitMQ, Kafka), webhooks |
| Workflow orchestration | Airflow, Prefect, Dagster, Temporal, Step Functions, n8n, Zapier/Make, Power Automate |
| Data pipelines | SQL/dbt, Spark, Python, Fivetran/Airbyte, Airflow |
| Business-app glue | Zapier, Make, n8n, Power Automate, Apps Script, Office Scripts |
| Browser/UI automation (last resort) | Playwright, Selenium, RPA suites |
| Personal/home | Shortcuts, IFTTT, Home Assistant |
- Choose by team skills, reliability needs, volume, cost, data sensitivity, and maintainability.

## Step 3 - Script Design Standards
- **Structure:** parse args/config -> validate -> do work in functions -> report results -> exit with meaningful code.
- **Bash:** `set -euo pipefail`; quote variables; use `trap` for cleanup; avoid parsing `ls`; shellcheck; keep to simple glue (switch to Python when logic grows).
- **Python/Node:** virtual environments/lockfiles; type hints; `argparse`/`click` or equivalent; structured logging; timeouts on every network call; no bare `except`.
- **Idempotency techniques:** upsert instead of insert; unique keys/dedup tokens; check-then-act inside transactions; write to temp then atomic rename; "ensure state" semantics (create if missing).
- **Concurrency safety:** lock files/advisory locks/leases to prevent overlapping runs; handle partial runs.
- **Dry-run flag** (`--dry-run`) showing intended changes without executing; verbose/debug mode.
- **Parameterize** environments (dev/stage/prod); avoid hard-coded paths, IDs, or URLs.
- **Time:** use UTC internally; explicit time zones for schedules; account for DST.
- **Portability:** document OS/tool versions; containerize when dependencies are complex.
- **Safety:** confirm before destructive operations; validate inputs (paths, IDs) to prevent wiping the wrong target; never run `rm -rf` on unvalidated variables.

## Step 4 - Scheduling & Triggers
- **Triggers:** time-based, event-based (file arrival, webhook, message queue, database change, commit/PR), manual (button/command), dependency completion.
- Prefer **event-driven** over polling when possible; if polling, use sensible intervals with backoff and conditional requests (ETags/`since`).
- **Schedulers:** define overlap policy (skip, queue, or kill), catch-up/backfill policy for missed runs, timeouts, and retries.
- **Cron hygiene:** log output, set `PATH`/env explicitly, use absolute paths, write to a lock, send failures to alerts; consider "dead-man's switch" monitoring (alert when a job *doesn't* check in).
- Stagger heavy jobs; avoid top-of-the-hour pile-ups; respect API rate limits and maintenance windows.

## Step 5 - CI/CD Pipelines
- **Pipeline stages:** checkout -> install (cached) -> lint/format -> unit tests -> build -> security scans (SAST, dependency, secrets, container, IaC) -> integration/e2e tests -> package/sign -> deploy to staging -> smoke tests -> approval (for prod) -> deploy to prod -> post-deploy verification -> notify.
- **Principles:** fast feedback (fail early, parallelize, cache); reproducible builds (pinned versions, lockfiles, containers); build once, promote the same artifact through environments; trunk-based development with small PRs; protected branches and required checks.
- **Deployments:** blue/green, canary, or rolling with automated health checks and **automatic rollback**; feature flags to decouple deploy from release; database migrations backward-compatible (expand/contract).
- **Security:** least-privilege pipeline credentials; OIDC/short-lived tokens instead of long-lived secrets; pin third-party actions/plugins by version/SHA; protect secrets from untrusted forks/PRs; sign artifacts and generate SBOMs.
- **Quality gates:** coverage thresholds, lint rules, vulnerability thresholds, performance budgets.
- **Observability:** pipeline duration, failure/flakiness rates, DORA metrics (deployment frequency, lead time, change failure rate, MTTR).
- Fix or quarantine flaky tests promptly.

## Step 6 - Infrastructure & IT Automation
- **Infrastructure as Code:** declarative definitions in version control; code review for changes; plan/preview before apply; remote state with locking; modules for reuse; separate environments/accounts; policy-as-code (OPA, Sentinel, Checkov, tfsec) for guardrails; tag resources; cost controls.
- **Configuration management:** idempotent playbooks/roles (Ansible, etc.); immutable images (Packer) for fleets; avoid snowflake servers.
- **GitOps:** Git is the source of truth; controllers reconcile cluster/infrastructure state; drift detection and auto-remediation with alerts.
- **Self-service and runbooks as code:** turn common ops tasks (provision user, rotate cert, restart service, scale) into tested scripts or pipelines with approvals and audit logs.
- **Patching & lifecycle:** automated OS/dependency updates (Renovate/Dependabot), staged rollouts, maintenance windows.
- **Backups & DR:** automated, monitored, and **restore-tested** regularly.
- **Identity automation:** joiner-mover-leaver provisioning via SCIM/IdP; periodic access review reports.

## Step 7 - Integrations: APIs, Webhooks & Events
- **Read the API docs for:** auth, rate limits, pagination, idempotency keys, error codes, versioning, webhooks/signing.
- **Authentication:** OAuth 2.0 / service accounts with scoped permissions; token refresh handling; rotate credentials.
- **Reliability patterns:**
  - Retries with **exponential backoff + jitter** for 429/5xx/timeouts; don't retry non-idempotent calls without idempotency keys; don't retry 4xx validation errors.
  - **Timeouts** on every call; **circuit breakers** for failing dependencies.
  - **Pagination and batching**; respect rate-limit headers.
  - **Webhooks:** verify signatures, respond fast (2xx) then process asynchronously via a queue, deduplicate by event ID, handle out-of-order and replayed events.
  - **Outbox/inbox patterns** and **dead-letter queues** for guaranteed delivery and poison-message handling.
  - **Reconciliation jobs** to detect and fix drift between systems.
- **Data mapping:** document field maps, types, time zones, encodings, units; validate schemas (JSON Schema/pydantic) at boundaries.
- **Versioning & change:** pin API versions; monitor deprecation notices; contract tests for critical integrations.

## Step 8 - Data & Reporting Automation
- ELT/ETL with raw -> staged -> modeled layers; incremental loads with watermarks; schema-change handling; data-quality tests (not-null, unique, accepted values, freshness, row-count anomalies); lineage and documentation.
- Reports: parameterized queries, reproducible definitions, scheduled delivery with links to the source, anomaly flags, and ownership.
- Protect PII: masking, least-privilege access, retention.

## Step 9 - RPA / Browser Automation (when no API exists)
- Use stable selectors (data attributes/accessible roles) not brittle XPaths/coordinates; explicit waits instead of sleeps; handle pop-ups, MFA, and session expiry; run in isolated, monitored environments with dedicated bot accounts.
- Respect site terms of service and robots rules; avoid scraping personal data without a lawful basis; throttle requests.
- Add screenshots/traces on failure; maintain selectors as UIs change; plan the migration to an API when available.

## Step 10 - Testing Automation
- **Unit tests** for logic and parsers; **integration tests** against sandboxes/mocks/contract stubs; **end-to-end** in staging with realistic data; **failure-injection** (timeouts, 500s, malformed data, duplicates, partial failures).
- Test idempotency (run twice), concurrency (overlapping runs), and rollback.
- Use test fixtures and anonymized production-like data; never test destructive actions on production first.
- Shadow/parallel runs against the manual process to compare outputs before cutover.

## Step 11 - Security & Secrets
- Secrets in a vault/secret manager (not repos, plain env files, logs, or chat); inject at runtime; rotate on schedule and on exposure; scan repos/pipelines for leaked secrets.
- Dedicated **service accounts** with minimal scopes; no personal credentials in production automation; separate credentials per environment.
- Sanitize inputs used in shell commands/SQL (avoid injection); avoid `eval`; pin and verify dependencies; use signed images; restrict network egress.
- Audit trails: who/what ran, with which inputs, and what changed.
- For AI-assisted automation: treat external content as untrusted data, constrain tool permissions, validate outputs before acting, and require human approval for irreversible actions.

## Step 12 - Observability & Operations
- **Logging:** structured (JSON), timestamps (UTC), correlation/run IDs, levels, no secrets/PII; searchable and retained appropriately.
- **Metrics:** success/failure counts, duration, queue depth, retry counts, throughput, cost; SLOs for critical automations.
- **Alerting:** on failures, missed runs (dead-man's switch), SLA breaches, anomalies; route to an owner with context and run links; avoid alert fatigue with severity and deduplication.
- **Runbooks:** how to diagnose, re-run safely, roll back, and escalate; known failure modes.
- **Ownership:** named owner and backup; on-call or support path; documented purpose and dependencies.
- **Lifecycle:** periodic review (quarterly) of usefulness, permissions, dependencies, and costs; deprecate and remove dead automations.
- **Change management:** version, test, stage, approve, and announce changes; maintain a changelog.

## Reliability Patterns Cheat Sheet
| Problem | Pattern |
|---|---|
| Duplicate execution | Idempotency keys, unique constraints, locks |
| Transient failures | Retry with backoff + jitter |
| Cascading failures | Timeouts, circuit breakers, bulkheads, rate limiting |
| Lost messages | Durable queues, acks, DLQ, outbox pattern |
| Poison messages | Dead-letter queue + alert + replay tool |
| Partial failure across systems | Saga/compensating actions, reconciliation jobs |
| Long-running jobs | Checkpointing, resumability, heartbeats |
| Thundering herd | Jitter, staggering, queue-based leveling |
| Config drift | GitOps/IaC reconcile, drift detection |
| Runaway cost/loops | Budgets, max iterations, quotas, kill switch |

## Deliverables
- **Automation spec:** goal, trigger, inputs/outputs, steps, systems, permissions, error handling, SLAs, owner, metrics.
- **Code/config in version control** with README (setup, run, test, deploy, troubleshoot).
- **Runbook and monitoring dashboard/alerts.**
- **Rollback and disaster-recovery notes.**
- **ROI/baseline report** (time/error/cost before vs after).

## Common Mistakes
- Automating an undocumented or unstable process
- Non-idempotent jobs that duplicate or corrupt data on retry
- No timeouts, so a hung call blocks everything
- Silent failures; alerts that nobody owns
- Secrets in code, logs, or shared sheets; over-privileged bots
- Testing destructive automation directly in production
- Overlapping scheduled runs; no locking
- Ignoring rate limits, pagination, and API changes
- Flaky or ignored pipelines; manual hotfixes that bypass the pipeline
- No documentation, owner, or review cycle ("zombie automations")

## Checklist
- [ ] Process understood and stable; ROI estimated; right tool chosen
- [ ] Idempotent, parameterized, with dry-run and input validation
- [ ] Triggers/schedules defined with overlap, catch-up, and timeout policies
- [ ] Retries/backoff, timeouts, DLQ/exception path, and kill switch
- [ ] Secrets in vault; least-privilege identities; audit logging
- [ ] Tested (unit, integration, failure injection, idempotency) and piloted in shadow mode
- [ ] CI/CD with gates, staged rollout, and automatic rollback
- [ ] Structured logs, metrics, alerts (including missed-run detection), runbook
- [ ] Owner, documentation, and periodic review scheduled
