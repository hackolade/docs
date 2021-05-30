# NoSQL databases, storage formats, REST APIs

Hackolade's main added value is in providing the ability to perform the data modeling for JSON-based databases, mainly nested objects (sub-documents and arrays, a.k.a. maps and lists.)&nbsp; Hackolade even has a pending patent on its "Method and Process to graphically model schemas for NoSQL and multimodel databases and REST APIs".

&nbsp;

Whereas most relational database adhere to a SQL standard which ensures a common approach (even though some nuances are possible), NoSQL databases have sometimes fundamentally different approaches for storage and architecture, and often use different terminology for similar concepts:

&nbsp;

| **Generic terminology** | **SQL** | **MongoDB** | **DynamoDB** | **Couchbase** | **Azure Cosmos DB** | **Elasticsearch** | **Datastax Cassandra** | **Apache HBase** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Container | User schema | Database | Region | Bucket | Collection | Index | Keyspace | Namespace |
| Entity | Table | Collection | Table | Document kind | Document type | Type | Table | Table |
| Record | Record | Document | Item | Document | Document | Document | Row | Row |
| Attribute | Column | Field | Attribute | Field | Field | Field | Column | Column |
| Primary Key | Primary Key | ObjectID | Hash (\& range) | Document ID | id | id | Partition Key+ Clustering Key&nbsp; | Row Key |
| Index | Index | Index | Index | Index | Index | Index | Index | Index |
| Partition | Partition | Shard | Partition | vBucket | Partition | Shard | Partition | Shard |
| View | View | View | Global Secondary Index | View | n/a | Filtered alias | Materialized View | View |
| Object | n/a | Sub-document | Map | Object | Object | Object/Nested | Map | n/a |
| Array | Array | Array | List | Array | Array | Array | List | n/a |


&nbsp;

| **Generic terminology** | **Google RealTime Firebase** | **Google Cloud Firestore** | **MarkLogic** | **Apache Hive** | **Apache Avro** | **Couchbase Analytics** | **Goocle Cloud BigQuery** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Container | User schema | Database | Database | Database | Namespace | Dataverse | Dataset |
| Entity | Table | Collection | Collection/Directory | Table | Record | Dataset | Table |
| Record | Record | Document | Document | Row | n/a | Document | Record |
| Attribute | Column | Field | Field | Column | Field | Field | Field |
| Primary Key | Primary Key | ObjectID | URI | Partition Key+ Clustering Key&nbsp; | n/a | Document ID | n/a |
| Index | Index | Index | Index | Index | n/a | Index | n/a |
| Partition | Partition | Shard | Forest | Partition | n/a | n/a | Partition |
| View | View | View | View | View | n/a | n/a | View |
| Object | n/a | Sub-document | Object | Map | Record/map | Object | Record |
| Array | Array | Array | Array | List | Array/enum | Array | Array |


&nbsp;

| **Generic terminology** | **Parquet** | **AWS Glue Data Catalog** | **ScyllaDB** | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Container | File | Database | Keyspace | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| Entity | Message | Table | Table | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| Record | Row | Row | Row | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| Attribute | Column | Column | Column | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| Primary Key | n/a | Partition Key+ Clustering Key&nbsp; | Partition Key+ Clustering Key&nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| Index | n/a | Index | Index | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| Partition | n/a | Partition | Parition | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| View | n/a | View | Materialized view | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| Object | Map | Map | Map | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| Array | List | List | List | &nbsp; | &nbsp; | &nbsp; | &nbsp; |


&nbsp;

Each target vendor may also support its own functional features and list of attribute types.

&nbsp;

To simplify the user's life, Hackolade adapts to the terminology and feature set of each database platform target for the model.&nbsp; The menu items, contextual menus, toolbar icon tooltips, and documentation all dynamically change depending on the selected target.

&nbsp;

Isn't it ironic that a technology that bears the label of 'schemaless' is also known for the fact that schema design is one of its toughest challenges?&nbsp; Each of the NoSQL vendors dedicates a large part of its documentation to data modeling: [MongoDB](<https://docs.mongodb.com/manual/core/data-modeling-introduction/> "target=\"\_blank\""), [DynamoDB](<http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GuidelinesForTables.html> "target=\"\_blank\""), [Couchbase](<https://developer.couchbase.com/documentation/server/current/data-modeling/intro-data-modeling.html> "target=\"\_blank\""), [Cassandra](<http://docs.datastax.com/en/cql/3.3/cql/ddl/ddlCQLDataModelingTOC.html> "target=\"\_blank\"").

&nbsp;

The following pages analyze the characteristics of each NoSQL database vendor, from the perspective of a data modeler.&nbsp; These pages do not cover the technical architecture as it pertains to infrastructure and performance, which would go well beyond the scope of the Hackolade application.

