# SQL and NoSQL databases, APIs, and storage formats

Hackolade's main added value is in providing the ability to perform the data modeling for JSON-based databases, mainly nested objects (sub-documents and arrays, a.k.a. maps and lists.) Hackolade even has a pending patent on its "Method and Process to graphically model schemas for NoSQL and multimodel databases and REST APIs".

&nbsp;

Whereas most relational database adhere to a SQL standard which ensures a common approach (even though some nuances are possible), NoSQL databases have sometimes fundamentally different approaches for storage and architecture, and often use different terminology for similar concepts:

&nbsp;

<table style="width:100%">
<colgroup><col style="width:11%"><col style="width:10%"><col style="width:11%"><col style="width:13%"><col style="width:12%"><col style="width:13%"><col style="width:11%"><col style="width:10%"><col style="width:9%"></colgroup>
<thead>
<tr>
<th>Generic terminology</th>
<th>SQL</th>
<th>MongoDB</th>
<th>DynamoDB</th>
<th>Couchbase</th>
<th>Azure Cosmos DB</th>
<th>Elasticsearch</th>
<th>Datastax Cassandra</th>
<th>Apache HBase</th>
</tr>
</thead>
<tbody>
<tr>
<td>Container</td>
<td>User schema</td>
<td>Database</td>
<td>Region</td>
<td>Bucket</td>
<td>Collection</td>
<td>Index</td>
<td>Keyspace</td>
<td>Namespace</td>
</tr>
<tr>
<td>Entity</td>
<td>Table</td>
<td>Collection</td>
<td>Table</td>
<td>Document kind</td>
<td>Document type</td>
<td>Type</td>
<td>Table</td>
<td>Table</td>
</tr>
<tr>
<td>Record</td>
<td>Record</td>
<td>Document</td>
<td>Item</td>
<td>Document</td>
<td>Document</td>
<td>Document</td>
<td>Row</td>
<td>Row</td>
</tr>
<tr>
<td>Attribute</td>
<td>Column</td>
<td>Field</td>
<td>Attribute</td>
<td>Field</td>
<td>Field</td>
<td>Field</td>
<td>Column</td>
<td>Column</td>
</tr>
<tr>
<td>Primary Key</td>
<td>Primary Key</td>
<td>ObjectID</td>
<td>Hash (&amp; range)</td>
<td>Document ID</td>
<td>id</td>
<td>id</td>
<td>Partition Key+ Clustering Key</td>
<td>Row Key</td>
</tr>
<tr>
<td>Index</td>
<td>Index</td>
<td>Index</td>
<td>Index</td>
<td>Index</td>
<td>Index</td>
<td>Index</td>
<td>Index</td>
<td>Index</td>
</tr>
<tr>
<td>Partition</td>
<td>Partition</td>
<td>Shard</td>
<td>Partition</td>
<td>vBucket</td>
<td>Partition</td>
<td>Shard</td>
<td>Partition</td>
<td>Shard</td>
</tr>
<tr>
<td>View</td>
<td>View</td>
<td>View</td>
<td>Global Secondary Index</td>
<td>View</td>
<td>n/a</td>
<td>Filtered alias</td>
<td>Materialized View</td>
<td>View</td>
</tr>
<tr>
<td>Object</td>
<td>n/a</td>
<td>Sub-document</td>
<td>Map</td>
<td>Object</td>
<td>Object</td>
<td>Object/Nested</td>
<td>Map</td>
<td>n/a</td>
</tr>
<tr>
<td>Array</td>
<td>Array</td>
<td>Array</td>
<td>List</td>
<td>Array</td>
<td>Array</td>
<td>Array</td>
<td>List</td>
<td>n/a</td>
</tr>
</tbody>
</table>

&nbsp;

<table style="width:100%">
<colgroup><col style="width:10%"><col style="width:13%"><col style="width:13%"><col style="width:13%"><col style="width:13%"><col style="width:13%"><col style="width:13%"><col style="width:12%"></colgroup>
<thead>
<tr>
<th>Generic terminology</th>
<th>Google RealTime Firebase</th>
<th>Google Cloud Firestore</th>
<th>MarkLogic</th>
<th>Apache Hive</th>
<th>Apache Avro</th>
<th>Couchbase Analytics</th>
<th>Google Cloud BigQuery</th>
</tr>
</thead>
<tbody>
<tr>
<td>Container</td>
<td>User schema</td>
<td>Database</td>
<td>Database</td>
<td>Database</td>
<td>Namespace</td>
<td>Dataverse</td>
<td>Dataset</td>
</tr>
<tr>
<td>Entity</td>
<td>Table</td>
<td>Collection</td>
<td>Collection/Directory</td>
<td>Table</td>
<td>Record</td>
<td>Dataset</td>
<td>Table</td>
</tr>
<tr>
<td>Record</td>
<td>Record</td>
<td>Document</td>
<td>Document</td>
<td>Row</td>
<td>n/a</td>
<td>Document</td>
<td>Record</td>
</tr>
<tr>
<td>Attribute</td>
<td>Column</td>
<td>Field</td>
<td>Field</td>
<td>Column</td>
<td>Field</td>
<td>Field</td>
<td>Field</td>
</tr>
<tr>
<td>Primary Key</td>
<td>Primary Key</td>
<td>ObjectID</td>
<td>URI</td>
<td>Partition Key+ Clustering Key</td>
<td>n/a</td>
<td>Document ID</td>
<td>n/a</td>
</tr>
<tr>
<td>Index</td>
<td>Index</td>
<td>Index</td>
<td>Index</td>
<td>Index</td>
<td>n/a</td>
<td>Index</td>
<td>n/a</td>
</tr>
<tr>
<td>Partition</td>
<td>Partition</td>
<td>Shard</td>
<td>Forest</td>
<td>Partition</td>
<td>n/a</td>
<td>n/a</td>
<td>Partition</td>
</tr>
<tr>
<td>View</td>
<td>View</td>
<td>View</td>
<td>View</td>
<td>View</td>
<td>n/a</td>
<td>n/a</td>
<td>View</td>
</tr>
<tr>
<td>Object</td>
<td>n/a</td>
<td>Sub-document</td>
<td>Object</td>
<td>Map</td>
<td>Record/map</td>
<td>Object</td>
<td>Record</td>
</tr>
<tr>
<td>Array</td>
<td>Array</td>
<td>Array</td>
<td>Array</td>
<td>List</td>
<td>Array/enum</td>
<td>Array</td>
<td>Array</td>
</tr>
</tbody>
</table>

&nbsp;

<table style="width:100%">
<colgroup><col style="width:10%"><col style="width:13%"><col style="width:13%"><col style="width:13%"><col style="width:13%"><col style="width:13%"><col style="width:13%"><col style="width:12%"></colgroup>
<tbody>
<tr>
<td><strong>Generic terminology</strong></td>
<td><strong>Parquet</strong></td>
<td><strong>AWS Glue Data Catalog</strong></td>
<td><strong>ScyllaDB</strong></td>
<td><strong>RDBMS</strong></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>Container</td>
<td>File</td>
<td>Database</td>
<td>Keyspace</td>
<td>Schema/user</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>Entity</td>
<td>Message</td>
<td>Table</td>
<td>Table</td>
<td>Table</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>Record</td>
<td>Row</td>
<td>Row</td>
<td>Row</td>
<td>Row</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>Attribute</td>
<td>Column</td>
<td>Column</td>
<td>Column</td>
<td>Column</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>Primary Key</td>
<td>n/a</td>
<td>Partition Key+ Clustering Key</td>
<td>Partition Key+ Clustering Key</td>
<td>Primary Key</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>Index</td>
<td>n/a</td>
<td>Index</td>
<td>Index</td>
<td>Index</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>Partition</td>
<td>n/a</td>
<td>Partition</td>
<td>Partition</td>
<td>Partition</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>View</td>
<td>n/a</td>
<td>View</td>
<td>Materialized view</td>
<td>View</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>Object</td>
<td>Map</td>
<td>Map</td>
<td>Map</td>
<td>n/a</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>Array</td>
<td>List</td>
<td>List</td>
<td>List</td>
<td>n/a</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

&nbsp;

Each target vendor may also support its own functional features and list of attribute types.

&nbsp;

To simplify the user's life, Hackolade adapts to the terminology and feature set of each database platform target for the model. The menu items, contextual menus, toolbar icon tooltips, and documentation all dynamically change depending on the selected target.

&nbsp;

Isn't it ironic that a technology that bears the label of 'schemaless' is also known for the fact that schema design is one of its toughest challenges? Each of the NoSQL vendors dedicates a large part of its documentation to data modeling: [MongoDB](<https://docs.mongodb.com/manual/core/data-modeling-introduction/> "target=\"_blank\""), [DynamoDB](<http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GuidelinesForTables.html> "target=\"_blank\""), [Couchbase](<https://developer.couchbase.com/documentation/server/current/data-modeling/intro-data-modeling.html> "target=\"_blank\""), [Cassandra](<http://docs.datastax.com/en/cql/3.3/cql/ddl/ddlCQLDataModelingTOC.html> "target=\"_blank\"").

&nbsp;

The following pages analyze the characteristics of each NoSQL database vendor, from the perspective of a data modeler. These pages do not cover the technical architecture as it pertains to infrastructure and performance, which would go well beyond the scope of the Hackolade application.
