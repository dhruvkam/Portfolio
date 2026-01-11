# Finance GenAI Platform Overview

## 1) Project Identity and Framing

### Working Project Names

- **FDH-GenAI Enablement (Report Agent)** / Finance Assistant integrated into Finance Data Hub (FDH), providing AI Insights (summaries) and a chat-based "Finance Assistant" for data Q&A and visualizations

- **LLM over Finance Data Factory (FDF)** — a "Data Agent" / Text-to-SQL capability designed to expose Walmart finance/transaction data to LLMs at scale, with cross-dataset intelligence and governed access

### One-line Executive Summary (Resume-Safe)

> Built and scaled a governed GenAI finance assistant that lets analysts and leaders query enterprise finance + transaction data in natural language, automatically generating auditable answers, summaries, and visuals inside existing finance reporting experiences—reducing SQL dependency and accelerating "insights-to-action."

---

## 2) The Problem Being Solved

### Baseline Workflow Pain

Finance associates and business partners routinely need "quick answers" (performance vs plan, variance drivers, forecast context). Historically this requires:

1. Knowing where the data lives (which tables / which report)
2. Understanding complex schemas and business logic
3. Writing SQL / using Power BI/Tableau/Excel at a high level
4. Or escalating to more technical resources (data engineers, senior analysts), creating bottlenecks and delays

The PRD explicitly describes ad hoc analysis as time-intensive and requiring technical proficiency beyond many finance associates, highlighting the goal of shifting time away from data-searching toward strategic finance work.

### Why GenAI (and why "RAG + enterprise data context")

- LLMs alone have limitations (hallucination + lack of real-time business context)
- RAG helps, but scaling many RAG implementations creates architectural complexity and cost
- Leadership pressure exists to expose data context at a foundation level to accelerate adoption and reduce total cost of ownership

### Outcome Sought

Enable self-service analytics where a finance user can ask:

- *"How did we perform in hardlines last quarter vs plan?"*
- *"What drove the miss in Net Sales this month?"*

...and get accurate, explainable results quickly, without writing SQL.

This aligns directly with: *"Enable faster, more intuitive exploration of business performance through natural language questions and automated insights directly within reports,"* with **time savings** and **democratized data**.

---

## 3) Who the Project Serves

### Primary End Users

| Persona | Use Case |
|---------|----------|
| **Finance analysts / associates** (including non-SQL users) | Ad hoc analysis and root-cause investigation |
| **Finance leadership / decision-makers** | Fast diagnostic answers without relying on junior analyst pull requests |
| **Report consumers inside FDH** | Insights directly in the reporting workflow (metrics tiles, reports, drill-downs, publications) |

### Supporting Personas / Partner Teams

- **Data stewards** — ground truth documentation, correctness ownership
- **Report/Semantic owners** — Power BI semantic layer owners; ensuring consistency with reporting logic
- **Engineering, Architecture, Data Engineering, UX, Program/PMO** — explicitly listed as resources/stakeholders

---

## 4) What the Product Enables (Capabilities)

This initiative is best understood as **two tightly-related product layers**:

1. **Experience layer** in FDH (Finance Data Hub)
2. **Foundation "data agent" layer** (LLM over FDF / Text-to-SQL across datasets)

### 4.1 FDH GenAI Enablement: "AI Insights + Finance Assistant"

#### Core Objective

Integrate GenAI into FDH so users can:

- Get proactive summaries/insights on KPIs and reports
- Ask natural-language questions about the data powering reports/metrics
- Generate custom visuals via chat
- Get support/guidance (definitions, access, points-of-contact)

#### Features in Scope (Six Use-Case Model)

**SUMMARY / INSIGHTS**
1. **Insights at a glance** — AI-generated summaries on metric tiles and report pages (multi-level L1–L4)

**CHAT**
2. **Data Q&A** — Chat with report/metric data; get instant answers
3. **Custom visuals** — Create charts/tables through chat
4. **Support & guidance** — Ask "how do I…?" about FDH reports, definitions, access, and who to contact

**GENERATE** (future / partially out of scope depending on release)
5. **Key issue surfacing** — Notifications/alerts/highlights/nudges for early visibility
6. **Personalized metric creation** — Create personalized KPI cards via chat

#### What "Good" Looks Like (User-Level Outcomes)

- **Time savings** — Routine analyses automated; insights in seconds rather than hours
- **Lower technical barrier** — "Anyone can ask" questions like "Why did sales dip?" without SQL or Power BI expertise
- **Proactive insights** — Detect/understand drivers of anomalies or material shifts

#### Reporting Coverage (Initial Rollout)

August launch targeting **8 reports**, including:
- DST suites
- P&L suites (Walmart, Sam's, International, Consolidated, Corporate, etc.)
- Future expansion: eCFR (enterprise forecast)

#### Behavioral Guardrails and Edge Cases

| Constraint | Detail |
|------------|--------|
| Fiscal week timing | Walmart fiscal week is Saturday–Friday; Saturday questions may show incomplete/zero week-to-date |
| Report refresh timing | ~5 a.m. CST affects "latest day" availability |
| No predictive questions | Supports historical data analysis only (in this release) |
| Driver questions | Default to hierarchy breakdown unless basket metrics are explicitly requested |

> These constraints are exactly the "product realism" that helps in interviews: you're not just building a chatbot, you're building a **governed analytics workflow**.

---

### 4.2 LLM over FDF: The Foundational "Data Agent"

#### Core Objective (Foundation-Level)

Build a scalable "SQL agent" that can work across datasets in the Finance Data Factory (FDF), exposing Walmart transactional/finance data to LLM context *"in a cheaper, faster way at scale."*

**Key Objectives:**
- Scalability to hundreds of tables
- Fast onboarding of new datasets
- Cross-dataset intelligence
- Continual learning with user feedback

**Target Scale:** Certified data products, 100 tables, 1000 users

#### Positioning: What It Is and What It Is Not

| ✅ It Is | ❌ It Is Not |
|----------|-------------|
| A foundational solution to expose financial/transaction data to LLMs in a scalable, performant, cost-effective manner | The primary prescriptive/descriptive reporting system |
| An ad hoc diagnostic tool for analysts and leadership—on-demand exploration and root-cause analysis | A replacement for BI |
| An interactive diagnostic layer | — |

> This distinction is important for resume/interviews: you can show **product clarity** and avoidance of "replacing BI," instead **complementing it**.

#### Value Proposition Pillars

| Pillar | Description |
|--------|-------------|
| **Universal accessibility** | Users regardless of SQL/technical skill can explore enterprise data using natural language |
| **Context-aware conversation** | Multi-step exploration with context retention and follow-up support |
| **Trust through transparency** | SQL preview, reasoning engine, auditable logs to show the "why" behind results |
| **Enterprise-scale data access** | Query across raw/refined/cross-domain datasets, not only curated models |
| **Cross-dataset intelligence** | Automatic joins across domains (e.g., sales, assets) so users don't manually stitch tables |
| **Governed flexibility** | Dynamic RBAC and masking so sensitive columns are hidden/masked based on user access |
| **Modular architecture** | Agent-based design so capabilities can be added without major rewrite (e.g., forecasting agent, multi-table join agent) |

#### Design Principles / Constraints

- Minimize data movement; expose data where it exists
- Leverage existing investments (DDLs, semantic models, glossary, etc.)
- Minimize training / ground truth capture effort
- Ensure access control, security, privacy, governance
- Fail fast / learn maximum

> This is strong portfolio material because it shows you made **architectural choices tied to cost and governance**—not just "used an LLM."

#### Why It Matters in the Finance Analyst Workflow

In the FDF sandbox there are **thousands of analysts running suboptimal, high-latency queries** (hours in some cases), implying a productivity and performance opportunity if a governed agent can generate better queries and reduce iteration time.

#### Industry Analogs

Pinterest and Uber examples referenced as benchmarks for productivity improvements using Text-to-SQL systems (Querybook, QueryGPT).

---

## 5) Key Functional Scope

### 5.1 FDH: "Insights + Chat" Across Levels (L1–L4)

| Level | Surface |
|-------|---------|
| L1 | Metric tile |
| L2 | Metric detail page |
| L3 | Publication/report summary |
| L4 | Report page itself |

> Not a single chat window, but **embedded across the reporting workflow**.

### 5.2 Chat Outputs and Formats

**Supported Formats:**
- **Text:** Paragraphs, lists, definitions, Q&A, step-by-step guides
- **Tables:** Markdown or image (with intent to improve dynamic rendering)
- **Visuals:** Bar, line, waterfall, pie/donut, scatter, heat maps, etc. (many supported "as image")

*Note: Data visualization was desktop-only initially; mobile support was in development.*

### 5.3 Explainability and Trust UX

| Feature | Purpose |
|---------|---------|
| **Source attribution** | Show which dataset/report the answer came from; links back to source |
| **Explainability** | "Explain This" feature to clarify financial terms, metric logic, how a response is generated |
| **Transparency** | SQL preview / reasoning / auditable logs |

### 5.4 Feedback and Continuous Learning Loop

- Thumbs up/down with optional comments on summaries and chat responses
- Feedback classification and continuous learning as a **non-negotiable capability** to improve accuracy over time

---

## 6) Data Scope and "What Can It Answer?"

### 6.1 FDH Scope (Report-Centric)

**KPI Coverage:**
- Net sales, GMV/services, digital sales
- Basket metrics: transaction count, units, AUR, UPB, ticket size, etc.

**Comparisons:**
- vs LY, LY%, comp %, plan
- *Known constraint: "plan not available for basket metrics" in some cases*

**Supported Hierarchies:**
- **Merchandise:** SBU, department
- **Location:** Region/division/subdivision; country-level for international
- **Channel:** In-store, delivery, pickup

### 6.2 FDF Scope (Data-Factory-Centric, Cross-Dataset)

Finance and transaction data in Google BigQuery (GBQ), with early releases focusing on:

| Dataset | Status |
|---------|--------|
| General ledger actuals (monthly + daily) | In scope |
| Plan/forecast (OneStream) | In scope |
| Sales (Walmart US + PR; Sam's Club) | In scope |
| Transactions (Walmart; Sam's) | In scope |
| MUMD, external weather data | Later phases |

**Release 1 (October):** Sales + Txns + SAP GL + MUMD with actual/plan/forecast scenarios

---

## 7) Roadmap and Delivery Approach

### 7.1 FDH GenAI Strategy and Sequencing

1. Complete in-flight enhancements (e.g., SG&A bot, P&L narratives)
2. Educate finance on existing tools (role-specific demos/training)
3. Scale agent experience across finance (AI-enabled reports in FDH, Finance Assistant Agent)
4. Complete specific use cases in procurement, controllership, investor relations, etc.

### 7.2 LLM over FDF Phased Plan

| Phase | Timeline | Scope |
|-------|----------|-------|
| **Pilot** | June | Internal dev testing (sales + transactions, L1 actuals) |
| **MVP V1** | July | UAT with pilot users (add SAP GL actuals) |
| **MVP V2** | August | Add plan + forecast |
| **Release 1** | October | Production release; expand scope (MUMD) + features (images/history/access controls) |

### 7.3 Ways of Working

Sprint ceremonies: grooming, planning, demos, retros, daily standups with program tracking via internal documentation.

---

## 8) Non-Functional Requirements (Enterprise-Grade)

### Security, Access, and Compliance

- **SSO + RBAC:** Only show data permitted by role; prevent data leakage
- **Dynamic RBAC + masking** at the data layer for LLM over FDF
- **Encryption** in transit and at rest

### Data Consistency and Freshness

- GenAI outputs must reflect latest refresh
- Cache invalidation after refresh (prevent stale insights)

### Performance and Scalability

- Concurrency targets and telemetry (uptime, response time, error rate, conversation metrics)
- LLM over FDF latency: 20s–2m depending on complexity due to multi-step internal processing

### Transparency and Auditability

- Source attribution and auditable logs as trust mechanisms

### UX Friction Points Identified

| Issue | Resolution Approach |
|-------|---------------------|
| Context passing from report filters into chat | So users don't restate filters repeatedly |
| Chat window size limitations | Allow resizing for number-heavy outputs |
| Session timeout limitations | Request to extend session duration |

---

## 9) Success Metrics and KPIs

| Metric | Description |
|--------|-------------|
| **User adoption** | Active users per week |
| **Accuracy** | Data accuracy rate (measured via feedback) |
| **Impact** | Query-to-output time (median seconds from question to results) |

---

## 10) Key Risks / Challenges (and Mitigations)

### Typical Enterprise Text-to-SQL Challenges

| Challenge | Mitigation |
|-----------|------------|
| Complex schemas | Robust semantic layers/knowledge graphs |
| Ambiguous language | Clarifying dialog and intent resolution |
| Dynamic schema evolution | Continuous updating of retrieval/semantic layers |
| Security/compliance | Inherit permissions and protect sensitive data |

### Mitigation Patterns Implemented

- Ground-truth documentation and stewardship (reduce hallucination, enforce correctness)
- Source attribution + explainability UX (build trust, aid validation)
- Feedback loops + continuous learning (improve accuracy over time)

---

## 11) Resume/Portfolio Narrative

### 11.1 Resume-Safe Positioning Statement (2–3 lines)

> Senior Product Manager leading a GenAI finance decision-support platform that embedded AI Insights + conversational analytics into an enterprise Finance Data Hub and extended to a foundation-level Text-to-SQL data agent across finance/transaction datasets. Delivered governed, auditable natural-language analytics (summaries, Q&A, visuals) with enterprise-grade SSO/RBAC, data freshness guarantees, and continuous-learning feedback loops.

### 11.2 Bullet Bank (Pick 4–6)

#### Strategy / Product Definition

- Defined product vision and roadmap for a GenAI "Finance Assistant" enabling self-service natural-language analytics and automated KPI/report insights across FDH surfaces (metric tiles, drill-downs, report pages, publications)

- Established enterprise principles for scaling LLM access to finance/transaction data (minimize data movement, leverage existing semantic assets, enforce governance, fail-fast learning)

#### Delivery / Execution

- Led phased rollout from pilot → MVP → production for cross-dataset GenAI analytics, expanding coverage from sales/transactions to GL actuals and plan/forecast scenarios

- Operationalized sprint ceremonies, grooming, demos, and cross-functional commitments across product, architecture, engineering, data stewardship, UX, and program management

#### Platform + Governance

- Implemented enterprise-grade access controls (SSO/RBAC), encryption, and data masking patterns to ensure the assistant only returns permissible finance data

- Delivered trust and auditability features including source attribution (report/dataset references), explainability UX, and feedback-driven continuous improvement loops

#### User Experience + Adoption

- Shipped conversational workflows that preserve context (filters, hierarchy selections, time periods) and support multi-turn drilldowns, reducing repetitive query phrasing and improving usability

- Drove measurable success metrics framework for adoption, accuracy, and query-to-output latency; instrumented telemetry and feedback mechanisms to tune model performance

### 11.3 Keywords / Skills (ATS-Friendly)

GenAI product strategy, LLM applications, RAG, Text-to-SQL, semantic layer, governed analytics, enterprise data products, BigQuery / cloud data warehouse, role-based access control (RBAC), SSO, data privacy, observability/telemetry, experimentation, UX for analytics, feedback loops / continuous learning, cross-functional leadership

---

## 12) Portfolio Write-Up Recommendations

If publishing externally (portfolio site), recommend:

1. **Sanitized architecture diagram**
   - Experience layer → Orchestrator → Agents → Governed data access

2. **User story arc**
   - Pain: "Wait on analysts / write SQL"
   - Solution: "Ask question → see answer + chart + sources"

3. **Trust section**
   - RBAC, source attribution, refresh consistency, feedback loops

4. **Measured impact section**
   - Even without exact numbers yet, structure as:
     - Adoption
     - Time saved
     - Decreased escalations
     - Faster decisions
   - The KPI framework is already defined; insert real numbers later
