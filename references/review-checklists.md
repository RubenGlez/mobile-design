# Review Checklists

Use this before final delivery or when the user asks for a design review.

## Design Read

- Design read stated.
- User context, task success, and platform are reflected in the UI.
- Dials are set and followed.
- Existing brand/system constraints are preserved or intentionally revised.

## Visual Quality

- Five-second comprehension test passes: place, purpose, priority, next action, state.
- Clear primary job for the screen.
- One coherent visual system for color, type, spacing, radius, iconography, and depth.
- No unsupported decorative defaults.
- Cards, blur, shadows, gradients, and animation communicate hierarchy or feedback.
- Realistic content and imagery.
- Text fits at small and large device widths.
- Dark mode is intentionally designed.

## Platform Fit

- iOS: safe areas, Dynamic Type, edge-swipe back, sheets/alerts/context menus, and SF Symbols are appropriate.
- Android: 48dp targets, system back, gesture nav, edge-to-edge/insets, Material 3 roles, and dynamic color are handled.

## Accessibility

- Normal text contrast >= 4.5:1.
- Large text and UI component contrast >= 3:1.
- Interactive elements have names, roles, and states.
- Focus order is logical.
- Important gestures have visible alternatives.
- Reduced Motion path exists for nonessential animation.
- Text scaling does not clip or overlap.
- Color is not the only status indicator.

## Interaction States

- Tappable elements are visually obvious.
- Pressed/focused, loading/submitting, disabled/unavailable, success, error/retry, empty, offline, and permission-denied states are handled where relevant.

## React Native / Expo

- Imports match installed packages.
- Tokens are used for spacing, radius, type, and color.
- Lists use stable keys and appropriate virtualization.
- `getItemLayout` only used for fixed-size rows.
- `removeClippedSubviews` tested if enabled.
- Images have dimensions, caching/loading behavior, and accessible labels when meaningful.
- Secure data is not stored in AsyncStorage.
- Platform divergence is explicit and maintainable.

## Verification

Run what applies: typecheck/lint/tests, iOS/Android screenshots, dark mode, large fonts, screen reader spot check, keyboard/form flow, deep links/back behavior, and performance checks for long lists or heavy animation.

If something cannot be verified, state it plainly in the final response.
