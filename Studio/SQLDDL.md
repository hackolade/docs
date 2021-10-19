# SQL DDL

Migrating from relational databases to NoSQL requires a mind shift, and Hacklolade can help in the migration of the schema from a relational model to a model combining embedding and referencing, so you can leverage the power, performance, and flexibility of NoSQL.

&nbsp;

For more information on NoSQL document schema design, you may want to read this 3-part [blog](<http://blog.mongodb.org/post/87200945828/6-rules-of-thumb-for-mongodb-schema-design-part-1> "target=\"\_blank\"").&nbsp; Then use Hackolade to facilitate the migration...

&nbsp;

The table below summarizes denormalization strategies and best practices:

| **If...** | **Then...** |
| --- | --- |
| Relationship is one-to-one | Merge tables into one collection |
| Relationship is one-to-few | Merge tables into parent collection with an array of embedded child documents |
| Relationship is one-to-many | Embed parent data as nested sub-document in child collection (consider bucketing) |
| Relationship is one-to-zillions | Store reference to parent in child document (consider child tables) |
| Relationship is many-to-one | Embed child data as nested sub-document in parent |
| Relationship is many-to-many | Store data as separate documents, with reference to the parent in the child, and vice-versa |
| Data reads are mostly parent fields | Store children as separate documents |
| Data writes are mostly parent fields or child fields (not both) | Store children as separate documents |
| Data writes are mostly parent fields and child fields (both) | Store children as nested objects |


&nbsp;

From the blog referenced above, here are some “rules of thumb” to guide you through these innumerable (but not infinite) choices:

1. think in terms of queries, updates, and data representation, rather than in terms of storage.&nbsp; Data access patterns (instead of 3NF) drives you data model
1. favor embedding unless there is a compelling reason not to
1. needing to access an object on its own is a compelling reason not to embed it
1. arrays should not grow without bound. High-cardinality arrays are a compelling reason not to embed.
1. don't be afraid of application-level joins (with proper indexing)
1. consider the write/read ratio when denormalizing. A field that will mostly be read and only seldom updated is a good candidate for denormalization.

&nbsp;

## Reverse-engineer a Data Definition Language file (DDL)

Data Definition Language (DDL) is a vocabulary used to define data structures in SQL databases. These statements are used to create, alter, or drop data structures in an SQL database instance.

&nbsp;

If you generate a DDL from Oracle, Microsoft SQL Server, MySQL, PostgreSQL, or Hadoop Hive, you can then read it with Hackolade and generate a model of the schema.

&nbsp;

Choose Tools \> Reverse-Engineering \> Data Definition Language file:

![Reverse-Engineering -- DDL menu](<lib/Reverse-Engineering%20--%20DDL%20menu.png>)

&nbsp;

Then choose the source database (as each vendor has it's own implementation of the DDL syntax).&nbsp; The structure of a DDL can be imported either as an entity in the Entity Relationship Diagram, or alternatively as a model definition so it could be re-used in the model:

&nbsp;

![Reverse-Engineering -- DDL select file](<lib/Reverse-Engineering%20--%20DDL%20select%20file.png>)

&nbsp;

and select the file from your file system.

&nbsp;

If you wish to force the destination of the reverse-engineering operation, you may specify the container in which the entities will be inserted.

&nbsp;

Hackolade currently supports the following SQL dialects: Oracle, MariaDB, MySQL, SQL Server, DB2, PostgreSQL, Informix, Refshift, Snowflake, and Teradata.

&nbsp;

When you click OK, Hackolade will read the DDL file and generate the schema model, for example:

![Reverse-engineering -- Northwind Oracle](<lib/Reverse-engineering%20--%20Northwind%20Oracle.png>)

&nbsp;

## Suggest denormalization

You should save the resulting model as a base, for example v0.&nbsp; Then it is suggested you save it again as v1 and work with the denormalization function to make v1 evolve towards a denormalized model.

&nbsp;

The user needs to have a fairly good idea of where he wants to go with the schema design, and use Hackolade to facilitate the work.&nbsp; For example, with the Northwind database shown above, in a NoSQL model, one would want to merge the tables 'orders' and 'order details' while embedding some data from the master tables around.

&nbsp;

![Suggest denormalization -- select tables](<lib/Suggest%20denormalization%20--%20select%20tables.png>)

The successive steps could include:

&#49;. Embed as sub-documents into 'orders': employees, customers, and shippers

&#50;. Embed as sub-documents into 'products': suppliers and categories

&#51;. Embed as sub-documents into 'order details': products

&#52;. Embed as an array of sub-documents into 'order': order details

&#53;. Delete 'order details'

&nbsp;

![Reverse-Engineering - denormalization](<lib/Reverse-Engineering%20-%20denormalization.png>)

&nbsp;

As a susequent step, the modeler may want to denormalize products information into the order detail lines by embedding product sub-documents in the child, the deleting the unnecesary fields.&nbsp; This time, as a products master collection is justified as its own entity, it should not be deleted.

&nbsp;

![Reverse-Engineering - denomalization step 2](<lib/Reverse-Engineering%20-%20denomalization%20step%202.png>)

&nbsp;

But denormalization, depending on how you want to access data to optimize performance, may also include 2-way referencing, or 2-way embedding.

