# Three-Horizon Roadmap & Board Pitch

## Roadmap

*MitigationIQ has no product backlog yet, so these initiatives are derived from the strategy in this repo (M1–M5). "Supports" names the strategy component each initiative serves. For a concept, "existing capabilities" in H1 means the Lovable prototype plus customer validation.*

### Horizon 1 — Now (0-3 months)
*Quick wins. Ship with existing capabilities.*

| Initiative | Supports | Metric | Confidence |
|-----------|----------|--------|-----------|
| Pilot interviews with 10 consulting firms and state mitigation offices | Bet | ≥3 of 10 agree to pilot on a real plan cycle (kill criterion) | M |
| Run the golden dataset against the prototype and fix funding-rule errors (e.g., fire station funded from the clean-water loan) | Contract | 100% pass on rule-judged rows; golden dataset grows from 10 to 25 rows | H |
| Require a reason for every planner override, recorded in the audit trail | Guardrails | 100% of overrides captured with a reason | H |
| Kill-switch basics: AI gateway, backup provider and explanation evals | Moat | Provider swap proven in staging within 48 hours | M |
| Data-sharing and correction-sharing clauses in pilot contracts | Moat | Clauses in 100% of signed pilots | M |
| Test hybrid pricing ($150 base + $300 per package) and prepaid bundles with pilot buyers | Margin | ≥3 buyers accept hybrid pricing or bundles; packages-per-seat estimate confirmed | M |

### Horizon 2 — Next (3-9 months)
*Bets. Requires new capabilities or integrations.*

| Initiative | Supports | Metric | Confidence |
|-----------|----------|--------|-----------|
| Production optimizer and funding-rules engine (BRIC, FMA, HMGP plus 2 states), with rule citations on every eligibility statement | Bet | Portfolio-building time cut ≥50% vs. spreadsheets plus FEMA's BCA Toolkit; 100% rule-judged accuracy | M |
| Confidence tiers and a "show the math" view | Contract | Fewer portfolio exports to Excel for rechecking; override rate below half of recommendations | M |
| Grant drafting add-on, priced per package | Margin | 1–2 packages per seat per month; ≥95% of drafts pass planner review | M |
| Cascading model routing and prompt caching | Margin | AI COGS ≤$32.60/user/month; 65% / 35% cascade ratio | M |
| Funding-rule change digest ("what changed for your plan") | Moat | Rule changes reflected within 5 business days; replaces ChatGPT summaries of funding notices | M |
| ArcGIS export for council maps (partner, not build) | Moat | Share of portfolios exported to maps | H |
| Governance operations: weekly evals, monthly 1% review, override triage within 10 business days | Guardrails | 100% of overrides triaged within 10 business days | H |

### Horizon 3 — Bet (9-18 months)
*Moonshots. High uncertainty, high potential.*

| Initiative | Supports | Metric | Confidence |
|-----------|----------|--------|-----------|
| Anonymized cost benchmark across customers, starting with state offices | Moat | ≥5 states contributing cost outcomes; Network loop moves from 1/5 to 3/5 | L |
| Outcome calibration loop (estimated vs. bid vs. final costs) feeding confidence tiers | Guardrails | Projects in the >90% tier hold up at least 90% of the time | L |
| Second hazard type (wildfire or extreme heat) | Moat | Second hazard launched reusing the flood funding and cost models | L |
| Outcome-based pricing option (share of funding won), pending a 2 CFR 200 review | Margin | Legal sign-off; pilot with 1 customer | L |

## Board Pitch

**Thesis (1 sentence):**
Communities have far more flood-protection projects than money, and MitigationIQ helps the planners and consultants who decide between them build a funded, defensible plan in half the time, with every number traceable to its source.

**The case:**
1. Why now: Federal pre-disaster mitigation funding was cancelled in 2025, restored by a court and relaunched in 2026 with new priorities. Every community's funding plan is being rebuilt against new rules, while the tools in use still stop at mapping risk or checking one project's benefit-cost ratio. Nothing turns risk, costs and funding rules into a portfolio a council will approve. The same turmoil cuts both ways: unstable federal funding means unstable buyer budgets, which is why the ask is staged.
2. What's defensible: Not much yet, and we know it. Our own flywheel score is 8/20, and every compounding loop is still missing. What we have today is a head start in effort: funding-rule logic and numbers that come from a rules-based optimizer, not a language model, which general-purpose AI can't match. The moat we're building is a neutral cost benchmark across firms and communities, led by state offices, with data-sharing rights written into every pilot contract. Microsoft and Esri each see only their own customers' data. One open question: if cost outcomes turn out to be public records, the moat has to be making messy data usable, not owning the data. We check that in the first 6 weeks.
3. The economics: AI costs about $0.033 per request, or about $32.60 per user per month. At a planning case of 1–2 grant packages per seat a month, hybrid pricing ($150 base + $300 per package) runs a 94–96% gross margin. A flat $150 seat with the same AI runs 78% and drops to 57% if inference costs triple; hybrid pricing stays above 95%. These are modeled numbers: no buyer has seen a price yet, and the 5-package upside case isn't what we're pitching.

**The risks:**
1. Trust / failure modes: The front-page story is a council that applies for federal money based on our recommendation, only for FEMA to reject the project as ineligible, or a buyout in a low-income neighborhood that gets deprioritized without anyone noticing. Our safeguards:
   - Every number comes from the optimizer, and 100% of AI explanations are checked against it.
   - Eligibility statements must cite a funding rule, or they're blocked.
   - Anything below 70% confidence, or any change that affects households, goes to a named human reviewer before export.
   - The weakness: our prototype currently breaks one of its own funding rules. That's the first fix, measured by a test set growing from 10 to 25 cases.
2. Scale / governance: Costs and model quality aren't what break at 10x. What breaks is funding-rule upkeep and the human review queue, which grow with every new state, not every new user. Today's cost model budgets a quarter of one person for rule upkeep, and that's too little. The ask funds a full-time grants-policy expert, and we'll plan growth around "states supported" rather than seats. Feeding customer corrections back into the product depends on contract clauses public agencies may refuse; we'll know from the first pilots.
3. Competitive: The scenario that forces a kill is Esri bundling a "good enough" portfolio and funding module into ArcGIS, sold to the state offices that already use it, before we have 3 signed pilots. If that happens, we stop competing on the core product and become the funding-rules layer that plugs into ArcGIS. The closest competitor, Jupiter Intelligence with Arcadis, already models adaptation returns but has shown no funding-rules logic. That's the gap we have to close first.

**The ask:**
**$900K, 4 people (PM/founder, 2 engineers, 1 grants-policy expert), 9 months to 3 signed pilots**, released in two stages:
- **$150K now:** 6 weeks of validation and a first funding-rules engine for BRIC, FMA and one state.
  - **Validation:** 10 discovery calls, 5 prototype walkthroughs and pricing tests.
  - **The gate:** at least 3 of 10 target customers agree to pilot. If not, we stop and the remaining $750K is never spent.
- **$750K once the gate is met:** the production optimizer and rules engine, the confidence and "show the math" views, the grant drafting add-on, and pilots with at least one state office and one consulting firm.

**What we get:** an answer to whether planners accept the recommendations, a real willingness-to-pay figure, the measured cost of rule upkeep per state, and 3 signed pilots with data-sharing terms.

**What gets paused:** the cross-customer benchmark beyond pilot customers, a second hazard type, and outcome-based pricing. None of them starts until the core is validated.

## M1 Baseline vs. Now
*Your 3-sentence AI strategy from Module 1 vs. what you'd say now:*

**M1 baseline:**

**Now:**

## AI Evaluation
*Generated with the course's AI strategy evaluation prompt, run against the M1–M5 summary in `README.md`.*

**Bet Validation**, Score: 2/5
- **Strengths:**
  - The kill criteria are concrete and measurable. "Fewer than 3 of 10 agree to pilot" is a real line to walk away at.
  - The problem framing is sharp: many tools map risk, but few turn it into a defensible decision about money.
  - The prototype makes the idea tangible.
- **Gaps:**
  - The bet rests on conviction, not evidence. There are no interviews, no usage data and no buyer signals; every number is synthetic or estimated.
  - The core hypothesis is never stated in falsifiable form. Something like: *planners will adopt an optimizer's recommendation as the starting point for their funding plan, and accept most of it.*
  - "Why now" leans on federal funding turmoil, which is a double-edged argument: an unstable BRIC also means unstable budgets for the very buyers you're selling to.
- **Recommendation:** Validate within 4–6 weeks, not months. Run 10 discovery calls, and put the Port Halden prototype in front of 5 planners. Ask each one whether they would take the recommended portfolio to council. Record whether they would accept, change or reject it.

**Capability Assessment**, Score: 2/5
- **Strengths:**
  - Keeping the LLM away from the numbers keeps AI risk low.
  - The model tiers, kill switch and degraded mode are sensible.
- **Gaps:**
  - The hard capabilities aren't AI at all. They are:
    - a constrained optimizer that handles interactions between projects
    - a funding-rules engine covering federal programs and 50 different state programs
    - turning messy PDF hazard mitigation plans into structured data
  - The cost model budgets a quarter of one person for funding-rule upkeep. That's likely far too little once the product covers several states.
  - Several dependencies could block progress:
    - **Hosting certification:** StateRAMP or FedRAMP can take months.
    - **FEMA program stability:** the programs keep changing.
    - **Data quality:** the risk data and each community's plan may not be good enough.
  - No team or domain experts are named for operations research or grants policy.
- **Recommendation:** Build the rules engine for BRIC, FMA and one state before anything else, and track the hours it takes. That number determines whether funding-rule upkeep is affordable, which is one of your kill criteria.

**Impact Analysis**, Score: 3/5
- **Strengths:**
  - There are clear metrics: time saved, package revenue and NRR (net revenue retention) through funding windows.
  - The upside from hybrid pricing is quantified, along with a range.
- **Gaps:**
  - **Revenue and value come from different places.** Most revenue comes from grant drafting, the add-on that `kill-switch.md` calls not defensible. The core product's value, better decisions about public money, is mostly monetized through the $150 seat.
  - **The market size is never stated.** 250 seats at $150 is about $450,000 a year in base fees. How many mitigation consultants and state staff exist in total?
  - **Impact may plateau.** Plan cycles run 5 years, so usage could be bursty rather than compounding.
  - **Opportunity cost isn't addressed.** For example, a narrower tool for state offices only could be an alternative.
- **Recommendation:** Size the market from the bottom up: how many state offices, how many consulting firms, and how many planners in each. Then check whether the core product can stand on its own without grant drafting.

**Defensibility Check**, Score: 2/5
- **Strengths:**
  - The analysis is honest: the flywheel scores itself 8/20.
  - Funding-rule logic and traceable numbers are real barriers to a general-purpose model.
  - A neutral benchmark across customers is something Microsoft structurally can't offer.
- **Gaps:**
  - **Every compounding loop is missing.** At launch, the moat is just a lead in effort.
  - **Microsoft is a 12-month threat.** Copilot plus each firm's own spreadsheets is a "good enough" threat within 12 months, and Esri owns the buyer relationship.
  - **The cost-data moat may not be proprietary.** Public agencies' cost data may be subject to public-records requests, so a competitor could request it too.
  - **Switching costs depend on becoming the system of record,** which hasn't been proven.
- **Recommendation:** Find out now whether cost outcomes are public records in your first two target states. If they are, rebuild the moat around making messy data usable and around funding-rule expertise, not around exclusive access to data.

**Pricing Alignment**, Score: 3/5
- **Strengths:**
  - Charging per package matches the costly, occasional work.
  - The structure holds up when a power user does 10× the average volume or inference costs triple. Margin stays above 95% in each case.
  - The Maximize posture is well reasoned.
- **Gaps:**
  - There's no willingness-to-pay signal at all. The $150 seat is made up for the exercise, and $300 per package is based on an estimate of hours saved.
  - Per-seat pricing doesn't fit government buyers well. State offices have few seats and buy per program or per plan.
  - The 98% margin headline comes from the 5-package case, which is itself flagged as an upper bound.
- **Recommendation:** Test two structures with pilot buyers: one priced per community plan per year and one per seat plus packages. Lead every pitch with the 1–2 package case.

**Trust & Reliability**, Score: 4/5
- **Strengths:**
  - This is the strongest part of the strategy:
    - Rule-checked targets are 100%, and every production explanation gets a number check.
    - Confidence is measured, not self-reported by the AI.
    - Users can see when the AI is uncertain.
    - Each kind of review has a named reviewer.
  - The adversarial tests go after the right risks for this domain.
- **Gaps:**
  - The golden dataset has only 10 rows.
  - There's no promise on uptime or availability.
  - Partner red-team findings are missing.
  - The prototype appears to break its own funding rule, the fire station funded from the clean-water loan, so the design is ahead of what's been built.
- **Recommendation:** Grow the dataset to 25 rows now and run it against the prototype. Publishing the pass rate, failures included, makes a stronger sales story than the targets alone.

**Governance & Scale**, Score: 3/5
- **Strengths:**
  - The governance policy is specific. Owners are named and the review cadence has four layers.
  - Agents are tightly limited, and the escalation triggers cover the Air Canada- and Samsung-style risks.
  - The broken feedback loop was found, and there's a concrete plan to fix it.
- **Gaps:**
  - **Growing to new states is what breaks.** Funding-rule upkeep and the review queue grow with each new state, not each new user.
  - **The shadow AI audit is simulated,** so its signals aren't real yet.
  - **Feeding corrections back** depends on contract clauses public agencies may not accept.
  - **There's no process for changing models** beyond running evals before release.
- **Recommendation:** Model the cost of adding each new state, in rules, reviewers and evals. Make "states supported" the unit you plan scale around, not seats.

**Gap Identification**, Score: 2/5
- **Weakest components:** the Bet, because it has no evidence behind it, and the Moat, because every loop is missing.
- **Untested assumptions:**
  - willingness to pay
  - packages per seat
  - planner acceptance of recommendations
  - the cost of funding-rule upkeep
  - whether public agencies will share data
  - procurement speed
- **The board question you can't answer:** *"Who has said yes, and what did they say they'd pay?"* A sharper version: *"If cost outcomes are public records, what exactly is proprietary?"*
- **Biggest 6-month risk:** government sales cycles. If a pilot takes 6–12 months to procure, you can't test your kill criteria in time, and you'll run low on money while you wait.

---

- **Overall Score:** **3/5.** Well designed, but unvalidated. The Contract and Guardrails are well ahead of the evidence for the Bet and the Moat.
- **Biggest Risk:** No real customer commitment or willingness-to-pay data, combined with slow government buying cycles. The strategy could be internally consistent and still have no buyer.
- **Top 3 Actions:**
  1. **Validate in 6 weeks:** 10 discovery calls and 5 prototype walkthroughs, testing three things: whether planners accept the recommendations, what buyers would pay (seat, plan or package), and whether they'd share data.
  2. **Prove the hard part:** build the funding-rules engine for BRIC, FMA and one state, measure the upkeep hours, and fix the prototype's eligibility error by running the 25-row golden dataset against it.
  3. **Find a faster way to buy, and size the market:** look for a path around slow procurement, such as consultant-led pilots or cooperative purchasing contracts. Then size the market from the bottom up, so the board pitch rests on real market numbers rather than the 5-package case.
