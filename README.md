# Snowflake Data Engineering: Zero to Expert

A portfolio of six hands-on Snowflake projects. They progress from core fundamentals, through real-time and geospatial visual builds, to enterprise-grade Financial Services platforms, and finish with an AI-powered capstone.

Each project lives in its own folder with a detailed README covering the architecture, setup, implementation steps and lessons learned.

---

## Why This Repo Exists

These labs were designed to:

1. **Increase in complexity:** each lab builds on the skills from the one before.
2. **Reflect enterprise data architecture:** medallion, dimensional modelling, data mesh, lakehouse, governance, DataOps and MLOps.
3. **Cover most of the Snowflake platform:** from `COPY INTO` to Cortex Agents.
4. **Be demo-able:** several labs ship with interactive frontends and maps.
5. **Focus on Financial Services:** the enterprise labs are set in wealth management, capital markets and financial crime, with UK/EU regulation in the background.

---

## The Labs

| #   | Project                                                                        | Level                 | Theme                                 | Frontend  |
| --- | ------------------------------------------------------------------------------ | --------------------- | ------------------------------------- | :-------: |
| 1   | [Retail Sales Analytics Foundation](./01-retail-sales-foundation/)             | Beginner              | Core platform fundamentals            | Dashboard |
| 2   | [London Property Explorer](./02-london-property-explorer/)                     | Beginner–Intermediate | Geospatial analytics                  |    ✅     |
| 3   | [Live London Tube Tracker](./03-live-tube-tracker/)                            | Intermediate          | Real-time streaming                   |    ✅     |
| 4   | [Governed Wealth Management Client Platform](./04-wealth-management-platform/) | Intermediate–Advanced | FSI governance & DataOps              |           |
| 5   | [Capital Markets Risk Lakehouse](./05-capital-markets-lakehouse/)              | Advanced              | FSI lakehouse, mesh & Spark migration |           |
| 6   | [AI Fraud & Financial Crime Intelligence](./06-ai-financial-crime/)            | Expert                | FSI AI/ML capstone                    |    ✅     |

---

### 1. Retail Sales Analytics Foundation

_Beginner · Core fundamentals_

A mid-size retailer wants its daily sales CSV exports moved out of spreadsheets. This lab loads CSV, JSON and Parquet files from internal and external stages with `COPY INTO`, and builds a star schema (`FACT_SALES` plus customer, product, store and date dimensions). It also sets up a role hierarchy, resource monitors, Time Travel and a zero-copy-cloned dev environment, and finishes with a Snowsight dashboard.

**Key features:** virtual warehouses, stages, file formats, `COPY INTO`, `VARIANT`/`FLATTEN`, RBAC, Time Travel, zero-copy cloning, resource monitors

---

### 2. London Property Explorer

_Beginner–Intermediate · Geospatial · Visual_

This lab loads HM Land Registry Price Paid data, ONS postcode lookups and London borough boundaries. It then uses Snowflake's geospatial capabilities to power an interactive Streamlit map of house prices by borough and postcode, trends over time and price heatmaps.

**Key features:** `GEOGRAPHY`, H3 indexing, `ST_*` functions, spatial joins, Streamlit in Snowflake

---

### 3. Live London Tube Tracker

_Intermediate · Real-time streaming · Visual_

This lab polls the TfL Unified API through an external access integration, streams the events in with Snowpipe Streaming, and processes them through a bronze/silver/gold medallion pipeline. The result is a live map of the tube network showing train positions, delays and crowding. Pipeline health is monitored with data quality checks and alerting.

**Key features:** external access integrations, Snowpipe Streaming, Streams, Tasks, Dynamic Tables, dbt (incremental models, snapshots), Data Metric Functions, Alerts, Streamlit / Snowpark Container Services

---

### 4. Governed Wealth Management Client Platform

_Intermediate–Advanced · FSI · Governance & DataOps_

This lab builds a client, portfolio and transaction platform for a wealth manager, with dbt at its core. PII is classified and masked automatically, and row-level security ensures advisers see only their own clients. The lab also covers GDPR right-to-erasure handling, full CI/CD with infrastructure-as-code and FinOps chargeback.

**Key features:** dbt (contracts, tests, Slim CI, dbt Projects on Snowflake), sensitive data classification, tag-based masking, row access policies, `ACCESS_HISTORY` lineage, Git integration, Snowflake CLI, budgets, query tags
**Regulatory context:** FCA Consumer Duty, GDPR, auditability

---

### 5. Capital Markets Risk Lakehouse

_Advanced · FSI · Lakehouse, Data Mesh & Spark Migration_

A bank runs Spark on a data lake for trade and market data. This lab builds an Iceberg lakehouse shared between Spark and Snowflake, then migrates a VaR / exposure aggregation job off Spark three ways: Snowpark Connect, Snowpark and dbt. The Trading, Risk and Finance domains publish data products in a data mesh. Regulatory reports are shared securely with a "regulator" account, and a Data Clean Room handles counterparty data. Failover groups provide operational resilience.

**Key features:** Iceberg tables, catalog integrations, Snowflake Connector for Spark, Snowpark Connect for Spark, Snowpark Migration Accelerator, Secure Data Sharing, listings, Data Clean Rooms, replication & failover groups, performance tuning
**Regulatory context:** BCBS 239, DORA, PRA operational resilience

---

### 6. AI Fraud & Financial Crime Intelligence

_Expert · FSI · AI/ML capstone · Visual_

This lab combines synthetic card and payment transactions with KYC documents and complaint call transc[118;1:3uripts. Snowflake ML trains fraud and AML scoring models, Cortex AI extracts KYC fields from PDFs, and a Cortex Agent explains why a customer was flagged. The frontend is an investigator console with a geospatial map of suspicious transaction flows, network graphs of linked accounts and case summaries generated by the agent.

**Key features:** Snowpark Python, Snowflake ML (Feature Store, Model Registry), Cortex AI functions, Document AI / `AI_EXTRACT`, Cortex Search, semantic views, Cortex Analyst, Cortex Agents, Snowpark Container Services, event tables
**Regulatory context:** AML/KYC, Consumer Duty, explainable and governed AI

---

## Feature Coverage

| Feature Area                    |  1  |  2  |  3  |  4  |  5  |  6  |
| ------------------------------- | :-: | :-: | :-: | :-: | :-: | :-: |
| Warehouses & compute            |  ●  |  ●  |  ●  |  ●  |  ●  |  ●  |
| Batch ingestion (`COPY INTO`)   |  ●  |  ●  |     |     |     |     |
| Semi-structured data            |  ●  |     |  ●  |     |     |     |
| RBAC & security                 |  ●  |     |     |  ●  |  ●  |     |
| Time Travel & cloning           |  ●  |     |     |  ●  |     |     |
| Geospatial                      |     |  ●  |  ●  |     |     |  ●  |
| Streamlit / frontends           |  ●  |  ●  |  ●  |     |     |  ●  |
| External access & APIs          |     |     |  ●  |     |     |  ●  |
| Streaming ingestion             |     |     |  ●  |     |     |     |
| Streams, Tasks, Dynamic Tables  |     |     |  ●  |  ●  |     |  ●  |
| dbt                             |     |     |  ●  |  ●  |  ●  |  ●  |
| Data quality & alerting         |     |     |  ●  |  ●  |     |  ●  |
| Governance (tags, masking, RAP) |     |     |     |  ●  |  ●  |  ●  |
| CI/CD & IaC                     |     |     |     |  ●  |  ●  |     |
| Cost management / FinOps        |  ●  |     |     |  ●  |     |  ●  |
| Iceberg / lakehouse             |     |     |     |     |  ●  |     |
| Spark interop & migration       |     |     |     |     |  ●  |     |
| Data sharing & clean rooms      |     |     |     |     |  ●  |     |
| Replication & DR                |     |     |     |     |  ●  |     |
| Performance tuning              |  ●  |     |     |     |  ●  |     |
| Snowpark Python                 |     |     |     |     |  ●  |  ●  |
| Snowflake ML                    |     |     |     |     |     |  ●  |
| Cortex AI / Search / Agents     |     |     |     |     |     |  ●  |
| Snowpark Container Services     |     |     |  ●  |     |     |  ●  |

---

## Architecture Concepts Covered

- **Data modelling:** Kimball star schemas, SCD Type 2, Data Vault 2.0, one big table
- **Pipeline patterns:** medallion architecture, CDC, Lambda vs Kappa, imperative vs declarative pipelines
- **Platform patterns:** data lake vs warehouse vs lakehouse, open table formats, data mesh, multi-account strategy
- **Governance:** least-privilege RBAC, classification, masking, row-level security, lineage, audit
- **Operations:** DataOps, CI/CD, infrastructure-as-code, FinOps, disaster recovery (RPO/RTO)
- **AI/ML:** MLOps lifecycle, RAG, semantic layers, governed and explainable AI

---

## Repository Structure

```
.
├── README.md
├── 01-retail-sales-foundation/
├── 02-london-property-explorer/
├── 03-live-tube-tracker/
├── 04-wealth-management-platform/
├── 05-capital-markets-lakehouse/
└── 06-ai-financial-crime/
```

Each project folder contains:

- `README.md`: scenario, architecture diagram, setup and walkthrough
- `sql/`: setup and teardown scripts
- `dbt/`, `app/` or `notebooks/`, where relevant
- `docs/`: diagrams, screenshots and write-ups

---

## Prerequisites

- A Snowflake account (a [free trial](https://signup.snowflake.com/) works for most labs)
- Snowflake CLI and Git
- Python 3.10+
- A cloud storage bucket (S3, Azure Blob or GCS) for external stage labs
- Docker, for the Snowpark Container Services labs
- dbt, for Labs 3–6

---

## Data Sources

| Lab | Data                                                                                |
| --- | ----------------------------------------------------------------------------------- |
| 1   | Synthetic retail data / Snowflake sample data                                       |
| 2   | HM Land Registry Price Paid Data, ONS Postcode Directory, London borough boundaries |
| 3   | TfL Unified API                                                                     |
| 4   | Synthetic wealth management clients, portfolios and transactions                    |
| 5   | Synthetic trades and market data                                                    |
| 6   | Synthetic payments, KYC documents and transcripts                                   |

> Check each source's licence and terms of use before publishing derived data or public demos.

---

## Cost Note

Every lab includes a teardown script and records the credits it consumed. Run the teardown when you finish to avoid ongoing charges.
