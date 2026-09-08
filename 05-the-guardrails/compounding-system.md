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

**How knowledge flows:** Through shared MyCF data/services, common AI architecture and cross-functional Product–Engineering–Data Science work; reusable retrieval, prompting and eval improvements can propagate across fleet domains.

**Where it silos:** Customer feedback, corrections, failure patterns and domain expertise remain fragmented across teams and use cases, with no systematic mechanism to turn them into reusable context.

## Governance Policy

**Scope:** The policy governs the AI Assistant's use of MyCF customer and fleet data to answer authenticated user questions, generate fleet insights and recommendations, retrieve and synthesise authorised information, and explain the evidence supporting its answers.
It covers:
- LLM inference, prompting, RAG and retrieval.
- Data access and authorisation enforcement.
- Answer generation, confidence handling and citations/evidence.
- User feedback, corrections and human escalation.
- Model/provider changes and AI releases.
- Logging, monitoring, evaluation and incident response.
- Any future tool use or agentic capabilities exposed through the Assistant. Excludes: Core MyCF functionality outside the AI Assistant; underlying source-system data governance already governed by existing MCF policies; internal experimentation not exposed to customers; and autonomous operational actions until separately risk-assessed and explicitly approved.

**Autonomy boundaries:** Answer a standard fleet question using data the authenticated user is authorised to access, auto. Generate non-binding insight or recommendation, auto. Answer when evidence is incomplete, conflicting, below confidence threshold or outside supported scope, human approval required. Execute a consequential customer action — e.g. change configuration, contact drivers, modify fleet records or initiate a workflow, human approval required. Override permissions, expose unauthorised customer data, make legal/compliance determinations or autonomously take safety-critical action, never auto.

**Escalation triggers:** The Assistant must fail safely, request clarification, refuse or route to human review when any defined trigger occurs: 1. Confidence <50% or the agreed low-confidence threshold. 2. No authoritative evidence can be retrieved for a factual fleet-specific claim. 3. Retrieved sources are conflicting, stale or materially incomplete. 4. Request would require data outside the authenticated user's authorised scope. 5. Potential cross-customer data leakage or access-control anomaly is detected. 6. Request involves legal, regulatory, privacy, safety or other consequential interpretation beyond the Assistant's approved scope. 7. User asks the Assistant to perform an action classified as human-approval required. 8. Prompt-injection, jailbreak, anomalous retrieval or suspected security behaviour is detected. 9. Production hallucination/error thresholds defined in the Reliability Contract are breached. 10. A user explicitly challenges the accuracy of an answer or requests human review. For security/privacy triggers, escalation should not simply mean "show a human": stop the affected operation, preserve audit evidence and invoke the relevant security/incident process.

**Audit cadence:** Real-time, Access-control violations, security events, prompt-injection signals, provider/service failures and critical reliability thresholds (Security / Platform Engineering owner). Daily, Production health: failures, refusals, latency, token/cost anomalies and critical user-reported answer issues (AI Engineering owner). Weekly, Accuracy, hallucination rate, low-confidence rate and golden-dataset/eval performance; sample production conversations and corrections (AI Product Manager). Monthly, Drift, recurring failure categories, domain coverage, escalation trends and unresolved reliability risks (Head of Data Science / AI). Quarterly, Governance policy, vendor/model risk, privacy/security controls, autonomy boundaries, regulatory exposure and material architecture changes (CISO + DPO + Product Leadership).

**Regulatory exposure (EU AI Act / other):** Primary governance should account for GDPR / UK GDPR and Data Protection Act 2018, the EU AI Act where the Assistant falls within its territorial scope, contractual/customer data-processing obligations, information-security requirements, and relevant MCF/Michelin enterprise security and AI governance policies.. Risk tier: limited. Controls: Based on the current described use case, I would not label the Assistant high-risk by default: it supports authenticated fleet users with information and operational insights rather than autonomously making decisions in one of the AI Act's specified high-risk areas. However, classification must be reassessed whenever scope or autonomy expands.

**Controls in Place**
- RBAC and authenticated-user access enforced before retrieval, not by the LLM.
- Customer/tenant data isolation.
- Data minimisation and purpose limitation.
- Approved model/provider and data-processing controls.
- Encryption in transit and at rest.
- Evidence-backed responses and source traceability.
- Confidence thresholds and safe failure behaviour.
- Human oversight for consequential actions.
- Prompt-injection and data-exfiltration protections.
- Production logging and auditable decision/action records.
- Golden-dataset regression evaluation before material releases.
- Defined retention/deletion rules for prompts, responses and feedback.
- DPIA/security assessment where required.
- Incident response and rollback mechanisms.
- Periodic regulatory and model-risk reassessment.


## Agent Topology

Not applicable yet.

The current architecture is better governed as:

User → AI Assistant → authorised retrieval/RAG → MyCF data/services → evidence-backed response → user

If/When we later introduce agents capable of invoking tools or changing state, agent topology becomes mandatory. Each agent should then have an explicit tool allowlist, data scope, action boundary, approval owner and audit trail.


## Shadow AI Audit (user-side), Module 5

## Discover, User-Side Workarounds
- Export MyCF data → ChatGPT/Copilot for deeper analysis, summaries or follow-up questions | source: User interview | signal: Capability gap | freq: H | spend: $~$20–30/user/mo | decision: Build
- Copy AI Assistant output/data → Excel/Power BI to manipulate, compare and create management reports | source: User interview | signal: Workflow gap | freq: H | spend: $Existing enterprise spend/mo | decision: Build
- Copy insight → email/Teams/Slack to communicate or trigger follow-up with colleagues | source: User interview | signal: Workflow gap | freq: H | spend: $Existing enterprise spend/mo | decision: Partner
- Use external AI to combine MyCF information with other business data — e.g. ERP, maintenance, fuel or operational datasets | source: API pattern | signal: Capability gap | freq: M | spend: $variable/mo | decision: Partner
- Manually verify AI answers against dashboards/reports before acting | source: User interview | signal: Trust gap | freq: H | spend: $$0, but high time cost/mo | decision: Build
- Use Zapier/Make/API scripts to turn an insight into an operational workflow | source: API pattern | signal: Workflow gap | freq: M | spend: $variable/mo | decision: Partner

## Pattern Assessment
- Workarounds found: 6
- Build candidates: 3
- Partner candidates: 3
- Ignore decisions: 0
- Adjacent spend: $2030/mo
- Dominant signal: Workflow gap

## Action Plan
### Build
Prioritise capabilities that strengthen MyCF's proprietary advantage: follow-up/deeper analysis, evidence and verification, comparisons, reusable analysis/reporting, and eventually safe in-product operational workflows. These improve the core Assistant and deepen the contextual moat.

### Partner
Integrate where the destination already owns the workflow: Teams/Slack/email for collaboration; Power BI/Excel where sophisticated analysis or presentation is required; and selected enterprise systems/APIs where customers need MyCF intelligence combined with external operational data. Don't build another collaboration suite or BI platform.

### Ignore + Monitor
Accept bespoke Zapier/Make workflows and niche external AI use cases where frequency is low and customer-specific. Instrument API usage and discovery interviews to see whether multiple customers independently converge on the same workaround. Repeated convergence is the trigger to reconsider build/partner.

## Roadmap Brief
- Based on your audit: 6 user-side workarounds discovered.
- Decisions: 3 build · 3 partner · 0 ignore · 0 TBD.
- Estimated adjacent spend: $2030/mo across surveyed users.
- Dominant signal: Workflow gap.

Next step: Workflow gaps dominate, the AI Assistant users are stitching the product into multi-step pipelines. Strongest near-term move is partner integrations with the AI tools they already chain in.

Sequence the Build column by frequency × strategic relevance. Confirm Partner candidates with the external tools' partnership teams. Re-run this audit each quarter, workarounds shift fast.


<!-- Governance Policy, AI Assistant -->


