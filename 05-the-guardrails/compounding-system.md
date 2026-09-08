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

**Broken loop identified by partner:** The critical distinction is data accumulation ≠ learning. The Assistant already generates more interaction data as adoption increases, but unless that data systematically changes retrieval, prompts, evals, models, customer context or product behaviour, the system is scaling rather than learning.

Recursive Learning — Broken. We have the ingredients: production interactions, feedback/corrections and an emerging golden dataset/eval framework. The break is the closed-loop mechanism. A correction needs to travel reliably through failure → labelled example → eval → improvement → validation → deployment. Until that pipeline operates systematically, feedback is collected rather than compounded.

Cross-Domain Transfer — Broken/emerging. The MyCF platform gives this significant potential because multiple operational domains share underlying fleet entities and data. But adding another domain does not automatically constitute transfer. It compounds only when improvements in one domain make subsequent domains measurably faster or better to build.

Network Intelligence — Missing. This could eventually become the strongest moat: enough fleet interactions and proprietary operational data could generate benchmarks and patterns an isolated fleet or generic LLM cannot produce. But unless cross-customer learning is technically, legally and commercially enabled—with aggregation/privacy controls—it should not be claimed as an existing flywheel.

**Fix plan:** The custom loop I would prioritise: Context Accumulation

This is particularly aligned with the strategy of making MyCF an operational system customers depend on.
Customer context → better answer → more usage → richer context → better answer.

For example, the Assistant progressively understands that a particular customer cares about specific depots, vehicle groups, KPIs, terminology and operational thresholds. The 100th interaction should therefore be materially better than the first. If interaction 100 is essentially interaction 1 with a larger chat history, there is no compounding loop.

**The vulnerability**
The current architecture appears strongest at proprietary data access and distribution, but weaker at turning usage into durable intelligence.

That creates a strategic vulnerability:
The AI Assistant can scale faster than it learns. More customers create more conversations and inference cost, but not necessarily a proportionately better product.

That matters against a platform encroacher. A generic AI provider can continue improving its underlying model globally. The defensible advantage therefore cannot simply be “our AI knows MyCF data.” It needs to become “every trusted interaction makes the MyCF intelligence layer harder to replicate.”

Therefore, the current compounding architecture needs to be described as 1 emerging learning loop + 2–3 latent loops + 1 active scale loop. The highest-priority gap is closing Recursive Learning, followed by Context Accumulation; those are the two most achievable mechanisms for converting your existing data advantage into an actual compounding moat.

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
