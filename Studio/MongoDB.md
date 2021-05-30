# MongoDB

MongoDB is a free and open-source cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with schemas. MongoDB is developed by MongoDB Inc. &nbsp;

&nbsp;

Hackolade was specially built to support the [data modeling of MongoDB](<https://hackolade.com/nosqldb/mongodb-data-modeling.html> "target=\"\_blank\"") collections, supporting multiple databases as well.&nbsp; The application closely follows the terminology of the database.

&nbsp;

The data model in the picture below results from the reverse-engineering of the [Yelp Challenge Dataset](<https://www.yelp.com/dataset\_challenge> "target=\"\_blank\"").

![Image](<lib/MongoDB%20workspace.png>)

&nbsp;

## ObjectID

In MongoDB, each document stored in a collection requires a unique \_id field that acts as a primary key. If an inserted document omits the \_id field, the MongoDB driver automatically generates an ObjectId for the \_id field.&nbsp; ObjectIds are small, likely unique, fast to generate, and ordered. ObjectId values consists of 12-bytes, where the first four bytes are a timestamp that reflect the ObjectId’s creation, specifically:

* a 4-byte value representing the seconds since the Unix epoch,
* a 3-byte machine identifier,
* a 2-byte process id, and
* a 3-byte counter, starting with a random value.

&nbsp;

## Data types

MongoDB represents JSON documents in binary-encoded format called BSON behind the scenes. BSON extends the JSON model to provide [additional data types](<https://docs.mongodb.com/manual/reference/bson-types/> "target=\"\_blank\""), ordered fields, and to be efficient for encoding and decoding within different languages.&nbsp; The MongoDB BSON implementation is lightweight, fast and highly traversable. Like JSON, MongoDB's BSON implementation supports embedding objects and arrays within other objects and arrays – MongoDB can even 'reach inside' BSON objects to build indexes and match objects against query expressions on both top-level and nested BSON keys.

&nbsp;

BSON is a binary serialization format used to store documents and make remote procedure calls in MongoDB. The BSON specification is located [here](<http://bsonspec.org> "target=\"\_blank\"").

&nbsp;

Hackolade was specially built to support the data types and attributes behavior of MongoDB, including the BSON types.

![Image](<lib/MongoDB%20DTD.png>)

## Indexes

MongoDB provides a number of different index types to support specific types of data and queries.

* [default \_id index](<https://docs.mongodb.com/manual/core/document/#document-id-field> "target=\"\_blank\""):&nbsp; MongoDB creates a unique index on the \_id field during the creation of a collection. The \_id index prevents clients from inserting two documents with the same value for the \_id field. You cannot drop this index on the \_id field.
* [single field](<https://docs.mongodb.com/manual/core/index-single/> "target=\"\_blank\""): MongoDB supports the creation of user-defined ascending/descending indexes on a single field of a document.
* [compound index](<https://docs.mongodb.com/manual/core/index-compound/> "target=\"\_blank\""): MongoDB also supports user-defined indexes on multiple fields, i.e. compound indexes.
* [multikey index](<https://docs.mongodb.com/manual/core/index-multikey/> "target=\"\_blank\""): MongoDB uses multikey indexes to index the content stored in arrays. If you index a field that holds an array value, MongoDB creates separate index entries for every element of the array. These multikey indexes allow queries to select documents that contain arrays by matching on element or elements of the arrays. MongoDB automatically determines whether to create a multikey index if the indexed field contains an array value; you do not need to explicitly specify the multikey type.
* [geospatial index](<https://docs.mongodb.com/manual/core/geospatial-indexes/> "target=\"\_blank\""): to support efficient queries of geospatial coordinate data, MongoDB provides two special indexes: [2d indexes](<https://docs.mongodb.com/manual/core/2d/> "target=\"\_blank\"") that uses planar geometry when returning results and [2dsphere indexes](<https://docs.mongodb.com/manual/core/2dsphere/> "target=\"\_blank\"") that use spherical geometry to return results.
* [text index](<https://docs.mongodb.com/manual/core/index-text/> "target=\"\_blank\""): MongoDB provides a text index type that supports searching for string content in a collection. These text indexes do not store language-specific stop words (e.g. “the”, “a”, “or”) and stem the words in a collection to only store root words.
* [hashed indexes](<https://docs.mongodb.com/manual/core/index-hashed/> "target=\"\_blank\""): to support hash based sharding, MongoDB provides a hashed index type, which indexes the hash of the value of a field. These indexes have a more random distribution of values along their range, but only support equality matches and cannot support range-based queries.

&nbsp;

MongoDB can have the following properties:

* [unique indexes](<https://docs.mongodb.com/manual/core/index-unique/> "target=\"\_blank\""): the unique property for an index causes MongoDB to reject duplicate values for the indexed field. Other than the unique constraint, unique indexes are functionally interchangeable with other MongoDB indexes.
* [partial indexes](<https://docs.mongodb.com/manual/core/index-partial/> "target=\"\_blank\""): they only index the documents in a collection that meet a specified filter expression. By indexing a subset of the documents in a collection, partial indexes have lower storage requirements and reduced performance costs for index creation and maintenance.&nbsp; Partial indexes offer a superset of the functionality of sparse indexes and should be preferred over sparse indexes.
* [sparse indexes](<https://docs.mongodb.com/manual/core/index-sparse/> "target=\"\_blank\""): the sparse property of an index ensures that the index only contain entries for documents that have the indexed field. The index skips documents that do not have the indexed field.&nbsp; The sparse index option can be combined with the unique index option to reject documents that have duplicate values for a field but ignore documents that do not have the indexed key.
* [TTL indexes](<https://docs.mongodb.com/manual/core/index-ttl/> "target=\"\_blank\""): time-to-live indexes are special indexes that MongoDB can use to automatically remove documents from a collection after a certain amount of time. This is ideal for certain types of information like machine generated event data, logs, and session information that only need to persist in a database for a finite amount of time.

&nbsp;

## Views

Read-only views in MongoDB were introduced with version 3.4.&nbsp; DBAs can define non-materialized views that expose only a subset of data from an underlying collection, i.e. a view that filters out entire documents or specific fields, such as Personally Identifiable Information (PII) from sales data or health records. As a result, risks of data exposure are dramatically reduced. DBAs can define a view of a collection that's generated from an aggregation over another collection(s) or view.

&nbsp;

MongoDB views are handled through a pipeline projection of the fields of a collection (with possible $lookup to additional collections.)&nbsp; In Hackolade views are represented in the Entity Relationship diagram alongside collections with a visual icon to distinguish them. &nbsp;

&nbsp;

## Sharding

Sharding is a method for distributing data across multiple machines.&nbsp; MongoDB uses sharding to support deployments with very large data sets and high throughput operations.&nbsp; Database systems with large data sets or high throughput applications can challenge the capacity of a single server.&nbsp; There are two methods for addressing system growth: vertical scaling (bigger, more powerful server) and horizontal scaling (more servers with divided datasets).&nbsp; MongoDB supports horizontal scaling through sharding.

&nbsp;

To distribute the documents in a collection, MongoDB partitions the collection using the shard key.&nbsp; The shard key consists of an immutable field or fields that exist in every document in the target collection.&nbsp;

&nbsp;

You choose the shard key when sharding a collection.&nbsp; The choice of a shard key cannot be changed after sharding.&nbsp; A sharded collection can have only one shard key.

&nbsp;

MongoDB supports 3 sharding strategies for distributing data across sharded clusters: hashed sharding, ranged sharding, and tag-aware (or zoned):

* [hashed sharding](<https://docs.mongodb.com/manual/core/hashed-sharding/> "target=\"\_blank\""): it involves computing a hash of the shard key field’s value.&nbsp; Each chunk is then assigned a range based on the hashed shard key values.&nbsp; MongoDB automatically computes the hashes when resolving queries using hashed indexes.&nbsp; Applications do not need to compute hashes.
* [ranged sharding](<https://docs.mongodb.com/v3.4/core/ranged-sharding/> "target=\"\_blank\""): it involves dividing data into ranges based on the shard key values.&nbsp; Each chunk is then assigned a range based on the shard key values.
* [zone sharding](<https://docs.mongodb.com/manual/tutorial/manage-shard-zone/> "target=\"\_blank\"") (previously known as tag-aware): in sharded clusters, you can create zones that represent a group of shards and associate one or more ranges of shard key values to that zone.&nbsp; MongoDB routes reads and writes that fall into a zone range only to those shards inside of the zone.&nbsp;

## Forward-Engineering

For those developing Node.js applications on top of a MongoDB database, you may want to leverage the object document mapper (ODM) [Mongoose](<http://mongoosejs.com/> "target=\"\_blank\"") that allows you build what your object model would look like, then auto-generate all the boilerplate logic that goes with it.&nbsp; Hackolade dynamically generates the Mongoose script based on model attributes and constraints.

&nbsp;

Since version 3.2, MongoDB provides the capability to validate documents during updates and insertions. Validation rules are specified on a per-collection basis using the validator option, which takes a document that specifies the validation rules or expressions.&nbsp; Hackolade dynamically generates the [validator](<https://docs.mongodb.com/manual/core/document-validation/> "target=\"\_blank\"") script based on model attributes and constraints.

&nbsp;

Since version 3.6, this script is now in extended JSON Schema syntax.&nbsp; Hackolade easily generates the proper syntax without requiring any JSON Schema knowledge.&nbsp;

&nbsp;

![Image](<lib/Forward-Engineering%20-%20MongoDB%20Script.png>)

&nbsp;

A button lets the user apply to a selected instance the script to create databases, collections with optional $jsonschema validator, indexes, and sharding configuration, as well sa sample data if desired.

&nbsp;

## Reverse-Engineering

The connection is established using a connection string including (IP) address and port (typically 27017), and authentication using username/password if applicable. X.409 SSL encryption can be specified, and SSH tunneling to a Cloud instance is supported as well. Hackolade also supports MongoDB Enterprise security features, with LDAP and Kerberos authentication.

&nbsp;

The Hackolade process for reverse-engineering of MongoDB databases is different depending on the MongoDB version.&nbsp; For versions prior to 3.2, collections are queried with a random function. Starting with version 3.2, Hackolade uses [$sample](<https://docs.mongodb.com/manual/reference/operator/aggregation/sample/> "target=\"\_blank\"") syntax to perform the statistical sampling followed by the schema inference. &nbsp;

&nbsp;

User may define the sampling with a specific aggregation pipeline query and sort.

&nbsp;

For more information on MongoDB in general, please consult the [website](<http://www.mongodb.com/> "target=\"\_blank\"").

