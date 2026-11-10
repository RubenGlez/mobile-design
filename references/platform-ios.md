# iOS and iPadOS

Use for iOS-specific structure, controls, materials, typography, and system surfaces. Verify version-specific names and values against the current Human Interface Guidelines (`source-map.md`) before citing them. Apple revises its materials, navigation components, and layout guidance yearly.

## The iOS Trust Test

Would a fluent iPhone user trust this app at once, or would they hesitate at controls that don't behave as expected? The usual tell is an app that looks *ported*, from the web or from Android: custom navigation bars, a broken edge-swipe back, web-shaped buttons, hover-dependent affordances, Material-shaped controls. Default to the platform's patterns. Depart from them only for a reason users would thank you for.

## Structure and Navigation

- **Tab bar** for 2–5 top-level sections (sections, never actions), visible throughout each section's hierarchy. On iPad, the tab bar can become a sidebar.
- **Navigation stack** for hierarchy. Large titles on top-level screens collapse to an inline title on scroll. Detail screens use inline titles.
- **Edge-swipe back** always works. Never disable it or overlay it with a custom gesture.
- **Sheets** for focused, self-contained tasks. Use detents when keeping the underlying context visible helps. Full-screen covers for immersive or high-commitment tasks.
- **Clear Cancel and Done** in modal tasks. Swipe-to-dismiss stays enabled unless dismissing would lose work, in which case confirm.
- Search lives where the platform puts it: in the navigation bar, in a dedicated tab, or at the bottom where the current system places it.
- Don't stack modals. Don't hide the tab bar on push.

## Layout

- Lay out inside the safe areas. Backgrounds and media may extend under the bars; text and controls may not.
- Respect the standard margins and the readable content width on iPad.
- Use size classes, not device names, to restructure. iPad multitasking can give the app a compact width.
- Grouped (inset) lists for settings-shaped content. Avoid bespoke card stacks for that job.

## Controls

- Prefer system controls: buttons (with the system's prominence levels), toggles, segmented controls, steppers, pickers, menus, context menus, swipe actions, and share sheets. Reinventing these for flavor is the most common native tell.
- **44×44pt** minimum hit area.
- One tint color drives the interactive elements. Don't use it for decoration.
- Context menus (long press) for secondary actions on content, always with a visible path as well.

## Typography

- Use SF Pro through the system text styles (Large Title through Caption 2) so text follows Dynamic Type. Body is 17pt at the default size, and nothing essential goes below 11pt.
- Custom fonts must scale with Dynamic Type, including the accessibility sizes, and should map to the system text styles.
- Use SF Mono for code and aligned technical data, and tabular figures for changing numbers.

## Color and Materials

- Semantic system colors (label, secondary label, system background, grouped background, separator, tint) adapt to Dark Mode and Increase Contrast automatically. A custom color needs light, dark, and increased-contrast variants.
- Use the system materials (including the current Liquid Glass treatment) for bars, sheets, and controls floating above content, rather than hand-rolled blur. Keep content legible on top, never stack translucent layers, and respect Reduce Transparency.
- Dark Mode is a first-class appearance. Design and test both.

## Iconography

- Use SF Symbols for UI icons. They align with text, scale with Dynamic Type, and come in weights and rendering modes. Match the symbol weight to the adjacent text.
- Custom symbols follow the same metrics.

## Feedback

- Haptics: use the system types (selection, impact, notification success/warning/error) for meaningful events only (`motion-haptics.md`).
- Alerts only for critical information and destructive confirmations. Prefer inline messages and banners for everything else.
- Show waiting immediately: acknowledge the tap, then show inline progress or a skeleton.

## System Surfaces

Design these when the product benefits. Each needs its own design, not a shrunken screen:

- **Widgets**: glanceable, personal information on the Home and Lock Screen, in each supported size. Tapping one opens the matching content directly.
- **Live Activities and the Dynamic Island**: ongoing, time-bound tasks (a delivery, a ride, a workout, a timer), with compact, minimal, and expanded presentations.
- **App Shortcuts and Siri**: the few actions users repeat outside the app.
- **Notifications**: high value only, grouped and categorized, with actions where they save a trip into the app.
- **Spotlight and the share sheet**: make content findable and shareable through the system.
- **App icon and launch screen**: the launch screen mirrors the first screen (no splash logos or loading theater). The icon is simple, recognizable at small sizes, and provided in light, dark, and tinted variants.

## Interruptions

Calls, Siri, app switching, Control Center, and the lock screen interrupt at any moment. Pause media and games, save drafts, keep the position, and resume exactly where the user was.

## iOS Checklist

- Dynamic Type at the largest accessibility sizes, on the smallest iPhone.
- VoiceOver labels, order, and focus handling in modals.
- Reduce Motion, Reduce Transparency, Increase Contrast, Bold Text.
- Light and dark appearance.
- Safe areas on Dynamic Island, notch, and home-button devices, with the keyboard open.
- Edge-swipe back on every pushed screen. Sheet dismissal protects work.
- iPad: full screen, split width, keyboard, and pointer, if supported.
