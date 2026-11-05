---
name: powerpoint-presentations
description: Design and build clear, persuasive, professional slide decks - storyline, slide content, visuals, design, speaker notes, and delivery. Use for business, pitch, executive, technical, training, academic, and conference presentations.
---

# PowerPoint / Presentations Skill

## Core Principles
1. **Message before slides.** Decide the one thing the audience must think, feel, or do - then build backward.
2. **One slide = one idea.** If you need "and" in the title, split it.
3. **Slides support the speaker; they are not the script.** Dense documents belong in a handout or appendix.
4. **Titles are conclusions** (action titles), not topics: "Churn fell 30% after onboarding redesign," not "Churn."
5. **Show, don't list.** Prefer a chart, diagram, or image over a bullet wall.
6. **Design is clarity.** Remove everything that doesn't help understanding.
7. **Know the audience** - their knowledge, priorities, objections, and time.

## Phase 1 - Brief
Capture before building:
- **Audience:** who, size, seniority, prior knowledge, what they care about, likely objections
- **Objective:** inform / persuade / decide / train / inspire - and the desired action
- **Context:** time limit, live vs sent-ahead (reading deck vs speaking deck), room/screen, formality
- **Key message** in one sentence
- **Assets:** data, brand template, logos, existing material
- **Constraints:** slide count, language, compliance

Rule of thumb: ~1-2 minutes per content slide; a 20-minute talk = ~10-12 slides.

## Phase 2 - Storyline
Draft the narrative as a list of action titles *before* any design - it should read as a coherent argument.

### Frameworks
- **Pyramid Principle:** answer first -> 3 supporting arguments -> evidence. Best for executives.
- **SCQA:** Situation -> Complication -> Question -> Answer. Best for opening a business case.
- **Problem -> Solution -> Benefit -> Proof -> Ask.** Best for sales/pitch.
- **Before -> After -> Bridge.** Best for change proposals.
- **Story arc:** hook -> tension -> turning point -> resolution -> call to action. Best for keynotes.
- **What? So what? Now what?** Best for updates and insight reviews.

### Standard Deck Skeleton
1. Title
2. Executive summary / key takeaway (the answer up front)
3. Context / problem (why this matters)
4. Core content - 3-5 sections, each with an action-title slide and evidence
5. Recommendation / solution / roadmap
6. Risks & mitigations (if decision deck)
7. Next steps / the ask (owner, date, decision needed)
8. Appendix (backup data, methodology, detail)

**Test:** Read only the slide titles in order. Do they tell the full story? If not, rewrite.

## Phase 3 - Slide Content Rules
- **Title:** full-sentence takeaway, <= 2 lines (~12-15 words).
- **Body:** <= 3-5 short points; <= ~30-40 words per slide for speaking decks (more only for reading decks).
- **Bullets:** parallel structure, start with a strong verb or noun, no full paragraphs.
- **Numbers:** round sensibly, highlight the one that matters, give comparison/context.
- **Sources:** footnote under every data slide.
- **Consistency:** terms, units, date formats, capitalization, number formatting.
- **Progressive disclosure:** build complex diagrams in steps; use reveal sparingly.
- **Transitions:** use minimal, consistent; avoid distracting effects.

## Choosing the Right Visual
| Goal | Visual |
|---|---|
| Trend over time | Line chart |
| Compare categories | Bar/column chart (sorted) |
| Part-to-whole (few parts) | Stacked bar or simple donut (<= 5 slices) |
| Distribution | Histogram / box plot |
| Relationship | Scatter plot |
| Change bridge (A -> B) | Waterfall |
| Process / flow | Flowchart, chevrons |
| Timeline / roadmap | Gantt-style or milestone line |
| Structure / hierarchy | Org chart, tree |
| Positioning | 2x2 matrix |
| Comparison of options | Table with highlighted recommendation |
| Geography | Map |
| Single powerful number | Big-number callout |
| Concept explanation | Simple icon diagram, photo, analogy |

### Chart Best Practices
- Title states the insight; label axes and units; start bars at zero.
- Direct labels instead of legends where possible; highlight the key series with color, mute others in gray.
- Remove chart junk: gridlines, 3D, shadows, redundant borders.
- One message per chart; annotate the key point with a callout.
- Never truncate axes to exaggerate; keep scales comparable across slides.

## Phase 4 - Design System
- **Layout:** align to a grid; generous white space; consistent margins; left-aligned text; clear visual hierarchy (title > key visual > supporting text).
- **Typography:** 1-2 font families max. Title 28-40 pt, body >= 18-24 pt, footnotes >= 10-12 pt. Sans-serif for screens. Avoid ALL CAPS paragraphs.
- **Color:** 1 primary + 1-2 accent + neutrals. Use accent only to direct attention. Keep brand colors consistent.
- **Contrast:** WCAG AA at least (4.5:1 for text). Don't rely on color alone (add labels/patterns) - consider color-blind viewers (avoid red/green-only encoding).
- **Imagery:** high-resolution, relevant, consistent style; no stretched or pixelated images; respect licenses; no cliche stock clutter.
- **Icons:** one consistent set and style.
- **Master slides/templates:** use them; don't manually position repeating elements; apply layouts for consistency; name layouts logically.
- **Accessibility:** alt text on images/charts, logical reading order, slide titles on every slide, sufficient font size, captions for video.

## Phase 5 - Speaker Notes & Delivery
- Notes: key talking points, transitions, data sources, anticipated questions - not a verbatim script.
- Open with a hook (question, surprising fact, story). State the roadmap briefly. Close with the ask.
- Speak to the audience, not the slide; pause on key points; rehearse out loud and time it.
- Prepare Q&A backup slides for likely challenges.
- Have a plan B (PDF export, offline copy, remote-friendly version).

## Deck Types - Quick Guides
- **Executive update:** answer on slide 2, 5-8 slides, decisions needed explicit, appendix for detail.
- **Investor pitch (10-12 slides):** problem, solution, product, market size, business model, traction, go-to-market, competition, team, financials, the ask/use of funds.
- **Sales deck:** customer pain -> impact -> your solution -> proof (case studies, ROI) -> pricing/next steps.
- **Technical deck:** architecture diagrams, trade-offs, benchmarks with methodology, decision rationale, risks.
- **Training/workshop:** learning objectives, short segments, activities, checks for understanding, summary, resources.
- **Academic/conference:** motivation, research question, method, results (figure-led), implications, limitations, future work.
- **Reading deck (sent ahead):** denser text allowed, self-explanatory titles and annotations, executive summary up front.

## Building Files (Tooling Notes)
- Prefer a real .pptx using the project's template/master. With python-pptx: use layouts and placeholders, set text via placeholders, add native charts (editable) instead of pasted images when possible, set alt text, and keep fonts to those available on the target machine.
- Render slides to images and visually inspect for overflow, overlap, alignment, and legibility.
- Export a PDF copy for sharing.
- If building from structured data, keep content in a data file separate from layout code so edits are easy.

## Common Mistakes
- Topic titles instead of conclusions
- Walls of text; reading the slides aloud
- Too many fonts/colors/effects; low-contrast text; tiny fonts
- Unlabeled charts; 3D/pie-chart overuse; truncated axes
- Inconsistent alignment, spacing, and styling
- No clear ask or next step
- Starting in PowerPoint instead of with the story
- Raw data dumps without a "so what"

## QA Checklist
- [ ] Objective and audience-defined; key message in one sentence
- [ ] Titles alone tell the story
- [ ] One idea per slide; minimal text
- [ ] Every chart has an insight title, labels, units, and source
- [ ] Consistent fonts, colors, spacing, and alignment (uses master)
- [ ] Contrast and font sizes meet accessibility standards; alt text added
- [ ] Numbers verified; spelling and grammar proofread
- [ ] Speaker notes and Q&A backup prepared
- [ ] Timing rehearsed; clear call to action
- [ ] Exported and tested on the target device
