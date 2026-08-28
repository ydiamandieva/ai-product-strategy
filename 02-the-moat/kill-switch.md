# Kill Switch Audit

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | AWS Bedrock is the primary model platform, with GPT-4 available as an alternative. This reduces single-model dependency, but production behaviour, security controls, quotas, and prompts may still be optimised mainly for Bedrock. | M | Risk: Medium. Maintain one production-approved secondary provider with contracted access, confirmed data-processing controls, sufficient quotas, validated model versions, and preconfigured credentials. Within 48 hours, activate the secondary model through configuration only—without changing application code. | 
| **Abstraction** | LangChain and a modular LLM architecture provide an abstraction layer, while RAG keeps proprietary fleet knowledge outside the foundation model. Some prompts, tool schemas, token handling, safety controls, or response formats may still contain provider-specific logic. | M | Introduce a single internal model-adapter interface covering generation, tool use, structured outputs, citations, errors, and usage reporting. Within 48 hours, switch the adapter configuration and run the same application contract against the secondary provider. |
| **Routing** | The architecture can potentially use more than one model, but there is no confirmed automated routing or failover policy based on availability, cost, latency, capability, or data sensitivity. A swap may therefore depend on manual engineering intervention. | H | mplement configuration-driven routing with health checks, timeout rules, fallback order, circuit breakers, and rollback controls. Within 48 hours, redirect approved traffic—first canary, then full production traffic—to the secondary provider through a feature flag. |
| **Eval** | The Assistant is expected to produce trusted, evidence-backed answers, but there is no confirmed provider-neutral regression suite demonstrating that an alternative model meets the same quality and safety thresholds. This is the largest barrier to a responsible rapid swap. | H | Build a golden evaluation set from representative fleet questions, including answer accuracy, citation correctness, groundedness, refusal behaviour, permissions, latency, and cost. Within 48 hours, run the complete suite and approve or reject the alternative against predetermined release thresholds. |

## Portability Score
<!-- Ready / Partial / Locked -->

## If [primary vendor] doubles pricing tomorrow:
<!-- What's your 48-hour response? -->

## If [primary vendor] ships a competing product:
<!-- What's defensible that they can't replicate? -->
