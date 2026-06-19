# iOS Platform

Use this for iOS-specific interaction, visual conventions, HIG alignment, SF Symbols, safe areas, Dynamic Type, sheets, and Apple ecosystem surfaces.

## HIG Principles

Use Apple's core principles as practical checks:

- Clarity: text, icons, hierarchy, and controls are understandable.
- Deference: UI supports content instead of competing with it.
- Depth: layers communicate navigation, modality, and focus.

## Typography

- Prefer SF Pro and semantic text styles in native code.
- Support Dynamic Type.
- Avoid fixed-height containers that clip larger text.
- Use SF Mono for code or aligned technical data.
- Use custom fonts only when brand value outweighs platform familiarity and loading cost.

## Controls and Touch

- Minimum hit area: 44pt by 44pt.
- Use native-feeling controls when possible: buttons, toggles, segmented controls, pickers, sheets, context menus.
- Icons should usually be SF Symbols for iOS-native work.
- Use haptics sparingly for meaningful state changes.

## Navigation

- Bottom tab bars work well for 3-5 top-level destinations.
- Root screens can use large titles; pushed detail screens often use compact titles.
- Preserve edge-swipe back.
- Do not place critical controls behind the home indicator, Dynamic Island, notch, or keyboard.

## Sheets and Modality

- Use sheets for focused supplementary tasks.
- Use detents when partial height improves context.
- Use full-screen only for immersive or high-commitment flows.
- Provide visible close/done actions.
- Confirm before discarding user work.

## Safe Areas

React Native:

```tsx
import { useSafeAreaInsets } from 'react-native-safe-area-context';

const insets = useSafeAreaInsets();

<View style={{ paddingTop: insets.top, paddingBottom: insets.bottom }}>
  {children}
</View>
```

Rules:

- Backgrounds may extend behind safe areas.
- Text and interactive controls should not.
- Bottom CTAs need home-indicator clearance.
- Keyboard-aware forms must preserve focused input and submit actions.

## Color and Materials

- Prefer semantic system colors for native iOS UI.
- Use adaptive asset catalog colors for brand tokens in native code.
- Blur is appropriate for transient or layered surfaces, not generic repeated cards.
- Test Increase Contrast and dark mode.

## Apple Ecosystem Surfaces

Use only when relevant to the product:

- Live Activities and Dynamic Island for time-sensitive ongoing tasks.
- Widgets for glanceable, repeat-use information.
- App Intents/Shortcuts for actions users repeat outside the app.
- Share sheets, context menus, and system pickers for platform-native tasks.

## iOS QA

- Dynamic Type at large sizes.
- VoiceOver labels, order, and modal focus.
- Reduce Motion.
- Increase Contrast.
- Dark mode.
- Safe areas on small, large, and Dynamic Island devices.
- Keyboard form behavior.
- Edge-swipe back and modal dismissal.
