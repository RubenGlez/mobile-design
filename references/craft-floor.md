# Craft Floor

Load this immediately before producing or changing a design. Apply it without reciting it. The brief's own words override everything here except the Floor.

Rules come in three tiers:

- **Floor**: never waived. These cover correctness, access, honesty, and safety.
- **Reflex**: a default that generated designs fall into. Avoid it unless the design has a real, specific reason. When you keep one, say why in one line that names this product. If the same reflex gets waived repeatedly in a project, it is a house style and belongs in `DESIGN.md`.
- **Finish**: craft detail that is visible up close. Check it and fix what is cheap. It never blocks delivery.

## Floor

Every item is checked on the result, not intended.

**Access**
- Touch targets are at least 44×44pt on iOS and 48×48dp on Android. Hit areas do not overlap, and adjacent targets keep at least 8pt/dp apart.
- Body text and placeholders reach 4.5:1 contrast. Large text (about 24pt regular or 19pt bold and above, WCAG's 18pt/14pt bold in CSS points), icons that carry meaning, and control boundaries reach 3:1. This holds in light and dark.
- Text scales with the system setting. At the largest accessibility sizes, layouts reflow (stack, wrap, scroll) instead of clipping or truncating essential text.
- Every interactive element exposes a name, role, and state. Reading order follows visual order. Decorative elements are hidden from assistive technology.
- Status and meaning never rely on color alone. Pair color with text, icon, shape, or position.
- Motion respects Reduce Motion with a gentler equivalent. Nothing flashes more than three times per second.

**Platform integrity**
- No essential content or control under system UI: notch, island, status bar, home indicator, navigation bar, display cutouts, or the keyboard.
- System back, edge-swipe back, and predictive back keep working. Modals have a visible dismiss path.
- Every gesture-only action has a visible alternative: a button, a menu item, or an edit mode.

**State and safety**
- Every region that shows data has loading, empty, error, and populated states, and every state offers a way forward.
- Destructive or irreversible actions are named explicitly ("Delete 3 photos") and protected by undo, or by confirmation when undo is impossible.
- Entered data survives validation errors, failed submits, navigation, backgrounding, and rotation.
- Pending is never shown as success. Payments, sends, and bookings show their real state.

**Honesty**
- No fabricated metrics, ratings, reviews, testimonials, user counts, or logos. Missing material becomes a labeled slot or is left out.
- No dark patterns: fake urgency or scarcity, confirmshaming, preselected upsells, hidden costs, obstructed cancellation, disguised ads (`trust-ethics.md`).
- Permissions are requested in context, after explaining the value, and the app stays usable when they are declined.

## Reflexes

These are what generated mobile UI looks like regardless of product. Each one is legitimate for some brief. Reaching for one when the brief leaves that axis free means no decision was made. The alternative listed is where to start instead.

### Structure

| Reflex | Start instead from |
| --- | --- |
| Home screen as a greeting ("Good morning, Alex") above a grid of equal stat cards | The one object the app is known by (the ledger, the route, the queue, the plan), first and largest. Stats follow, by urgency. |
| Everything in identical rounded cards, cards inside cards | Lists, grouped sections, spacing, and alignment. Use a card only when it is a distinct, tappable object. Never nest one card in another. |
| Hero-metric template: huge number, small label, trend chip, sparkline | The number in the sentence or row that gives it meaning, with its unit and comparison. Show a trend only when someone measured it. |
| Centered, website-style hero screens inside an app | Task-first screens: content and the next action, aligned to the platform's leading edge. |
| Carousels of onboarding slides that explain the app | Let the user start the task and explain in context. If onboarding is truly needed, keep it to three screens or fewer and make it skippable. |
| A modal or sheet for every task | Inline editing, disclosure, or a pushed screen. Modality is for focused, self-contained, interruptible tasks. |
| A floating action button plus a bottom CTA plus a header action, all for the same job | One primary action per screen, placed where the thumb is. |
| Hamburger menu as the primary navigation on a phone | A tab bar or navigation bar for 2–5 top-level sections. Menus are for secondary destinations. |

### Surface

| Reflex | Start instead from |
| --- | --- |
| Purple-to-blue gradients, glow halos, gradient text | One committed brand color used for action and state. Emphasis comes from weight and size. |
| Hand-rolled glassmorphism on ordinary cards | Opaque surfaces. Use translucency only where the platform uses it: bars, sheets, and overlays floating over moving content. |
| The same soft grey shadow under every element | One elevation scale, where depth means something: background, surface, raised, overlay. On Android, tonal elevation first. |
| One border radius on everything | A radius scale where nested corners are concentric (outer radius = inner radius + padding). |
| Emoji or mixed icon sets as UI icons | One icon family, one stroke weight matched to the adjacent text weight, outline by default and filled for the selected state. |
| Light or dark chosen by category ("fintech = dark") | Light or dark chosen by the use scene: who, where, under what light. Design both when the app follows the system. |
| Tracked all-caps eyebrow labels above every heading | The heading carries itself. Section labels are sentence case, in the body face, one step smaller. |
| Meta strings joined with middle dots, arrows appended to every button label | Plain structure: separate rows, a clear label and value, verbs on buttons. |
| Grey secondary text on colored surfaces | Secondary text tinted from the surface hue or from the foreground color at reduced emphasis. |
| Stock avatars, generic thumbnails, lorem ipsum | Real or realistic content at realistic lengths, or labeled slots naming what belongs there. |

### Motion

Motion slop shows up as frequency and uniformity. One instance can be polish; the same effect everywhere is a tell.

| Reflex | Start instead from |
| --- | --- |
| Pulsing, breathing, or glowing status dots and CTAs | A static indicator. Animate only on change. |
| Every list staggering in on every visit | No entrance motion on repeat views. Use at most one orchestrated moment, on first arrival or after a meaningful change. |
| Bouncy springs on toggles, menus, sheets, and dialogs | Critically damped motion for utility actions. Save bounce for gestures released with momentum. |
| Scale-up on every press, card, and image | Press feedback proportional to the element: a subtle highlight or a slight scale-down, the same everywhere. |
| Confetti or celebration on routine completions | Celebration reserved for rare, earned peaks. Routine success is a quiet confirmation. |
| Long transitions on frequent paths | Instant or near-instant changes for actions taken many times a day. |

### Copy

| Reflex | Start instead from |
| --- | --- |
| "Seamless", "effortless", "unlock", "elevate", "powerful", "supercharge", "all-in-one" | The concrete fact the word stands in for: the step count, the failure case, the number. |
| Two-fragment headlines ("Track less. Live more.") and "not X, but Y" contrasts | A plain sentence that names what the screen holds or does. |
| Generic labels: "Submit", "OK", "Continue", "Click here" | A verb and its object: "Pay $42.18", "Save address", "Send invite". |
| Apologetic or vague errors ("Oops! Something went wrong") | What failed, why if known, and what to do now (`ux-writing.md`). |
| Invented specifics (made-up percentages, testimonials, counts) | The brief's facts, or a plainer line without them. |

Tells change with every model generation. Learn why each one reads as generated (it is a default that fits every product), not only the list.

## Finish

These are checked up close. They separate designed from assembled.

- **Alignment.** Every element aligns to something: a grid line, a text edge, a baseline, or an optical center. Center icons and play glyphs optically, not geometrically.
- **Spacing.** Related items are close and groups are separated, with more space above a heading than below it. Values come from one spacing scale (a 4pt base works for most apps).
- **Type.** Clear steps in the scale, with no near-duplicate sizes. Tracking tightens as size grows. Numbers that change or compare use tabular figures. Lines end without single-word orphans in headings.
- **Depth.** Shadows have offset and soft blur and are tinted to the surface. Borders mark structure or state, shadows mark elevation, and neither stands in for the other.
- **Icons.** Same family, same stroke, same optical size per level. Icons align to the text baseline or center.
- **States.** Pressed, focused, selected, disabled, loading, and error look distinct and consistent across components. Pressed states do not shift the layout.
- **Content edges.** Long names, one-letter names, zero, one, thousands, missing images, and translated strings all hold (`states-edge-cases.md`).
- **System surfaces.** Status bar style matches the background beneath it, and the keyboard type matches the field. Launch, app icon, and splash match the first screen.
- **Consistency.** One primary button style, one card treatment, one radius scale, one link look, and the same verb for the same action everywhere.

## Pre-Delivery Pass

Before handing over, answer each briefly to yourself:

1. Does any Floor item fail? Fix it.
2. Which reflexes are present? Replace them, or state the specific reason for keeping each.
3. Would a neighboring product in this category get this same design? If so, change one decision and say which.
4. Is the boldness spent in one place? Remove one accessory if anything competes with the signature.
5. Which finish checks are cheap to fix now?
