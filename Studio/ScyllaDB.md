# ScyllaDB

ScyllaDB is an open-source distributed NoSQL column-oriented data store, designed to be compatible with [Apache Cassandra](<Cassandra.md>).&nbsp; It supports the same CQL query language but is written in C++ instead of Java to increase raw performance and leverage modern multi-code servers self-tuning.

&nbsp;

ScyllaDB is also a hybrid between a key-value and a column-oriented database.&nbsp; Rows are organized into tables.&nbsp; The first component of a primary key is a partition key, and rows clustered by the remaining columns of the key.&nbsp; Other columns may be indexed separately from the primary key.

&nbsp;

To perform data modeling for SycllaDB with Hackolade, you must first download the ScyllaDB [plugin](<DownloadadditionalDBtargetplugin.md>). &nbsp;

&nbsp;

Hackolade was specially adapted to support ScyllaDB, following the principles of [Cassandra data modeling](<https://hackolade.com/nosqldb/cassandra-data-modeling.html> "target=\"\_blank\""), including User-Defined Types and the concepts of Partitioning and Clustering keys.&nbsp; It lets users define, document, and display Chebotko physical diagrams.&nbsp; The application closely follows the ScyllaDB terminology, data types, and Chebotko notation. &nbsp;

&nbsp;

The data model in the picture below results from the reverse-engineering of a sample application imported in ScyllaDB.

&nbsp;

![Image](<lib/ScyllaDB%20workspace.png>)

## Keyspace ##

A keyspace is a ScyllaDB namespace that defines data replication on nodes.&nbsp; A cluster contains one keyspace per node.&nbsp; A keyspace is logical grouping of tables analogous to a database in relation database systems.&nbsp;

&nbsp;

## Table ##

Tables in ScyllaDB contain rows of columns, and a primary key identifies the location and order of stored data.&nbsp; Tables can also be used to store JSON.&nbsp; Tables are declared up front at schema definition time.

&nbsp;

&nbsp;

![Image](<lib/Cassandra%20table.png>)

&nbsp;

## Primary, Partition, and Clustering Keys ##

In ScyllaDB, primary keys can be simple or compound, with one or more partition keys, and optionally one or more clustering keys.&nbsp; The partition key determines which node stores the data.&nbsp; It is responsible for data distribution across the nodes.&nbsp; The additional columns determine per-partition clustering.&nbsp; Clustering is a storage engine process that sorts data within the partition.

&nbsp;

## Attributes data types ##

ScyllaDB supports a variety of scalar and complex data types, including lists, maps, and sets.

&nbsp;

Hackolade was specially adapted to support the data types and attributes behavior of ScyllaDB.

![Image](<lib/Cassandra%20data%20types.png>) ![Image](<lib/Cassandra%20string%20modes.png>) ![Image](<lib/Cassandra%20numeric%20modes.png>)

Some scalar types can be configured for different modes.&nbsp;

&nbsp;

Hackolade also supports ScyllaDB User-Defined Types (UDTs) via its [re-usable object definitions](<Reusableobjectsdefinitions.md>).

&nbsp;

&nbsp;

## Materialized Views ##

ScyllaDB supports materialized views to handle automated server-side denormalization.&nbsp; In theory, this removes the need for client-side handling and would ensure consistency between base and view data.&nbsp; Materialized views work particularly well with immutable insert-only data, but should not be used in case of low-cardinality data.&nbsp; Materialized views are designed to alleviate the pain for developers, but are essentially a trade-off of performance for connectedness.&nbsp; See more info in this [article](<http://www.doanduyhai.com/blog/?p=1930> "target=\"\_blank\"").

&nbsp;

Hackolade supports ScyllaDB materialized views, via a SELECT of columns of the underlying base table, to present the data of the base table with a different primary key for different access patterns. &nbsp;

&nbsp;

## Forward-Engineering ##

Hackolade dynamically generates the CQL script to create keyspaces, tables, columns and their data types, and indexes for the structure created with the application.

![Image](<lib/Cassandra%20forward-engineering.png>)

&nbsp;

As many people store JSON within text or blob columns, Hackolade allows for the schema design of those documents.&nbsp; That JSON structure is **not** forward-engineered in the CQL scrip, but is useful for developers, analysts and designers.

&nbsp;

## Reverse-Engineering ##

The connection is established using a connection string including (IP) address and port (typically 9042), and authentication using username/password if applicable.&nbsp;

&nbsp;

The Hackolade process for reverse-engineering of ScyllaDB databases includes the execution of cqlsh DESCRIBE statements to discover keyspaces, tables, columns and their types, and indexes.&nbsp; If JSON is detected in string columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

For more information on ScyllaDB in general, please consult the [website](<https://www.scylladb.com/> "target=\"\_blank\"").


***
_Created with the Personal Edition of HelpNDoc: [Easy EPub and documentation editor](<https://www.helpndoc.com>)_
