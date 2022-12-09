# Polyglot Data Modeling

Hackolade was originally created to perform schema design, i.e. physical data models only.&nbsp; But as support for more and more targets grew, customers started asking to be able to save a model for one target into a model for another target.&nbsp; Then they also started to ask that Hackolade could ensure the consistency of schemas across different technologies in data pipelines.

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

In traditional data modeling approaches for relational databases using the conceptual, logical, and physical types of models, the purpose for a logical model has been defined as a database-agnostic view of normalized structures and business rules. &nbsp;

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

Starting with version 5.2.0 of Hackolade Studio, users can now define structures once in a technology-agnostic polyglot data model, complete with denormalization and complex data types, then represent these structures in a variety of physical data models respecting the specific aspects of each target technology.

&nbsp;

The polyglot functionality is there to help cope with the challenges of [polyglot persistence](<https://en.wikipedia.org/wiki/Polyglot\_persistence> "target=\"\_blank\"").&nbsp; Polyglot persistence can be applied to different use cases, for example a large operational application:

![Polyglot persistence - e-commerce](<lib/Polyglot%20persistence%20-%20e-commerce.png>)

&nbsp;

or through a data pipeline:

![Polyglot persistence - data pipeline](<lib/Polyglot%20persistence%20-%20data%20pipeline.png>)&nbsp;

&nbsp;

For example, you want to make sure to keep in sync the structures of an operational database in MongoDB, a landing zone with Avro files on S3 object storage, a data lake on Databricks with bronze-silver-gold states, streaming with Kafka and a Confluent Schema Registry, and a data warehouse in Snowflake.&nbsp; It is hard enough to build this data pipeline, imagine what it takes to support to dynamic evolution of these schemas as new attributes are constantly added during the application lifecycle. &nbsp;

&nbsp;

If you add/delete/modify entities or attributes in the polyglot model from which several target models are derived, all these changes can trickle down in the target models.

&nbsp;

## Flexibilty

In a basic use case, you could have just one polyglot model, and several target models derived entirely from the common polyglot models.&nbsp; Each target model would just reflect the physical implementation for its respective technology.&nbsp; Entities can be deleted from the target model, others can be added, and the model can be enriched with entity options, indexes, etc. to generate the proper artifacts (script, DDL, ...)&nbsp; You may also deactivate attributes in the target model if they're not necessary, or you may modify some their properties.

&nbsp;

But overall, the above use case is a bit theoretical, and reality will quickly dictate more flexible approaches. In a slightly more realistic use case, you could have target models that are each a different subset of a same polyglot model.&nbsp; Each target model may be supplemented by its own additional entities.

&nbsp;

Elaborating further, you could derive a target model from multiple polyglot models, or subsets thereof:

![Polyglot multiple subsets](<lib/Polyglot%20multiple%20subsets.png>)

&nbsp;

&nbsp;

&nbsp;

## Conceptual modeling

It is generally said that there are 3 categories of data modeling: conceptual, logical, and physical.&nbsp; In summary, conceptual modeling captures the common business language and defines the scope, whereas the logical model captures the business rules, and the physical model represents the specific implementation of the model.

&nbsp;

With version 6.6.0 of Hackolade Studio, we facilitate the process of conceptual data modeling by providing a Graph Diagram view to capture the entities and their relationships..

![Polyglot Cocenptual Graph View](<lib/Polyglot%20Cocenptual%20Graph%20View.png>)

&nbsp;

## Logical modeling

**Important:** for users coming from traditional data modeling tools for RDBMS and the traditional process of conceptual, logical, physical, it may be tempting to use Hackolade's Polyglot models purely in the same way as before, and ignore the nuances and purpose of our Polyglot approach.&nbsp; Please don't, as you might be disappointed by the result.&nbsp; It would be the same as wanting to use MongoDB with a normalized data model.

&nbsp;

Again, while our Polyglot model is technology-agnostic like logical models, it is really a **common physical schema** with the following features:

* allows denormalization, if desired, given access patterns;
* allows complex data types;
* generates schemas for a variety of technologies, with automatic mapping to the specific data types of the respective target technologies.

&nbsp;

Typically in logical models, you will have normalized entities, and you may denormalize in the physical model for performance.&nbsp; With a Polyglot model, it is advised to do things the other way around.&nbsp; You should use query-driven access patterns to define Polyglot structures with complex data types, including denormalization and polymorphism.&nbsp; When you derive to an RDBMS target, you will want to let our process normalize the structure, while you will want to keep the hierarchical structure for technology targets that allow it.

&nbsp;

Let's take this example of a Polyglot entity with a complex sub-object as well as a choice representing different possible sub-types for inheritance:

![Polyglot - complex structure and super-type](<lib/Polyglot%20-%20complex%20structure%20and%20super-type.png>)

&nbsp;

If you derive this Polyglot model in JSON, Avro, or MongoDB/CosmosBD/MarkLogic/etc., the target model will be exactly as above in the Polyglot model, since these technologies handle well complex data types and polymorphism.&nbsp; But if you derive this model in an RDBMS, we automatically normalize into the structure below where the complex attribute is moved into a separate table with a foreign key, and the choice is converted to inheritance tables:

![Polyglot - normalized complex and sub-types](<lib/Polyglot%20-%20normalized%20complex%20and%20sub-types.png>)

&nbsp;

&nbsp;

&nbsp;

More information about the philosophy behind our Polyglot Data Model concept can found on [this page](<https://hackolade.com/polyglot-data-modeling.html> "target=\"\_blank\"").

&nbsp;

This [other page](<PolyglotDataModel.md>) details how to use polyglot data models.

&nbsp;

