# BigQuery

BigQuery is a serverless, highly-scalable, and cost-effective cloud data warehouse with an in-memory BI Engine and machine learning built in.&nbsp; BigQuery uses familiar ANSI-compliant SQL.&nbsp; BigQuery uses managed columnar storage, massively parallel execution, and automatic performance optimizations. &nbsp;

&nbsp;

BigQuery manages the technical aspects of storing structured data, including compression, encryption, replication, performance tuning, and scaling. BigQuery offers the standard database concepts of tables, partitions, columns, and rows.&nbsp; BigQuery uses a columnar storage that supports semi-structured data — nested and repeated fields.

&nbsp;

To perform data modeling for BigQuery with Hackolade, you must first download the Redshift [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  

&nbsp;

Hackolade was specially adapted to support the data modeling of BigQuery, including datasets, tables and views, plus the generation of DDL Create Table syntax, in Standard SQL or in JSON Schema. Hackolade natively supports the ability to represent nested complex data types: STRUCT (record) and ARRAY.&nbsp; While BigQuery does not support Primary Key and Foreign Key constraints, you may declare them in Hackolade for documentation purposes, with no effect on DDL scripts.&nbsp; The application closely follows the BigQuery terminology and storage structure.

&nbsp;

The data model in the picture below results from the data modeling of the [CMS Synthetic Patient Data OMOP](<https://redivis.com/Demo/datasets/1709> "target=\"\_blank\""):

![Image](<lib/BigQuery%20workspace.png>)

&nbsp;

&nbsp;

## Projects and datasets

Projects are top-level containers in Google Cloud Platform. They store information about billing and authorized users, and they contain BigQuery data. Each project has a name and a unique ID.&nbsp; In Hackolade, we show a property linking to a single project at the model level.

&nbsp;

Datasets are top-level containers that are used to organize and control access to your tables and views.&nbsp; A dataset is contained within a specific project.&nbsp; It is the equivalent to a schema in RDBMS.&nbsp; Tables and views must belong to a dataset.&nbsp; Geographic location can be set at creation time only. After a dataset has been created, the location becomes immutable and can't be changed.

&nbsp;

## Tables

A BigQuery table contains individual records organized in rows. Each record is composed of columns (also called fields).&nbsp; BigQuery supports the following table types: native tables backed by BigQuery storage, external tables backed by storage external to BigQuery, and views which are virtual tables defined by a SQL query.

&nbsp;

## Views

A view is a virtual table defined by a SQL query. &nbsp; Views are read-only.&nbsp; Views are treated as table resources in BigQuery, with a type “VIEW”.&nbsp; The schemas of the underlying tables are stored with the view when the view is created.&nbsp; BigQuery's views are logical views, not materialized views. Because views are not materialized, the query that defines the view is run each time the view is queried.

&nbsp;

## Unique, Primary, and Foreign Keys, and Not Null

Google BigQuery has no primary key or unique constraints.&nbsp; There are also no foreign keys enforced by the database, although they can be defined in Hackolade for documentation purposes.

&nbsp;

For each column, BigQuery allows the following modes: nullable (default), required (NULL values are not allowed), or repeated (columns containing an array of values of the specified data type.)

&nbsp;

## Partitioning and clustering

Both partitioning and clustering can improve performance and reduce query cost. You may want to review [this page](<https://cloud.google.com/bigquery/docs/clustered-tables#when\_to\_use\_clustering> "target=\"\_blank\"") for circumstances under which to use&nbsp; partitioning, clustering, or a combination of both.

&nbsp;

## Data types

Every table is defined by a schema that describes the column names, data types, and other information. The schema of a table can be specified when it is created, or a table can be created without a schema and the schema is declared in the query job or load job that first populates it with data.

&nbsp;

When a table schema is specified, each column must have a name and a data type. It may optionally have a column's description and a mode

&nbsp;

BigQuery standard SQL lets you specify the following data types in your schema. Data type is required.

&nbsp;

![Image](<lib/BigQuery%20data%20types%20table.png>)

&nbsp;

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the DDL script to create datasets, tables, columns and their data types, for the structure created with the application.

&nbsp;

![Image](<lib/BigQuery%20DDL%20forward-engineering.png>)

&nbsp;

&nbsp;

A button lets the user apply to a selected instance the script to create datasets, tables and views.&nbsp; Scripts can be generated in JSON Schema format as well.

&nbsp;

## Reverse-Engineering

The connection is established using a connection using Google Cloud IAM credentials key file:

&nbsp;

![Image](<lib/BigQuery%20connection%20settings.png>)

&nbsp;

&nbsp;

The Hackolade process for reverse-engineering of Google BigQuery datasets includes the execution of SQL statements to discover datasets, tables and views, columns and their data types.&nbsp;

&nbsp;

For more information on Google BigQuery in general, please consult the [website](<https://cloud.google.com/bigquery/docs> "target=\"\_blank\"").

