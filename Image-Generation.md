---
name: image-generation
description: Write effective prompts and workflows for AI image generation and editing - subject, style, composition, lighting, camera, color, text rendering, references, iteration, negative constraints, consistency, and responsible use. Use when creating or refining prompts for text-to-image, image-to-image, inpainting, and design assets.
---

# Image Generation Skill

## Core Principles
1. **Be specific about what matters; leave room for the model on what doesn't.** Over-specified prompts can conflict; under-specified ones are generic.
2. **Describe the picture, not the idea.** Convert abstract concepts into visible subjects, settings, actions, and details.
3. **Structure beats length.** A clear, ordered description outperforms a pile of keywords.
4. **Iterate deliberately.** Change one or two things at a time and keep what works.
5. **Know the purpose.** Social post, product mockup, concept art, slide illustration, and print poster need different composition, aspect ratio, and resolution.
6. **Describe in positive terms.** Say what you want rather than listing what to avoid (unless the tool supports a separate negative prompt).
7. **Use responsibly.** Original concepts only; respect IP, privacy, and consent; don't deceive with realistic fakes.

## The Prompt Formula
Order from most to least important:
**[Subject + action] + [setting/context] + [style/medium] + [composition/camera] + [lighting] + [color/mood] + [details/materials] + [technical/output specs]**

Example:
> A weathered fisherman repairing a blue wooden boat on a foggy harbor dock at dawn, documentary photograph, 35mm lens, shallow depth of field, eye-level shot, soft diffused morning light, muted teal and warm amber tones, visible rope texture and salt-stained wood, natural film grain, 3:2 horizontal.

### 1. Subject & Action
- Who/what is the main subject? How many? Age, clothing, posture, expression, material, color, size, condition.
- Specify the action or pose (verbs help): "laughing while pouring tea," not just "woman."
- Mention secondary elements and their relationship ("a small dog sleeping at her feet").
- For products: shape, material, finish, branding-free surfaces (if no logos desired), angle.

### 2. Setting & Context
- Location, time of day, weather, season, era, background elements, scale and depth cues, environment mood.
- Foreground / midground / background layering adds depth.

### 3. Style & Medium
- **Photography:** documentary, editorial, studio product, macro, aerial/drone, street, architectural, film stock look, vintage Polaroid.
- **Illustration/art:** watercolor, gouache, ink linework, risograph, flat vector, isometric, low-poly 3D, claymation look, paper-cut collage, oil painting, pencil sketch, pixel art, storybook, technical diagram, blueprint, concept art, matte painting.
- **Design:** minimal icon set, editorial poster, infographic style, packaging mockup, UI illustration, sticker sheet.
- Name general art movements or techniques (Art Deco, Bauhaus, Ukiyo-e inspired, mid-century modern) rather than imitating a specific living artist's name; avoid copying a specific copyrighted work or character.

### 4. Composition & Camera
- **Framing:** extreme close-up, close-up, medium shot, wide shot, full body, bird's-eye, top-down flat lay, low angle, high angle, over-the-shoulder, Dutch angle, centered, rule of thirds, symmetrical, negative space on the left/right for text.
- **Lens/camera cues:** 24mm wide, 50mm natural, 85mm portrait, 200mm telephoto compression, macro; shallow vs deep depth of field; bokeh; tilt-shift.
- **Aspect ratio:** 1:1 (social/profile), 4:5 (portrait feed), 9:16 (stories/reels), 16:9 (video/hero banner), 3:2 (photo), 2:3 (poster). Choose before generating; reserve negative space for headlines if needed.

### 5. Lighting
- Golden hour, blue hour, overcast soft light, hard noon sun, backlit rim light, Rembrandt, softbox studio, neon signage glow, candlelight, moonlight, volumetric rays, dramatic chiaroscuro, high-key (bright, airy) vs low-key (dark, moody).
- Light direction and quality determine realism and mood more than almost anything else.

### 6. Color & Mood
- Palette: "muted earth tones," "monochrome blue," "pastel pink and mint," "high-contrast black and neon yellow," brand hex colors if the tool supports text matching (verify output).
- Mood words: serene, tense, nostalgic, playful, futuristic, cozy, majestic, melancholic.
- Color harmony (complementary, analogous) and contrast level.

### 7. Details & Materials
- Texture and surface: brushed aluminum, linen, matte ceramic, wet asphalt, frosted glass, hand-knit wool, weathered paint.
- Small, concrete details increase believability; avoid piling dozens of competing details.

### 8. Text in Images
- Put exact text in quotation marks and specify placement, font style, color, and size ("the headline 'OPEN LATE' in bold white sans-serif capital letters across the top third").
- Keep text short (a few words); long passages often render incorrectly. Verify spelling, and add real text in a design tool afterward when precision matters.
- For layouts requiring copy, leave clean negative space and place text in post.

## Workflows by Task

### Text-to-Image (from scratch)
1. Define purpose, aspect ratio, and key message.
2. Write the first prompt with the formula.
3. Generate multiple variations; pick the best direction.
4. Refine one variable at a time (lighting, angle, style, color).
5. Upscale/enhance; do light retouching in an editor; check for artifacts (hands, text, symmetry, extra objects).

### Image-to-Image / Reference-Guided
- Provide a reference for composition, pose, palette, or style; state exactly what to preserve ("keep the pose and layout") and what to change ("make it a watercolor illustration at sunset").
- Control strength: lower = closer to the original; higher = more transformation.
- Use your own images or ones you have rights to; don't use images of real people without consent.

### Editing / Inpainting / Outpainting
- Mask only the area to change; describe the replacement in context ("replace the empty table with a vase of white tulips, matching the soft window light").
- Match lighting, perspective, scale, and grain of the surrounding image.
- Outpaint to extend canvas in a chosen direction with consistent style.
- Remove objects by describing the clean background to fill.

### Product & Marketing Imagery
- Clean studio: seamless backdrop, soft shadows, consistent lighting, 3/4 angle, hero shot + detail shots.
- Lifestyle: product in realistic use, appropriate context, target audience cues.
- Avoid generating real brand logos or trademarked packaging; keep placeholder/branding-neutral and composite real assets afterward. Don't fabricate product claims or misleading "before/after" results.

### Character & Brand Consistency (original characters)
- Write a **character sheet** and reuse it verbatim: age, build, face shape, hair, skin tone, eyes, signature clothing and colors, accessories, personality/pose style.
- Fix the **style anchor** (medium, line weight, palette, lighting) and reuse it.
- Use reference images or seed/consistency features when available; generate turnarounds (front/side/back) and expression sheets first.
- Keep backgrounds simple while establishing the character, then vary scenes.
- Create **original** characters; do not recreate existing copyrighted or trademarked characters.

### Infographics & UI/Diagram Illustrations
- AI is better at atmosphere and illustration than precise data or text. Generate backgrounds/icons/illustrative elements and assemble charts, labels, and exact text in a design tool.

### Storyboards & Sequences
- Define scene list, consistent character/setting descriptions, shot types, and a continuity checklist (costume, time of day, props, color grade).

## Negative Constraints & Fixes
- If supported, use a negative prompt for: extra fingers, distorted hands, blurry, low resolution, watermark, text artifacts, duplicate subjects, cropped head.
- If no negative prompt, rephrase positively: "clean uncluttered background," "sharp focus," "five fingers on each hand, natural anatomy."
- Common issues and fixes:
  | Problem | Fix |
  |---|---|
  | Generic look | Add specific medium, lighting, lens, materials, and a distinct mood |
  | Messy composition | State framing, focal point, negative space, fewer elements |
  | Wrong anatomy/hands | Simplify pose, hide hands (pockets, props), regenerate or inpaint |
  | Garbled text | Shorten text, use quotes and placement, or add text in post |
  | Style drift | Repeat style anchor; use reference; reduce conflicting style words |
  | Wrong colors | Name colors explicitly; mention dominant/accent; use reference |
  | Over-saturated "AI shine" | Ask for natural, matte, subtle grain, realistic skin texture, muted palette |
  | Subject too small | Specify "close-up"/"fills the frame" |
  | Inconsistent objects | Reduce object count; describe each clearly; inpaint corrections |

## Prompt Writing Tips
- Use natural, descriptive sentences or comma-separated phrases consistently, per what the tool responds to best.
- Lead with the most important elements; avoid contradictory instructions ("minimalist" + "highly detailed ornate").
- Use concrete nouns and adjectives; avoid vague superlatives ("beautiful, amazing, epic" add little).
- Keep a **prompt log**: prompt, settings (model, seed, aspect ratio, strength), output notes, and what changed - makes iteration reproducible.
- Build a reusable **style library** (lighting setups, palettes, camera looks) and **prompt templates** with placeholders.
- Generate at the right resolution and upscale last; export in appropriate formats (PNG for transparency, JPG/WebP for web, TIFF/PDF for print).

## Prompt Templates
**Photoreal portrait:** "[Age/description] [person] with [distinct features], [expression], wearing [clothing], [setting], portrait photograph, 85mm lens, f/1.8 shallow depth of field, [lighting], natural skin texture, [color palette], [aspect ratio]." (Use fictional/consented subjects; don't depict real, identifiable people.)
**Product hero shot:** "[Product, material, color] on [surface], studio product photography, 3/4 angle, softbox lighting with soft shadow, seamless [color] backdrop, crisp detail, minimal, [aspect ratio]."
**Illustration:** "[Subject doing action] in [setting], [medium] illustration, [line/texture qualities], [limited palette], [mood], flat shading, [aspect ratio]."
**Isometric scene:** "Isometric 3D illustration of [scene], clean low-poly style, soft pastel palette of [colors], soft shadows, white background, high detail."
**Hero banner with space for text:** "[Scene], wide 16:9 composition, subject on the right third, large clean negative space on the left, soft gradient lighting, [mood/palette]."
**Pattern/texture:** "Seamless tileable pattern of [motif], [style], [palette], flat lay, evenly spaced, no borders."

## Quality Review Checklist (before using an image)
- [ ] Matches the brief, message, and audience
- [ ] Composition, focal point, and negative space work for the use
- [ ] Anatomy, objects, perspective, reflections, and shadows look right
- [ ] Text is correct (or intentionally added in post)
- [ ] No unintended logos, watermarks, or resemblance to real people, characters, or protected works
- [ ] Resolution and format suitable for the destination
- [ ] Accessible: alt text written; sufficient contrast for overlaid text
- [ ] Disclosure and rights requirements met (platform rules, client policies, provenance/labeling where required)

## Responsible Use
- **Rights & originality:** don't reproduce existing artworks, logos, album/book covers, or recognizable copyrighted characters; create original designs; check platform and commercial-use terms.
- **People & consent:** don't generate realistic images of real people (public or private) in misleading, sexual, or harmful contexts; don't create deceptive deepfakes, fake documents, fake IDs, fake news imagery, or fabricated "evidence."
- **No minors in sexualized or inappropriate contexts, ever.**
- **Bias & representation:** specify diverse, respectful depictions; check outputs for stereotypes.
- **Transparency:** label AI-generated imagery where expected or required; keep provenance metadata (e.g., C2PA) when available.
- **Privacy & sensitive data:** don't upload private images of others without permission.
- **Safety:** avoid generating content intended to facilitate harm.

## Common Mistakes
- Vague prompts ("a cool futuristic city") with no camera, light, or mood
- Contradictory or overloaded prompts
- Changing many variables per iteration
- Expecting exact text, logos, and data accuracy from the model
- Ignoring aspect ratio and intended use until after generation
- Copying a specific artist, brand, or character instead of developing an original style
- Skipping review for artifacts and unintended content
