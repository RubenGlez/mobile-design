# Adversarial audit — mobile-design skill (2026-07-03)

Auditor: Claude (adversarial codebase audit). Scope: all 19 tracked files, read in full.
Repo: `RubenGlez/mobile-design`, branch audited: `claude/codebase-adversarial-audit-wo8pbw` (off `main` @ `daaee79`).

---

## 1. System map

**What it is.** An Agent Skill for professional mobile UI design (React Native / Expo / iOS / Android). The skill's "code" is prose: a root `SKILL.md` (frontmatter + operating loop + hard constraints + output contract) that routes into 13 `references/*.md` files loaded selectively per task.

**Discovery / install.** Root-level `SKILL.md` layout (not the `skills/<name>/SKILL.md` subdirectory convention). Installed via `npx skills add RubenGlez/mobile-design` (README). Frontmatter: `name: mobile-design` (matches repo name), `description` 470 chars (within the 1024 limit), third-person with explicit trigger nouns — valid and well-formed for discovery. No optional `license`/`metadata` fields.

**Routing.** `SKILL.md` mandates `references/design-process.md` on every task, then a task→file table for the other 12 files. Verified: **every routed file exists, and every existing reference file is routed** — no dead links, no orphans. Internal cross-references (`accessibility-touch → motion-haptics`, `screen-patterns → forms`, `visual-system → typography-color`/`react-native-implementation`) all resolve.

**Supporting files.** README (install + structure, matches actual layout), MIT LICENSE, minimal AGENTS.md/CLAUDE.md (contributor-facing), `.gitignore` (only `.harness/`).

---

## 2. Findings (ranked by severity)

### HIGH

**F1 — `references/forms.md:60` — "`returnKeyType="next"` moves to the next field" is literally false.**
`returnKeyType` only changes the return key's *label*; focus advance requires `onSubmitEditing={() => nextRef.current?.focus()}` plus `submitBehavior="submit"` (or legacy `blurOnSubmit={false}`), none of which appear anywhere in the file — not even in the "Anatomy" field block (which sets `returnKeyType="next"` with no `onSubmitEditing`). *Failure scenario:* an agent builds the documented field block, ships a login form whose "Next" key dismisses the keyboard instead of advancing, and then self-certifies against the Form QA item "Return key flow works" believing the prop alone satisfied it. **CONFIRMED.** Fix: add `onSubmitEditing`/ref-chaining to the anatomy example and reword the Focus Flow bullet.

**F2 — `references/forms.md:34`, `references/accessibility-touch.md:97` — the skill's canonical "announce it" examples use `accessibilityLiveRegion`, which is Android-only in React Native.**
Both files instruct "Announce async success/error results" / show error text, and both demonstrate it with `<Text accessibilityLiveRegion="polite">`. On iOS this prop is a no-op; VoiceOver announcement needs `AccessibilityInfo.announceForAccessibility()` (or `aria-live`, which also maps to the Android-only behavior). *Failure scenario:* an agent copies the sample, checks off the QA items "Error messages are announced" (accessibility-touch.md:127) and "VoiceOver/TalkBack reads … error" (forms.md:143), and ships a form where iOS VoiceOver users never hear validation errors — in the skill's own flagship accessibility file. **CONFIRMED.** Fix: show the cross-platform pattern (live region for Android + `announceForAccessibility` for iOS) or at minimum label the prop Android-only.

**F3 — `references/accessibility-touch.md:13-24` — the hitSlop example produces a hit area below the minimums stated six lines above.**
Line 13 allows a 20–24pt visible icon; the example adds `hitSlop` of 10 per edge. Arithmetic: 20+20=40pt (fails both the 44pt iOS and 48dp Android minimums), 24+20=44pt (passes iOS, still fails the 48dp Android minimum from line 10). *Failure scenario:* an agent asked for a cross-platform icon button copies the file's only concrete example and violates the skill's own Hard Constraint (SKILL.md:76) and Touch QA item ("Every target meets platform minimum hit area") — on Android, in every case. **CONFIRMED** (pure arithmetic). Fix: size the example to 48 (e.g. hitSlop 12–14 around a 24pt icon plus padding, or state minWidth/minHeight 48).

**F4 — `references/platform-ios.md:6-11` — "Clarity, Deference, Depth" presented as Apple's current core principles; file predates the current iOS design language.**
That trio is the iOS 7-era formulation, removed in Apple's 2023 HIG restructure; since the 2025 redesign (iOS 26, Liquid Glass) Apple's stated foundations are hierarchy/harmony/consistency and the Liquid Glass material system — which this file (whose entire job is "iOS-specific conventions … HIG alignment") never mentions, while confidently teaching the obsolete trio as "Apple's core principles." *Failure scenario:* an agent doing an "HIG alignment" review cites Clarity/Deference/Depth as the governing framework in 2026 and evaluates materials/blur against a pre-Liquid-Glass model, producing a review that reads as authoritative but is a design-language generation behind. The SKILL.md "Source Freshness" rule partially mitigates — but only for "version-specific" advice, and principle names don't read as version-specific, so the agent has no cue to re-verify them. **CONFIRMED** (stale as of audit date). Fix: reframe the trio as historical heuristics or replace with the current foundations; add a Liquid Glass note next to the blur/materials guidance.

**F5 — `README.md:3` — stale skills.sh badge contradicts the repo's own deliberate removal of skills.sh distribution.**
Commit `3d8f2d5` removed `skills.sh.json`; commit `977a805` removed the README's entire "Distribution" section for skills.sh — yet the badge `[![skills.sh](https://skills.sh/b/RubenGlez/mobile-design)]` survived at line 3, still advertising and linking the channel the maintainer withdrew from. *Failure scenario:* a user clicks the badge to evaluate/install and lands on a listing the maintainer no longer maintains config for; contributors get contradictory signals about the intended distribution channel. **CONFIRMED** (git history above). Fix: delete the badge, or restore skills.sh support intentionally.

### MEDIUM

**F6 — `SKILL.md:19-25,60-70` vs `references/design-process.md:18-28,103-155` — the design-read sentence and all three dial tables are duplicated (dials effectively triplicated with `references/motion-haptics.md:19-27`).**
Currently the copies agree; nothing marks one as canonical. *Failure scenario:* a future edit changes the default variance or the 4-6 band meaning in one file only, and agents get different behavior depending on which file they loaded — the classic drift this audit is meant to pre-empt. **CONFIRMED** duplication / **PLAUSIBLE** drift. Fix: make SKILL.md a one-line pointer ("dial semantics live in design-process.md") or vice-versa.

**F7 — `references/navigation.md:79` — "`createStaticNavigation` accepts linking prefixes" points at the wrong API surface.**
In React Navigation v7's static API, `createStaticNavigation(RootStack)` returns a component; linking prefixes are passed to that component's `linking` prop (`<Navigation linking={{ prefixes, ... }} />`), and route-level paths live in screen `linking` options — `createStaticNavigation` itself takes no linking argument. The sentence hedges with "Check current docs," which softens but does not neutralize the misdirection. *Failure scenario:* an agent tries `createStaticNavigation(Root, { linking })`, hits a type error, and burns a cycle. **PLAUSIBLE** (hedged; API shape as of knowledge cutoff). Fix: "prefixes are passed via the `linking` prop of the component returned by `createStaticNavigation`."

**F8 — Repo layout: root `SKILL.md` means `npx skills add` installs the whole repo — README, LICENSE, AGENTS.md, CLAUDE.md, `.gitignore` — into the consumer's skill folder.**
The subdirectory convention (`skills/mobile-design/SKILL.md`) exists precisely so only the bundle installs; this author uses it in other projects (reelme ADR-0004). Root layout works with the skills CLI, but contributor files (including a `CLAUDE.md` containing `@AGENTS.md`) ride along into every consumer's agent context directory. *Failure scenario:* consumer's skill folder accumulates non-skill files; a future non-skill addition to the repo root silently ships to all installers. **PLAUSIBLE** (behavior depends on installer version; root-SKILL.md single-skill repos are commonly copied whole). Fix: either move to `skills/mobile-design/`, or accept and document the root layout ("everything in this repo ships with the skill").

**F9 — `SKILL.md:15,27-36` — Operating Loop step 4 and "Source Freshness" require consulting official docs with no offline fallback.**
"Check current local package versions **and official docs** before version-specific implementation advice" is unexecutable in sandboxed/no-network environments, and the skill never says what to do then. *Failure scenario:* a conscientious agent stalls or repeatedly fails WebFetch; a sloppy one silently skips the step yet still reports "verified" under the Output Contract. **PLAUSIBLE.** Fix: add "if docs are unreachable, say so and mark the advice as unverified-against-current-docs" (the Output Contract's "what could not be verified" hook exists — wire the two together explicitly).

**F10 — `references/forms.md:54` — one-time-code row gives only the iOS half (`textContentType="oneTimeCode"`); no Android SMS-OTP autofill (`autoComplete="sms-otp"`).**
Every other row in the table pairs cross-platform props; this row's omission reads as "Android has nothing." *Failure scenario:* agent ships an OTP field that autofills from Messages on iOS but requires manual copy on Android. **PLAUSIBLE** (RN supports `autoComplete="sms-otp"` on Android). Fix: add it to the row.

**F11 — `references/typography-color.md:34-42` — Android title style combines `fontFamily: 'sans-serif-medium'` with `fontWeight: '700'`.**
The 700 weight overrides/synthesizes over the medium family, so the "medium" choice is dead config and the rendered weight differs from the visually-intended medium; agents copying the token will propagate the confusion. **CONFIRMED** (self-contradictory style), low impact. Fix: pick one (`sans-serif` + '700', or 'sans-serif-medium' + '500'/default).

**F12 — `references/platform-android.md:27-36` — Compose snippet declares `role = Role.Button` on a `Box` with no click action.**
`minimumInteractiveComponentSize()` + button semantics without `Modifier.clickable {}` yields a TalkBack "button" that cannot be activated and, per Compose semantics, minimum-size enforcement is tied to interactive components. The example teaches semantics divorced from action. *Failure scenario:* agent copies it for a custom control and ships a non-activatable announced button. **PLAUSIBLE.** Fix: add `.clickable(onClick = …)` (which supplies the role) or use an `IconButton`.

**F13 — `references/typography-color.md:64-71` — Type Direction table recommends commercial typefaces (Neue Montreal, GT America; Satoshi is free-with-license-terms) with zero licensing caveat.**
*Failure scenario:* an agent scaffolds `expo-font` loading for a font the project has no license to bundle, creating legal exposure the skill never flagged. **PLAUSIBLE.** Fix: one sentence — "verify font licensing before bundling; these are direction examples, not free-to-use assets."

### LOW

**F14 — `SKILL.md:40` "Always start with design-process.md" vs `SKILL.md:14` "Load only the relevant reference files."**
For a one-line tweak ("increase this button's padding"), the mandatory 165-line design-process read plus a design-read sentence and dial-setting is ceremony disproportionate to the task; agents follow "always" literally. **CONFIRMED** tension, low harm (cost is tokens/latency, not wrong output). Fix: scope the mandate — "for any design, review, or screen-level task."

**F15 — Frontmatter omits the optional `license` field despite the repo carrying MIT.** Registries/tools that surface skill licensing show nothing. **CONFIRMED**, trivial fix.

**F16 — No versioning/changelog for installed copies.** `skills add` installs a snapshot; consumers have no way to know what changed on update. **PLAUSIBLE**, low. Consider a `metadata.version` and a CHANGELOG.

**F17 — `references/design-process.md:69` cascade cell "custom/Phosphor/SF/Material by platform" is the one place the skill names a third-party icon brand inside a defaults table** (elsewhere Phosphor appears only as an "installed family" option, `visual-system.md:109`). Minor inconsistency in how strongly third-party icon sets are endorsed. **PLAUSIBLE**, cosmetic.

---

## 3. Design tensions

**T1 — Embedded volatile facts vs. the "everything is unstable" doctrine.** SKILL.md declares all platform/library detail unstable and routes to source-map, yet the references hard-code exactly such facts (HIG principle names — already stale, F4; "dynamic color is Android 12+"; React Navigation static-API shape; RN prop behaviors). The two strategies fight: agents can't tell which embedded facts are load-bearing heuristics vs. cached claims needing re-verification. *Alternatives:* (a) tag volatile claims inline ("as of 2026 — verify via source-map"), (b) strip version-coupled claims into source-map entries and keep references purely heuristic, (c) date-stamp each reference file's last fact-check.

**T2 — Duplication as UX vs. single source of truth (F6).** Repeating the design read and dials in SKILL.md makes the skill usable without loading design-process.md — a real benefit — but creates three-way drift surfaces. *Alternatives:* SKILL.md keeps only dial names + one-line meanings and delegates semantics; or a generated SKILL.md section with a "do not hand-edit, mirrors design-process.md" marker.

**T3 — Root layout vs. subdirectory bundle (F8).** Root SKILL.md maximizes discoverability (visible on the GitHub landing page) but conflates repo scaffolding with the installable artifact. The author's own reelme repo chose `skills/<name>/` for exactly this reason. Either answer is defensible; the current state is the only undocumented one.

**T4 — Numeric dials without acceptance criteria.** `DESIGN_VARIANCE 6` vs `7` has no testable difference; two agents given the same brief will pick different numbers and both claim compliance. The translation tables help but map bands, not values. *Alternative:* named presets (`native / branded / expressive / experimental`) with per-preset must/must-not lists — checkable in review, unlike a scalar.

**T5 — Self-certifying QA loops.** Every reference ends in a checklist the same agent that wrote the code ticks off — and F1–F3 show the file bodies can steer the agent into violating their own checklists while believing they pass. Checklists that say "Return key flow works" need the *mechanism* ("verify onSubmitEditing advances focus on device/simulator") or they become confirmation theater.

---

## 4. Expectation gaps

- **Expected** the author's own `skills/<name>/SKILL.md` convention (used in reelme); **found** root layout with contributor files shipping alongside the skill.
- **Expected** the skills.sh badge to disappear with the two commits that removed skills.sh config and the Distribution section; **found** the badge still live at README:3.
- **Expected** the iOS platform file to reflect the 2025–26 HIG era (Liquid Glass, current foundations); **found** iOS 7-era principles taught as current, and no mention of the platform's present design language.
- **Expected** the accessibility file's code samples to satisfy the skill's own hard constraints; **found** a hit-area example below the Android minimum (F3) and an announcement API that is silent on iOS (F2).
- **Expected** forms.md's anatomy block to be a copy-paste-safe golden example; **found** it missing the focus-advance wiring its own Focus Flow section implies exists (F1).
- **Expected** a statement of what `npx skills add` actually installs and how updates work; **found** neither (README shows the command only).
- **Expected** README/AGENTS.md drift; **found** none — README's file listing matches the tree exactly, and AGENTS.md is accurate (a genuine positive).
- **Expected** broken routing somewhere across 13 references; **found** zero dead links or orphans — the routing table is fully sound (positive).

## 5. Open questions

1. Is skills.sh still an intended distribution channel (badge says yes, git history says no)? If yes, should `skills.sh.json` return?
2. Is the root-SKILL.md layout deliberate, and is shipping README/LICENSE/AGENTS.md/CLAUDE.md to consumers acceptable?
3. Should references carry a "facts verified as of <date>" stamp so staleness like F4 is detectable rather than silent?
4. Are the commercial font recommendations (F13) intentional, and should licensing guidance accompany them?
5. Is there an intended update story (version metadata / changelog) for users who installed an earlier snapshot?
6. Should the skill declare tool expectations (WebFetch for Source Freshness, simulator access for "Verify the result") so host agents can degrade gracefully (F9)?

---

*Verification notes: all 19 tracked files read in full; link/orphan check done mechanically (grep of `references/*.md` mentions vs. tree); hit-area arithmetic in F3 checked by hand; F5 confirmed against `git show 3d8f2d5` / `977a805`; F1/F2/F7/F10 checked against React Native / React Navigation API behavior as of knowledge cutoff (Jan 2026) — re-verify against current docs before acting, per the skill's own source-map rule.*
