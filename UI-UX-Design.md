---
name: ui-ux-design
description: Research, design, evaluate, and hand off user interfaces and experiences - user research, information architecture, flows, wireframes, visual UI, interaction patterns, design systems, accessibility, usability testing, and UX writing. Use for app/web design, redesigns, UX audits, and design critiques.
---

# UI/UX Design Skill

## Core Principles
1. **Design for real users and real tasks.** Start with who they are, what they're trying to do, and in what context.
2. **Evidence over opinion.** Validate with research and testing; assumptions are hypotheses.
3. **Clarity over cleverness.** Users should understand where they are, what they can do, and what happens next.
4. **Reduce cognitive load.** Fewer choices, progressive disclosure, familiar patterns, sensible defaults.
5. **Accessibility is a requirement, not a feature.** Design for the full range of abilities and situations.
6. **Consistency builds learnability.** Reuse patterns, components, and language.
7. **Iterate.** Design -> prototype -> test -> refine. First ideas are rarely the best.
8. **Business goals and user needs both matter.** Good design aligns them without manipulating users (no dark patterns).

## The Process
**Discover -> Define -> Ideate -> Prototype -> Test -> Build/Handoff -> Measure -> Iterate**

### 1. Discover (Research)
- **Goals:** product/business goals, success metrics, constraints, stakeholders.
- **Methods:** user interviews, contextual inquiry, surveys, analytics review, support ticket analysis, competitor/heuristic review, diary studies, card sorting (for IA).
- Interview rules: open-ended questions, ask about past behavior (not hypothetical opinions), listen for pain points and workarounds, avoid leading questions, 5-8 participants per segment reveals most patterns.
- Synthesize: affinity mapping, insights, **personas** (evidence-based), **jobs-to-be-done**, **journey maps** (stages, actions, thoughts, emotions, pain points, opportunities).

### 2. Define
- Problem statement / "How might we..." questions.
- Prioritize needs and scope; define success metrics (task success rate, time on task, error rate, SUS, conversion, retention, NPS/CSAT).
- Write user stories and acceptance criteria; define key scenarios and edge cases.

### 3. Ideate & Structure
- **Information architecture:** group content by users' mental models; navigation labels in user language; sitemap; hierarchy depth; search and wayfinding.
- **User flows:** map entry points, decisions, happy path, errors, and exits for key tasks; minimize steps.
- Sketch many ideas quickly (crazy 8s); compare options against goals; choose and refine.

### 4. Prototype
- **Low-fidelity wireframes:** layout, content hierarchy, and flow without visual styling - cheap to change.
- **Mid/high-fidelity UI + interactive prototype** for testing key flows.
- Use real content (not lorem ipsum) - content shapes layout.
- Cover all states: default, empty, loading, partial, error, success, disabled, offline, long text, permission-denied.

### 5. Test & Evaluate
- **Usability testing:** 5 users per round uncovers most major issues; give realistic tasks without hints; observe, think-aloud; measure completion, time, errors, satisfaction.
- **Heuristic evaluation** (Nielsen's 10): visibility of system status; match with the real world; user control and freedom; consistency and standards; error prevention; recognition rather than recall; flexibility and efficiency; aesthetic and minimalist design; help users recover from errors; help and documentation.
- Other methods: first-click tests, tree tests, A/B tests, analytics funnels, session recordings, accessibility audits.
- Prioritize issues by severity (frequency x impact x persistence) and fix the biggest blockers first.

## UI Design Fundamentals

### Layout & Hierarchy
- Use a **grid** (e.g., 12-column desktop, 4-column mobile) and a consistent **spacing scale** (4 or 8 px base).
- Clear visual hierarchy: primary action prominent, secondary subdued, tertiary text/links.
- Group related items (proximity), separate sections with space and dividers, align consistently.
- Reading patterns (F/Z); place key info and actions where users expect them.
- **Responsive design:** mobile-first, breakpoints driven by content, fluid layouts, touch targets >= 44x44 px (iOS) / 48x48 dp (Android), thumb-reach zones.

### Typography
- Type scale (e.g., 12/14/16/20/24/32/40); body 16 px+ on web; line height 1.4-1.6; line length 45-75 characters.
- 1-2 typefaces; use weight and size for hierarchy; avoid all-caps long text.
- System or web-safe fallbacks; support dynamic type/zoom to 200%.

### Color
- Neutral base + one primary brand color + semantic colors (success, warning, error, info).
- **Contrast:** 4.5:1 for normal text, 3:1 for large text and UI components (WCAG 2.2 AA).
- Never rely on color alone (add icons, text, patterns).
- Provide dark mode with checked contrast; define tokens, not hex values scattered everywhere.

### Components & Patterns
- Buttons (clear verb labels; one primary per view), forms, inputs, selects, toggles, checkboxes/radios, tabs, modals, toasts, tooltips, cards, tables, lists, navigation (top, side, bottom tab bar), search, pagination/infinite scroll, breadcrumbs, empty states, skeleton loaders.
- Follow platform conventions (iOS Human Interface Guidelines, Material Design, web standards) unless there's a strong, tested reason not to.
- **Forms:** single column, labels above fields (always visible, not placeholder-only), mark optional vs required, inline validation with clear messages, sensible defaults, input types/masks, autofill support, minimal fields, progress for long flows, preserve data on error.
- **Navigation:** limit primary items (about 5-7), indicate current location, keep consistent across pages.
- **Feedback:** immediate response to actions (< 100 ms feels instant); progress indicators for waits > 1 s; confirmations for destructive actions with undo preferred over "Are you sure?".
- **Error messages:** say what happened, why, and how to fix it, in plain language; never blame the user.
- **Empty states:** explain and offer the next step.
- **Onboarding:** teach in context, progressive, skippable; show value quickly.

### Motion & Interaction
- Purposeful animation: guide attention, show relationships, confirm actions; 150-300 ms typical; ease-in-out; respect "reduce motion" preferences.
- Provide hover, focus, active, and disabled states; support keyboard, touch, and pointer; gestures need visible alternatives.

## Accessibility (WCAG 2.2 AA baseline)
- **Perceivable:** text alternatives for images, captions/transcripts, contrast, resizable text, no content that depends on color/sound alone.
- **Operable:** full keyboard access, visible focus indicator, logical tab order, no keyboard traps, skip links, sufficient time, no flashing > 3 per second, target size adequate, alternatives to drag gestures.
- **Understandable:** plain language, consistent navigation, predictable behavior, clear labels and instructions, error prevention and suggestions.
- **Robust:** semantic HTML, correct ARIA only when needed (native elements first), labels and names for controls, status messages announced to screen readers.
- Test with keyboard-only, screen readers (VoiceOver, NVDA, TalkBack), zoom, high-contrast, and automated tools (axe, Lighthouse) - automation catches only a portion of issues.
- Consider situational and temporary limitations (glare, one hand, noisy room) and cognitive accessibility.

## UX Writing (Microcopy)
- Use clear, concise, user-centered language; verbs on buttons ("Save changes," not "Submit"); consistent terminology; sentence case.
- Explain why you need sensitive information; avoid jargon, blame, or humor in error states.
- Localization-ready: avoid concatenated strings, leave room for text expansion (30%+).

## Design Systems & Handoff
- **Design tokens** (color, type, spacing, radius, elevation, motion) -> **components** (with variants, states, usage rules, accessibility notes) -> **patterns/templates**.
- Document: when to use / not use, anatomy, behavior, content guidelines, code references.
- Name layers and components consistently; use auto-layout/constraints; annotate interactions, edge cases, and responsive behavior.
- Collaborate with developers early; review builds against designs; keep a single source of truth; version the system and communicate changes.

## Mobile & Platform Notes
- Mobile: one primary task per screen; thumb-friendly controls; minimize typing; offline and low-connectivity states; permissions requested in context with explanation; respect safe areas.
- Web: performance (fast load), SEO-friendly structure, responsive behavior, browser support matrix.
- Desktop/complex tools: keyboard shortcuts, density options, bulk actions, undo/redo, customization.
- Data-heavy dashboards: clear primary metric, progressive detail, consistent filters, honest charts, accessible tables.

## Ethical Design
- No dark patterns: confirmshaming, hidden costs, forced continuity, disguised ads, obstructive cancellation, preselected extras.
- Privacy by design: collect minimal data, transparent consent, easy controls.
- Inclusive: diverse users, languages, cultures, abilities; avoid biased imagery and assumptions.
- Consider addictive-pattern risk and user wellbeing.

## UX Audit Report Format
1. **Summary:** overall assessment, top issues, quick wins.
2. **Findings:** location/screen, issue, heuristic/principle violated, evidence, severity (Critical/High/Medium/Low), recommendation, effort.
3. **Accessibility findings** mapped to WCAG criteria.
4. **Prioritized roadmap** (quick wins vs structural changes) and metrics to track.

## Design Critique Format
*Goal fit -> What works -> Issues (hierarchy, clarity, consistency, accessibility, flow) -> Specific suggestions -> Questions for the team.* Critique against user goals, not personal taste.

## Common Mistakes
- Designing without research; assuming "I am the user"
- Skipping empty, error, and loading states
- Hiding key actions in icons without labels
- Placeholder text as label; low-contrast gray text
- Overloading screens; unclear primary action
- Inconsistent components and copy
- Ignoring mobile and accessibility until late
- Dark patterns; designing only for the happy path
- Treating handoff as the end instead of measuring outcomes

## Checklist
- [ ] Users, goals, and success metrics defined from evidence
- [ ] Clear IA, flows, and task paths with minimal steps
- [ ] All states and edge cases designed
- [ ] Visual hierarchy, spacing, type, and color systematic (tokens)
- [ ] WCAG 2.2 AA checked; keyboard and screen reader tested
- [ ] Usability tested with representative users; issues prioritized
- [ ] Microcopy clear and consistent
- [ ] Components documented; developer handoff annotated
- [ ] Post-launch metrics and iteration plan
