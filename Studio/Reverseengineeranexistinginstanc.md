# Reverse-engineering

Reverse engineering is a useful feature to facilitate the modeling and documentation of existing instances.&nbsp; After the reverse engineering has been performed, the user can enrich the model created, by filling descriptions, recording constraints that were not obvious from the stored data, documenting relationships, etc…

&nbsp;

Hackolade supports the reverse engineer of different types of data sources:

* a JSON document: conversion of a basic JSON document into a Hackolade collection schema
* a JSON Schema: conversion of a JSON Schema file into a Hackolade collection schema
* a Data Definition Language file (DDL): from Oracle, Microsoft SQL Server, MySQL, PostgreSQL, Hadoop Hive, Snowflake, Teradata
* an XSD schema file from another ER tool, such as erwin, ER/Studio, PowerDesigner, or other
* an Excel file template: first export a Hackolade model (even an empty one) to generate an Excel file for the target of your choice.&nbsp; Then you may bulk edit your model or create a new one before ingesting it bak into the application.
* target-specific
  * an Apache Avro data file or schema.Hackolade reads .avro and .avsc files from the file system or cloud storage to convert the Avro schema in a Hackolade model.
  * a Cassandra or DataStax (DSE) instance: Hackolade accesses a Cassandra instance through the REST API, reads the table and column setup, then samples columns with JSON types to probabilistically infer the Hackolade schema from the sampled JSON data.
  * a Cosmos DB instance: Hackolade can reverse-engineer a local instance of Cosmos DB or hosted at Azure, using the SQL API (previously known as DocumentDB API), the MongoDB API, or the Gremlin API.&nbsp; The process performs a sampling of the selected collections and document types, and probabilistically infers the Hackolade schema from the sampled data.
  * a Couchbase instance through a connection, samples the selected bucket(s), and probabilistically infers the Hackolade schema from the sampled data.
  * a DynamoDB instance: Hackolade accesses DynamoDB either local or hosted at AWS.&nbsp; It performs a sampling of the selected tables, and probabilistically infers the Hackolade schema from the sampled data.
  * a MongoDB database: Hackolade accesses a MongoDB instance through a connection, samples the selected collection(s), and derives a Hackolade schema from the sampled data
  * a Mongoose schema: conversion of the JavaScript file containing a Mongoose schema, and transformation into a Hackolade collection schema&nbsp;
  * a Schema Registry of AWS EventBridge, in OpenAPI 3.0.x format
  * an Elasticsearch instance: Hackolade accesses an Elasticsearch instance through the REST API, samples the selected indices and types, and probabilistically infers the Hackolade schema from the sampled data plus the retrieved mappings.
  * an AWS Glue Data Catalog instance: Hackolade access AWS via the CLI to read the catalog databases, tables and columns definitions
  * an HBase instance: Hackolade accesses an HBase instance through the REST API, reads the table and column family setup, then samples column qualifiers with JSON types to probabilistically infer the Hackolade schema from the sampled JSON data.
  * an Apache Hive instance: Hackolade accesses Hive via the Thrift service, reads the table and column setup, then samples columns with JSON types to probabilistically infer the Hackolade schema from the sampled JSON data.
  * a MarkLogic instance: Hackolade access a MarkLogic instance and samples collections (or directories) to infer the schema of sampled documents.
  * a Neo4j graph instance: Hackolade accesses a Neo4j instance through the REST API, and reads the Cypher setup for node labels and relationship types.
  * a Parquet data file: Hackolade reads .parquet files from the file system or cloud storage to convert the Parquet schema in a Hackolade model.
  * a ScyllaDB instance: Hackolade accesses a ScyllaDB instance through the REST API, reads the table and column setup, then samples columns with JSON types to probabilistically infer the Hackolade schema from the sampled JSON data.
  * SQL Server and Azure SQL: Hackolade accesses an on-prem or cloud-based instance to fetch the DDL and derive the schema.&nbsp; If a column with data type varchar(MAX) or varchar(4000) is detected to contain JSON documents, records are sampled and the schema is inferred. &nbsp;
  * Snowflake: Hackolade accesses an instance to fetch the DDL and derive the schema.&nbsp; If a column with data type VARIANT is detected to contain JSON documents, records are sampled and the schema is inferred. &nbsp;
  * Synapse: Hackolade accesses an instance to fetch the DDL and derive the schema.&nbsp; If a column with data type varchar(MAX) or varchar(4000) is detected to contain JSON documents, records are sampled and the schema is inferred. &nbsp;
  * Swagger and OpenAPI documentation files, in either JSON or YAML format
  * a TinkerPop instance: Hackolade accesses a TinkerPop instance through the REST API, and reads the Gremlin setup for node labels and edge types.

&nbsp;

This feature is also available via the [Command-Line Interface](<CommandLineInterface.md>).

## Reverse-engineering process

This process includes a series of steps outlined below.&nbsp; After going through the steps, the user is free to enrich the model for documentation purposes, and to generate forward-engineering scripts.

### Choose the model target

Create a new model and select the target of your choice.&nbsp; The reverse-engineering process is fairly similar for all targets, with local nuances when needed.&nbsp; But the terminology and connection protocols can be very different.

### Choose the reverse-engineering function

This screen will vary depending on the selected target.

![Tools  Reverse-Engineer  MongoDB Collection](<lib/Tools%20%20Reverse-Engineer%20%20MongoDB%20Collection.png>)

&nbsp;

### Establishing a connection

The options here will vary depending on the selected target.&nbsp; Refer to the pages below to find the specific details.&nbsp; The images below refer to MongoDB.

![Reverse-Engineering Connection Settings](<lib/Reverse-Engineering%20Connection%20Settings.png>)

&nbsp;

***TIP:***&nbsp; note, if you have instances with a very large number of databases, you may wish to declare a particular database directly in the connection string by appending the address with: /\<name of the database you wish to access directly\>, for example: localhost/NBA

&nbsp;

![Reverse-Engineering Connection Selection](<lib/Reverse-Engineering%20Connection%20Selection.png>)

&nbsp;

For more information on the various authentication and encryption protocols, please consult these [pages](<ConnecttoaMongoDBinstance.md>).

&nbsp;

### Selecting one or more collections/entities

![Reverse-Engineer MongoDB Collection selection](<lib/Reverse-Engineer%20MongoDB%20Collection%20selection.png>)

&nbsp;

### Sampling of one or more collections/entities

Sampling is currently limited for performance reasons to at most 10.000 documents, adjustable via a user parameter in Tools \> Options \> Reverse-Engineering, or up to 100k documents with the [Command-Line Interface](<CommandLineInterface.md>).&nbsp;

&nbsp;

Since MongoDB 3.2, collections are sampled with the [$sample](<https://docs.mongodb.com/manual/reference/operator/aggregation/sample/#pipe.\_S\_sample> "target=\"\_blank\"") operator via the [/core/aggregation-pipeline](<http://docs.mongodb.org/manual/core/aggregation-pipeline?\_ga=1.108259590.544578421.1459505203> "target=\"\_blank\""). This provides efficient random sampling without replacement over the entire collection, or over the subset of documents specified by a query.

&nbsp;

In MongoDB 3.0 and 2.6, collections are sampled via a backwards-compatible algorithm. It takes place in three stages:

\- Hackolade opens a cursor on the desired collection, sorted in descending order of the \_id field.

\- sampleSize documents are randomly selected from the stream, using [reservoir sampling](<http://en.wikipedia.org/wiki/Reservoir\_sampling> "target=\"\_blank\"").

\- Hackolade performs a query to select the chosen documents directly via \_id.

&nbsp;

Note that this sampling mechanism is originally provided in Open Source by [MongoDB](<https://github.com/mongodb-js/collection-sample> "target=\"\_blank\""), and adapted to the specific needs of Hackolade.

&nbsp;

### Probabilistic inference of schema

From the sample set gathered above, measurable metrics can be applied to the schema, including schema depth and width, and class interactions, as described here:

![RevEng schema inference](<lib/RevEng%20schema%20inference.png>)

&nbsp;

Note that this inference mechanism is originally provided in Open Source by [MongoDB](<https://github.com/mongodb-js/mongodb-schema> "target=\"\_blank\""), and adapted to the specific needs of Hackolade.

&nbsp;

In this step, when the instance being reverse-engineered is v3.2 and above, stored validator setup is leveraged as well, using the [db.getCollectionInfos()](<https://docs.mongodb.com/manual/reference/method/db.getCollectionInfos/> "target=\"\_blank\"") method&nbsp;

&nbsp;

#### Pattern field detection

As of v2.5.0 of Hackolade, we've also introduced the ability to detect **pattern fields** during the reverse-engineering process.&nbsp; For any sub-object at a given level, we can infer the presence of a pattern field if we detect the recurrence of similar regex patterns in field names.

![Reverse-Engineering pattern field detection](<lib/Reverse-Engineering%20pattern%20field%20detection.png>)&nbsp;

&nbsp;

This pattern field recognition was further enhanced in v4.2.3 with the following logic:

a) attribute must be a complex data type (object or array)

b) in a list of successive complex attributes in a branch of the schema hierarchy, the structure of each of these complex attributes must be exactly identical&nbsp;

c) the names of these successive complex attributes with identical structure must be similar as per either:

\- an ID-like structure of the same length of at least 12 characters that can only include hexadecimal numbers and dashes;

\- or by by using [Levenshtein distance](<https://en.wikipedia.org/wiki/Levenshtein\_distance> "target=\"\_blank\""). The distance parameter may be modified in Tools \> Options \> Reverse-Engineering (default = 1)&nbsp; An online Levenshtein distance calculator can be found [here](<https://planetcalc.com/1721/> "target=\"\_blank\"").

&nbsp;

#### Inference of Foreign Key relationships

With v4.2.13, the option was introduced to attempt foreign key relationship inference.&nbsp; This features is only available for the MongoDB target, and is for documentation purposes only, as Foreign Key relationships are not enforced by the database.&nbsp; For each field in a collection with the data type ObjectID, the application finds if the sampled value can be linked to a document in the same collection (for a recursive FK) or another collection in the database.&nbsp; The cardinality is set by default to "0...n" on the child side, but can be adjusted manually by the user.

&nbsp;

### Transformation into a Hackolade collection schema

In this final step, the derived schema needs to be converted and persisted into the Hackolade notation, so it can be visualized, adapted and enriched in the application.

&nbsp;

### Conflict resolution during merge into an existing model

When reverse-engineering into an existing model, it is possible that source objects already match existing objects in the model.&nbsp; This could be container names and/or entity names.&nbsp; When the process detects such case, the user is asked to decide on the logic to be used during processing:

&nbsp;

![Conflict resolution dialog](<lib/Conflict%20resolution%20dialog.png>)

&nbsp;

Keep both: leaves the objects in the mode untouched, and adds new objects in the model

Replace: overwrites the existing objects with the new ones

Merge: combines the new objects with the existing objects in the model.&nbsp; New detected attributes will be added.&nbsp; Existing properties of attributes are maintained.

Cancel: abort process

&nbsp;

By checking the option "Apply to all conflicts", the user tells the process to apply the same choice to all subsequently detected conflicts, so the question is not asked again.

&nbsp;

The feature is also available as an argument in revEng Command-Line Interface commands, but can only "apply to all conflicts".

