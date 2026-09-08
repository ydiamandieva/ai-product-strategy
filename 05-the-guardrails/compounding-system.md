# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | User questions, thumbs up/down, corrections, failed/low-confidence answers, support feedback, eval results | Better golden dataset → improved prompts/RAG/retrieval → higher answer quality → more usage → more feedback | Y | broken |
| Cross-Domain Transfer | Patterns learned across fleet use cases: fuel, maintenance, safety, utilisation, EV, compliance; shared MyCF data models and APIs | Capabilities built for one domain become reusable in others, reducing time/cost to launch new AI capabilities | Y - if knowledge is reusable | broken / emerging |
| Network Intelligence | Aggregated, appropriately anonymised fleet patterns across customers, vehicles and operational contexts | Benchmarks, anomaly detection, peer insights and increasingly differentiated recommendations | Y | missing |
| Context Accumulation (custom) | Customer-specific questions, preferences, corrections, terminology, fleet configuration and recurring workflows | Increasingly contextual answers and lower interaction effort for each customer over time | Y | missing / very limited |
| Evaluation Flywheel (custom) | Production failures, edge cases, user corrections, incident learnings and adversarial tests | Expanding golden dataset → stronger eval coverage → safer releases → failures become harder to repeat | Y | emerging |
| Usage Scale (important, but not a learning loop) | More customers, conversations and queries | More inference volume, usage data and operational evidence | N | active |

**Broken loop identified by partner:**
**Fix plan:**

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

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
