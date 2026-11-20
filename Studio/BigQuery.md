---
description: Model Google BigQuery datasets, tables, nested and repeated fields, views and partitioning in Hackolade Studio.
seoTitle: Google BigQuery data modeling with Hackolade Studio
image: lib/BigQuery workspace.png
---
# BigQuery

BigQuery is a serverless, highly-scalable, and cost-effective cloud data warehouse with an in-memory BI Engine and machine learning built in. BigQuery uses familiar ANSI-compliant SQL. BigQuery uses managed columnar storage, massively parallel execution, and automatic performance optimizations.

BigQuery manages the technical aspects of storing structured data, including compression, encryption, replication, performance tuning, and scaling. BigQuery offers the standard database concepts of tables, partitions, columns, and rows. BigQuery uses a columnar storage that supports semi-structured data — nested and repeated fields.

To perform data modeling for BigQuery with Hackolade, you must first download the BigQuery [plugin](DownloadadditionalDBtargetplugin.md).

Hackolade was specially adapted to support the data modeling of BigQuery, including datasets, tables and views, plus the generation of DDL Create Table syntax, in Standard SQL or in JSON Schema. Hackolade natively supports the ability to represent nested complex data types: STRUCT (record) and ARRAY. While BigQuery does not support Primary Key and Foreign Key constraints, you may declare them in Hackolade for documentation purposes, with no effect on DDL scripts. The application closely follows the BigQuery terminology and storage structure.

The data model in the picture below results from the data modeling of the [CMS Synthetic Patient Data OMOP](<https://redivis.com/Demo/datasets/1709> "target=\"_blank\""):\
![BigQuery workspace](<lib/BigQuery workspace.png>)

## Projects and datasets

Projects are top-level containers in Google Cloud Platform. They store information about billing and authorized users, and they contain BigQuery data. Each project has a name and a unique ID. In Hackolade, we show a property linking to a single project at the model level.

Datasets are top-level containers that are used to organize and control access to your tables and views. A dataset is contained within a specific project. It is the equivalent to a schema in RDBMS. Tables and views must belong to a dataset. Geographic location can be set at creation time only. After a dataset has been created, the location becomes immutable and can't be changed.

## Tables

A BigQuery table contains individual records organized in rows. Each record is composed of columns (also called fields). BigQuery supports the following table types: native tables backed by BigQuery storage, external tables backed by storage external to BigQuery, and views which are virtual tables defined by a SQL query.

## Views

A view is a virtual table defined by a SQL query. Views are read-only. Views are treated as table resources in BigQuery, with a type “VIEW”. The schemas of the underlying tables are stored with the view when the view is created. BigQuery's views are logical views, not materialized views. Because views are not materialized, the query that defines the view is run each time the view is queried.

## Unique, Primary, and Foreign Keys, and Not Null

Starting in March 2023, BigQuery introduced support for primary key constraints. At this point Google BigQuery has no support for unique constraints. There are also no foreign keys enforced by the database, although they can be defined in Hackolade for documentation purposes.

For each column, BigQuery allows the following modes: nullable (default), required (NULL values are not allowed), or repeated (columns containing an array of values of the specified data type.)

## Partitioning and clustering

Both partitioning and clustering can improve performance and reduce query cost. You may want to review the Google guidance on [when to use partitioning, clustering, or a combination of both](<https://cloud.google.com/bigquery/docs/clustered-tables#when_to_use_clustering> "target=\"_blank\"").

## Tags

In Google Cloud, [tags](<https://cloud.google.com/bigquery/docs/tags> "target=\"_blank\"") are key-value pairs that your organization defines in Resource Manager, then attaches to resources to grant or deny access through IAM. They are different from labels, which help you organize and filter resources.

In Hackolade Studio, you attach tags to a dataset, a table or a view in the **Tags** property of its Properties Pane: one row per tag, with its **Key** and its **Value**. Enter the key in its namespaced form, `PROJECT_ID/TAG_KEY` or `ORGANIZATION_ID/TAG_KEY`, for example the `my-project/environment` key with the `production` value.

For a column of a native or external table, you can attach one tag in the **Data governance tag** property. Your security administrator can then use it in BigQuery data policies, for column-level access control and data masking. The property is not available for a STRUCT column or an ARRAY of STRUCT: attach the tag to their nested fields instead.

In the DDL script, Hackolade Studio writes the tags in the `OPTIONS` of the CREATE SCHEMA, CREATE TABLE and CREATE VIEW statements (`tags=[...]`), and the data governance tag in the `OPTIONS` of the column (`data_governance_tags=[...]`). Currently, the ALTER script does not include tag changes.

> [!IMPORTANT]
> Hackolade Studio does not create tag keys and tag values in Google Cloud. They must exist in Resource Manager before you apply the script to an instance, and the key of a data governance tag must have the `DATA_GOVERNANCE` purpose. Otherwise, BigQuery rejects the statement.

## Data types

Every table is defined by a schema that describes the column names, data types, and other information. The schema of a table can be specified when it is created, or a table can be created without a schema and the schema is declared in the query job or load job that first populates it with data.

When a table schema is specified, each column must have a name and a data type. It may optionally have a column's description and a mode

BigQuery standard SQL lets you specify the following data types in your schema. Data type is required.

![BigQuery data types table](<lib/BigQuery data types table.png>)

## Forward-Engineering

Hackolade dynamically generates the DDL script to create datasets, tables, columns and their data types, for the structure created with the application.

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

![BigQuery DDL forward-engineering](<lib/BigQuery DDL forward-engineering.png>)

A button lets the user apply to a selected instance the script to create datasets, tables and views. Scripts can be generated in JSON Schema format as well.

## Reverse-Engineering

The connection uses a Google Cloud IAM credentials key file, as explained in [Connect to a BigQuery instance](ConnecttoaBigQueryinstance.md).

The Hackolade process for reverse-engineering of Google BigQuery datasets includes the execution of SQL statements to discover datasets, tables and views, columns and their data types, as well as the tags of datasets, tables and views, and the data governance tags of columns. If JSON is detected in text columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

For more information on Google BigQuery in general, please consult the [website](<https://cloud.google.com/bigquery/docs> "target=\"_blank\"").
