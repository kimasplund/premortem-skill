# premortem-skill

An agent skill that runs a rigorous five-stage premortem on any plan before it launches. Instead of answering "is this a good plan?" with reassurance, it assumes the plan already failed and reasons backwards to why — then rebuilds the plan so it doesn't.

## What it does

Given a plan, launch, pitch, career move, budget, or any significant decision, the skill produces one report with five stages:

1. **The Autopsy** — ~7 specific failure modes, ranked by calibrated probability shares, each narrated month-by-month in past tense, with the hidden assumption and first warning sign for each.
2. **The Verdict** — an impact × feasibility ranking: most likely killer, most dangerous killer, the hidden assumption found by convergence, and the fatal flaw (or the honest statement that there isn't one).
3. **The Rebuild** — the plan rewritten with the failure modes closed, each change priced, gated by an explicit IF/THEN decision rule for any irreversible step.
4. **The Adversary** — a profile of who gains most from your failure, their dated kill chain, and the detection opportunity for each move.
5. **The Tripwires** — a monitoring table where every failure mode gets a measurable signal, a threshold, a check date, and a pre-decided response — plus the combination that means stop, not adjust.

## Install

The skill is self-contained: `SKILL.md` + `references/failure-class-checklist.md`, no dependencies. Copy the directory into your agent's skills location:

```bash
# Kimi Code (user scope, available in every project)
git clone https://github.com/kimasplund/premortem-skill.git ~/.agents/skills/premortem-evolved

# Claude Code
git clone https://github.com/kimasplund/premortem-skill.git ~/.claude/skills/premortem-evolved
```

Or drop the files into a project-level `.agents/skills/premortem-evolved/` directory to keep it scoped to one repo. Restart your agent session so it picks up the new skill.

## Usage

Once installed, just share a plan. The skill triggers on requests like:

- "Here's my plan for …, what do you think?"
- "Poke holes in this."
- "Should I do it?"
- "Run a premortem on this."

For best results, include the concrete actions, timeline, budget/resources, what success looks like (a number and a date), who else is involved, and constraints. If those are missing the skill will ask once, or proceed with an explicit assumptions block.

## Example output

- [examples/deployboard-premortem.md](examples/deployboard-premortem.md) — the skill at full scale: a solo founder's SaaS launch with a quit-your-job gate. Shows the funnel arithmetic caught as the top failure mode, an IP-assignment mode with no warning sign picked as most dangerous, the compound "zombie plan" scenario, a seeded competitor's dated kill chain, and a kill condition with pre-written tripwire responses.
- [examples/premortem-newsletter-example.md](examples/premortem-newsletter-example.md) — a compact run on a smaller plan (paid local newsletter), showing how the format scales down without padding.

## Provenance

Evolved through four rounds of blind, pre-registered A/B testing across two independent evaluation harnesses. In every round, independent writer agents produced reports under both skills on the same plans; persona-diverse blind judges scored them dimension-major on specificity, causal chaining, probability honesty, flaw detection, rebuild actionability, adversarial depth, tripwire quality, tone, and bloat; a mechanical auditor cross-checked the guard dimensions; and a sealed key matrix verified detection of planted flaws against generic no-skill controls.

- **Rounds 1–2** (Kimi swarm): the original skill was evolved into v2; three later candidate branches (v3–v5) each beat v2 on totals and blind preference and were still rejected by conjunctive regression guards. Their validated machinery — urgency-tiered rebuilds, pre-launch falsifiers, prevent/limit/accept labels, re-upgrade tripwire rows, dated calibration review, and the proportionality screen — was preserved as a research inventory.
- **Round 3** (Claude, skill-gauntlet): a v6 candidate carrying that inventory plus two mechanical fixes ran against v2 on a fresh brief slate with fresh judges. It won 12/12 blind forced choices, detected 97.2% of planted flaws vs 91.7–93.1%, eliminated v2's stage-narration leak class (~1 vs ~19 machinery leaks), halved-and-more its probability-ladder violations (3 vs 9), and deflated a trivial-task fixture that v2 answered with a 3,900-word ceremony — with no regression on any instrument. The pre-registered gate still returned NO ADOPTION on a statistical-sufficiency line (the D7 margin sat inside a noise band at n=9 runs/arm); v2.1 ships v6 by explicit owner decision, disclosed in full in [evolution/round-3.md](evolution/round-3.md).

The complete round-3 record — pre-registration, sealed mapping, scorecards, and the specified v7 recipe — lives in [evolution/](evolution/).

## Changelog

- **v2.1** (2026-08-18) — ships the v6 candidate: de-ordinalized report template plus a mechanical leak-scan gate (no more "Stage N" machinery narration), tie-pair enumeration for the probability ladder, a proportionality screen that answers trivial reversible plans in a few lines instead of running the full ceremony, and the validated v3–v5 rebuild/tripwire machinery (urgency tiers with decision dates, falsifiers, prevent/limit/accept, re-upgrade rows, calibration review).
- **v2** (2026-08-16) — initial public release; survivor of evolution rounds 1–2.

Note: the two example reports were generated under v2 and keep its numbered section headers; v2.1 output uses the same five sections with unnumbered names.

## License

[MIT](LICENSE)
