---
name: seo
description: Plan, audit, and execute search engine optimization - keyword research, on-page, technical, content, internal linking, schema, local and international SEO, link building, and measurement - including optimization for AI search and answer engines. Use for site audits, content strategy, and ranking-improvement plans.
---

# SEO Skill

## Core Principles
1. **Serve search intent.** Rankings follow pages that best satisfy what the searcher actually wants.
2. **Helpful, original, people-first content** - written by or reviewed by people with real experience (E-E-A-T: Experience, Expertise, Authoritativeness, Trustworthiness).
3. **Technical health is the foundation.** If search engines can't crawl, render, and index it, nothing else matters.
4. **Think in topics, not just keywords.** Build topical authority with connected, comprehensive content.
5. **Sustainable over tricks.** No keyword stuffing, hidden text, link schemes, or scaled low-quality content - these risk penalties.
6. **Measure and iterate.** SEO is a cycle: research -> publish -> measure -> improve.
7. **Verify current guidance.** Algorithms, features, and best practices change; check current documentation (Google Search Central) and recent data before asserting specifics.

## Workflow
1. Goals & baseline -> 2. Technical audit -> 3. Keyword & intent research -> 4. Content strategy -> 5. On-page optimization -> 6. Internal linking & architecture -> 7. Authority/link building -> 8. Measure & iterate.

## Step 1 - Goals & Baseline
- Business goals: leads, sales, signups, brand reach; target markets and languages.
- Current performance: organic traffic, conversions, top pages, rankings, indexed pages, backlinks.
- Tools: Google Search Console, Google Analytics, Bing Webmaster Tools, crawl tool (Screaming Frog, Sitebulb), keyword/backlink tools (Ahrefs, Semrush, Moz), PageSpeed Insights/Lighthouse.
- Competitors: who ranks for your target queries (SERP competitors, not just business competitors).

## Step 2 - Technical SEO Audit
**Crawlability & indexing**
- `robots.txt` doesn't block important resources; XML sitemap is clean, submitted, and lists only canonical 200-status indexable URLs.
- Check index coverage: "Crawled - not indexed," "Discovered - not indexed," soft 404s, duplicates, excluded pages.
- Proper status codes: 200 for live, 301 for permanent moves, 404/410 for gone; avoid redirect chains/loops; fix broken links.
- Canonical tags point to the preferred URL; handle parameters, pagination, faceted navigation, trailing slashes, http/https, www/non-www.
- `noindex` only where intended; no accidental noindex on live pages.

**Architecture & URLs**
- Shallow structure: key pages within ~3 clicks from the homepage.
- Short, descriptive, lowercase, hyphenated URLs; stable URLs; logical hierarchy.
- Breadcrumbs; no orphan pages (every page has internal links).

**Performance & Core Web Vitals**
- LCP (loading), INP (interactivity), CLS (visual stability) in the "good" range per current thresholds.
- Optimize images (modern formats, responsive sizes, lazy-loading below the fold), minimize/defer JS and CSS, use caching/CDN, fast server response.

**Mobile & rendering**
- Mobile-first: content and structured data parity with desktop; responsive; legible tap targets.
- Ensure critical content is in rendered HTML (watch client-side-only rendering); test with URL Inspection.

**Security & signals**
- HTTPS everywhere, no mixed content; avoid intrusive interstitials.

**International**
- `hreflang` with reciprocal tags and correct language-region codes; consistent canonicals; avoid auto-redirecting by IP.

## Step 3 - Keyword & Intent Research
- Seed topics from products, customer questions, sales calls, support tickets, forums, "People also ask," autocomplete, competitor pages, Search Console queries.
- Classify **intent**: informational, navigational, commercial investigation, transactional (and local).
- Evaluate: search volume (directional), difficulty, business value, current ranking, SERP features, trend/seasonality.
- **Analyze the SERP:** what content types rank (guides, lists, product pages, tools, videos)? What do they cover? What's the angle? That reveals intent and the bar to beat.
- Prioritize: high intent + business fit + realistic difficulty. Mix quick wins (positions 4-20) with long-term head terms.
- Group keywords into **clusters** mapped to one primary page each to avoid cannibalization.
- Keep a keyword map: keyword/cluster -> URL -> intent -> priority -> status.

## Step 4 - Content Strategy
- **Topic clusters:** pillar page (broad, comprehensive) + supporting cluster pages (specific subtopics) interlinked.
- Content types matched to intent: how-to, comparison, "best of," glossary, templates, calculators, case studies, product/category pages, landing pages.
- Differentiate with **information gain**: original data, first-hand experience, expert quotes, unique frameworks, clear examples, better visuals - not rewording the top results.
- Cover the topic completely: subtopics, questions, objections, next steps.
- Plan updates: refresh outdated high-potential pages; consolidate thin or overlapping content (merge + 301); prune only with care.
- Editorial standards: accuracy, citations to credible sources, author bios and credentials, publish and update dates, clear sourcing.
- Avoid scaled, unedited AI content made primarily to manipulate rankings; AI-assisted content must be accurate, reviewed, and genuinely useful.

## Step 5 - On-Page Optimization
- **Title tag:** unique, ~50-60 characters (display varies), primary keyword near the front, compelling and accurate.
- **Meta description:** ~150-160 characters; persuasive summary with a call to action (influences CTR, not a direct ranking factor).
- **H1:** one per page, matches intent; logical H2/H3 hierarchy that mirrors subtopics.
- **Intro:** answer the query quickly; set expectations; no fluff.
- **Body:** natural language, semantic variations, entities; scannable (short paragraphs, lists, tables, TL;DR); answer questions concisely (helps featured snippets and AI answers).
- **Images:** descriptive file names, alt text, compressed, dimensions set; video with transcripts where useful.
- **Links:** descriptive anchor text; link to relevant internal pages and authoritative external sources.
- **URL slug:** short and clear.
- **UX signals:** fast, readable, minimal intrusive ads, clear CTA.
- **E-E-A-T on page:** author, credentials, reviews, first-hand evidence, contact and about info, transparent policies.

## Step 6 - Internal Linking & Site Architecture
- Link from high-authority pages to priority pages with descriptive anchors.
- Every important page reachable via crawlable `<a href>` links; add contextual links within content; use hub pages and breadcrumbs.
- Find orphan pages and pages with few internal links (crawl data) and fix.
- Avoid excessive links per page or generic anchors ("click here").

## Step 7 - Structured Data & SERP Features
- Implement relevant **schema.org** markup in JSON-LD: Organization, WebSite, Article/BlogPosting, Product (offers, reviews), BreadcrumbList, FAQPage (limited display now), HowTo, LocalBusiness, Event, Recipe, VideoObject, etc.
- Markup must match visible content; validate with Rich Results Test and Schema Markup Validator. Don't mark up content users can't see.
- Target featured snippets and "People also ask" with concise definitions, step lists, and tables.

## Step 8 - Authority & Link Building
- Earn links with link-worthy assets: original research, tools, data, guides, expert commentary, PR, partnerships, integrations, community involvement.
- Tactics: digital PR, HARO-style expert responses, guest contributions with real value, broken-link and resource-page outreach, unlinked brand mentions, supplier/partner pages.
- Prioritize relevance and quality over volume; vary anchor text naturally.
- **Avoid:** paid links that pass PageRank without proper `rel` attributes, link exchanges at scale, PBNs, comment/forum spam. Disavow only for clear manipulative links when needed.

## Local SEO (if relevant)
- Complete and verified Google Business Profile: accurate NAP (name, address, phone), categories, hours, services, photos, posts, Q&A.
- Consistent citations; location pages with unique content (not doorway pages); local schema; embed map.
- Collect genuine reviews and respond professionally; never fake or incentivize improperly.

## E-commerce SEO (if relevant)
- Unique product descriptions, specs, images, reviews; Product schema; handle variants and faceted navigation with canonicals and crawl control; optimize category pages (intro copy, filters, internal links); manage out-of-stock and discontinued pages (keep, redirect, or 410 thoughtfully).

## AI Search & Answer Engines (GEO/AEO)
- Provide clear, factual, well-structured, quotable answers; use headings that mirror questions; summaries and definitions near the top.
- Strong entity signals: consistent brand/author info, structured data, authoritative citations, mentions across reputable sites.
- Ensure crawler access for the AI bots you want to allow (robots.txt policy decision); keep content accessible in HTML.
- Track brand and citation visibility in AI answers, not just blue-link rankings.

## Measurement & Iteration
- **KPIs:** organic sessions, non-brand clicks, impressions, average position/visibility, CTR, conversions and revenue from organic, indexed pages, Core Web Vitals, backlinks/referring domains, share of voice.
- Use Search Console queries/pages to find: high impressions + low CTR (improve titles/snippets), positions 8-20 (strengthen content/links), declining pages (refresh).
- Annotate changes (migrations, updates, releases); compare like-for-like periods; allow weeks to months for effects.
- A/B test titles and templates where traffic allows.

## Site Migration Safety
- Map every old URL to a new URL (1:1 301s); keep content and internal links equivalent; update canonicals, sitemaps, hreflang; crawl staging; monitor Search Console, crawl errors, and rankings closely after launch; keep old redirects for at least a year.

## Prioritization Framework
Rank tasks by **Impact x Confidence / Effort**. Typical order: (1) fix indexing/crawl blockers, (2) fix high-traffic page issues, (3) quick wins on titles/snippets and internal links, (4) content gaps and refreshes, (5) authority building, (6) long-term investments.

## Audit Report Format
1. **Executive summary:** health score/verdict, top 5 issues, expected impact.
2. **Findings** grouped by area (Technical, On-page, Content, Authority, UX) with: issue, evidence (URLs/screenshots/data), impact (High/Med/Low), fix, effort.
3. **Quick wins (0-30 days)** vs **Strategic projects (30-180 days).**
4. **Keyword opportunity map and content gaps.**
5. **Measurement plan and KPIs.**

## Common Mistakes
- Targeting keywords without checking intent or SERP
- Multiple pages competing for the same query (cannibalization)
- Thin, duplicate, or purely AI-generated filler content
- Blocking CSS/JS or whole sections via robots.txt; accidental noindex
- Slow, bloated pages; poor mobile experience
- Chasing links over content quality; buying links
- Changing URLs without redirects
- Expecting immediate results; no tracking

## Checklist
- [ ] Goals, baseline, and tracking (Search Console + Analytics) in place
- [ ] Crawl/index issues fixed; sitemap and canonicals correct
- [ ] Core Web Vitals and mobile experience healthy
- [ ] Keyword clusters mapped to single target URLs by intent
- [ ] Titles, metas, headings, and content optimized and original
- [ ] Internal links, schema, and E-E-A-T signals implemented
- [ ] Link-earning plan that complies with guidelines
- [ ] Reporting cadence and prioritized backlog (impact x confidence / effort)
