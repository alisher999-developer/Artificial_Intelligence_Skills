---
name: document-management
description: Organize, name, version, store, secure, retain, and retrieve documents and records - for personal files, teams, and organizations. Use for folder structures, naming conventions, version control, templates, knowledge bases, retention policies, cleanup, and document workflows.
---

# Document Management Skill

## Core Principles
1. **Findable in 30 seconds.** If someone can't locate a document quickly without asking you, the system has failed.
2. **One source of truth.** Every document has a single authoritative home; others link to it rather than copy it.
3. **Consistency beats perfection.** A simple convention everyone follows outperforms a clever one nobody does.
4. **Clear ownership.** Every document has an owner, a status, and a review date.
5. **Secure by default.** Least-privilege access; sensitive data classified and protected.
6. **Lifecycle thinking.** Create -> Review -> Approve -> Publish -> Maintain -> Archive -> Dispose.
7. **Make the right way the easy way.** Templates, defaults, and automation over policing.

## Step 1 - Audit the Current State
- Inventory: where do documents live (drives, email, chat, local machines, paper)?
- Pain points: duplicates, unclear versions, lost files, access problems, outdated content.
- Volume, types, owners, sensitivity, legal/regulatory requirements.
- Identify "what is critical, what is clutter, what is unknown."

## Step 2 - Design the Structure

### Folder Taxonomy
- Organize by what people **search for** - usually Project/Client/Function first, then document type, then date.
- Keep depth to **3-4 levels max**; prefer fewer, broader folders plus good search/metadata.
- Don't mirror the org chart if it reorganizes often; mirror stable work (clients, products, processes).
- Use a numbered prefix for fixed ordering (`01_Contracts`, `02_Finance`, `03_Delivery`).
- Include `00_Admin` (templates, readme) and `99_Archive` (closed items).
- Avoid "Misc," "Stuff," "New Folder," and personal-name folders for shared work.

Example:
```
Clients/
  Acme-Corp/
    01_Contracts/
    02_Proposals/
    03_Deliverables/
    04_Correspondence/
    99_Archive/
Internal/
  Finance/  HR/  Legal/  Marketing/  Templates/
```

### Naming Convention
Pattern: `YYYY-MM-DD_Project_DocType_Description_vNN` (dates first sort chronologically).
- ISO dates (`2026-11-05`), not `11/5/26`.
- No spaces or special characters (`_` or `-`); keep under ~60 characters.
- Include version or status (`v02`, `DRAFT`, `FINAL` - but prefer a version number to "final_final2").
- Same order every time; lowercase or consistent title case; avoid abbreviations nobody knows.
- Document the convention on one page and pin it.

Good: `2026-11-05_Acme_Proposal_Q1-Marketing_v03.docx`
Bad: `Proposal final FINAL (2) new.docx`

### Metadata & Tags
- Add fields where the system supports them: owner, status, type, project, confidentiality, review date, retention class.
- Use a controlled vocabulary (a short approved tag list), not free-for-all tags.

## Step 3 - Version Control
- **Prefer a system with built-in version history** (SharePoint, Google Drive, Notion, Confluence, Git for text) over filename versions.
- Edit in place and co-author in the cloud rather than emailing attachments.
- Major vs minor versions: `1.0` published, `1.1` small edit, `2.0` significant revision; keep a short change log.
- Lock approved/final documents (read-only or PDF) and create a new version for changes.
- Record **who changed what and why** (version comment).
- Never overwrite the only copy; keep restoration possible.

## Step 4 - Document Lifecycle & Workflow
| Stage | Practices |
|---|---|
| Create | Start from a template; set owner, status, and review date |
| Review | Named reviewers, deadline, comments tracked in the document |
| Approve | Clear approver; record date and version approved |
| Publish | Move to the controlled location; notify stakeholders |
| Maintain | Review cycle (e.g., every 6-12 months); flag stale documents |
| Archive | Move out of active areas; keep searchable and read-only |
| Dispose | Delete securely per retention schedule; log disposal |

Statuses: `Draft -> In Review -> Approved -> Published -> Superseded -> Archived`.

## Step 5 - Templates & Standards
- Standard templates for recurring documents: proposals, reports, meeting notes, SOPs, contracts, invoices, project briefs, decision logs.
- Template includes: title, owner, date, version, purpose, status, change log, and consistent headings/styles.
- Use styles (Heading 1/2/3), not manual formatting, so tables of contents and accessibility work.
- Provide a "how to name and file" cheat sheet inside the template.

## Step 6 - Security, Privacy & Compliance
- **Classify:** Public / Internal / Confidential / Restricted; label documents accordingly.
- **Access:** role-based, least privilege, group-based rather than individual; review access quarterly; remove leavers promptly.
- **Sharing:** expiring links, no "anyone with link" for sensitive files, watermarks where needed.
- **Protect:** encryption at rest and in transit, MFA, DLP rules, secure disposal.
- **PII/regulated data** (GDPR, HIPAA, SOX, PCI, etc.): know where it lives, minimize collection, document legal basis and retention. Consult legal/compliance for requirements - this skill is not legal advice.
- **Audit trail:** log access, edits, shares, and deletions for sensitive content.
- **Backup & recovery:** 3-2-1 rule (3 copies, 2 media types, 1 offsite); test restores.

## Step 7 - Retention & Disposal
- Create a **retention schedule** by record type (e.g., contracts, financial, HR, project files, email) based on legal, tax, and business needs.
- Define: retention period, trigger event (contract end, employee departure), disposition (archive or destroy), legal hold process.
- Don't keep everything forever: unnecessary retention increases risk and cost.
- Suspend disposal when litigation or investigation is possible (legal hold).

## Step 8 - Findability
- Search-first culture: good titles, descriptions, and metadata beat deep folders.
- Maintain an **index/landing page** of key documents with links (a "start here" page per project or team).
- Link to documents instead of attaching copies; use stable links.
- Add summaries at the top of long documents (purpose, audience, last updated).
- Cross-reference related documents; maintain a glossary for team terms.
- OCR scanned PDFs so they're searchable.

## Step 9 - Cleanup & Migration Project
1. Freeze the scope; back up everything first.
2. **Triage:** Keep / Archive / Delete / Needs-review (apply "ROT" test: Redundant, Obsolete, Trivial).
3. Detect duplicates (hash or name+size); keep the best version; redirect or link the rest.
4. Rename and refile in batches using the convention; pilot on one team first.
5. Communicate: what changes, the new rules, where to ask; train briefly.
6. Redirect/redirect links, keep the old location read-only for a short period, then retire.
7. Audit after 30/90 days and fix drift.

## Step 10 - Governance & Adoption
- Name a **document owner/steward** per area; define who can create folders and change structure.
- Publish a one-page policy: structure, naming, versioning, sharing, retention.
- Onboard new hires with the system; add it to checklists.
- Measure: search success, time to find, % of documents with owner/review date, stale content count, duplicate count.
- Quarterly housekeeping: archive stale, fix permissions, update templates.

## Personal Document Management Quick System
- One inbox folder for new files; process weekly.
- Top-level: `Projects`, `Areas` (ongoing responsibilities), `Resources`, `Archive` (PARA method).
- Same naming convention; cloud sync + backup; scan paper and file it with the date; shred what you scan if not legally required.

## Common Mistakes
- Deep nesting and vague folder names
- Emailing attachments instead of linking to one source
- "final_v3_REAL" filenames
- No owner or review date, leading to stale content
- Over-engineered taxonomy nobody follows
- Open sharing of sensitive files; permissions never reviewed
- Keeping everything forever, or deleting without a retention check
- Migrating without a backup or communication

## Checklist
- [ ] Single source of truth and owner for each document set
- [ ] Simple, documented folder and naming convention
- [ ] Version history enabled; approved versions locked
- [ ] Templates for recurring documents
- [ ] Classification and least-privilege access in place
- [ ] Retention schedule and disposal process defined
- [ ] Index/landing pages and metadata for findability
- [ ] Backup tested; audit trail for sensitive content
- [ ] Training and periodic housekeeping scheduled
