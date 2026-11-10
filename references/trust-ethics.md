# Trust and Ethics

Use for money, health, privacy, permissions, subscriptions, social safety, persuasion, and any flow where the design could work against the user.

## High-Stakes Moments

For each high-value moment, define the trigger, the visible state change, the feedback, and the recovery or next step. Lower visual variance and motion in risky or irreversible flows instead of trying to make them exciting.

| Moment | Design for | Avoid |
| --- | --- | --- |
| Payment or transfer confirmation | Confidence and control: exact amount, recipient, fees, timing, and a protected final action | Ambiguous labels, fees revealed late, celebration before completion |
| Health result or reminder | Reassurance and agency: what it means, what to do, when to escalate | Alarming color or copy without an action |
| Permission request | Informed consent: value first, a real decline path | A cold system prompt at launch; punishing a decline |
| Checkout or booking failure | Recovery: the cart or booking kept, the cause, a retry or an alternative | Dead ends, lost data, blame |
| Onboarding completion | Momentum: the next useful action | Blocking celebration, a vague "You're all set" |
| Social, safety, or privacy action | Ownership: who sees it, how to undo it, how to report | Invisible audience, moderation, or undo state |
| Cancellation or account deletion | Respect: as easy as signing up, with the consequences stated | Obstruction, guilt, hidden steps |

## Privacy and Permissions

- Ask only for what the feature needs, at the moment of need, after explaining the value in the app's own UI. State the cost in that same moment, before the system prompt: background location, continuous sensors, or uploads should say what they mean for battery and data.
- Prefer the least invasive option the platform offers: a one-time or approximate location, a limited photo selection, a system picker instead of full library access.
- Design the declined state as a first-class state: what still works, what doesn't, and how to enable it later through Settings.
- Don't require an account until the user needs an account-only feature. Offer the platform's privacy-preserving sign-in options where they exist.
- Show what is shared and with whom, at the point of sharing.

## Persuasion Without Manipulation

Persuasion is legitimate when it helps users decide in their own interest with true information. It becomes manipulation when it relies on deception, pressure, or hidden consequences.

Do not:

- Manufacture urgency or scarcity. Timers and "only 2 left" messages must reflect real constraints.
- Use variable rewards, streak anxiety, or notification nagging to drive engagement for its own sake.
- Hide the cost, the renewal, or the consequence of an action.
- Make the option the business prefers visually louder while the user's likely choice looks disabled or hidden.

## Deceptive Pattern Catalog

Never design these. In Critique, flag them under MD-015 with confidence *likely* (the design or copy directly shows it) or *possible* (the cues are there but behavior can't be confirmed). Don't claim intent or legality. Each one has an honest alternative.

| Pattern | What it looks like | Honest alternative |
| --- | --- | --- |
| **Confirmshaming** | "No thanks, I don't like saving money" | A neutral decline: "Not now" |
| **Fake urgency** | Countdown timers that reset; "offer ends soon" with no end | Real deadlines only, with the date stated |
| **Fake scarcity** | "Only 2 left!" not backed by real inventory | Real stock levels, or nothing |
| **Fake social proof** | Invented reviews, ratings, activity ("12 people viewing") | Real, attributable reviews and counts |
| **Preselection** | Add-ons, insurance, or marketing consent checked by default | Unchecked by default; the user opts in |
| **Sneaking** | Items or fees added to the cart without the user choosing them | Only what the user chose |
| **Hidden costs** | Fees appear at the last step | The full price from the first price shown |
| **Hidden subscription** | A trial that converts to paid without clear disclosure or a reminder | The renewal date and price shown up front, with a reminder before charging |
| **Hard to cancel** | Cancellation buried, routed through calls or chat, or a maze of retention screens | Cancel in as few steps as signing up; one retention offer at most |
| **Obstruction** | Extra steps added only to the path the business disfavors | Equal effort for equivalent choices |
| **Forced action** | Requiring contacts, an account, or sharing to continue an unrelated task | Ask only for what the task needs |
| **Nagging** | Repeated prompts after "no" (ratings, notifications, upgrades) | Respect "no"; ask again only after a meaningful change, at most rarely |
| **Trick wording** | Double negatives, confusing opt-outs ("Uncheck to not receive…") | Plain, positive phrasing; one meaning |
| **Visual interference** | Low-contrast decline buttons, a disguised close control, key terms in tiny grey text | Equal visual weight for equivalent choices; legible terms |
| **Disguised ads** | Ads styled like content or native UI | Clearly labeled sponsored content |
| **Comparison prevention** | Plans that can't be compared (different units, hidden features) | One comparison table with the same rows for every plan |

## Paywalls and Subscriptions

- Show the price per billing period, the renewal terms, the trial length and end date, and what the free tier keeps.
- Make the close or "Continue with free" control visible and legible from the first frame.
- Plan picker: a recommended plan may carry an honest label ("Best value", computed from the real prices), but no plan is preselected. The user taps a plan, and then the primary button states exactly what will be charged and when ("Start free trial, then $59.99/year on Mar 12"). Never preselect add-ons.
- Label the plan the business recommends honestly, and keep the other options equally readable.
- Restore purchases is easy to find.
