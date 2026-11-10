# States and Edge Cases

Use for Harden mode, and whenever a design includes data, input, network, permissions, or risky capabilities. A design that shows only the populated state has drawn a quarter of the screen.

## Think in States

For every component or flow, list its states, the events that move between them, and what the user sees in each:

- **Form**: idle → editing → validating → submitting → success or error → back to editing, with the data kept.
- **Data region**: loading → populated, empty, or error; error → retrying; populated → refreshing → populated, keeping the stale data visible.
- **Sync item**: local → syncing → synced, or failed → retry or resolve conflict.
- **Async action**: idle → in progress → done or failed, with undo or retry.

Rules:

- No impossible combinations, such as loading and error shown at once, or a success screen while a request is still pending.
- Every state has a way out: retry, edit, go back, contact support, continue offline.
- Map every state to a visible representation and copy. Name the states in the spec so a builder cannot skip them.

## The Four Data States

Every region that shows data designs all four:

| State | Design for | Avoid |
| --- | --- | --- |
| **Loading** | A skeleton in the shape of the real content, or inline progress when the shape is unknown | Full-screen blocking spinners; skeletons that don't match the final layout |
| **Empty** | What belongs here, why it is empty, and the one action that fills it | A bare "No items"; an illustration with no action |
| **Error** | What failed, what is still available (cached data stays visible), and how to recover | Dead ends, raw error codes, wiping the screen |
| **Populated** | Realistic content at realistic lengths and counts | Only the ideal demo dataset |

There are three kinds of empty state, and each needs its own design: **first use** (teach and invite), **user cleared** (confirm and reassure: "All caught up"), and **no results** (say what was searched, then offer to broaden, fix, or clear filters).

Also design, where relevant: **partial** (some content loaded, some failed), **stale** (offline data, with its age shown), **refreshing**, **unavailable** (feature off, region-locked, plan limit), and **permission denied**.

## Loading and Waiting

- Acknowledge every tap immediately with a visual change (Doherty: about 400ms).
- To avoid flicker, delay showing a loader for about 150–300ms, and once shown, keep it visible for at least about 300–500ms.
- A button that triggers work keeps its label, shows progress inside or beside it, and blocks duplicate submits.
- **Optimistic updates** work when success is likely and the action is reversible (likes, toggles, reordering, sending a message). Show the result at once, reconcile in the background, and on failure roll back with an explanation and a retry. Never be optimistic about payments, bookings, or anything irreversible.
- Show progress for long work: determinate progress when it can be measured, otherwise named steps ("Uploading 3 of 12"). Let users leave and come back.
- Load progressively: show what is ready, then fill in the rest. Don't hold the whole screen back for its slowest part.

## Worst-Case Content

Design against plausible worst cases, not the demo dataset. Every value must be something a real user could produce, or the real limit of the field. Strings like "aaaaaaaa" prove nothing.

| Kind | Test values | What breaks |
| --- | --- | --- |
| **Names** | `Aleksandra Wiśniewska-Kowalczyk`, `Jo`, `J`, `María José de la Cruz y Fernández`, `王秀英`, `نور الهدى`, an emoji-first name, a missing name | Row overflow, initials logic, RTL alignment, clipped diacritics, empty fallback |
| **Identifiers** | A 60-character email, a long URL, a camera file name, a UUID | Unbreakable strings push siblings off-screen; end truncation hides what differs |
| **Labels from data** | A long job title, a translated status badge, a German compound (`Benachrichtigungseinstellungen`), 12 tags on one item | Badges squeeze names; tag rows wall up and need a `+8` overflow |
| **Numbers** | 0, 1, 1,284, 1,000,000, negative values, 142%, values that update live | Zero states, plurals ("1 items"), separators, badge width, out-of-range meters, digit jitter (use tabular figures) |
| **Money** | Large totals, two currencies, locales that use comma decimals | Overflowing totals, hard-coded separators |
| **Collections** | 0, 1, exactly a page, a page plus 1, thousands, one item 10× taller than the rest | One-card grids look broken, "Showing 40 of 40", performance, uneven rows |
| **Time** | Just now, 12 days ago, a future date, a date across time zones | "0 seconds ago", relative-time thresholds, wrong day |
| **Media** | Missing image, portrait in a landscape slot, a very large photo, a slow load | Empty frames, crops that cut the subject, layout shift |
| **Environment** | Largest text, RTL, dark mode, smallest width, landscape, keyboard open | Clipping, mirroring, contrast, reach |

Report what breaks and propose a fix for each. Some breaks are design decisions (truncate or wrap, middle- or end-truncate, hide or show a placeholder); name the choice.

## Input and Data Safety

- Preserve input through validation errors, failed submits, network loss, backgrounding, rotation, and back navigation. When leaving would discard work, ask, or save a draft automatically.
- Prevent double submission. Make retried operations safe to repeat.
- Long tasks survive interruption (calls, app switching, lock screen) and resume where they were.
- Destructive actions: prefer undo within a short window (a snackbar or toast with Undo) over confirmation dialogs. Confirm only what cannot be undone, and name the consequence in the dialog.

## Offline and Sync

- State the connection honestly but quietly: an inline banner or a status in context, never a blocking modal for a passing condition.
- Keep cached content readable, and show how old it is when that matters.
- Queue actions that are safe to defer, show them as pending, and sync when the connection returns. Surface conflicts with a clear choice.
- Disable only what truly needs the network, and say why when the user tries to use it.

## Risky Capabilities: Preflight

Run this only for features involving permissions, sensors, camera or media, background work, real-time or offline sync, payments, auth or sensitive data, or hardware-dependent behavior. Skip it for ordinary screens.

1. What user outcome requires the capability?
2. What happens if permission is declined, the device lacks support, the network drops, or the task is interrupted?
3. What data is collected, where is it kept, and for how long? What does the user see about that?
4. Does every target platform support the capability, and with what differences?
5. How will it be verified on real devices or representative simulators?

| Risk | Required design response |
| --- | --- |
| Permission or sensitive capability | Explain the value before the system prompt; design the decline path and a route back to settings; keep the app usable without it |
| Offline or unstable network | Preserve local work, show sync state, offer retry |
| Background or long-running work | Show status, explain battery and data impact where relevant, and define interruption behavior |
| Payments or sensitive data | Explicit confirmation, and never show pending as success |
| Platform divergence | Don't promise a capability one platform lacks; design the fallback |
| Performance-sensitive UI | Define the lowest target device and how responsiveness will be checked |

State the primary path, the fallback, user control, and the verification plan. Skip composite risk scores; they hide blockers.

## Harden Report

```markdown
## Hardening: <screen or flow>
**States** | state | present? | design / copy | way out |
**Worst cases** | value tested | what breaks | proposed fix (or decision needed) |
**Data safety** | scenario (error, back, background, double tap) | current behavior | required behavior |
**Risks** | capability | fallback | verification |
**Open decisions** | <truncate vs wrap, confirm vs undo, ...> |
```
