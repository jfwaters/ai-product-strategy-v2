# Cost Curve & Pricing Strategy

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | $8.50 | Mid tier: council rationales, "why?" and "what if?" answers, scenario comparison. ~170 requests at $0.05. |
| Inference (cascading/triage) | $7.83 | Small-tier triage: $0.33 (~325 requests at $0.001). Frontier escalations and grant drafts: $7.50 (5 drafts at $1.50, range $6–$15). |
| Infrastructure | $3.00 | Optimizer compute $1.00; app hosting, AI gateway and monitoring $1.50, including a premium for government-grade hosting; eval runs $0.50. |
| Data/storage | $0.75 | Plans, scenarios, audit trail, documents and LLM logs, with long retention for public records. Public risk data only (e.g., FEMA National Risk Index). |
| Human-in-the-loop | $12.50 | Funding-rule upkeep $10.00 (0.25 FTE policy analyst, ~$2,500/month across 250 users); quality checks on 1% of rationales and drafts $2.50. |
| **Total AI COGS** | **~$32.60** | **~$25.10 without the grant drafting add-on.** ~$22.60 if funding-rule upkeep is treated as R&D instead of COGS. |

### Features → Tiers → Blended Cost

| Feature | Complexity | Model Tier | Cost/Req | Volume % | Weighted |
|---|---|---|---|---|---|
| Gap flags, input checks and simple chat answers | Simple | Small | $0.001 | 65% | $0.0007 |
| Council rationale, "why?" and "what if?" answers, scenario comparison | Medium | Mid | $0.05 | 34% | $0.017 |
| Grant application drafting (Killer add-on) | Complex | Frontier | $1.50 | 1% | $0.015 |
| **Blended** | | | | **100%** | **~$0.033** |

Cost per request = typical tier pricing × estimated tokens per request:
- **Small:** ~3K input / 300 output tokens at $0.05–$0.25 / $0.40–$1.50 per 1M tokens (e.g., Claude Haiku 5.5, Gemini 3.1 Flash-Lite, GPT-5 nano)
- **Mid:** ~15K input / 1.5K output tokens at $2–$2.50 / $10–$15 per 1M tokens (e.g., Claude Sonnet 5.5, GPT-5.4)
- **Frontier:** ~200K input / 20K output tokens over ~10 agent steps at $4–$10 / $20–$50 per 1M tokens (e.g., Claude Opus 5.5, Claude Fable 5.1, gpt-6-astra)

**Assumptions:**
- 500 AI requests per active user per month; 1% reach the frontier tier, about 5 grant drafts per user per month.
- 250 active users, which sets the per-user share of infrastructure and funding-rule upkeep.
- Vendor-neutral tier pricing, since no primary LLM provider has been chosen. Claude prices are Anthropic's published rates as of October 2026; other vendors' prices come from third-party comparisons and are unverified.
- No prompt caching. Caching the shared portfolio context could noticeably reduce mid-tier cost.
- The optimizer uses ordinary compute, not an LLM, so it's counted under Infrastructure.
- Public risk data only; licensed vendor hazard data would add significantly, or customers might bring their own license.
- Customers' planners review grant drafts, so that review time isn't MitigationIQ's cost.
- Loaded cost of ~$120K/year for a policy analyst and $60/hour for reviewers.

**To validate:**
1. **Funding-rule upkeep:** hours per month to keep BRIC, FMA, HMGP and state program rules current. This is the largest cost line.
2. **Year-one user count:** at 50 users, fixed costs per user roughly quintuple; at 1,000, rule upkeep falls to $2.50 per user.
3. **Requests per user per month:** real usage from pilot logs, likely seasonal around plan updates and funding windows.
4. **Grant drafts per user:** at 2 per month instead of 5, total COGS drops about $4.50, to roughly $28.10.
5. **Tokens per grant draft:** run one prototype draft end to end to confirm the frontier cost.
6. **Hosting requirements:** whether state customers require certified government cloud hosting (e.g., StateRAMP or FedRAMP).
7. **Small-model quality and sampling rate:** whether small-model answers pass evals at a 65% triage share, and whether 1% quality sampling catches errors before they reach a council or funder.

## Cascading Strategy
<!-- Cheap model → frontier model routing logic -->

**Triage model:** A small-tier model (e.g., Claude Haiku 5.5 or a Gemini Flash-Lite-class model) that sorts every free-form request and handles the simple ones itself.
**Frontier model:** A frontier-tier model (e.g., Claude Opus 5.5 or a GPT-6-class model), used only for grant drafting and escalations. A mid-tier model sits in between for council rationales and harder chat answers.
**Routing rule:** Route by task type first: rationales go to the mid tier and grant drafts to the frontier tier. Chat goes to triage; questions answerable from optimizer output or the glossary stay on the small model, and questions that reason across scenarios or funding rules move to the mid tier. A mid-tier answer that fails the `kill-switch.md` eval check (a number that doesn't match the optimizer, or a missing source) escalates to the frontier tier.
**Expected cascade ratio:** 65% / 35% (triage handles 65%; 35% escalates, with ~1% of all requests reaching the frontier tier, mostly grant drafts).

## Pricing Model

**Current pricing:**
**Proposed AI pricing:**
**Model:** seat-based / usage-based / outcome-based / hybrid

### Packaging Decision

| | Feature | Why |
|---|---|---|
| **Leader** | Funding-constrained portfolio recommendation | What customers come for: which projects to fund, from which sources and in what order (workflow steps 2–4), produced by the deterministic optimizer. |
| **Filler** | AI explanation layer: council rationale, gap flags, "why?" and "what if?" chat, scenario comparison, BCA Toolkit export | Light, low-cost LLM features that make each portfolio more valuable. Safe to bundle, since degraded mode already treats them as separable. |
| **Killer** | Grant application drafting: an agent workflow that assembles a program-specific application package (BRIC, FMA or HMGP) for a funded project, for human review | Long, multi-step generation with heavy inference, used at a different moment: during a funding window, after planning is done. |

**% of users using the Killer:** ~25–35% (estimate)
**Decision:** Add-on, priced per application package. The unit of charge matches the unit of value, and consultants who submit many applications aren't subsidized by everyone else.

**Assumptions:**
- The Leader is the core intelligence even though it isn't LLM-generated, consistent with the rule that the LLM never produces the numbers.
- Well over 70% of users touch at least one Filler feature, since every recommendation comes with a rationale.
- Applications are drafted mainly by consultants and some local planners; state offices review applications rather than write them.
- Grant drafting is a later add-on for human review, not automated submission, which stays out of MVP scope.

**To validate:**
1. **Killer usage rate:** ask pilot customers how many users prepare applications themselves. If consultants dominate the user base, usage could pass 70%, which would favor bundling.
2. **Chat usage on its own:** if under 70%, the rule would make chat an add-on; keep it bundled anyway because its cost is low and explainability is core.
3. **Willingness to pay per application:** whether consultants can pass the cost to clients, and whether state and local procurement rules allow per-application pricing.
4. **Defensibility:** `kill-switch.md` lists draft justifications as not defensible, so the add-on needs to rely on funding-rule logic and the audit trail to avoid being commoditized.
5. **Inference cost per application:** needed for the Cost Model above.

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | | |
| Heaviest segment doubles | | |
| Model provider raises prices 50% | | |

## Board One-Pager
<!-- Before/After: Old SaaS revenue vs. AI usage revenue for your product -->

**Before (traditional SaaS):**
**After (AI-enabled):**
**Net margin shift:**
