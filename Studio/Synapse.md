# Synapse

&nbsp;

Azure Synapse Analytics is a limitless analytics service that brings together enterprise data warehousing and Big Data analytics. It uses either serverless or provisioned resources with a unified experience to ingest, prepare, manage, and serve data for immediate BI and machine learning needs.

&nbsp;

Azure Synapse and Parallel Data Warehouse are built on the SQL engine with standard ANSI-compliant T-SQL dialect of SQL language used on SQL Server and Azure SQL Database for data analysis.

&nbsp;

JSON functions in Synapse enable users to combine NoSQL and relational concepts in the same database. Users can combine classic relational columns with columns that contain documents formatted as JSON text in the same table, parse and import JSON documents in relational structures, or format relational data to JSON text.

&nbsp;

To perform data modeling for Synapse with Hackolade, you must first download the Synapse [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  While similar to the SQL Server plugin, the Synapse plugin was specially adapted to support the data modeling of Synapse: adapted metadata properties, removed data types removed, adjusted index and constraints, plus adapted the generation of DDL Create Table syntax.&nbsp;

&nbsp;

In particular, Hackolade has the unique ability to model complex semi-structured objects stored in columns of the (N)VARCHAR(MAX) and (N)VARCHAR(4000) data types.&nbsp; We're not talking about functions that "flatten" JSON into standard columns, which runs the risk of inconsistencies, if not errors, when doing the Cartesian product of multiple complex data types.&nbsp; But about the storage of entire JSON documents.&nbsp; The reverse-engineering function, if it detects JSON documents, will sample records and infer the schema to supplement the DDL table definitions. &nbsp;

&nbsp;

The data model in the picture below results from the data modeling of the [AdventureWorks sample database](<https://docs.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver15> "target=\"\_blank\""):

&nbsp;

![Image](<lib/Synapse%20workspace.png>)

&nbsp;

## Schemas

Schemas are a good way to group tables, used in a similar fashion, together. If you're migrating multiple databases from an on-prem solution to SQL pool, it works best to migrate all of the fact, dimension, and integration tables to one schema in SQL pool.&nbsp;

&nbsp;

## Tables

All data in Synapse is stored in database tables, logically structured as collections of columns and rows, optionally with single-column or multi-column constraints.&nbsp; As users may name tables without the qualifier "fact" or "dim" in the table name, they may manually define a role for the table: Fact, Dimension, Outrigger (used to normalize data in dimension tables for snowflake schemas), or Staging.&nbsp; This table role does not get forward-engineered to the DDL Script. &nbsp;

&nbsp;

A fundamental feature of SQL pool is the way it can store and operate on tables across distributions. SQL pool supports three methods for distributing data: [round-robin](<https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-tables-distribute> "target=\"\_blank\"") (default), [hash](<https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-tables-distribute> "target=\"\_blank\"") and [replicated](<https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/design-guidance-for-replicated-tables> "target=\"\_blank\"").&nbsp; While this might not always be true, and therefore can be adjusted by the user, the application will assign a tole during reverse-engineering based on the following logic:

\- hash distribution -\> fact role

\- replicated distribution -\> dimension role

\- round-robin distribution -\> staging role

&nbsp;

## Constraints

PRIMARY KEY is only supported when NONCLUSTERED and NOT ENFORCED are both used. UNIQUE constraint is only supported with NOT ENFORCED is used. Check [SQL pool Table Constraints](<https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-table-constraints>).&nbsp; FOREIGN KEY constraint is not supported in Synapse SQL pool.

&nbsp;

## Unsupported table features

SQL pool supports many, but not all, of the table features offered by other databases. The following list shows some of the table features that aren't supported in SQL pool: [Computed Columns, ](<https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-table-computed-column-definition-transact-sql?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json\&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json\&view=azure-sqldw-latest> "target=\"\_blank\"")[Indexed Views, ](<https://docs.microsoft.com/en-us/sql/relational-databases/views/create-indexed-views?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json\&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json\&view=azure-sqldw-latest> "target=\"\_blank\"")[Sequence, ](<https://docs.microsoft.com/en-us/sql/t-sql/statements/create-sequence-transact-sql?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json\&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json\&view=azure-sqldw-latest> "target=\"\_blank\"")[Sparse Columns, ](<https://docs.microsoft.com/en-us/sql/relational-databases/tables/use-sparse-columns?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json\&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json\&view=azure-sqldw-latest> "target=\"\_blank\"")Surrogate Keys - Implement with [Identity, ](<https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-tables-identity> "target=\"\_blank\"")[Synonyms, ](<https://docs.microsoft.com/en-us/sql/t-sql/statements/create-synonym-transact-sql?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json\&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json\&view=azure-sqldw-latest> "target=\"\_blank\"")[Triggers, ](<https://docs.microsoft.com/en-us/sql/t-sql/statements/create-trigger-transact-sql?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json\&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json\&view=azure-sqldw-latest> "target=\"\_blank\"")[Unique Indexes, ](<https://docs.microsoft.com/en-us/sql/t-sql/statements/create-index-transact-sql?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json\&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json\&view=azure-sqldw-latest> "target=\"\_blank\"")[User-Defined Types.](<https://docs.microsoft.com/en-us/sql/relational-databases/native-client/features/using-user-defined-types?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json\&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json\&view=azure-sqldw-latest> "target=\"\_blank\"")&nbsp; More info is available [here](<https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-tables-overview#unsupported-table-features> "target=\"\_blank\"").

&nbsp;

Constraints in SQL Server are predefined rules and restrictions that are enforced in a single column or multiple columns, regarding the values allowed in the columns, to maintain the integrity, accuracy, and reliability of that column’s data. Constraints in SQL Server can be defined at the column level, where it is specified as part of the column definition and will be applied to that column only, or declared independently at the table level. 

&nbsp;

There are six main constraints that are commonly used in SQL Server: NOT NULL, UNIQUE, PRIMARY, FOREIGN, CHECK, and DEFAULT. &nbsp;

&nbsp;

## Data types

In Synapse, each column, local variable, expression, and parameter has a related [data type](<https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-tables-data-types> "target=\"\_blank\""). A data type is an attribute that specifies the type of data that the object can hold: integer data, character data, monetary data, date and time data, binary strings, and so on.

&nbsp;

Additionally, in (N)VARCHAR(MAX) and (N)VARCHAR(4000) columns, Hackolade supports the data modeling of JSON files with standard JSON data types: string, number, object, array, boolean, and null.

&nbsp;

Unsupported data types are 'geography','geometry','hierarchyid','image','text','ntext','sql\_variant','xml' and useful alternatives are suggested [here](<https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-tables-data-types#unsupported-data-types> "target=\"\_blank\"").

## Views

Synapse supports standard and materialized views. Both are virtual tables created with SELECT expressions and presented to queries as logical tables. Views encapsulate the complexity of common data computation and add an abstraction layer to computation changes so there's no need to rewrite queries.

&nbsp;

A standard view computes its data each time when the view is used. There's no data stored on disk. People typically use standard views as a tool that helps organize the logical objects and queries in a database. To use a standard view, a query needs to make direct reference to it.

&nbsp;

A materialized view pre-computes, stores, and maintains its data in SQL pool just like a table. There's no recomputation needed each time when a materialized view is used. That's why queries that use all or subset of the data in materialized views can get faster performance. Even better, queries can use a materialized view without making direct reference to it, so there's no need to change application code.

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the DDL script to create schemas, tables, columns and their data types, indexes and constraints for the structure created with the application.

&nbsp;

![Image](<lib/Synapse%20DDL%20forward-engineering.png>)

&nbsp;

If you store JSON within (N)VARCHAR(MAX) or (N)VARCHAR(4000) columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

&nbsp;

## Reverse-Engineering

Details on how to connect Hackolade to a Synapse instance can be found on [this page](<ConnecttoSynapse.md>).

&nbsp;

The Hackolade process for reverse-engineering of Synapse instances includes the execution of statements to discover schemas, tables, columns and their types, indexes and constraints.&nbsp; If JSON is detected in (N)VARCHAR columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

For more information on Synapse in general, please consult the [website](<https://azure.microsoft.com/en-us/services/synapse-analytics/> "target=\"\_blank\"") and [documentation](<https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/> "target=\"\_blank\""). &nbsp;

&nbsp;

During reverse-engineering, a "best guess" attempt is made to determine the table role (Fact vs Dimension vs Staging) using recommendations found [https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/develop-tables-overview#common-distribution-methods-for-tables](<https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/develop-tables-overview#common-distribution-methods-for-tables> "target=\"\_blank\""), but admittedly, thes recommendations are ambiguous and it is likely that the user will need to adjust the role after reverse-engineering.

&nbsp;

