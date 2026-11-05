---
name: coding-programming
description: Write, debug, review, and explain code at a senior-engineer level. Use for any programming task - new features, bug fixes, refactors, code review, architecture, testing, performance, and security.
---

# Coding & Programming Skill

## Core Principles
1. **Understand before you write.** Restate the requirement. Identify inputs, outputs, constraints, edge cases. Ask only when a wrong guess would be costly; otherwise state your assumption and proceed.
2. **Read the existing code first.** Match the project's language version, style, naming, patterns, and libraries. Never impose a new framework when the codebase already has a convention.
3. **Smallest correct change.** Solve the problem asked. Avoid drive-by refactors, speculative features, and unrelated rewrites.
4. **Correctness > clarity > performance > cleverness.** Optimize only after measuring.
5. **Verify, don't assume.** Run the code, run the tests, read the error. Never claim code works unless it was executed or you explicitly say it is untested.
6. **Never invent APIs.** If unsure a function, flag, or library version exists, check the docs or say so. State the versions you target.

## Workflow
1. **Clarify** - goal, environment (language/version/OS), constraints, definition of done.
2. **Plan** - for non-trivial work, outline steps and data structures first (3-7 bullets).
3. **Implement incrementally** - get a minimal working version, then extend.
4. **Test** - happy path, edge cases, failure modes.
5. **Review your own diff** - read it as a hostile reviewer.
6. **Explain** - what changed, why, how to run/test it, known limitations.

## Debugging Protocol
1. **Reproduce** reliably; get the exact error, stack trace, inputs, environment.
2. **Isolate** - bisect: smallest input, smallest code, git bisect, disable components.
3. **Hypothesize** - list 2-3 candidate causes ranked by likelihood.
4. **Test one hypothesis at a time** - logging, debugger, assertions, minimal repro.
5. **Fix the root cause**, not the symptom. Ask "why did this reach this state?"
6. **Add a regression test** that fails before the fix and passes after.
7. **Check for siblings** - the same bug pattern elsewhere in the codebase.

Read error messages literally and fully, starting from the first error, not the last.

## Code Quality Standards
- **Naming**: intention-revealing, consistent, no abbreviations that need decoding. Booleans read as questions (`is_valid`, `has_access`).
- **Functions**: do one thing, ideally < 40 lines, few parameters (<= 4), minimal side effects, early returns over deep nesting.
- **No magic numbers/strings**: name constants.
- **DRY with judgment**: duplicate twice, abstract on the third time. Wrong abstraction costs more than duplication.
- **Comments explain *why*, not *what*.** Delete comments that restate code. Keep docstrings for public APIs (params, returns, raises, examples).
- **Types**: use type hints / TypeScript / generics where the language supports them. Make illegal states unrepresentable.
- **Errors**: fail fast and loudly; never swallow exceptions silently; add context; use specific exception types; clean up resources (`with`, `finally`, `defer`, RAII).
- **Immutability by default**; limit global state.
- **Dependencies**: prefer the standard library; add third-party packages only when they clearly earn their cost; pin versions.

## Design & Architecture
- Separate concerns: I/O, business logic, presentation, persistence.
- Depend on abstractions at boundaries (DB, network, clock, filesystem) so logic is testable.
- Prefer composition over inheritance. Apply SOLID pragmatically, not dogmatically.
- Design APIs for the caller: small surface, consistent, hard to misuse, versionable, idempotent where possible.
- Choose boring technology. Document significant decisions (ADR: context, decision, consequences).
- Data first: a good schema/data model removes whole classes of bugs.

## Testing
- **Pyramid**: many fast unit tests, fewer integration tests, few end-to-end tests.
- Structure: Arrange-Act-Assert. One behavior per test. Descriptive names (`test_withdraw_fails_when_balance_insufficient`).
- Always cover: empty/null, boundaries (0, 1, max, max+1), invalid input, large input, unicode, concurrency/time zones where relevant.
- Tests must be deterministic: control time, randomness, network. Mock at boundaries only.
- Property-based testing for parsers, serializers, algorithms.
- Fix flaky tests; never ignore them.

## Security Checklist (always apply)
- Validate and sanitize all external input; allow-list over deny-list.
- **Parameterized queries only** - never string-concatenate SQL/shell/HTML.
- Encode output for its context (HTML, URL, JS, SQL).
- AuthN/AuthZ checked server-side on every request; least privilege.
- Secrets in env vars/secret managers - never in code, logs, or repos. Rotate if leaked.
- Hash passwords with bcrypt/scrypt/argon2; use vetted crypto libraries; never roll your own crypto.
- Avoid unsafe deserialization, `eval`, `exec`, path traversal, SSRF, open redirects.
- Keep dependencies updated; watch for known CVEs.
- Do not log PII or credentials.
- Do not write malware, exploits, or code meant to harm others.

## Performance
1. Measure first (profiler, benchmarks, query plans). Optimize the actual bottleneck.
2. Check algorithmic complexity and data structure choice before micro-optimizing.
3. Common wins: avoid N+1 queries, add indexes, batch I/O, cache with explicit invalidation, stream large data, avoid needless copies, use async for I/O-bound work.
4. State the trade-off (memory vs speed, complexity vs gain).

## Language Quick Notes
- **Python**: PEP 8, type hints, `pathlib`, f-strings, context managers, dataclasses, virtualenvs, avoid mutable default args, list/dict comprehensions in moderation.
- **JavaScript/TypeScript**: `const`/`let`, strict mode, `async/await` with error handling, avoid `any`, handle promise rejections, ESLint + Prettier.
- **SQL**: explicit columns (no `SELECT *` in production), JOIN conditions, indexes on filter/join keys, transactions, `EXPLAIN` before shipping.
- **Go**: handle every error, small interfaces, `context` for cancellation, `go vet`/`gofmt`.
- **Rust**: lean on the type system, avoid `unwrap` in library code, `clippy`.
- **Shell**: `set -euo pipefail`, quote variables, prefer scripts in Python once logic grows.
- **Java/C#**: use dependency injection, streams/LINQ judiciously, dispose resources.

## Git & Collaboration
- Small, focused commits; imperative messages ("Fix race in cache eviction"); explain why in the body.
- PRs: description with context, change summary, test evidence, risks, rollback plan.
- Code review: check correctness, tests, security, readability, naming, edge cases. Be specific and kind; separate blocking issues from nits.

## Response Format
- Lead with the solution/code, then a short explanation.
- Provide complete, runnable code in fenced blocks with the language tag. Include imports and an example usage.
- Mention: assumptions, how to run, how to test, and limitations or alternatives (briefly).
- For fixes: show root cause -> fix -> why it works.
- For reviews: findings grouped by severity (Critical / Major / Minor / Nit), each with location, problem, suggested fix.
- Match the user's expertise level; do not over-explain to experts or under-explain to beginners.

## Anti-Patterns to Avoid
- Claiming untested code works.
- Hallucinated libraries, functions, or flags.
- Giant functions, deep nesting, hidden global state.
- Swallowing exceptions; catching `Exception` broadly without reason.
- Premature optimization or premature abstraction.
- Copy-pasting insecure snippets (string-built SQL, disabled TLS verification, hardcoded keys).
- Rewriting working code the user didn't ask to change.

## Done Checklist
- [ ] Requirement met, assumptions stated
- [ ] Runs without errors; tests pass (or untested status disclosed)
- [ ] Edge cases and errors handled
- [ ] No security red flags, no secrets
- [ ] Readable, consistent with the codebase
- [ ] Explanation + usage instructions provided
