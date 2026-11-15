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

**Broken loop identified by partner:**
**Fix plan:**

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

Planner override reasons and engineer corrections sit in each customer's audit trail. Unless they're routed to MitigationIQ's policy analyst and golden dataset, the product never learns from real use. And without data-sharing rights, each customer's cost outcomes stay isolated, so the benchmark never forms.

## Governance Policy

**Scope:**
**Autonomy boundaries:**
**Escalation triggers:**
**Audit cadence:**
**Regulatory exposure (EU AI Act / other):**

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:**
**Tools after triage:**
**Estimated hidden spend:**
