# MitigationIQ — Product Context

> Early-stage concept for an AI Product Strategy course. Not a real product. Use synthetic data only.

## What it is

MitigationIQ helps communities decide **which disaster-protection projects to fund, with which money, and why.** It is a B2B/B2G SaaS planning workspace. It turns hazard risk data, project costs and funding rules into a recommended, explainable portfolio of projects.

"Mitigation" means spending before a disaster to reduce the damage it causes: elevating flood-prone homes, upgrading storm drains, building flood walls. Communities have far more candidate projects than money. Many tools map the risk. The gap is turning that risk into a defensible decision about what to build, in what order, and with which funding.

**Tagline:** Make every resilience dollar count.

## Why it's hard

- **Money comes in pieces.** Projects are funded by combining federal grants, state programs, loans and local bonds. Each source has its own eligibility rules, a local cost share (often about 25%) and a benefit-cost requirement.
- **Rules change.** FEMA's main pre-disaster grant program was cancelled in 2025, restored by a court, and relaunched in 2026 with new priorities.
- **Projects interact.** Two flood projects in the same area don't simply add up. One can reduce the other's benefit or depend on it.
- **Decisions must be defended** to councils, funders and the public.

## Users

- **Launch customers to test:** (1) resilience/engineering consulting firms; (2) state hazard mitigation offices, which rank many local grant applications against a fixed allocation.
- **Primary user:** the analyst or planner who builds and compares portfolios.
- **Secondary users:** engineers who validate assumptions, and officials who approve spending.

## Core workflow

1. **Load the plan.** Import candidate projects from the community's five-year hazard mitigation plan, along with risk data and the community's priorities.
2. **Model each project.** Capture cost and range, avoided losses and range, maintenance cost, readiness, and interactions with other projects.
3. **Match projects to money.** Assign each project to eligible funding sources, check cost share and the community's ability to pay its match, and phase the work across years.
4. **Recommend a portfolio.** Show performance across scenarios and who benefits. Show fairness tradeoffs openly.
5. **Explain.** Produce a plain-language rationale where every number traces to its source, plus an audit trail of changes.
6. **Hand off.** Export inputs ready for FEMA's Benefit-Cost Analysis Toolkit. Don't compete with the Toolkit.
7. **Track and re-plan.** Record what was funded and built. Re-score the portfolio when funding rules change.

## AI design rules

- **Oracle is the dominant archetype; Copilot is secondary.** The core value is recommendations for high-stakes decisions. A chat layer lets users question and adjust them.
- **The LLM never produces the numbers.** Risk, cost and benefit figures come from deterministic models. Portfolio selection comes from constrained optimization.
- **Generative AI** explains results, flags gaps or inconsistent assumptions, answers scenario questions and drafts justifications for human review.
- **Every recommendation** must be explainable and traceable to its data.
- **Every planner override needs a reason.** When a planner changes a recommendation, the product asks why (e.g., "council rejected this" or "cost estimate is outdated") and keeps the change and reason in the audit trail. These reasons feed model inputs and rules through human review, not automated retraining.

## Positioning

MitigationIQ is a **model-agnostic decision layer**. It ingests risk data from public sources (FEMA National Risk Index) or vendors, and does not build its own disaster models. Its defensibility comes from three things:
- being the system of record for the mitigation plan cycle;
- funding-rule logic;
- a data flywheel that starts with cost and schedule outcomes (estimate vs. bid vs. final cost). These resolve in 1–3 years, while proving benefits takes far longer.

Competitors: Esri, Jupiter Intelligence, Microsoft, Autocase, FEMA BCA Toolkit.

## MVP prototype scope

**Goal:** A consultant builds an explainable, budget- and funding-constrained flood mitigation portfolio for a fictional coastal town.

**Build:**
- A candidate project list with cost, avoided losses, readiness and eligible funding sources
- 2–3 funding sources with different rules and cost shares (e.g., federal grant, state loan fund, local bond; about $20M total)
- At least one project interaction (e.g., a drainage upgrade reduces a flood wall's benefit)
- Controls for budget and priorities (maximize avoided losses / protect critical facilities / prioritize vulnerable neighborhoods)
- A recommended portfolio with funding assignment and phasing
- AI explanation panel plus a chat to ask "why?" and "what if?"
- Side-by-side scenario comparison
- Saved scenarios, to show how planning carries over to the next cycle

**Principles:**
- Use realistic, clearly labeled synthetic data
- Keep calculations internally consistent
- Visibly separate optimizer output from AI explanation
- Use a clean dark theme
- Favor a few strong interactions over breadth

**Out of scope:** proprietary hazard models, real-time monitoring, automated grant applications, engineering design, production integrations, and autonomous funding decisions.

## Glossary

- **Hazard mitigation plan:** a community's official list of risks and candidate projects. It is updated every 5 years and required for federal mitigation grants.
- **Avoided losses:** the damage a project is expected to prevent over its life.
- **BCA:** benefit-cost analysis. FEMA requires benefits to be at least equal to costs.
- **Cost share / local match:** the part of a project's cost the community pays itself.
- **BRIC / HMGP / FMA:** FEMA's main mitigation grant programs (pre-disaster competitive, post-disaster, and flood-specific).
