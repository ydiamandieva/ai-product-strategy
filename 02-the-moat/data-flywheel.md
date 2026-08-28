# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.
> The four loops below are the M2 starting point - adapt if your product has 2 or 6 loops instead of 4.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | 3/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | 2/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | 3/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | 3/5 |

### Correction Loop - 3/5
**What you capture today:** User feedback and corrections are captured for selected workflows, but not consistently across all interactions.

**How it compounds:** Captured feedback supports periodic improvements to prompts, rules, or models, but is not automatically fed back into learning.

### Preference Loop - 2/5
**What you capture today:** Limited user preferences are captured, with little persistence across sessions or teams.

**How it compounds:** Personalization is mostly static, so user interactions generate limited cumulative value over time.

### Domain Context Loop - 3/5
**What you capture today:** Knowledge and signals are reused within related product domains where shared data exists.

**How it compounds:** Learning from one operational area improves performance in adjacent use cases where underlying data overlaps.

### Network Loop - 3/5
**What you capture today:** Aggregate usage patterns across customers inform improvements to common AI capabilities.

**How it compounds:** Insights from multiple customers strengthen generic capabilities, although organization-specific learning remains largely isolated.

**Total Flywheel Score: 11/20**

**Weakest Loop:** Preferences Loop scored lowest (2/5). That is where a competitor will probe first, shore up capture, feedback, or proprietary data there before we scale distribution.
**Fix for weakest loop:**

---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:** OpenAI
**Vector:** Introduces native enterprise AI agents that connect directly to business systems, making conversational access to operational data, reporting, and workflow automation a built-in capability. OpenAI's advantage is rapid model innovation, a broad enterprise ecosystem, and the ability to integrate across many SaaS platforms, reducing the need for standalone conversational interfaces.
**Time-to-threat:** 2-3 years
**% of value at risk:** 50-70%

This assessment reflects that OpenAI could commoditize much of the conversational layer, but it would still lack MyCF's proprietary fleet data, domain-specific reasoning, customer-specific operational context, and trusted, evidence-backed decision logic—the elements that create long-term differentiation.

### 2. Vertical Competitor
**Attacker:** Fleetio AI (or an AI-native fleet operations startup focused on maintenance and fleet workflows)
**Vector:** Builds deeper, workflow-specific AI for fleet operations (e.g. maintenance, inspections, compliance, and dispatch) using highly structured operational data and customer interactions that are richer within its niche than MyCF's broader fleet dataset.
**Time-to-threat:** 2–3 years
**% of value at risk:** 20–30%

The rationale for the relatively lower percentage at risk is that while a vertical competitor can outperform MyCF in a specific workflow, it is less likely to replace the broader operational assistant embedded across all MyCF fleet management use cases. The risk is concentrated in the niche where they have superior proprietary data and workflow depth, rather than across the entire AI Assistant proposition.

### 3. Adjacent Expansion
**Attacker:** Microsoft (Dynamics 365 + Copilot)
**Vector:** Adds fleet management AI as another Copilot capability within an ecosystem customers already use daily for operations, field service, and business workflows. Its distribution advantage is an enormous installed enterprise customer base and seamless integration across Microsoft 365, Dynamics, Teams, and Power Platform. Microsoft also has access to rich enterprise data (work orders, CRM, ERP, communications, calendars, documents, and business processes) that MyCF does not.
**Time-to-threat:** 2–4 years
**% of value at risk:** 30–40%
The percentage is lower than for frontier AI platforms because Microsoft would still need deep integrations with telematics providers like MyCF to deliver trusted fleet-specific insights. While it could commoditize the conversational interface and workflow orchestration, the proprietary fleet data, domain logic, and operational expertise remain MyCF's primary source of differentiation.

---

## 90-Day Encroachment Plan

*Your partner played the Big Tech attacker. What was their plan to kill you?*

**Attacker:** OpenAI (ChatGPT Enterprise / Agents)

<br>**Attack vector (target the weakest loop):** Preference Loop (2/5) - The AI Assistant has limited long-term memory of user and team preferences, making it relatively easy for users to switch to a more personalized AI experience without losing much accumulated value.

<br>**Weeks 1-4 - what they ship:** Launch a native Fleet Operations Agent that connects to MyCF and other enterprise systems via APIs, enabling conversational fleet queries, report generation, and workflow automation directly inside ChatGPT.

<br>**Weeks 5-8 - how they poach users:** Provide one-click integration, free migration for early adopters, and a superior personalized experience that remembers user preferences, works across multiple business applications, and becomes the default interface for daily operational work.

<br>**Weeks 9-12 - why users don't come back:** Users become accustomed to a single AI assistant that orchestrates work across their enterprise systems rather than only within MyCF. Their saved preferences, custom workflows, and embedded daily habits create switching costs, while MyCF is perceived as just another data source.

<br>**Your defense:** Strengthen the flywheel where OpenAI cannot compete: build proprietary fleet intelligence rather than a better chat interface. Invest in customer-specific operational memory, evidence-backed recommendations, closed-loop learning from fleet outcomes, and workflow execution that continuously improves from MyCF's unique telematics data. The objective is to make the AI Assistant indispensable because of what it knows about each fleet, not because of how users converse with it.
