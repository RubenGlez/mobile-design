# Android

Use for Android-specific structure, Material Design 3, edge-to-edge layout, dynamic color, adaptive layouts, and system surfaces. Verify version-specific component names, motion specs, and policies against current Material and Android guidance (`source-map.md`). Material's expressive components and the platform's edge-to-edge requirements keep changing.

## The Android Trust Test

Would a fluent Android user trust this app, or trip on components that don't behave as expected? The usual tell is an iOS app wearing Android's skin: back chevrons that ignore system back, a bottom tab bar copied untouched onto tablets, Cupertino-style switches and dialogs, centered titles everywhere. Material 3 is the reference. Theme the brand through it rather than around it.

## Structure and Navigation

- **Navigation bar** (bottom) for 3–5 top-level destinations on compact windows. Switch to a **navigation rail** on medium and expanded widths, and to a drawer only for many destinations or secondary areas.
- **Top app bar** gives screen context. Its variants (center-aligned, small, medium, large) collapse on scroll.
- **System back always works**, including the predictive back gesture, which previews the destination. Never trap the user or hijack the gesture. Intercept back only to protect unsaved work.
- **FAB** for the single most common, constructive action on a screen. One FAB at most. Never use it for secondary or destructive actions. Use an extended FAB when the icon alone is unclear.
- Bottom sheets for supplementary content and short tasks. Dialogs only for decisions that must interrupt.

## Edge-to-Edge and Insets

Current Android versions draw apps edge to edge by default.

- Backgrounds and scrolling content can extend behind the status bar and navigation bar. Text and controls are inset clear of the system bars, display cutouts, and the keyboard.
- Bottom bars and CTAs sit above the navigation bar, whether it's gesture navigation or three buttons.
- Keep system bar icons legible against what's behind them (contrast scrims where needed).
- Test with gesture navigation and with three-button navigation.

## Controls

- Use Material components: filled, tonal, outlined, and text buttons (in that order of emphasis); switches; checkboxes; chips (assist, filter, input, suggestion); segmented buttons; menus; sliders; and date and time pickers.
- **48×48dp** minimum touch target, with at least 8dp between targets.
- Snackbars for brief feedback, with an Undo action when the operation is reversible. Never use a toast for anything the user must act on.
- Touch feedback uses the platform's ripple or state layers, consistently.

## Typography

- Use the Material type scale: Display, Headline, Title, Body, and Label roles, each in large, medium, and small. Map every string to a role.
- Roboto or the device font is the system face. A brand face comes in through the type scale, keeping body text, labels, and controls legible.
- Text sizes use sp so they follow the user's font size, and the layout survives the largest font and display size settings.

## Color and Theming

- **Color roles** (primary, on-primary, primary-container, secondary, tertiary, surface and its container levels, surface-variant, outline, error) resolve light, dark, and contrast variants consistently. Raw hex values break this.
- **Dynamic color**: on supported devices the scheme can come from the user's wallpaper. Decide whether the brand adopts it fully, partially (neutrals only), or not at all, and always keep a static fallback scheme. Check contrast under generated palettes.
- **Elevation** is tonal first: higher surfaces take a stronger surface tint, with shadows used sparingly.
- The dark theme is a first-class scheme, not an inversion.

## Iconography

- Use Material Symbols with consistent fill, weight, grade, and optical size. Filled icons mark the selected destination in navigation.
- Don't use SF Symbols-style glyphs on Android unless the whole app is deliberately custom.

## Motion

- Use Material motion patterns: container transform (an element expands into its detail), shared axis (spatial or sequential navigation), fade through (unrelated destinations), and fade (enter and exit). Use them with the standard or emphasized easing.
- Predictive back shows a preview of the destination. Custom transitions must support it.
- Honor the system "Remove animations" setting with a crossfade or an instant cut.

## Adaptive Layouts

- Restructure by window size class: compact (one pane plus a navigation bar), medium (rail, optional second pane), expanded (list-detail or supporting pane, persistent navigation).
- Foldables: support folded, unfolded, and tabletop postures, and keep content clear of the hinge.
- Large screens, ChromeOS, and desktop windows: keyboard, mouse, and resizable windows are normal.

## System Surfaces

- **Widgets**: glanceable and resizable, themed with the app's color roles (including dynamic color), with a direct deep link on tap.
- **Notifications**: grouped into channels users can control, actionable, and high-value only. Ask for notification permission in context.
- **App shortcuts**: a few static and dynamic shortcuts for frequent actions.
- **Share and deep links**: verified app links open content directly. Use the system share sheet.
- **Photo picker and privacy-preserving APIs**: prefer system pickers to broad storage or media permissions.
- **Splash screen and icon**: use the system splash with the app icon. No extra splash or loading screens. Provide an adaptive icon, and a monochrome themed variant.

## Android Checklist

- TalkBack labels, traversal order, and custom actions.
- The largest font size and display size settings.
- Light, dark, and dynamic color (with several wallpapers), plus the static fallback.
- Edge-to-edge with gesture and three-button navigation, with the keyboard open.
- System back and predictive back on every screen.
- Compact, medium, and expanded widths, and foldable postures if supported.
- Performance on a low-end target device for long lists and image-heavy screens.
