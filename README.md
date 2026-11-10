# Mobile Design

Mobile Design is an agent skill that works like a senior mobile product designer for iOS and Android apps, whatever the stack: native, cross-platform, or a mobile web app.

**Interactive showcase:** [rubenglez.github.io/mobile-design-showcase](https://rubenglez.github.io/mobile-design-showcase/)

It shapes briefs, designs screens and flows, critiques and polishes existing UI, hardens states and edge cases, and adapts designs across platforms and window sizes. The output is design decisions (structure, specs, tokens, copy, motion, and critique) in platform-neutral terms, so they apply to any implementation.

The separate showcase repository contains interactive fictional product cases. It is intentionally kept outside this installed skill so visual assets and demo code do not add installation weight.

## Install

```bash
npx skills add RubenGlez/mobile-design
```

Then ask your agent for mobile design work:

```text
Use mobile-design to critique this onboarding flow.
This home screen looks generic. Make it feel like our product.
Design the empty, loading, and error states for the transactions list.
Adapt this iPhone design for Android tablets.
```

## What Makes It Different

- **Modes.** Shape, Design, Critique, Refine (polish, bolder, quieter, distill), Harden, and Adapt, each with its own playbook.
- **A craft floor in three tiers.** A non-negotiable Floor (access, platform integrity, state safety, honesty); Reflexes, the tells of generated mobile UI, each paired with a better starting point; and Finish checks for craft.
- **Specificity over templates.** A design read, a material inventory, a signature object, and a mirror test keep designs from becoming interchangeable.
- **Familiar where it matters.** Platform patterns carry navigation and controls. Identity lives in color, type, imagery, voice, motion, and one signature.
- **Structured critique.** First impression, specificity verdict, five ordered lenses, trunk test, Nielsen scoring, cognitive load, personas, a goodwill meter, P0–P3 severity, stable rule IDs, and a verdict.
- **States and edge cases.** Four data states, worst-case content, loading timing, optimistic updates, offline, and a preflight for risky capabilities.
- **Motion as design.** A frequency gate, interruptibility, springs described by damping and response, gesture phases, haptic rules, and a format for writing motion specs.
- **UX writing and ethics.** Message patterns and benchmarks, plus a catalog of deceptive patterns, each with its honest alternative.
- **Optional `DESIGN.md`.** Read when present, offered when a task made durable decisions.

## Skill Structure

```text
SKILL.md                     trigger metadata, modes, operating loop, Floor, routing
references/
  design-process.md          context, design read, material, signature, plan + mirror test, dials, DESIGN.md
  principles.md              eight design principles, feedback, wayfinding, UX laws
  craft-floor.md             Floor / Reflex / Finish, generated-UI tells
  modes.md                   Shape and Refine playbooks
  critique.md                critique sequence, instruments, severity, report format, rule IDs
  states-edge-cases.md       states, worst-case content, loading, offline, risk preflight
  screen-patterns.md         list, detail, home, search, tracking, forms, settings, onboarding, paywall
  navigation.md              information architecture, tabs, back, modality, entry points
  forms.md                   input intent, validation, submit, checkout, auth, search
  ux-writing.md              voice and tone, message patterns, benchmarks, copy tells
  visual-system.md           direction, light and dark, layout, color, depth, shape, imagery, icons
  typography-color.md        type scale, text scaling, color roles, contrast
  motion-haptics.md          purpose, frequency, fluid interaction, gestures, haptics, reduced motion
  accessibility-touch.md     targets, reach, gestures, screen readers, system settings
  adaptivity-localization.md windows, input, iOS-Android translation, web to native, RTL
  platform-ios.md            iOS and iPadOS conventions and system surfaces
  platform-android.md        Android and Material 3 conventions and system surfaces
  trust-ethics.md            high-stakes moments, privacy, deceptive patterns, paywalls
  source-map.md              official sources and precedence
evals/cases.md               22 forward-test cases with a baseline protocol
research/                    the analysis of the design-skill landscape behind v1.0
```

`SKILL.md` lives at the repo root, so `npx skills add` copies the whole repository into the consumer's skill folder. Agents load only `SKILL.md` and the references a task needs; `research/` and `evals/` are for maintainers and are never loaded during design work.

## Upgrading From 0.x

Version 1.0 is framework-agnostic. It no longer ships React Native, Expo, SwiftUI, or Compose code. When you are implementing, the agent translates the design decisions into your project's own stack after reading it.

## License

MIT
