---
name: video-generation
description: Plan and prompt AI video generation and production - concepts, scripts, shot lists, camera and motion language, scene and character consistency, audio, image-to-video, editing and assembly, and responsible use. Use for text-to-video, image-to-video, short-form content, ads, explainers, and storyboards.
---

# Video Generation Skill

## Core Principles
1. **Story and purpose first.** A clear message, audience, and call to action beat flashy visuals.
2. **Think in shots.** Video is a sequence of short, controlled shots edited together - not one long generation.
3. **Describe motion explicitly.** Subject action, camera movement, and timing are what make video different from images.
4. **Keep each shot simple.** One subject, one main action, one camera move per clip. Complexity multiplies artifacts.
5. **Design for consistency.** Characters, wardrobe, setting, lighting, and style must stay stable across shots.
6. **Plan for iteration.** Generate options, select the best takes, fix in editing.
7. **Sound is half the experience.** Plan voiceover, music, and effects as part of the design.
8. **Use responsibly.** Original content, consent, labeling, and no deception.

## Workflow Overview
**Brief -> Concept & script -> Storyboard/shot list -> Asset prep (reference images, style, character sheets) -> Generate shots -> Select & refine -> Edit/assemble -> Audio, captions, color -> Review -> Export & distribute -> Measure**

## Step 1 - Brief
- **Goal & CTA:** inform, sell, entertain, onboard; what should the viewer do after?
- **Audience & platform:** TikTok/Reels/Shorts (9:16, 15-60 s), YouTube (16:9, any length), LinkedIn (1:1 or 4:5, 30-90 s), website hero (16:9 loop), ads (6-30 s variants).
- **Length & pacing:** short-form: hook in the first 1-2 seconds, new visual every 2-4 s; explainers: 60-120 s; ads: front-load the message.
- **Tone & style:** cinematic, documentary, playful, minimal motion graphics, animated illustration, product demo.
- **Constraints:** budget, deadline, brand guidelines, legal/compliance, accessibility (captions), languages.

## Step 2 - Concept & Script
- **Hook -> Promise/Problem -> Value/Story -> Proof -> CTA.**
- Write the **script in two columns**: Visuals | Audio (voiceover/dialogue/sound). Time each beat (words per second: ~2.5 spoken words/second).
- Keep VO conversational, short sentences; read aloud to check pacing.
- Choose a **visual approach** that fits what the tools do well: atmospheric b-roll, stylized animation, product hero shots, abstract/metaphorical scenes, short character actions. Use real footage, screen recordings, or motion graphics for precise UI, data, text, or logos.

## Step 3 - Storyboard & Shot List
For each shot, define:
| Field | Example |
|---|---|
| Shot # & duration | 03 - 4 s |
| Shot type/framing | Medium close-up |
| Subject & action | A barista pours steamed milk into a latte, forming a leaf |
| Camera movement | Slow push-in |
| Setting & lighting | Sunlit cafe counter, warm morning light |
| Style/mood | Cozy, cinematic, shallow depth of field |
| Audio | Soft acoustic guitar, pour sound, VO line 2 |
| Transition | Cut on action to shot 04 |
- Typical AI clip lengths are short (roughly 4-10 seconds per generation, tool-dependent); plan edits around that.
- Vary shot sizes (wide establishing -> medium -> close-up detail) for rhythm; maintain screen direction continuity.

## Step 4 - Prompting Video Models

### Prompt Structure
**[Shot type + subject + action] + [setting] + [camera movement] + [lighting/mood] + [style/medium] + [color] + [details] + [duration/aspect/specs]**

Example:
> Medium close-up of a young chef in a white apron plating a colorful salad in a bright modern kitchen. Slow dolly-in from the front, shallow depth of field, soft window light from the left, warm natural tones, cinematic commercial style, crisp food detail, 16:9, 6 seconds.

### Camera Language
- **Movement:** static/locked-off, pan (left/right), tilt (up/down), dolly in/out, truck (side), crane/jib up/down, orbit/arc around subject, handheld (subtle shake), tracking/follow shot, whip pan, zoom (optical), drone fly-over, rack focus, parallax.
- **Speed & feel:** slow, smooth, steady, gentle, fast, energetic.
- **Framing:** extreme wide, wide, full, medium, close-up, extreme close-up, POV, over-the-shoulder, top-down.
- **Lens:** wide-angle (dynamic, distortion), 50mm (natural), telephoto (compressed), macro.

### Subject Motion
- Use clear verbs and pacing: "walks slowly toward camera," "turns and smiles," "steam rises from the cup," "leaves sway in a gentle breeze," "waves crash and recede."
- Limit to one primary action per clip; avoid complex multi-person interactions, fast intricate hand actions, or precise physics when you need reliability.
- Describe start and end states for transitions ("starts with the door closed; the door opens to reveal sunlight").

### Environment & Atmosphere
- Time of day, weather, particles (dust, mist, rain), background motion (traffic, crowds, water), depth layers.

### Style & Look
- Live-action cinematic, documentary, commercial, vintage film, anime-inspired original style, 3D animation, claymation, motion-graphic, hand-drawn animation, stop-motion look, vaporwave, noir. Keep one consistent style anchor for the whole project.
- Avoid copying a specific existing film/character/brand style or IP; describe the qualities (lighting, palette, pacing) instead.

### Audio Prompts (if the tool generates audio)
- Specify ambient sound, effects, music mood, and any spoken lines in quotes with who says them and tone; keep dialogue short. Verify lip-sync and clarity; often better to record/produce VO separately.

## Step 5 - Generation Modes
- **Text-to-video:** fastest for concepts and b-roll; less control over exact appearance.
- **Image-to-video:** start from a carefully crafted still (from an image model or photo you own) to lock composition, character, and style; prompt only the motion and camera. Best for consistency and brand control.
- **First/last-frame control:** define start and end images to guide transitions.
- **Video-to-video / style transfer:** apply a style or modify an existing clip; keep the source rights-cleared.
- **Reference-based (characters/objects):** provide reference images to keep identity consistent when supported.
- **Extension:** continue a clip from its last frame; chain carefully to avoid drift.
- **Lip-sync/avatars:** use consented, licensed avatars or your own likeness with permission; disclose AI use.

## Step 6 - Consistency Across Shots
- Build a **style bible**: look, palette, lighting, lens language, motion pace, aspect ratio.
- Build **character sheets** (original characters): face, hair, skin tone, build, outfit, accessories, age; reuse the exact description in every prompt; generate reference stills first and use image-to-video.
- Fix **setting details** (location, props, time of day) and repeat them.
- Use the same seed/model/settings where possible; keep shots short to limit drift.
- Cut away from tricky moments (hands, faces in profile, text) and rely on cutaways/b-roll.
- Color grade and match in editing to unify shots.

## Step 7 - Selecting & Fixing Takes
- Generate 3-5 variants per shot; choose by: subject stability, natural motion, no morphing/flicker, face/hand integrity, no stray text/logos, composition, continuity.
- Common issues and fixes:
  | Issue | Fix |
  |---|---|
  | Morphing/warping subjects | Shorten clip, simplify action, use image-to-video, reduce camera move |
  | Jittery/unnatural motion | Slow the motion, specify "smooth," lower complexity, change seed |
  | Face/hand artifacts | Wider shot, obscure hands, cut away quickly, regenerate |
  | Inconsistent character | Reference images, tighter character description, image-to-video |
  | Text/logo gibberish | Add real text/logos in editing |
  | Camera ignores instructions | Use simpler, standard camera terms; one move only |
  | Flicker/texture crawl | Reduce fine patterns, add stabilization/denoise in post |
  | Physics errors | Reframe the shot to avoid the problem or use alternate b-roll |

## Step 8 - Editing & Assembly
- Edit in a standard editor (Premiere, DaVinci Resolve, CapCut, Final Cut, Descript, etc.).
- **Structure:** hook shot -> build -> payoff -> CTA end card. Cut on action; use J/L cuts for audio flow; keep pace tight; trim the first and last frames of AI clips to remove glitches.
- **Speed ramps, crops, stabilization, upscaling/frame interpolation** where helpful.
- **Text & graphics:** add real titles, lower-thirds, logos, UI screenshots, charts in the editor for precision; use legible fonts and safe margins (platform UI overlays on vertical video).
- **Color:** consistent grade, correct skin tones, mild film grain to unify AI shots.
- **Captions/subtitles:** burned-in or sidecar (SRT/VTT); high contrast; accurate; essential for sound-off viewing and accessibility.
- **Audio mix:** VO clean and prominent (-16 to -12 LUFS typical for online, check platform guidance), music ducked under speech, sound effects for impact, no clipping; licensed music/sfx only.

## Step 9 - Export & Distribution
- **Specs:** H.264/H.265 MP4; 1080p (or 4K when needed); 24/25/30 fps (match project; 30/60 for social if desired); appropriate bitrate; correct aspect ratio per platform; safe areas.
- Create **variants:** different hooks, lengths (6/15/30 s), aspect ratios (9:16, 1:1, 16:9), languages.
- Thumbnails/cover frames with clear text and a strong focal point; titles, descriptions, tags, chapters.
- Test hooks and CTAs (A/B); monitor retention graphs and drop-off points; iterate.

## Use-Case Playbooks
- **Social short (15-30 s):** pattern-interrupt hook in 1-2 s, 4-6 shots, bold captions, trending-appropriate audio you have rights to, one CTA, loop-friendly end.
- **Product ad (15-30 s):** problem/desire -> hero product shots (image-to-video from clean product stills) -> benefits with text overlays -> social proof -> CTA/end card. Don't generate fake product demos or misleading performance claims; show real product footage for functional claims.
- **Explainer (60-120 s):** script-led, mix of motion graphics, screen recordings, and AI b-roll metaphors; clear structure and recap.
- **Brand story / mood film:** style bible, cinematic b-roll, music-led editing, minimal text.
- **Training/educational:** learning objective, short segments, visuals aligned with narration, on-screen key terms, captions, knowledge-check prompts.
- **Animated storybook (original characters):** character sheets, consistent illustration style, scene-by-scene image-to-video with gentle motion, narration, music.
- **Pre-visualization / animatics:** quick low-fidelity storyboards to test pacing and concept before real production.

## Responsible Use & Legal
- **Original and licensed only:** no copying existing films, characters, logos, or protected styles; license music, fonts, footage; check the tool's commercial-use terms.
- **Consent & likeness:** no realistic video of real people (public or private) without explicit permission; never create deceptive deepfakes, fake news/evidence, impersonation, harassment, or non-consensual or sexual content; no sexualized depictions of minors, ever.
- **Disclosure:** label AI-generated or synthetic media where platforms or laws require, and whenever it could mislead; retain provenance metadata (e.g., C2PA) when available.
- **Truth in advertising:** substantiate claims; don't fabricate testimonials, results, or demos.
- **Privacy & safety:** don't upload private footage of others without permission; avoid content that facilitates harm.
- **Bias:** represent people respectfully and diversely; review outputs for stereotypes.
- **Accessibility:** captions, readable text, avoid rapid flashing (seizure risk), provide audio description when needed.

## Common Mistakes
- Trying to generate the whole video in one prompt
- Overloaded shots (many characters, complex actions, multiple camera moves)
- No script, shot list, or style bible -> inconsistent output
- Depending on AI for exact text, logos, UI, or data
- Ignoring audio and captions
- Not trimming glitchy first/last frames; no color matching
- Weak hook and no CTA; wrong aspect ratio for the platform
- Using real people's likeness or protected IP without rights

## Checklist
- [ ] Goal, audience, platform, length, and CTA defined
- [ ] Script and timed shot list with camera/motion notes
- [ ] Style bible and character sheets; reference images prepared
- [ ] One simple action and one camera move per shot; multiple takes generated
- [ ] Best takes selected for stability and continuity
- [ ] Edited with real text/logos, captions, color grade, and clean audio mix
- [ ] Exported in correct formats/aspect ratios; variants for testing
- [ ] Rights, consent, disclosure, and accessibility checks complete
