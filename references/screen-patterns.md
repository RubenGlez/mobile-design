# Screen Patterns

Use when the task is a whole screen, flow, or redesign. These are structures to think with, not finished styles. Every pattern still gets a signature, all its states, and the craft floor.

## Universal Anatomy

Every screen answers: where am I, what matters most, what can I do next, and what state is the system in?

1. A container that respects the safe areas, with its background.
2. A title or navigation bar, only when it helps orientation.
3. The primary content, with the signature object first.
4. A reachable primary action when the screen has a linear job.
5. Secondary actions placed by priority and risk.
6. State surfaces: loading, empty, error, offline, permission (`states-edge-cases.md`).

## List or Feed

For inboxes, products, transactions, tasks, workouts, chats, and search results.

- A title and at most one high-value action in the header, not a toolbar full of icons.
- Add search and filters when the list is long enough to need them, and keep active filters visible.
- Rows have a stable hierarchy: the primary identifier, the key metadata, then status or action. The value the user scans for (amount, time, status) gets the strongest treatment, never weaker than its label.
- Operational lists use separators and compact rows. Discovery lists are image-led, with one featured item allowed to break the rhythm.
- Pull to refresh for remote content that changes. Swipe actions also exist as visible controls.
- Empty: the first-use invitation. Error: retry, with cached rows kept.

## Detail

For products, profiles, articles, bookings, transactions, recipes, and media.

- The entity is unmistakable in the first view: its image, name, status, and key number.
- Context metadata sits under the identity. The primary action is in the thumb zone if the screen is action-oriented. Secondary actions are grouped and quieter.
- Use a sticky action bar only when users need the action after scrolling.
- Commerce: inspect the product (zoom, variants), price, availability, delivery, and returns confidence. Transactions: amount, counterparty, date, status, and a path to dispute or get help. Profiles: identity, relationship state, privacy controls.
- Loading keeps the detail layout's shape, so content doesn't jump.

## Home

For apps checked repeatedly: finance, health, productivity, fitness.

- Lead with the signature object or the most important status or next action, not a greeting above equal stat cards.
- Order the following modules by frequency and urgency, and show what changed since the last visit.
- Metrics carry labels, units, and context (compared with what). Show a trend only when it is measured.
- Alerts interrupt only when action is needed. Empty modules explain setup, or collapse.
- Personalize by user stage: guided and minimal for new users, routine-focused for returning users, denser stats and shortcuts for experts.

## Search

- Before typing: recent searches, suggestions, and categories. Never a blank screen.
- While typing: fast suggestions with the matched text highlighted.
- Results: grouped by type when that helps, with filters visible and resettable.
- No results: echo the query, suggest fixes, and offer to broaden it.

## Status Tracking

For orders, deliveries, rides, applications, and support cases.

- Open with a confident status sentence ("Arriving by 6:40 pm").
- Show a visual timeline of the steps with the current one emphasized, not a list of dates.
- Humanize it where real data exists: courier name, photo, contact actions.
- Live updates show up in place. Consider a Live Activity or a widget for time-bound tasks (`platform-ios.md`, `platform-android.md`).

## Form, Creation, or Checkout

Use with `forms.md`.

- A title that names the task, and fields grouped by mental model.
- Keyboard-aware layout, a reachable primary action that shows its state, and drafts preserved.
- Short forms fit on one screen. Long ones split into steps with visible progress and a way back.
- Irreversible or paid actions get a review step with the full cost.

## Settings

- Grouped lists by topic, with the most used first. Search when there are many settings.
- Toggles take effect immediately. Changes with consequences explain them inline.
- Privacy and permission settings link to the system settings rather than duplicating them.
- Destructive account actions sit at the end, separated, explicit, and confirmed.

## Onboarding

Use onboarding only when it prevents later confusion or collects setup the product truly needs.

- Prefer **task-first** entry: start the core action and explain in context.
- Other options: a single setup screen (a goal, a preference), a preview of a realistic finished state, or a guided checklist for genuinely multi-step tools.
- Three screens or fewer unless onboarding is the product. Every step can be skipped unless it is required. Defer sign-in until the user needs an account-only feature.
- Ask for permissions at the moment of value, not in a row at launch.
- Primary actions are concrete: "Set a running goal", "Import contacts".
- The app must work well for users who skipped onboarding, through good empty states.

## Paywall

- Show what the user gets in concrete terms, the price per period, trial terms with the end date, and what the free tier keeps.
- The close or "continue free" control is visible from the first frame.
- Plans can be compared directly, and Restore purchases is easy to find. See `trust-ethics.md` for patterns to never use.

## Screen Verification

- Smallest and largest phone widths, plus tablet if supported.
- The largest text size and dark mode.
- Every state: empty, loading, error, offline, permission denied.
- Keyboard open on input screens.
- Back and dismiss behavior.
- Screen reader order through the primary task.
