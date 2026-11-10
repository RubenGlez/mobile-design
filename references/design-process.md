# Design Process

Use this for any design task. It turns the brief into decisions that follow the user, the context, the product, and the platform.

## Core Frame

Mobile is not a small desktop. It is personal, interrupted, thumb-driven, glanced at in motion, and constrained by system UI, keyboards, connectivity, and accessibility settings.

Before designing, identify:

- **User**: familiarity, ability, emotional state, privacy expectations, and stage (first run, returning, expert).
- **Context**: one-handed use, movement, glare, noise, connectivity, interruption.
- **Category**: finance, health, fitness, social, commerce, productivity, media, utility, education, creative.
- **Platforms**: iOS, Android, both, tablet or foldable, or a mobile web app that must feel native.
- **Task success**: the concrete outcome the user came for.
- **Constraints**: existing brand and design system, `DESIGN.md`, store requirements, supported sizes and locales.

Three questions anchor everything: what is the user trying to accomplish, how should this moment make them feel, and what is the one thing they should notice first?

## Design Read and Thesis

State one line before designing or critiquing:

`Reading this as: <category> for <audience in context>, with a <direction> interface, on <platforms>.`

- `Reading this as: a transfer flow for anxious first-time investors, with a calm, exacting interface, on iOS and Android.`
- `Reading this as: a run tracker glanced at mid-stride outdoors, with a bold high-contrast interface, Android-first.`

Then the thesis: the screen's single job, and the most characteristic thing about it. If you cannot name both, the design has no center yet.

## Ask Once, or Infer

Ask only when the answer changes the design and cannot be inferred safely: target platform, an existing brand or system to keep, real content that must appear, an accessibility or regulatory constraint. Ask in a single message of at most three questions, and assert the likely answer in each:

`I'm reading this as iOS-first with your current teal brand. Should Android ship at the same time, or later?`

Otherwise decide, then state the inferences in one line at the top of the response. When the project shows a pattern (tokens, components, navigation model, icon family), follow it unless the task is a redesign.

## Material Inventory

Before composing, list what the design can actually show:

- **Real**: names, numbers, prices, dates, places, copy, and assets the brief or product provides.
- **Pictures**: product UI, user content, photography, illustration. Note where each comes from.
- **Absent**: proof that does not exist yet (reviews, metrics, logos, testimonials). Never invent it. Leave a labeled slot, or design without it.

Content drives structure. A screen that has photographs leads with them. A screen about numbers leads with the number that matters, in context.

## Signature

Every product has one object it is known by: the ledger, the route map, the queue, the streak, the score, the recipe step, the waveform. That object is the signature. Show it at its best, early and large, made from the product's own material. A greeting above four stat cards is not a signature.

One signature per screen, with everything around it quiet. In utility apps the signature can be small and still be a real choice: a precise number treatment, a distinctive progress shape, a characteristic transition.

## Plan Before Producing

Write a compact plan before any detailed design:

- **Structure**: navigation placement, content order, the primary action and where the thumb reaches it. For layout options, sketch ASCII wireframes at compact width (and at regular width when tablets are supported).
- **System**: 4–6 named color roles with light and dark values and contrast figures; type roles and scale; spacing base; radius scale; elevation levels. If a system exists, list only the changes.
- **Signature**: what it is and why it belongs to this product.
- **Motion**: the one orchestrated moment, if the context supports it, and the feedback behaviors.
- **States**: the states this screen needs (`states-edge-cases.md`).

**Mirror test.** Would a neighboring product in the same category get this exact plan? Would you have produced it for a similar brief about a different product? If yes, it is a default: change one decision (structure, palette, type voice, or signature), and say what changed and why. If the plan is already specific, say so and keep it.

Check the plan against the platform. Navigation and controls still use familiar system patterns.

## Category Posture

Starting points, not rules.

| Category | Posture | Watch for |
| --- | --- | --- |
| Finance / banking | Calm, exact, explicit feedback | Playful motion near money, hidden risk, vague status |
| Health / wellness | Supportive, readable, reassuring | Shame language, alarming color without action, small text |
| Fitness / sport | High contrast, glanceable, decisive | Low outdoor contrast, tiny controls in motion |
| Social / community | Expressive, reactive, identity-rich | Unclear audience and privacy state, sterile layouts |
| Commerce | Image-led, confident CTAs, transparent cost | Cluttered grids, weak product inspection, late fees |
| Productivity / tools | Efficient, dense, predictable | Decorative motion, card mosaics, slow repeated paths |
| Media / entertainment | Immersive, content-first | Heavy chrome, generic thumbnails, poor loading |
| Kids / education | Clear, forgiving, playful | Tiny targets, punitive errors, unbounded stimulation |

### Read Cascade

Turn the read into first choices, then adapt to the product:

| Read | Type | Color | Radius | Motion | Layout |
| --- | --- | --- | --- | --- | --- |
| Finance, professional | System sans, strong numeric hierarchy, tabular figures | Cool neutrals, restrained accent, unambiguous status colors | 10–16 | Low, structural | Lists, summaries, explicit confirmation |
| Health, consumer | System or friendly rounded sans | Warm neutrals, soft accent | 16–24 | Gentle | Guided steps, supportive empty and error states |
| Fitness, outdoor | Bold sans, very large metrics | High contrast, glare-safe accent | 12–20 | Snappy | Large controls, bottom actions, glanceable stats |
| Social | Expressive but readable | Warmer palette, identity colors used sparingly | 20+ | Reactive | Content- and avatar-led, visible privacy state |
| Commerce / editorial | Display face for moments, readable body | Monochrome or rich brand color | 12–20 | Smooth | Image-led detail, short checkout path |
| Productivity | System sans, compact scale (ratio about 1.125–1.2) | Neutral roles, functional accent | 4–12 | Minimal | Dense lists, toolbars, separators over cards |
| Media | Content-led type, bold titles | Dark, media-first, scrims | 8–16 | Cinematic but restrained | Full-bleed media, clear playback controls |
| Kids / education | Friendly rounded type | Saturated but controlled | 20+ | Playful, forgiving | Large targets, clear progress, positive recovery |

Modifiers: *premium* means fewer colors and more precise spacing; *playful* means rounder shapes and springier response with predictable navigation; *calm* means softer contrast that still passes AA; *bold* means larger type and decisive CTAs; *native* means platform type, icons, transitions, and semantic colors.

## Emotional Design

Choose a feeling only when it helps the user finish: confidence before a payment, control during a permission request, relief after recovery, momentum after setup. Earn it with clarity and feedback, not with celebration layered over uncertainty.

- **Felt state first.** Name what the person is feeling at this moment (waiting anxiously, recovering from an error, finishing a streak). Find a physical analogue (a soft landing, a held breath, a door closing gently), then express it through one layer: easing, delay, copy tone, color temperature, or spacing.
- **Peak and end.** People remember the most intense moment and the last one. Pick one peak in the core flow (a milestone, a personal insight, a task completed after effort) and design it deliberately. Then design the ending: a summary, the next step, a reason to return. Keep everything else efficient.
- **Information weight.** Heavy news arrives calmly and with a next step. Good news can be immediate.
- **Ownership.** When the system fails, the copy owns it; never make the user feel responsible for it.
- **Warmth is active.** Removing friction is not the same as warmth. Acknowledge small wins briefly, and match the tone to the stakes.

High-stakes and trust moments are covered in `trust-ethics.md`.

## Mobile Realities

- Repeated primary actions belong in the lower half of the screen. Keep destructive actions out of accidental thumb paths.
- Users scan first. Strong headings, clear grouping, and visible state changes matter more than decoration.
- The keyboard covers about half the screen. Forms need visible focus, scrolling, and a reachable submit action.
- Offline, slow networks, declined permissions, and interrupted sessions are normal states. Design them.
- Accessibility settings are everyday preferences, not edge cases.
- Prefer conventional patterns for risky or familiar flows: back, forms, checkout, permissions, destructive actions, settings. Spend novelty on content, brand moments, empty states, and the signature.
- If a screen feels weak, repair in this order: content, grouping, spacing, type, contrast, color, depth, motion. Never use effects to compensate for unclear hierarchy.

## Dials

Set the dials after the design read, and let them shape density, motion, and visual risk.

| Dial | Low | High |
| --- | --- | --- |
| `DESIGN_VARIANCE` | Platform-native, expected | Distinctive, editorial, experimental |
| `MOTION_INTENSITY` | Instant state changes | Choreographed, physical transitions |
| `VISUAL_DENSITY` | Spacious and guided | Compact, operational, repeat-use |

| Value | `DESIGN_VARIANCE` | `MOTION_INTENSITY` | `VISUAL_DENSITY` |
| --- | --- | --- | --- |
| 1–3 | System type, standard navigation and controls, minimal custom surfaces | System transitions and press feedback only | Large spacing, few choices per screen, one guided action |
| 4–6 | Custom tokens, committed brand color, one distinctive detail | Continuity on sheets and lists, responsive press feedback | Standard app density, comfortable lists and forms |
| 7–8 | Custom display type or imagery, varied compositions, strong shape language | Shared-element moments, a richer peak moment | Compact rows, more data per screen, separators over cards |
| 9–10 | Experimental structure or interaction, only for briefs that invite it | Choreographed system; heavier verification burden | Expert, cockpit-like; strong grouping and careful accessibility checks |

Money, health, auth, permissions, and safety lower variance and motion. Repeated operational work raises density and lowers decorative motion. Low density is not emptiness: precision carries it. High variance must never break navigation, controls, or small-screen stability.

## DESIGN.md

`DESIGN.md` is an optional file at the project root that keeps decisions across tasks. If it exists, read it first; it overrides this skill's defaults, but not the Floor. Offer to write one only when a task made durable decisions. Keep it short:

```markdown
# Design
Read: <design read>
Platforms: <targets, sizes, locales>
Dials: variance <n> · motion <n> · density <n>
Signature: <the object the app is known by, and how it is shown>
Color roles: <role: light / dark, contrast>
Type roles: <role: size/leading/weight>
Spacing / radius / elevation: <scales>
Motion: <personality, durations or spring feel, reduced-motion approach>
Voice: <three adjectives, plus words used and avoided>
House rules: <reflexes deliberately kept, with reasons>
```
