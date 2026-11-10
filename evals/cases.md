# Mobile Design Evaluation Cases

Forward-test a revision before release. Give the agent only the prompt and any named artifact. Score the output against the passing signals and the failure signals.

## Protocol

1. **Baseline.** Run each case once without the skill and once with it, on the same model. A case passes only if the skill run shows the signals and is clearly better than the baseline. A skill that doesn't beat the baseline isn't earning its tokens.
2. **Judge.** Score each run from 1 to 5 on six axes:
   - *Specificity*: authored for this product, or interchangeable.
   - *Hierarchy*: the first three things the eye lands on are the right ones.
   - *Completeness*: states, edge cases, accessibility, platforms.
   - *Restraint*: boldness spent once; no reflexes.
   - *Correctness*: no false platform claims, no framework APIs presented as design.
   - *Actionability*: numbers, exact copy, and specs a builder can follow.
3. **Record** the prompt, the output, the artifacts inspected, any verification, the signals missed, and the scores for both runs.

Global failure signals (any one fails the case): a library or framework API prescribed without being in the user's project; invented metrics, testimonials, or logos; a Floor violation in the delivered design; a pending state shown as success; a dark pattern proposed.

## Cases

| # | Mode | Prompt | Passing signals |
| --- | --- | --- | --- |
| 01 | Design | Redesign a banking transfer confirmation for iOS and Android. | Exact amount, recipient, fees, and timing; a protected final action that names the amount; restrained motion; pending vs. done states; a platform divergence table. |
| 02 | Design | Design a sign-up form with email, phone, and password. | Input intent per field (keyboards, autofill, password manager); a visible Continue for the phone pad; validation on blur; submit stays enabled and points to the first error; input preserved on failure. |
| 03 | Critique | Review a feed screen with tiny icon actions and swipe-only delete. (Provide a description or screenshot.) | First impression; target-size and gesture-alternative findings with MD IDs and P-levels; concrete fixes with sizes; a verdict. |
| 04 | Design | Design a fitness dashboard for outdoor runners. | Glare-safe contrast figures; glanceable large metrics; the signature object first (not a greeting above stat cards); bottom-reachable actions. |
| 05 | Adapt | Adapt a message list from phone to tablet and foldable. | Window-first restructure (rail plus list-detail); hinge avoidance; state preserved across size changes; no stretched phone layout. |
| 06 | Design | Specify an animated favorite button. | Named purpose; the frequency gate applied (fast, subtle); touch-down feedback; no bounce for a tap; a Reduce Motion path; a haptic on commit only; accessible toggle state. |
| 07 | Adapt | Localize a commerce checkout to Arabic and German. | RTL mirroring with the exceptions named; room for long strings; locale formats for money and dates; no concatenated sentences. |
| 08 | Harden | Harden a team-members list (names, emails, roles, invite status). | A worst-case table with plausible values (long, short, CJK, RTL, missing); plurals; zero, one, and thousands; four data states with copy; decisions named (truncate vs. wrap). |
| 09 | Design | Design permission onboarding for location and notifications. | Value before the system prompt, asked at first use; a skip path; a designed denied state; the app still usable; honest copy. |
| 10 | Design | Design a reusable destructive-action pattern. | Prefers undo; confirmation only when irreversible, naming the consequence; dialog buttons as verbs; semantic states; accessible names. |
| 11 | Critique | Review a modal checkout that loses the draft on swipe-down. | Finds data loss (MD-016, P0/P1); dismiss protection; recovery; goodwill drains named. |
| 12 | Adapt | Redesign a dense support tool for tablet with keyboard and pointer. | Focus order; shortcuts; compact density without breaking targets; hover never the only affordance. |
| 13 | Harden | Design background location tracking with an offline route log for a cycling safety feature. | Runs the preflight; consent and battery explained; offline queue and sync state; fallback when declined; verification plan. |
| 14 | Design | Redesign a failed payment screen for a medical booking app. | The booking preserved; the cause and recovery in the error-copy pattern; escalation path; no false success; no fake urgency. |
| 15 | Design | "I'm building the settings screen in SwiftUI; design it." | Design specs (grouped list, roles, states, copy) in platform-neutral terms; may use the user's own stack vocabulary, but doesn't invent APIs or prescribe libraries. |
| 16 | Refine | "This home screen looks generic. Make it feel like ours." (A meal-planning app; provide a greeting-plus-cards screen.) | Specificity verdict; names the reflexes; finds a signature from the product's material (the week's plan); the mirror test stated; navigation and controls stay familiar. |
| 17 | Shape | "Design an app for my bakery." | Asks once (at most three questions, each with an assumed answer) or infers and states it; produces a brief, not a visual; covers the material inventory (no invented reviews). |
| 18 | Design | Write all the copy for a file-upload flow: idle, uploading, success, three failure types, empty library. | Verb+object buttons; error pattern with cause and recovery; in-progress ellipsis; three empty-state types; no hype words or "Oops". |
| 19 | Design | Design a subscription paywall with a 7-day trial; the client wants the "maximum conversion" version. | Trial end date and price stated; visible close; comparable plans; refuses confirmshaming, preselection, and fake urgency, and offers honest persuasion instead. |
| 20 | Critique | Full critique of a three-screen onboarding flow (provide screenshots or descriptions). | Trunk test per screen; Nielsen scores with an applicable maximum; the goodwill meter across the flow; personas, including the distracted one-hander; considered-and-left-alone; a verdict. |
| 21 | Adapt | Port an iOS-designed bottom-tab app to Android. | The translation table applied (navigation bar or rail, predictive back, FAB only if there is a single primary action, snackbar); names the "iOS wearing Android's skin" tells; the brand carried through color roles. |
| 22 | Design | Specify a draggable bottom sheet with three detents for a map app. | Track and release phases; velocity handoff; projection to the nearest detent; dismiss on distance or velocity; scrim linked to progress; no conflict with system gestures; reduced-motion path; motion spec format. |

## Regression Notes

Rerun 03, 08, 16, and 19 on every release. They protect the skill's most distinctive behavior: critique structure, worst-case hardening, specificity, and ethics.
