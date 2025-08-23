# Cassandra

Apache Cassandra is designed to handle large amounts of data across many commodity servers, providing high availability through robust support for clusters spanning of multiple data centers and asynchronous masterless replication and low latency operations.&nbsp; It is essentially a hybrid between a key-value and a column-oriented database.&nbsp; Rows are organized into tables.&nbsp; The first component of a primary key is a partition key, and rows clustered by the remaining columns of the key.&nbsp; Other columns may be indexed separately from the primary key.

&nbsp;

DataStax is a software vendor whose employees are key contributors to the Apache Cassandra project. &nbsp;

&nbsp;

To perform data modeling for Cassandra with Hackolade, you must first download the Cassandra [plugin](<DownloadadditionalDBtargetplugin.md>). &nbsp;

&nbsp;

Hackolade was specially adapted to support the [data modeling of Cassandra](<https://hackolade.com/nosqldb/cassandra-data-modeling.html> "target=\"\_blank\""), including User-Defined Types and the concepts of Partitioning and Clustering keys. It lets users define, document, and display Chebotko physical diagrams.&nbsp; The application closely follows the Cassandra terminology, data types, and Chebotko notation. &nbsp;

&nbsp;

The data model in the picture below results from the data modeling of an application described in [Chapter 5](<https://www.oreilly.com/ideas/cassandra-data-modeling> "target=\"\_blank\"") of the book "Cassandra: the Definitive Guide" from O'Reilly.

&nbsp;

![Cassandra workspace](<lib/Cassandra workspace.png>)

## Keyspace

A keyspace is a Cassandra namespace that defines data replication on nodes.&nbsp; A cluster contains one keyspace per node.&nbsp; A keyspace is logical grouping of tables analogous to a database in relation database systems.&nbsp;

&nbsp;

## Table

Tables in Cassandra contain rows of columns, and a primary key identifies the location and order of stored data.&nbsp; Tables can also be used to store JSON.&nbsp; Tables are declared up front at schema definition time.

&nbsp;

&nbsp;

![Image](<lib/Cassandra table schema tree view.png>)

&nbsp;

## Primary, Partition, and Clustering Keys

In Cassandra, primary keys can be simple or compound, with one or more partition keys, and optionally one or more clustering keys.&nbsp; The partition key determines which node stores the data.&nbsp; It is responsible for data distribution across the nodes.&nbsp; The additional columns determine per-partition clustering.&nbsp; Clustering is a storage engine process that sorts data within the partition.

&nbsp;

## Attributes data types

Cassandra supports a variety of scalar and complex data types, including lists, maps, and sets.

&nbsp;

Hackolade was specially adapted to support the data types and attributes behavior of Cassandra.

![Cassandra data types](<lib/Cassandra data types.png>) ![Cassandra string modes](<lib/Cassandra string modes.png>) ![Cassandra numeric modes](<lib/Cassandra numeric modes.png>)

Some scalar types can be configured for different modes.&nbsp;

&nbsp;

Hackolade also supports Cassandra User-Defined Types via its [re-usable object definitions](<Reusableobjectsdefinitions.md>).

&nbsp;

&nbsp;

## Indexes

An index provides a means to access data in DataStax Enterprise using attributes other than the partition key. The benefit of an index is fast, efficient lookup of data that matches a given condition.&nbsp; Built-in indexes are best on a table having many rows that contain the indexed value. The more unique values that exist in a particular column, the more overhead on average is required to query and maintain the index.&nbsp; It is useful to consult this section on [when not to use an index](<https://docs.datastax.com/en/dse/6.7/cql/cql/cql\_using/useWhenIndex.html#Whennottouseanindex> "target=\"\_blank\"").

&nbsp;

Hackolade supports [Global Secondary Indexes](<https://docs.datastax.com/en/dse/6.7/cql/cql/cql\_using/useSecondaryIndex.html> "target=\"\_blank\""), as well as [custom indexes](<https://docs.datastax.com/en/dse/6.8/cql/cql/cql\_reference/cql\_commands/cqlCreateCustomIndex.html> "target=\"\_blank\"") and [search indexes](<https://docs.datastax.com/en/dse/6.8/cql/cql/cql\_reference/cql\_commands/cqlCreateSearchIndex.html> "target=\"\_blank\"").

&nbsp;

## Materialized Views

With version 3.0, Cassandra introduced materialized views to handle automated server-side denormalization.&nbsp; In theory, this removes the need for client-side handling and would ensure consistency between base and view data.&nbsp; Materialized views work particularly well with immutable insert-only data, but should not be used in case of low-cardinality data.&nbsp; Materialized views are designed to alleviate the pain for developers, but are essentially a trade-off of performance for accuracy.&nbsp; See more info in this [article](<http://www.doanduyhai.com/blog/?p=1930> "target=\"\_blank\"").

&nbsp;

Hackolade supports Cassandra materialized views, via a SELECT of columns of the underlying base table, to present the data of the base table with a different primary key for different access patterns. &nbsp;

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the CQL script to create keyspaces, tables, columns and their types, and indexes for the structure created with the application.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Cassandra forward-engineering](<lib/Cassandra forward-engineering.png>)

&nbsp;

As many people store JSON within text or blob columns, Hackolade allows for the schema design of those documents.&nbsp; That JSON structure is **not** forward-engineered in the CQL scrip, but is useful for developers, analysts and designers.

&nbsp;

## Reverse-Engineering

The connection is established using a connection string including (IP) address and port (typically 9042), and authentication using username/password if applicable.&nbsp; Details on how to connect Hackolade to a Cassandra instance can be found on [this page](<ConnecttoaCassandrainstance.md>).

&nbsp;

The Hackolade process for reverse-engineering of Cassandra databases includes the execution of cqlsh DESCRIBE statements to discover keyspaces, tables, columns and their types, and indexes.&nbsp; If JSON is detected in string columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

For more information on Cassandra in general, please consult the Apache Cassandra [website](<http://cassandra.apache.org/> "target=\"\_blank\""), DataStax [website](<https://www.datastax.com/> "target=\"\_blank\""), and [book](<https://www.oreilly.com/ideas/cassandra-data-modeling> "target=\"\_blank\"").

