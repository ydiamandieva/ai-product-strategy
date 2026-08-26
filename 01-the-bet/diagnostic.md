# Three-Axis Vulnerability Diagnostic

## Product
<!-- Name the product you're diagnosing. Real product at your company — not a hypothetical. -->

**Product:** AI Assistant
**Your Role:** Product Manager

---

## Scores

### Contextual Moat — 4/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:** The AI Assistant is deeply embedded in authenticated fleet management workflows rather than acting as a generic chatbot. It solves operational questions using customers' proprietary fleet context, making it significantly harder for horizontal AI products to replace. However, the moat is not yet a 5 because the product is still early in its journey. Customers could potentially recreate parts of the experience using enterprise copilots if the workflows and knowledge layer are not continuously expanded. The competitive advantage comes from workflow integration rather than from technology alone.

**Named attacker (from partner challenge):** Microsoft Copilot - Microsoft is steadily embedding AI into enterprise workflows (Teams, Dynamics 365, Power Platform). If fleet managers increasingly work inside Microsoft's ecosystem, Copilot could become the default interface for operational queries. Your defence is that it lacks the deep workflow integration and domain-specific actions available within MyCF.

---

### Data Advantage — 5/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:** This is the strongest pillar of the strategy. Every answer relies on proprietary operational fleet data that exists only inside MyCF, including vehicle telemetry, driver behaviour, compliance information and customer-specific operational history. Competitors and foundation models cannot reproduce these insights because they do not possess the underlying data. Moreover, your strategy explicitly limits answers to trusted MyCF and approved third-party data, reinforcing explainability and trust. The quality and exclusivity of the data are the primary source of differentiation.

**Named attacker (from partner challenge):** GeoTab - Geotab possesses one of the world's largest connected fleet datasets and has invested heavily in AI and analytics. If any competitor can match MyCF's data-driven insights, it is another fleet platform with comparable proprietary telemetry and operational history. Our advantage depends on continuing to leverage our own customer-specific data better than competitors do.

---

### Platform Exposure — 4/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

**Score rationale:** The assistant benefits from advances in foundation models and cloud AI platforms without needing to build LLM technology itself. The architecture is deliberately modular (AWS Bedrock, interchangeable models), reducing vendor lock-in and allowing rapid adoption of model improvements. However, the strategy is still exposed to platform evolution because changes in model pricing, capabilities or APIs can influence costs and product behaviour. Furthermore, some conversational capabilities are becoming commoditised across Microsoft, Google and OpenAI ecosystems, meaning differentiation must continue to come from MyCF's proprietary data and workflows rather than the conversational interface itself.

**Named attacker (from partner challenge):** OpenAI (or more broadly, foundation model providers) - Rapid advances in foundation models continually commoditise conversational AI capabilities. As models become more capable, the conversational interface itself becomes less differentiated. AI Assistant's strategy mitigates this by treating LLMs as interchangeable infrastructure (via AWS Bedrock) while differentiating through proprietary data, orchestration, and workflow integration.

---

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? --> The strategic bet fails if conversational interaction does not become the preferred interface for fleet managers' operational decision-making.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? --> H – High. The strategy is underpinned by a strong proprietary data advantage and deep workflow integration, with the primary remaining uncertainty being execution and customer behaviour rather than strategic positioning.
