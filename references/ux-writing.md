# UX Writing

Use for any interface copy: labels, buttons, titles, errors, empty states, confirmations, notifications, permission prompts, onboarding. Words are design material. They exist to make the interface easier to understand and use.

## Standards

Every string is, in this order of editing:

1. **Purposeful**: it helps the user act or understand. If it does neither, delete it.
2. **Concise**: the fewest words that keep the meaning. Front-load the important part.
3. **Conversational**: plain verbs, articles kept, active voice, the way a helpful person would say it.
4. **Clear**: specific, unambiguous, and consistent with the rest of the app.

Write from the user's side. Name things by what users understand, not by how the system is built: "Notifications", not "push config". Use one term per concept across the whole app. An action keeps its name through the flow: the button says "Publish", the confirmation says "Published".

## Patterns

| Element | Pattern | Examples |
| --- | --- | --- |
| Screen titles | Noun phrase, sentence case, names the content | "Payment methods", "Your library" |
| Buttons and actions | Verb + object; names what happens | "Pay $42.18", "Save address", "Send invite" |
| Menu items that open more input | End with an ellipsis | "Rename…", "Move to…" |
| In-progress states | Present participle + ellipsis | "Saving…", "Uploading 3 of 12…" |
| Success | Past tense, specific, brief | "Address saved", "Invite sent to Dana" |
| Field labels | Noun phrase, always visible | "Email address", "Card number" |
| Placeholders | An example of the format, never the label | "name@example.com" |
| Helper text | Why the field is needed, or its format | "We send receipts here" |

Avoid "OK", "Submit", "Yes/No", and "Click here". Dialog buttons repeat the verb: "Delete draft" and "Keep editing", not "Yes" and "Cancel".

## Errors

An error says what happened, why if known, and what to do now. It never blames the user, never apologizes at length, and is never vague.

| Type | Pattern | Example |
| --- | --- | --- |
| Inline validation (on blur or after first submit) | [Field] + requirement | "Use at least 8 characters" |
| System failure | [What failed]. [Likely cause]. [Recovery]. | "Couldn't save changes. You're offline. We'll retry when you reconnect." |
| Blocking | [What's blocked]. [Why]. [Action]. | "Update required. This version no longer syncs. Update to continue." |
| Payment | [Outcome]. [Cause]. [Next step]. | "Payment declined. Your bank didn't approve it. Try another card." |
| Permission denied | [What's unavailable] + [how to enable] | "Location is off, so nearby stores can't be shown. Turn it on in Settings." |

Avoid raw codes ("Error 403") unless support needs them, and then only as secondary text. Avoid blame words ("invalid", "illegal", "you failed"), "Oops", and "Something went wrong" when the cause is known. When the system is at fault, own it.

## Empty States

Explain what belongs here and offer the one action that fills it.

- **First use**: "No trips yet. Plan your first route and it will appear here." → [Plan a route]
- **User cleared**: "All caught up." No action needed; a quiet sense of completion.
- **No results**: "No results for 'blu jeans'." → suggestions, a spelling fix, or [Clear filters]

## Permissions and Notifications

- **Pre-permission context**, before the system prompt: [the benefit to the user] + [what's needed]. "Get alerts when your order ships. Allow notifications?" Ask when the feature is first used, not at launch.
- **Notifications**: lead with the change itself, and make it specific and actionable: "Dana accepted your invite", not "You have a new update". Group and categorize them so users can control them.

## Voice and Tone

**Voice** is constant: three adjectives that describe the product's personality, plus the words it uses and avoids. Keep them in `DESIGN.md`. **Tone** shifts with the moment:

| Moment | Tone |
| --- | --- |
| Loading | Present and calm: "Getting your statements" |
| Empty | Inviting: what belongs here |
| User error | Clear and directive, without blame; one specific next step |
| System error | Owns the problem, gives a path forward |
| Success | Warm and brief; acknowledge, don't gush |
| Money, health, safety | Precise and neutral; no jokes, no exclamation marks |
| Onboarding | Contextual: what they can do now, not how the app works |

Humor is fine only where the stakes are low and it never delays the task.

## Length Benchmarks

| Element | Target |
| --- | --- |
| Buttons | 1–4 words (25 characters at most before translation) |
| Titles | 1–6 words |
| Errors, including the fix | 12–18 words |
| Instructions | 14 words is ideal; 20 at most |
| Notifications | Title plus body, 10–15 words |

Comprehension falls quickly past about 14 words per sentence. Aim for grade 7–8 reading level for general audiences, 9–10 for professional tools. Leave room for about 30–40% expansion in translation (more for short labels), and never build sentences by concatenating fragments.

## Copy Tells

Generated copy reads the same across products. Replace each tell with the fact it stands in for:

- **Hype words**: seamless, effortless, powerful, robust, unlock, elevate, supercharge, next-level, all-in-one. → The step count, the failure handling, the number.
- **Stock lines**: "Say goodbye to…", "X made simple", "at your fingertips", "Ready to transform your…?" → What the screen holds or does.
- **Shapes**: two-fragment headlines ("Plan less. Do more."), "not X, but Y" contrasts, a colon reveal ("One thing changed: …"), a trailing "-ing" rider (", ensuring a smooth start"). → One plain sentence.
- **Invented specifics**: made-up percentages, counts, or quotes. → The brief's facts, or a plainer line.
- **Punctuation**: exclamation marks in body copy, emoji as bullets, an arrow on every link. → Plain punctuation.

Delete a line if the screen works without it. If cutting 30% of the copy makes the screen better, keep cutting.

## Accessibility in Copy

- Link and button text makes sense out of context ("View order 1042", not "Tap here").
- Icon-only controls have accessible names written as actions ("Close", "Share photo").
- Spell out symbols and abbreviations in accessible labels when they would be read wrongly.
- Plain language and short sentences help everyone, and especially people with cognitive or reading differences.
