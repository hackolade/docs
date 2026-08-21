# dbt artifacts

[dbt](<https://www.getdbt.com/> "target=\"\_blank\"") is a SQL-first transformation workflow that lets teams quickly and collaboratively deploy analytics code following software engineering best practices like modularity, portability, CI/CD, and documentation. It helps teams work directly within the warehouse to produce trusted datasets for reporting, ML modeling, and operational workflows.&nbsp;

&nbsp;

dbt performs the T (Transform) of ETL (actually ELT) but it doesn’t offer support for Extraction and Load operations. It allows companies to write transformations as queries and orchestrate them in a more efficient way.&nbsp;

&nbsp;

Multiple SQL-like [databases](<https://docs.getdbt.com/docs/trusted-adapters> "target=\"\_blank\"") are supported currently, including: BigQuery, Databricks, Hive, MySQL, Oracle, PostgreSQL, Redshift, Snowflake, SQL Server, Synapse, and Teradata.

&nbsp;

For selected targets, Hackolade Studio facilitates the transformation of data in your warehouse with dbt, by letting you generate dbt property files directly from your Hackolade model.&nbsp; This includes model properties files (models.yml) for your transformation models, and source definition files (sources.yml) for the raw tables your models build on. The feature is available in Tools \> Forward-Engineering \> dbt Property Files.

&nbsp;

Hackolade Studio supports&nbsp;

\- the generation of [dbt schema models](<dbtschemamodels.md>) with dbt-specific model-level properties, column-level properties, and custom properties to be included in dbt meta.

\- the generation of [dbt sources.yml files](<dbtsources.md>)

\- plus [dbt tests and custom headers and footers](<Commontodbtmodelsandsources.md>)

