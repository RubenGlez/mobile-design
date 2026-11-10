# Principles and UX Laws

Use these as the reasoning layer behind decisions and critiques. A screen that breaks a principle has a bigger problem than any single guideline it breaks.

## Eight Principles

Apple restated its design principles in 2026. They apply to Android and to any app as well. Ask the question for each.

| Principle | Question |
| --- | --- |
| **Purpose** | What is this for, and does every element serve it? Deciding what not to build counts. |
| **Agency** | Can people explore, skip, choose their own path, and undo mistakes? Confirmation is only for truly destructive actions; overuse trains people to tap through. |
| **Responsibility** | Are permissions, data use, and consequences transparent and in the user's interest? Is misuse anticipated, especially in AI features? |
| **Familiarity** | Do patterns match the platform and stay consistent, so the same thing always looks and behaves the same? Break a familiar pattern only when you can show the new one is better. |
| **Flexibility** | Does it work across sizes, inputs, text sizes, languages, abilities, and situations? |
| **Simplicity** | Has every element earned its place? Simplicity is not minimalism: hiding everything in one menu looks minimal but isn't simple. Sometimes adding context simplifies. |
| **Craft** | Is every spacing, timing, and alignment value a choice you could defend? Jitter, misalignment, and broken rotation read as carelessness. |
| **Delight** | Is there a feeling here, and is it the right one? Delight comes from getting the other seven right, not from decoration added on top. |

## Feedback and Wayfinding

- **Four kinds of feedback**: status (what is happening), completion (it worked), warning (before a problem), error (what went wrong and how to recover). Every meaningful action produces one of them.
- **Wayfinding**: every screen answers *Where am I? Where can I go? What's here? How do I get out?* Never trap the user.
- **Mapping**: put controls near what they affect, arranged like the thing they change. If a control needs a label to explain what it controls, the mapping is weak.
- **Specific names**: name destinations by their contents ("Library", "Progress") rather than umbrellas ("Home", "Hub"). Specificity makes the app predictable.

## UX Laws as Tools

| Law | What it says | Mobile use |
| --- | --- | --- |
| **Fitts** | Time to hit a target depends on its distance and size | Large primary actions within thumb reach; small or distant targets only for rare or risky actions |
| **Hick** | Decision time grows with the number of choices | Fewer visible options; a sensible default; progressive disclosure |
| **Working memory (Cowan)** | People hold about four chunks at once | At most four options per decision point; group anything larger; never make users carry information between screens |
| **Jakob** | People expect your app to work like the others they use | Platform patterns for navigation, controls, and gestures |
| **Doherty** | Responses under about 400ms keep people in flow | Acknowledge every tap immediately; show progress, or optimistic results, when work takes longer |
| **Tesler** | Complexity is conserved; someone has to carry it | Move complexity into the system (smart defaults, autofill, inference), not onto the user |
| **Peak-end** | Experiences are remembered by their peak and their end | Design one peak and the ending of core flows deliberately |
| **Zeigarnik** | Unfinished tasks stay on people's minds | Visible progress and resumable drafts; never use it to nag |
| **Serial position** | First and last items are remembered best | Put the most important tab, option, or message at the start or the end |
| **Aesthetic-usability** | Attractive interfaces are perceived as easier | Craft earns patience, but it never fixes a broken flow; test the task itself |
| **Postel** | Be liberal in what you accept | Accept any reasonable input format (spaces in card numbers, pasted codes) and normalize it |

## Progressive Disclosure

Show the common path first. Put advanced options one level deeper, behind a clearly labeled control. Reveal complexity when the user's action calls for it, and keep the disclosure state when they come back.
