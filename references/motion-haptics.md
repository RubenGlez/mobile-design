# Motion and Haptics

Use for transitions, micro-interactions, gestures, springs, loading motion, haptics, and reduced motion. Motion is part of the design from the start. Specify it as behavior (what moves, why, how it responds to the finger, how it settles) so any implementation can match it.

## Purpose First

Every animation does at least one job. If you can't name it, remove the animation.

- **Feedback**: confirms that an input was received.
- **Orientation**: shows where something came from or went (continuity between screens and states).
- **Hierarchy**: explains what changed and what matters now.
- **Status**: shows progress or waiting.
- **Character**: expresses the brand at a rare, earned moment.

The best motion in a working app goes unnoticed. If people remark on an animation every time they see it, it is too prominent for something they repeat.

## Frequency Gate

Before adding or approving motion, ask how often the user triggers it:

| Frequency | Motion |
| --- | --- |
| Rare (first run, milestones, monthly) | Expressive motion is welcome |
| Occasional (a few times a day) | Subtle and fast |
| Frequent (dozens to hundreds of times a day) | Instant, or a near-instant change of color or opacity |
| Keyboard- or shortcut-initiated | None |

Weigh the gate by context. A kids' or creative app can afford more expressive motion than a banking or productivity tool. Match the conventions the app already has, unless they are the problem.

## Timing and Easing

- Feedback on press appears immediately, within about 100ms, on touch-down, not on release.
- Typical durations: micro-feedback 100–200ms; component transitions (menus, sheets, expanding rows) 200–350ms; screen transitions follow the platform. Larger distances and larger elements take longer; small elements move faster.
- Entering elements decelerate (ease-out). Exits are quicker and subtler than entries, because the user's attention has already moved on. Avoid linear motion for anything that moves through space.
- Never start a scale from zero. Begin from about 0.9 or higher, combined with opacity.
- Anchor motion to its source: menus and popovers grow from the control that opened them, and things leave the way they came.
- Use one orchestrated moment at most per screen, on first arrival or after a meaningful change. Don't add entrance motion to repeat visits.

## Fluid Interaction

These principles separate fluid from merely animated:

- **Interruptible.** Any animation can be grabbed, reversed, or redirected mid-flight. Never lock input during a transition. The new motion starts from the element's current on-screen position, never from where it was supposed to end.
- **Springs over fixed durations** for anything the user touches. Describe a spring by its **damping ratio** (1.0 = no overshoot, below 1.0 = bounce) and its **response** (how quickly it settles, in seconds). These map to any spring implementation.

| Interaction | Damping | Response |
| --- | --- | --- |
| Default UI movement, repositioning | 1.0 | 0.3–0.4 |
| Sheet or drawer released by a drag | ~0.8–0.9 | 0.3 |
| A flicked or thrown object | ~0.7–0.8 | 0.3–0.4 |
| Toggles, menus, dialogs, utility actions | 1.0 | 0.25–0.35 |

- **Bounce only after momentum.** A slight overshoot is right when the user flicked something. The same element opened by a tap gets no bounce, because no force was applied.
- **Continuous feedback.** During a drag, the UI follows the finger 1:1 the whole way, keeping the offset from where it was grabbed. Never animate only at the end.

## Gestures

Every gesture has two phases:

1. **Tracking** (finger down): position maps directly to the finger. No easing, no delay. At boundaries, resist progressively (rubber-banding) instead of stopping dead.
2. **Release** (finger up): physics finishes the motion. The settle animation starts at the finger's release velocity, so there is no seam between dragging and animating.

Rules:

- Choose the destination from where the gesture is heading, not only from where it was released. A flick projects forward to the nearest snap point.
- Dismiss or commit on distance **or** velocity: past roughly half the travel, or a quick flick over a short distance. Snap back quickly when neither threshold is met.
- Require a small movement threshold (about 10pt) before committing to a direction, then track 1:1. Recognize competing gestures in parallel and settle on one as soon as intent is clear.
- Values that depend on the gesture (the dimming behind a sheet, the scale of the page beneath) derive from the gesture's progress, so they stay in sync when the user reverses.
- Never conflict with system gestures: edge-swipe back, the home indicator, and the notification and control areas.
- Every gesture-driven action also exists as a visible control.

## Loading Motion

- Skeletons match the final layout. Keep the shimmer slow and subtle, or replace it with a static placeholder under Reduce Motion.
- Don't let dozens of placeholders loop independently. Use one coordinated, calm treatment.
- Progress indicators should feel steady. Don't animate fake progress that stalls at 99%.

## Haptics

Haptics are part of the feedback system. They are not decoration.

- **Causality**: fire on the actual causal event (the toggle flipping, the item snapping into place, the payment confirming), and match the haptic's character to the physicality of the action.
- **Harmony**: the visual, the sound, and the haptic land on the same frame. Any lag between them breaks the illusion.
- **Utility**: reserve haptics for meaningful moments: success, warning, error, a commit, a snap to a detent, selection changes in pickers. Too much feedback trains users to ignore all of it.

Use the platform's semantic haptic types (selection, impact, notification success/warning/error) rather than raw vibration patterns. Never fire haptics on passive scrolling, background updates, or every frame of a gesture. Haptics never replace visual feedback, and they respect the system setting that turns them off.

## Reduced Motion and Related Settings

Reduced motion means a gentler equivalent, not removing feedback:

- **Reduce Motion**: replace slides, zooms, parallax, and springs with short cross-fades or instant changes. Remove overshoot and looping motion. Keep the color and opacity changes that help comprehension.
- **Reduce Transparency**: make translucent surfaces opaque.
- **Increase Contrast**: strengthen borders, separators, and text.
- Avoid large moving backgrounds, slow full-screen oscillations, and abrupt flashes of brightness for everyone, not only users with these settings on.
- Anything that moves for more than about 5 seconds alongside other content can be paused.

## Motion Spec Format

Specify motion so any implementation can reproduce it:

`<element> · trigger · property changes · spring (damping / response) or duration + easing · interruptible? · reduced-motion alternative · haptic`

Example: `Sheet · drag release past 50% or flick > ~800pt/s · y → closed, scrim 40% → 0 tied to progress · spring 0.85 / 0.3 seeded with release velocity · interruptible · Reduce Motion: 200ms fade · none`

## Motion Checklist

- Every animation has a named purpose and passes the frequency gate.
- Press feedback appears immediately on touch-down.
- Animations can be interrupted, and gestures hand off velocity.
- Exits are subtler than entries, and motion grows from its source.
- No pulsing indicators, no stagger on every list, no bounce on utility actions.
- A Reduce Motion path exists for every animation, and Reduce Transparency has an opaque fallback.
- Haptics are causal, in sync with the visuals, and rare.
