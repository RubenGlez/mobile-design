# Typography and Color

Use for type scales, text scaling, font choice, color roles, contrast, and status color.

## Type Principles

- System fonts are the safest default (SF Pro on iOS, Roboto or the device font on Android). They come with optical sizing, tuned tracking, full language coverage, and the ability to scale with the user's text size.
- A custom face has to earn its cost: brand voice, editorial identity, or real cross-platform consistency. Put it in display moments and content, and keep controls and navigation in the system face when the brand allows. Check the license and the language coverage before choosing it.
- Use one family, or two with clearly different roles. Build hierarchy from size, weight, and leading together, not from size alone. Weight adds emphasis without taking space.
- Primary reading text sits around 16–17pt/sp. Avoid text below 11pt/sp, and never put essential information in the smallest size.
- Tracking depends on size: tighten large display type slightly, keep body near 0, and loosen very small text a little. One letter-spacing value for every size is wrong somewhere.
- Leading works inversely to size: tight for large titles (about 1.1–1.2×), comfortable for body (about 1.3–1.5×). Give more room to scripts with tall ascenders and descenders.
- Use tabular figures for numbers that change, align, or compare: prices, timers, tables, stats.
- Keep line length readable (about 45–75 characters) on wide windows.

## Type Scale

Map every string to a role. Never pick sizes per screen.

| Role | Typical iOS | Typical Android (M3) | Use |
| --- | --- | --- | --- |
| Large title / Display | 34 | Display 36–57 | Top-level screen titles, hero numbers |
| Title | 28 / 22 / 20 | Headline 24–32, Title L 22 | Screen and section titles |
| Headline | 17 semibold | Title M 16 medium | Row titles, emphasized labels |
| Body | 17 | Body L/M 16 / 14 | Primary reading text |
| Callout / Subhead | 16 / 15 | Label L 14, Body S 12 | Secondary text, control labels |
| Footnote / Caption | 13 / 12 | Label M/S 12 / 11 | Metadata, timestamps |

These are reference points. Verify current values in the platform sources. Operational apps use a compact scale (ratio about 1.125–1.2); expressive apps can use larger jumps for display moments. Keep the number of distinct sizes small; near-duplicate sizes read as mistakes.

## Text Scaling

- All text follows the user's system text size. Accessibility sizes can more than triple body text.
- Layouts respond: rows wrap to multiple lines, side-by-side elements stack, fixed heights become flexible, and horizontal groups scroll.
- Cap scaling only for elements that cannot reflow (tab labels, some badges), and make sure the information stays available elsewhere, for example in an expanded label on long press.
- Test at the largest size on the smallest width.

## Color Roles

Define roles with a light and a dark value each, plus the contrast figure against the surface they sit on:

| Role | Purpose |
| --- | --- |
| background / surface / surface-raised | Layering |
| text-primary / text-secondary / text-tertiary | Text hierarchy (secondary ≥ 4.5:1 when it carries content) |
| separator / outline | Structure; input boundaries ≥ 3:1 |
| accent / on-accent | Primary action, selection, key state |
| success / warning / danger / info (+ "on" variants) | Status only |

On iOS, prefer the semantic system colors where possible. They adapt to dark mode and to Increase Contrast automatically. On Android, map brand colors to Material color roles so dynamic color, dark theme, and contrast levels resolve consistently.

## Contrast

| Element | WCAG 2.x AA minimum |
| --- | --- |
| Body text, including placeholders | 4.5:1 |
| Large text (about 24pt regular, or 19pt bold) | 3:1 |
| Meaningful icons, control boundaries, focus indicators | 3:1 |

- State the figure for every text and icon role in both themes.
- APCA gives a better perceptual reading for thin fonts and dark themes. Use it as a second opinion, but still meet the WCAG minimums, which remain the conformance standard.
- Interactive states (pressed, focused, selected) should raise contrast, not lower it.
- Disabled controls may fall below minimum contrast only when they are clearly disabled and not needed to understand the content.
- Text over images: check at the worst crop, and use a scrim when in doubt.
- Support the system's Increase Contrast setting with stronger separators and text.

## Meaning Beyond Color

- Pair every status color with text, an icon, or a shape: "Overdue" with an icon, not just red.
- For charts, use palettes safe for people with color-vision deficiency, add direct labels or patterns, and never rely on red versus green alone.
- Check critical flows in grayscale.

## Checklist

- Every string maps to a type role, and the scale has clear steps.
- At the largest text size: nothing clips, overlaps, or loses essential information.
- Long and translated strings wrap or truncate deliberately.
- Every color role has light and dark values with contrast figures.
- Status never depends on color alone.
- Numbers use tabular figures where they change or compare.
