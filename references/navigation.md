# Navigation

Use for information architecture, tabs, stacks, sheets, modals, menus, back behavior, state restoration, and entry points such as deep links and notifications.

Navigation answers four questions on every screen: where am I, what's here, where can I go, and how do I get back? If a user dropped onto any screen can't answer them, the structure is failing (see the trunk test in `critique.md`).

## Structure First

Before choosing components, map the information architecture:

- List the top-level destinations by frequency of use, not by org chart or backend model.
- Name each destination after its contents ("Trips", "Library", "Activity"), not an umbrella ("Home", "Hub", "Dashboard") unless that is genuinely what it holds.
- Keep the hierarchy shallow. Two or three levels below a tab is usually the most users can track.
- Find the entry points that skip the hierarchy: notifications, widgets, links, search, shortcuts. Each must land on a screen that makes sense on its own.

## Pattern Selection

| Pattern | Use for | Cautions |
| --- | --- | --- |
| Tab bar / navigation bar | 2–5 peer top-level sections used often | Tabs are sections, never actions or workflow steps. Labels stay visible. |
| Push (stack) | Drill-down: list to detail, settings to subsetting | Back always returns to the previous context, with its scroll and state |
| Sheet | A focused, self-contained subtask that relates to the screen beneath it | Not for primary navigation; give it a visible dismiss path and a drag handle when it can be swiped away |
| Full-screen modal | Immersive or high-commitment tasks: compose, camera, checkout, sign-in | Clear Cancel and Done; confirm before discarding work |
| Menu / overflow | Secondary or rare actions | Not a hiding place for primary actions |
| Drawer | Many secondary destinations on large screens or in admin tools | Rarely the right primary navigation on a phone |
| Navigation rail / sidebar | Medium and expanded windows (tablets, foldables, desktop-class) | Switch from the phone tab bar by window size, not by device name |
| List-detail / split view | Browsing collections on wide windows | Needs a single-pane fallback at compact width |
| Search-first | Large catalogs where users know what they want | Never a blank screen: show recent searches, suggestions, and categories |

## Tabs

- Each tab keeps its own navigation history and scroll position. Switching tabs never resets them.
- Tapping the active tab returns to its root, or scrolls to the top when already at the root.
- The tab bar stays visible throughout the hierarchy inside a tab. Hide it only for immersive or modal tasks.
- A badge means "something here needs you". Use one only when it leads to an action, and clear it when the user has seen it.
- Order tabs by importance; the first and last positions are remembered best.

## Back and Dismiss

- Back returns to the previous context exactly: the same scroll position, selection, filters, and drafts.
- Preserve the iOS edge-swipe back, and the Android system back and predictive back. Never disable or overlay them.
- Swipe-to-dismiss on sheets stays enabled unless dismissing would lose work. In that case, ask before discarding, and offer to save a draft.
- Interrupting back is acceptable only to protect unsaved work, and it should ask, not block.
- Never trap the user. Every modal, sheet, and flow has an obvious exit.

## Modality

A modal is the last answer, after inline editing, disclosure, and a pushed screen. Use modality when the task is self-contained, benefits from focused attention, and can be cancelled as a unit.

- Never stack modals on modals. Navigate inside a single modal instead.
- Alerts and dialogs are only for information that must interrupt: destructive confirmations, critical failures, required decisions. Use inline messages, banners, or snackbars for everything else.
- Name dialog buttons with verbs ("Delete draft", "Keep editing").

## Entry Points and State Restoration

Treat these as design requirements, not engineering details:

- A link or notification opens the exact content it refers to, with a sensible back path (to the parent list, not to nothing), from both a cold start and a running app.
- If sign-in or a permission interrupts an entry point, the user lands on the intended destination afterwards.
- After the app is backgrounded or killed, users come back to where they were: the screen, scroll position, drafts, and in-progress steps.
- Shareable things have shareable addresses.

## Navigation Checklist

- The current location is obvious within five seconds on every screen.
- Back works everywhere and restores context.
- Tab labels and titles survive large text and translation.
- Navigation adapts by window size: bar on compact, rail or sidebar on wider windows.
- Links and notifications land correctly from cold and warm starts.
- Sheet and modal dismissal is visible, and work is protected.
