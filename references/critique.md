# Critique

Use for reviews, audits, and design feedback on screenshots, mockups, prototypes, code, or descriptions. A critique tells the owner what to fix first and why, with enough precision to act on it.

## Setup

Before judging, pin down:

- **Platform and form factor.** If the platform is unknown and it would change the verdict, ask. Otherwise review for both and say so.
- **Category, audience, and context of use.**
- **The artifact and its limits.** Say what it can and cannot show. A screenshot cannot prove contrast values or text scaling; a code fragment cannot show composition. A limit is not a finding: list it under verification instead.
- **The goal.** Full audit, a specific worry, a pre-ship check, or a direction for improvement.
- **The screen's thesis.** Its single job and the most characteristic thing about it. If the design gives no answer, that is a finding.

Pick the depth: **quick** (primary path, at most 5 findings, P0–P2 only) or **full** (the whole scope, at most 15 findings). Default to full unless the user asks for quick or the artifact is a single small component.

## Sequence

### 1. First impression

Form the gut reaction before analysing anything:

- "It communicates **___**." (competence, calm, playfulness, confusion)
- "The first three things my eye goes to: **1**, **2**, **3**." If these are not what the screen needs the user to see, the hierarchy is wrong.
- "In one word: **___**."

### 2. Specificity verdict

Does this feel authored for this product, or could an unrelated app use it unchanged? Name the category-interchangeable choices (`craft-floor.md` reflexes) and the missed opportunities for product character. A deliberately quiet utility can be the right answer; when it is, say so.

### 3. Five lenses, in order

Each lens carries a default severity. Raise or lower it with the evidence.

1. **Accessibility** (default P1; P0 if it blocks a task). Targets, contrast, text scaling, assistive-technology names and order, color-only meaning, gesture alternatives, Reduce Motion.
2. **Platform conventions** (default P1). Navigation model, back behavior, safe areas, system controls, modality, and platform tells (`platform-ios.md`, `platform-android.md`).
3. **Visual design and craft** (default P2). Hierarchy, type scale, spacing rhythm, color roles, depth, icon discipline, signature, reflexes, finish.
4. **Interaction and states** (default P2). Feedback timing, all states present, error recovery, data preservation, motion purpose and frequency.
5. **Content and writing** (default P2). Labels name actions, errors guide recovery, empty states invite action, and terms stay consistent (`ux-writing.md`).

Review the flow, not only the screen. A good screen can break the navigation around it.

### 4. Instruments

Use the ones the artifact supports:

- **Trunk test**, per screen. Dropped here with no context, can a user tell: which app this is, which screen, the main sections, their options here, where they are in the hierarchy, and how to search? 6/6 passes, 4–5 is partial, 3 or fewer is a P1 finding however polished it looks.
- **Five-second test.** Place, purpose, priority, next action, system state.
- **Cognitive load.** Single focus, chunking into groups of four or fewer, visible grouping, clear hierarchy, one decision at a time, at most four options per decision point, no memory bridges between screens, progressive disclosure. Two or three failures is moderate load; four or more is high.
- **Heuristics.** Score Nielsen's ten, 0–4 each: visibility of status, match with the real world, user control and freedom, consistency and standards, error prevention, recognition over recall, flexibility and efficiency, aesthetic and minimalist design, error recovery, help and documentation. Mark any heuristic the artifact cannot show as n/a with a reason, and total against the applicable maximum (for example /32). Most real apps score 20–32 out of 40. A 4 means genuinely excellent.
- **Goodwill across a flow.** Start at 70. Drains: information the user wants is hidden (−15); interstitials, forced tours, or splash delays (−15); format punishment, such as rejecting spaces in a card number (−10); unnecessary data requests (−10); sloppy appearance (−10); each ambiguous choice (−5). Fills: top tasks are obvious (+10); graceful error recovery (+10); upfront about costs and limits (+5); each saved step, default, or autofill (+5). Report the meter step by step. Below 30 is critical; above 60 is healthy.
- **Personas.** Walk the primary task as two or three of these, and report what broke for each, not generic profiles:
  - *Distracted one-hander*: thumb only, interrupted mid-flow, poor connection, returns later.
  - *First-timer*: reads labels literally, hesitates at unfamiliar icons, needs to know an action worked.
  - *Expert*: wants speed, skips onboarding, repeats the task many times a day.
  - *Assistive-tech user*: screen reader or switch access, largest text, Reduce Motion on.
  - *Stress tester*: long names, zero and thousands of items, offline, double taps, back mid-flow.
  - Add one persona from the product's real audience when it is known.
- **Emotional arc.** Where stress peaks, whether high-stakes moments get reassurance, and how the flow ends (`design-process.md`).

## Severity

| Level | Meaning | Test |
| --- | --- | --- |
| **P0** | Blocks the task, loses data or money, or locks out a group of users | Ship-stopper |
| **P1** | Causes real difficulty, confusion, or exclusion | Would a user contact support about it? Then it is at least P1 |
| **P2** | Annoyance or inconsistency, with a workaround | Fix in the next pass |
| **P3** | Polish with no real user impact | Fix if cheap |

## Report Format

```markdown
## Design critique: <screen or flow>

**First impression.** <communicates / first three / one word>
**Specificity.** <verdict in two or three sentences>
**Scope and coverage.** <depth, platforms, artifact limits; every lens marked reviewed, clear, or not reviewable and why>

### Findings
| Sev | Rule | Where | Problem → Fix | Why it matters |
| --- | --- | --- | --- | --- |
| P1 | MD-002 | Inbox row, swipe-to-delete | Delete exists only as a swipe → add Delete to the row's context menu and to edit mode | Users who don't discover the gesture, and switch-access users, can't delete |

### What works
<two or three specific strengths, and why they work>

### Scores (full depth)
<heuristics table with total and band; goodwill meter if a flow was walked; trunk test results>

### Considered and left alone
<one to five candidate findings that were rejected, and why>

### Verification
<what was checked and how; what could not be verified>

**Verdict:** Block · Needs changes · Ship
```

Rules for the report:

- Lead with the most severe findings. Merge a systemic issue into one row listing every location.
- Give each fix concrete values: the hex and ratio, the target size, the component that replaces the custom one, and the exact copy.
- Cite the source guideline when one applies (`source-map.md`). Otherwise label the point as judgment.
- Do not pad to the cap. A strong design gets a short critique and a clear statement of what makes it strong.
- Don't flatten personality. If the fixes would leave the design indistinguishable from a template, they went too far.
- Cut hedges such as "consider exploring". Say what to do.
- Verdict: **Block** if any P0 remains, **Needs changes** for P1–P2, **Ship** when only P3 or nothing remains. List unverified checks beside the verdict.
- When critiquing code, cite `file:line`. When critiquing images, cite the screen and element.

## Review Rule IDs

Use these stable IDs in the Rule column so findings can be tracked across reviews. Report only rules that apply. Never invent a finding to cover the list.

| ID | Rule |
| --- | --- |
| MD-001 | A control exposes an accessible name, role, and current state. |
| MD-002 | A gesture-only or touch-only action has a visible alternative. |
| MD-003 | Text, controls, system UI, and the keyboard never clip or hide the primary task. |
| MD-004 | Loading, empty, error, offline, and permission states exist and offer a way forward. |
| MD-005 | Destructive or irreversible actions are explicit and protected by undo or confirmation. |
| MD-006 | Back, dismiss, and navigation behave as the target platform expects. |
| MD-007 | Text scaling, contrast, dark mode, and color-independent status preserve meaning. |
| MD-008 | Motion has a purpose, fits its frequency, and has a Reduce Motion path. |
| MD-009 | Layout survives supported window sizes, orientation, and input methods. |
| MD-010 | Localized products handle long strings, locale formats, and RTL. |
| MD-011 | Components share consistent states, sizes, and semantics across the app. |
| MD-012 | Platform claims match current official guidance. |
| MD-013 | The design is specific to the product; no unexamined generated-UI reflexes. |
| MD-014 | Copy names actions and outcomes, and errors explain recovery. |
| MD-015 | No dark patterns, fabricated proof, or manipulative urgency. |
| MD-016 | Entered data and in-progress work survive errors, navigation, and interruption. |
