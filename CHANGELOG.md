# Changelog

All notable changes to the mobile-design skill are documented here. The version tracks `metadata.version` in `SKILL.md`.

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
