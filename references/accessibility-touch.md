# Accessibility and Touch

Use for touch targets, reach, gestures, affordance, screen readers, focus, system accessibility settings, motor access, and cognitive load. Accessibility settings are everyday preferences. Large text, dark mode, Reduce Motion, and screen readers are used by many people, not by edge cases.

## Touch Targets

- Minimum hit area: 44×44pt on iOS, 48×48dp on Android. Design cross-platform components to 48 so they satisfy both.
- The visible element can be smaller (a 24pt icon) as long as its hit area reaches the minimum through padding.
- Hit areas never overlap. Adjacent targets keep at least 8pt/dp between them, and more between a destructive action and a frequent one.
- Whole rows are tappable when the row is the target. Don't make only the text or the chevron active.
- Nothing that looks interactive is dead, and nothing interactive looks static.

## Affordance

Interactive elements show at least one clear signal: a button treatment, a row chevron, a familiar platform control, a visible label, or an established icon convention. Tappable cards and static cards must look different. Icon-only actions need universally understood icons and accessible names; when in doubt, add a text label.

## Reach

- Repeated primary actions sit in the lower half of the screen. Phone navigation sits at the bottom.
- Top-of-screen actions are for rare or reversible actions, and frequent ones get a reachable path as well.
- Keep destructive actions away from the places the thumb rests and from frequently used targets.
- Design for both hands. Don't put every important control in one corner.
- On large phones and tablets, reach changes. Consider controls near the edges where people hold the device.

## Gestures

Gestures are invisible, so use them when they are expected, reversible, and backed by a visible control.

Good: pull to refresh on scrolling content; swipe actions on rows that reveal visible buttons; pinch to zoom media and maps; long press for context menus; dragging a sheet by its handle.

Avoid:

- Horizontal swipes across the whole screen that conflict with system back.
- Gestures near the bottom edge that fight the home indicator or gesture navigation.
- Critical actions available only as a gesture.
- Multi-finger or path-based gestures without a single-tap alternative.
- One region with competing gestures (tap, drag, and back-swipe on the same area).

## Screen Readers

Every interactive element exposes:

- **Name**: what it is or does ("Delete photo", not "trash icon").
- **Role**: button, link, toggle, slider, tab, heading, image.
- **State**: selected, checked, expanded, disabled, busy.
- **Value**: the current value of sliders, steppers, and progress indicators.
- **Hint**: only when the result of activating it isn't obvious.

Also:

- Group related content into one element when reading the parts separately would be noisy. For example, a product row reads "Linen shirt, $48, in stock".
- Hide purely decorative images and icons.
- Reading order follows visual order: top to bottom, leading to trailing, respecting RTL.
- Mark headings so users can jump between sections.
- Custom gestures and swipe actions are also available as accessibility actions.

## Focus and Dynamic Content

- When a modal or sheet opens, focus moves into it. When it closes, focus returns to the control that opened it.
- Async results (saved, failed, new messages) are announced politely, without stealing focus.
- Validation errors are announced and placed next to their fields. After a failed submit, focus moves to the first error.
- Timed content (toasts, auto-advancing carousels) waits long enough to be read and can be paused. Critical information never lives only in a toast.

## System Settings to Honor

| Setting | Design response |
| --- | --- |
| Larger text | Layout reflows; nothing clips; icons and controls scale with the text where that makes sense |
| Bold text | Weights increase; the layout still fits |
| Increase contrast | Stronger separators, borders, and text colors |
| Reduce motion | Cross-fades or instant changes (`motion-haptics.md`) |
| Reduce transparency | Opaque surfaces |
| Dark appearance | A deliberately designed dark theme |
| Differentiate without color | Icons, labels, or shapes on every status |
| Switch control / full keyboard access / external keyboard | Logical focus order, visible focus, every action reachable |
| Voice control | Visible labels match the accessible names, so "Tap Send" works |

## Motor and Cognitive Access

- Don't require fast or precise actions, rapid repeated taps, or a long hold without an alternative.
- Offer undo for destructive actions, and generous time limits that can be extended.
- Avoid nested scrolling regions that fight each other.
- Keep each decision small: one primary action, at most about four options at a time, and a clear next step.
- Use plain language. Never require users to remember information from a previous screen.

## Accessibility Checklist

- Every target meets the platform minimum, with no overlaps.
- Contrast figures are stated and pass in both themes.
- The largest text size works on the smallest width.
- A screen reader can complete the primary flow: names, roles, states, and order all check out.
- Every gesture has a visible alternative.
- Reduce Motion and Reduce Transparency paths exist.
- Status is never conveyed by color alone.
