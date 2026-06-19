# Mobile Design

[![skills.sh](https://skills.sh/b/RubenGlez/mobile-design)](https://skills.sh/RubenGlez/mobile-design)

Mobile Design is an agent skill for designing, implementing, and reviewing professional mobile UI for React Native, Expo, iOS, and Android apps.

It gives coding agents a mobile-product design process with platform-aware guidance for navigation, forms, typography, color, accessibility, touch targets, gestures, haptics, motion, safe areas, and React Native implementation details.

## Install

Install with the skills CLI:

```bash
npx skills add RubenGlez/mobile-design
```

Then ask your agent for mobile UI work, for example:

```text
Use the mobile-design skill to redesign this checkout screen for iOS and Android.
```

## What It Covers

- React Native and Expo mobile UI implementation
- iOS and Android platform conventions
- Navigation, screen structure, forms, search, filters, and state design
- Typography, color, dark mode, visual hierarchy, and design tokens
- Touch targets, accessibility, Dynamic Type, screen readers, and motor access
- Gesture handling, haptics, motion, loading states, and Reduce Motion support
- Mobile design reviews with platform, accessibility, and polish checklists

## Skill Structure

```text
SKILL.md
references/
  accessibility-touch.md
  design-process.md
  forms.md
  motion-haptics.md
  navigation.md
  platform-android.md
  platform-ios.md
  react-native-implementation.md
  review-checklists.md
  screen-patterns.md
  source-map.md
  typography-color.md
  visual-system.md
```

`SKILL.md` contains the trigger metadata and operating loop. The `references/` files are loaded selectively by the agent based on the mobile task.

## Best Use Cases

- Redesigning mobile screens or flows
- Building React Native or Expo components with production-level states
- Reviewing app UI for usability, accessibility, and platform fit
- Translating a rough product idea into a mobile-native interaction model
- Checking iOS HIG, Material Design, and current mobile library guidance before implementation advice

## Distribution

This repository is published for installation through skills.sh:

```bash
npx skills add RubenGlez/mobile-design
```

After installs are reported by the skills CLI, the package appears on skills.sh at:

```text
https://skills.sh/RubenGlez/mobile-design
```
