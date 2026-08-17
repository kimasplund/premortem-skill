---
name: premortem-evolved
description: Run a full 5-stage failure analysis on a plan before it launches — a steelmanned, category-forced autopsy of how it died with calibrated probability shares, an impact-by-feasibility verdict, a rebuilt plan gated by a decision rule, an adversary's dated kill chain, and tripwires that include the adversary's moves. Use this whenever someone shares a plan, launch, pitch, campaign, career move, business idea, budget, or any significant decision they're about to commit to — including when they only ask "is this a good plan?", "what do you think?", "any holes in this?", "should I do it?", or "poke holes in this". Assume a plan being shared is a request for a premortem unless they clearly want something else.
---

# Premortem

Asking "is this a good plan?" pulls for confirmation — the natural reply hunts for reasons it works, and the person executes on something broken and finds out weeks later. A premortem inverts it: assume the plan already failed, then reason backwards to why. Prospective hindsight ("it failed" → "because...") reliably surfaces more, and more specific, causes than prospective forecasting ("it might fail if..."). Gary Klein's version of this is standard practice before major launches at plenty of large companies.

Deliver all five stages in one report, in order. They build: the autopsy generates the failure modes, the verdict picks the ones that matter, the rebuild closes them, the adversary finds what the first three missed, and the tripwires make it all checkable on specific dates.

## Step 1: Get the plan specific enough to kill

A premortem is only as good as the detail it has to work with. Vague plan in, generic autopsy out — and a generic autopsy is worse than useless because it feels like analysis.

Before writing, you need:
- **What exactly they're doing** — the concrete actions, not the ambition
- **Timeline** — start date, milestones, the horizon (default 6 months)
- **Budget / resources** — money, hours per week, people, runway
- **What success looks like** — a number and a date, ideally
- **Who else is involved** — customers, partners, employer, family, investors
- **Constraints** — what they can't change

If two or more of these are missing, ask for them in one batch before writing. Ask once, not repeatedly. If they say "just run it" or don't answer, proceed — but open the report with an explicit **Assumptions I'm working from** block listing what you filled in, because those assumptions become load-bearing in the analysis and they need to be able to correct them.

## Step 2: Write the report

Use this structure.

### Generate before you write

First, recompute the plan's own success math with its own numbers — runway, funnel, conversion, capacity, target date. If the plan misses its target on its own assumptions, that is a top-2 failure mode, stated as arithmetic, not as a risk.

Then silently generate **12–15 candidate failure modes** — at least one per failure class in [references/failure-class-checklist.md](references/failure-class-checklist.md), or an explicit N/A with a reason. Stop when two consecutive candidates fold into existing modes. Then cut to ~7: drop a candidate only if it is low-probability AND low-danger AND duplicates another mode's mechanism — a low-probability, high-severity, non-mitigable mode stays. In the report, one line under the autopsy: `**Considered and cut:** X (folded into #3), Y (<2%, recoverable).`

For every person the plan depends on, grade the commitment you actually hold — champion / endorse / accept / comply — not the one narrated. Anything below Endorse is a failure mode or a checklist item (convert it to paper before launch).

After cutting, run the diversity test: each surviving mode must differ from every other in at least 2 of {cause domain, who triggers it, timing of onset, detectability, reversibility}. Two modes sharing cause-domain + trigger + timing are one mode — merge and regenerate the slot. Seven variations of "not enough clients" is one failure mode wearing seven hats.

The generation pass is silent — none of it ships in the report except the cut line. The failure classes, diversity dimensions, cut criteria, commitment scale, and the pre-delivery verification checklist all live in [references/failure-class-checklist.md](references/failure-class-checklist.md).

```markdown
# Premortem: [plan name]
**Horizon:** [date, 6 months out by default] · **Success was defined as:** [their words]
**Note on the percentages:** shares of failure — "if this dies, this is what killed it" — not the probability the plan fails overall. They sum to ~100. [Optional, high-stakes only: **Overall chance this misses its success definition by the horizon:** ~X%]
**Assumptions I'm working from:** [only if you filled gaps — otherwise omit]

## 1. The Autopsy
**The strongest case for this plan:** [3-5 lines — why a smart, informed person, with the best evidence available, believes this works. Every failure mode below must beat THIS plan, not a strawman. A genuine advocate must be able to recognize their own case.]
Seven ways this died, ranked by probability.

### 1. [A specific sentence naming the failure, not a category]
**Probability:** ~X% — [one-clause justification]
**Cause of death:** [what actually killed it]
**How it unfolded:**
- Month 1: ...
- Month 2: ...
- (through to the month it died)
**The assumption that allowed it:** [the belief they held without knowing they held it]
**First warning sign:** [what they'd have seen, and roughly when]

[repeat through ~7; one entry is the compound scenario — the two modes most likely to co-occur, narrated as an interaction]
**Considered and cut:** [mode (folded into #N), mode (low-probability, recoverable), ...]

## 2. The Verdict
| # | Impact (1-5) | Feasibility (1-5) | I×F |
[one row per autopsy mode]
**Most likely:** #N — highest feasibility among the high scorers, because...
**Most dangerous:** #N — highest impact regardless of feasibility, weighted by silence × irreversibility: how late the first warning sign appears relative to the point of no return, and whether you can recover if it fires. If it's the same mode as most-likely, say why.
**The hidden assumption:** find it by convergence — pairwise-compare the modes' mechanisms; the belief the most modes share as a root is the hidden assumption. Two modes that both die unless the same belief holds is stronger evidence than either's probability alone.
**Fatal flaw:** [name it plainly — or state plainly that there isn't one, and name the real binding constraint instead]

## 3. The Rebuild
**The revised plan:** [rewritten with the failure modes closed]
**What changed and why:**
| Change | Failure mode it closes | What it costs |
**Pre-launch checklist:** 3-5 things to verify before executing anything. For each: what to check, how to check it, and the specific result that means walk away entirely.
**Decision rule:** [for any irreversible commitment, the IF/THEN that gates it — "resign IF one self-originated client has paid AND both anchors signed, ELSE extend 8 weeks." Sequence the risky capability test before the irreversible step; never split the difference without arguing why it doesn't inherit the worst of both.]
**How the rebuilt plan dies:** [2-4 lines — each fix is itself a plan with assumptions; name the new weakest joint the rebuild introduces, or state the fix is strictly dominant.]
**Residual risk:** [what still kills this even rebuilt]

## 4. The Adversary
**Playing:** [who gains most — motivation, resources, risk tolerance, what they *can't* do, and what their best alternative costs them]
**The kill chain:** [dated sequence of 3-5 moves anchored to their timeline — probe, position, strike, entrench]
**Detection opportunities:** [for each move, the observable signal the defender would see, and when]
**The move you'd never see coming:** [the one outside their frame]
**What this means you should change:** [1-3 lines]

## 5. The Tripwires
| Failure mode | Measurable signal | Threshold | Check on | If tripped |
[one row per failure mode from stage 1, plus one row per adversary detection opportunity]
**Kill condition:** [which combination means stop, not adjust]
```

## What separates this from generic advice

These are the things that make the difference between a premortem worth acting on and a list of business platitudes:

**Steelman first.** Write the strongest case for the plan before any failure mode. Stage 4's adversary attacks the plan's strongest element, not its weakest excuse.

**Every cause of death traces to something in their plan.** A specific number, date, dependency, channel, person, or price they gave you — or a specific thing they left out. Test: if a cause could be pasted into a stranger's premortem unchanged, it isn't finished. Rewrite it until it couldn't.

**Write it in past tense, from the future.** It already happened. "The two verbal commitments didn't convert" — not "the commitments might not convert." The tense is what makes the reasoning concrete; hedged tense produces hedged causes.

**Chain the months causally.** Each month's event should be caused by the previous month's, not a list of separate bad things stacked in a timeline. That chain is what makes the first warning sign identifiable.

**Rank honestly and show the numbers.** Use the coarse ladder — ~5 / ~10 / ~15 / ~20 / ~30 / ~40 — with words (rare / plausible / common / likely); never a decimal like 23%. Every number carries a one-clause justification ("the non-solicit clauses already exist unread"); a naked number fails the delivery check. Anchor the top two modes to a reference class ("consultants leaving firms fail on origination, not delivery") with one disanalogy line: where this plan differs from the reference class and which direction that pushes the number. If the domain is fast-moving (platforms, ad costs, AI tooling), run one dated search before fixing those numbers. Cap the top mode at ~40% — if one mode would exceed ~50%, the plan is dominated by a single risk and the Verdict says so instead. Allow at most one tied rung per autopsy, with the tie-break written out; if the whole spread is under 20 points, justify why the modes are genuinely that close or merge the tail. A ranking with no mode above ~20% is a strong-plan finding, not a failed premortem — say it plainly. Flag modes the reference class can't cover as judgment calls.

**Include the two failure modes people miss.** At least one from something the plan doesn't mention at all (the omission — the thing they never priced, never staffed, never scheduled). And at least one where the plan *worked* and that's what killed it: demand they couldn't serve, growth that broke the thing, attention that attracted a competitor. And keep one slot for what this plan's frame can't see — a risk you can't yet mechanism-ize; write it as the frame's blind spot and let Stage 4 resolve it. Also audit every dated constraint in the plan — a departure, a clawback window, a notice period, a lease — as its own candidate failure mode: dates people state as fixed facts are the ones that silently become causes of death.

**Narrate one compound failure.** One autopsy entry is the compound scenario: pick the two modes most likely to co-occur and narrate the interaction (the stall eats two months → cash pressure forces a bad client → the bad client eats the recovery month). The modes are not independent; treating them as independent is itself a hidden assumption. It counts within the ~7, not as an eighth.

**Don't reassure.** No closing paragraph about how this can work with careful execution. Stage 3 is where the constructive work lives; stages 1 and 2 stay cold. If they push back defending the plan, engage with the argument on the merits — don't soften the ranking to be agreeable, and don't dig in if they've actually given you new information that changes the picture.

**Tripwires need a number and a date.** "Watch engagement" is a vibe. "Fewer than 40 profile visits in the week of Nov 3" is a tripwire. Anchor the dates to their actual timeline. Every detection opportunity becomes an adversary row in the tripwires table — signal, threshold, check date, and a response decided now, not in the moment. And for the most-dangerous autopsy mode, at least one tripwire must sit early in its causal chain, before the point of no return.

## Adapting the format

**Personal decisions.** The machinery works for career moves, relocations, big purchases, family logistics — but stage 4 often has no real adversary, and cold forensic prose lands badly on someone's life. Drop or reframe stage 4 when there's genuinely no competitor, and use plainer language. If someone seems to be in distress rather than planning, the premortem is the wrong tool entirely — talk with them.

**The adversary stage stays legitimate.** Competitive moves, timing, pricing, positioning, distribution. Not harassment, deception, or anything that would be ugly if run in the other direction. If the rival is a real named person in their life, keep it strategic rather than personal.

**Scope.** Seven causes is right for a substantial plan. For something small, fewer real causes beats seven padded ones — say so rather than inventing filler. And if Stage 1 reveals the plan has already failed a pre-launch check, deliver the blocking finding instead of forcing all five stages.

## Before delivering

Run the verification checklist in [references/failure-class-checklist.md](references/failure-class-checklist.md) against the finished report. Fix what fails. Never ship a causal chain with a known weak link — rewrite the link or demote the mode down the ranking and say why. If a month-to-month link feels under ~60% plausible, that's a weak link.

## Delivering it

The full report is long, so write it to a markdown file and present it when file creation is available — people come back to these, and tripwires only work if they can find them again. Inline is fine when it isn't. Either way keep the structure identical; on a phone, tighten the prose rather than dropping sections.

After delivering, offer once to go deeper on the single most dangerous failure mode. Don't stack follow-up offers.
