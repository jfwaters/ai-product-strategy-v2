# MitigationIQ

A B2B/B2G planning workspace that helps communities decide which disaster-mitigation projects to fund, with which money, and why. It turns hazard risk data, project costs and funding rules into a recommended, explainable project portfolio. *(Early-stage course concept; synthetic data only.)*

> **The bet:** MitigationIQ helps resilience consultants and state mitigation offices turn hazard risk, project costs and fragmented funding rules into a defensible, explainable project portfolio, because federal mitigation funding was reset in 2025–26 and communities have far more candidate projects than money.

Product context: [`MITIGATIONIQ.md`](MITIGATIONIQ.md)

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|-------------|
| **The Bet** | M1 | [x] | `01-the-bet/` |
| **The Moat** | M2 | [x] | `02-the-moat/` |
| **The Margin** | M3 | [x] | `03-the-margin/` |
| **The Contract** | M4 | [x] | `04-the-contract/` |
| **The Guardrails** | M5 | [x] | `05-the-guardrails/` |
| **The Pitch** | M6 | [x] | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:** An explainable, funding-constrained portfolio recommender for disaster mitigation. A deterministic optimizer produces the numbers; AI explains them.
- **AI Value Archetype:** Oracle (dominant), with a Copilot layer for "why?" and "what if?" questions.
- **Vulnerability Scores:** Moat 3/5 · Data 2/5 · Platform 3/5 (8/15)
- **Top Risk:** The data flywheel doesn't exist at launch, so an incumbent with the install base (Esri) could ship a "good enough" portfolio module before MitigationIQ becomes the system of record for the plan cycle.
- **Confidence:** M
- **Prototype:** https://mitigation-iq.lovable.app/
- **Kill Criteria:** Fewer than 3 of 10 target customers agree to pilot; planners override most recommendations; less than half the time saved vs. spreadsheets plus FEMA's BCA Toolkit; funding rules can't be kept current affordably; or customers won't record project cost outcomes.

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in 6 months.**

- **Data Flywheel Score:** 8/20 (Correction 3 · Preference 2 · Domain Context 2 · Network 1)
- **Weakest Loop:** Network (1/5)
- **Top Encroachment Threats:** Esri (largest: bundles a portfolio module into ArcGIS); Jupiter Intelligence with Arcadis (most urgent: already models adaptation ROI); Microsoft (90-day attack via Copilot on each firm's own cost history).
- **Encroachment Defense:** A neutral, anonymized cost benchmark across firms and communities, led by state offices, with data-sharing rights written into pilot contracts. Plus traceable numbers and current funding rules, which general-purpose AI can't match.
- **Vendor Portability:** Partial. The LLM never produces the numbers, and degraded mode keeps recommendations working without it, but abstraction, fallback routing and evals aren't built yet.

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Gross Margin (current):** 78.3% (AI added to a flat $150 seat)
- **Gross Margin (AI-adjusted):** 98.0% at 5 packages per seat; 94–96% at the 1–2 package planning range
- **Pricing Model:** Hybrid (base fee + metered work), Maximize posture
- **Pricing Today → Tomorrow:** $150/user/month flat seat *(assumed; no real price yet)* → $150/user/month base + $300 per grant application package
- **Total AI COGS / unit:** ~$32.60/user/month (~$25.10 without grant drafting); blended ~$0.033 per AI request
- **Cascading Strategy:** Small-tier triage handles 65% of requests; 35% escalate to a mid tier for rationales and harder chat; ~1% reach a frontier model, mostly grant drafts.
- **Net Margin Shift:** +19.7 points and +$375K/month gross profit at 5 packages per seat (250 seats); +$0.9–1.8M/year at the 1–2 package planning range. Each package per seat adds ~$75K/month.
- **Break-even at:** ~20 seats to cover fixed COGS (funding-rule upkeep, ~$2,500/month) from base fees alone. Full operating break-even isn't modeled yet.

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **Reliability Target:** 100% on rule-judged checks (budget, eligibility, benefit-cost math); 95% on LLM-judged explanation quality; 0% wrong numbers in explanations.
- **Golden Dataset:** 10 rows: 2 edge cases, 3 adversarial (growing to ~300 by launch). Partner review *(simulated)* found 4 coverage gaps: grant drafting, messy inputs, fairness, and funding-rule changes.
- **Confidence UX:** Three tiers (>90%, 70–90%, <70%), measured from scenario stability, input verification and an explanation number check, not the AI rating itself. Below 70% goes to human review and blocks council export.
- **HITL Architecture:** Confidence <70%, a failed number check, a safety flag, or any grant draft → routed to a named reviewer (customer engineer, grants lead or planner; MitigationIQ policy analyst or on-call PM). Corrections feed the weekly golden dataset audit.
- **Failure Mode Coverage:** Adversarial tests for prompt injection in imported plans, pressure to state unsupported numbers, and requests to break funding rules. Red-team finding *(simulated)*: a portfolio can stay "confident" after a funding-rule change, because every check passes against outdated rules. Fix: stamp each portfolio with its rule version, and downgrade confidence and lock council export when rules change.

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales, and what compounds.**

- **Compounding System:** Five loops (planner overrides, outcome calibration, cross-domain transfer, cost benchmark, funding-rule upkeep); four compound, and all are missing until launch. Broken loop: override reasons have no data right, owner or deadline to reach MitigationIQ. Fix: a correction-sharing clause in pilot contracts and weekly triage by the policy analyst.
- **Governance Posture:** Covers all AI explanations, the grant drafting add-on, and AI's use of optimizer output and funding rules.
- **Autonomy Boundaries:** Optimizer runs, explanations and sandbox "what if?" reruns are automatic; grant drafts are draft-only; adopting or exporting a portfolio needs human approval; submitting applications or changing numbers is never automatic.
- **Escalation Triggers:** Confidence <70%, a failed number check, a safety flag, every grant draft, changes affecting households or vulnerable neighborhoods, funding-rule changes, and any uncited eligibility claim.
- **Audit Cadence:** Real-time number checks; weekly golden dataset eval; monthly human review of a 1% sample and all escalations; quarterly policy and fairness review.
- **Shadow AI Audit (user-side):** *(simulated)* 5 workarounds, 3 build candidates, ~$40/user/month adjacent spend. Top build: an in-product digest of funding-rule changes.
- **Agent Boundaries:** The Grant Drafting Agent drafts only and can't submit, contact agencies or change numbers. The Scenario Chat Assistant reruns the optimizer on a sandbox copy only.
- **Regulatory Exposure:** EU AI Act not in scope (US public sector; likely limited risk if it entered the EU). US: 2 CFR 200, FEMA benefit-cost requirements, state public-records laws, possibly state AI laws, Title VI. Sensitive data: property-owner details and critical-infrastructure vulnerabilities.

→ Details: [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

**How you get this funded, shipped, and adopted.**

- **Horizon 1 (Now, 0–3 months):** Validate and harden the prototype: pilot interviews (≥3 of 10 agree to pilot), golden dataset fixes, required override reasons, kill-switch basics, data-sharing clauses and a pricing test.
- **Horizon 2 (Next, 3–9 months):** Build the real product: production optimizer and funding-rules engine, confidence tiers and "show the math," the grant drafting add-on, model routing, a funding-rule change digest, an ArcGIS export, and governance operations.
- **Horizon 3 (Bet, 9–18 months):** Compounding bets: a cross-customer cost benchmark, outcome calibration, a second hazard type and outcome-based pricing.
- **Board Narrative:** Communities have far more flood-protection projects than money, and MitigationIQ helps the planners and consultants who decide between them build a funded, defensible plan in half the time, with every number traceable to its source. Pitched to founders / an early-stage funding committee.
- **Ask:** $900K, 4 people (PM/founder, 2 engineers, 1 grants-policy expert), 9 months to 3 signed pilots. $150K funds 6 weeks of validation; the remaining $750K is released only if ≥3 of 10 target customers agree to pilot.
- **Key Strategic Change:** From "use AI to give planners better answers and more value per mitigation dollar" (M1) to a specific bet: an AI that explains the numbers but never invents them, defended by funding-rule expertise and a neutral cost benchmark, priced per package, and gated on customer evidence. In practice: lead with state offices, staff funding-rule upkeep full-time, and release $750K only after the week-6 pilot gate. *(AI evaluation: 3/5 overall; weakest areas are Bet evidence and the Moat.)*

→ Details: [`06-the-pitch/`](06-the-pitch/)
