# Teradata

Teradata Vantage is a suite of big data analytics solutions based on a core relational database. It allows deep analysis and manipulation of semi-structured data format and can be deployed on multiple cloud providers, public or private but also on premises. It offers capabilities to leverage analytics engines such as Apache Spark and Tensorflow.

&nbsp;

To perform data modeling for Teradata with Hackolade, you must first download the Teradata [plugin](<DownloadadditionalDBtargetplugin.md>).  

&nbsp;

Hackolade was specially adapted to support the data modeling of Teradata databases, including tables and views, indexes and constraints, plus the generation of DDL Create Table syntax.

&nbsp;

In particular, Hackolade has the unique ability to model complex semi-structured objects stored in columns of the JSON data types. We're not talking about functions that "flatten" JSON into standard columns, which runs the risk of inconsistencies, if not errors, when doing the Cartesian product of multiple complex data types. But about the storage of entire JSON documents.  The reverse-engineering function, if it detects JSON documents, will sample records and infer the schema to supplement the DDL table definitions.  

&nbsp;

The data model in the picture below results from the data modeling of the [Czech Bank financial dataset demo](<https://github.com/dnoeth/1999\_Czech\_financial\_dataset\_Teradata> "target=\"\_blank\""):

&nbsp;

![Image](<lib/PostgreSQL%20workspace.png>)

&nbsp;

## Databases

Unlike some other SQL engines there is no concept of SCHEMA. In Teradata a SCHEMA is called a DATABASE.

&nbsp;

A database is a namespace that contains named objects such as tables, views, indexes, data types, functions, stored procedures and operators. Databases allow you to organize objects e.g., tables into logical groups to make them more manageable.

&nbsp;

A single Hackolade model deals with can handle multiple Teradata databases.

&nbsp;

## Tables

A table consists of rows and columns. The number and order of the columns is fixed, and each column has a name. Each column has a data type. The data type constrains the set of possible values that can be assigned to a column and assigns semantics to the data stored in the column so that it can be used for computations.

&nbsp;

## Unique, Primary, and Foreign Keys, plus Not Null, Check and Default constraints

Constraints in Teradata are predefined rules and restrictions that are enforced in a single column, multiple columns or at table level, regarding the values allowed in the columns, to maintain the integrity, accuracy, and reliability of that column’s data. Constraints in Teradata can be defined at the column level or table, where it is specified as part of the column definition and will be applied to that column only, or declared independently at the table level. 

&nbsp;

There are six main constraints that are commonly used in Teradata: NOT NULL, UNIQUE, PRIMARY, FOREIGN, CHECK, and DEFAULT.

## Partitioning

Teradata supports table partitioning. Partitioning refers to splitting what is logically one large table into smaller physical pieces. Partitioning can provide several benefits on the performance side. Large tables and join indexes are usually better candidates for row partitioning than smaller tables and join indexes because there is not much benefit to partitioning a table or join index small enough that a full‑table scan on the nonpartitioned table or join index takes only a few seconds.

## Indexes

The goal of an index on a database table then is to reduce I/O. Properly indexing a Teradata table is key to providing consistent, optimal performance. There are many things to consider when designing an index structure, but this goes beyond the scope of this document.&nbsp; Teradata has mainly four index levels and types, primary, secondary, hash and join indexes.

&nbsp;

Hackolade supports the most common types of Teradata indexes.

## Data types

Teradata has a rich set of [data types](<https://docs.teradata.com/r/Enterprise\_IntelliFlex\_VMware/Teradata-VantageTM-SQL-Fundamentals-17.20> "target=\"\_blank\"") available to users. A data type is an attribute that specifies the type of data that the object can hold: integer data, character data, monetary data, date and time data, binary strings, and so on.

&nbsp;

Additionally, in JSON columns, Hackolade supports the data modeling of JSON documents with standard JSON data types: string, number, object, array, boolean, and null.

&nbsp;

Structured/User-defined data types are based on the data types in Teradata. Structured / User-defined data types can be used when several tables store the same domain of values in a column and must ensure that these columns have exactly the same data type, length, and NULLability.

* JSON: The JSON data type represents data that is in JSON (JavaScript Object Notation) format.
* UDT: (User-Defined Type) data types are custom data types that you define to model the structure and behavior of the data used by your applications.
* XML: The XML data type represents XML content. The data is stored in a compact binary form that preserves the information set of the XML document, including the hierarchy information and type information derived from XML validation.

## Views

A view is a virtual table whose contents are defined by a query. Like a table, a view consists of a set of named columns and rows of data. Unless indexed, a view does not exist as a stored set of data values in a database. The rows and columns of data come from tables referenced in the query defining the view and are produced dynamically when the view is referenced. A view acts as a filter on the underlying tables referenced in the view. The query that defines the view can be from one or more tables or from other views in the current or other databases.

&nbsp;

## User-Defined methods

Hackolade supports user defined methods which are created in CREATE TYPE statements.

&nbsp;

## Functions and Procedures

Hackolade doesn't support yet user defined functions, macros, stored procedures nor triggers.

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the DDL script to create tables, columns and their data types, indexes and constraints for the structure created with the application, as well as functions and procedures.

&nbsp;

![Teradata forward-engineering](<lib/Teradata%20forward-engineering.png>)

&nbsp;

If you store documents in JSON columns, Hackolade allows for the schema design of those documents. However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

&nbsp;

To apply to instance, you need USAGE privileges, and if that's not possible, then at least INSERT, UPDATE, DELETE, TRUNCATE, REFERENCES, TRIGGER, CREATE, CONNECT.

## Reverse-Engineering

The Teradata instance can be hosted on-premises, or on virtualized machines in a private or public cloud. Details on how to connect Hackolade to Teradata can be found on [this page](<ConnecttoaTeradatainstance.md>).

&nbsp;

The Hackolade process for reverse-engineering of Teradata instances includes the execution of statements to discover databases, tables, columns and their types, indexes and constraints. For JSON columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

**Important:** when forward- or reverse-engineering a Teradata instance, the (Teradata) user used to connect to the target instance should have access to read **SYSUDTLIB** system database to retrieve DDL scripts for UDT, UDM etc...

&nbsp;

More information is available [here](<https://docs.teradata.com/r/Enterprise\_IntelliFlex\_VMware/Teradata-VantageTM-SQL-Data-Definition-Language-Syntax-and-Examples-17.20/Table-Statements/CREATE-TABLE-and-CREATE-TABLE-AS> "target=\"\_blank\"").

&nbsp;

For more information on Teradata in general, please consult the [website](<https://www.teradata.com//> "target=\"\_blank\"") and [documentation](<https://docs.teradata.com/r/Teradata-VantageTM-SQL-Data-Definition-Language-Syntax-and-Examples/July-2021/Introduction-to-SQL-Data-Definition-Language-Syntax-and-Examples> "target=\"\_blank\"").
