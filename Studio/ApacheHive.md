# Hive

Apache Hive is an open source data warehouse system built on top of Hadoop for querying and analyzing large datasets stored in Hadoop files.&nbsp; Hive uses a language called HiveQL (HQL), which is similar to SQL.&nbsp; HiveQL automatically translates SQL-like queries into MapReduce jobs.&nbsp; Apache Hive organizes data into tables. This provides a means for attaching the structure to data stored in HDFS.

&nbsp;

To perform data modeling for Apache Hive with Hackolade, you must first download the Hive [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  

&nbsp;

Hackolade was specially adapted to support the data modeling of Hive, including Managed and External tables and their metadata, partitioning, primitive and complex datatypes, and the full HQL Create Table syntax. The application closely follows the Hive terminology and storage structure.

&nbsp;

The data model in the picture below results from the modeling of an application described in Cloudera's [tutorial](<https://www.cloudera.com/content/dam/www/marketing/documents/partners/ungated/cloudera-msazure-hadoop-deployment-guide.pdf> "target=\"\_blank\"").

&nbsp;

![Hive workspace](<lib/Hive%20workspace.png>)

&nbsp;

&nbsp;

## Tables

The table in Hive is logically made up of the data being stored. And the associated metadata describes the layout of the data in the table. In Hadoop data typically resides in HDFS, although it may reside in any Hadoop filesystem, including the local filesystem or S3. But Hive stores the metadata in a relational database and not in HDFS.

&nbsp;

![Hive table properties](<lib/Hive%20table%20properties.png>)

&nbsp;

&nbsp;

## Partition keys, buckets

Hive organizes tables into partitions for grouping same type of data together based on a column or partition key. Each table in the Hive can have one or more partition keys to identify a particular partition. Using partition we can also make it faster to do queries on slices of the data.&nbsp; Tables or partitions are subdivided into buckets based on the hash function of a column in the table to give extra structure to the data that may be used for more efficient queries.

&nbsp;

## Data types

Hive supports different data types to be used in table columns. The data types supported by Hive can be broadly classified in Primitive and Complex data types.

&nbsp;

Hackolade was specially adapted to support the data types and attributes behavior of Hive, including arrays, maps and structs.

&nbsp;

![Hive data types](<lib/Hive%20data%20types.png>)

&nbsp;

## Views and Materialized Views

A Hive view is a searchable object in a database, which can be defined by a query.&nbsp; Data cannot be stored in a view, as it is a sort of virtual table.&nbsp; By using joins, it is possible to combine data from one or more tables. It may also hold a subset of information.&nbsp; More info can be found [here](<https://cwiki.apache.org/confluence/display/Hive/LanguageManual%20DDL#LanguageManualDDL-Create/Drop/AlterView> "target=\"\_blank\"").

&nbsp;

With version 3, Hive introduced materialized views to accelerate query processing in data warehouses with pre-computation of relevant summaries and automated server-side denormalization.&nbsp; In theory, this removes the need for client-side handling and would ensure consistency between base and view data.&nbsp; See more info [here](<https://cwiki.apache.org/confluence/display/Hive/Materialized%20views> "target=\"\_blank\"").

&nbsp;

Hackolade supports Hive materialized views, via a SELECT of columns of the underlying base tables.

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the HQL script to create tables, columns and their data types, and indexes for the structure created with the application.

&nbsp;

![Hive forward-engineering](<lib/Hive%20forward-engineering.png>)

&nbsp;

**Note:** foreign keys and primary keys were introduced in Hive version 2.1.0.&nbsp; We assume HIve version 2.1.0 or higher in the generation of the HQL script.

&nbsp;

As many people store JSON within text columns, Hackolade allows for the schema design of those documents.  That JSON structure is not forward-engineered, but is useful for developers, analysts and designers.

## Reverse-Engineering

The connection is established using a connection string including (IP) address and port (typically 10000), and authentication using username/password if applicable.

&nbsp;

The Hackolade process for reverse-engineering of Hive databases includes the execution of HQL DESCRIBE statements to discover tables, columns and their types, and indexes.  If JSON is detected in text columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

For more information on Apache HIve in general, please consult the Apache Hive [website](<https://hive.apache.org/> "target=\"\_blank\"").

