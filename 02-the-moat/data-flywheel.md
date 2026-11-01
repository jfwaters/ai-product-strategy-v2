# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.
> The four loops below are the M2 starting point - adapt if your product has 2 or 6 loops instead of 4.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | 3/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | 2/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | 2/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | 1/5 |

*Scored against the planned launch design, not the Lovable prototype or the product's long-term potential.*

### Correction Loop - 3/5
**What you capture today:** When a planner changes a recommendation (forcing a project in or ruling it out), the product asks why, for example "council rejected this" or "cost estimate is outdated", and keeps the change and reason in the audit trail. Later, it also records estimated, bid and final costs for projects that get built.
**How it compounds:** Reasons turn overrides into structured signal about what the optimizer misses, such as local constraints or stale cost inputs. Estimated vs. bid vs. final costs then check the assumptions against real outcomes within 1–3 years. Because the LLM never produces the numbers, corrections update model inputs and rules through human review, not automated retraining.

### Preference Loop - 2/5
**What you capture today:** Each community's priorities, budget, project choices and saved scenarios.
**How it compounds:** Saved context carries into the next plan cycle, so planners start from their last decision rather than a blank page. The product stores these choices but doesn't learn from them yet. Personalization also has a deliberate limit: recommendations must stay defensible, so they can't quietly drift toward a user's habits.

### Domain Context Loop - 2/5
**What you capture today:** Funding eligibility and cost-share rules, project interactions and the five-year plan structure, layered on public data such as the FEMA National Risk Index. These are details a generic model doesn't reliably know, but they come mostly from public sources and a competitor could rebuild them.
**How it compounds:** Flood projects come first. Lessons on costs, interactions and funding could later carry over to other hazards and regions, but that transfer doesn't happen at launch.

### Network Loop - 1/5
**What you capture today:** Nothing across customers. Each customer's data stays isolated, and one customer's use doesn't improve the product for anyone else.
**How it compounds:** It doesn't yet. Shared cost benchmarks could change that, but they need enough customers, multiple years of outcomes and permission to pool the data.

**Total Flywheel Score: 8/20**
**Weakest Loop:** Network (1/5)
**Fix for weakest loop:** Build an anonymized cost benchmark. Customers contribute estimated, bid and final costs, and in return see how their estimates compare with similar projects. Start where a single customer already spans many communities: a consulting firm sees many client towns, and a state mitigation office sees every local application in its state. That creates an early network effect inside one customer before the product needs data from many.

---

## Encroachment Threat Assessment

*Esri is the largest threat; Jupiter Intelligence with Arcadis is the most urgent. Time-to-threat runs until a credible alternative reaches launch customers. % of value at risk is an estimate of the share of MitigationIQ's seven workflow steps the attacker could replace; the percentages overlap and shouldn't be added together.*

### 1. Platform Encroachment
**Attacker:** Microsoft
**Vector:** Copilot in Excel, Word and Teams lets consultants build a "good enough" version in tools they already use. It can draft rationales, compare scenarios and summarize funding rules, but it would be weaker on rule-constrained optimization and traceable numbers.
**Time-to-threat:** 18–24 months. The niche is too small for a dedicated Microsoft product, so the risk comes from general Copilot improvements plus firms' own templates.
**% of value at risk:** 25%, mainly the Explain step and some of the Copilot layer.

### 2. Vertical Competitor
**Attacker:** Jupiter Intelligence, partnered with Arcadis
**Vector:** Jupiter's Adaptation Hub already models adaptation options such as floodwalls, including avoided losses and return on investment, and the PRICE framework it developed with Arcadis ranks options and builds investment cases. Together they go deeper on project-level adaptation economics, which is aimed directly at the work resilience consultants do.
**Time-to-threat:** 6–12 months. The capability partly exists today, but its public materials focus more on finance than government, and there's no sign yet of funding-stack logic.
**% of value at risk:** 40%, covering the Model Each Project and Recommend Portfolio steps, especially with consulting firms.

### 3. Adjacent Expansion
**Attacker:** Esri
**Vector:** Esri adds a portfolio and funding module to ArcGIS and sells it to governments that already use ArcGIS for hazard and asset data. It wins on bundling and distribution, not on being better.
**Time-to-threat:** 12–18 months. No such product has been announced, so this is a judgment about what Esri could do.
**% of value at risk:** 50%, because it attacks the system-of-record position the moat depends on, including the Load the Plan, Recommend Portfolio and Track steps.

---

## 90-Day Encroachment Plan

*Your partner played the Big Tech attacker. What was their plan to kill you?*

**Attacker:**
**Attack vector (target the weakest loop):**
**Weeks 1-4 - what they ship:**
**Weeks 5-8 - how they poach users:**
**Weeks 9-12 - why users don't come back:**
**Your defense:**
