# FluxGuard Motion Script — v2 (approved revisions)

**Status:** pre-production reference. This document plans the pitch video. It does not build the animation.
**Source of truth for wording:** `FluxGuard_Pitch_Deck.pptx` and `docs/deck-outline.md`.

---

## Revision notes (v2)

| # | Change | Why |
|---|--------|-----|
| 1 | Scene 2 lengthened to 15 s; scene 5 shortened to 20 s. Total stays 2:05. | Scene 2's narration didn't fit; scene 5 had spare time. |
| 2 | Narration rewritten for scenes 2, 8, 9 and 10. Scenes 1, 3 and 6 tightened. | Every scene now fits the 2.3 words-per-second check (see the timing table). |
| 3 | Cold open now reads "One day it's fine. The next, the burn is back." | "1 in 7" was shown twice in 20 seconds. It now appears only in scene 2. |
| 4 | On-screen text budget added: at most 20 words of copy per scene. | v1 copied nearly all of the deck's text; scene 8 alone needed about 20 s to read. The live deck carries the detail. |
| 5 | Phone demo values restored (24%, 3 / 10, 7h 40m, 12-day streak), with a "Sample screen" tag. | Without them the stress and sleep tiles looked empty. The tag makes clear they are illustrative, not data. |
| 6 | Scene 9 narration now says "a pilot with a partner physician". | v1's "physician-supported pilot" implied a physician is already on board. |
| 7 | Scenes 3, 5, 6, 7, 8, 9 and 10 trimmed to fit the text budget. | Readability at video pace. |

**Still open:** `[CONTACT EMAIL]` on the end card, and the reference images (see "Reference images — to produce").

---

## 1. Overview

### Core concept — "connecting the dots"

FluxGuard's visual story is one continuous system. Four soft glowing orbs — Food, Sleep, Stress and Activity — start apart, drifting and flickering coral. As the story moves from uncertainty to insight, the same orbs persist, move, change size and color, and become linked by fine lines. The connections gather into the FluxGuard shield.

The risk ring is the hero element: a calm circular gauge that resolves to **LOW RISK TODAY** in the product scene and returns in the outro to frame the logo.

Narrative arc: **random → pattern → connection → prediction → habit → trust → ask**

### Facts and sample values

Only these evidence-backed numbers appear, each with a source caption:

- **1 in 7** adults worldwide (13.98%) have GERD; about **1.03 billion** people — Nirwan et al., *Scientific Reports*, 2020.
- People with anxiety had **3.2×** the odds of severe reflux symptoms — HUNT population study, *Alimentary Pharmacology & Therapeutics*, 2007 (n = 65,333).
- **~15.8M** Filipinos — always labeled **estimate**: the global 13.98% applied to the 112.7M population in PSA's 2024 Census.

Sample values appear **only inside the phone mockup**, which always carries a visible **"Sample screen"** tag. They match the approved deck: 24% reflux risk, Stress 3 / 10, Sleep 7h 40m, 12-day logging streak. They must never appear outside the phone or be narrated as results.

### Runtime and format

- Runtime: **2:05** (125 s)
- Canvas: **1920 × 1080**, 16:9, **30 fps**
- Viewing: opens a live pitch, so it must work **with the sound off**. Every essential point is on screen; narration adds warmth and clarity.

### Pacing

- **Intro and problem:** restrained, slightly tense, slow orbital drift.
- **Insight and reveal:** connections speed up gently, then settle.
- **Product loop:** the crispest pacing — short staggered entrances, clear UI hierarchy.
- **Market and trust:** slower and more editorial.
- **Outro:** generous breathing room for the ask and contact.

### Sound direction

No copyrighted music. Choose a royalty-free track with a soft, modern health-tech pulse: warm synth bed, restrained low end, subtle glass-and-air texture, and a light rhythmic motif that resolves as the dots connect. Avoid ominous pulses, hospital clichés, alarm beeps, glitch effects and aggressive drops.

Sound design is tactile and sparse:

- low, soft hum under the drifting orbs;
- tiny glass-like ticks when lines connect;
- a soft tonal lift when the shield forms;
- restrained UI ticks for counters and cards;
- one gentle notification chime for the early warning;
- a warm final chord under the logo and ask.

---

## 2. Motion system

### Springs and easing

Smooth spring ease-outs throughout. The motion should feel engineered, not playful.

| Use | Remotion `spring()` config |
|-----|---------------------------|
| Default | `stiffness: 120, damping: 18, mass: 0.8` |
| Soft entrance | `stiffness: 95, damping: 20, mass: 0.9` |
| Micro UI | `stiffness: 180, damping: 22, mass: 0.65` |

- Opacity: `interpolate()` 0 → 1 with a short ease-out; never linear when paired with movement.
- Scale entrances: 0.96 → 1.00, no overshoot.
- Orb drift: slow, low-amplitude sine motion layered under the spring-driven scene changes.
- Not allowed: bounce, glitch, shake, elastic overshoot, hard-cut resets.

### Standard durations

| Motion | Duration |
|--------|----------|
| Major scene entrance | 0.45–0.70 s |
| Headline entrance | 0.35–0.50 s |
| Card entrance | 0.35–0.50 s |
| Micro UI entrance | 0.20–0.35 s |
| Standard hold | 1.0–2.5 s |
| Exit / handoff | 0.30–0.55 s |
| Orb relocation | 0.8–1.4 s |
| SVG line draw | 0.45–0.90 s |
| Risk ring sweep | 0.9–1.3 s |

### Stagger

| Group | Offset |
|-------|--------|
| Headline → subhead | +0.08 s |
| Card stack | +0.08–0.12 s per card |
| Four orbs | +0.06–0.10 s per orb |
| Feature grid | +0.07 s per card |
| Timeline milestones | +0.12 s per milestone |

### Transition types

- **Persistent-world morph:** the four orbs stay mounted across scene boundaries; interpolate position, size, opacity and meaning-color.
- **Line handoff:** connecting lines extend toward the next scene's focal object.
- **Shield gather:** orbs travel along their connection paths into the logo mark.
- **UI slide:** phone and dashboard cards rise 20–32 px with a spring ease-out.
- **Risk ring match cut:** the ring stays centered while the context around it changes.
- **Soft crossfade:** only where no geometric handoff works.

### Type scale at 1080p

Inter, unless the Figma file specifies another font.

| Role | Size | Weight |
|------|------|--------|
| Display / hero | 76–88 px | 700–800 |
| Section headline | 52–64 px | 700 |
| Large statistic | 88–112 px | 700–800 |
| Subheadline | 30–36 px | 500–600 |
| Body | 28 px | 400–500 |
| Card title | 28 px | 650–700 |
| Label / UI text inside the phone | 22–24 px | 500–650 |
| Source caption | 18 px | 400 |
| Eyebrow | 18 px, tracking +0.04em | 650 |

Readable-text minimum is **28 px**. Only source captions, eyebrows and UI text inside the phone mockup may go smaller, never below 18 px.

### Text budget

- **At most 20 words of copy per scene.** Copy means headlines, statements and card titles.
- **Not counted:** source captions, and short labels of six words or fewer attached to a number, axis, pill, person or UI element.
- **Reading time:** hold copy about 0.3 s per word, and at least 2 s after it finishes animating.

### Layout

- Safe margins: **96 px** on every side
- Grid: 12 columns, 24 px gutters, 8 px baseline
- Card radius 12–24 px; pills fully rounded
- Backgrounds: deep navy `#0F1630` for cinematic scenes; white or light blue `#E8F6FC` for product scenes

### Color rules

| Color | Hex | Meaning |
|-------|-----|---------|
| Sky | `#29A8E0` | FluxGuard / product emphasis |
| Light blue | `#E8F6FC` | Soft UI surfaces |
| Navy | `#1A2340` | Text on light backgrounds |
| Deep navy | `#0F1630` | Cinematic background |
| White | `#FFFFFF` | Text on dark backgrounds |
| Coral | `#FF6B4A` | Reflux / risk / problem |
| Mint | `#22C39A` | Safe / low risk |
| Amber | `#FFB547` | Caution |
| Slate | `#7C8AA5` | Source captions, secondary copy |

---

## 3. Timing overview

Narration is checked at **2.3 words per second** (about 140 words per minute).

| # | Scene | Timecode | Length | Narration words | Est. speech | Fits |
|---|-------|----------|--------|-----------------|-------------|------|
| 1 | Cold open | 00:00–00:07 | 7 s | 15 | 6.5 s | ✓ |
| 2 | Problem | 00:07–00:22 | 15 s | 32 | 13.9 s | ✓ |
| 3 | Insight | 00:22–00:34 | 12 s | 19 | 8.3 s | ✓ |
| 4 | Logo reveal | 00:34–00:42 | 8 s | 14 | 6.1 s | ✓ |
| 5 | How it works | 00:42–01:02 | 20 s | 40 | 17.4 s | ✓ |
| 6 | Features | 01:02–01:14 | 12 s | 20 | 8.7 s | ✓ |
| 7 | Where we fit | 01:14–01:26 | 12 s | 17 | 7.4 s | ✓ |
| 8 | Market + model | 01:26–01:38 | 12 s | 25 | 10.9 s | ✓ |
| 9 | Progress + trust | 01:38–01:52 | 14 s | 30 | 13.0 s | ✓ |
| 10 | Outro | 01:52–02:05 | 13 s | 27 | 11.7 s | ✓ |
| | **Total** | | **125 s** | **239** | | |

---

## 4. Scene by scene

### Scene 1 — INTRO / cold open · 00:00–00:07 · 7 s

- **Visuals:** Deep navy field. The four orbs (Food, Sleep, Stress, Activity) sit far apart, drifting and flickering coral. The center is mostly empty.
- **Animation beats:**
  - 0.0 s: first orb fades up.
  - +0.15 / +0.30 / +0.45 s: the other three orbs appear.
  - +1.0 s: slow drift begins.
  - +1.8 s: line 1 enters.
  - +3.6 s: line 2 enters.
  - +5.0 s: coral glow briefly intensifies, then steadies.
- **On-screen copy (10 words):**
  - "One day it's fine."
  - "The next, the burn is back."
- **Narration (15 words):** "For millions, reflux feels random. One day it's fine. The next, the burn is back."
- **Sound:** low warm drone; four soft tonal ticks as the orbs appear.
- **Transition out:** copy fades while the orbs drift inward behind the incoming stat cards. No hard cut.
- **Build notes:** `GlowOrbField`, `Orb`, `Headline`. Spring entrances and slow `interpolate()` drift.

### Scene 2 — Problem · 00:07–00:22 · 15 s

- **Visuals:** The orbs orbit softly behind three large stat cards, one clean beat per statistic. A statement follows, then source captions.
- **Animation beats:**
  - 0.0 s: stat 1 rises and counts up.
  - +3.0 s: stat 2.
  - +6.0 s: stat 3.
  - +9.5 s: the statement enters below.
  - +12.0 s: source captions settle.
  - Hold until 15.0 s.
- **On-screen copy (8 words):** "Most people treat the burn — not the cause."
- **Stat labels:**
  - **1 in 7** — adults worldwide live with GERD
  - **1.03B** — people with GERD globally
  - **3.2×** — odds of severe symptoms with anxiety
- **Source caption:** "Sources: Nirwan et al., Scientific Reports (2020), meta-analysis of 102 studies in 37 countries · HUNT population study, Alimentary Pharmacology & Therapeutics (2007), n = 65,333."
- **Narration (32 words):** "One in seven adults live with reflux disease — over a billion people. Anxiety is linked to over three times the odds of severe symptoms. Yet most treat the burn, not the cause."
- **Sound:** subtle count-up ticks. No alarm.
- **Transition out:** the cards flatten into four small glowing points, and lines begin to draw between them.
- **Build notes:** `StatCounter`, `SourceCaption`, `Orb`. Count-ups only for the approved numbers.

### Scene 3 — Insight · 00:22–00:34 · 12 s

- **Visuals:** The four orbs settle around a central coral "Reflux episode" hub. Fine sky-blue lines connect each orb to the hub.
- **Animation beats:**
  - 0.0 s: the title enters and the hub appears.
  - +0.6 s: Food line draws.
  - +0.8 s: Sleep line.
  - +1.0 s: Stress line.
  - +1.2 s: Activity line.
  - +4.0 s: all four lines pulse together once.
  - +6.5 s: the closing line enters.
  - Hold until 12.0 s.
- **On-screen copy (14 words):**
  - Title: "Reflux is a pattern, not one bad meal"
  - Closing line: "FluxGuard looks at all four — together."
- **Labels:** "Reflux episode" · Food · Sleep · Stress · Activity
- **Narration (19 words):** "Reflux rarely comes from one thing. Food, sleep, stress and movement interact — and single-purpose apps only see one piece."
- **Sound:** four light connection ticks; a soft harmonic lift on the pulse.
- **Transition out:** the lines converge toward a shield silhouette while the hub recedes.
- **Build notes:** `OrbNetwork` with SVG path draw-on.

### Scene 4 — Logo reveal · 00:34–00:42 · 8 s

- **Visuals:** The four orbs gather into the white shield-with-check inside a rounded sky-blue square. The background shifts from deep navy toward light blue.
- **Animation beats:**
  - 0.0 s: lines tighten.
  - +0.8 s: orbs travel along their paths.
  - +1.5 s: shield outline forms.
  - +2.0 s: check draws on.
  - +3.2 s: square settles at scale 1.0.
  - +4.0 s: wordmark enters.
  - +4.6 s: tagline enters.
- **On-screen copy (7 words):**
  - Wordmark: "FluxGuard"
  - Tagline: "Stop acid reflux before it starts."
- **Narration (14 words):** "That's the gap FluxGuard fills: connect the dots, learn the pattern, and act earlier."
- **Sound:** warm tonal resolve; a single soft logo chime.
- **Transition out:** the logo shrinks to a small top-left anchor as the phone rises beside it.
- **Build notes:** `ShieldGather`, `LogoMark`. SVG path morph and draw-on, spring scale.

### Scene 5 — How it works · 00:42–01:02 · 20 s

- **Visuals:** The phone mockup dominates the frame, with a four-step loop around it: Log → Analyze → Alert → Improve. The risk ring sits inside the phone. A "Sample screen" tag is pinned to the phone's top edge for the whole scene.
- **Animation beats:**
  - 0.0 s: phone rises; title enters.
  - +1.0 s: LOG step lights.
  - +3.5 s: ANALYZE step lights; lines run from the loop into the phone.
  - +6.5 s: risk ring sweeps to 24% in mint.
  - +8.5 s: "LOW RISK TODAY" pill; Stress and Sleep tiles rise.
  - +10.5 s: ALERT step lights; the push alert slides in.
  - +13.0 s: IMPROVE step lights.
  - +14.5 s: tip highlight.
  - +16.0 s: streak badge pops in.
  - +18.0 s: the loop closes and the closing line holds.
- **On-screen copy (11 words):**
  - Title: "How FluxGuard works"
  - Closing line: "Every log makes the next prediction more personal."
- **Loop labels:** Log · Analyze · Alert · Improve
- **Phone UI labels:**
  - "Sample screen" · "Today" · "Mon, Oct 5"
  - "24%" · "reflux risk" · "LOW RISK TODAY"
  - "Stress 3 / 10" · "Sleep 7h 40m"
  - Alert: "Big meal after 8 PM? Try a lighter snack tonight."
  - "12-day logging streak"
- **Narration (40 words):** "Every day starts with a quick log: food, portion and time, sleep, activity, mood, stress and symptoms. FluxGuard analyzes the patterns, warns you when today looks risky, and helps you improve with tips and streaks. Then the loop starts again."
- **Sound:** UI ticks; a soft rising tone on the ring sweep; one gentle notification chime.
- **Transition out:** the phone slides off-frame while the four loop steps expand into the six-card feature grid.
- **Build notes:** `PhoneMockup` (`sampleTag`), `RiskRing`, `LoopStep`, `PushAlert`, `StreakBadge`. `spring()`, `interpolate()`, SVG arc draw.

### Scene 6 — Features · 01:02–01:14 · 12 s

- **Visuals:** Six feature cards in a 3×2 grid on light blue. Each card is an icon bubble plus a title. The orbs remain as tiny background accents.
- **Animation beats:**
  - 0.0 s: title enters.
  - +0.4 s: first row of cards at +0.00 / +0.07 / +0.14 s.
  - +0.8 s: second row of cards at +0.00 / +0.07 / +0.14 s.
  - +6.0 s: icons brighten in sequence.
  - Hold until 12.0 s.
- **On-screen copy (19 words):**
  - Title: "Everything in one app"
  - Card titles: Smart daily log · Validated stress check · Trigger report · Risk score & alerts · Personalized tips · Streaks & badges
- **Narration (20 words):** "Everything lives in one app: a smart log, a validated stress check, trigger reports, risk alerts, personal tips and streaks."
- **Sound:** six tiny UI ticks, one per card.
- **Transition out:** the cards slide outward and the grid lines become the axes of the 2×2 map.
- **Build notes:** `FeatureCard`, `IconBubble`. Staggered springs.

### Scene 7 — Where we fit · 01:14–01:26 · 12 s

- **Visuals:** A 2×2 positioning map on deep navy. Competitor text pills fill three quadrants; FluxGuard flies into the empty top-right corner.
- **Animation beats:**
  - 0.0 s: title enters; axes draw on.
  - +1.0 s: competitor pills fade in (+0.12 s each).
  - +4.5 s: the FluxGuard pill travels a curved path into the top right and glows.
  - +7.0 s: the edge line enters.
  - +9.0 s: caption settles.
  - Hold until 12.0 s.
- **On-screen copy (14 words):**
  - Title: "Where FluxGuard fits"
  - Edge line: "Links stress and reflux in one model — not two separate apps"
- **Labels:**
  - Axes: Tracks symptoms → Predicts & prevents · Gut only → Gut + mind
  - Pills: Moodfit · Mindful GERD · NoBurn · GERDragon · Food Marble · Cara Care · FluxGuard
- **Caption:** "Placement reflects each app's publicly listed features."
- **Narration (17 words):** "Existing tools focus on symptoms, food or mood. FluxGuard combines gut and mind in a prevention-first loop."
- **Sound:** a soft spatial whoosh as FluxGuard flies in.
- **Transition out:** the empty quadrant expands into the outer market circle.
- **Build notes:** `MarketMap`, `CompetitorPill`. SVG axis draw, path interpolation. Text pills only, no competitor logos.

### Scene 8 — Market + model · 01:26–01:38 · 12 s

- **Visuals:** Nested circles (global → Philippines estimate → Bohol pilot) on the left. A horizontal three-tier ladder (Free → Premium → Clinic) on the right, with Premium highlighted.
- **Animation beats:**
  - 0.0 s: title enters; the 1.03B circle grows.
  - +1.8 s: the ~15.8M circle grows, with its estimate caption.
  - +3.6 s: the Bohol pilot marker pulses.
  - +5.5 s: tier cards stagger in (Free, Premium, Clinic, +0.3 s each).
  - +7.5 s: arrows draw between the tiers.
  - Hold until 12.0 s.
- **On-screen copy (7 words):**
  - Title: "A big, underserved market"
  - Tier names: Free · Premium · Clinic
- **Labels:**
  - Circles: "1.03B — with GERD worldwide" · "~15.8M — Filipinos (estimate)" · "Bohol pilot"
  - Tier eyebrows: "For everyone" · "Monthly subscription" · "Per-clinic license"
- **Source caption:** "Estimate: global 13.98% prevalence (Nirwan et al., 2020) applied to 112.7M Filipinos (PSA 2024 Census) — not a local survey."
- **Narration (25 words):** "The need is global; we start with a focused pilot in Bohol. Free builds the habit, Premium monetizes insight, and clinics add trust and reach."
- **Sound:** low pulse; a subtle three-note motif as the tiers appear.
- **Transition out:** the tier ladder flattens into the horizontal timeline line.
- **Build notes:** `MarketCircles`, `PricingTier`. Scale interpolation, card stagger. No prices.

### Scene 9 — Progress + trust · 01:38–01:52 · 14 s

- **Visuals:**
  - **Part A:** a timeline with four milestones.
  - **Part B:** three trust pillars replace the timeline.
- **Animation beats:**
  - 0.0 s: title enters; the timeline line draws.
  - +0.8 s: milestone 1 (DONE).
  - +1.6 s: milestone 2 (DONE).
  - +3.0 s: milestone 3 (IN PROGRESS), with a gentle pulse.
  - +4.4 s: milestone 4 (NEXT), in outline style.
  - +7.0 s: the timeline fades up and out; the three pillars rise.
  - +10.0 s: shield and check accents settle on the pillar icons.
  - Hold until 14.0 s.
- **On-screen copy (19 words):**
  - Title: "Built so far"
  - Milestones: Figma prototype · Live backend · Flutter app · Pilot & feedback
  - Pillars: Preventive, not diagnostic · Medically grounded · Private by design
- **Labels:** DONE · DONE · IN PROGRESS · NEXT
- **Narration (30 words):** "Our prototype is designed and our backend is live. The Flutter app is in progress, then a pilot with a partner physician. We're preventive, medically grounded and private by design."
- **Sound:** quiet ticks for completed items; a warm lift as the pillars rise.
- **Transition out:** the pillars fade, and the orbs drift back in behind the team avatars.
- **Build notes:** `ProgressTimeline`, `TrustPillar`. Line draw-on, staggered cards.

### Scene 10 — OUTRO · 01:52–02:05 · 13 s

- **Visuals:** Three team avatars (initials) with names and the adviser line. Then three ask cards. The risk ring returns, closes around the logo and turns mint for the end card.
- **Animation beats:**
  - 0.0 s: avatars and names rise (+0.12 s each).
  - +2.2 s: adviser line.
  - +4.0 s: "We're looking for" and the three ask cards.
  - +7.5 s: team and asks fade; the risk ring sweeps in around the logo.
  - +9.0 s: ring completes in mint.
  - +9.6 s: tagline, "Thank you!" and contact enter.
  - +10.5 s: final lockup holds to 13.0 s.
- **On-screen copy (17 words):**
  - "We're looking for"
  - Ask titles: A partner physician · Pilot users · Seed support
  - Tagline: "Stop reflux before it starts."
  - "Thank you!"
- **Labels:**
  - Names: Earl Benedict Ejara · Jezreel Lewis Guiritan · Richelle Domaluan
  - Role line: "Co-founders · BS Information Technology, Cristal e-College"
  - Adviser: "Adviser: Michael Spike Rondulf L. Cuizon"
  - End card: "FluxGuard" · `[CONTACT EMAIL]`
- **Narration (27 words):** "We're Earl, Jezreel and Richelle, with our adviser, Mr. Cuizon. We're looking for a partner physician, pilot users and seed support. FluxGuard: stop reflux before it starts."
- **Sound:** the music resolves; one soft final chime. No salesy sting.
- **Transition out:** the end card holds; fade to deep navy only after the final beat.
- **Build notes:** `TeamCard`, `AskCard`, `RiskRing`, `LogoMark`, `EndCard`. The ring match-cuts back to the intro geometry.

---

## 5. Narration — clean read

About 240 words over 2:05. Each paragraph starts at its scene's timecode; pause naturally between scenes.

**[00:00]** For millions, reflux feels random. One day it's fine. The next, the burn is back.

**[00:07]** One in seven adults live with reflux disease — over a billion people. Anxiety is linked to over three times the odds of severe symptoms. Yet most treat the burn, not the cause.

**[00:22]** Reflux rarely comes from one thing. Food, sleep, stress and movement interact — and single-purpose apps only see one piece.

**[00:34]** That's the gap FluxGuard fills: connect the dots, learn the pattern, and act earlier.

**[00:42]** Every day starts with a quick log: food, portion and time, sleep, activity, mood, stress and symptoms. FluxGuard analyzes the patterns, warns you when today looks risky, and helps you improve with tips and streaks. Then the loop starts again.

**[01:02]** Everything lives in one app: a smart log, a validated stress check, trigger reports, risk alerts, personal tips and streaks.

**[01:14]** Existing tools focus on symptoms, food or mood. FluxGuard combines gut and mind in a prevention-first loop.

**[01:26]** The need is global; we start with a focused pilot in Bohol. Free builds the habit, Premium monetizes insight, and clinics add trust and reach.

**[01:38]** Our prototype is designed and our backend is live. The Flutter app is in progress, then a pilot with a partner physician. We're preventive, medically grounded and private by design.

**[01:52]** We're Earl, Jezreel and Richelle, with our adviser, Mr. Cuizon. We're looking for a partner physician, pilot users and seed support. FluxGuard: stop reflux before it starts.

---

## 6. Component list

| Component | Purpose | Props | States |
|-----------|---------|-------|--------|
| `GlowOrbField` | Keeps the continuous orb world alive behind every scene | `orbs`, `background`, `driftAmplitude`, `driftSpeed`, `sceneProgress` | problem, insight, product, outro |
| `Orb` | One lifestyle factor (Food, Sleep, Stress, Activity) | `label`, `position`, `size`, `glow`, `tone` (coral / sky / mint / amber), `opacity`, `driftSeed`, `connected` | separated, flicker, connected, gathering, safe, background |
| `OrbNetwork` | Connects the four orbs to the "Reflux episode" hub | `nodes`, `hub`, `paths`, `lineColor`, `drawProgress` | idle, drawing, connected, converging |
| `ShieldGather` | Moves the orbs and lines into the logo | `orbPositions`, `targetPositions`, `progress`, `lineProgress` | separated, gathering, formed |
| `LogoMark` | White shield-with-check in a rounded sky-blue square | `size`, `scale`, `opacity`, `checkProgress` | hidden, outline, resolved, endCard |
| `Headline` | All titles and statements, from type tokens | `text`, `role` (display / section / sub), `align`, `progress` | hidden, entering, visible, exiting |
| `StatCounter` | Approved statistics only | `value`, `prefix`, `suffix`, `label`, `countDuration` | hidden, counting, settled |
| `SourceCaption` | Source / estimate captions | `text`, `maxWidth`, `opacity` | hidden, visible |
| `PhoneMockup` | Product visualization | `screen`, `scale`, `shadow`, `uiProgress`, `sampleTag` (always `true` when sample values show) | home, alert |
| `RiskRing` | Hero gauge in scene 5 and the outro | `value` (24 in scene 5; none in the outro), `label`, `tone`, `trackColor`, `size`, `sweepProgress` | neutral, sweeping, low, outro |
| `LoopStep` | Log / Analyze / Alert / Improve | `index`, `label`, `icon`, `active`, `progress` | idle, active, complete |
| `PushAlert` | Early-warning notification | `body`, `icon`, `slideProgress` | hidden, entering, visible |
| `StreakBadge` | Habit reinforcement (sample value) | `label`, `icon`, `progress` | hidden, popping, visible |
| `FeatureCard` | Six-feature grid | `title`, `icon`, `index`, `active` | entering, idle, highlighted |
| `IconBubble` | Shared icon container | `icon`, `size`, `tone`, `background` | idle, active |
| `MarketMap` | 2×2 competitive landscape | `xLabels`, `yLabels`, `pills`, `fluxGuardPosition`, `drawProgress` | empty, populated, fluxGuardEntering, complete |
| `CompetitorPill` | Text-only competitor marker | `name`, `position`, `tone`, `opacity` | hidden, visible, highlighted |
| `MarketCircles` | Nested opportunity circles | `levels`, `labels`, `estimateCaption` | collapsed, expanding, complete |
| `PricingTier` | Free / Premium / Clinic | `name`, `eyebrow`, `highlight`, `index` | hidden, entering, active |
| `ProgressTimeline` | Product progress | `milestones` (title + status), `drawProgress` | drawing, complete |
| `TrustPillar` | Three trust pillars | `title`, `icon`, `index` | hidden, visible |
| `TeamCard` | Team avatars and adviser line | `initials`, `name`, `tone`, `index` | hidden, visible |
| `AskCard` | The three asks | `title`, `icon`, `index` | hidden, visible |
| `EndCard` | Final lockup | `tagline`, `contact`, `ringProgress` | forming, settled, hold |

---

## 7. Assets

### Available

- `FluxGuard_Pitch_Deck.pptx` — approved wording, sources and layout reference.
- Brand palette and logo treatment (white shield-with-check in a rounded sky-blue square).
- `docs/deck-outline.md` — extracted slide text and speaker notes.

### Not yet inventoried

- **`Fluxguard Motion graphics/`** — v1 ran without access to the repo, so this folder hasn't been checked. Inventory it before building and reuse anything that fits the brand system.

### To create

- Four orb artworks (Food, Sleep, Stress, Activity)
- Shield-with-check vector logo
- Risk ring arc (SVG)
- Phone frame and home-screen UI layers, with the "Sample screen" tag
- Icons: six feature icons, the four loop-step icons and three trust-pillar icons — lucide, 2 px stroke
- Push alert card and streak badge
- Market map axes, competitor pills and nested circles
- Tier cards, timeline markers, team initial avatars
- End-card lockup

### To supply (team)

- Contact email for the end card
- Royalty-free music track (optional)
- Real app screens from Figma (optional — they replace the drawn phone UI)

### Suggested asset structure

```
assets/
  brand/      fluxguard-logo.svg, colors.json
  orbs/       orb-food.svg, orb-sleep.svg, orb-stress.svg, orb-activity.svg
  ui/         phone-frame.svg, risk-ring.svg, push-alert.svg, streak-badge.svg
  icons/      log.svg, analyze.svg, alert.svg, improve.svg, feature-*.svg, trust-*.svg
  market/     market-axis.svg, competitor-pill.svg
```

---

## 8. Reference images — to produce

| File | Contents |
|------|----------|
| `refs/00-brand-board.png` | Palette swatches with hex codes, type specimen, logo mark, shape language, icon style |
| `refs/01-components.png` | Every component above in its key states (e.g. risk ring at 0%, 24% low and 70% high; orb idle vs. flicker; phone with the "Sample screen" tag) |
| `refs/styleframes/scene-01.png` … `scene-10.png` | One key frame per scene at its most important moment, with the v2 copy |
| `refs/storyboard.png` | Three thumbnails per scene (start, key moment, end), each labeled with scene number, timecode and a one-line action note |

All images are 1920 × 1080 unless noted. Check every frame against the 96 px margins, the 28 px minimum text size, the text budget and color contrast.

---

## 9. Claims and source rules

- No statistics beyond the three approved facts.
- Every statistic carries an on-screen source caption.
- "~15.8M Filipinos" is always labeled an estimate, never presented as a local survey.
- Sample values appear only inside the phone, always with the "Sample screen" tag, and are never narrated as results.
- FluxGuard is preventive, not diagnostic. Never imply that it diagnoses GERD, guarantees prevention, or has clinically validated risk scores before the planned physician validation.
- Competitor placement keeps the caption "Placement reflects each app's publicly listed features." Text pills only, no logos.
- No testimonials, user counts, prices, clinical outcomes or performance claims.
- Every critical point is readable on screen with the sound off.

---

## 10. Implementation notes for the Remotion build

- Top-level `AbsoluteFill` scene container with a shared `BrandContext` (colors, type tokens, spacing).
- Keep the four `Orb` instances mounted across scene boundaries; animate their transforms rather than remounting them.
- `spring()` for entrances, `interpolate()` for controlled position, color and opacity changes.
- SVG paths for every connection line and the risk ring arc, so draw progress stays resolution-independent.
- `TransitionSeries` only where the persistent-world interpolation can't carry the change.
- All text comes from `src/content.ts` and the type tokens; no per-scene font-size improvisation.
- A shared layout helper enforces the 96 px safe margins.
- Source captions are real components, never baked into images.
- Keep the phone UI modular so the risk ring, alert, tiles and badge can be reused in close-ups and the outro callback.
