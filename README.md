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

[examples/premortem-newsletter-example.md](examples/premortem-newsletter-example.md) — a full five-stage premortem on a paid local-newsletter plan, showing the report structure end to end: the funnel arithmetic caught as the top failure mode, the compound failure narration, the adversary kill chain, and dated tripwires.

## Provenance

Evolved from an original premortem skill through structured A/B testing: multiple independent writer agents produced reports under both the original and evolved skill on the same plans, and blind judges scored them on specificity, causal chaining, calibration, actionability, adversarial depth, and tripwire quality. This version is what survived.

## License

[MIT](LICENSE)
