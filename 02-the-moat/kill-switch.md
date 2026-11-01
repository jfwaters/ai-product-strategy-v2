# Kill Switch Audit

> **Note:** MitigationIQ is a product concept and hasn't chosen a primary LLM provider yet, so `[primary vendor]` remains a placeholder below. This audit assesses the launch design and treats anything not yet specified as not built. It covers LLM vendors only. File and function names are illustrative, since no production code exists.

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | The launch design assumes one LLM vendor, not yet chosen, for explanations, gap flags, scenario chat and draft justifications. Optimizer and risk figures don't depend on it. No backup vendor is planned yet. | M | By Friday, list every planned LLM call with its vendor, model and estimated monthly cost in `docs/ai-vendors.md`, and set up API access with a primary and a backup vendor. |
| **Abstraction** | The product is positioned as model-agnostic, but no generic interface has been built or proven. | M | By Friday, move all LLM calls behind `ai_gateway.explain()`, `ai_gateway.flag_gaps()` and `ai_gateway.chat()`, with no vendor SDK imports outside `ai_gateway/`. |
| **Routing** | Every task goes to one model, with no fallback. Portfolio planning isn't real-time, so an outage delays explanations but not recommendations. | M | Add `ai_routes.yaml` mapping each task to a primary and fallback model, then send `chat` to the backup in staging and confirm it works. |
| **Eval** | There are no automated tests. A replacement model could misstate a number or drop a source in a council rationale, and nothing would catch it. | H | Build `evals/explanations/` with 25 Port Halden scenarios. Fail any model whose rationale includes a number that doesn't match optimizer output or omits a source trace. |

## Portability Score
**Partial.** Because the LLM never produces the numbers, a provider swap puts only the explanation layer at risk, and degraded mode keeps recommendations available with no LLM at all. But with no abstraction, fallback or evals built yet, a swap in 48 hours would be possible but unproven. Finishing the four actions would move this toward Ready.

## If [primary vendor] doubles pricing tomorrow:
1. **Hours 0–4:** Pull usage and cost by task to see what's driving spend.
2. **Hours 4–24:** Move lower-stakes tasks, chat and gap flags first, to the backup model through `ai_routes.yaml`.
3. **Hours 24–48:** Run the evals on the backup model and switch council rationales only if they pass. If they fail, keep the current vendor for rationales and absorb the cost temporarily.
4. **Throughout:** Recommendations and numbers don't change, so customers shouldn't see any difference in the results.

This response only works once the Eval action is done. M3 will show how much this cost shock matters to margin.

## If [primary vendor] ships a competing product:
**Defensible:**
- The deterministic optimizer, with its rule-constrained funding logic
- Traceable numbers and an audit trail that planners can defend
- The plan-cycle system of record, including saved scenarios and override reasons
- Cost and schedule outcome data, as it builds
- Neutrality: MitigationIQ can use any model or risk source, which a vendor's own product can't credibly offer

**Not defensible:** Plain-language explanations, funding-rule summaries and scenario chat. A vendor can match these quickly, so they shouldn't be what MitigationIQ sells.
