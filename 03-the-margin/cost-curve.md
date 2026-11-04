# Cost Curve & Pricing Strategy

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | | |
| Inference (cascading/triage) | | |
| Infrastructure | | |
| Data/storage | | |
| Human-in-the-loop | | |
| **Total AI COGS** | | |

## Cascading Strategy
<!-- Cheap model → frontier model routing logic -->

**Triage model:**
**Frontier model:**
**Routing rule:**
**Expected cascade ratio:**

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
