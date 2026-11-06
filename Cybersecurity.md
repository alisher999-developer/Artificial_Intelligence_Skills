---
name: cybersecurity
description: Defensive cybersecurity - threat modeling, risk assessment, secure architecture, hardening, identity and access, vulnerability management, detection and monitoring, incident response, and security awareness. Use for security reviews, policies, secure design, incident handling, and compliance-minded planning. Defensive and authorized use only.
---

# Cybersecurity Skill (Defensive)

> **Scope & ethics:** This skill is for *defending* systems you own or are explicitly authorized to assess. Do not provide working exploits, malware, phishing kits, credential-theft tooling, or instructions for unauthorized access. For penetration testing or red-team work, require written authorization, defined scope, rules of engagement, and a safe-handling plan - and keep guidance at the level of methodology, risk, and remediation rather than weaponized steps.

## Core Principles
1. **Risk-based.** Protect what matters most first: identify assets, threats, vulnerabilities, impact, and likelihood.
2. **Defense in depth.** Layer controls so one failure doesn't mean compromise.
3. **Least privilege & zero trust.** Never trust by network location; verify explicitly; grant the minimum access, for the minimum time.
4. **Secure by design & by default.** Build security in; safe defaults; fail closed.
5. **Assume breach.** Plan for detection, containment, and recovery, not only prevention.
6. **Simplicity & reduction of attack surface.** Fewer components, ports, privileges, and dependencies mean fewer vulnerabilities.
7. **People and process matter as much as technology.** Most incidents involve human factors.
8. **Continuous improvement.** Threats change; measure, test, and iterate.
9. **Usable security.** Controls people bypass don't protect anyone.

## Frameworks to Anchor On
- **NIST CSF 2.0:** Govern, Identify, Protect, Detect, Respond, Recover.
- **CIS Critical Security Controls** (prioritized safeguards), **ISO/IEC 27001/27002**, **SOC 2**, **NIST 800-53/800-171**, **PCI DSS**, **HIPAA**, **GDPR** (apply those relevant; compliance != security).
- **MITRE ATT&CK** (adversary behaviors for detection coverage), **OWASP Top 10 / ASVS / MASVS / LLM Top 10** (application and AI security), **STRIDE** (threat modeling), **CVSS/EPSS/CISA KEV** (vulnerability prioritization).

## 1. Risk Assessment
1. **Inventory assets:** data (classified by sensitivity), systems, applications, identities, third parties, cloud resources, devices. You can't protect what you don't know.
2. **Identify threats & vulnerabilities:** threat actors (criminals, insiders, nation-states, hacktivists), common attack paths (phishing, credential stuffing, unpatched software, misconfiguration, supply chain, ransomware).
3. **Assess:** likelihood x impact (confidentiality, integrity, availability, legal, financial, reputational) -> risk rating.
4. **Treat:** mitigate, transfer (insurance, contracts), avoid, or accept (with documented owner sign-off).
5. **Track in a risk register** with owners, deadlines, and residual risk.

## 2. Threat Modeling
Ask four questions: **What are we building? What can go wrong? What are we going to do about it? Did we do a good job?**
- Draw a **data flow diagram:** actors, processes, data stores, trust boundaries, data flows.
- **STRIDE** per element: Spoofing (authentication), Tampering (integrity), Repudiation (logging), Information disclosure (confidentiality), Denial of service (availability), Elevation of privilege (authorization).
- Rate threats (e.g., DREAD-like, or likelihood x impact); define mitigations; assign owners; revisit when architecture changes.
- Also consider abuse cases ("how would an attacker misuse this feature?").

## 3. Identity & Access Management (the new perimeter)
- **MFA everywhere**, prioritizing phishing-resistant methods (FIDO2/passkeys, hardware keys) for admins and remote access; avoid SMS where possible.
- SSO + centralized identity provider; lifecycle automation (joiner-mover-leaver); promptly remove access.
- **Least privilege & RBAC/ABAC;** separate admin and daily accounts; privileged access management (just-in-time, session recording); regular access reviews.
- Strong password policy aligned with NIST 800-63B (length over complexity, breached-password checks, no forced periodic rotation without cause); use password managers.
- Service accounts and API keys: unique per workload, scoped, rotated, stored in a secrets manager, monitored; prefer short-lived tokens and workload identity.
- Conditional access (device health, location, risk signals).

## 4. Secure Architecture & Hardening
- **Network:** segmentation/micro-segmentation, default-deny firewall rules, private subnets, egress filtering, VPN/ZTNA, DNS filtering, TLS 1.2+ everywhere, secure Wi-Fi (WPA3/enterprise), DDoS protection, WAF for web apps.
- **Endpoints:** EDR/XDR, full-disk encryption, automatic patching, application allow-listing where feasible, local admin removal, secure baselines (CIS Benchmarks), mobile device management.
- **Servers & cloud:** minimal images, remove unused services, immutable infrastructure, infrastructure-as-code with policy checks, secure configuration (CSPM), no public storage buckets/databases by default, private endpoints, encryption at rest and in transit with managed keys, separate accounts/projects per environment, centralized logging.
- **Email & web:** SPF/DKIM/DMARC enforcement, anti-phishing and sandboxing, link/attachment protection, secure web gateways.
- **Data protection:** classify data; encrypt; tokenization/masking; DLP; retention and secure disposal; backups following **3-2-1-1-0** (3 copies, 2 media, 1 offsite, 1 offline/immutable, 0 errors after restore testing).
- **Physical:** access control, visitor management, device handling, clean desk.

## 5. Application & Software Supply Chain Security
- **Secure SDLC:** requirements -> threat model -> secure coding standards -> code review -> SAST/DAST/IAST -> dependency (SCA) scanning -> secrets scanning -> container/IaC scanning -> security testing -> release gating.
- **OWASP Top 10 focus:** broken access control, cryptographic failures, injection, insecure design, misconfiguration, vulnerable components, authentication failures, integrity failures, logging/monitoring failures, SSRF.
- Input validation, output encoding, parameterized queries, strong session management, CSRF/XSS protection, secure headers (CSP, HSTS), rate limiting, authorization on every request.
- **Supply chain:** SBOMs, pinned and verified dependencies, signed artifacts and provenance (e.g., SLSA), protected CI/CD (least-privilege runners, no long-lived secrets, branch protection), vetted third-party code and vendors.
- **Secrets:** never in code or logs; rotate on exposure; use pre-commit/CI scanning.
- **AI/LLM applications:** guard against prompt injection, data leakage, insecure output handling, excessive agency, and model/supply-chain risks; constrain tool permissions, validate outputs, log and monitor, require human approval for high-risk actions.

## 6. Vulnerability & Patch Management
- Continuous asset discovery and scanning (authenticated where possible).
- **Prioritize** with exploitability, not CVSS alone: known-exploited (CISA KEV), EPSS, internet exposure, asset criticality, compensating controls.
- SLAs by severity (e.g., critical/known-exploited in days; high in 2-4 weeks); emergency process for zero-days; virtual patching/mitigations when patching isn't immediate.
- Track exceptions with expiry and owner; verify fixes; report mean time to remediate.

## 7. Detection & Monitoring
- **Centralize logs** (identity, endpoint, network, cloud control plane, applications, email) in a SIEM/data lake; synchronize time; protect log integrity; define retention.
- **Detection engineering:** map detections to MITRE ATT&CK; focus on high-signal behaviors (impossible travel, new admin creation, mass file access/encryption, disabled security tools, unusual data egress, suspicious PowerShell/LOLBins, anomalous cloud API use); tune to reduce false positives; test with purple-team exercises.
- Honeypots/canary tokens for high-confidence alerts.
- 24x7 coverage via SOC/MDR if you can't staff it; define triage, severity, and escalation.
- Threat intelligence: use relevant, actionable feeds; share with ISACs.

## 8. Incident Response (NIST 800-61 lifecycle)
**Prepare -> Detect & Analyze -> Contain, Eradicate & Recover -> Post-Incident Activity**
- **Prepare:** IR plan and playbooks (ransomware, phishing/BEC, lost device, data breach, insider, DDoS, cloud compromise), roles (incident commander, comms, legal, forensics, IT), contact lists, out-of-band communication channel, retainers (forensics, counsel, insurer), tabletop exercises at least annually, tested backups.
- **Detect & analyze:** validate the alert; scope (which systems, accounts, data); determine severity; preserve evidence (memory, logs, disk images; maintain chain of custody); keep a timestamped log of actions.
- **Contain:** short-term (isolate hosts, disable compromised accounts, block IOCs, revoke tokens/sessions) and long-term (segmentation, temporary controls) - balance business impact against spread.
- **Eradicate:** remove persistence, patch the root cause, reset credentials and secrets (including service accounts and API keys), rebuild from known-good images.
- **Recover:** restore from clean backups, monitor closely for re-compromise, phased return to service.
- **Notify:** legal, regulators, customers, and law enforcement per applicable breach-notification rules and contracts (consult counsel).
- **Lessons learned:** blameless review within ~2 weeks; root cause, detection gaps, control improvements, updated playbooks, tracked actions.
- **Ransomware specifics:** isolate immediately, don't power off if volatile evidence is needed, identify patient zero and exfiltration, check backups' integrity, involve legal/insurer/law enforcement before any payment decision (payment is not guaranteed to restore data and may carry legal risks).

## 9. Security Awareness & Human Factors
- Short, regular, role-based training; phishing simulations used for learning, not punishment.
- Teach: recognizing phishing and business-email-compromise, verifying payment/banking changes out-of-band, MFA fatigue, QR/SMS phishing, deepfake/voice-clone fraud, safe sharing, reporting without fear.
- Make reporting easy (one-click report button); celebrate reports.
- Secure defaults and good tooling reduce reliance on perfect user behavior.
- Insider risk: separation of duties, monitoring proportionate to risk and legal/privacy limits, offboarding controls.

## 10. Third-Party & Cloud Risk
- Vendor due diligence: security questionnaires, SOC 2/ISO evidence, data flows, subprocessors, breach notification terms, right to audit, exit plan.
- Limit vendor access (least privilege, time-bound); monitor integrations and OAuth app grants.
- Understand the **shared responsibility model** for each cloud/SaaS service.

## 11. Business Continuity & Resilience
- Business impact analysis; RTO/RPO targets; tested disaster recovery runbooks; immutable/offline backups; failover design; crisis communication; cyber insurance review (coverage, exclusions, requirements).

## 12. Governance, Metrics & Compliance
- Policies: acceptable use, access control, data classification, incident response, vulnerability management, vendor management, secure development, BYOD, remote work. Keep concise and enforced.
- Clear ownership (CISO or accountable exec), board reporting, budget aligned to risk.
- **Metrics:** MFA coverage, patch latency for critical/KEV vulnerabilities, EDR coverage, mean time to detect/respond/contain, phishing report rate, privileged account count, backup restore success rate, % of assets inventoried, open high risks past SLA.
- Compliance: map controls to frameworks once and reuse evidence; automate evidence collection; remember "compliant" does not mean "secure."

## Quick Wins for Small Organizations (priority order)
1. MFA on email, admin, remote access, and finance systems
2. Automatic updates and endpoint protection on all devices
3. Tested, offline/immutable backups
4. Password manager and unique passwords; remove shared accounts
5. Email security (SPF/DKIM/DMARC, phishing filtering)
6. Least privilege; remove ex-employee access
7. Inventory of assets and data; encrypt laptops and phones
8. Simple incident response plan with contacts; run a tabletop
9. Security awareness basics, including payment-fraud verification procedures
10. Review cloud/SaaS sharing and public exposure settings

## Output Formats
- **Security review/assessment:** scope -> method -> findings (title, evidence, affected assets, risk rating, impact, remediation, effort, owner) -> prioritized roadmap (quick wins / 30-90 days / strategic) -> residual risk.
- **Threat model:** diagram, assets, trust boundaries, threats (STRIDE), mitigations, open questions.
- **Incident report:** summary, timeline, impact, root cause, containment/eradication actions, evidence, notifications, lessons, follow-ups.
- **Policy/Standard:** purpose, scope, roles, requirements (testable "must/should"), exceptions, enforcement, review date.

## Common Mistakes
- Treating compliance as security; shelfware tools without owners
- No asset inventory; unknown shadow IT
- Relying on perimeter controls; flat networks
- SMS-only MFA for admins; shared and over-privileged accounts
- Unpatched internet-facing systems; ignoring known-exploited vulnerabilities
- Backups that are never restore-tested or are reachable by attackers
- No logging, or logs nobody monitors
- Untested incident plans; unclear decision authority during incidents
- Secrets in code repositories
- Blaming users instead of fixing systems

## Checklist
- [ ] Assets, data, and risks inventoried and prioritized
- [ ] Threat model for key systems; mitigations assigned
- [ ] Phishing-resistant MFA, least privilege, lifecycle management
- [ ] Hardened, segmented, patched environments with encryption
- [ ] Secure SDLC and supply-chain controls
- [ ] Centralized logging, tuned detections, response coverage
- [ ] Incident response plan tested; backups tested and immutable
- [ ] Vendor and cloud risk managed
- [ ] Awareness program and easy reporting
- [ ] Metrics reviewed; policies owned and current
