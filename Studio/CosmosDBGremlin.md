# Cosmos DB Gremlin

Microsoft Azure Cosmos DB is a globally distributed, multi-model database service supporting document, key-value, graph, and column-family data models. Azure Cosmos DB provides a graph database service via the Gremlin API on a fully managed database service designed for any scale.

&nbsp;

Azure Cosmos DB's Gremlin API is built based on the graph computing framework Apache TinkerPop 3.2.&nbsp; The [Gremlin API](<https://docs.microsoft.com/en-us/azure/cosmos-db/graph-introduction> "target=\"\_blank\"") in Azure Cosmos DB uses the Gremlin query language.&nbsp; To be clear, Hackolade is *not* a graph visualization tool, but a tool for **data modeling** of Cosmos DB Gremlin graph databases. &nbsp;

&nbsp;

To perform data modeling for Cosmos DB Gremlin API with Hackolade, you must first download the Cosmos DB Gremlin API [plugin](<DownloadadditionalDBtargetplugin.md>).&nbsp; You can find more details on graph-specific controls in [this page](<Graphshapes.md>).

&nbsp;

Hackolade was specially adapted to support the data modeling of vertices and edges and their respective properties. The application closely follows the terminology of the database.

&nbsp;

The data model in the picture below results from the reverse-engineering of a [sample graph](<https://docs.microsoft.com/en-us/azure/cosmos-db/graph-introduction#graph-database-by-example> "target=\"\_blank\"") imported in Cosmos DB.&nbsp; Two views of the data model are available:

&nbsp;

&#49;) a graph view, with familiar circular vertex labels:

![Image](<lib/CosmosDB-Gremlin%20workspace.png>)

&nbsp;

&nbsp;

&#50;) an Entity-Relationship Diagram (ERD) view, with the advantage of displaying properties for both vertex labels and edge labels:

![Image](<lib/CosmosDB-Gremlin%20ERD%20view.png>)

&nbsp;

&nbsp;

## Vertex labels

Vertex labels are a semantic representation of vertices in the graph.&nbsp; Vertex labels are used to represent the role of the vertex in the domain, making it possible to query the graph, to define constraints, and add indexes for properties.&nbsp; Labels can also be used to mark temporary states of a vertex.&nbsp;

&nbsp;

## Properties

A vertex label usually has attributes, called "properties" where the name (or key) is a string.

![Image](<lib/CosmosDB%20Gremlin%20vertex%20label%20properties.png>)

&nbsp;

## Property data types

The supported property types are:

* Number
* String
* Boolean

&nbsp;

## Edge labels

Edge labels are a semantic representation of relationships in the graph. Every relationship must have one and only type, and 2 nodes can be linked by several relationship types.&nbsp; Relationship types are used during complex traversals across the graph, when only certain kinds of paths from node to node are necessary for a specific query.

&nbsp;

In Cosmos DB, edges are unidirectional, going from one vertex label to another vertex label.&nbsp; In Hackolade we also represent edge labels that are implicitly bi-directional.&nbsp; For example, IS\_MARRIED\_TO should not require 2 edge labels, but instead be considered bi-directional.&nbsp; Since Gremlin does not support the bi-directional concept, marking an edge label as bi-directional in Hackolade is for documentation purposes only.&nbsp;

&nbsp;

![Image](<lib/Neo4j%20relationship%20type.png>)

&nbsp;

As Cosmos DB Gremlin is a type of graph database known as 'property graph', edge labels may have attributes, or properties, just like vertex labels:

![Image](<lib/Neo4j%20relationship%20type%20property%20keys.png>)

&nbsp;

## Indexes

By default, all Azure Cosmos DB data is indexed.&nbsp; And while many customers are happy to let Azure Cosmos DB automatically handle all aspects of indexing, it also supports specifying a custom indexing policy for collections during creation.&nbsp; More information can be found [here](<https://docs.microsoft.com/en-us/azure/cosmos-db/indexing-policies> "target=\"\_blank\"").

## Stored Procedures, database triggers, and user-defined function

Azure Cosmos DB's language integrated transactional execution of JavaScript lets developers write stored procedures, triggers, and user-defined function (UDFs) natively.&nbsp; Developers can write application logic that be executed on the database storage partitions.&nbsp; More details can be found [here](<https://docs.microsoft.com/en-us/azure/cosmos-db/programming> "target=\"\_blank\"").

&nbsp;

## Forward-Engineering

Cosmos DB does not provide an abstraction for schemas. Gremlin is a functional, data-flow language that enables users to succinctly express complex traversals on (or queries of) their application's property graph.&nbsp; In order to provide added-value in forward-engineering, Hackolade provides a graph example in Gremlin syntax for the data model.&nbsp; The script also includes the creation of indexes, stored Procedures, triggers, and UDFs, and it can be applied to the Azure instance.&nbsp;

&nbsp;

![Image](<lib/CosmosDB%20Gremlin%20script%20forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create graph vertices and edges by example, as well as indexes, stored procedures, functions, and triggers.

&nbsp;

## Reverse-Engineering

For the Gremlin API, the connection is established using a connection string including URI address and port (typically 443), and authentication using an account key. Details on how to connect Hackolade to a Cosmos DB instance can be found on [this page](<ConnecttoaCosmosDBinstance.md>).

&nbsp;

&nbsp;

For more information on Cosmos DB in general, please consult the [website](<https://gotcosmos.com/> "target=\"\_blank\"").and [documentation](<https://docs.microsoft.com/en-us/azure/cosmos-db/introduction> "target=\"\_blank\"").

