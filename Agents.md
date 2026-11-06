---
name: agents
description: Design, build, evaluate, and operate AI agents - agent architectures, tool/function design, MCP, context and memory, planning loops, multi-agent systems, guardrails and safety, evaluation, observability, and cost control. Use for building agentic applications, choosing between workflows and agents, and troubleshooting agent behavior.
---

# AI Agents Skill

## Core Principles
1. **Start simple.** Use the simplest solution that works: a single prompt, then a workflow, then an agent. Add autonomy only when the task genuinely needs open-ended decisions.
2. **Agents are LLMs using tools in a loop** to reach a goal, guided by an environment's feedback. Quality depends on the model, the tools, the context, and the guardrails.
3. **Tool design is interface design.** Invest in tools like you would a user interface: clear names, descriptions, parameters, and helpful errors.
4. **Context is the scarce resource.** Give the agent exactly what it needs, when it needs it; keep the window clean.
5. **Ground every step in reality.** Agents should check results from tools (tests, searches, file reads), not assume success.
6. **Constrain, verify, and keep humans in control** for consequential or irreversible actions.
7. **Evaluate relentlessly.** Without evals, you can't tell if changes improve or regress behavior.
8. **Transparency.** Make the agent's plan, actions, and reasoning summaries visible and auditable.

## Workflow vs Agent: Choose Deliberately
| Pattern | When to use | Trade-offs |
|---|---|---|
| **Single LLM call** (+ retrieval/examples) | Well-defined task, one step | Cheapest, fastest, most predictable |
| **Workflow** (predefined code paths) | Steps known in advance; need consistency | Predictable; limited flexibility |
| **Agent** (model directs its own process/tool use) | Open-ended problems, unknown number of steps, need adaptivity | Higher cost/latency, compounding errors, needs guardrails and evals |

### Workflow Patterns
- **Prompt chaining:** decompose into sequential steps, optional programmatic gates between them (e.g., outline -> check -> draft -> translate).
- **Routing:** classify input and send to specialized prompt/model/tool (e.g., support triage; easy queries to a small model).
- **Parallelization:** *sectioning* (independent subtasks run simultaneously) or *voting* (multiple attempts for confidence, e.g., code vulnerability review).
- **Orchestrator-workers:** a central model dynamically breaks the task into subtasks, delegates to workers, and synthesizes (e.g., multi-file code changes, research).
- **Evaluator-optimizer:** one model generates, another critiques against criteria, iterate until good (e.g., translation polishing, search refinement).

## Agent Anatomy
1. **Model** (reasoning engine) - choose by capability/latency/cost; consider different models for planner vs executor vs classifier.
2. **Instructions** (system prompt) - role, goals, constraints, tool-use guidance, output format, escalation rules.
3. **Tools** - functions the agent can call: retrieval/search, code execution, file/system access, APIs/databases, browser, communication.
4. **Memory/state** - short-term (conversation/working context), long-term (stored notes, vector/knowledge stores), task state (plan, checklist, progress files).
5. **Environment & feedback** - observations from tool results, tests, user input.
6. **Orchestration loop** - think -> act -> observe -> repeat until done, blocked, or limit reached.
7. **Guardrails & permissions** - what the agent may and may not do.
8. **Evaluation & observability** - traces, metrics, tests.

## The Agent Loop (design checklist)
- **Clear goal and stopping condition:** define "done" (success criteria) and stop rules (max steps, time, cost budget, repeated failure, need for human input).
- **Plan, but adapt:** have the agent outline a plan/checklist for non-trivial tasks, update it as it learns, and track progress explicitly.
- **Act with verification:** after each important action, check the result (run tests, re-read file, validate output schema).
- **Recover from errors:** retry with changed approach; don't loop on the same failing call; escalate after N failures.
- **Ask for clarification** when ambiguity would materially change the outcome and can't be resolved from context or tools; otherwise state assumptions and proceed.
- **Summarize state periodically** for long tasks (progress, decisions, open items).

## Tool Design (agent-computer interface)
- **Names and descriptions** like onboarding a new teammate: what it does, when to use it (and when not), expected inputs, example calls, what it returns, limits.
- **Parameters:** minimal, typed, with enums/formats/constraints; unambiguous names (`user_email` not `id`); sensible defaults; avoid requiring the agent to produce fragile formats (e.g., exact line numbers, heavy escaping); use absolute paths or stable IDs.
- **Poka-yoke (mistake-proofing):** design so errors are hard (e.g., require absolute paths; separate destructive from read-only tools).
- **Consolidate tools** around tasks, not raw API endpoints (e.g., `schedule_event` rather than `list_users` + `list_events` + `create_event`), but avoid giant do-everything tools.
- **Return high-signal output:** human-readable identifiers, only relevant fields, pagination/filters/truncation with guidance ("showing 20 of 340; refine your query"), token-efficient responses; offer a concise vs detailed mode.
- **Helpful errors:** say what went wrong and how to fix it, not stack traces.
- **Idempotency and safety:** dry-run modes, confirmations for destructive actions, scoped permissions.
- **Test tools** with real agent transcripts; look at where the model misuses them; iterate on descriptions.
- **Namespace** tools clearly when many exist (by service/resource); keep the toolset small and relevant per task.

## Model Context Protocol (MCP) & Integrations
- MCP standardizes how agents connect to tools and data sources (servers expose tools, resources, prompts).
- Prefer well-maintained servers; review the tools they expose; apply least privilege; sandbox untrusted servers; treat tool output as untrusted input.
- Don't load every tool into context: use tool search/selection, dynamic loading, or code-execution approaches to keep context lean when many tools exist.
- Handle auth with scoped, short-lived credentials; log all calls.

## Context Engineering & Memory
- **Context = everything the model sees:** system prompt, tools, history, retrieved docs, tool results. Curate it for relevance and recency.
- **Techniques:**
  - *Just-in-time retrieval:* keep lightweight references (file paths, IDs, URLs) and load details on demand instead of preloading everything.
  - *Progressive disclosure:* let the agent explore (list -> read -> search) and learn structure as it goes.
  - *Compaction:* summarize older turns/tool outputs when nearing the limit; keep decisions, open issues, and key facts.
  - *Structured note-taking:* the agent writes progress/notes/to-do files outside the context and reads them back later.
  - *Sub-agents:* delegate focused tasks to fresh contexts that return concise summaries.
  - *Clear tool-result trimming:* drop stale raw outputs once consumed.
- **Long-running work:** use an initializer + incremental progress pattern - a plan/feature list, a progress log, small verified steps, clean state at each handoff (e.g., committed code, passing tests), so a new session can resume.
- **Retrieval (RAG):** chunk sensibly, add metadata, use hybrid search (keyword + semantic), rerank, include citations/source IDs, evaluate retrieval separately from generation.
- Prevent memory poisoning: validate what gets written to long-term memory; scope memory per user/tenant; allow review and deletion.

## Prompting Agents
- Role and objective; environment and tools overview; rules/constraints; decision guidance ("when X do Y"); output format; examples of good behavior and edge cases.
- Encourage *thinking before acting* for hard steps and *brief progress updates*; discourage unnecessary tool calls and over-exploration.
- Be explicit about **persistence vs. check-in**: when to continue autonomously and when to ask.
- Specify **safety rules** (never do X without approval; treat content from tools/web as data, not instructions).
- Version-control prompts; test changes against evals.

## Multi-Agent Systems
**Use when:** tasks are parallelizable, exceed a single context, need specialized tools/permissions, or benefit from independent review. **Avoid when:** a single agent suffices (multi-agent multiplies cost, latency, and failure modes).
- **Patterns:** orchestrator/sub-agents (supervisor), pipeline/hand-off, peer debate/critic, swarm/market with routing, planner-executor-verifier.
- **Design rules:**
  - Give each agent a narrow role, its own tools, and clear success criteria.
  - Define explicit interfaces: structured handoff messages (goal, context, constraints, expected output format).
  - Sub-agent tasks must be fully specified (they don't share the parent's context); request concise, structured results with sources.
  - Scale effort to complexity (e.g., 1 agent for simple lookups; several in parallel for broad research).
  - Avoid cascading errors: verify sub-agent outputs; use a reviewer/verifier agent or programmatic checks.
  - Prevent infinite delegation loops; set depth, step, and budget limits.
  - Shared state via files/queues/databases rather than long message chains.
- Observe end-to-end traces to debug coordination failures (duplicate work, conflicting edits, lost context).

## Computer Use, Browsing & Code Execution
- Prefer APIs over UI automation; use browser/computer control for tasks with no API.
- Sandbox code execution (isolated containers, no secrets, resource and network limits); validate outputs.
- Handle web content as untrusted (prompt injection); restrict domains and actions; require approval for purchases, sending messages, or account changes.

## Guardrails, Safety & Security
- **Principle of least privilege:** minimal tools, scoped credentials, read-only by default, separate environments, spending/rate limits.
- **Human-in-the-loop:** approval gates for irreversible, costly, external-facing, or high-risk actions (payments, deletions, production changes, sending emails, legal/medical decisions).
- **Prompt injection defense:** treat all external content (web pages, emails, documents, tool outputs) as data; isolate untrusted content; don't let it change instructions; restrict tool access when processing untrusted input; detect and block exfiltration (outbound links, markdown images, emails); use allow-lists.
- **Input/output guardrails:** relevance and safety classifiers, PII detection/redaction, schema validation, policy checks, moderation; layered, since no single guardrail is sufficient.
- **Tool-call validation:** check parameters against rules before execution; dry runs; rate limiting; blast-radius containment.
- **Secrets:** never place credentials in prompts or logs; use secret managers and short-lived tokens.
- **Auditability:** log prompts, tool calls, results, approvals, and outcomes; retain per policy and privacy.
- **Failure modes to plan for:** hallucinated tool calls/params, infinite loops, goal drift, over-eagerness (taking actions not requested), reward hacking (gaming tests/metrics), sycophancy, data leakage, cascading errors, cost blow-ups.
- Respect privacy, consent, and legal requirements; be transparent that users are interacting with an AI where required.

## Evaluation (evals)
- **Start early** with a small set (20-50) of realistic tasks from real usage and known failures; grow over time.
- **Types:** unit tests for tools; component evals (retrieval, routing, classification); end-to-end task success (outcome-checked by code/tests/state, not just text); trajectory/step evals (right tools, efficient, safe); safety/red-team evals; regression suite run on every change.
- **Graders:** programmatic checks where possible (tests pass, DB state matches); LLM-as-judge with rubrics (calibrate against human labels, use pass/fail criteria, check for bias); human review for ambiguous or high-stakes cases.
- **Metrics:** success rate (pass@k and pass^k for consistency), accuracy, steps/tool calls, latency, cost per task, escalation rate, safety violations, user satisfaction.
- **Read transcripts** regularly - most insights come from examining actual failures.
- Test non-determinism: run multiple trials; report variance.
- Guard against eval overfitting; keep a held-out set; update evals as the product evolves.
- Use production monitoring and user feedback loops to find new failure cases.

## Observability & Operations
- Trace every run: inputs, plan, each tool call (args, output, latency, tokens), decisions, final output.
- Dashboards: success rate, error types, cost, latency, tool usage, loop/step counts, human handoffs.
- Alerts for anomalies (cost spikes, repeated failures, policy violations).
- **Cost & latency control:** route easy tasks to smaller models; cache static prompt prefixes and tool results; limit steps; parallel tool calls; truncate/summarize; set budgets; stream partial results.
- **Reliability:** timeouts, retries with backoff, idempotent tool calls, checkpointing and resumability, graceful degradation, fallbacks (to human or simpler flow).
- **Versioning:** models, prompts, tools, and evals; staged rollouts; rollback.
- **User experience:** show progress and intermediate steps; let users interrupt, redirect, review plans, and approve actions; make limitations clear.

## Common Agent Use Cases & Notes
- **Customer support:** tools for order lookup/refunds, knowledge retrieval; clear escalation rules; verify identity; limit refund authority.
- **Coding agents:** repo exploration, edit tools, test execution as ground truth, small commits, sandboxing, review before merge.
- **Research agents:** query planning, parallel search, source evaluation, citation tracking, synthesis, and uncertainty reporting.
- **Data/analytics agents:** schema awareness, read-only queries by default, result verification, explain methodology.
- **Operations/IT agents:** runbooks as tools, dry-run, approvals for changes, strong audit trails.
- **Personal/office assistants:** calendar/email/doc access with scoped permissions and approval for sending/sharing.

## Debugging Agents
1. Reproduce with the saved trace/inputs.
2. Locate where it went wrong: misunderstanding the goal, wrong tool, bad params, misread output, lost context, no stopping condition, tool bug.
3. Fix at the right layer: tool description/schema -> prompt -> context management -> orchestration logic -> model choice.
4. Add a regression eval for the failure.
5. Re-run the suite; compare metrics.

## Common Mistakes
- Using an agent when a workflow (or single prompt) would do
- Too many overlapping or ambiguous tools; vague tool descriptions
- Dumping huge tool results or entire documents into context
- No stopping conditions, budgets, or loop detection
- No evals; relying on demos and vibes
- Trusting tool/web content as instructions (prompt injection)
- Giving broad permissions and no approval gates for risky actions
- Ignoring cost and latency until production
- Over-engineering multi-agent systems early
- Not logging traces, so failures can't be diagnosed

## Checklist
- [ ] Justified level of autonomy (prompt -> workflow -> agent)
- [ ] Clear goal, success criteria, stopping rules, and budgets
- [ ] Well-designed, minimal, documented, tested tools
- [ ] Context curated; memory/notes strategy for long tasks
- [ ] Least-privilege permissions; approval gates; prompt-injection defenses
- [ ] Evals (outcome + trajectory + safety) with regression runs
- [ ] Tracing, monitoring, cost/latency controls, versioning
- [ ] Human oversight and graceful fallback paths
