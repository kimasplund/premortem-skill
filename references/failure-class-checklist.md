# Failure classes and pre-delivery checklist

Load this when generating failure modes (Step 2) and again before delivering. The generation pass and this checklist stay backstage — only the one-line cut log appears in the report.

## Part 1 — Failure classes (generation checklist)

Generate at least one candidate per class, or write an explicit "N/A — [reason]" for the class.

| Class | Prompt question |
|---|---|
| Market / demand | Does the demand they counted on actually exist, at the price they named? |
| Cash / runway | Recompute their runway post-tax, post-business-costs, with payment timing — what number do you get? |
| Delivery / execution & capacity | Who does the work, in which hours, once admin and overhead are priced in? |
| Pricing / unit economics | Does the price survive contact with real scope, real costs, real conversion? |
| Legal / contractual | What did they sign (or their counterparties sign) that they haven't read? |
| Concentration / dependency | What single client, channel, platform, or person carries more weight than it should? |
| External actors | Who with their own agenda — competitor, vendor, employer, regulator — can move first? |
| Human / psychological | Which motivation, stamina, or conflict cost is being spent but not budgeted? |
| Timing / sequencing | What is scheduled to happen before its prerequisite can plausibly complete? |
| Unknown / omission | What did the plan never price, never staff, never schedule, never mention? |

**Personal-decision variants:** for career/relocation/family plans, read *legal/contractual* as paperwork and contingencies (clawbacks, leases, custody, insurance) and *market/demand* as fit (does the new role, city, or school actually suit the people involved).

## Part 2 — Diversity dimensions

Each surviving mode must differ from every other in at least **2** of:

1. Cause domain (which Part-1 class it lives in)
2. Who triggers it (them, a client, a competitor, the market, chance)
3. Timing of onset (day one vs. month three vs. past the horizon)
4. Detectability (loud and early vs. silent until late)
5. Reversibility (recoverable vs. point of no return)

**Merge rule:** two modes sharing cause domain + trigger + timing are one mode. Merge them and regenerate the freed slot.

**Worked example:** "clients churn early" and "the anchor pauses in January" share domain (concentration), trigger (the client), and timing (early months) — one mode: "an anchor pauses at its January budget reset." The freed slot goes to a class with no survivor yet.

## Part 3 — Cut criteria, cut log, commitment grades

**Cut rule (asymmetric):** drop a candidate only if it is low-probability AND low-danger AND duplicates another mode's mechanism. A low-probability, high-severity, non-mitigable mode stays. Never cut a household or dependent single point of failure — a partner's income, health coverage, visa, or care arrangement the plan silently stands on — for low probability alone: keep it, or fold it into another mode with its replacement cost priced.

**Stop rule:** stop generating when two consecutive candidates fold into existing modes.

**Cut-log format (the only visible trace):** one line under the autopsy —
`**Considered and cut:** X (folded into #3), Y (<2%, recoverable).`

**Commitment grades** — grade the commitment you actually hold from each person the plan depends on, not the one narrated:

| Grade | Meaning |
|---|---|
| Champion | Spends their own capital — political, financial, reputational — to make it happen |
| Endorse | Says yes and will sign; acts when asked |
| Accept | Agrees, then silence does the killing — the pocket veto |
| Comply | Goes along while it costs nothing; defects at the first cost |

Anything below Endorse is a failure mode or a pre-launch checklist item: convert it to paper before launch.

**Optional, high-stakes only:** run a dual read — one cold pass over the plan as written, one reference-class pass over the numbers alone — and merge where they agree. Doubles runtime; not the default.

## Part 4 — Pre-delivery verification checklist

Run against the finished report. Fix what fails; do not ship a report that fails a line.

1. Every cause passes the stranger-paste test (couldn't be pasted into a stranger's premortem unchanged).
2. Steelman present; a genuine advocate would recognize their own case in it.
3. All entries past tense from the future; each month caused by the prior month.
4. No causal chain shipped with a known weak link (~60% plausibility floor per link).
5. Percentages on the coarse ladder (~5/~10/~15/~20/~30/~40), each with a justification clause; shares-of-failure note present; sums to ~100; top mode ≤ ~40%.
6. Top two modes carry a reference-class anchor plus a disanalogy line.
7. At least 1 omission mode, 1 success-kills mode, 1 frame-blind slot, 1 compound mode.
8. Diversity test passed (Part 2); cut log present.
9. I×F table consistent with the most-likely / most-dangerous picks; any divergence explained in prose.
10. Hidden assumption found by convergence, or convergence explicitly stated as absent.
11. Every rebuild change names the mode it closes + its cost; decision rule present for any irreversible step; residual risk stated.
12. Adversary profiled (motivation / resources / constraints / best alternative); kill chain dated and sequenced; each move has a detection opportunity.
13. Every tripwire: metric + threshold + check date anchored to their timeline + if-tripped action; adversary rows present; most-dangerous mode has an early-chain tripwire; kill condition is a combination, not a single signal.
14. No reassurance paragraph anywhere; stages 1 and 2 stay forensic.
