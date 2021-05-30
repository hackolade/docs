# Cosmos DB SQL & MongoDB APIs

Microsoft Azure Cosmos DB (formerly known as Document DB) is a fully managed, massively scalable NoSQL database service, working with schema-free JSON documents. It is used by Real Madrid, Halo Games, X-Box, OneNote, etc...

&nbsp;

Cosmos DB provides a choice between 2 document API's: either the [SQL API](<https://docs.microsoft.com/en-us/azure/cosmos-db/documentdb-introduction> "target=\"\_blank\"") (previously known as DocumentDB API) or a [MongoDB API](<https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction> "target=\"\_blank\"").&nbsp; Hackolade supports both API's, with a separate plugin each.&nbsp; We also support the [Gremlin API](<https://docs.microsoft.com/en-us/azure/cosmos-db/graph-introduction> "target=\"\_blank\"") which is documented in [this page](<CosmosDBGremlin.md>).

&nbsp;

To perform data modeling for Cosmos DB with Hackolade, you must first download the appropriate Cosmos DB [plugin](<DownloadadditionalDBtargetplugin.md>).&nbsp;

&nbsp;

Hackolade was specially adapted to support the data modeling of multiple object types within one single collection - while supporting multiple collections as well - in order to support the pricing model of Cosmos DB.&nbsp; The application closely follows the terminology of the database.

&nbsp;

The data model in the picture below results from the reverse-engineering of a sample travel application imported in Cosmos DB.

![Image](<lib/Cosmos%20DB%20workspace.png>)

## Collections

There is a fundamental difference with many other NoSQL document databases: Microsoft Azure Cosmos DB strongly suggests to store documents of different types into the same "collection".&nbsp; Pricing is consistent with this recommendation.&nbsp; It may seem counter-intuitive, when moving from a RDBMS or MongoDB, to store record (documents) of a different nature in the same container (collection), but this is done for performance and pricing purposes.&nbsp; A “type” attribute is necessary to differentiate the various objects stored in the collection.&nbsp; Most deployments have a low number of collections, although there is no hard limit. &nbsp;

&nbsp;

But having multiple collections is something that can be quite useful for different use cases:

\- multi-tenancy: you want to be sure all data are separated

\- different types of data requiring different [partitioning](<https://docs.microsoft.com/en-us/azure/cosmos-db/partitioning-overview> "target=\"\_blank\"") strategies

&nbsp;

## Document type

When mixing different kinds of documents into the same collection, it becomes necessary to specify a "type" attribute to differentiate the various documents stored in the collection.&nbsp; In Hackolade, each Document Type is modeled as a separate entity or box, so its attributes can be defined separately.&nbsp; A specific attribute name must be identified to differentiate the different document types.&nbsp; The unique key and the document type field are common to all document types in the collection, and displayed at the top of each box in the ERD document:

![Image](<lib/Cosmos%20DB%20ERD%20shapes.png>)

&nbsp;

## IDs

The id value is always required, and it must be unique across all other documents in the same collection.&nbsp; If left out out, then Cosmos DB would automatically generate one using a GUID or a Globally Unique Identifier.

&nbsp;

The id is always a string and it can't be a number, date, Boolean, or another object, and it can't be longer than 255 characters.

&nbsp;

Also, for any document committed to a collection, 5 system defined elements such as \_rid, \_ts, \_self, \_etag, and \_attachments are automatically appended at the end of the document.

&nbsp;

## Attributes data types

The data types depend on the API chosen.&nbsp; Cosmos DB with Document API supports standard JSON [data types](<https://www.tutorialspoint.com/documentdb/documentdb\_data\_types.htm> "target=\"\_blank\""), including arrays and objects.&nbsp; Cosmos DB with MongoDB API support [BSON data types](<https://docs.mongodb.com/manual/reference/bson-types/> "target=\"\_blank\"").&nbsp; The Hackolade menu items, contextual menus, toolbar icon tooltips, and documentation are adapted to Cosmos DB terminology and feature set. &nbsp;

&nbsp;

Hackolade was specially adapted to support the data types and attributes behavior of Cosmos DB.

&nbsp;

![Image](<lib/Couchbase%20DTD.png>)

&nbsp;

## Indexes

By default, all Azure Cosmos DB data is indexed.&nbsp; And while many customers are happy to let Azure Cosmos DB automatically handle all aspects of indexing, it also supports specifying a custom indexing policy for collections during creation.&nbsp; More information can be found [here](<https://docs.microsoft.com/en-us/azure/cosmos-db/indexing-policies> "target=\"\_blank\"").

## Stored Procedures, database triggers, and user-defined function

Azure Cosmos DB's language integrated transactional execution of JavaScript lets developers write stored procedures, triggers, and user-defined function (UDFs) natively.&nbsp; Developers can write application logic that be executed on the database storage partitions.&nbsp; More details can be found [here](<https://docs.microsoft.com/en-us/azure/cosmos-db/programming> "target=\"\_blank\"").

## Forward-Engineering

We provide a sort of "forward-engineering by example", with an automatic JSON data sample generation.&nbsp; The script also includes the creation of indexes, stored Procedures, triggers, and UDFs, and it can be applied to the Azure instance.

![Image](<lib/Cosmos%20DB%20SQL%20API%20forward-engineering%20script.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create collections by example, as well as indexes, stored procedures, functions, and triggers.

## Reverse-Engineering

For the SQL API (previously known as DocumentDB API), the connection is established using a connection string including URI address and port (typically 443), and authentication using an account key. Details on how to connect Hackolade to a Cosmos DB instance can be found on [this page](<ConnecttoaCosmosDBinstance.md>).

&nbsp;

For the MongoDB API, the connection is established using a host address and port (typically 10255), and authentication using a username and password.&nbsp; Click [here](<MongoDBAPI.md>) for more info.

&nbsp;

&nbsp;

For more information on Cosmos DB in general, please consult the [website](<https://gotcosmos.com/> "target=\"\_blank\"").and [documentation](<https://docs.microsoft.com/en-us/azure/cosmos-db/introduction> "target=\"\_blank\"").

