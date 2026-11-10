# Adaptivity, Cross-Platform, and Localization

Use for Adapt mode: tablets, foldables, multitasking windows, orientation, input beyond touch, moving a design between iOS and Android, web-to-native, RTL, and localized content.

Adaptation is not scaling. The job is to rethink the experience for the new context, inside that context's conventions.

## Assess the Adaptation

1. **Source context**: what was the design made for, and what did it assume? (Phone only, portrait only, one platform's idioms, a website.)
2. **Target context**: the window size, orientation, platform, input method, and how the device is used (one-handed on the move, two-handed at rest, on a desk with a keyboard).
3. **What breaks**: navigation that no longer fits, layouts that stretch instead of restructuring, gestures or controls that don't exist on the target.

## Window First

Design for the available window, not a named device. The same app moves between sizes through rotation, split screen, folding, and window resizing.

| Window | Typical structure |
| --- | --- |
| Compact (under 600dp; most phones in portrait, about 320–440pt wide) | One pane, bottom navigation, reachable actions, no horizontal overflow |
| Medium (600–840dp; large phones in landscape, small tablets, unfolded foldables) | A navigation rail or sidebar, wider margins, an optional supporting pane |
| Expanded (840dp and up; tablets, desktop-class windows) | List-detail or supporting panes, persistent navigation, constrained line length, more density |

- **Restructure, don't stretch.** A phone layout scaled up on a tablet is the failure mode. Switch navigation (bar → rail or sidebar), use the extra width for list-detail, and turn sheets into popovers or side panels where the platform does.
- Never stretch buttons, text lines, or cards across a wide window. Constrain them and use the space for structure.
- Multitasking is just another size: a tablet can hand the app a phone-width window.
- Keep the user's selection, drafts, scroll position, and in-progress work across size changes.
- Foldables: keep critical content and controls away from the hinge, and support folded, unfolded, and half-folded postures.
- Support portrait and landscape unless the task truly requires one orientation. Never lock orientation to hide a layout bug.
- Never hide core functionality on smaller windows. If it matters, make it work there.

## Input Beyond Touch

- Keyboard: logical focus order, visible focus, Tab and Shift-Tab traversal, Return to activate, Escape or back to dismiss, and shortcuts for frequent actions on tablets with keyboards.
- Pointer and trackpad: hover feedback where the platform supports it, but never hover as the only way to reveal an action. Context menus on secondary click.
- Stylus: precise input where the product benefits (drawing, annotation, handwriting into text fields).
- Touch targets stay full size even when a pointer is available.

## Translating Between iOS and Android

Translate idioms; don't transplant them. Rebuild navigation and controls in the target's vocabulary, and carry the brand through the target's theming (color intent, type accent, shape, motion personality).

| iOS | Android |
| --- | --- |
| Tab bar | Navigation bar (compact), navigation rail or drawer (wider) |
| Back chevron and edge-swipe back | System back and predictive back gesture |
| Large title collapsing to inline | Top app bar (large, medium, or small) collapsing on scroll |
| Sheet with detents | Bottom sheet (modal or standard) |
| Action sheet / confirmation dialog | Bottom sheet or dialog |
| Alert | Dialog |
| Context menu (long press) | Menu (long press, or overflow) |
| Switch, segmented control, stepper | Switch, segmented button, chips |
| Swipe actions on list rows | Swipe actions or a long-press menu, plus visible actions |
| Toolbar or primary button for the main action | FAB or a primary button for the single main action |
| Banner / inline confirmation | Snackbar (with Undo when reversible) |
| SF Symbols, SF Pro, Dynamic Type | Material Symbols, Roboto / device font, sp scaling |
| Semantic system colors, materials | Material color roles, tonal elevation, dynamic color |
| Push, sheet, and zoom transitions | Shared axis, container transform, fade through |

The tells to avoid: on iOS, an app that looks ported from a website or from Android (custom nav bars, broken swipe-back, Material-shaped controls). On Android, an iOS app wearing Android's skin (iOS-style back chevrons that ignore system back, Cupertino switches, centered iOS titles everywhere).

A single, fully branded cross-platform design is a legitimate choice. It still owes each platform its guarantees: safe areas and insets, system back behavior, text scaling, reduced motion, platform haptics, and familiar placement of navigation and controls.

## Web to Native

Reconform, don't reflow. Replace web navigation (header links, footers, breadcrumbs) with the platform's model. Replace web-shaped controls with platform controls, hover affordances with touch-first ones, and fixed pixel type with scalable text. Then hold the result to the platform reference.

## Localization and RTL

- Format dates, times, numbers, currencies, units, names, and addresses for the user's locale and region settings. Never build sentences by concatenating fragments, because word order varies by language.
- Plan for text expansion: German and Finnish run about 30% longer, and short labels can double. Labels, tabs, buttons, and errors must wrap, reflow, or truncate without hiding the action. Leave room in fixed-width elements.
- Plan for contraction and other scripts too: CJK text is shorter but needs proper line height and wrapping; Thai and Arabic need taller line heights.
- Use leading and trailing, never left and right, for layout.
- In RTL, mirror layout and directional icons (back arrows, progress direction, list chevrons). Don't mirror media playback controls, clocks, logos, or icons whose meaning isn't directional. Keep numbers and Latin text in their own direction.
- Choose the language from the user's language settings, never from their location.
- Screen readers read each string in its own language. Mark mixed-language content.

## Verification Matrix

Run the smallest matrix that covers the change:

| Concern | Minimum check |
| --- | --- |
| Layout | Compact and expanded widths, plus one size in between |
| Orientation | Portrait and landscape, when supported |
| Foldable | Folded and unfolded, with nothing critical over the hinge |
| Tablet multitasking | Full screen and a narrowed window |
| Input | Keyboard traversal and one pointer interaction on input-heavy screens |
| Localization | One long-text locale, one RTL locale if supported, real locale formats |

If a platform, locale, or form factor is intentionally unsupported, say so instead of implying it was tested.
