# RTP (Real-time Platform) Overview

## 1) What RTP is and what it does for Walmart

RTP (Real-time Platform) is Walmart's scalable event streaming platform within Customer Data & Identity, designed to ingest, enrich, and serve real-time customer and commerce events to downstream teams and systems. In practical terms, RTP operationalizes "real-time 101": each event is a snapshot of a customer interaction (e.g., browsing/searching, transacting, membership change), and RTP's job is to move those snapshots continuously, at scale, with the right enrichment and reliability so they can be actioned immediately by other products and teams (CRM, Ads, Savings/Rewards, Benefits, etc.).

### Current scale and business impact (as represented in the FY27 overview)

RTP is operating at very high throughput and has become a core dependency for multiple downstream functions:

- **16M+ events/min** flowing through the platform
- **15 downstream teams** consuming RTP outputs
- **$2.7B+** enabled business value cited as the aggregate GMV enabled by downstream teams (explicitly not attributable to RTP alone)
- **E2E peak latency < 60 seconds**, with a pipeline model of Ingest → Enrich → Serve

### What RTP streams (event domains)

RTP's upstream event coverage spans critical omni-customer and omni-commerce signals, including:

- Online transactions
- Offline transactions
- App / web interactions
- W+ membership & benefit usage
- Customer savings & rewards data
- List/registry behaviors (e.g., "hearting")
- Profile/identity and related enrichments

### Who RTP serves (downstream consumers)

Downstream teams consume RTP for both customer experience and operational outcomes, including:

- **Savings** (e.g., real-time savings aggregation and presentation)
- **CRM** (campaign triggers, facets, membership-driven personalization)
- **Benefits** (real-time benefits computation and summary)
- **Marketing** (retargeting/attribution/3P partner activation)
- **Rewards** (iBotta, B2B rewards, return incentives, W+ cashback calculations)
- **AdTech** (real-time targeting)
- Additional consumers like P13N, Voice/Converse, Spend Analyzer use cases

---

## 2) Why RTP matters: omnichannel customer interactions that only work in real-time

A key way to describe RTP's value is that it turns raw customer actions into actionable signals across channels—web/app, email/push, in-store, and post-purchase—fast enough to influence the next customer touchpoint.

The FY27 overview deck provides an illustrative "omni interaction" chain such as:

1. customer clicks an ad,
2. "hearts" an item / saves to list,
3. receives triggered messaging tied to rewards,
4. in-store detection and targeted guidance,
5. self-checkout identity experience,
6. savings/rewards updated in near real-time.

This framing is important because it explains RTP as an **experience-enabling platform** (not just a Kafka pipeline): the platform exists so that downstream products can react to customer intent and context quickly and consistently.

---

## 3) RTP 2.0: platform modernization and step-change outcomes

A major component of the RTP story is the move from legacy infrastructure patterns to RTP 2.0 (2025+), with explicit performance and productivity targets, including:

- **Latency reduction** from 5–6 hours E2E (SLA breaches) to < 2 minutes E2E (SLA compliant; >95% reduction)
- **Enablement time reduction** from ~2 sprints to < 1 sprint for a new interaction use case
- **Observability uplift** through centralized dashboards/alerts and proactive reconciliation/backfill patterns
- **Lower tooling footprint** and reduced operational cost / "firefighting," with higher release quality

This matters for your summary because your UI/portal work directly advances the RTP 2.0 thesis: it helps convert RTP from "infrastructure that only the platform team understands" into a productized platform with self-serve discoverability and trust-building transparency.

---

## 4) FY27 vision and roadmap: where RTP is going

### FY27 vision

The stated vision is for RTP to evolve into a **reliable, scalable global streaming platform** used to stream real-time enriched events globally.

### GTM trajectory (FY27)

The FY27 GTM sequence described includes:

1. Enrich CDP assets in real time,
2. Provide enriched customer intelligence to current consumers,
3. Increase adoption across Sam's and International,
4. Explore operational use cases in US / Sam's / Intl (discovery stage items noted).

### Platform evolution: "Front-end that builds trust" + "Back-end that scales"

The FY27 roadmap explicitly calls out two platform pillars:

#### A) Front-end platformization

- **Self-serve catalogue + flow visualization**
  - Intended impact: reduce discovery time by ~60% and increase adoption of real-time metrics across teams
- **Observability and monitoring dashboard**
  - Monitor system health and flows in real time; customize & subscribe for alerts

#### B) Back-end platformization

- **Contract registry** to flag schema changes, reduce escalations (target: cut by 50%)
- **Cost metering** so downstream teams can understand estimated pricing and allocate to cost centers
- **Agentic discovery, development and testing** (NL discovery, faster deployments, synthetic tests)

This roadmap aligns tightly with what you built: the flow visualization portal is a concrete implementation of the front-end "trust" layer; the RAG chatbot is a direct step toward "agentic discovery for attributes" and accelerated enablement.

---

## 5) The scaling/platformization initiatives being executed this year

The "RTP – Platform initiatives" one-pager lays out six "big rock" items that collectively operationalize platformization and scaling. These include:

### RTP UI / Portal (SPOC: you)

- **Goal:** centralized, secure, intuitive interface to manage/monitor real-time pipelines; support access, configuration, analysis with minimal latency
- **Planned modules:** observability, data dictionary, cost metering, self-serve pipeline management (with RBAC restrictions for RTP engineers)
- **Integration approach:** explore Grafana ingestion via DB/API vs iframe embedding

### Schema registry / contracts

- Central registry and JSON-based data contracts
- **Expected outcomes:** proactive schema validation/contract enforcement (reduce errors by 50%), improved metadata governance, and acceleration via automated regression testing

### Savings contract generalization

- Standardize savings contracts into a common schema across pipelines, deliver to savings platform via a single pipeline
- **Expected:** eliminate downstream rework and improve savings platform development velocity

### RTP as source for ST & CDL (single source of truth for RT/NRT)

- Reduce duplicate data consumption cost within CDP/DCA
- **Initial POC idea:** branch raw payloads to GCS (L0) and evaluate performance (start with transactions)

### Integration test suite

- End-to-end validation for each data flow, leveraging schema contracts
- **Expected:** catch mismatches pre-prod, CI/CD regression automation, traceability tied to schema versions

### Unified processing framework (DIFT + LENS consolidation)

- Reduce redundant layers/topics and simplify governance while preserving throughput
- **Plan:** stress test baseline and roll out from low-impact to high-impact pipelines

---

## 6) Your delivered work: what you built, why it matters, and how it accelerates RTP adoption

### A) You built the RTP Flow UI: end-to-end event lineage visualization as a product surface

You delivered the RTP Flow user interface that visualizes and explains the end-to-end flow of events across the RTP ecosystem. In the artifact you shared, the UI presents a multi-stage lineage view from:

**Upstream team → Upstream topic → rtp.xx topic → RTP canonical topic → Downstream team**

With interactive controls such as Search nodes, Filter Columns, Show Sections, Download CSV, Upload CSV, and Attributes (indicating the UI is designed for both exploration and operational usage).

This is not "just a diagram." It productizes RTP's complexity into a self-serve discovery and enablement surface:

**Downstream teams can quickly answer:**
- What events exist?
- Where do they come from?
- How do they map from producer topics to RTP topics?
- Which teams consume them today?
- What attributes are available and how should they interpret them?

It reduces cycle time for enablement and minimizes dependency on tribal knowledge or repeated 1:1 support.

This maps directly to the FY27 platform evolution requirement: a "Front-End that builds trust by enabling consumers to monitor flows and browse the event catalogue."

### B) Business impact: accelerating downstream enablement and attribute unlock

Your portal/flow work drives value in two explicit ways:

1. **Shorter discovery-to-consumption path for downstream teams**
   - Instead of teams reverse engineering producer topics, requesting docs, or waiting for platform deep-dives, they can use the UI to self-navigate the catalog and lineage. This directly supports the FY27 goal that self-serve catalog + flow visualization reduces discovery time and increases adoption of real-time metrics across teams.

2. **Faster activation of high-value attributes and events**
   - By making the data surface area legible and searchable, teams can unlock attributes faster, which in turn accelerates delivery of downstream outcomes such as marketing triggers, ad targeting, savings/rewards updates, benefits computation, and other "real-time intelligence" experiences. RTP overall is positioned as enabling major value across these consumers.

### C) You integrated an interactive chatbot with RAG for "ask-and-learn" discovery

You extended the portal beyond static visualization by embedding a chatbot that allows teams to ask natural-language questions and get grounded answers using retrieval-augmented generation (RAG).

Strategically, this is a material platform capability, because it:

- Converts the UI from "navigation" into "assisted discovery"
- Reduces repetitive support load on RTP engineers and PMs (fewer Slack pings, fewer ad hoc meetings)
- Moves RTP toward the FY27 direction of agentic discovery for attributes and faster deployment cycles (training discovery on RTP schema/metadata, generating artifacts like specs and regression scaffolds).

From a platformization standpoint, your RAG chatbot is an early version of the longer-term "agentic discovery, development and testing" theme described in the FY27 roadmap.

---

## 7) How your work supports the FY27 "big rocks" (tie-back for leadership narrative)

A strong way to present your contribution is to tie it explicitly to RTP's FY27 "big rocks" and measurable outcomes:

### Big Rock: Platformization + Self-Serve Discovery

The AOP FY27 big rock calls out a Searchable RTP Contract Catalog and lineage visibility, with targeted reductions in lead time and reclaimed story points.

Your Flow UI is the concrete front-end foundation for that self-serve catalog and lineage experience (and the chatbot makes it queryable).

### Big Rock: Reporting, Observability & Alerts

The FY27 roadmap calls for dashboards/alerts, real-time visibility, and consumer-specific health reporting.

Your portal is the natural container for those modules (as also described in the "RTP UI/Portal" initiative scope: observability, cost metering, data dictionary, and role-based management).

### Big Rock: Real-Time Identity & Customer Intelligence Enrichment

RTP's FY27 plan is to enrich events using customer intelligence signals (demographics, persona, engagement propensity, etc.) and make that enrichment available to consumers.

Your catalog/flow UI is the mechanism that makes those enriched attributes discoverable and understandable—critical for adoption once the enrichment surface expands (CAS attributes span account fundamentals, demographics, socio-economic indicators, registry signals, persona, purchase/spend metrics, propensities, CRM/digital engagement, and more).

---

## 8) Suggested "pipeline leadership" framing using the flow work you delivered

Even if your primary ownership is the platform UI, you can credibly describe pipeline leadership in terms of cross-domain enablement, because your flow product spans and operationalizes visibility across multiple major pipelines, such as:

- Transactional domains (online/offline)
- Interactions domains (app/web)
- List/registry ("hearting") domains
- Membership domains
- Profile/identity-related domains

This matters because RTP's downstream consumers do not experience RTP as "one pipeline"—they experience RTP as a catalog of event products. Your work turned those pipelines into a coherent product surface.

---

## 9) Near-term next steps (positioned as "what you are driving next")

Based on the FY27 roadmap and the platform initiatives list, a clean forward-looking statement for you is:

### Expand RTP Portal from "flow visualization" into the full self-serve platform surface

- Add/finish core modules: data dictionary, observability dashboards, and cost metering
- Implement RBAC-restricted "self-serve pipeline management" for RTP engineers (as planned)

### Deep integration with schema registry / contracts

- Expose contract versions and schema diffs directly in the portal
- Use contract metadata as a first-class retrieval source for the chatbot (improves accuracy and governance)

### Operationalize the "agentic discovery" direction

Evolve the chatbot from Q&A into guided workflows:
- "Find correct attributes"
- "Show lineage"
- "Draft enablement spec"
- "Estimate blast radius"
- "Suggest regression checks"

(These are explicitly aligned with FY27's agentic discovery + regression themes.)

### Drive adoption and measure the portal's ROI

Track:
- Time-to-discovery
- #teams onboarded
- #enablement requests reduced
- #catalog searches
- #chat queries
- Reduction in escalations related to schema misunderstandings

---

## 10) Copy-paste accomplishment bullets (performance review / promo packet style)

You can use the following verbatim or adapt:

- **Built and delivered the RTP Flow UI**, a self-serve lineage and discovery portal that visualizes the end-to-end flow of real-time events from producers to RTP topics to downstream consumers, materially reducing downstream dependency on tribal knowledge and accelerating enablement across teams. (Aligns with FY27 platform evolution: self-serve catalog + flow visualization.)

- **Implemented an interactive RAG-based chatbot** embedded in the RTP Flow experience, enabling downstream teams to ask natural-language questions about RTP events/attributes and receive grounded answers, reducing repetitive support load and accelerating attribute discovery.

- **Led the "RTP UI/Portal" platformization initiative** to evolve the portal into a centralized, secure interface for observability, data dictionary, cost metering, and role-based pipeline management, including exploration of Grafana integration patterns.

- **Productized RTP transparency and trust** by converting complex Kafka/topic-level plumbing into a coherent catalog and flow surface—positioning RTP for broader adoption across US, Sam's, and International as RTP scales volume and catalog breadth.
