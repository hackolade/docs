# Snowflake

Snowflake is an analytics data warehouse provided as Software-as-a-Service (SaaS.)&nbsp; Snowflake’s architecture is a hybrid of traditional shared-disk database architectures and shared-nothing database architectures. It supports the most common standardized version of SQL: ANSI, including DDL statements to manage database objects such as schemas, tables, columns and indexes.&nbsp; The VARIANT data type lets users store semi-structured file formats including JSON, Avro, ORC and Parquet.

&nbsp;

To perform data modeling for Snowflake with Hackolade, you must first download the Snowflake [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  

&nbsp;

Hackolade was specially adapted to support the data modeling of Snowflake, including schemas, tables and views, plus the generation of DDL Create Table syntax. In particular, Hackolade has the unique ability to model complex semi-structured objects stored in columns of the VARIANT data type.&nbsp; The reverse-engineering function, if it detects JSON documents, will sample records and infer the schema to supplement the DDL table definitions.&nbsp; The application closely follows the Snowflake terminology and storage structure.

&nbsp;

The data model in the picture below results from the data modeling of the [sample weather data](<https://docs.snowflake.com/en/user-guide/sample-data-openweathermap.html> "target=\"\_blank\"") available in some regions of the trial sandbox:

![Image](<lib/Snowflake%20workspace.png>)

&nbsp;

&nbsp;

## Schemas ##

A schema is a logical grouping of database objects (tables, views, etc.). Each schema belongs to a single database.&nbsp; Together, a database and schema comprise a namespace in Snowflake. When performing any operations on database objects in Snowflake, the namespace is inferred from the current database and schema in use for the session.

&nbsp;

## Tables ##

All data in Snowflake is stored in database tables, logically structured as collections of columns and rows, optionally with single-column or multi-column constraints.&nbsp; Snowflake does not use indexes, which is one of the things that makes it scale for arbitrary queries. Instead, Snowflake calculates statistics about columns and records in files that you load, and uses those statistics to figure out what parts of what tables/records to actually load to execute a query.

&nbsp;

## Unique, Primary, and Foreign Keys, and Not Null ##

Snowflake supports the following constraint types from the ANSI SQL standard: UNIQUE, PRIMARY, FOREIGN, and NOT NULL. &nbsp;

&nbsp;

**Note:** Snowflake supports defining and maintaining constraints, but does not enforce them, except for NOT NULL constraints, which are always enforced.

&nbsp;

## Clustering Keys ##

In general, Snowflake produces well-clustered data in tables; however, over time, the data in some table rows may no longer cluster optimally on desired dimensions.&nbsp; To improve the clustering of the underlying table micro-partitions, you can always manually sort rows on key table columns and re-insert them into the table; however, performing these tasks could be cumbersome and expensive.&nbsp; Instead, Snowflake supports automating these tasks by designating one or more table columns/expressions as a *clustering key* for the table. A table with a clustering key defined is considered to be *clustered*.

&nbsp;

## Data types ##

Snowflake supports the most basic [SQL data types](<https://docs.snowflake.com/en/sql-reference/intro-summary-data-types.html> "target=\"\_blank\"") (with some restrictions) for use in columns. Data types are automatically coerced whenever necessary and possible. Snowflake VARCHAR holds unicode characters.

&nbsp;

In addition to the standard ANSI SQL data types, Snowflake also supports the semi-structured data types: VARIANT, OBJECT and ARRAY to represent arbitrary data structures which can be used to import and operate on semi-structured data (JSON, Avro, ORC, Parquet, or XML.) Snowflake stores these types internally in an efficient compressed columnar binary representation of the documents for better performance and efficiency.

&nbsp;

Currently, Hackolade lets you model JSON structures and data types in VARIANT, plus during reverse-engineering, will detect JSON and infer the schema.&nbsp; Similar support for Avro, ORC and Parquet is foreseen, but not yet available.

&nbsp;

Hackolade also supports Snowflake User-Defined Types via its [re-usable object definitions](<Reusableobjectsdefinitions.md>).

&nbsp;

## (Materialized) Views ##

A view allows the result of a query to be accessed as if it were a table. The query is specified in the CREATE VIEW statement.&nbsp; Views serve a variety of purposes, including combining, segregating, and protecting data.

&nbsp;

Hackolade supports Snowflake (materialized) views, via a SELECT of columns of the underlying base table, to present the data of the base table with a different primary key for different access patterns. &nbsp;

&nbsp;

## Forward-Engineering ##

Hackolade dynamically generates the DDL script to create schemas, tables, columns and their data types, for the structure created with the application.

&nbsp;

![Image](<lib/Snowflake%20DDL%20forward-engineering.png>)

&nbsp;

If you store JSON within VARIANT columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

&nbsp;

## Reverse-Engineering ##

A Snowflake account can be hosted on any of the following cloud platforms: Amazon Web Services, Google Cloud Platform, or Microsoft Azure.&nbsp; Each platform provides one or more [regions](<https://docs.snowflake.com/en/user-guide/intro-regions.html>) where the account is provisioned.&nbsp; Details on how to connect Hackolade to Snowflake can be found on [this page](<ConnecttoaSnowflakeinstance.md>).

&nbsp;

The Hackolade process for reverse-engineering of Snowflake databases includes the execution of DDL DESCRIBE statements to discover schemas, tables, columns and their data types.&nbsp; If JSON is detected in VARIANT columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

For more information on Snowflake in general, please consult the [website](<https://www.snowflake.com/> "target=\"\_blank\"").&nbsp; See also this excellent [hands-on lab guide](<https://s3.amazonaws.com/snowflake-workshop-lab/Snowflake\_free\_trial\_LabGuide.pdf> "target=\"\_blank\"").


***
_Created with the Personal Edition of HelpNDoc: [Qt Help documentation made easy](<https://www.helpndoc.com/feature-tour/create-help-files-for-the-qt-help-framework>)_
