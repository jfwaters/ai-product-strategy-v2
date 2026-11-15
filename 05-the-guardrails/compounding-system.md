# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| **Recursive Learning:** planner overrides | Planner overrides with required reasons (e.g., "council rejected this," "cost estimate is outdated"), plus reviewer corrections | Updated model inputs and funding rules, after human review, and new golden dataset rows | Y | missing |
| **Outcome calibration** | Estimated, bid and final costs and schedules for funded projects | Tighter cost ranges and better-calibrated confidence tiers | Y | missing |
| **Cross-Domain Transfer** | Costs, project interactions and funding results from flood projects | Starting estimates for other hazards (wildfire, heat) and new regions | Y | missing |
| **Network Intelligence:** cost benchmark | Anonymized cost outcomes pooled across customers, starting with state offices | A neutral benchmark showing each customer how its estimates compare with similar projects | Y | missing |
| **Funding-rule upkeep** | FEMA and state funding notices and rule changes | Current eligibility and cost-share rules, and rescored portfolios | N | missing |

*All loops are missing because MitigationIQ is a concept and nothing is shipping yet. Funding-rule upkeep keeps the product accurate but doesn't make it smarter with use, so it's a feature, not a flywheel.*

**Broken loop identified by partner:** Recursive Learning. Override reasons and engineer corrections are captured in each customer's audit trail, but there's no data right, owner or deadline for moving them into MitigationIQ's golden dataset and funding-rule reviews. The corrections are recorded, then thrown away.
**Fix plan:**
1. **Pilot contracts include a correction-sharing clause:** anonymized override reasons and corrections flow to MitigationIQ for product improvement.
2. **Owner:** the funding-rule policy analyst triages all override reasons weekly.
3. **Deadline:** each override is resolved within 10 business days as one of three outcomes: rule fix, new golden dataset row, or no action with a recorded reason.
4. **Tracking:** the weekly eval report shows the count of corrections turned into fixes.

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

Planner override reasons and engineer corrections sit in each customer's audit trail. Unless they're routed to MitigationIQ's policy analyst and golden dataset, the product never learns from real use. And without data-sharing rights, each customer's cost outcomes stay isolated, so the benchmark never forms.

## Governance Policy

*MitigationIQ v1.0*

**Scope:** All AI features in MitigationIQ: AI explanations (council rationales, gap flags, "why?" and "what if?" chat) and the grant drafting add-on. It also covers the optimizer and funding rules wherever AI reads or explains their output. Excludes MitigationIQ's internal analytics and sales tools, which fall under a separate internal-use policy.

**Autonomy boundaries:**
- **Runs automatically:** optimizer runs, rationale drafts, gap flags, chat answers, and "what if?" reruns on a sandbox copy that never overwrites a saved portfolio.
- **Draft only:** grant application packages and council-ready rationales.
- **Needs human approval:** adopting a portfolio as the plan of record, exporting "Ready for council," overrides (with a required reason), applying funding-rule changes (the policy analyst approves), and rescoring a saved portfolio after a rule change (the planner approves).
- **Never automatic:** submitting applications to FEMA or state portals, changing optimizer numbers, contacting officials or the public, or deleting audit-trail records.

**Escalation triggers:** (1) Confidence **<70%**. (2) An explanation **fails the number check**. (3) A **safety flag**: prompt injection, or a request to break a funding rule or state an unsupported number. (4) **Every grant draft**, before it leaves the product. (5) A portfolio change that **adds or drops projects affecting individual households** (home elevations, buyouts) or vulnerable neighborhoods. (6) A **funding-rule change** that affects saved portfolios. (7) Any **eligibility statement** without a rule citation: eligibility must come from the rules engine with a cited rule, never from the LLM, and uncited eligibility claims are blocked.

**Audit cadence:**
- **Real time:** automated number check on 100% of explanations (owner: engineering lead).
- **Weekly:** automated eval against the golden dataset (owner: product manager).
- **Monthly:** human review of a 1% sample plus all escalations and overrides (owner: QA lead and funding-rule policy analyst).
- **Quarterly:** full policy review with security and legal, including a fairness review of who benefits from recommendations (CEO sign-off).

**Regulatory exposure (EU AI Act / other):**
- **EU AI Act:** not currently in scope, since MitigationIQ serves US public agencies. If it entered the EU, it would likely be **limited risk**, with disclosure duties for AI-generated text. It ranks projects, not people, though buyout and elevation choices do affect households.
- **US:** federal grant rules (2 CFR 200: procurement and records retention); FEMA's benefit-cost analysis requirements; **state public-records laws**, under which outputs and audit trails may be disclosable; possibly **state AI laws** that treat government services as high-stakes decisions, such as Colorado's AI Act (effective date has been delayed and may change); civil-rights rules (Title VI) for fair prioritization.
- **Data:** minimal personal data (property-owner addresses for elevations and buyouts) and **critical-infrastructure vulnerability details** (e.g., flood depths at the wastewater plant, gaps in emergency-center backup power), both kept out of prompts where possible, with no training on customer data. LLM vendors must agree not to retain prompt data. StateRAMP or FedRAMP hosting where buyers require it.

*Owners are roles, since MitigationIQ is a concept. The regulatory list is a starting point, not legal advice; confirm with counsel before using it with a buyer.*

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

| Agent | Can do | Can't do |
|---|---|---|
| **Grant Drafting Agent** | Read the funded portfolio, project data and program rules. Draft application narratives and prepare inputs for FEMA's Benefit-Cost Analysis Toolkit, citing sources. | Submit applications, contact agencies, change any number, create projects, or access other customers' data. The planner or consultant who submits it approves every draft. |
| **Scenario Chat Assistant** | Answer "why?" and "what if?" questions, and rerun the optimizer on a sandbox copy. | Overwrite a saved portfolio, change funding rules, or export anything as council-ready. |

## Shadow AI Audit

> **Simulated:** MitigationIQ isn't a real product yet, so there are no support tickets, interviews or usage logs to search. The workarounds, signal sources, frequencies and spend below are **plausible user behavior simulated for this exercise**, based on how planners and consultants work today. Validate them in pilot interviews before using them for roadmap decisions.

*Columns follow the course mapping: Tool = workaround, Owner = signal source, Risk Level = how often it shows up, Decision = build / partner / ignore, with the dominant gap type.*

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| **ChatGPT or Microsoft Copilot to draft grant narratives** from a portfolio export | Pilot interviews; support tickets mentioning "ChatGPT" | H | **Build** (capability gap). This is the grant drafting add-on; the workaround confirms demand. |
| **ChatGPT to summarize new FEMA and state funding notices** and check what changed in eligibility | Support searches for "NOFO" and "ChatGPT"; questions after BRIC's relaunch | H | **Build** (capability gap): an in-product "what changed" digest whenever funding rules update. |
| **Excel, with Copilot, to recheck funding splits** by exporting the portfolio and redoing the math | Product analytics (CSV exports before council meetings); CS calls | M | **Build** (trust gap → reopen M4): a "show the math" view tracing each funding assignment to its rule. |
| **Zapier or Power Automate to push portfolios into Esri ArcGIS** for council maps | Zapier directory; integration requests to CS | M | **Partner** (workflow gap): an ArcGIS export or connector instead of building maps. |
| **Paid grant-discovery tools (Instrumentl, Grantable) or ChatGPT** to find funding sources beyond the three in the plan | Sales calls; pilot interviews | L | **Ignore for now** (pricing gap): re-examine packaging first; funding-source discovery may belong in the base plan. |

**Total tools found (workarounds found):** 5
**Tools after triage (build candidates):** 3: grant drafting, the funding-notice digest and the "show the math" view. One partner, one ignore.
**Estimated hidden spend (adjacent spend):** ~$40/user/month, or ~$10K/month (~$120K/year) across 250 users. Simulated mix: ~40% on ChatGPT plans at ~$25, ~30% on Microsoft 365 Copilot at ~$30, ~15% on grant-discovery tools at ~$130, and ~10% on Zapier at ~$30. List prices are approximate and should be checked.

**The workaround we've been dismissing:** ChatGPT summaries of funding notices. Funding-rule upkeep was treated as a back-office job for the policy analyst, but users are pasting notices into ChatGPT because they need to know *what changed for their plan*, today. It's not an edge case; it's a build candidate, and it turns the non-compounding funding-rule upkeep loop into something users see and value.

*Governance link: rows 1 and 2 are Samsung-style paste paths. Planners may paste critical-infrastructure details into consumer AI tools, which is another reason to ship these natively under the Governance Policy's data rules.*
