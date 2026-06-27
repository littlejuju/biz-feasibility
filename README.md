# biz-feasibility

A cold, kill-criteria business-feasibility evaluator, packaged as a [Claude Code](https://claude.com/claude-code) skill.

> **Quick start** — clone into your Claude Code skills dir, then just describe an idea:
> ```bash
> git clone https://github.com/littlejuju/biz-feasibility.git ~/.claude/skills/biz-feasibility
> ```
> In Claude Code, type `/biz-feasibility` or simply pitch your venture — it auto-triggers. Example: *"I want to build a community dog-walking app in Singapore as a side project — can it work?"* It will ask for any missing load-bearing info, then return a verdict (PROMISING / 副业·CAPPED / KILL / CONDITIONAL).

**The point is not to cheerlead an idea — it's to falsify it.** It defaults to skepticism and dares to return KILL. It's tuned for the messy reality of small markets (e.g. Singapore, thin supply) and for the founder-side questions that actually decide a venture's fate: *is the supply already operating without me? does reaching scale unlock a privately-capturable engine, or is this forever a public good? is it a platform or just an agency? where does the revenue actually hang — and will both sides route around me?*

It runs a fast structural screen (a 9-filter platform module + three "mother" death-causes + the frequency-density-WTP deadlock + per-type unit-economics), enforces a strict **data-provenance discipline** (every load-bearing number gets a confidence color; load-bearing-but-unverified triggers an alarm), and — on request — a deeper two-round adversarial multi-agent evaluation.

Recent additions:

- **Epistemic-status self-declaration** — it announces up front that it's a decision-hygiene / red-team protocol, *not* a back-tested predictor; its single most dangerous failure mode is the **false-kill**, which the closing red-team must probe explicitly.
- **Verdict vector** — every KILL / 副业·CAPPED pins the verdict to the sub-object it actually applies to (current form vs. founder-full-time vs. venture-scale vs. cheapest wedge), so "KILL" is never misread as "every form of this dies."
- **Input-isolation gate** — a silent pre-judgment pass: no cross-case entity bleed, no un-redacting a de-identified brief, no importing a direction the brief never gave.
- **Trigger-specific gates** — channel-fit, strategic-migration, legal-wording precision, and category-not-dead gates that fire only when the brief trips them.
- **Escape-testing** — every KILL/CAPPED's cheapest test must include an *escape-test* that probes the one survival path the idea claims, not just a *death-test* that reproduces the death-cause; passing an escape-test lifts the verdict at most to its passed-state ceiling, never auto-PROMISING.

## What's here

| File | What it is |
|---|---|
| `SKILL.md` | The whole framework. This is the skill. |
| `feasibility-workflow.js` | Optional deep-mode [Workflow](https://docs.claude.com/en/docs/claude-code) template: brainstorm ≥N proposals → adversarially score each → mother-death escape adjudication → loop-until-dry → chief synthesis. Edit its `CONFIG` block per evaluation. |

## Four verdicts (one action each)

- **PROMISING** — clears opportunity cost, investable / scalable → go.
- **副业 · CAPPED** — clears cash cost but can't scale / can't be invested; whether it clears *opportunity* cost depends on *this* founder's own baseline.
- **KILL** — can't even clear cash cost (chronic bleed) or structurally doesn't stand up → don't / exit.
- **CONDITIONAL** — an untested swing variable routes to one of the above → go run the cheapest falsification test first.

(The deprecated `WEAK` label was split into the four above, because one tag mapping to two opposite actions — "capped, so do it as a side gig" vs "failing, so don't" — is itself a defect.)

## Install

Drop the folder into your Claude Code skills directory:

```
~/.claude/skills/biz-feasibility/
  ├── SKILL.md
  └── feasibility-workflow.js
```

Then invoke `/biz-feasibility`, or just describe a venture idea — it auto-triggers. Before screening it will ask for any missing load-bearing info (supply side / real WTP + who pays / founder assets) rather than guessing.

## Language

The framework prose is written in Chinese, but the **report is generated in the user's own language** — it mirrors whatever language you pitch in (Chinese → Chinese, English → English, etc.). See `交付可读性 ④` in `SKILL.md`.

## Scope boundary

It judges the **idea**, not the person. It never coaches, never prescribes a life/career vehicle, and makes no claims about your interior. When the question turns into "what should I do with my life / am I finished," it declares its boundary and refers out.

## Provenance of the examples

The framework was hardened case-by-case on real evaluations. Case codes like `A1–A14 / S1–S20 / CG-CLEAN / DOG` (and aliases like `代号 M/T/R/E`, `化名 J`) are **anonymized** — the original subjects are de-identified. They're kept (not deleted) because the concrete "实犯" failures are what ground the abstract rules; removing them would weaken the screen. Named real companies (LinkedIn, Clubhouse, Quibi, Jibo, Rover/Wag, Character.AI, Strava, Renaissance, …) are public facts cited as teaching examples.

## License

MIT — see [`LICENSE`](./LICENSE).
