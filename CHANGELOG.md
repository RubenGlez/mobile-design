# Changelog

All notable changes to the mobile-design skill are documented here. The version tracks `metadata.version` in `SKILL.md`.

## 1.0.0

Breaking: the skill is now purely about design and works with any stack. Informed by an analysis of 22 design skills (`research/skills-landscape-2026-11.md`).

- Removed all framework code and library guidance (React Native, Expo, Reanimated, SwiftUI, Compose). Designs are specified in platform-neutral terms, and the agent translates them into the user's stack only after reading the project.
- Added modes with their own playbooks: Shape, Design, Critique, Refine (polish, bolder, quieter, distill), Harden, and Adapt.
- Added `craft-floor.md` with three rule tiers: a non-negotiable Floor; Reflexes, the tells of generated mobile UI in structure, surface, motion, and copy, each paired with a better starting point; and Finish checks.
- Added `critique.md`, which replaces `review-rules.md` and `review-checklists.md`: first impression, specificity verdict, five ordered lenses, trunk test, five-second test, cognitive load, Nielsen scoring, goodwill meter, personas, P0–P3 severity, a coverage-aware report format, and rule IDs MD-001 to MD-016.
- Added `principles.md` (eight design principles, the four kinds of feedback, wayfinding, UX laws), `states-edge-cases.md` (state modeling, the four data states, worst-case content, loading timing, optimistic updates, offline, and a risk preflight that absorbs `feasibility-risk.md`), `ux-writing.md`, `trust-ethics.md` (high-stakes moments, privacy, a catalog of 16 deceptive patterns with honest alternatives, paywalls), and `modes.md`.
- Reworked the design process: design read plus thesis, asking once or inferring, material inventory, signature object, a compact plan with a mirror test, emotional design (felt state, peak-end), and an optional `DESIGN.md`.
- Rewrote motion as design: a frequency gate, interruptibility, springs by damping and response, gesture tracking and release with velocity handoff, the causality, harmony, and utility of haptics, related accessibility settings, and a motion spec format.
- Rewrote the platform references with native trust tests, system surfaces (widgets, Live Activities, shortcuts, notifications, launch), and an iOS-Android translation table.
- Rewrote the evals: 22 cases covering every mode, a baseline protocol, six judging axes, and global failure signals.

## 0.3.0

- Added a conditional feasibility preflight for permission, offline, data, native-runtime, and performance risks, with fallbacks and verification instead of a misleading numeric score.
- Added trust, emotional-design, and recovery guidance for high-value mobile moments, including finance, permissions, health, checkout, onboarding, and privacy.
- Made implementation scope explicit: React Native and Expo are the concrete code path, while native iOS and Android implementation requires inspecting the appropriate native project and toolchain.
- Extended review checks and evaluation coverage for risky mobile features and stack-appropriate implementation advice.

## 0.2.0

- Fixed form guidance for iOS `phone-pad`, which does not fire `onSubmitEditing`, and made password autofill hints safe across platforms.
- Fixed loading button examples so their visual, interactive, and accessibility disabled states agree.
- Added reduced-motion detection for React Native and explicit fallback guidance.
- Added adaptive-window, external-input, RTL, and localization guidance plus corresponding QA checks.
- Added stable review rule IDs, a terse review format, and a 12-case evaluation suite for maintainers.
- Added component-contract guidance for reusable primitives and refreshed canonical sources.

## 0.1.0

- Corrected `forms.md` focus flow: `returnKeyType` only relabels the return key; the anatomy example now wires `onSubmitEditing` and `submitBehavior` to advance focus.
- Made async announcement guidance cross-platform in `forms.md` and `accessibility-touch.md` (`accessibilityLiveRegion` is Android-only; iOS needs `AccessibilityInfo.announceForAccessibility`).
- Fixed the `accessibility-touch.md` hitSlop example to meet the 48dp Android minimum.
- Reframed the iOS HIG principles in `platform-ios.md` around the current foundations and Liquid Glass; kept Clarity/Deference/Depth as legacy heuristics.
- Added Android SMS-OTP autofill (`autoComplete="sms-otp"`) to the one-time-code row in `forms.md`.
- Corrected the `createStaticNavigation` linking description in `navigation.md`.
- Resolved the Android `fontFamily`/`fontWeight` conflict in `typography-color.md` and added a font-licensing caveat.
- Fixed the non-activatable Compose button example in `platform-android.md`.
- Marked `design-process.md` as the canonical source for design dials; `SKILL.md` and `motion-haptics.md` now note they mirror it.
- Added an offline fallback to the Source Freshness rule, scoped the "start with design-process.md" mandate, and added `license` and `metadata.version` to the skill frontmatter.
- Removed the stale skills.sh badge and documented what `npx skills add` installs.
