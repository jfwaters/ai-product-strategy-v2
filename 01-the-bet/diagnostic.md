# Three-Axis Vulnerability Diagnostic

## Product

**Product:** MitigationIQ, a B2B/B2G planning workspace that helps communities decide which disaster-mitigation projects to fund, with which money, and why. It turns hazard risk data, project costs and funding rules into a recommended, explainable project portfolio. *(Early-stage course concept; synthetic data only.)*
**Your Role:** Product Manager / concept owner

**Target users:** resilience and engineering consulting firms and state hazard mitigation offices (launch customers); the analyst or planner who builds portfolios (primary user).
**AI archetype:** Oracle (dominant), Copilot (secondary). Deterministic models and constrained optimization produce the numbers; the LLM explains, flags gaps and answers "why?" and "what if?".

---

## Scores

### Contextual Moat — 3/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:** The context MitigationIQ holds is hard for a generic tool to rebuild: the community's five-year hazard mitigation plan, project interactions, funding eligibility and cost-share rules, phasing, and an audit trail that decisions are defended against. Once a community runs a full plan cycle in it, switching means rebuilding that record and losing its history. The moat is not real yet, though. Until a customer completes a cycle, a consultant could leave in a weekend and go back to spreadsheets plus FEMA's BCA Toolkit. Funding-rule logic is valuable but public, and rules change (BRIC was cancelled, restored and relaunched between 2025 and 2026), so the logic needs constant upkeep to stay a moat.

**Named attacker:** A large engineering consulting firm (a launch-customer type) building an in-house portfolio tool on top of Excel and Microsoft Copilot.

---

### Data Advantage — 2/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:** Today the inputs are public (FEMA National Risk Index) or licensed from vendors, so there is no unique data at launch. The planned flywheel is real but slow: tracking estimated vs. bid vs. final cost and schedule outcomes across projects would build a proprietary calibration set no one else has, but those outcomes take 1–3 years to resolve, and proving avoided losses takes much longer. Until enough customers record funded and built projects, the data advantage is a plan rather than an asset.

**Named attacker:** Esri. It already holds communities' hazard and asset data in ArcGIS and could add a portfolio and funding module to an install base MitigationIQ has to win one customer at a time.

---

### Platform Exposure — 3/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

**Score rationale:** A general-purpose model can't ship the hero feature tomorrow: the recommendation comes from constrained optimization over funding rules, cost shares and project interactions, not from an LLM, and buyers need traceable numbers they can defend to councils and funders. The niche is too small and too regulated for OpenAI or Google to target directly. The realistic platform exposure is Microsoft: general Copilot improvements in Excel and Word could give consultants a "good enough" version over 18–24 months, though it would be weaker on rule-constrained optimization and traceable numbers. Being model-agnostic (any risk data source, any LLM for explanation) and handing off to the BCA Toolkit instead of competing with it keeps pivot speed high.

**Named attacker:** Microsoft, through Copilot in Excel, Word and Teams.

---

**Overall vulnerability:** 8/15
**Your crack (weakest axis):** Data Advantage (2/5)

## Top Vulnerability
The data flywheel doesn't exist at launch and takes years to compound, so an incumbent with the install base (Esri) could add a "good enough" portfolio module before MitigationIQ becomes the system of record for the plan cycle. Esri is the largest threat; the most urgent is Jupiter Intelligence with Arcadis, which already models adaptation options and builds investment cases.

## Confidence Level
**M.** The problem is real and underserved: many tools map risk, few turn it into a defensible, funding-constrained decision. But the moat depends on winning the plan-cycle workflow early and on customers recording outcomes long enough for the cost-and-schedule data loop to pay off.
