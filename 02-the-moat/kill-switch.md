# Kill Switch Audit

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | AWS Bedrock is the primary model platform, with GPT-4 available as an alternative. This reduces single-model dependency, but production behaviour, security controls, quotas, and prompts may still be optimised mainly for Bedrock. | M | Risk: Medium. Maintain one production-approved secondary provider with contracted access, confirmed data-processing controls, sufficient quotas, validated model versions, and preconfigured credentials. Within 48 hours, activate the secondary model through configuration only—without changing application code. | 
| **Abstraction** | LangChain and a modular LLM architecture provide an abstraction layer, while RAG keeps proprietary fleet knowledge outside the foundation model. Some prompts, tool schemas, token handling, safety controls, or response formats may still contain provider-specific logic. | M | Introduce a single internal model-adapter interface covering generation, tool use, structured outputs, citations, errors, and usage reporting. Within 48 hours, switch the adapter configuration and run the same application contract against the secondary provider. |
| **Routing** | The architecture can potentially use more than one model, but there is no confirmed automated routing or failover policy based on availability, cost, latency, capability, or data sensitivity. A swap may therefore depend on manual engineering intervention. | H | mplement configuration-driven routing with health checks, timeout rules, fallback order, circuit breakers, and rollback controls. Within 48 hours, redirect approved traffic—first canary, then full production traffic—to the secondary provider through a feature flag. |
| **Eval** | The Assistant is expected to produce trusted, evidence-backed answers, but there is no confirmed provider-neutral regression suite demonstrating that an alternative model meets the same quality and safety thresholds. This is the largest barrier to a responsible rapid swap. | H | Build a golden evaluation set from representative fleet questions, including answer accuracy, citation correctness, groundedness, refusal behaviour, permissions, latency, and cost. Within 48 hours, run the complete suite and approve or reject the alternative against predetermined release thresholds. |

Three actions to reach 48-hour readiness

This week — Establish the swap baseline

Complete a dependency inventory covering models, embeddings, prompts, tool calling, guardrails, vector storage, authentication, monitoring, quotas, and provider-specific code. Nominate the approved secondary provider and conduct a manual swap rehearsal in a non-production environment.
Output: A signed-off dependency map, named technical owner, documented swap runbook, and a measured baseline for how long a swap currently takes.

This month — Make the swap executable

Standardise the internal model interface, remove provider-specific logic from core application workflows, introduce configuration-driven routing and feature flags, and secure production-ready access and capacity with the secondary provider. Build the minimum viable golden evaluation set and automate it in the deployment pipeline.

Output: Both providers can run the same priority workflows, using the same tools and RAG sources, with no application-code changes required to switch.

This quarter — Prove 48-hour readiness

Run at least two full portability exercises: one planned failover and one unannounced simulation. Validate quality, security, permissions, observability, cost, latency, rollback, and operational ownership. Resolve failures and make the exercise a recurring quarterly control.

Output: Evidence that the team can detect a provider issue, evaluate the alternative, redirect production traffic, validate performance, and roll back if necessary—all within 48 hours.

Definition of “48-hour swap ready”

A swap is complete only when the alternative provider:

Requires configuration changes rather than application redevelopment.

Passes the agreed quality, groundedness, security, and permissions thresholds.

Has sufficient production quota and contractual approval.

Supports monitoring, cost attribution, incident response, and rollback.

Successfully serves production traffic within 48 hours of the decision to switch.

Overall portability risk: Medium–High. The architectural foundations are promising, but the decisive gap is operational proof: until routing and provider-neutral evaluations are automated and rehearsed, multi-provider capability is an option on paper rather than genuine swap readiness.

## Portability Score
<!-- Ready / Partial / Locked -->

## If [primary vendor] doubles pricing tomorrow:
<!-- What's your 48-hour response? -->

## If [primary vendor] ships a competing product:
<!-- What's defensible that they can't replicate? -->
