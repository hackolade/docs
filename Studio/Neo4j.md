# Neo4j

Neo4j is a graph database management system described as an ACID-compliant transactional database with native graph storage and processing.&nbsp; Neo4j is by far the most popular graph database according to [DB-Engines ranking](<https://db-engines.com/en/ranking/graph%20dbms> "target=\"\_blank\"").&nbsp; Cypher is a declarative graph query language that allows for expressive and efficient querying and updating of a property graph.

&nbsp;

Hackolade was specially built to support the data modeling of Neo4j node labels and relationship types.&nbsp; The application closely follows the terminology of the database.

&nbsp;

To be clear, Hackolade is *not* a graph visualization tool, but a tool for **data modeling** of Neo4j graph databases. &nbsp;

&nbsp;

To perform [data modeling for Neo4j](<https://hackolade.com/nosqldb/neo4j-data-modeling.html> "target=\"\_blank\"") with Hackolade, you must first download the Neo4j [plugin](<DownloadadditionalDBtargetplugin.md>).&nbsp; You can find more details on graph-specific controls in [this page](<Graphshapes.md>).

&nbsp;

The data model in the picture below results from the reverse-engineering of the movie recommendations [Neo4j sandbox](<https://neo4j.com/sandbox-v2/> "target=\"\_blank\"").&nbsp; Two views of the data model are available:

&nbsp;

&#49;) a graph view, with familiar circular node labels

![Graph Neo4j workspace](<lib/Graph%20Neo4j%20workspace.png>)

&nbsp;

&#50;) an Entity-Relationship Diagram (ERD) view, with the advantage of displaying properties for both node labels and relationship types:

![Neo4j workspace](<lib/Neo4j%20workspace.png>)

&nbsp;

&nbsp;

&nbsp;

## Node labels

Node labels are a semantic representation of nodes in the graph.&nbsp; Node labels are used to represent the role of the node in the domain, making it possible to query the graph, to define constraints, and add indexes for properties.&nbsp; Labels can also be used to mark temporary states of a node.&nbsp;

&nbsp;

![Neo4j node label](<lib/Neo4j%20node%20label.png>)

&nbsp;

## Property keys

A node label usually has attributes, called "property keys" where the name (or key) is a string.

![Neo4j node label property keys](<lib/Neo4j%20node%20label%20property%20keys.png>)

&nbsp;

## Property data types

The supported property types are:

* *Number*, an abstract type, which has the following subtypes:
  * Integer
  * Float
* String
* Boolean
* *Spatial types*:
  * Point (with subtypes: WGS84, WGS84 3D, Cartesian and Cartersian 3D)
* *Temporal types*:
  * Date
  * Time
  * LocalTime
  * DateTime
  * LocalDateTime
  * Duration

&nbsp;

## Node key constraints

A node key constraint ensures that all nodes with a particular label have a set of defined properties whose combined value is unique, and where all properties in the set are present.

![Neo4j node key contraint](<lib/Neo4j%20node%20key%20contraint.png>)

## Relationship types

Relationship types are a semantic representation of relationships in the graph. Every relationship must have one and only type, and 2 nodes can be linked by several relationship types.&nbsp; Relationship types are used during complex traversals across the graph, when only certain kinds of paths from node to node are necessary for a specific query.

&nbsp;

In Neo4j, relationship types are unidirectional, going from one node label to another node label.&nbsp; In Hackolade we also represent relationship types that are implicitly bi-directional.&nbsp; For example, IS\_MARRIED\_TO should not require 2 relationship types, but instead be considered bi-directional.&nbsp; Since Neo4j does not support the bi-directional concept, marking a relationship as bi-directional in Hackolade is for documentation purposes only.&nbsp;

&nbsp;

![Neo4j relationship type](<lib/Neo4j%20relationship%20type.png>)

&nbsp;

As Neo4j is a type of graph database known as 'property graph', relationship types may have attributes, or property keys, just like node labels:

![Neo4j relationship type property keys](<lib/Neo4j%20relationship%20type%20property%20keys.png>)

&nbsp;

## Indexes

In Neo4j, it is possible to create an [index](<https://neo4j.com/docs/developer-manual/current/cypher/schema/index/> "target=\"\_blank\"") on a single property for any given label.&nbsp; A so-called composite index can also be created on more than one property for a given label.

![Neo4j node index](<lib/Neo4j%20node%20index.png>)

&nbsp;

With Neo4j version 5, new indexes types have been added: range, text, point, and full-text.

&nbsp;

## Forward-Engineering

Cypher is a declarative graph query language that allows for expressive and efficient querying and updating of a property graph.&nbsp; Hackolade dynamically generates [Cypher](<https://neo4j.com/developer/cypher/> "target=\"\_blank\"") code as the model is created via the application.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Neo4j forward-engineered Cypher](<lib/Neo4j%20forward-engineered%20Cypher.png>)

&nbsp;

## Reverse-Engineering

The process to reverse-engineer uses the APOC procedure [apoc.meta.subgraph()](<http://neo4j-contrib.github.io/neo4j-apoc-procedures/3.5/schema/meta-graph/> "target=\"\_blank\"") to query the database, infer the [schema](<https://neo4j.com/docs/developer-manual/current/cypher/schema/> "target=\"\_blank\"") and represent the node labels and relationship types with their property keys, constraints, and indexes.&nbsp; If APOC is not available, the process falls back on the Cypher function db.schema(), but db.schema() is not preferred as it is known to have [some bugs](<https://github.com/neo4j/neo4j/issues/9726> "target=\"\_blank\"") (also [here](<https://github.com/opencypher/morpheus/issues/666> "target=\"\_blank\"").)

&nbsp;

For more details, you may consult the Neo4j [website](<https://neo4j.com/> "target=\"\_blank\"") and [graph database concepts page](<https://neo4j.com/docs/developer-manual/current/introduction/graphdb-concepts/> "target=\"\_blank\"").

