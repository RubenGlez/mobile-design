# Eval Results: v1.0.0 (November 2026)

## Method

- All 22 cases in `cases.md`, each run in two arms on the same model: **skill** (the agent reads `SKILL.md` and its references) and **baseline** (no skill, own knowledge only). Cases 03, 11, 16, and 20 used written descriptions of flawed screens as their artifacts.
- Each arm was answered by six independent agents, each handling 3–4 cases.
- **Blind judging.** For each case the two answers were relabeled A/B at random. Six judge agents, who didn't know a skill existed, scored each answer 1–5 on six axes, marked every expected signal yes/partial/no, flagged global failures, and picked a winner. The judges were told not to reward length.

## Results

| | Skill | Baseline |
| --- | --- | --- |
| Cases won | **22 / 22** | 0 |
| Mean score (1–5) | **4.63** | 3.59 |
| Expected signals fully met | **93%** (104 / 112, 8 partial, 0 missed) | 58% (65 / 112, 27 partial, 20 missed) |
| Global failure flags | 2 | 25 |

| Axis | Skill | Baseline | Δ |
| --- | --- | --- | --- |
| Specificity | 4.68 | 3.50 | +1.18 |
| Hierarchy | 4.82 | 3.73 | +1.09 |
| Completeness | 4.95 | 4.05 | +0.90 |
| Restraint | 3.82 | 2.95 | +0.87 |
| Correctness | 4.64 | 3.27 | +1.37 |
| Actionability | 4.86 | 4.05 | +0.81 |

Baseline failure flags: framework APIs prescribed in 18 of 22 answers, 7 factual errors (for example, a "Next" key on the phone pad, and the claim that VoiceOver skips disabled controls), 1 accessibility floor violation, and 1 dark pattern proposed.

Skill failure flags: one unsourced benchmark copied from `critique.md` ("most apps score 20–32/40"), and one overstated localization rule.

The smallest margins were in case 18 (microcopy, 4.50 vs 4.33) and case 03 (critique, 4.50 vs 4.17). The largest were in cases 06, 15, and 04 (+1.5 to +1.8).

## Weaknesses Found and Fixed After the Run

| Judge observation (skill arm) | Fix |
| --- | --- |
| Process ritual exposed to users: "dials: variance 5", thesis lines, mirror-test narration, MD rule IDs, token tables for single controls (lowest axis: restraint) | `SKILL.md` Output Contract: run the process silently, no internal vocabulary, scale the output to the task; rule IDs are optional in `critique.md` |
| Critique scaffolding outweighed the fixes; unsourced benchmark | `critique.md`: scores shown compactly after the findings, benchmark removed |
| Paywall answer ambiguous about preselecting the annual plan | `trust-ethics.md`: rule for plan pickers |
| Battery cost not raised at consent | `trust-ethics.md`: state battery and data cost before the system prompt |
| Plurals not addressed | `ux-writing.md`: zero/one/other forms per locale |
| Sheet spec didn't address home-indicator conflict | `motion-haptics.md`: drag from a handle above the system zone, stated in the spec |

## Verification of the Fixes

After the fixes, cases 06, 17, 19, and 22 were rerun with the updated skill and judged blind against the first skill run. The updated skill won 4/4, with a mean of 4.79 against 4.29. Restraint rose from 3.00 to 4.50 and hierarchy from 4.00 to 5.00. Answers were 8% shorter on average (22% shorter on case 22), and process vocabulary nearly disappeared. The sheet spec now resolves the home-indicator conflict.

One gap remained. Case 19 still preselected the annual plan, because the paywall rule allowed preselection when the charge was stated. The rule now forbids preselecting any plan.

## Limitations

- One run per case per arm. Variance between runs wasn't measured.
- The agents and judges are the same model family as the author of the skill, and the cases were written by the skill's author. An external human review would strengthen the evidence.
- Skill answers averaged about 15% longer. The judges were told to penalize length, and restraint still favored the skill, but length may still have some influence.
- Text-only deliverables. Rendered screens weren't evaluated.
