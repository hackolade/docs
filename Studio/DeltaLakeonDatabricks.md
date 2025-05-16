# Delta Lake on Databricks

Delta Lake is an open-source storage layer that brings reliability to data lakes. It was initially developed by [Databricks](<https://databricks.com/> "target=\"\_blank\"") in 2016 and open-sourced to the Linux Foundation in 2019.&nbsp; Delta Lake provides ACID transactions, scalable metadata handling, and unifies streaming and batch data processing. It is a storage layer on top of cloud object stores (Amazon S3, Azure Data Lake Storage, Google Cloud Storage and etc) or distributed filesystems like [HDFS](<https://en.wikipedia.org/wiki/Apache\_Hadoop>), which describes and defines the formats of data object and transaction logs, and a set of access protocols enabling DBMS-like features.&nbsp; It is fully compatible with Apache Spark APIs.&nbsp; Its schema enforcement automatically handles schema variations to prevent insertion of bad records during ingestion.&nbsp; The Databricks Lakehouse platform provides data engineering, SQL analytics, data science and Machine Learning on Azure Databricks, Databricks on AWS and google Cloud.

&nbsp;

Apache Spark SQL in Databricks is designed to be compatible with&nbsp; Apache Hive, including metastore connectivity, SerDes, and UDFs.&nbsp; So every Databricks deployment has a central Hive metastore accessible by all clusters to persist table metadata, and Hackolade has been supporting Hive for several years. &nbsp;

&nbsp;

To perform data modeling for Delta Lake on Databricks with Hackolade, you must first download the DeltaLake [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  

&nbsp;

Hackolade was specially adapted to support the data modeling of Delta Lake, including the Databricks storage structure of clusters, databases, tables, views, and indexes.&nbsp; It leverages Hive primitive and complex data types, plus user-defined types.&nbsp; And combines it all with the usual capabilities of forward-engineering of HiveQL scripts, reverse-engineering, documentation generation, model comparison, command-line interface integration with CI/CD pipelines, etc...The application closely follows the Delta Lake terminology.

&nbsp;

The data model in the picture below results from the modeling of an application described in this [tutorial](<https://www.cloudera.com/content/dam/www/marketing/documents/partners/ungated/cloudera-msazure-hadoop-deployment-guide.pdf> "target=\"\_blank\"").

&nbsp;

![Delta Lake on Databricks workspace](<lib/Delta Lake on Databricks workspace.png>)

&nbsp;

&nbsp;

## Clusters

A Databricks ***cluster*** is a set of computation resources and configurations on which you run data engineering, data science, and data analytics workloads, such as production ETL pipelines, streaming analytics, ad-hoc analytics, and machine learning. &nbsp;

&nbsp;

## Databases

A Databricks ***database*** is a collection of tables.

&nbsp;

## Tables

A Databricks ***table*** is a collection of structured data. Tables be can queried with Spark APIs and Spark SQL.&nbsp; The table is logically made up of the data being stored in cloud object stores (Amazon S3, Azure Data Lake Storage, Google Cloud Storage and etc) or distributed filesystems like [HDFS.&nbsp; The table metadata](<https://en.wikipedia.org/wiki/Apache\_Hadoop>) describes the layout of the data in the table and defines the formats of data object and transaction logs, and a set of access protocols enabling DBMS-like features.&nbsp; It is fully compatible with Apache Spark APIs.&nbsp; Its schema enforcement automatically handles schema variations to prevent insertion of bad records during ingestion.

&nbsp;

Every Databricks deployment has a central Hive metastore accessible by all clusters to persist table metadata. Instead of using the Databricks Hive metastore, users have the option to use an [existing external Hive metastore](<https://docs.databricks.com/data/metastores/external-hive-metastore.html> "target=\"\_blank\"") instance or the [AWS Glue Catalog](<https://docs.databricks.com/data/metastores/aws-glue-metastore.html> "target=\"\_blank\"").

&nbsp;

Delta Lake does not enforce multi-table transactions, primary or foreign keys, but they still can be declared . The only constraints supported by Delta Lake are NOT NULL and CHECK.

&nbsp;

![Databricks table properties](<lib/Hive table properties.png>)

&nbsp;

&nbsp;

## Data types

Delta Lake supports different data types to be used in table columns. The Hive data types supported by Delta Lake can be broadly classified in Primitive and Complex data types.

&nbsp;

Hackolade was specially adapted to support the data types and attributes behavior of Delta Lake, including arrays, maps and structs.

&nbsp;

In addition to the Hive data types, Databricks also supports the semi-structured data types: VARIANT, OBJECT and ARRAY to represent arbitrary data structures which can be used to import and operate on semi-structured data (JSON, Avro, ORC, Parquet, or XML.)&nbsp; Variant provides an order of magnitude performance improvements compared with storing these data as JSON strings, while maintaining the flexibility for supporting highly nested and evolving schema.

&nbsp;

&nbsp;

![Hive data types](<lib/Hive data types.png>)

&nbsp;

## Views

A Databricks view is a searchable object in a database, which can be defined by a query.&nbsp; Data cannot be stored in a view, as it is a sort of virtual table.&nbsp; By using joins, it is possible to combine data from one or more tables. It may also hold a subset of information.&nbsp; More info can be found [here](<https://docs.databricks.com/spark/latest/spark-sql/language-manual/sql-ref-syntax-ddl-create-view.html> "target=\"\_blank\"").

&nbsp;

Hackolade supports Delta Lake views, via a SELECT of columns of the underlying base tables.&nbsp; We also support the \[column\_list\] syntax, but note that if columns are present in the SELECT statement, they take precedence over the column\_list.&nbsp; f there is no column list, the view inherits the column names from the underlying query. All columns in a view must be uniquely named.

&nbsp;

## Databricks Unity Catalog

The Unity Catalog is a unified governance solution for data and AI assets on the Databricks Lakehouse.&nbsp; It provides centralized access control, auditing, lineage, and data discovery capabilities across Databricks workspaces.&nbsp; It was introduced with Runtime 11.3

&nbsp;

All data in Unity Catalog is referenced using a [three-level namespace](<https://docs.databricks.com/data-governance/unity-catalog/queries.html#three-level-namespace-notation>): catalog.schema.table.

![Unity Catalog object model diagram](<lib/Unity Catalog object model diagram.png>)

&nbsp;

&nbsp;

&nbsp;

**Catalog:** Catalogs are the highest level in the data hierarchy (catalog \> schema \> table/view/volume) managed by the Unity Catalog metastore. They are intended as the primary unit of data isolation in a typical Databricks data governance model.&nbsp; Catalogs represent a logical grouping of schemas, usually bounded by data access requirements. Catalogs often mirror organizational units or software development lifecycle scopes. You may choose, for example, to have a catalog for production data and a catalog for development data, or a catalog for non-customer data and one for sensitive customer data.

&nbsp;

**Schema (Database):** Schemas, also known as databases, are logical groupings of tabular data (tables and views), non-tabular data (volumes), functions, and machine learning models. They give you a way to organize and control access to data that is more granular than catalogs. Typically they represent a single use case, project, or team sandbox.

&nbsp;

**Tables:** Tables reside in the third layer of Unity Catalog’s three-level namespace. They contains rows of data. Unity Catalog lets you create *managed tables* and *external tables*.

&nbsp;

**Views:** A view is a read-only object derived from one or more tables and views in a metastore.

&nbsp;

**Volumes:** Volumes reside in the third layer of Unity Catalog’s three-level namespace. They manage non-tabular data. You can use volumes to store, organize, and access files in any format, including structured, semi-structured, and unstructured data. Files in volumes cannot be registered as tables.

&nbsp;

For more information on the Unity Catalog, consult the [documentation](<https://docs.databricks.com/data-governance/unity-catalog/index.html> "target=\"\_blank\"").

&nbsp;

### Tags in Unity Catalog

This feature is only available for Runtime 13 and up.

&nbsp;

Tags are attributes containing keys and optional values that can be applied to different objects in Unity Catalog. Tagging is useful for organizing and categorizing objects within a metastore. Using tags also simplifies search and discovery of your data assets.

&nbsp;

In Hackolade Studio, tags are groups of key-value pairs that appear at different levels: catalog, schema, table, and attribute. &nbsp;

![Image](<lib/Databricks Unity Catalog tags.png>)

&nbsp;

They translate into the corresponding DDL statements during forward-engineering:

&nbsp;

> ALTER \<LEVEL\> \<levelObject\_name\>\
SET TAGS ('key1' = 'value1', 'key2' = 'value2')\
\
where SET TAGS ( { tag\_name = tag\_value } \[, …\] )

> &nbsp;

> where tag\_name is a literal STRING. The tag\_name must be unique within the object, and tag\_value is a literal STRING.

&nbsp;

Tags are also picked up during reverse-engineering.

&nbsp;

There are some constraints:

\- to add tags to Unity Catalog securable objects when applying the DDL script to intance, users must have the APPLY TAG privilege on the object, as well as the USE SCHEMA privilege on the object’s parent schema and the USE CATALOG privilege on the object’s parent catalog.

\- you can assign a maximum of 20 tags to a single securable object

\- the maximum length of a tag is 255 characters (use regex validation property)

\- special characters&nbsp; '.', ',', '-', '=', '/', ':', ' ' (blank space) cannot be used in tag names (use regex validation property)

&nbsp;

Note that the tag value is optional, i.e. there can be a tag without value.

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the HiveQL script to create databases, tables, columns and their data types, as well as views for the structure created with the application.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Databricks forward-engineering](<lib/Delta Lake forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically creates the database, tables, views, columns, including constraints and indexes.

&nbsp;

**Note:** As foreign keys and primary keys are not supported in Delta Lake, they can be used in Hackolade for informational purposes, but are not generated in the HQL script.

&nbsp;

As many people store JSON within text columns, Hackolade allows for the schema design of those documents.  That JSON structure is not forward-engineered, but is useful for developers, analysts and designers.&nbsp; It is often integrated into a CI/CD pipeline, using the [Command-Line Interface](<CommandLineInterface.md>).

## Reverse-Engineering

The connection is established using a connection string including the Cloud provider and a personal access token.

&nbsp;

In the premium version of Databricks, it is possible to control [table access](<https://docs.databricks.com/security/access-control/table-acls/index.html#table-access-control> "target=\"\_blank\"").  If that's the case, the user must be granted the following [data object privileges](<https://docs.databricks.com/security/access-control/table-acls/object-privileges.html#data-object-privileges> "target=\"\_blank\""):

1. for reverse-engineering: READ\_METADATA and SELECT  on the tables and views
1. for forward-engineering (apply to instance): rights to CREATE/UPDATE schema, table, and view: CREATE on the CATALOG, and either OWN or both USAGE and CREATE on the schema, tables and views.

&nbsp;

The Hackolade process for reverse-engineering of Delta Lake databases includes the execution of HQL SHOW statements to discover databases, tables, columns and their data types.  If JSON is detected in text columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

For more information on Delta Lake in general, please consult the [website](<https://delta.io/> "target=\"\_blank\"").&nbsp; Here is the links to the [Databricks website](<https://databricks.com/product/data-lakehouse> "target=\"\_blank\"").

