# Three-Horizon Roadmap & Board Pitch

## Roadmap

### Horizon 1 — Now (0-3 months)
*Quick wins. Ship with existing capabilities.*

| Initiative | Metric | Confidence |
|-----------|--------|-----------|
| Trusted conversational answers across core MyCF fleet data, with evidence/source grounding and confidence UX| ≥90% answer accuracy; <1% hallucination rate; ≥70% successful-answer rate without fallback | H |
| Drive repeat operational usage, instrumenting the core question → answer → action journey and capturing corrections/feedback | ≥30% of activated users become weekly active AI users; ≥25% 4-week repeat usage | H |

### Horizon 2 — Next (3-9 months)
*Bets. Requires new capabilities or integrations.*

| Initiative | Metric | Confidence |
|-----------|--------|-----------|
| Proactive operational insights and recommended actions — surface exceptions, risks and opportunities rather than waiting for a prompt | ≥30% of surfaced insights opened; ≥20% result in a downstream action; measurable reduction in time-to-insight | M |
| Cross-workflow integration and deeper domain capability, including HGV-specific workflows and approved third-party data where it materially improves decisions | ≥25% of active AI users use 2+ AI-assisted workflows monthly; ≥15% uplift in AI engagement within enabled cohorts | M |

### Horizon 3 — Bet (9-18 months)
*Moonshots. High uncertainty, high potential.*

| Initiative | Metric | Confidence |
|-----------|--------|-----------|
| Agentic Fleet Copilot — proactively identifies operational issues, recommends actions and executes bounded, reversible workflows with human approval where required | ≥30% of eligible operational workflows initiated through AI; ≥20% reduction in time-to-resolution; no material unauthorised actions | L |

## Board Pitch

**Thesis (1 sentence):** We are turning MyCF's proprietary fleet data into a trusted operational copilot that moves fleet managers from finding information, to understanding what matters, to taking action — making MyCF progressively more embedded in daily fleet decision-making.

**The case:**
1. Why now: Fleet managers already have significant operational data but still expend time navigating reports and dashboards to interpret it. Generative AI creates an opportunity to collapse that workflow into conversational, decision-oriented interaction while leveraging data MyCF already holds.
2. What's defensible: The model itself is not the moat. Defensibility comes from proprietary fleet context + authenticated customer data + domain-specific operational workflows + accumulated user corrections and interaction signals. Each validated interaction can improve the Assistant's understanding of which signals matter in real fleet operations.
3. The economics: The Assistant is built on the existing MyCF customer and data footprint, limiting incremental acquisition cost. Model routing, smaller models for lower-complexity tasks, caching and provider abstraction create levers to control inference COGS as usage scales. The economic thesis is ultimately retention and expansion value generated per AI-active account > incremental AI serving cost.

**The risks:**
1. Trust / failure modes: Trust / failure modes: A confidently incorrect operational answer can destroy adoption quickly. We therefore treat reliability as a product contract: grounded answers, golden-dataset regression testing, confidence states, explicit fallback behaviour and human control for consequential actions.
2. Scale / governance: Higher usage increases inference cost, data-access complexity and the blast radius of failures. Provider abstraction, routing, continuous evals, role-based authorisation and explicit agent boundaries need to scale ahead of autonomy.
3. Competitive: Foundation-model providers and fleet competitors can reproduce conversational UI. Our defence therefore cannot be “we have a chatbot”; it must compound around proprietary operational context, trusted workflows and customer-specific learning that are progressively harder to replicate.

**The ask:** Fund the roadmap in evidence-gated horizons: prove trusted repeat usage in H1, release investment into proactive workflows when H1 thresholds are met, and fund agentic execution only when H2 demonstrates measurable operational action and retention value.

## M1 Baseline vs. Now
*Your 3-sentence AI strategy from Module 1 vs. what you'd say now:*

**M1 baseline:** We will transform MyCF from a system fleet managers use into one they depend on by making conversation the primary interface to fleet intelligence. We will win by providing faster, trusted and evidence-backed answers from proprietary fleet data, reducing the friction of traditional dashboards and reports. Success means higher engagement, retention and customer lifetime value.

**Now:** We are building an Operational Copilot that turns proprietary MyCF data into trusted decisions and, eventually, bounded action. The strategy compounds through operational context, customer-specific usage and correction signals, while reliability contracts, model routing and explicit agent boundaries protect trust and economics as usage scales. We will earn the right to make AI the primary operational interface through three evidence gates: trusted repeat usage → measurable decision impact → safe operational action.
