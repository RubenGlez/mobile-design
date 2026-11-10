# Modes: Shape and Refine

Playbooks for the modes that do not have a reference of their own. Design mode follows the operating loop in `SKILL.md`. Critique, Harden, and Adapt live in `critique.md`, `states-edge-cases.md`, and `adaptivity-localization.md`.

## Shape

Use when the brief is sparse, the problem is unclear, or the user asks to plan before designing. Shape ends with a confirmed brief and produces no visual design.

### Discovery

Ask one round of two or three questions, the ones that most change the result. Assert the likely answer in each so the user can just confirm. Add a second round only when the answers expose a real gap. Never send a questionnaire, and never ask about values the designer should decide (hex codes, spacing).

Round 1, purpose and people:

- What is this for, and what problem must it solve?
- Who reaches it, in what situation and state of mind? (one-handed on a commute, anxious before a payment, expert on the hundredth use)
- What must they understand or do, and what does success look like?
- What is true here that a neighboring product could not claim?

Round 2, only if needed:

- What real content, data, and assets exist? What are the realistic minimum, typical, and maximum values?
- Which states matter: first run, empty, loading, error, offline, permission denied, expert use?
- What must not change? What would feel wrong even if it looked polished?
- Which platforms, window sizes, locales, and accessibility needs are binding?

If no one can answer (a headless run), state the assumptions and continue.

### The brief

Write the smallest brief that settles the decisions. Use three to five bullets when the task is clear, and the full structure only for ambiguous or multi-screen work.

1. **Job and audience**: who arrives, in what context, needing what.
2. **Outcome**: the primary action, what success looks like, the product-specific truth to show.
3. **Direction**: design read, dials, signature, and what the screen will be remembered by.
4. **Scope**: fidelity, screens or flow covered, what stays untouched, anti-goals.
5. **States and ranges**: content ranges, required states, edge cases.
6. **Constraints and open decisions**: platforms, accessibility, localization, existing system, and choices a builder must not invent.

Present it for confirmation, then stop.

## Refine

Refinement works inside the existing identity. Before changing anything, identify the current system: its tokens, components, radius, type, and motion. Fix inconsistencies toward that system, not toward personal taste. Name the sub-mode, then follow it.

### Polish

The final pass before shipping. Work the whole path, not one screen.

1. **Establish the system.** Note the existing tokens and patterns. Every value changed in polish must land on that system.
2. **Gather evidence.** Walk the primary flow and every state: pressed, focused, disabled, loading, empty, error, success, offline. Check large text, dark mode, the smallest width, and RTL if supported.
3. **Triage.** Floor violations first, then reflexes, then finish checks (`craft-floor.md`).
4. **Polish the path:**
   - Flow and hierarchy: the primary action is obvious, reachable, and consistently named.
   - Layout and type: alignment is deliberate, spacing rhythm is consistent, and the type scale has clear steps.
   - Color, imagery, icons: one icon family and stroke, accent used only for action, selection, and state.
   - Interaction and state: feedback within about 100ms of touch, and transitions that explain what changed.
   - Content: real copy and verbs that match the action (`ux-writing.md`).
5. **Verify and finish.** Re-walk the path. List what changed, and what was considered and left alone.

### Bolder

Use when a design is safe to the point of anonymity, and only where the context allows (see the dials).

- Find the signature first: the product's strongest real thing. Make it larger, give it more space, and put it earlier.
- Amplify one axis at a time: scale contrast in type, a committed color field, a distinctive shape language, or a characteristic motion moment.
- Keep navigation and controls familiar. Boldness belongs in content and identity, not in reinvented controls.
- Stop when one element is unmistakable. Two competing bold moves cancel out.

### Quieter

Use when a design is loud, busy, or tiring.

- Remove decoration that carries no information: gradients, glows, borders that only fake depth, repeated badges, ornamental icons.
- Reduce accent usage to action, selection, and state.
- Cut motion on frequent interactions to instant or near-instant.
- Lower the number of type sizes and weights, and replace boxes with spacing and alignment.
- Keep the signature. Quieter does not mean anonymous.

### Distill

Use when a screen does too much.

- Name the screen's single job. Everything that does not serve it moves deeper, collapses, or goes.
- Count the options at each decision point. Above four, group them, disclose them progressively, or choose a default (`principles.md`, working memory).
- Merge duplicate paths to the same outcome.
- Prefer adding context over adding controls: a scrubber that shows time remaining beats a separate remaining-time label.
- Show the common path first and put advanced options one level deeper.
