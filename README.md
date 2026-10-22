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

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[BigQuery ML (Google)](https://cloud.google.com/bigquery/docs/model-overview)**  

  Train and deploy ML models directly in BigQuery using SQL `CREATE MODEL` statements. Supports linear regression, logistic regression, k-means, XGBoost, AutoML, and imported TensorFlow models. **Workflow**: create model → preprocess features → tune hyperparameters → evaluate → infer → explain predictions . Consumption-based pricing on top of BigQuery compute.



- **[Snowflake Cortex](https://docs.snowflake.com/en/user-guide/snowflake-cortex/aisql)**  

  Snowflake's managed AI/ML service with LLM functions (`AI_COMPLETE`, `AI_CLASSIFY`, `EMBED_TEXT`) and ML functions. **Access control**: RBAC on model objects plus account-level allowlists; qualified identifiers are case-sensitive . Consumption-based pricing with per-token or per-function costs.



- **[Amazon Redshift ML](https://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_MODEL.html)**  

  Create models with SQL using Amazon SageMaker Autopilot under the hood. **Supported algorithms**: XGBoost, MLP, Linear Learner, KMeans, and Forecast. **Key parameter**: `AUTO ON` enables automatic preprocessor/algorithm/hyperparameter selection; `AUTO OFF` requires explicit configuration . Consumption-based pricing on Redshift compute plus SageMaker costs.



- **[Azure Synapse Analytics ML](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-predict)**  

  Score ONNX models inside dedicated SQL pools using T-SQL `PREDICT`. **Critical limitation**: models must be trained externally (not in Synapse) and converted to ONNX format. Models are stored as `varbinary(max)` hex strings and loaded via `COPY INTO` . Note: Serverless SQL pools do not support this feature.



- **[Oracle Autonomous Database (OML4SQL)](https://docs.oracle.com/en/database/oracle/machine-learning/oml-notebooks/)**  

  In-database machine learning with SQL-based algorithms including clustering, regression, text mining, time series, and partitioned models. **Key capability**: automatically extracts predictive features from text columns using Oracle Text . Enterprise-tier pricing.



- **[Databricks Lakehouse ML](https://docs.databricks.com/aws/en/reference/api)**  

  Unified data and AI platform with MLflow for experiment tracking, AutoML, and model serving. While not strictly "in-database" SQL ML, Databricks integrates Spark MLlib and MLflow into the lakehouse architecture . Consumption-based pricing.



- **[SingleStore](https://docs.singlestore.com/)**  

  Real-time database with AI functions (`AI_CLASSIFY`, `AI_EXTRACT`, `EMBED_TEXT`) for in-database text classification, extraction, and embeddings . Proprietary with free tier; consumption-based pricing.



- **[CockroachDB](https://www.cockroachlabs.com/docs/v26.2/cockroachdb-and-ai)**  

  **Not an in-database ML training platform**—CockroachDB provides vector search and similarity for RAG, plus MCP servers for AI-assisted development . Included for context: it's a data store for AI applications, not a model training engine.



- **[ClickHouse](https://clickhouse.com/docs/en/sql-reference/functions/regular-functions/machine-learning-functions)**  

  Native ML functions including `stochasticLinearRegression`, `stochasticLogisticRegression`, `naiveBayesClassifier`, and `evalMLMethod` for prediction. Models are trained in-database via aggregate functions and evaluated with `evalMLMethod` . Open-source core with managed cloud offering.



- **[Teradata Vantage Analytics](https://www.teradata.com/)**  

  In-database ML functions including `TD_DecisionForest` for training and prediction. Tree-based models are stored as JSON in the database . Enterprise-tier pricing.



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
