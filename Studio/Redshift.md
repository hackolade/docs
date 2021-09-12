# Redshift

Amazon Redshift is a data warehouse product as part of Amazon Web Services.&nbsp; It is built on top of technology from massive parallel processing (MPP) to handle large scale data sets and database migrations.&nbsp; Redshift is a columnar database better suited for analytics, and thus a more appropriate platform for a data warehouse.&nbsp; When data is loaded into a Redshift table, Redshift distributes the rows of the table across nodes according to the table's distribution style.

&nbsp;

Amazon Redshift is based on PostgreSQL, but they have a number of very important differences.&nbsp; Amazon Redshift is specifically designed for online analytic processing (OLAP) and business intelligence (BI) applications, which require complex queries against large datasets.&nbsp; Amazon Redshift does not support tablespaces, table partitioning, inheritance, and certain constraints. Redshift doesn't support indexes. Instead, each table has a sort key, which determines how rows are ordered when the data is loaded.&nbsp; Redshift doesn't enforce primary key, foreign key, or uniqueness constraints, although primary keys and foreign keys are used as planning hints and they should be declared if ETL process or some other process in applications to enforce their integrity.

&nbsp;

To perform data modeling for Redshift with Hackolade, you must first download the Redshift [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  

&nbsp;

Hackolade was specially adapted to support the data modeling of Redshift, including schemas, tables and views, plus the generation of DDL Create Table syntax. In particular, Hackolade has the unique ability to model complex semi-structured objects stored in columns of the [SUPER data type](<https://docs.aws.amazon.com/redshift/latest/dg/ingest-super.html> "target=\"\_blank\"").&nbsp; The reverse-engineering function, if it detects JSON documents in a column with the SUPER data type, will sample records and infer the schema to supplement the DDL table definitions.&nbsp; The application closely follows the Redshift terminology and storage structure.

&nbsp;

The data model in the picture below results from the data modeling of the [sample TICKIT data](<https://docs.aws.amazon.com/redshift/latest/gsg/rs-gsg-create-sample-db.html> "target=\"\_blank\""):

![Image](<lib/Redshift%20workspace.png>)

&nbsp;

&nbsp;

## Clusters and databases

An Amazon Redshift cluster consists of nodes. Each cluster has a leader node and one or more compute nodes, the configuration of which should be done through the Redshift console.&nbsp; Within a cluster, the console prompts for the creation of a database. The console implies that only a single database can be created per cluster.&nbsp; While it is possible to create multiple databases in a single cluster, a Hackolade model corresponds to a single Redshift cluster/database.&nbsp; If you have more additional databases inside a cluster, you should create a Hackolade model per database.

&nbsp;

## Schemas

A database contains one or more named schemas. Each schema in a database contains tables and other kinds of named objects. By default, a database has a single schema, which is named PUBLIC. You can use schemas to group database objects under a common name. Schemas cannot be nested.

&nbsp;

## Tables

As you plan your database, certain key table design decisions heavily influence overall query performance. These design choices also have a significant effect on storage requirements, which in turn affects query performance by reducing the number of I/O operations and minimizing the memory required to process queries.In [these pages](<https://docs.aws.amazon.com/redshift/latest/dg/c\_designing-tables-best-practices.html> "target=\"\_blank\""), you can find a summary of the most important design decisions and presents best practices for optimizing query performance.

&nbsp;

## Unique, Primary, and Foreign Keys, and Not Null

As mentioned, Redshift doesn't support indexes. Redshift also doesn't enforce primary key, foreign key, or uniqueness constraints, though primary keys and foreign keys should be declared to be used as planning hints, and for better comprehension of the data model.&nbsp; The NOT NULL parameter is enforced.

&nbsp;

## Distribution style and keys

The goal in selecting a table distribution style is to minimize the impact of the redistribution step by locating the data where it needs to be before the query is run. Some suggestions are made [here](<https://docs.aws.amazon.com/redshift/latest/dg/c\_best-practices-best-dist-key.html> "target=\"\_blank\""):

\- distribute the fact table and one dimension table on their common columns

\- choose the largest dimension based on the size of the filtered dataset

\- choose a column with high cardinality in the filtered result set

\- change some dimension tables to use ALL distribution

or specify AUTO for the distribution style to have Amazon Redshift choose the appropriate distribution style,&nbsp;

&nbsp;

## Data types

Each value that Amazon Redshift stores or retrieves has a data type with a fixed set of associated properties. Data types are declared when tables are created. A data type constrains the set of values that a column or argument can contain.&nbsp; The following table lists the data types that you can use in Amazon Redshift tables.

&nbsp;

![Image](<lib/Redshift%20data%20types%20table.png>)

&nbsp;

With the flexible semistructured SUPER data type, currently only available in preview, Redshift can receive and ingest schemaless JSON into a SUPER value.&nbsp; The SUPER column requires no schema modifications while ingesting the irregular structures of schemaless JSON. The native format used for the SUPER data type is a binary format that requires lesser space than the JSON value in its textual form. This enables faster ingestion and runtime processing of SUPER values at query time.

&nbsp;

Composite data types (multiple) are not supported by Redshift, except inside JSON documents in the SUPER data type.&nbsp; Hackolade has the unique ability to detect JSON and infer the schema during reverse-engineering.

&nbsp;

## (Materialized) Views

A *materialized view* contains a precomputed result set, based on an SQL query over one or more base tables. This is to avoid processing complex queries on large tables that can be expensive in terms of system resources and the time it takes to compute the results, as they perform multiple-table joins and aggregations on tables that contain billions of rows. 

&nbsp;

A view allows the result of a query to be accessed as if it were a table. The query is specified in the CREATE VIEW statement.&nbsp; Views serve a variety of purposes, including combining, segregating, and protecting data.

&nbsp;

Hackolade supports Redshift (materialized) views, via a SELECT of columns of the underlying base table, to present the data of the base table with a different primary key for different access patterns. &nbsp;

&nbsp;

## Functions and Procedures

You can create a custom scalar user-defined function (UDF) using either a SQL SELECT clause or a Python program. The new function is stored in the database and is available for any user with sufficient privileges to run. 

&nbsp;

Stored procedures are commonly used to encapsulate logic for data transformation, data validation, and business-specific logic. By combining multiple SQL steps into a stored procedure, you can reduce round trips between your applications and the database.

&nbsp;

Both User-Defined Functions and Stored Procedures can be defined within Hackolade and forward-engineered to Redshift.

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the DDL script to create schemas, tables, columns and their data types, for the structure created with the application.

&nbsp;

![Image](<lib/Redshift%20DDL%20forward-engineering.png>)

&nbsp;

A button lets the user apply to a selected instance the script to create schemas, tables and views.

&nbsp;

If you store JSON within SUPER columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

&nbsp;

## Reverse-Engineering

The connection is established using a connection using AWS IAM credentials:

![Image](<lib/Glue%20connection%20settings.png>)

&nbsp;

or through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\"") of the AWSCLI.

&nbsp;

The Hackolade process for reverse-engineering of Amazon Redshift databases includes the execution of DDL DESCRIBE statements to discover schemas, tables, columns and their data types.&nbsp; If JSON is detected in SUPER columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

For more information on Amazon Redshift in general, please consult the [website](<https://aws.amazon.com/redshift/> "target=\"\_blank\"").

