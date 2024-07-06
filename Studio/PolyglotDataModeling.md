# Polyglot Data Modeling

In traditional data modeling for relational databases using the conceptual, logical, and physical types of models, the purpose for a logical model has been defined as a database-agnostic view of normalized structures and business rules. &nbsp;

&nbsp;

It becomes quickly obvious that a logical model can only be technology-agnostic if and only if the target is strictly RDBMS.&nbsp; But as soon as you need for the logical model to be useful with other technologies, the strict definition of a logical model becomes too constraining.&nbsp; Given that Hackolade Studio supports so many technologies of databases and data exchanges that are not RDBMS, it was necessary to free ourselves from the strict constraints of the definition of logical models.&nbsp; To emphasize the differences, we found that using a different word was also necessary. &nbsp;

&nbsp;

> polyglot \| \\ ˈpä-lē-ˌglät \\ : speaking or writing several languages : multilingual

&nbsp;

Also with RDBMS vendors, the differences between the physical implementations are fairly minor, and so are the differences between the SQL dialects.&nbsp; Not so with all the targets supported by Hackolade for data-at-rest and data-in-motion.&nbsp; The feature set, the storage model, the terminology, the data types, the indexing capabilities, the schema syntax, etc.: there is very little in common between a MongoDB and a Cassandra data model, or between a Parquet and a Neo4j data model for example.&nbsp; The generation of physical names for entities (could be called tables, collections, nodes, vertices, files, etc.. in target technology) and attributes (could be called columns, fields, etc.. in target technology) should be capable of following different transformation rules, as Cassandra for example does not allow UPPERCASE while MongoDB will prefer camelCase, etc.

&nbsp;

In our definition, a Polyglot Data Model is sort of a logical model in the sense that it is technology-agnostic, but with additional features:

* it allows denormalization, if desired, given query-driven access patterns;
* it allows complex data types;
* it generates schemas for a variety of technologies, with automatic mapping to the specific data types of the respective target technologies;
* it combines in a single model both a conceptual layer in the form of a graph diagram view to be friendly to business users, as well as an ER Diagram for the logical layer.

&nbsp;

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

It is generally said that there are 3 categories of data modeling: conceptual, logical, and physical.&nbsp; In summary, conceptual modeling captures the common business language and defines the scope, whereas the logical model captures the business rules in a technology-agnostic manner, and the physical model represents the specific implementation of the model.

&nbsp;

With version 6.6.0 of Hackolade Studio, we facilitate the process of conceptual data modeling by providing a Graph Diagram view to capture the entities and their relationships..

![Polyglot Conceptual Graph View](<lib/Polyglot%20Conceptual%20Graph%20View.png>)

&nbsp;

## Logical modeling

**Important:** for users coming from traditional data modeling tools for RDBMS and the traditional process of conceptual, logical, physical, it may be tempting to use Hackolade's Polyglot models purely in the same way as before, and ignore the nuances and purpose of our Polyglot approach.&nbsp; Please don't, as you might be disappointed by the result.&nbsp; It would provide results similar to an exercise of using MongoDB with a normalized data model, i.e. not the optimal use of a NoSQL document database...

&nbsp;

**Note:** for decades, it has been said that logical models were "technology-agnostic.&nbsp; All that works well enough using the famous [rules of database normalization](<https://en.wikipedia.org/wiki/Database\_normalization> "target=\"\_blank\"") -- as long as your target technologies are relational only. &nbsp; But as soon as we're having to deal with NoSQL or with APIs and modern storage formats, it turns out that logical models which respect third normal form for many-to-many relationships with junction tables aren't "technology-agnostic" after all.  In a NoSQL document database, you would embed information and not use any junction table.  Similarly, supertypes/subtypes can be handled in NoSQL via polymorphism instead of inheritance tables, etc.

&nbsp;

&nbsp;

While our Polyglot model is truly technology-agnostic, it is also a **common physical model** with the following features:

* allows denormalization, if desired, given access patterns;
* allows complex data types;
* generates schemas for a variety of technologies, with automatic mapping to the specific data types of the respective target technologies.

&nbsp;

Typically in logical models, you would have normalized entities, and you may denormalize in the physical model for performance.&nbsp; With a Polyglot model, it is advised to do things the other way around.&nbsp; You should use query-driven access patterns to define Polyglot structures with complex data types, including denormalization and polymorphism.&nbsp; When you derive to an RDBMS target, you will want to let our process normalize the structure on-the-fly, while you will want to keep the hierarchical structure for technology targets that allow it.

&nbsp;

### Supertypes and subtypes

Hackolade Studio will let you create supertypes and subtypes in a Polyglot model, following either the traditional method:

![Polyglot - normalized complex and sub-types](<lib/Polyglot%20-%20normalized%20complex%20and%20sub-types.png>)

&nbsp;

or a denormalized method, with a complex sub-object as well as a oneOf choice representing different possible sub-types for inheritance

![Polyglot - complex structure and super-type](<lib/Polyglot%20-%20complex%20structure%20and%20super-type.png>)

&nbsp;

&nbsp;

Either way, the application will understand, depending on the target technology and its capabilities, whether to normalize with inheritance tables, or denormalize for NoSQL and leverage polymorphism.

&nbsp;

### Many-to-many relationships

With logical models having to be normalized, they are only "technology-agnostic" if their use is limited to relational databases, as explained above.&nbsp; With NoSQL databases allowing for denormalization with embedded objects and arrays, no junction tables are necessary to represent many-to-many relationships.

&nbsp;

Therefore, our Polyglot data models have a more intuitive way of documenting a many-to-many business rule:

![Polyglot many-to-many relationship](<lib/Polyglot%20many-to-many%20relationship.png>)

&nbsp;

And our automatic normalization function, when deriving the Polyglot model to an relational database, will generate the expected junction table:

![Polyglot many-to-many normalization](<lib/Polyglot%20many-to-many%20normalization.png>)

&nbsp;

Conversely, the derivation to a NoSQL target will leave the entities as declared in the Polyglot model and allow for further denormalization according to the needs of the access patterns.&nbsp; Ideally, the denormalization takes place directly in the Polyglot model.

&nbsp;

&nbsp;

More information about the philosophy behind our Polyglot Data Model concept can found on [this page](<https://hackolade.com/polyglot-data-modeling.html> "target=\"\_blank\"").

&nbsp;

This [other page](<PolyglotDataModel.md>) details how to use polyglot data models.

&nbsp;

&nbsp;

## Lineage and impact analysis of changes

Once a target model has been created and derived from a polyglot model, it contains all the derived objects.&nbsp; You may make some changes to the target model:

\- make changes to the properties of entities and attributes without changing them in the polyglot model.&nbsp; This is used if you need minor deviations;

\- add new entities and views that are specific to the physical target model, for example based on access patterns;

\- remove entities from the target model.&nbsp; This action does not delete the entity in the polyglot model;

\- add, delete or modify attributes, again without effect on the Polyglot model.

&nbsp;

You may also join entities from multiple polyglot models by repeating the operation to derive from polyglot.

&nbsp;

You may supplement the target model with metadata, index and partitioning information specific to the target technology, then forward-engineer artifacts according to your use case.

&nbsp;

An impact analysis dialog is displayed to let you decide which objects to include as part of this refresh operation.&nbsp; Maybe these objects were not selected originally, or they could have been added to the polyglot model since the previous refresh or derive operation, or they could have been deleted in the target model. &nbsp;

&nbsp;

![Polyglot Impact Analysis](<lib/Polyglot%20Impact%20Analysis.png>)

&nbsp;

When opening a target model with a reference to one or more polyglot models, you are presented with the option to update the objects.

&nbsp;

You may also permanently break the connection to the polyglot model.&nbsp; This operation should be done with care of course, as it cannot be re-established afterwards without restarting all the steps from scratch.&nbsp; The operation replaces all references to the objects of the polyglot model by the objects themselves.&nbsp; But further modifications in the polyglot model will no longer have any effect in the target model.

