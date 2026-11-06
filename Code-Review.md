---
name: code-review
description: Review code changes (diffs, pull requests, files, snippets) for correctness, security, performance, maintainability, and test coverage, and deliver prioritized, actionable, respectful feedback. Use for PR reviews, audits, and self-review before merging.
---

# Code Review Skill

## Core Principles
1. **Goal: ship better code, not prove superiority.** Review the code, never the person.
2. **Understand intent first.** Read the PR description, linked issue, and requirements before judging details.
3. **Correctness and risk before style.** Bugs, security holes, data loss, and broken contracts outrank formatting.
4. **Be specific and actionable.** Point to the line, explain the problem, propose a fix.
5. **Prioritize.** Separate blocking issues from suggestions and nits. Too many comments bury the important ones.
6. **Automate the trivial.** Formatting and lint belong to tools, not humans.
7. **Don't speculate - verify.** If unsure, run it, trace it, or ask a question rather than assert.

## Review Process
1. **Context (2 min):** What is the change for? Size? Risk level? Any deadlines or rollback plan?
2. **Big picture:** Is the approach right? Does it fit the architecture? Is the scope appropriate (one concern per PR)? Is there a simpler way?
3. **Tests first:** Read the tests to learn intended behavior, then check they truly cover it.
4. **Line-by-line pass:** correctness, edge cases, error handling, security, performance, readability.
5. **Run it when risk is high:** pull the branch, run tests, try failure cases.
6. **Summarize:** overall verdict, top concerns, what's good.

For large diffs, review in layers: public interfaces and data model -> core logic -> tests -> peripherals. Ask to split PRs over ~400 changed lines.

## What to Check

### Correctness
- Does it do what the requirement says? Off-by-one, boundary, null/None/undefined, empty collections, zero, negative, very large values.
- Logic errors: inverted conditions, wrong operators, short-circuit mistakes, mutation of shared state.
- Concurrency: race conditions, deadlocks, non-atomic check-then-act, shared mutable state, missing locks or idempotency.
- Error handling: swallowed exceptions, missing cleanup/rollback, partial failures, retries without backoff, misleading messages.
- Resource handling: unclosed files/connections/streams, leaks, unbounded growth.
- Time: time zones, DST, clock reliance, date parsing, leap cases.
- Numeric: float for money, overflow, rounding, unit mismatches.
- Backward compatibility: API contract changes, DB migrations (locking, reversibility), serialization formats, feature flags.

### Security
- Input validation and output encoding (XSS, SQL/command/template injection, path traversal, SSRF, open redirect).
- Authentication and authorization on every sensitive path; IDOR (user can access others' IDs).
- Secrets, tokens, or PII in code, logs, errors, or URLs.
- Cryptography: standard libraries only, strong algorithms, proper randomness, password hashing.
- Unsafe deserialization, `eval`, dynamic code execution, unvalidated file uploads.
- Dependency changes: new packages vetted, pinned, licenses OK, known CVEs.
- CORS, CSRF, rate limiting, headers, least privilege for service accounts.

### Performance & Scalability
- Algorithmic complexity on realistic data sizes; unnecessary nested loops.
- N+1 queries, missing indexes, unbounded queries (no pagination or limit), `SELECT *`.
- Repeated work in loops; missing caching or cache invalidation bugs.
- Blocking I/O in async paths; large payloads in memory instead of streaming.
- Only flag micro-optimizations when there's evidence they matter.

### Design & Maintainability
- Single responsibility; clear boundaries; no leaky abstractions.
- Naming: reveals intent; consistent with codebase.
- Duplication vs premature abstraction; dead code; speculative generality.
- Function length, nesting depth, parameter count; hidden side effects; global state.
- Comments explain why, not what; stale comments; TODOs with owners/tickets.
- Consistency with existing patterns and conventions in the repo.
- Public API: minimal, documented, hard to misuse.

### Tests
- New behavior and bug fixes have tests; bug fix has a regression test.
- Tests assert behavior, not implementation details; no over-mocking.
- Edge cases, failure paths, and boundary values covered.
- Deterministic (no real time/network/randomness); no flaky patterns; clear names.
- Don't accept "tests pass" as proof if the tests don't exercise the change.

### Operations
- Logging at the right level without secrets; useful context for debugging.
- Metrics/alerts for new critical paths; health checks.
- Config via env/secret store; safe defaults; rollout/rollback plan; feature flags.
- Migrations tested on realistic data and backwards compatible with the running version.

### Documentation
- README/API docs/changelog updated; examples correct; breaking changes called out.

## Severity Scale
| Level | Meaning | Action |
|---|---|---|
| **Blocker / Critical** | Security vuln, data loss, crash, broken core behavior | Must fix before merge |
| **Major** | Likely bug, significant design or performance problem, missing important tests | Should fix before merge |
| **Minor** | Maintainability, small edge cases, clarity | Fix or consciously defer |
| **Nit** | Style or preference | Optional; prefix with "nit:" |
| **Question** | Need to understand intent | Reply requested |
| **Praise** | Something done well | Reinforce good practice |

## Comment Format
```
[Severity] file:line - Short title
Problem: what is wrong and the concrete consequence (input -> bad outcome).
Suggestion: a specific fix or snippet.
(Optional) Why: principle or reference.
```
Example:
```
[Major] orders/service.py:88 - Race condition on stock decrement
Problem: read-then-write lets two concurrent requests both pass the check and oversell.
Suggestion: use an atomic UPDATE ... WHERE stock >= qty (or SELECT FOR UPDATE) and handle 0 rows affected.
```

## Tone & Communication
- Ask questions rather than issue commands: "What happens if `items` is empty?"
- Use "we" and "this code," not "you."
- Explain the reason behind requests; link to docs or standards.
- Offer alternatives, not just objections. Acknowledge trade-offs.
- Call out what is good - specific praise builds trust.
- Don't block on personal taste; defer to the team style guide.
- If a discussion gets long, move to a call and record the outcome.
- As an author: keep PRs small, self-review first, explain context, respond to every comment, don't take it personally.

## Review Summary Template
```
## Summary
One or two sentences on what the change does and overall impression.

## Verdict
Approve / Approve with comments / Request changes

## Must fix (blocking)
1. ...

## Should fix
1. ...

## Suggestions / nits
- ...

## What's good
- ...

## Test & risk notes
Tested? Risky areas? Rollout/rollback suggestions.
```

## Self-Review Checklist (before opening a PR)
- [ ] Read my own diff top to bottom as if I were the reviewer
- [ ] No debug code, commented-out code, or secrets
- [ ] Tests added and passing; lint/format clean
- [ ] Edge cases and failures handled
- [ ] Docs/changelog updated
- [ ] PR description: what, why, how tested, risks, screenshots if UI

## Anti-Patterns
- Rubber-stamping ("LGTM") without reading
- Nitpicking style while missing a bug
- Rewriting the PR in the comments to match your taste
- Vague comments ("this is bad")
- Demanding scope creep that belongs in a follow-up ticket
- Reviewing only the diff and missing how it interacts with surrounding code
- Asserting a bug without verifying it
