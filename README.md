# Awesome-In-Database-Machine-Learning

## Top In-Database Machine Learning Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on SQL-Native Model Training, In-Database Inference & Self-Hosted ML Extensions*  

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **In-Database Machine Learning**. These tools enable data teams to train, evaluate, and deploy ML models directly inside the database using SQL—eliminating data movement, reducing latency, and keeping sensitive data within existing security boundaries.



**Examples** include BigQuery ML, Snowflake Cortex, Amazon Redshift ML, Azure Synapse ML, Oracle OML4SQL, Databricks, and MindsDB (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, SQL-native ML, and transparent model training—ideal for organizations that cannot move data out of their databases, avoid per-query ML pricing, and require auditable model workflows. The open-source landscape is anchored by **Apache MADlib** (the mature in-database ML library for PostgreSQL/Greenplum), **MindsDB** (the AI query engine that federates across data sources), and **PostgresML** (the PostgreSQL extension for training and inference), with **ClickHouse** and **SingleStore** offering native SQL ML functions.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [Sector Overview & Market Dynamics](#sector-overview--market-dynamics)
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## Sector Overview & Market Dynamics

The global in-database analytics and Data Science & Machine Learning (DSML) platform market is estimated at approximately **$170B – $220B** (projected to exceed $750B+ into the 2030s at an ~18–30% CAGR). The sector is **moderately concentrated to oligopolistic**—dominated at the infrastructure layer by hyperscalers (Alphabet, Microsoft, Amazon) and dedicated data giants (Databricks, Snowflake), while remaining dynamic and fragmented at the specialized engine, vector search, and open-source extension tiers.

## SaaS/Hosted Platforms

| Platform | Provider / Company | Company Size (Valuation / Market Cap) | Key In-Database ML Capabilities | Specific Starting Price | Free Tier / Trial Limits |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **[BigQuery ML](https://cloud.google.com/bigquery/docs/model-overview)** | Google (Alphabet) | ~$4.15 Trillion (Market Cap) | Train and deploy ML models directly in BigQuery with SQL (`CREATE MODEL`). Supports linear/logistic regression, k-means, XGBoost, AutoML, and TensorFlow inference. | $6.25 per TB (on-demand query data scanned beyond free allowance); ML model training compute billed at $250.00 per TB for AutoML or equivalent slot compute | 10 GB active storage and 1 TB of query data processed per month (Free Forever) |
| **[Azure Synapse Analytics ML](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-predict)** | Microsoft | ~$3.95 Trillion (Market Cap) | Native scoring of pre-trained ONNX models directly inside dedicated SQL pools via T-SQL `PREDICT` (models loaded via `COPY INTO`). | $1.51 per hour for Dedicated SQL Pool (DW100c base tier) + $23 per TB/month storage | 30-day free trial with $200 Azure credits (No permanent free tier for dedicated SQL pools) |
| **[Amazon Redshift ML](https://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_MODEL.html)** | Amazon (AWS) | ~$2.83 Trillion (Market Cap) | Create, train, and tune ML models in Redshift via SQL powered under the hood by SageMaker Autopilot (`AUTO ON`/`OFF`). | $0.25 per hour (Provisioned `dc2.large` node on-demand) or $0.375 per RPU-hour ($1.50/hr for base 4-RPU Serverless) | 2-month free trial of 750 hours/month on `dc2.large` node (Provisioned), or 90-day trial with $300 credits (Serverless) |
| **[Oracle Autonomous Database (OML4SQL)](https://docs.oracle.com/en/database/oracle/machine-learning/oml-notebooks/)** | Oracle | ~$396 Billion (Market Cap) | Native in-database algorithms (clustering, regression, text mining, time-series) executed via SQL and PL/SQL with automated text feature extraction. | $0.336 per ECPU-hour (Serverless Transaction Processing/Lakehouse, license included) or $0.0807 per ECPU-hour (BYOL) | 2 Autonomous Database instances with 20 GB storage each & up to 30 sessions (Always Free Forever) |
| **[Databricks Lakehouse ML](https://docs.databricks.com/aws/en/reference/api)** | Databricks | ~$190 Billion (Private Valuation) | Unified lakehouse platform embedding Spark MLlib, native AutoML, MLflow tracking, and serverless model endpoints on lakehouse data. | $0.07 per DBU (AI & Model Training/Serving entry rate) or $0.15 per DBU (Jobs Compute) + cloud VM infrastructure | 14-day free trial with $400 DBU platform credits; Databricks Free Edition provides forever-free serverless compute with daily quotas |
| **[Snowflake Cortex](https://docs.snowflake.com/en/user-guide/snowflake-cortex/aisql)** | Snowflake | ~$111 Billion (Market Cap) | SQL-native ML functions and Cortex AI LLM functions (`AI_COMPLETE`, `AI_CLASSIFY`, `EMBED_TEXT`) with strict RBAC access controls. | $2.00 per Snowflake Credit (Standard Edition on-demand); $3.00 per credit (Enterprise Edition) | 30-day free trial with $400 usage credits across compute and storage (No permanent free tier) |
| **[CockroachDB](https://www.cockroachlabs.com/docs/v26.2/cockroachdb-and-ai)** | Cockroach Labs | ~$5 Billion (Private Valuation) | Distributed SQL database offering native vector search, embeddings similarity, and MCP server integrations for real-time AI apps. | $0.18 per hour (Standard provisioned cluster) or pay-as-you-go request units on Serverless | 50 million Request Units (RUs) and 10 GiB storage per month (Free Forever) |
| **[Teradata Vantage Analytics](https://www.teradata.com/)** | Teradata | ~$2.82 Billion (Market Cap) | Enterprise in-database predictive ML functions (`TD_DecisionForest`, clustering, GLM) storing trained model artifacts as JSON in the database. | $0.22 per minute elastic compute (~$4,800/month baseline cloud tier commitment) + $23 per TB/month storage | 30-day free trial sandbox with interactive pre-loaded environments (No permanent free tier) |
| **[ClickHouse Cloud](https://clickhouse.com/docs/en/sql-reference/functions/regular-functions/machine-learning-functions)** | ClickHouse Inc. | ~$2 Billion (Private Valuation) | Fast analytical engine with native SQL ML aggregate functions (`stochasticLinearRegression`, `naiveBayesClassifier`, `evalMLMethod`). | ~$0.22 to $0.75 per compute unit-hour (scale-to-zero when idle, dev configurations start at ~$66/month) + $25/TB-month storage | 30-day free trial with $300 usage credits (scale-to-zero compute supported) |
| **[SingleStore Helios](https://docs.singlestore.com/)** | SingleStore | ~$1.3 Billion (Private Valuation) | Real-time distributed SQL database with built-in AI functions (`AI_CLASSIFY`, `AI_EXTRACT`, `EMBED_TEXT`) and vector index execution. | $0.99 per hour (Standard S-00 entry workspace, 2 vCPU / 16 GB RAM) + $0.023 per average GB/month storage | 1 GB compressed storage (~4 GB raw data) with standard SQL and vector search features (Free Forever Shared Tier) |

## Open-Source GitHub Projects



- **[Apache MADlib](https://github.com/apache/madlib)**  

  **The mature in-database ML standard for PostgreSQL and Greenplum.** Apache Top-Level Project with data-parallel implementations of mathematical, statistical, graph, and ML methods for structured and unstructured data . **Key advantages**: uses MPP architecture's full compute and memory—no sampling required; familiar SQL interface; scales with additional nodes . **Supported platforms**: Greenplum 6.x/5.x and PostgreSQL 12.x/11.x (last three major versions tested per release) . Apache 2.0 licensed. Best for PostgreSQL/Greenplum shops that want proven, scalable SQL-native ML without data movement.



- **[MindsDB](https://github.com/mindsdb/mindsdb)**  

  **The AI query engine and MCP server.** Connects and unifies data across databases, vector stores, and applications; enables creating, serving, and fine-tuning AI models in real-time from federated data sources . **Positioning**: "The only MCP Server you'll ever need"—exposes ML capabilities to AI agents via Model Context Protocol. **Note**: MindsDB describes itself as an "AI data automation solution" rather than strictly in-database ML—it federates queries across sources rather than training inside a single database. GPL-3.0 licensed (core). Best for teams building AI applications that need to query and learn from data across multiple systems.



- **[PostgresML](https://github.com/postgresml/postgresml)**  

  A PostgreSQL extension for training and inference directly in the database. Supports GPU acceleration and integrates with Hugging Face models. Best for PostgreSQL users wanting modern ML (including embeddings and LLM inference) without external services.



### Additional Strong Open-Source Options



- **pgml** — The extension underlying PostgresML, available separately for PostgreSQL deployments. Best for teams that want the ML extension without the full PostgresML platform.

- **PL/Python + scikit-learn** — Not a framework, but a pattern: use PostgreSQL's `plpython3u` extension to call scikit-learn inside SQL functions. Best for ad-hoc in-database ML when MADlib's algorithm coverage is insufficient.

- **Frameworks for building custom systems**: Use **Apache MADlib** for proven SQL-native ML on PostgreSQL/Greenplum. Use **MindsDB** when you need to federate queries and models across multiple data sources. Use **ClickHouse** native functions for lightweight regression/classification on ClickHouse data. For PostgreSQL with GPU needs, use **PostgresML**. For data that must stay in Redshift/Snowflake/BigQuery, use the respective managed service.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- **"In-database" means different things across tools**: BigQuery ML, Redshift ML, and MADlib train models inside the database engine. Azure Synapse ML only scores pre-trained ONNX models—training must happen externally . MindsDB federates across sources rather than training in a single database .

- **Managed services charge for compute beyond the database**: Redshift ML uses SageMaker under the hood ; BigQuery ML consumes BigQuery slots. Budget accordingly.

- **Open-source in-database ML has platform constraints**: MADlib supports PostgreSQL and Greenplum, not MySQL, SQL Server, or Oracle . Verify compatibility before committing.



---



**Made for data engineers, analytics teams, and organizations that want ML without moving data.**  

Let's make in-database machine learning more open, SQL-native, and accessible.
