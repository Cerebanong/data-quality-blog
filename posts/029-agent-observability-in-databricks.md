---
title: Treating Agent Behavior as a First-Class Data Domain in the Databricks Lakehouse
slug: agent-observability-in-databricks
pillar: ai-data-quality
author: Kevin L Frank
date_published: '2026-05-12'
tags:
- ai-data-quality
- agent-observability
- mlflow
- databricks
- unity-catalog
- regulated-industries
- model-risk-management
excerpt: Agent traces are data. In Databricks, that single framing turns observability,
  drift detection, A/B testing, and regulator-ready audit trails into work the data
  team already knows how to do.
seo_title: Agent Behavior as a Data Domain in Databricks
seo_description: How teams running on Databricks can treat AI-agent traces as a first-class
  data domain in Unity Catalog, with citations to current MLflow, Mosaic AI, and regulatory
  references.
featured_image: images/029-agent-observability-in-databricks-featured.png
---

## The Question Regulators Will Eventually Ask

An AI agent dispatched to a sub-agent, which called a tool, which returned a result that flowed into an answer your customer acted on. Three months later, that answer is the subject of a complaint, an internal escalation, or a supervisory information request. The question is the same in all three cases: what did the agent actually do, and on what basis.

Agent traces are the answer. They are the time-stamped, span-by-span record of every prompt, every retrieval, every model call, every tool invocation, every sub-agent dispatch, every evaluation score. In regulated environments, the question is not whether to capture them. The EU AI Act mandates a minimum of six months of automatically generated logs for high-risk AI systems (EU AI Act Art. 12, 2024), and US banking supervisors have signaled that the principles of the revised interagency model risk management guidance apply by analogy to GenAI and agentic deployments even though those systems are formally out of scope (Federal Reserve, FDIC, OCC SR 26-02, 2026). The question is how to capture them in a form regulators, auditors, and your own incident responders can use.

This post is for teams already running on Databricks. The argument is that the right place for agent traces is exactly where the rest of your governed data lives: Delta tables in Unity Catalog, with the same access controls, lineage, retention policies, and audit logging as any other regulated data domain. A useful comparison: a **pharmaceutical batch record** carries every input, every machine, every operator, every timestamp, and every quality check for one lot of medicine, and an inspector who arrives a year later can reconstruct the lot from that record alone. Agent traces, treated the same way, are the batch record of an AI decision.

## The Databricks Stack Already Provides Most of the Pieces

A typical Databricks customer has already provisioned the components needed for native agent observability. The pieces that matter for this conversation:

- **MLflow Tracing** is built into the Databricks workspace, with GenAI tracing as a first-class feature rather than a plugin. It captures inputs, outputs, intermediate steps, and metadata using OpenTelemetry-compatible spans, and auto-instruments popular GenAI libraries (Databricks docs, 2026; Databricks blog on MLflow 3.0, 2025).
- **Mosaic AI Agent Framework** is the agent authoring layer. Agents and sub-agents registered through it are traced automatically when logged through MLflow (Databricks blog, 2024).
- **Mosaic AI Agent Evaluation** scores traces using LLM-as-judge and rule-based approaches, against curated golden datasets or live production traces.
- **Unity AI Gateway** (the rebranded Mosaic AI Gateway) sits between agents and external models. It enforces rate limits, cost caps, and key management, and it captures usage and payload data into Unity Catalog Delta tables (Databricks docs, 2026; Databricks blog on Mosaic AI Gateway updates, 2024). Older references in the docs and the wider literature still call this product Mosaic AI Gateway.
- **Unity Catalog** governs the traces, prompts, agents, models, tools, and evaluation datasets as cataloged assets with table-level and column-level lineage, access control, and audit logging.
- **Workflows** orchestrate scheduled and triggered jobs for evaluation runs, drift checks, and reporting.
- **Databricks SQL, AI/BI dashboards, and AI/BI Genie** are the analytics surface that sits on top of the trace tables, including a natural-language query interface over governed tables (Databricks docs, 2026).

That set of components does not require a separate observability tier from an external vendor. It treats agent runs as data, and Databricks is already optimized for treating things as data.

## Where Trace Data Lands Dominates Every Downstream Decision

The single most consequential architectural decision is where the trace data lives. When MLflow tracing is configured to store traces in Unity Catalog using the OpenTelemetry format, every trace lands in a Delta table governed by Unity Catalog (Microsoft Learn, 2026). Five things follow from that.

Traces inherit the same access control model as the rest of the Lakehouse. The row-level and column-level security applied to customer data applies to traces of agents that handled customer data. There is no second permission model to build, audit, or defend.

Traces inherit lineage. Unity Catalog's lineage graph shows which prompts, which agents, which tools, and which models contributed to a given trace. When something goes wrong, the lineage graph is what walks the incident responder backwards from a bad output to the contributing inputs.

Traces are queryable with the same SQL the rest of the business uses. There is no separate observability query language to learn, no data export step, no separate identity boundary.

Traces are time-travelable. Delta versioning lets a query return the exact trace state on a given day, which is precisely what an audit response requires when the question is what the system looked like at a moment in the past (Databricks, 2019).

Traces feed Power BI and existing reporting stacks with no impedance mismatch. Anything the business already builds on top of Delta tables, it can also build on top of trace tables.

That set of properties is what makes everything downstream tractable. A guardrail dashboard, a drift alert, an A/B test, a compliance reconstruction: each becomes a SQL query or a Workflow job against governed Delta tables rather than a new platform decision.

## Building a Guardrail Observability Layer

There are three guardrail jobs that recur in production agent systems: monitoring the guardrails that already exist, building the next round of guardrails, and supporting investigations. Each one maps to a Databricks-native pattern.

For **monitoring existing guardrails**, a Databricks SQL view on top of the trace tables surfaces guardrail-firing events: every time a content filter blocked an output, every time a tool was rejected by an allowlist, every time a policy classifier flagged a retrieval. That view feeds an AI/BI dashboard with alerting wired through Workflows. A subtle but important detail: if guardrail firings drop to zero, that should fire its own alert. A silent guardrail is more often a broken instrumentation path than a clean week.

For **building new guardrails**, the trace store doubles as a labeled-dataset source. Traces with negative feedback become candidate training examples. Mosaic AI Vector Search clusters traces semantically, surfaces the patterns worth governing, and lets those clusters define the next round of policy. A guardrail that starts life as a SQL view can graduate to a model-based classifier registered as a Unity Catalog model, with versioning and access controls already in place.

For **investigation**, the trace tables are the audit trail. Given a session ID from a customer complaint, an internal escalation, or a regulator question, the span tree reconstructs what happened. The reconstruction is reproducible because the underlying data is versioned in Delta.

This is the part of the regulated-environments conversation that examiners care about. Regulators want documentation, not assertions. "We have observability" is not enough. "Here is the SQL that produces the audit log, here is the retention policy, here is the access log on who queried it, here is the lineage graph" is what an examiner accepts. Unity Catalog provides all four.

## Drift Detection Without a New Tool

Lakehouse Monitoring already exists for traditional data and feature drift, with built-in profiling and drift metric tables stored as Delta in Unity Catalog (Databricks docs, 2026). The pattern extends to agent traces with little additional effort.

**Input distribution drift** on the prompt corpus is monitored over time using statistical tests on derived features such as length, language, intent classification, and entity types. Lakehouse Monitoring handles this with its built-in profiling.

**Tool output drift** is monitored on the response shapes coming back from each tool, including schema changes, latency distributions, and error rate changes. This is ordinary time-series monitoring against trace span data.

**Model behavior drift** is monitored by scheduling an Agent Evaluation job that scores a fixed evaluation dataset against the current production agent and writes the scores to Delta. When scores move outside their historical band, an alert fires. The evaluation dataset lives in Unity Catalog. The scoring runs through Mosaic AI Agent Evaluation. The alert routes through Workflows.

**Prompt-phrasing drift** is monitored using Vector Search on the prompt embeddings, watching for shifts in the centroid over time. New phrasing patterns emerge as new clusters, and new clusters trigger a review.

None of these require new infrastructure. They are SQL, scheduled jobs, and existing monitoring features applied to a new data source.

## BI on BI: Trace Data Is Just Data

Trace data lives in Delta. AI/BI Genie converts natural-language questions into SQL using Unity Catalog metadata (Databricks docs, 2026). Together, those two facts create a self-service interface for asking questions about agent behavior:

- Which sub-agents had the highest error rate this month?
- What is the average token cost per session for the fraud-detection agent?
- Which prompts produced the longest reasoning loops yesterday?
- How has tool selection changed since the customer-monitoring skill was updated?

These are questions a data or AI leader should be able to ask without writing SQL or filing an analytics ticket. Genie running on top of governed trace tables turns that into a self-service capability.

Power BI on top of trace tables is the same idea with a familiar user experience. Weekly executive reporting on agent reliability, cost trends, adoption curves, and SLA performance becomes a normal BI deliverable rather than a special project. Once agent operations metrics live alongside the rest of the operations metrics, the practical effect is that agent quality stops being a separate conversation and starts being part of the existing monthly business review.

## Prompt and Model A/B Testing as a SQL Query

When prompts and models are versioned in Unity Catalog and traces are tagged with the version that produced them, A/B testing becomes a SQL query rather than a separate experimentation platform.

The pattern is straightforward. Every trace carries the prompt version and the model version. A defined percentage of traffic routes to the candidate prompt or model. After a defined window, a comparison query joins error rate, token cost, latency, evaluation scores, and downstream feedback, grouped by version. The decision to promote or roll back is evidence-based.

This is the same discipline already applied to data-pipeline development. A pipeline change does not ship on a flag flip and an optimistic email; it ships on a comparison of historical and candidate runs. Agent changes deserve the same rigor, and the trace tables make that rigor a few hundred lines of SQL away.

## Error Analytics That Feed Back into Design

Error analytics in a trace store are an embedding problem. Each error span normalizes into a row with the error message, an embedding of the message, the surrounding context (which tool, which prompt version, which model), and a fingerprint hash. Vector Search clusters them. Databricks SQL queries the clusters. A Workflow alerts when a cluster spikes.

A second layer of evaluation scores each cluster for whether it represents a recoverable failure or a hard one, which sets the priority order. The output of that scoring is a ranked list of error clusters, fed back into the agent design loop as candidates for prompt or tool fixes.

For regulated workloads, error analytics double as a compliance signal. A spike in error clusters tied to a regulatory category (KYC lookups failing, AML flag retrievals failing, sanctions checks timing out) is a control-trigger event with the trace data as the source of truth. The same query that catches a quality regression catches an emerging control gap.

## The Orchestrator and Sub-Agent Contract Is an Emerging Pattern

Multi-agent systems introduce a class of failure that single-agent systems do not: information loss or distortion as parameters move from an orchestrator to a sub-agent and back. Academic work on agent failure modes has begun to formalize this. The arXiv survey by Chen et al. (2025) on LLM-agent hallucinations names **Communication Hallucinations** (induced when inter-agent updates are inconsistent or stale) and **Reasoning Hallucinations** (where the agent's chain of reasoning departs from its inputs) as distinct categories.

When orchestrator-to-sub-agent dispatch is captured in the same trace store as everything else, contract-testing those interactions is a SQL exercise. Four queries cover most of the surface:

- For each parameter dispatched, was it referenced in the sub-agent's output?
- What is the reference rate per parameter, per sub-agent, over time?
- Are there sub-agents whose outputs frequently mention things not in their input parameters? (A possible hallucination signal.)
- Are there parameters the orchestrator passes that no sub-agent ever uses? (A possible specification drift in the orchestrator.)

These are queries a data engineer can write in an afternoon against governed Delta tables. The result is a contract-testing dashboard for an agent system. Span-level parent and child relationships are already part of the MLflow trace model and the wider OpenTelemetry GenAI semantic conventions (OpenTelemetry, 2026), so the joins are well-defined. This is an under-developed pattern in production today, but the underlying primitives are in place and the literature pointing at the problem is growing.

## A Reference Architecture

A workable end-to-end pattern for a regulated Databricks deployment looks like this.

User requests flow into the agent. The agent sits behind Unity AI Gateway. Models are called through the gateway, which enforces rate limits, cost caps, and key management and writes its own usage table. Sub-agents are spawned through Mosaic AI Agent Framework. Every span lands in MLflow tracing, which writes to Unity Catalog Delta tables.

On top of the trace table:

- A continuous Agent Evaluation job, scheduled in Workflows, scores incoming traces and writes scores back to Delta.
- A drift detection job, run through Lakehouse Monitoring, watches input and tool output distributions.
- A guardrail monitoring view in Databricks SQL surfaces guardrail firings and feeds an alerting Workflow.
- A Vector Search index over prompts and over errors supports clustering, pattern detection, and the contract-testing queries.
- A Power BI semantic model on top of trace summaries supports weekly executive reporting.
- An AI/BI Genie space scoped to the trace tables supports self-service questions from leadership (not needed early, but a high-value addition once the trace store stabilizes).

The prompt registry, the agent definitions, and the evaluation datasets all live in Unity Catalog with versioning. The whole pipeline is governed by the same access controls as the rest of the platform.

That architecture is achievable today with components that are either generally available or in active preview, using skills already present on a typical Databricks data engineering team.

## Considerations for Regulated Environments

Four considerations deserve explicit attention when this pattern lands in a regulated environment.

**PII handling.** Traces may contain personally identifiable information. Unity Catalog Data Classification auto-tags PII across the catalog using a built-in classifier, and attribute-based access control (ABAC) policies enforce row filters and column masks against those tags (Databricks blog on Data Classification, 2025; Databricks docs on ABAC, 2026). The combination produces automatic masking on trace columns that hold customer data without requiring per-table policy.

**Auditability.** Every trace access is itself logged through Unity Catalog audit logs. The compliance position is therefore not "we have observability" but "here is the SQL that produces the audit trail, here is the retention policy, here is the log of who queried what." That is what a supervisory request actually asks for.

**Model risk management.** Treating a foundation-model version change (a Claude minor upgrade, a Llama point release, a GPT-class rev) as a model change in the regulatory sense is now a defensible position rather than a niche concern. SR 11-7 was the US framework for model risk management from 2011 onward; on 17 April 2026 the Federal Reserve, FDIC, and OCC issued revised, principles-driven guidance that replaced it (SR 26-02, 2026). GenAI and agentic systems are formally out of scope of the revised guidance, but supervisors and internal audit have already begun applying the principles by analogy to LLM-based underwriting assistants, AML triage agents, and customer-facing copilots (Databricks Banker's Guide, 2026). For European deployments and global institutions, EU AI Act Article 12 sets a six-month minimum retention floor for the same kind of logs (EU AI Act, 2024). The evidence trail that supports whatever model-change policy your firm adopts is the trace history plus the evaluation results.

**Vendor concentration.** Delta is an open table format. Microsoft Fabric uses Delta natively, and OneLake provides automatic metadata virtualization between Delta and Apache Iceberg through Apache XTable, so a trace store written by MLflow into Delta can be read by Iceberg-native tools without copying (Microsoft Fabric blog, 2025). The trace schema is documented through OpenTelemetry GenAI semantic conventions, which the major observability vendors are converging on (OpenTelemetry, 2026). Operating natively on Databricks does not paint the trace store into a corner.

## Practical Application

For a Databricks team ready to start, the order of operations that produces the most value per hour of work:

1. Turn on MLflow GenAI tracing in the development workspace, configure trace storage in Unity Catalog using OpenTelemetry format, and confirm that traces land in a Delta table the data engineering team can query.
2. Register prompts, agent definitions, and evaluation datasets as versioned Unity Catalog assets. Add tags for environment, owner, and regulatory scope.
3. Build the guardrail-firing view and an AI/BI dashboard on top of it. Wire the "firings dropped to zero" alert through Workflows.
4. Schedule the first Agent Evaluation job against a small golden dataset. Land the scores in a Delta table next to the trace store.
5. Apply Lakehouse Monitoring to the input distribution and tool output distributions. Set the baseline to the first two weeks of production data.
6. Apply Unity Catalog Data Classification and ABAC column masking on any trace column that may contain PII before the trace store is exposed to anyone outside the immediate engineering team.
7. Stand up the Power BI semantic model on the trace summary tables. Add a weekly cost-and-reliability page to the existing operations review.
8. Only after the first six steps are stable, scope an AI/BI Genie space to the trace tables and grant leadership read access. Genie value is bounded by the cleanliness of the metadata, so this is a later step rather than an early one.

## Key Takeaways

- **Agent traces are data, and the right place for them is the same place as your other governed data.** When traces land in Unity Catalog Delta tables, they inherit access control, lineage, audit logging, time travel, and BI tool compatibility for free.
- **The Databricks customer who already has MLflow, Mosaic AI, Unity Catalog, Workflows, and AI/BI does not need a separate observability tier.** Most of the observability stack is provisioned. The remaining work is wiring it together and treating trace data as a first-class data domain.
- **Drift detection, A/B testing, error analytics, and guardrail monitoring are all SQL exercises against trace tables.** They are not new platforms to evaluate.
- **The orchestrator and sub-agent contract is an under-developed but increasingly important pattern.** Multi-agent hallucination taxonomy in the literature names the failure modes (Chen et al., 2025), and the trace store already carries the information needed to query them.
- **In regulated environments, the trace store is the audit trail.** Recent US (SR 26-02, 2026) and European (EU AI Act Article 12, 2024) guidance treat AI logs as evidence, and the practical answer to a supervisor's question is a SQL query against versioned Delta tables, not an assertion.

## Sources

1. Databricks. "MLflow Tracing: GenAI observability." 2026. https://docs.databricks.com/aws/en/mlflow3/genai/tracing
2. Databricks. "MLflow 3.0: Build, Evaluate, and Deploy Generative AI with Confidence." 2025. https://www.databricks.com/blog/mlflow-30-unified-ai-experimentation-observability-and-governance
3. Databricks. "Announcing Mosaic AI Agent Framework and Agent Evaluation." 2024. https://www.databricks.com/blog/announcing-mosaic-ai-agent-framework-and-agent-evaluation
4. Databricks. "Unity AI Gateway." 2026. https://docs.databricks.com/aws/en/ai-gateway/
5. Databricks. "Advanced Security and Governance in Mosaic AI Gateway." 2024. https://www.databricks.com/blog/new-updates-mosaic-ai-gateway-bring-security-and-governance-genai-models
6. Microsoft Learn. "Store MLflow traces in Unity Catalog." 2026. https://learn.microsoft.com/en-us/azure/databricks/mlflow3/genai/tracing/trace-unity-catalog
7. Databricks. "Introduction to Databricks Lakehouse Monitoring." 2026. https://docs.databricks.com/aws/en/lakehouse-monitoring/
8. Databricks. "What is a Genie Space." 2026. https://docs.databricks.com/aws/en/genie/
9. Databricks. "Introducing Delta Time Travel for Large Scale Data Lakes." 2019. https://www.databricks.com/blog/2019/02/04/introducing-delta-time-travel-for-large-scale-data-lakes.html
10. Databricks. "Find Sensitive Data at Scale with Data Classification in Unity Catalog." 2025. https://www.databricks.com/blog/find-sensitive-data-scale-data-classification-unity-catalog
11. Databricks. "Attribute-based access control in Unity Catalog." 2026. https://docs.databricks.com/aws/en/data-governance/unity-catalog/abac/
12. Microsoft Fabric Blog. "New in OneLake: Access your Delta Lake tables as Iceberg automatically." 2025. https://blog.fabric.microsoft.com/en-gb/blog/new-in-onelake-access-your-delta-lake-tables-as-iceberg-automatically
13. OpenTelemetry. "Semantic Conventions for Generative AI Systems." 2026. https://opentelemetry.io/docs/specs/semconv/gen-ai/
14. Chen, Y., et al. "LLM-based Agents Suffer from Hallucinations: A Survey of Taxonomy, Methods, and Directions." arXiv:2509.18970, 2025. https://arxiv.org/html/2509.18970v1
15. Federal Reserve, FDIC, OCC. "SR 26-02: Revised Interagency Guidance on Model Risk Management." 17 April 2026. https://www.federalreserve.gov/supervisionreg/srletters/SR2602.pdf
16. Databricks. "Model Risk Management in 2026: A Banker's Guide to the Revised Interagency Guidance." 2026. https://www.databricks.com/blog/model-risk-management-2026-bankers-guide-revised-interagency-guidance
17. EU Artificial Intelligence Act. "Article 12, Record-Keeping." 2024. https://artificialintelligenceact.eu/article/12/

## What's Next

For the policy-level argument that traditional data quality dimensions are insufficient for AI workloads, and the seven-dimension AI-ready data framework that motivates the trace-as-data framing in this post, see [AI Didn't Replace Data Quality. It Raised the Bar.](/blog/gartner-2026-data-quality-in-the-age-of-ai).

For the broader observability discussion that frames the same problem outside the agent context (data quality monitoring, pipeline health, lineage), the upcoming Data Observability: Beyond Monitoring post will cover the five-layer framework that this pattern is one application of.

For the related discipline of model feature observability, which applies many of the same techniques to feature distributions and training and serving skew, the upcoming ML Feature Observability post will cover the production-monitoring side of the AI quality picture.
