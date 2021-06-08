# HBase

A Bigtable is a sparse, distributed, persistent multidimensional sorted map.&nbsp; The map is indexed by a row key, column key, and a timestamp; each value in the map is an uninterpreted array of bytes.&nbsp; HBase uses a data model very similar to that of Bigtable.&nbsp; Users store data rows in labelled tables.&nbsp; A data row has a sortable key and an arbitrary number of columns.&nbsp; The table is stored sparsely, so that rows in the same table can have crazily-varying columns, if the user likes.&nbsp; Unlike most map implementations, in HBase/BigTable the key/value pairs are kept in strict alphabetical order. &nbsp;

&nbsp;

HBase is a NoSQL database that runs on top of a Hadoop cluster and provides random ream-time read/write access to data.&nbsp; It can also be used to store JSON in cells.

&nbsp;

To perform data modeling for HBase with Hackolade, you must first download the HBase [plugin](<DownloadadditionalDBtargetplugin.md>). &nbsp;

&nbsp;

Hackolade was specially adapted to support the data modeling of HBase, including the concepts of Column Families and Column Qualifiers.&nbsp; The application closely follows the terminology of the database.

&nbsp;

The data model in the picture below results from the modeling of an example from ["Introduction to HBase Schema Design"](<http://0b4af6cdc2f0c5998459-c0245c5c937c5dedcca3f1764ecc9b2f.r43.cf2.rackcdn.com/9353-login1210\_khurana.pdf> "target=\"\_blank\"") by Amandeep Khurana.

![Image](<lib/HBase%20workspace.png>)

## Namespace

A namespace is a logical grouping of tables analogous to a database in relation database systems. This abstraction lays the groundwork for upcoming multi-tenancy related features.&nbsp; A namespace can be created, removed or altered.&nbsp; Namespace membership is determined during table creation.

&nbsp;

## Table

Tables in HBase can serve as the input and output for [MapReduce](<https://en.wikipedia.org/wiki/Mapreduce> "target=\"\_blank\"") jobs run in Hadoop.&nbsp; Tables can also be used to store JSON.&nbsp; Tables are declared up front at schema definition time.

&nbsp;

![Image](<lib/HBase%20table.png>)

&nbsp;

## Row Keys

Row keys are uninterpreted bytes. Rows are lexicographically sorted with the lowest order appearing first in a table. The empty byte array is used to denote both the start and end of a tables' namespace.

&nbsp;

## Attributes data types

HBase supports a "bytes-in/bytes-out" interface, so anything that can be converted to an array of bytes can be stored as a value. Input could be strings, numbers, complex objects, or even images as long as they can rendered as bytes.

&nbsp;

Hackolade was specially adapted to support the data types and attributes behavior of HBase.

![Image](<lib/HBase%20-%20treeview.png>)

&nbsp;

## Forward-Engineering

Hackolade generates the create statement for the namespace, table, and column family.

&nbsp;

![Image](<lib/HBase%20forward-engineering%20script.png>)

&nbsp;

## Reverse-Engineering

You may define the connection parameters to your instance.&nbsp; Take a look at [this page](<ConnecttoanHBaseinstance.md>) for more information.

&nbsp;

The Hackolade reverse-engineering process of an HBase table includes a query for a representative random sample of rows, followed by a schema inference based on the sample, leading.&nbsp; You can easily discover, document, and enrich the structure of your column families and qualifiers, plus infer the structure of JSON documents you store in HBase.

&nbsp;

For more information on Apache HBase in general, please consult the [website](<http://hbase.apache.org/> "target=\"\_blank\"") and [book](<http://hbase.apache.org/book.html> "target=\"\_blank\"").

