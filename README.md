# AI Assistant

> If fleet managers can obtain trusted, evidence-backed operational answers through natural conversation faster than navigating dashboards and reports, they will increasingly rely on the AI Assistant as their primary workflow, improving engagement, retention and long-term customer …

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|-------------|
| **The Bet** | M1 | done | `01-the-bet/` |
| **The Moat** | M2 | done | `02-the-moat/` |
| **The Margin** | M3 | done | `03-the-margin/` |
| **The Contract** | M4 | done | `04-the-contract/` |
| **The Guardrails** | M5 | done | `05-the-guardrails/` |
| **The Pitch** | M6 | done | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:** AI Assistant
- **AI Value Archetype:** Operational Copilot — an AI assistant that augments fleet managers by interpreting proprietary operational data, prioritising what matters most, and accelerating trusted decision-making.
- **Vulnerability Scores:** _(Moat 4/5 · Data 5/5 · Platform 4/5)_
- **Top Risk:** The strategic bet fails if conversational interaction does not become the preferred interface for fleet managers' operational decision-making.
- **Confidence:** H
- **Prototype:** https://fleet-insight-copilot.lovable.app
- **Kill Criteria:** Within 6 months of General Availability, fewer than 30% of eligible customers use the AI Assistant weekly, or fewer than 50% of AI interactions result in a follow-up operational action, indicating that conversational AI is not becoming an indispensable workflow and the strategic investment should be reassessed.

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in 6 months.**

- **Data Flywheel Score:** 11/20
- **Weakest Loop:** Preferences Loop scored lowest (2/5). That is where a competitor will probe first, shore up capture, feedback, or proprietary data there before we scale distribution.
- **Top Encroachment Threat:** OpenAI
- **Encroachment Defense:** Strengthen the flywheel where OpenAI cannot compete: build proprietary fleet intelligence rather than a better chat interface. Invest in customer-specific operational memory, evidence-backed recommendations, closed-loop learning from fleet outcomes, and workflow execution that continuously improves from MyCF's unique telematics data. The objective is to make the AI Assistant indispensable because of what it knows about each fleet, not because of how users converse with it.
- **Vendor Portability:** _Partial_

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Gross Margin (current):** 0%
- **Gross Margin (AI-adjusted):** 2%
- **Pricing Model:** platform entitlement for core AI capabilities, with premium/usage-based economics for advanced or unusually compute-intensive capabilities.
- **Pricing Today → Tomorrow:** AI Assistant is embedded within the existing MyCF proposition rather than monetised as a standalone AI SKU. → Initially retain AI Assistant within the core MyCF proposition to accelerate adoption and prove measurable retention and engagement value. Introduce premium pricing only for advanced/high-cost capabilities or materially higher usage tiers once willingness-to-pay and incremental customer value are evidenced.
- **Total AI COGS / unit:** £10.40
- **Cascading Strategy:** Triage: Lower-cost, lower-latency model for intent classification, straightforward retrieval and routine operational questions.; frontier: Higher-capability model reserved for complex reasoning, multi-source synthesis, ambiguous queries and requests requiring stronger contextual interpretation.; ratio 60% triage / 40% frontier, with a target to progressively increase the proportion safely handled by lower-cost models as routing and evaluation maturity improve.
- **Net Margin Shift:** −4.8 percentage points of gross margin, or £2.40 incremental COGS/user/month.
- **Break-even at:**

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **Reliability Target:** ≥92% weekly on the production-representative golden dataset
- **Golden Dataset:** 15 rows, adversarial — prompt injection, unauthorised data access, ambiguous queries, missing/incomplete data, unsupported causal or predictive claims, invalid vehicle identifiers, stale/unavailable source data, and misleading time-period comparisons.
- **Confidence UX:** For the MyCF AI Assistant, I’d combine all three mechanisms: show uncertainty + tiered confidence + human-in-the-loop/escalation triggers. The governing principle should be: the lower the confidence, the less authoritative the Assistant becomes and the more control shifts to the user.
- **HITL Architecture:** **Trigger:** Human review is triggered when confidence falls below the safe-answer threshold, evidence cannot sufficiently support the answer, trusted sources conflict, the request is outside supported scope, access/authorisation is ambiguo…
- **Failure Mode Coverage:** N/A

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales, and what compounds.**

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | User questions, thumbs up/down, corrections, failed/low-confidence answers, support feedback, eval results | Better golden dataset → improved prompts/RAG/retrieval → higher answer quality → more usage → more feedback | Y | broken |
| Cross-Domain Transfer | Patterns learned across fleet use cases: fuel, maintenance, safety, utilisation, EV, compliance; shared MyCF data models and APIs | Capabilities built for one domain become reusable in others, reducing time/cost to launch new AI capabilities | Y - if knowledge is reusable | broken / emerging |
| Network Intelligence | Aggregated, appropriately anonymised fleet patterns across customers, vehicles and operational contexts | Benchmarks, anomaly detection, peer insights and increasingly differentiated recommendations | Y | missing |
| Context Accumulation (custom) | Customer-specific questions, preferences, corrections, terminology, fleet configuration and recurring workflows | Increasingly contextual answers and lower interaction effort for each customer over time | Y | missing / very limited |
| Evaluation Flywheel (custom) | Production failures, edge cases, user corrections, incident learnings and adversarial tests | Expanding golden dataset → stronger eval coverage → safer releases → failures become harder to repeat | Y | emerging |
| Usage Scale (important, but not a learning loop) | More customers, conversations and queries | More inference volume, usage data and operational evidence | N | active |

→ Details: [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

**How you get this funded, shipped, and adopted.**

- **Horizon 1 (Now):** Trusted conversational answers across core MyCF fleet data, with evidence/source grounding and confidence UX · Drive repeat operational usage, instrumenting the core question → answer → action journey and capturing corrections/feedback
- **Horizon 2 (Next):** Proactive operational insights and recommended actions — surface exceptions, risks and opportunities rather than waiting for a prompt · Cross-workflow integration and deeper domain capability, including HGV-specific workflows and approved third-party data where it materially improves decisions
- **Horizon 3 (Bet):** Agentic Fleet Copilot — proactively identifies operational issues, recommends actions and executes bounded, reversible workflows with human approval where required
- **Board Narrative:** We are turning MyCF's proprietary fleet data into a trusted operational copilot that moves fleet managers from finding information, to understanding what matters, to taking action — making MyCF progressively more embedded in daily fleet decision-making.
- **Ask:** Fund the roadmap in evidence-gated horizons: prove trusted repeat usage in H1, release investment into proactive workflows when H1 thresholds are met, and fund agentic execution only when H2 demonstrates measurable operational action and re…
- **Key Strategic Change:**

→ Details: [`06-the-pitch/`](06-the-pitch/)
