# Visual System

Use for visual direction, layout, surfaces, depth, imagery, iconography, shape, and perceived quality. In an app, the visual world contributes type, palette, shape, density, imagery, and one signature move. It never replaces the navigation model or the familiar controls.

## Direction From the Product

Draw the visual world from the subject: its materials, artifacts, vernacular, and the scene where the app is used. A trail app can borrow from topographic maps, a recipe app from cookbooks and kitchen light, a ledger from financial print. Translate the subject into tokens. Do not costume the interface as the object: no fake paper, no leather textures, no instrument bezels.

| Context | Direction | Avoid by default |
| --- | --- | --- |
| Trust and risk | Orderly structure, explicit states, stable color | Bounce, ambiguous icons, decorative effects near money |
| Wellbeing | Soft contrast that still passes AA, supportive hierarchy | Sterile dashboards, harsh warning colors |
| Performance and outdoor | Bold contrast, large figures, quick controls | Delicate type, low-contrast accents in sunlight |
| Commerce and editorial | Imagery that lets people inspect the product, confident CTAs | Crowded grids, generic thumbnails |
| Productivity | Quiet surfaces, dense lists, predictable affordances | Card mosaics, decorative gradients |
| Media | Content edge to edge, scrims, strong playback controls | Heavy chrome over content |

## Light and Dark

Choose the default from the use scene (who, where, under what light), not from the category. When the app follows the system appearance, design both themes deliberately.

Dark mode is its own design:

- Use near-black surfaces when depth and legibility matter. Use true black for OLED-first media or always-on contexts.
- Express elevation by making surfaces lighter as they rise, more than with shadows.
- Desaturate and slightly lighten accents so they don't vibrate against dark surfaces. Recheck every contrast figure.
- Redesign image scrims, charts, maps, and illustrations for dark backgrounds.
- Ease theme switches. Avoid abrupt full-screen brightness jumps.

## Hierarchy Before Decoration

When a screen feels weak, fix in this order: real content, grouping, spacing, type scale and weight, contrast, color, depth, motion. Borders, shadows, gradients, and animation never compensate for an unclear hierarchy.

Test it: blur the screen or view it at thumbnail size. The primary element and the primary action should still be the first things you see. Remove all decorative shadows: if the design no longer reads, depth was standing in for hierarchy.

## Layout

- Content first, with the primary action reachable. Bottom-anchored actions for linear flows, and sticky controls only when users need them repeatedly while scrolling.
- Lists for scanning, grids for visual comparison, carousels only when horizontal browsing is the core behavior.
- Align to the platform's leading edge. Centered layouts are for single-purpose moments (empty states, confirmations), not for content screens.
- Use one spacing scale on a 4pt base (4, 8, 12, 16, 20, 24, 32, 40, 48…). Related items sit close; groups are clearly separated. If items in a group are 8 apart, the gap between groups is roughly double.
- Use standard screen margins (typically 16–20pt/dp on phones) and keep them consistent. Constrain line length on wide windows.
- Asymmetric or editorial compositions must collapse to a stable single column at the smallest width, without horizontal scrolling.

## Color

- Define roles, not raw colors: background, surface, surface-raised, text-primary, text-secondary, separator, accent, on-accent, and status roles (success, warning, danger, info). Give each a light and a dark value.
- A strong default: one committed brand color for primary actions, selection, and key state. It carries meaning, so don't use it for decoration.
- Status colors mean status only. Don't use red for a brand moment.
- Keep one neutral temperature (warm or cool), and don't mix them by accident.
- On colored surfaces, tint secondary text and icons from that hue or from the foreground. Never use flat grey.
- On Android, plan whether the app adopts the user's dynamic color, and keep a static fallback scheme.

## Surfaces and Depth

Depth explains hierarchy: **background** (the screen), **surface** (grouped content, inputs), **raised** (floating controls, cards that move), **overlay** (sheets, menus, dialogs).

- Use one elevation scale. Shadows have an offset and a soft blur, and are tinted toward the surface below. A zero-offset glow is decoration, not depth.
- Shadows mark elevation. Borders mark structure (dividers, input outlines) and state (focus, selection). Don't use a border to fake depth, or a shadow to fake a divider.
- Use a card only when the content is a distinct object, often tappable. Otherwise use grouped lists, spacing, and separators. Never put a card inside a card.
- Translucent materials belong where the platform puts them: bars, sheets, and overlays floating above moving content. Never stack a translucent layer on another, keep text legible over them (heavier weight, higher contrast), and provide an opaque fallback when Reduce Transparency is on.
- Dim the background to focus a modal task. Use separation without a scrim for parallel, non-blocking panels.

## Shape

- Choose a radius system and apply it with rules: sharp (4–8) for tools and data, soft (10–16) for most apps, round (20+) for playful or social products.
- Nested corners are concentric: outer radius = inner radius + padding. Equal radii on a parent and its child look pinched.
- Use pills and capsules for controls whose shape is a platform convention. Don't turn every tag into a pill by reflex.

## Imagery

Order of preference: the user's or product's real content, then imagery specific to the domain, then generated or licensed imagery that fits the world, then labeled slots that say what belongs there.

- Crop to the subject. Check the crop at every aspect ratio the layout uses.
- Text over imagery needs a scrim or gradient and contrast checked at the worst crop.
- Use one treatment across the app (color grading, framing, corner style).
- Reserve the space for an image before it loads, and show a meaningful placeholder when it is missing.

## Iconography

- Use one icon family per app, with one stroke weight matched to the adjacent text weight (a heavier stroke beside semibold text). Never mix families on one surface.
- On iOS, prefer SF Symbols. On Android, prefer Material Symbols. A custom family must match their optical sizes and metrics.
- Outline icons by default and filled for the selected state, applied consistently at each level of the hierarchy.
- Use icon sizes from a scale (for example 16, 20, 24, 28), and align icons to the text baseline or optical center.
- Icon-only controls must be universally recognizable, have an accessible name, and keep a full-size hit area. When in doubt, add a text label.

## Signature Moves

Spend boldness once per screen. Candidates: a distinctive treatment of the hero object (the number, the map, the cover), a committed color field in one region, a display type moment, a characteristic transition, or a custom data visualization. Around it, everything stays quiet and systematic.
