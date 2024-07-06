# DocumentDB

Amazon DocumentDB (with MongoDB compatibility) is a fully managed document database service that supports MongoDB workloads. As a document database,&nbsp; DocumentDB makes it easy to store, query, and index JSON data. Developers can use the same MongoDB application code, drivers, and tools as they do with MongoDB to run, manage, and scale workloads on Amazon DocumentDB.

&nbsp;

Its architecture separates storage and compute so that each layer can scale independently, though the system is limited to a single writable master. Amazon DocumentDB uses the Aurora Storage Engine, originally built for the MySQL relational database.&nbsp; The storage engine is distributed, fault-tolerant, self-healing, and durable, which it maintains by replicating data six ways across three AWS Availability Zones (AZs).&nbsp;

&nbsp;

“MongoDB compatible” means that DocumentDB interacts with the open source MongoDB 3.6 and 4.0 APIs. users can use the same MongoDB drivers, applications, and tools like Hackolade with DocumentDB with little or no changes. While DocumentDB supports a vast majority of the MongoDB APIs that customers actually use, it does not support every MongoDB API. The supported APIs, operations and data types are documented [here](<https://docs.aws.amazon.com/documentdb/latest/developerguide/mongo-apis.html> "target=\"\_blank\"").&nbsp; This other page documents the [functional differences ](<https://docs.aws.amazon.com/documentdb/latest/developerguide/mongo-apis.html> "target=\"\_blank\"")between DocumentDb and MongoDB.

&nbsp;

To perform data modeling for DocumentDB with Hackolade, you must first download the DocumentDB [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  

&nbsp;

Hackolade was specially adapted to support the data modeling of DocumentDB, including databases, collections and indexes.The application closely follows the terminology of the database.

&nbsp;

The data model in the picture below results from the reverse-engineering of the [Yelp Challenge Dataset](<https://www.kaggle.com/yelp-dataset/yelp-dataset> "target=\"\_blank\"").

&nbsp;

![Image](<lib/DocumentDB%20workspace.png>)

&nbsp;

## ObjectID

Each document stored in a collection requires a unique \_id field that acts as a primary key. If an inserted document omits the \_id field, the MongoDB driver automatically generates an ObjectId for the \_id field.&nbsp; ObjectIds are small, likely unique, fast to generate, and ordered. ObjectId values consists of 12-bytes, where the first four bytes are a timestamp that reflect the ObjectId’s creation, specifically:

* a 4-byte value representing the seconds since the Unix epoch,
* a 3-byte machine identifier,
* a 2-byte process id, and
* a 3-byte counter, starting with a random value.

&nbsp;

## Data types

MongoDB represents JSON documents in binary-encoded format called BSON behind the scenes. BSON extends the JSON model to provide [additional data types](<https://docs.mongodb.com/manual/reference/bson-types/> "target=\"\_blank\""), ordered fields, and to be efficient for encoding and decoding within different languages.&nbsp; The MongoDB BSON implementation is lightweight, fast and highly traversable. Like JSON, MongoDB's BSON implementation supports embedding objects and arrays within other objects and arrays.&nbsp; DocumentDB does not support all of the BSON data tyoes.&nbsp; See details [here](<https://docs.aws.amazon.com/documentdb/latest/developerguide/mongo-apis.html#mongo-apis-data-types> "target=\"\_blank\"").

&nbsp;

## Indexes

MongoDB provides a number of different index types to support specific types of data and queries.&nbsp; DcoumentDB does not support all the indexes and index properties of MongoDB.&nbsp; More details [here](<https://docs.aws.amazon.com/documentdb/latest/developerguide/mongo-apis.html#mongo-apis-index>).

* [default \_id index](<https://docs.mongodb.com/manual/core/document/#document-id-field> "target=\"\_blank\""):&nbsp; creates a unique index on the \_id field during the creation of a collection. The \_id index prevents clients from inserting two documents with the same value for the \_id field. You cannot drop this index on the \_id field.
* [single field](<https://docs.mongodb.com/manual/core/index-single/> "target=\"\_blank\""): supports the creation of user-defined ascending/descending indexes on a single field of a document.
* [compound index](<https://docs.mongodb.com/manual/core/index-compound/> "target=\"\_blank\""): also supports user-defined indexes on multiple fields, i.e. compound indexes.
* [multikey index](<https://docs.mongodb.com/manual/core/index-multikey/> "target=\"\_blank\""):&nbsp; uses multikey indexes to index the content stored in arrays. If you index a field that holds an array value, DocumentDB creates separate index entries for every element of the array. These multikey indexes allow queries to select documents that contain arrays by matching on element or elements of the arrays. It automatically determines whether to create a multikey index if the indexed field contains an array value; you do not need to explicitly specify the multikey type.
* [geospatial index](<https://docs.mongodb.com/manual/core/geospatial-indexes/> "target=\"\_blank\""): to support efficient queries of geospatial coordinate data, DocumentDB provides [2dsphere indexes](<https://docs.mongodb.com/manual/core/2dsphere/> "target=\"\_blank\"") that use spherical geometry to return results.

&nbsp;

&nbsp;

MongoDB can have the following properties:

* [unique indexes](<https://docs.mongodb.com/manual/core/index-unique/> "target=\"\_blank\""): the unique property for an index causes DocumentDB to reject duplicate values for the indexed field. Other than the unique constraint, unique indexes are functionally interchangeable with other indexes.
* [sparse indexes](<https://docs.mongodb.com/manual/core/index-sparse/> "target=\"\_blank\""): the sparse property of an index ensures that the index only contain entries for documents that have the indexed field. The index skips documents that do not have the indexed field.&nbsp; The sparse index option can be combined with the unique index option to reject documents that have duplicate values for a field but ignore documents that do not have the indexed key.
* [TTL indexes](<https://docs.mongodb.com/manual/core/index-ttl/> "target=\"\_blank\""): time-to-live indexes are special indexes that DocumentDB can use to automatically remove documents from a collection after a certain amount of time. This is ideal for certain types of information like machine generated event data, logs, and session information that only need to persist in a database for a finite amount of time.

&nbsp;

## Views

DocumentDB does not currently support MongoDB read-only views.

&nbsp;

## Sharding

MongoDB sharding is not necessary, given the distributed storage architecture of DocumentDB.

&nbsp;

## Forward-Engineering

DocumentDB does not provide an abstraction for schemas. In order to provide added-value in forward-engineering, Hackolade provides a JSON document by example for each collection in the model.&nbsp; The script also includes the creation of collection and indexes, and it can be applied to the DocumentDB instance.&nbsp;

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Image](<lib/DocumentDB%20forward-engineering.png>)

&nbsp;

&nbsp;

A button lets the user apply to a selected instance the script to create databases, collections with indexes as well as sample data if desired.

&nbsp;

## Reverse-Engineering

The connection to the DocumentDB cluster instance is established using connection parameters further described in [this page](<ConnecttoaDocumentDBinstance.md>).&nbsp;

&nbsp;

is established using a connection string including (IP) address and port (typically 27017), and authentication using username/password if applicable. X.409 SSL encryption can be specified, and SSH tunneling to a Cloud instance is supported as well. Hackolade also supports MongoDB Enterprise security features, with LDAP and Kerberos authentication.

&nbsp;

The Hackolade process for reverse-engineering uses [$sample](<https://docs.mongodb.com/manual/reference/operator/aggregation/sample/> "target=\"\_blank\"") syntax to perform the statistical sampling followed by a schema inference step.&nbsp; You may define a custom sampling with a specific aggregation pipeline query and sort.&nbsp; You may also enable inference of implicit relationship in the data.&nbsp; You may also enable inference of implicit relationship in the data.&nbsp; &nbsp;

&nbsp;

For more information on DocumentDB in general, please consult the [website](<https://aws.amazon.com/documentdb/> "target=\"\_blank\"").and [documentation](<https://docs.aws.amazon.com/documentdb/latest/developerguide/what-is.html> "target=\"\_blank\"").
