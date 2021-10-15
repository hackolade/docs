# DynamoDB

Amazon Web Services' DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability.&nbsp; It is derived from the ground-breaking 2007 [Dynamo paper](<http://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf> "target=\"\_blank\"") which, along with Google’s 2006 [Bigtable paper](<http://static.googleusercontent.com/media/research.google.com/en//archive/bigtable-osdi06.pdf> "target=\"\_blank\""), introduced the concept of NoSQL databases.

&nbsp;

Hackolade was specially adapted to support the data modeling of DynamoDB tables including partition (hash) and sort (range) keys, supporting multiple regions as well.&nbsp; The application closely follows the terminology of the database.&nbsp; Support was enhanced with v5.0.8 for single-table storage, through the use of views (a more visual equivalent to the concept of facets in the [NoSQL Workbench](<https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/workbench.html> "target=\"\_blank\"").)

&nbsp;

The data model in the picture below results from the reverse-engineering of the sample application described [here](<http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/SampleData.CreateTables.html> "target=\"\_blank\"").

![DynamoDB workspace](<lib/DynamoDB%20workspace.png>)

&nbsp;

## Table groups

In DynamoDB, you can assign multiple tables to a single group to manage your resources. Simply provide a group name and a key-value pair for tagging your table to the group to be created.

&nbsp;

## Tables, items and attributes

A table is collection of data.&nbsp; Each table contains zero or more items. An *item* is a group of attributes that is uniquely identifiable among all of the other items. There is no limit to the number of items you can store in a table.&nbsp; Each item is composed of one or more attributes.

## Keys

As is often the case with NoSQL databases, DynamoDB has a unique storage model:&nbsp; When a table is created, in addition to the table name, a primary key for the table has to be specified.&nbsp; The primary key uniquely identifies each item in the table, so that no two items can have the same key.&nbsp; DynamoDB supports two different kinds of primary keys:

* Partition key – A simple primary key, composed of one attribute.&nbsp; DynamoDB uses the partition key's value as input to an internal hash function.&nbsp; The output from the hash function determines the partition (physical storage internal to DynamoDB) in which the item will be stored.&nbsp; *No two items in a table can have the same partition key value.*
* Partition key and sort key – Referred to as a composite primary key, this type of key is composed of two attributes.&nbsp; The first attribute is the partition key, and the second attribute is the sort key.&nbsp; DynamoDB uses the partition key value as input to an internal hash function.&nbsp; The output from the hash function determines the partition (physical storage internal to DynamoDB) in which the item will be stored.&nbsp; *All items with the same partition key are stored together, in sorted order by sort key value.&nbsp; It is possible for two items to have the same partition key value, but those two items must have different sort key values.*

&nbsp;

**Note:**

The partition key of an item is also known as its 'hash' attribute.&nbsp; The term hash attribute derives from DynamoDB's usage of an internal hash function to evenly distribute data items across partitions, based on their partition key values.

The sort key of an item is also known as its 'range' attribute.&nbsp; The term range attribute derives from the way DynamoDB stores items with the same partition key physically close together, in sorted order by the sort key value.

&nbsp;

Each primary key attribute must be a scalar (meaning that it can only hold a single value).&nbsp; **The only data types allowed for primary key attributes are string, number, or binary.**&nbsp; There are no such restrictions for other, non-key attributes.

&nbsp;

## Other table properties

Given the fully managed nature of DynamoDB, when you create a table, you need to specify how much provisioned throughput capacity you want to reserve for reads and writes. DynamoDB will reserve the necessary resources to meet the specified throughput needs while ensuring consistent, low-latency performance. The provisioned throughput settings can be changed at any time, increasing or decreasing capacity as needed.&nbsp; The throughput settings can be documented in Hackolade.

&nbsp;

Many applications can benefit from the ability to capture changes to items stored in a DynamoDB table, at the point in time when such changes occur.&nbsp; DynamoDB Streams captures a time-ordered sequence of item-level modifications in any DynamoDB table, and stores this information in a log for up to 24 hours. Other applications can access this log and view the data items as they appeared before and after they were modified, in near real time.&nbsp; When you enable a stream on a table, DynamoDB captures information about every modification to data items in the table.&nbsp; The stream settings can be documented in Hackolade.

&nbsp;

## Data types

DynamoDB supports many different data types for attributes within a table.&nbsp; They can be categorized as follows:

* Scalar Types – A scalar type can represent exactly one value.&nbsp; The scalar types are **number, string, binary, Boolean, and null.**
* Document Types – A document type can represent a complex structure with nested attributes—such as you would find in a JSON document.&nbsp; The document types are list and map.
  * A list type attribute can store an ordered collection of values.&nbsp; Lists are enclosed in square brackets: \[ ... \]&nbsp; **A list is similar to a JSON array.**&nbsp; There are no restrictions on the data types that can be stored in a list element, and the elements in a list element do not have to be of the same type.
  * A map type attribute can store an unordered collection of name-value pairs.&nbsp; Maps are enclosed in curly braces: { ... }&nbsp; **A map is similar to a JSON object.**&nbsp; There are no restrictions on the data types that can be stored in a map element, and the elements in a map do not have to be of the same type.&nbsp; Maps are ideal for storing JSON documents in DynamoDB.&nbsp;
* Set Types – A set type can represent multiple scalar values.&nbsp; The set types are string set, number set, and binary set.&nbsp; All of the elements within a set must be of the same type.&nbsp; For example, an attribute of type Number Set can only contain numbers; String Set can only contain strings; and so on.

Note that date values are stored as ISO-8601 formatted strings, shifted to UTC, with millisecond precision.

&nbsp;

Hackolade was specially adapted to support the data types and attributes behavior of DynamoDB.&nbsp; The data model in the picture below is the direct result of the reverse-engineering of the sample application described [here](<http://docs.aws.amazon.com/amazondynamodb/latest/gettingstartedguide/GettingStarted.NodeJs.01.html> "target=\"\_blank\"").&nbsp;

&nbsp;

![Image](<lib/DynamoDB%20schema%20tree%20view.png>)

&nbsp;

## Indexes

Whenever a write occurs on a table, all of the table's indexes must be updated. In a write-heavy environment with large tables, this can consume large amounts of system resources. In a read-only or read-mostly environment, this is not as much of a concern—however, one should ensure that the indexes are actually being used by the application, and not simply taking up space.

&nbsp;

Indexes in DynamoDB are different from their counterparts with relational databases. When you create a secondary index, you must specify its key attributes – a partition key and a sort key. After you create the secondary index, you can query it or scan it just as you would with a table. DynamoDB does not have a query optimizer, so a secondary index is only used when you query it or scan it.

&nbsp;

DynamoDB supports two different kinds of indexes:

* [Global secondary indexes](<http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GSI.html> "target=\"\_blank\"") – The primary key of the index can be any two attributes from its table.
* [Local secondary indexes](<http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/LSI.html> "target=\"\_blank\"") – The partition key of the index must be the same as the partition key of its table. However, the sort key can be any other attribute.

&nbsp;

DynamoDB ensures that the data in a secondary index is eventually consistent with its table. You can request strongly consistent Query or Scan actions on a table or a local secondary index. However, global secondary indexes only support eventual consistency.

&nbsp;

More information can be found [here](<http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/SecondaryIndexes.html> "target=\"\_blank\"").

## Views

In Hackolade, we have enabled the views feature.&nbsp; While these views do not get forward-engineered to the database instance, they are useful in the context of single-table storage, in order to visualize and document access patterns for a table.&nbsp; Views are a more visual equivalent to the concept of facets in the [NoSQL Workbench](<https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/workbench.html> "target=\"\_blank\"")).

&nbsp;

![DynamoDB views](<lib/DynamoDB%20views.png>)&nbsp;

&nbsp;

## Forward-Engineering

Hackolade dynamically generates [CreateTable](<http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API\_CreateTable.html> "target=\"\_blank\"") and [ConditionExpression](<http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Expressions.SpecifyingConditions.html> "target=\"\_blank\"") scripts based on model attributes and constraints.&nbsp; These can be applied directly to the DynamoDB instance:

![DynamoDB apply to instance](<lib/DynamoDB%20apply%20to%20instance.png>)

## Reverse-Engineering

A DynamoDB can be installed either locally or as a managed database at AWS.&nbsp; The connection is established using a connection string including (IP) address and port (typically 8000), and if managed at AWS, authentication using the IAM awsAccessKeyId/awsSecretAccessKey for the region where the DynamoDB instance is located.

&nbsp;

The Hackolade reverse-engineering process of a DynamoDB table includes a query for a representative random sample of items, followed by a schema inference based on the sample.

&nbsp;

For more information on DynamoDB in general, please consult the [website](<http://aws.amazon.com/dynamodb/> "target=\"\_blank\"").

