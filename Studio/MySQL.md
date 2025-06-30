# MySQL

MySQL is one of the most widely used relational database management system (RDBMS) on the market.&nbsp; MySQL is free and open-source software under the terms of the GNU General Public License, and is also commercially supported.&nbsp;

&nbsp;

MySQL supports native JSON data types and functions to combine NoSQL and relational concepts in the same database since version 5.7.8. The native JSON data types allows you to store JSON documents more efficiently than the JSON text format in the previous versions. MySQL stores JSON documents in an internal format that allows quick read access to document elements. The JSON binary format is structured in the way that permits the server to search for values within the JSON document directly by key or array index, which is very fast.

&nbsp;

To perform data modeling for MySQL with Hackolade, you must first download the MySQL [plugin.](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"")

&nbsp;

Hackolade was specially adapted to support the data modeling of MySQL, including databases, tables and views, indexes and constraints, plus the generation of DDL Create Table syntax.&nbsp;

&nbsp;

In particular, Hackolade has the unique ability to model complex semi-structured objects stored in columns of the LONGTEXT data type.&nbsp; We're not talking about functions that "flatten" JSON into standard columns, which runs the risk of inconsistencies, if not errors, when doing the Cartesian product of multiple complex data types.&nbsp; But about the storage of entire JSON documents.&nbsp; The reverse-engineering function, if it detects JSON documents, will sample records and infer the schema to supplement the DDL table definitions. &nbsp;

&nbsp;

The data model in the picture below results from the data modeling of the [Sakila sample database](<https://github.com/kousen/sakila/blob/master/sakila-schema.sql> "target=\"\_blank\""):

&nbsp;

![MySQL workspace](<lib/MariaDB workspace.png>)

&nbsp;

## Databases

MySQL tables are contained within database object containers.&nbsp; The database also works as a security boundary, where you can limit database user permissions to be on a specific schema level only. &nbsp;

&nbsp;

## Database engines

Storage engines, like [InnoDB](<https://dev.mysql.com/doc/refman/8.0/en/innodb-introduction.html> "target=\"\_blank\""), handle data at the physical level. Storage engines are designed to efficiently manage data files, the data, and the index caches.

&nbsp;

## Tables

All data in MySQL is stored in database tables, logically structured as collections of columns and rows, optionally with single-column or multi-column constraints. &nbsp;

&nbsp;

## Unique, Primary, and Foreign Keys, plus Not Null, Check and Default constraints

Constraints in MySQL are predefined rules and restrictions that are enforced in a single column or multiple columns, regarding the values allowed in the columns, to maintain the integrity, accuracy, and reliability of that column’s data. Constraints in MySQL can be defined at the column level, where it is specified as part of the column definition and will be applied to that column only, or declared independently at the table level. 

&nbsp;

There are six main constraints that are commonly used in MySQL: NOT NULL, UNIQUE, PRIMARY, FOREIGN, CHECK, and DEFAULT. &nbsp;

## Indexes

The goal of an index on a database table then is to reduce I/O.&nbsp; Properly indexing a MySQL table is key to providing consistent, optimal performance. There are many things to consider when designing an index structure, but this goes beyond the scope of this document. &nbsp;

&nbsp;

Hackolade supports the most common types of MySQL indexes, but not all of them yet. &nbsp;

&nbsp;

## Data types

In MySQL, each column, local variable, expression, and parameter has a related [data type](<https://MySQL.com/kb/en/data-types/> "target=\"\_blank\""). A data type is an attribute that specifies the type of data that the object can hold: integer data, character data, monetary data, date and time data, binary strings, and so on.

&nbsp;

Additionally, in LONGTEXT columns, Hackolade supports the data modeling of JSON documents with standard JSON data types: string, number, object, array, boolean, and null.

&nbsp;

User-defined data types are based on the data types in MySQL. User-defined data types can be used when several tables store the same domain of values in a column and must ensure that these columns have exactly the same data type, length, and NULLability.

&nbsp;

## Views

A view is a virtual table whose contents are defined by a query. Like a table, a view consists of a set of named columns and rows of data. Unless indexed, a view does not exist as a stored set of data values in a database. The rows and columns of data come from tables referenced in the query defining the view and are produced dynamically when the view is referenced.&nbsp; A view acts as a filter on the underlying tables referenced in the view. The query that defines the view can be from one or more tables or from other views in the current or other databases.

&nbsp;

## Functions and Procedures

A function takes any number of arguments and returns a value from the function body. The function body can be any valid SQL expression as you would use, for example, in any select expression.A Stored Procedure is a routine invoked with a [CALL](<https://MySQL.com/kb/en/call/> "target=\"\_blank\"") statement. It may have input parameters, output parameters and parameters that are both input parameters and output parameters.

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the DDL script to create databases, tables, columns and their data types, indexes and constraints for the structure created with the application, as well as functions and procedures.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![MySQL DDL Forward-Engineering](<lib/MariaDB DDL Forward-Engineering.png>)

&nbsp;

If you store JSON within LONGTEXT columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

&nbsp;

## Reverse-Engineering

The MySQL engine can be hosted on-premises, or on virtualized machines in a private or public cloud Details on how to connect Hackolade to MySQL can be found on [this page](<ConnecttoaMySQLinstance.md>).

&nbsp;

The Hackolade process for reverse-engineering of MySQL databases includes the execution of statements to discover databases, tables, columns and their types, indexes and constraints.&nbsp; If JSON is detected in LONGTEXT columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

For more information on MySQL in general, please consult the [website](<https://mariadb.org/> "target=\"\_blank\"") and [documentation](<https://mariadb.org/documentation/> "target=\"\_blank\""). &nbsp;

