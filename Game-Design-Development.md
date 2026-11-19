---
name: game-design-development
description: Design, prototype, balance, and ship games - core loops, mechanics and game feel, systems and economies, level design, difficulty and balancing math, playtesting, production planning, and engine workflows for Unity 6, Godot 4, and Unreal Engine 5 (plus Bevy, GameMaker, Defold, web). Use whenever the user mentions game design, GDD, game mechanics, level design, game balance, progression, economy, platformer/roguelike/RPG/shooter/puzzle/strategy design, game jams, prototyping, game feel, or building and shipping a game in Unity, Godot, or Unreal - even if they never say "design document".
---

# Game Design & Development Skill

> **Scope note:** Engine versions, prices, and store policies change quickly. Facts marked *(as of Nov 2026)* were checked against official or press sources on that date - re-verify before the user commits money or a pipeline to them. Numeric "starting values" in this file are rules of thumb to tune by feel, not laws.

## Core Principles
1. **Fun is found, not planned.** A design on paper is a hypothesis. Build the smallest playable test fast and let play prove or kill it.
2. **Start from the player experience, then derive mechanics.** Write the target feeling ("tense scavenging", "power fantasy") first; every mechanic must serve it (MDA: Mechanics -> Dynamics -> Aesthetics - designers build the first, players feel the last).
3. **Protect the core loop.** If the 30-second loop is not enjoyable alone, content, story, and polish will not save it.
4. **Scope is the silent killer.** Most games die from overreach, not bad ideas. Cut early, ship small, expand from a working base.
5. **Feedback makes mechanics legible.** A rule the player cannot see, hear, or feel might as well not exist ("juice" is communication, not decoration).
6. **Teach by playing.** Introduce, test, then twist each mechanic in safe space before combining it. Walls of text lose players.
7. **Numbers serve intent.** Decide what a number should *feel* like (fast kill, slow grind, close match) before choosing its value; then verify with data and humans.
8. **Observe behavior, not opinions.** Players are experts on their own experience, not on solutions. Watch what they do; discount what they say they want.
9. **Systems over scripts.** Prefer a few interacting rules that produce varied situations over hand-authored one-offs - but hand-author the critical first hour.
10. **Choose tools for the team and the game, not hype.** Engine, language, and architecture should match team skills, target platforms, and budget.
11. **Respect players and rules.** Honest monetization, accessibility, original assets, and correct licensing are part of the craft.

## Workflow
1. **Frame the project** - genre, platform(s), audience, team size and skills, timeline, budget, engine constraints, success metric (learning project, jam, commercial release).
2. **Pillars and fantasy** - 3 pillars max + a one-sentence pitch; use them as a veto filter.
3. **Core loop paper-design** - verbs, goals, feedback, progression hook, failure cost.
4. **Prototype** (days, greybox, throwaway) - answer ONE question per prototype; gate: "is the core loop fun for 10 minutes without art?"
5. **Vertical slice** - ~5-15 minutes at final-ish quality in all disciplines; proves tech, art direction, and production pace.
6. **Production** - content in milestone-sized batches; feature freeze, then content lock; regular playtests and build-every-day habit.
7. **Alpha -> Beta -> Release Candidate** - bug and balance burn-down, performance and platform certification, accessibility and localization passes.
8. **Launch and live** - store page early, demo/playtest, launch checklist, telemetry, patch cadence, community.
9. **Post-mortem** - what went well/badly, root causes, actions.

If the user is vague, ask at most 3 questions first (genre/reference games, platform + engine, team/timeline), then proceed with stated assumptions.

---

## Part A - Design Foundations

### Pillars, Fantasy, Pitch
- **One-sentence pitch:** "[Player role] [core verb] to [goal] in [setting], while [tension]." Example: "A lighthouse keeper repairs and defends a sinking island by day and scavenges storm wrecks by night."
- **Pillars:** 2-3 testable statements ("every fight is a puzzle", "movement is a toy"). Test each feature: does it strengthen a pillar? If not, cut or defer.
- **Reference games:** list 3 comps for *what to borrow* and 1 for *what to avoid*; never clone - isolate the mechanic or feeling.

### The Core Loop (design it explicitly)
`Goal -> Action (verbs) -> Feedback -> Reward/Progress -> New capability or new goal -> ...`
- **Micro loop** (seconds: jump, shoot, match), **meso loop** (minutes: a fight, a level, a run), **macro loop** (hours: progression, meta, story).
- Each loop must have: clear goal, meaningful decisions (not just execution), readable feedback, and an incentive to repeat.
- **Interesting decisions test:** a choice is interesting when options differ, are all situationally viable, and consequences are visible later. Remove dominated or purely cosmetic choices.

### Player Motivation
- **Self-Determination Theory:** autonomy (meaningful choice), competence (mastery with clear feedback), relatedness (connection/social/story). Check each loop against all three.
- **Flow:** keep challenge near skill; ramp, then relieve. Use mastery curve + rest beats.
- **Player-type models** (Bartle: achievers/explorers/socializers/killers; Quantic Foundry motivation clusters): use as checklist for who you serve - never as fixed labels for individuals.
- Reward schedules: predictable rewards build competence; variable rewards drive excitement but can feel manipulative - use deliberately and ethically.

### Documentation That Gets Used
- **One-page design:** pitch, pillars, core loop diagram, target player, platforms, scope, risks.
- **Living GDD:** wiki or short pages per system (purpose, rules, edge cases, UI, tuning values, open questions). Keep numbers in data files/spreadsheets, not prose. Prefer diagrams, tables, and GIFs over paragraphs.
- Keep a **decision log** (what, why, date) and a **cut list** (what was removed and why - prevents re-litigating).

---

## Part B - Mechanics, Systems, and Game Feel

### Anatomy of a Mechanic
`Input -> Rule/State change -> Feedback (visual, audio, haptic, UI) -> Consequence`
Specify each mechanic with: verbs, inputs, preconditions, costs, effects, cooldowns/limits, counters, failure states, and how it combines with other mechanics. Write edge cases (what if two happen on the same frame? what if the player is stunned/dead/in a cutscene?).

### System Patterns
| Pattern | Use it for | Watch out for |
|---|---|---|
| Resource loop (sources, sinks, converters) | Economy, crafting, ammo, stamina | Runaway inflation or starvation |
| Positive feedback (snowball) | Excitement, momentum, "power fantasy" | Decided-too-early matches |
| Negative feedback (rubber-banding, catch-up) | Close finishes, fairness | Feeling punished for skill |
| Risk/reward | Tension, player expression | Dominant safe option |
| Counter / intransitive (rock-paper-scissors) | Variety, rosters, builds | Single dominant counter-picks |
| Gating (key, skill, time, resource) | Pacing, progression | Backtracking drudgery; soft-locks |
| Procedural generation | Replayability | Samey output; unfair/unwinnable seeds - add validators |
| Emergence | Memorable stories | Hard to test - use scenario tests and sandbox bots |

### Game Feel (Swink-style: input, response, context, polish, metaphor, rules)
Starting values - tune per genre and by hand:
| Technique | Starting range | Effect |
|---|---|---|
| Coyote time | 80-150 ms | Jump still allowed just after leaving a ledge |
| Jump / action input buffer | 100-150 ms | Early presses are remembered |
| Variable jump height | cut upward velocity ~40-60% on release | Player controls arc |
| Hit-stop (freeze frames) | 40-120 ms | Makes impact feel heavy |
| Screen shake | 100-250 ms, decaying, scaled by impact | Emphasis; ALWAYS add an off/reduce setting |
| Attack telegraph | 300-600 ms windup (genre dependent) | Fairness and readability |
| Total input-to-screen latency | well under ~100 ms; twitch/competitive far lower | Responsiveness |
| Acceleration/deceleration curves | tune separately for ground, air, turning | Control "weight" |

Language-agnostic pseudocode for forgiving jumps:
```
if on_ground: coyote = COYOTE_TIME else coyote -= dt
if jump_pressed: buffer = BUFFER_TIME else buffer -= dt
if buffer > 0 and coyote > 0: jump(); buffer = 0; coyote = 0
if jump_released and velocity.y > 0: velocity.y *= JUMP_CUT   # 0.4-0.6
```
Juice checklist per important action: anticipation (windup), action (fast), impact (hit-stop, flash, particles, sound layer), follow-through (recoil, settle), UI confirmation. Layer 2-3 sounds per impact; vary pitch to avoid repetition fatigue.

### Genre Quick Reference
| Genre | Core loop | Main tuning levers | Classic failure |
|---|---|---|---|
| Platformer | run-jump-avoid -> reach goal | movement curves, level metrics, checkpoints | floaty/unfair jumps, unreadable hazards |
| Roguelike/lite | run -> build -> die -> meta-unlock | build synergy, run length, RNG fairness, meta pacing | one dominant build, meta power-creep |
| Action/Shooter | aim-move-react | TTK, weapon roles, spawn/cover, netcode | hitscan/lag disputes, spawn deaths |
| RPG | explore-fight-loot-level | XP curve, itemization, choice consequences | stat bloat, trivializing gear |
| Strategy/4X | expand-exploit-exterminate | economy snowball, tech tree, AI | solved opening, AI that cheats visibly |
| Puzzle | learn rule -> apply -> aha | difficulty curve, hint system | one trivial trick, trial-and-error brute force |
| Survival/Crafting | gather-craft-build-defend | need decay, recipe depth, base threat | busywork, grind walls |
| Idle/Incremental | spend -> multiply -> prestige | cost curves, prestige timing | dead time, no new decisions |
| Metroidvania | explore-gate-ability-unlock | map layout, ability order, backtrack aids | confusing gating, soft-locks |
| Horror | tension-release | information control, sound, vulnerability | fatigue, cheap jump-scares |

---

## Part C - Level Design

### Process
1. **Brief:** purpose in the game, new mechanic taught/tested, emotional beat, length, entry/exit state.
2. **Layout on paper:** flow diagram (rooms/nodes, loops, shortcuts, gates, secrets, rewards, rest points).
3. **Greybox/blockout:** primitives only. Engine tools: Unity ProBuilder, Godot CSG nodes or GridMap, Unreal Modeling Mode / BSP-style blockout. Playtest before any art.
4. **Metrics pass:** lock sizes in units tied to the player (see below).
5. **Encounter and pacing pass:** place challenges and rests; target an intensity curve.
6. **Guidance and readability pass:** lighting, color, landmarks, audio, sightlines.
7. **Art/lighting/audio pass**, then **polish and optimization** (occlusion, LOD, streaming).
8. **Test with fresh players**; watch where they stall, stray, or die.

### Metrics (write them down as a table, enforce with snap/grid)
- Player height, width, step height, run/walk speed, jump height and distance (max, comfortable, safe), crouch height, melee/weapon ranges, camera distance/FOV.
- Derive: min corridor width, door size, gap lengths (design to ~70-80% of max jump so there is margin), cover height, climb height, sightline distances.
- Re-derive metrics whenever movement tuning changes; keep a metrics test map.

### Teaching and Pacing
- **Teach -> Test -> Twist -> Combine -> Master:** safe introduction, simple test, new variation, mixed with other mechanics, then a skill-check finale.
- **Intensity curve:** build tension, climax, release; avoid flat difficulty or constant peaks. Insert rest/safe spaces after peaks (save, shop, vista).
- **Failure cost and checkpoints:** punish proportionally; retry in under ~10 seconds for hard sections.
- **Rule of three examples:** show, repeat in variation, subvert.

### Guiding Players Without Text
- Leading lines, light on the path, color-coding for interactables, contrast, movement (animated objects pull the eye), audio cues, landmarks visible from afar ("see it, go to it"), funnel/choke points, and consistent affordance vocabulary (same visual = same function).
- **Gates:** hard (key/ability) vs soft (difficulty/knowledge). Always give feedback on what is blocked and a hint of what unlocks it.
- **Loops and shortcuts:** unlock returns to hubs; reduce repeat-walk fatigue.
- **Secrets/rewards:** telegraph that something exists (broken wall, odd light), reward curiosity proportionally.

### Combat / Encounter Space
- Define each arena's purpose: cover density, flanking routes, verticality, hazards, spawn logic, escape paths.
- Mix enemy roles (rusher, ranged, support, tank, disruptor) so players change tactics; introduce one new variable per encounter.
- Give readable attack telegraphs and consistent hitbox language; limit simultaneous attackers (token system) for fairness.

### Open World / Large Spaces
- Points of interest at readable intervals, varied by activity and reward; use landmarks and a triangle-of-sights approach so the next destination is almost always visible.
- Mix density and emptiness deliberately; empty space is pacing, not failure.
- Technical: streaming cells (Unreal World Partition, Unity Addressables/additive scenes, Godot threaded scene loading), HLOD/LOD, draw distance budgets.

---

## Part D - Balancing

### Process
1. **Intent:** write targets ("average fight 20-40 s", "veteran finishes in 4 h", "no weapon > 55% pick rate").
2. **Anchor:** pick a baseline unit (basic enemy, starter weapon, 1 minute of income) and express all else relative to it.
3. **Model:** spreadsheet or simulation first; change one variable at a time.
4. **Test:** humans for feel, bots/sims for coverage, telemetry for scale.
5. **Tune and log:** record every change and reason; avoid knee-jerk nerfs - fix the cause (information, counterplay, cost) before the number.

### Core Formulas
| Quantity | Formula | Notes |
|---|---|---|
| Expected damage/s | dmg x rate x hit chance x (1 + crit chance x (crit mult - 1)) | Compare weapons at equal conditions |
| Time-to-kill | (ceil(HP / dmg) - 1) / rate | First shot lands at t = 0. Example: 100 HP, 25 dmg, 4/s -> 4 shots -> 0.75 s |
| Effective HP | HP / (1 - damage reduction) | |
| Armor with diminishing %DR | DR = A / (A + K) | K=100: A=100 -> 50%, 300 -> 75%. Mitigation % diminishes but EHP = HP x (1 + A/K) stays linear in A (1000 HP: A=0/100/200/300 -> 1000/2000/3000/4000) - never lets DR reach 100% |
| Polynomial XP curve | XP(n) = base x n^e | 100 x n^1.5: L10 = 3,162; L20 = 8,944; L50 = 35,355 |
| Exponential cost curve | cost(n) = base x g^n | g = 1.15 -> x1,084 by n=50; g = 1.07 -> x29. Small rate changes explode; typical idle/incremental growth ~1.07-1.15 |
| Drop chance over tries | P(at least 1) = 1 - (1 - p)^n; expected tries = 1/p | p = 1%: 100 tries = 63.4%, 299 tries = 95%. Add pity/bad-luck protection so the unlucky tail does not churn |
| Upgrade payback | cost / (gain per second) | Keep payback in a target band so buys feel good, not mandatory or pointless |
| Win rate fairness | target ~50% for symmetric modes; asymmetric factions ~45-55% at skill parity | Segment by skill tier, not just global |

### Structural Balance Rules
- **Sidegrades over upgrades:** options should be *different*, not strictly better. If one option beats others in all contexts, it is dominant - change its cost, risk, or counter, not just its stat.
- **Power budget:** give every item/ability a point budget (damage, range, utility, cost) so designers compare like with like; spend deliberately on unusual traits.
- **Diminishing returns and caps** stop stacking from breaking systems; **multiplicative stacking** needs hard caps or tests.
- **Counters and costs:** every strong thing needs a hard counter, a soft counter (positioning), or a real cost (cooldown, resource, vulnerability).
- **Positive vs negative feedback:** choose per mode on purpose; mix (snowball early, catch-up late) is common.
- **Degenerate strategy hunt:** list the cheapest, safest, most repeatable route to the goal and test whether it is fun; if not, fix the incentive.

### Difficulty Design
- Aim for a **flow channel**: a rising baseline with peaks and valleys; first 10 minutes are easier than they feel.
- Use multiple levers, not just HP/damage multipliers: enemy aggression/variety, resource scarcity, checkpoint spacing, hint frequency, assist options (slow-mo, aim assist, skip puzzle). Separate **challenge** (skill) from **tedium** (time).
- **Dynamic difficulty:** be transparent or optional; hidden rubber-banding can feel unfair in single-player and fatal in competitive.
- Spot spikes with death/quit heatmaps and per-section completion funnels.

### Economy Design
- Map **faucets** (sources), **sinks**, **converters**, and **stocks** per currency. Track median and mean wealth, time-to-next-purchase, and inflation over days.
- Prefer sinks that give meaning (upgrades, cosmetics, risk) over taxes that just delete.
- Never gate core fun behind friction designed to sell relief. If you monetize, follow platform rules and local law (see Part K).

### Tools
- Spreadsheet with named inputs (blue) and formulas; chart curves; sensitivity tables.
- Monte Carlo / bot simulation for matchups and drop tables:
```python
import random
def duel(hpA,dmgA,accA,hpB,dmgB,accB):
    a,b=hpA,hpB
    while True:
        if random.random()<accA: b-=dmgA
        if b<=0: return 1
        if random.random()<accB: a-=dmgB
        if a<=0: return 0
wins=sum(duel(100,20,.8,120,18,.75) for _ in range(20000))/20000   # ~0.69 over 20,000 trials
```
- Machinations-style diagrams for resource flows; in-game debug overlay showing live DPS, TTK, income/s; telemetry dashboards (pick rate, win rate, retention by cohort).

---

## Part E - Engine Workflows

### Choosing an Engine *(as of Nov 2026 - verify prices and versions)*
| | Unity 6.x (C#) | Godot 4.x (GDScript, C#, C++ via GDExtension) | Unreal Engine 5.x (Blueprints, C++) |
|---|---|---|---|
| Latest / support | Unity 6.3 LTS supported to Dec 2027; 6.0 LTS public support ended Oct 2026 (Enterprise/Industry get +1 yr); Update releases (6.4 shipped Mar 2026, later 6.x follow) | 4.7 stable Jun 18 2026, 4.7.x maintenance patches since | 5.8 (Jun 17 2026) is the last planned UE5 feature release; UE6 early access signalled for roughly late 2027 (reports differ) |
| Cost | Personal free up to $200K revenue/funding; Pro required above it (about $2,310/seat/yr prepaid in 2026); Enterprise for large orgs; Runtime Fee cancelled in 2024 | Free, MIT license, no royalties | Free to start; 5% royalty on lifetime gross revenue above $1M per product; Epic Games Store sales are royalty-free |
| Strengths | Huge ecosystem, mobile/2D/3D/XR reach, fast iteration, DOTS/ECS now core in 6.4+ | Lightweight, fast editor start, open source, great for 2D and small-medium 3D, easy to modify | Top-end 3D fidelity (Nanite, Lumen, MegaLights), open worlds, built-in gameplay frameworks, source access |
| Trade-offs | Asset/package churn, engine-version upgrades, GC pitfalls | Smaller 3D/console tooling; console export via third-party partners | Heavy editor, bigger builds, steeper learning curve, long compile/iteration for C++ |
| Best for | Mobile, 2D/3D indie to mid-size, XR, cross-platform | Jams, 2D, stylized 3D, solo/small teams, open-source needs | AAA-leaning 3D, realistic visuals, large worlds, shooters |

Pick by: team language skills -> target platforms -> visual target -> multiplayer needs -> budget/licensing -> available talent. Other valid choices: Bevy (Rust/ECS), GameMaker (2D), Defold (lightweight, web/mobile), Phaser/PlayCanvas/Three.js (web), custom (only if the engine is the product).

### Concept Map Across Engines
| Concept | Unity | Godot | Unreal |
|---|---|---|---|
| Reusable thing | Prefab | Scene (.tscn) | Blueprint class / Actor |
| Entity | GameObject | Node | Actor |
| Behavior | MonoBehaviour / component | Script on a node | ActorComponent / Blueprint graph / C++ |
| Data asset | ScriptableObject | Resource (.tres) | Data Asset / Data Table |
| Events | C# events, UnityEvent | Signals | Delegates, Event Dispatchers |
| Input | Input System package | InputMap + Input | Enhanced Input |
| Fixed physics step | FixedUpdate | _physics_process | Tick + physics substepping settings |
| UI | UI Toolkit / uGUI | Control nodes | UMG (over Slate) |
| Animation | Animator, Timeline | AnimationPlayer / AnimationTree | Animation Blueprint, Sequencer |
| Large-world loading | Addressables, additive scenes | threaded scene loading | World Partition, level streaming |
| Profiling | Profiler, Frame Debugger, Memory Profiler | Debugger -> Profiler/Monitors | Unreal Insights, `stat unit`, `stat gpu` |
| Version control | Git + LFS or Unity Version Control | Git (text-based scenes) | Perforce, or Git + LFS |

### Universal Architecture Rules
- **Separate data from logic:** tuning values, item stats, enemy definitions in data assets/tables so designers iterate without code changes and balance can be diffed.
- **Composition over deep inheritance;** small components (Health, Mover, Weapon) glued by data.
- **Decouple with events/signals;** avoid hard references across systems; use interfaces for "can be damaged/interacted".
- **State machines** (or behavior trees) for characters, enemies, and game flow; make states explicit and debuggable.
- **Fixed timestep for physics/gameplay logic,** variable for rendering; never multiply by delta incorrectly (frame-rate-independent movement).
- **Input abstraction:** actions, not keys; rebinding and multi-device from day one.
- **Object pooling** for bullets, VFX, enemies; avoid per-frame allocations.
- **Save system early:** versioned, data-driven, tested with old saves.
- **Debug tools:** cheat console, teleport, god mode, spawn menu, time scale, on-screen stats - they pay for themselves within a week.
- **Determinism where it matters** (replays, lockstep, procedural seeds): own your RNG, log the seed.

### Unity 6 Playbook
- **Setup:** pick a supported LTS/Update release and pin it; choose URP for most projects (HDRP for high-end PC/console); Input System, Cinemachine, Addressables, Test Framework; assembly definitions to speed compile.
- **Design data:** ScriptableObjects for items/enemies/config; avoid singleton sprawl; use events for UI updates.
- **Code:** cache `GetComponent`; no `Find*` or LINQ/allocations in `Update`; coroutines or async (Awaitable) for sequencing; physics in `FixedUpdate`; camera in `LateUpdate`. Unity 6 renamed `Rigidbody.velocity` to `linearVelocity` (same for Rigidbody2D).
- **Scale:** use ECS/DOTS (core package from 6.4) only where entity counts or CPU-bound simulation justify the complexity; keep the rest in GameObjects.
- **Performance:** Profiler first, then Memory Profiler/Frame Debugger; SRP Batcher, GPU instancing, LOD, occlusion culling, texture compression/atlases, Project Auditor for static checks.
- **Build/release:** Version Control with proper `.gitignore` (Library, Temp, Logs excluded; `.meta` files committed); CI builds via Unity Build Automation or GitHub Actions; test on real target devices early.

### Godot 4 Playbook
- **Setup:** pin one 4.x release (4.7 stable; use latest maintenance patch); text scenes diff cleanly in Git, ignore `.godot/`.
- **Architecture:** scene = reusable object; "call down, signal up"; autoloads for truly global services only; `Resource` subclasses for data (`@export` fields); groups for broadcast.
- **Code:** typed GDScript (`var hp: int`) for speed and safety; physics in `_physics_process`; `CharacterBody2D/3D.move_and_slide()` for controllers; `await` for sequencing; C# if you need .NET libraries and use the .NET build; GDExtension (C++/Rust) for hot paths.
- **2D:** use `TileMapLayer` (replaced `TileMap` in 4.3); Jolt is the default 3D physics engine for new projects since 4.6 - confirm in project settings; pixel-perfect via snap + integer scaling.
- **UI/tools:** Control nodes with containers and theme resources; 4.7 adds Control offset transforms, built-in VirtualJoystick, AreaLight3D, HDR output, and a new Asset Store (beta).
- **Performance:** built-in Profiler and Monitors, visual profiler for GPU; MultiMesh for instancing, visibility ranges/LOD, server APIs for extreme cases.
- **Export:** install export templates matching the editor version; test Web (SharedArrayBuffer/headers requirements), Android (SDK/keystore), and desktop early; console export goes through third-party porting partners.

### Unreal Engine 5 Playbook
- **Setup:** pick a stable 5.x (5.8 for new projects, or a version your plugins support); source control with Perforce or Git LFS plus file locking for binary assets; use Enhanced Input and Data Assets from the start.
- **Blueprint vs C++:** prototype and iterate gameplay in Blueprints; move hot paths, complex math, and shared base classes to C++; expose C++ to designers via `UPROPERTY`/`UFUNCTION`. Keep Blueprints small and event-driven.
- **Frameworks:** GameMode/GameState/PlayerController/Pawn separation; Gameplay Ability System for abilities/attributes/effects (high learning cost, worth it for RPG/ability-heavy games); Data Tables/Data Assets for tuning; Mass for large crowds.
- **World building:** World Partition and Data Layers for big maps; Nanite/Lumen/Virtual Shadow Maps for visuals; MegaLights is production-ready in 5.8 and Lumen Lite targets handhelds/lower-end - test on hardware, not just a dev PC; Mesh Terrain (5.8) is experimental.
- **Performance:** `stat unit/fps/gpu`, Unreal Insights, GPU Visualizer; set scalability tiers, budget draw calls and VRAM, profile in packaged builds (Development/Test), not the editor.
- **Release:** cook and package early and often; watch shader compilation/PSO stutter (PSO caching); test on target consoles/handhelds; plan for UE6 migration (new Verse language) only after official early access details land.

---

## Part F - Prototyping & Production

### Prototype Rules
- One question per prototype ("is wall-running fun?"); timebox to days; greybox, placeholder everything; **throw it away** or rewrite cleanly before production.
- Gate to proceed: players smile, replay voluntarily, and you can describe why. Otherwise change the mechanic or kill it - sunk cost is not a reason.
- Jam rules: define the loop in the first hour, cut features by half at midpoint, leave 20% time for polish and a playable build.

### Milestones
| Milestone | Definition |
|---|---|
| Concept | pitch, pillars, comps, risks |
| Prototype | core loop playable in greybox |
| Vertical slice | representative quality, 5-15 min, all disciplines |
| Alpha | feature complete (all systems exist, content incomplete) |
| Beta | content complete; only bug/balance/polish |
| Release candidate | no known blockers; cert/store checks passed |
| Live | patches, content, community |

### Scope and Estimation
- MoSCoW every feature; maintain an explicit **cut list** and keep a 15-25% buffer.
- Estimate with ranges (three-point PERT: (O + 4M + P)/6, e.g., 2/4/12 days -> 5); first-time-scope estimates are usually 2-3x too optimistic (planning fallacy) - multiply and cut.
- Build content as **repeatable pipelines** (templates, kits, modular assets) so cost per level/enemy is known after the first two.

### Engineering Hygiene
- Daily build, smoke test, and a rule that the main branch is always playable; short-lived branches; asset locking for binaries.
- Automated tests for pure logic (damage formulas, inventory, save/load) and scene "smoke" tests; CI builds for each target.
- Technical debt: log it, schedule payback before alpha; do not refactor in the last 10% of the schedule without a safety net.
- Backups: 3-2-1 (3 copies, 2 media, 1 offsite) for source and builds.

---

## Part G - Playtesting & Analytics
- **Protocol:** brief, then silence. Observe without hints; ask players to think aloud; record screen + face if consented; ask open questions after ("what were you trying to do?").
- **Cadence:** friends -> strangers; test early (greybox) and often. Roughly 5 players per round reveals most major usability problems; rerun after fixes. Include newcomers, genre veterans, and players with accessibility needs.
- **Triage:** rank issues by severity x frequency x cost to fix; separate *bugs*, *comprehension*, *balance*, *taste*. Fix comprehension and feel first.
- **Telemetry (with privacy consent):** funnel (tutorial completion), time-to-first-fun, death/quit locations, retention by cohort, economy flow, build/loadout pick and win rates. Define the question before instrumenting.
- Beware vanity metrics and small samples; combine quantitative signals with observed sessions.
- Retention benchmarks vary widely by genre and platform; compare to your own prior builds and current genre data, not generic numbers.

---

## Part H - Performance & Platforms
- **Frame budgets:** 30 fps = 33.3 ms, 60 fps = 16.7 ms, 90 fps = 11.1 ms, 120 fps = 8.3 ms per frame for CPU *and* GPU work. Leave headroom (~10-20%) for spikes.
- **Method:** profile -> find the bottleneck (CPU main thread, render thread, GPU, memory, loading, I/O) -> fix the biggest -> re-measure. Never optimize blind.
- **Common wins:** reduce draw calls (batching/instancing), LOD and culling, cheaper shaders/overdraw, texture compression and streaming, pooling and zero per-frame allocation, async loading, physics layers and simplified colliders, update frequency throttling for distant AI.
- **Platforms:** test on minimum-spec hardware, Steam Deck-class handhelds, Switch-class devices, and low-end phones early; thermal throttling and memory limits bite late. Respect console certification (Sony TRC, Xbox XR, Nintendo Lotcheck) and storefront rules from the start.

---

## Part I - UX, Accessibility, Audio
- **Onboarding:** teach inside play with just-in-time prompts; show, don't tell; allow skipping and re-reading; measure tutorial completion.
- **HUD/UX:** show only what decisions need; consistent iconography; clear states (disabled, locked, selected); controller + keyboard/mouse + touch parity where relevant.
- **Accessibility (consult Game Accessibility Guidelines / Xbox Accessibility Guidelines):** full control remapping, hold-vs-toggle, subtitles with size/contrast/speaker labels, colorblind-safe palettes and non-color cues, reduce motion/shake/flash toggles (photosensitivity safety), difficulty and assist options, readable fonts, audio cues with visual equivalents, screen-reader support for menus where possible. It widens your audience and costs far less when built in early.
- **Audio:** prioritize and duck (dialogue > critical cues > music > ambience), randomize and layer repeated sounds, mix at loudness targets, give each important mechanic a distinct sound signature.

---

## Part J - Multiplayer Essentials
- Decide early: single-player, local, co-op, competitive, MMO-scale - architecture differs radically.
- **Authority:** server-authoritative for anything cheat-sensitive; clients predict and reconcile; interpolate remote entities; lag compensation for hit detection; rollback netcode for fighting-style precision.
- **Bandwidth and tick rate:** send state deltas, quantize values, prioritize by relevance.
- **Tools:** Unity Netcode for GameObjects / Entities-based netcode with Unity Multiplayer services; Godot high-level multiplayer API (RPCs, `MultiplayerSynchronizer`/`MultiplayerSpawner`) with ENet/WebSocket/WebRTC peers; Unreal built-in replication with dedicated servers (and Iris on newer versions); also Photon, Mirror, Nakama, Steam Networking, EOS.
- Test with simulated latency/jitter/loss from the first prototype; design UX for waiting and disconnects; plan anti-cheat, moderation, and reporting.

---

## Part K - Launch, Business, Legal, and AI
- **Store presence:** page live early; clear capsule art and 30-second trailer that shows the core loop in-game; demo or playtest; wishlist/follower building; festivals and press kits; release date away from big competitors; community channel (Discord/forum).
- **Steam AI disclosure *(Jan 2026 rewrite)*:** disclosure targets generative AI content that players consume in the shipped game or store assets; behind-the-scenes efficiency tools (e.g., code assistants) are not covered. Be accurate - the survey is compared with your build and page. Other stores differ; check each.
- **Licensing and rights:** verify license/commercial use of every asset, font, plugin, and music track; keep a credits/asset ledger; avoid trademarked names, characters, and ripped assets; engine royalties and platform cuts must be in your revenue model.
- **Ratings, privacy, regulation:** age ratings (ESRB/PEGI/IARC), GDPR/CCPA/COPPA when collecting data (especially from children), accessibility laws in some markets, and region-specific rules on paid random rewards ("loot boxes") - confirm locally with a lawyer.
- **Ethics:** avoid dark patterns (fake scarcity, hidden costs, manipulative streak loss); treat players, especially minors, with care.
- **Post-launch:** monitor crash reports and reviews, ship a day-one/week-one patch plan, communicate transparently, update cadence you can sustain; plan localization and ports based on data.

---

## Templates
**One-page pitch:** Title - Pitch sentence - Pillars (3) - Core loop diagram - Target player - Platforms/engine - Scope (weeks/people) - Biggest risks - Unique hook.

**System spec:** Purpose - Player fantasy - Rules/inputs - States and transitions - Numbers (link to data) - UI/feedback - Edge cases - Dependencies - Test plan - Open questions.

**Level brief:** Name - Purpose/beat - New mechanic taught - Length and metrics - Flow diagram - Encounters and rewards - Gates/secrets - Art/audio mood - Success criteria (completion time, death rate).

**Balance sheet:** Item/enemy - Role - Cost - Stats - Derived (DPS/TTK/EHP) - Counter - Notes - Version/date.

**Playtest report:** Build - Testers (n, experience) - Goals - Observed issues (severity x frequency) - Quotes - Quant data - Decisions and next tests.

**Post-mortem:** Went well / Went badly / Surprises / Root causes / Actions with owners.

## Output Format (when answering the user)
1. **Recommendation first** (what to build/change and why, 1-3 sentences, with confidence).
2. **Design or plan** - tables for options, steps in order, concrete numbers marked as starting values.
3. **Engine-specific implementation** - match the user's engine and language; show a minimal working snippet or node/component setup rather than abstract advice.
4. **Risks and tests** - what could go wrong, how to playtest it, what would change the decision.
5. **Next steps** (smallest playable increment first). Ask 1-2 targeted questions only if a missing fact would change the advice.
Match depth to the user: a beginner gets a small win and one concept at a time; an expert gets trade-offs and numbers.

## Common Mistakes / Red Flags
- Designing the whole game before a playable prototype; no clear core loop; features without a pillar to justify them
- Content before fun; art polish on a mechanic that is not working; "we'll balance it later"
- Scope creep, no cut list, multiplayer or open world chosen by default; underestimating tools, UI, QA, and platform work
- Tutorial as text dump; unreadable feedback; designing for oneself and testing only with friends who know the game
- Single dominant strategy ignored; exponential economy with no sinks; RNG with no fairness protection
- Optimizing without profiling; per-frame allocations; huge uncompressed assets; testing only in the editor on a strong PC
- Engine-hopping mid-project; over-engineering architecture before the loop is proven; copy-pasted code with no data separation
- No version control or backups; binary merge conflicts; no build automation
- Ignoring accessibility, licensing, and store requirements until the last week; unclear AI-content disclosure

## Data & Sourcing Rules
- Look up current engine versions, pricing, store policy, and platform requirements before stating them; cite source and date.
- Engine facts in this file were checked on 19 Nov 2026 against: Unity release and pricing pages (unity.com/releases/unity-6, unity.com/runtime-fee), Godot release notes (godotengine.org/releases/4.7), Unreal licensing and 5.8 release coverage (unrealengine.com/license; CG Channel, GameFromScratch, 17 Jun 2026), and Steam AI-disclosure coverage (Jan 2026). Prefer official docs and release notes over aggregators.
- Do not invent benchmarks (retention, conversion, wishlist ratios). Say what to measure and how to find current genre data.
- Code and math must be run or checked; state engine version for any API-specific advice, since APIs rename and deprecate between releases.
- For legal, tax, or financial questions (royalties, contracts, regulations), explain the factors and suggest a qualified professional.

## Checklist
- [ ] Genre, platform, engine, team size, timeline, and success metric defined
- [ ] Pillars and one-sentence pitch written; features tested against them
- [ ] Core loop (micro/meso/macro) is explicit and prototyped before content
- [ ] Mechanics specified with feedback, edge cases, and counters
- [ ] Levels built from metrics, greyboxed, paced, and playtested before art
- [ ] Balance intent set; formulas, data tables, and simulations in place; changes logged
- [ ] Engine and architecture fit the team; data separated from logic; version control and builds automated
- [ ] Scope has a cut list, buffer, and milestones; estimates are ranges
- [ ] Playtests with fresh players on a schedule; telemetry questions defined
- [ ] Performance profiled on target hardware against a frame budget
- [ ] Accessibility, UX onboarding, audio, and localization planned
- [ ] Licensing, ratings, privacy, AI-disclosure, and store requirements checked
- [ ] Launch plan and post-launch support defined
- [ ] Facts dated and sourced; code/math verified; no guarantees of commercial success
