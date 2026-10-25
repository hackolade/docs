# Cosmos DB SQL & MongoDB APIs

Microsoft Azure Cosmos DB (formerly known as Document DB) is a fully managed, massively scalable NoSQL database service, working with schema-free JSON documents. It is used by Real Madrid, Halo Games, X-Box, OneNote, etc...

&nbsp;

Cosmos DB provides a choice between 2 document API's: either the [SQL API](<https://docs.microsoft.com/en-us/azure/cosmos-db/documentdb-introduction> "target=\"_blank\"") (previously known as DocumentDB API) or a [MongoDB API](<https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction> "target=\"_blank\""). Hackolade supports both API's, with a separate plugin each. We also support the [Gremlin API](<https://docs.microsoft.com/en-us/azure/cosmos-db/graph-introduction> "target=\"_blank\"") which is documented in [this page](CosmosDBGremlin.md).

&nbsp;

To perform data modeling for Cosmos DB with Hackolade, you must first download the appropriate Cosmos DB [plugin](DownloadadditionalDBtargetplugin.md).

&nbsp;

Hackolade was specially adapted to support the data modeling of multiple object types within one single collection - while supporting multiple collections as well - in order to support the pricing model of Cosmos DB. The application closely follows the terminology of the database.

&nbsp;

The data model in the picture below results from the reverse-engineering of a sample travel application imported in Cosmos DB.\
![Cosmos DB workspace](<lib/Cosmos DB workspace.png>)

&nbsp;

## Collections

There is a fundamental difference with many other NoSQL document databases: Microsoft Azure Cosmos DB strongly suggests to store documents of different types into the same "collection". Pricing is consistent with this recommendation. It may seem counter-intuitive, when moving from a RDBMS or MongoDB, to store record (documents) of a different nature in the same container (collection), but this is done for performance and pricing purposes. A “type” attribute is necessary to differentiate the various objects stored in the collection. Most deployments have a low number of collections, although there is no hard limit.

&nbsp;

But having multiple collections is something that can be quite useful for different use cases:

- multi-tenancy: you want to be sure all data are separated
- different types of data requiring different [partitioning](<https://docs.microsoft.com/en-us/azure/cosmos-db/partitioning-overview> "target=\"_blank\"") strategies

&nbsp;

## Document type

When mixing different kinds of documents into the same collection, it becomes necessary to specify a "type" attribute to differentiate the various documents stored in the collection. In Hackolade, each Document Type is modeled as a separate entity or box, so its attributes can be defined separately. A specific attribute name must be identified to differentiate the different document types. The unique key and the document type field are common to all document types in the collection, and displayed at the top of each box in the ERD document:\
![Cosmos DB ERD shapes](<lib/Cosmos DB ERD shapes.png>)

&nbsp;

## IDs

The id value is always required, and it must be unique across all other documents in the same collection. If left out out, then Cosmos DB would automatically generate one using a GUID or a Globally Unique Identifier.

&nbsp;

The id is always a string and it can't be a number, date, Boolean, or another object, and it can't be longer than 255 characters.

&nbsp;

Also, for any document committed to a collection, 5 system defined elements such as \_rid, \_ts, \_self, \_etag, and \_attachments are automatically appended at the end of the document.

&nbsp;

## Attributes data types

The data types depend on the API chosen. Cosmos DB with Document API supports standard JSON [data types](<https://www.tutorialspoint.com/documentdb/documentdb_data_types.htm> "target=\"_blank\""), including arrays and objects. Cosmos DB with MongoDB API support [BSON data types](<https://docs.mongodb.com/manual/reference/bson-types/> "target=\"_blank\""). The Hackolade menu items, contextual menus, toolbar icon tooltips, and documentation are adapted to Cosmos DB terminology and feature set.

&nbsp;

Hackolade was specially adapted to support the data types and attributes behavior of Cosmos DB.

&nbsp;

![Cosmos DB schema tree view](<lib/Couchbase schema tree view.png>)

&nbsp;

## Indexes

By default, all Azure Cosmos DB data is indexed. And while many customers are happy to let Azure Cosmos DB automatically handle all aspects of indexing, it also supports specifying a custom indexing policy for collections during creation. More information can be found [here](<https://docs.microsoft.com/en-us/azure/cosmos-db/indexing-policies> "target=\"_blank\"").

&nbsp;

## Stored Procedures, database triggers, and user-defined function

Azure Cosmos DB's language integrated transactional execution of JavaScript lets developers write stored procedures, triggers, and user-defined function (UDFs) natively. Developers can write application logic that be executed on the database storage partitions. More details can be found [here](<https://docs.microsoft.com/en-us/azure/cosmos-db/programming> "target=\"_blank\"").

&nbsp;

## Forward-Engineering

We provide a sort of "forward-engineering by example", with an automatic JSON data sample generation. The script also includes the creation of indexes, stored Procedures, triggers, and UDFs, and it can be applied to the Azure instance.

&nbsp;

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

&nbsp;

![Cosmos DB SQL API forward-engineering script](<lib/Cosmos DB SQL API forward-engineering script.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create collections by example, as well as indexes, stored procedures, functions, and triggers.

&nbsp;

## Reverse-Engineering

For the SQL API (previously known as DocumentDB API), the connection is established using a connection string including URI address and port (typically 443), and authentication using an account key. Details on how to connect Hackolade to a Cosmos DB instance can be found on [this page](ConnecttoaCosmosDBinstance.md).

&nbsp;

For the MongoDB API, the connection is established using a host address and port (typically 10255), and authentication using a username and password. Click [here](MongoDBAPI.md) for more info.

&nbsp;

For more information on Cosmos DB in general, please consult the [website](<https://gotcosmos.com/> "target=\"_blank\"").and [documentation](<https://docs.microsoft.com/en-us/azure/cosmos-db/introduction> "target=\"_blank\"").
