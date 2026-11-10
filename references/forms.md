# Forms

Use for sign-in, sign-up, checkout, settings, profile editing, creation flows, filters, and any input-heavy screen. On mobile the keyboard takes about half the screen, typing is slow and error-prone, and interruptions are constant. Every field must earn its place.

## Principles

- **Ask less.** Remove fields, infer what can be inferred, default sensibly, and defer optional fields until after the first success.
- **Group by the user's mental model**, not the database schema. One topic per group, with a short heading when there are several groups.
- **Keep labels visible.** Placeholders are examples of the format; they disappear as soon as typing starts.
- **Validate to help, not to scold.** Check on blur or after the first submit attempt, never on the first keystroke.
- **Preserve everything.** Input survives errors, failed submits, navigation, backgrounding, and rotation.
- **Accept liberally.** Take spaces, dashes, pasted values, and different formats, then normalize them. Never block typing; explain instead.

## Field Anatomy

Every field has: a visible label; the input, sized as a full-width touch target at least 44pt/48dp tall; optional helper text (why it's needed or its format); an error slot that doesn't shift other content when it appears; and the current state (empty, focused, filled, error, disabled, read-only) visible without relying on color alone.

## Input Intent

Specify each field's intent so any implementation can pick the right keyboard, autofill, and behavior:

| Field | Keyboard | Autofill / system help | Notes |
| --- | --- | --- | --- |
| Email | Email keyboard | Email autofill | No autocapitalization or autocorrect |
| New password | Default, secure entry | Password manager: generate a strong password | Show/hide toggle; state the requirements up front |
| Existing password | Default, secure entry | Password manager: fill | Always allow paste |
| One-time code | Numeric | System code-from-SMS or email autofill | Accept paste; advance automatically; offer resend with a visible cooldown |
| Phone | Phone pad | Phone autofill | Country picker; the phone pad often has no "next" key, so provide a visible Continue |
| Name | Default, capitalize words | Name autofill | Don't force first/last splits; support single names and long names |
| Address | Default | Address autofill, or system address search | Country-aware fields; avoid long dropdowns |
| Amount / number | Decimal or number pad | — | Locale decimal separator; show the currency; keep the full value visible |
| Date | System date picker | — | Avoid free-text dates; show the format in the user's locale |
| Search | Default with Search key | Recent searches | Clear button; suggestions while typing |
| Card | Number pad | Card scan or wallet where available | Group digits as typed; detect the card type |

Choose selection over typing when the options are known and few: segmented controls for 2–4 options, a list or picker for more, and an "Other" choice with free text as the fallback.

## Focus and Keyboard Flow

- The return key moves to the next field and submits on the last one, labeled for the action ("Next", "Go", "Send", "Search").
- When a keyboard has no return key (phone and number pads), give a visible way forward.
- The focused field and the primary action stay visible above the keyboard. The screen scrolls; content is never hidden behind the keyboard.
- Don't move focus unexpectedly. Autofocus the first field only when the screen exists solely to collect that input.

## Validation

Use three layers:

1. **Constraints while typing**, only to prevent impossible input (letters in a number pad field), and always with an explanation.
2. **Inline validation** on blur or after the first submit attempt, placed next to the field: "[Field] + requirement" (`ux-writing.md`).
3. **Server validation** after submit, mapped back to the specific field whenever possible.

Don't:

- Show red errors before the user had a chance to finish.
- Clear fields after a failed submit.
- Show "Something went wrong" when a specific field is at fault.
- Disable the submit button with no explanation. Prefer keeping it enabled, then on tap show what is missing and move focus to the first problem.

## Submit

- Name the outcome: "Create account", "Pay $42.18", "Save address".
- While submitting, keep the label, show progress, and prevent duplicate submits.
- On success, continue the flow with continuity or confirm briefly.
- On failure, keep every value, explain what happened, and offer to retry.

## Checkout and Payments

- Show the total, and what changes it, from the first price on. No fees revealed late.
- Make shipping, payment, promo codes, and contact details editable in place.
- Prefer the platform's wallet and payment sheets when available.
- The final action names the amount, and the screen shows its processing state until the payment is confirmed. Never show pending as success.
- After a failure, keep the cart and every field, and offer a different payment method.

## Sign-In and Sign-Up

- Support password managers, passkeys, and platform sign-in where they are available.
- Never block paste in password or code fields.
- Let people explore before creating an account whenever the product allows it.
- Error copy is calm and specific enough to recover, without revealing whether an account exists when security policy forbids it.
- Account recovery is one tap away from the sign-in screen.

## Search and Filters

- Before typing: recent searches, suggestions, and categories. Never a blank screen.
- While typing: suggestions, highlighted matches, and fast results.
- No results: echo the query, suggest corrections, and offer to broaden it or clear filters.
- Active filters are always visible, with a count and a one-tap reset. Apply small, fast filters live; use an explicit Apply for expensive ones.

## Form Checklist

- The keyboard never hides the focused field or the primary action.
- The return key and visible Continue path work through the whole form.
- Autofill and password managers fill the right fields.
- Labels, helper text, and errors survive the largest text size and translation.
- A screen reader announces each label, value, error, and state.
- An offline or server error keeps all input.
- Submit can't fire twice.
