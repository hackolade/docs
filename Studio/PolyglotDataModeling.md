# Polyglot Data Modeling

Hackolade was originally created to perform schema design, i.e. physical data models only.&nbsp; But as support for more and more targets grew, customers started asking, first to be able to save a model for one target into a model for another target.&nbsp; Then they also started to ask that Hackolade could ensure the consistency of schemas across different technologies in data pipelines.

&nbsp;

With RDBMS vendors, the differences between the physical implementations are fairly minor, and so are the differences between the SQL dialects.&nbsp; Not so with all the targets supported by Hackolade for data-at-rest and data-in-motion.&nbsp; The feature set, the storage model, the terminology, the data types, the indexing capabilities, the schema syntax, etc.: there is very little in common between a MongoDB and a Cassandra data model, or between a Parquet and a DynamoDB data model for example.

&nbsp;

Nevertheless, we had to find a solution.&nbsp; Hackolade having been built on top of JSON Schema, it seemed natural to use it as a bridge to convert from one physical target to another.&nbsp; But there a couple of major limitations with JSON Schema:&nbsp;

* the data types are very limited and don't provide the granularity found in many targets,&nbsp;
* only a single entity can be represented in a schema file
* there is no way to represent Foreign Key relationships

&nbsp;

Other schema standards presented similar issues (Avro or XSD) or other equally challenging issues (DDLs in SQL don't include nested objects or are able to represent polymorphism, Snowflake, Hive, ...). &nbsp;

&nbsp;

## A common physical schema from which target schemas are derived

In traditional data modeling approaches for relational databases using the conceptual, logical, and physical types, the purpose for a logical model has been defined as a database-agnostic view of structures and business rules. &nbsp;

&nbsp;

In our definition, a Polyglot Data Model sits over the previous boundary between logical and physical. It is sort of a logical model in the sense that it is technology-agnostic, but it is really a **common physical schema** with the following features:

* allows denormalization, if desired, given access patterns;
* allows complex data types;
* generates schemas for a variety of technologies, with automatic mapping to the specific data types of the respective target technologies.

&nbsp;

In RDBMS the different dialects of SQL will lead to fairly similar DDLs, whereas schema syntax for Avro, Parquet, OpenAPI, HiveQL, Neo4j Cypher, MongoDB, etc... are vastly different.

The generation of physical names for entities (could be called tables, collections, nodes, vertices, files, etc.. in target technology) and attributes (could be called columns, fields, etc.. in target technology) should be capable of following different transformation rules, as Cassandra for example does not allow UPPERCASE while MongoDB will prefer camelCase, etc.

&nbsp;

## Polyglot Data Modeling

With version 5.2.0 of Hackolade Studio, users can now define structures once in a technology-agnostic polyglot data model, complete with with denormalization and complex data types, then represent these structures in a variety of physical data models respecting the specific aspects of each target technology.

&nbsp;

The polyglot functionality is there to help cope with the challenges of [polyglot persistence](<https://en.wikipedia.org/wiki/Polyglot\_persistence> "target=\"\_blank\"").&nbsp; Polyglot persistence can be applied to different use cases, for example a large operational application:

![Image](<lib/Polyglot%20persistence%20-%20e-commerce.png>)

&nbsp;

or through a data pipeline:

![Image](<lib/Polyglot%20persistence%20-%20data%20pipeline.png>)&nbsp;

&nbsp;

For example, you want to make sure to keep in sync the structures of an operational database in MongoDB, a landing zone with Avro files on S3 object storage, a data lake on Databricks with bronze-silver-gold states, streaming with Kafka and a Confluent Schema Registry, and a data warehouse in Snowflake.&nbsp; It is hard enough to build this data pipeline, imagine what it takes to support to dynamic evolution of these schemas as new attributes are constantly added during the application lifecycle.&nbsp; That's the ambition of our polyglot data model capability.

&nbsp;

&nbsp;

More information about the philosophy behind our Polyglot Data Model concept can found on [this page](<https://hackolade.com/polyglot-data-modeling.html> "target=\"\_blank\"").

&nbsp;

This [other page](<PolyglotDataModel.md>) details how to use polyglot data models.

