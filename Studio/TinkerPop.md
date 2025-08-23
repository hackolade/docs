# TinkerPop

Apache TinkerPop is an open source, vendor-agnostic, graph computing framework for both graph databases (OLTP) and graph analytic system (OLAP.)&nbsp; It is distributed under the Apache2 license. When a data system is TinkerPop-enabled, its users are able to model their domain as a graph and analyze that graph using the Gremlin graph traversal language.

&nbsp;

Hackolade was specially built to support the data modeling of TinkerPop vertex labels and edge labels.&nbsp; The application closely follows the terminology of the database.

&nbsp;

To be clear, Hackolade is *not* a graph visualization tool, but a tool for **data modeling** of TinkerPop graph databases.&nbsp; You can find more details on graph-specific controls in [this page](<Graphshapes.md>).

&nbsp;

To perform data modeling for TinkerPop with Hackolade, you must first download the TinkerPop [plugin](<DownloadadditionalDBtargetplugin.md>). &nbsp;

&nbsp;

The data model in the picture below results from the reverse-engineering of the [Gremlin ThaCrew](<http://tinkerpop.apache.org/docs/current/tutorials/the-gremlin-console/#toy-graphs> "target=\"\_blank\"") example.&nbsp; Two views of the data model are available:

&nbsp;

&#49;) a graph view, with familiar circular node labels

![TinkerPop workspace](<lib/TinkerPop workspace.png>)

&nbsp;

&#50;) an Entity-Relationship Diagram (ERD) view, with the advantage of displaying properties for both vertex labels and edge labels:

![Tinkerpop workspace ERD](<lib/Tinkerpop workspace ERD.png>)

&nbsp;

&nbsp;

&nbsp;

## Vertex labels

Vertex labels are a semantic representation of vertices (nodes) in the graph.&nbsp; Vertex labels are used to represent the role of the vertex in the domain, making it possible to query the graph, to define constraints, and add indexes for properties.&nbsp; Labels can also be used to mark temporary states of a vertex.&nbsp;

&nbsp;

![Neo4j node label](<lib/Neo4j node label.png>)

&nbsp;

## Property keys

A vertex label usually has attributes, called "property keys" where the name (or key) is a string.

![Neo4j node label property keys](<lib/Neo4j node label property keys.png>)

&nbsp;

## Property types

Gremlin is data types-agnostic.&nbsp; It supports several formats for ingestion of data, in particular, GraphML, GraphSON, and GRYO.&nbsp;

&nbsp;

[GraphML](<http://tinkerpop.apache.org/docs/3.4.1/dev/io/#graphml> "target=\"\_blank\"") supports the following attribute types: string, float, double, int, long, and Boolean. &nbsp;

&nbsp;

[GraphSON](<http://tinkerpop.apache.org/docs/3.4.1/dev/io/#graphson> "target=\"\_blank\"") is considered both a "graph" format and a generalized object serialization format. That characteristic makes it useful as a serialization format for Gremlin Server where arbitrary objects of varying types may be returned as results.&nbsp; Without embedded types, the original type system was restricted to standard JSON types of Object, List, String, Number, Boolean and that will lead to "lossyness" in the format (i.e. a float will be interpreted as double).

&nbsp;

[Version 3.0 of GraphSON](<http://tinkerpop.apache.org/docs/3.4.1/dev/io/#graphson-3d0> "target=\"\_blank\"") was first introduced on TinkerPop 3.3.0 and is the default format when not specified.&nbsp; In GraphSON 3.0, there is explicit typed support for Map, List and Set as Gremlin relies on those types in quite specific ways that are not directly compatible with the JSON definitions of those collections.&nbsp; Null, Timestamp and UUID are also added.

&nbsp;

Multiple properties (**multi-properties**): a vertex property key can have multiple values. For example, a vertex can have multiple "name" properties.

Properties on properties (**meta-properties**): a vertex property can have properties (i.e. a vertex property can have key/value data associated with it).

&nbsp;

## Edge labels

Edge labels are a semantic representation of edges in the graph. Every edge must have one and only label, and 2 vertices can be linked by several edge labels.&nbsp; Edge labels are used during complex traversals across the graph, when only certain kinds of paths from vertex to vertex are necessary for a specific query.

&nbsp;

In TinkerPop, edges are unidirectional, going from one vertex to another vertex.&nbsp; In Hackolade we also represent edge labels that are implicitly bi-directional.&nbsp; For example, IS\_MARRIED\_TO should not require 2 edge labels, but instead be considered bi-directional.&nbsp; Since TinkerPop does not support the bi-directional concept, marking a relationship as bi-directional in Hackolade is for documentation purposes only.&nbsp;

&nbsp;

![Neo4j relationship type](<lib/Neo4j relationship type.png>)

&nbsp;

As TinkerPop is a type of graph database known as 'property graph', edge labels may have attributes, or properties, just like vertex labels do:

![Neo4j relationship type property keys](<lib/Neo4j relationship type property keys.png>)

&nbsp;

## Indexes

TinkerPop is also agnostic when it comes to index management.&nbsp; It is however possible to create an [index](<http://tinkerpop.apache.org/docs/current/reference/#index-step> "target=\"\_blank\"") on a single property key for any given label.&nbsp; A so-called composite index can also be created on more than one property key for a given label.

![Neo4j node index](<lib/Neo4j node index.png>)

&nbsp;

## Forward-Engineering

TinkerPop does not provide an abstraction for schemas. Gremlin is a functional, data-flow language that enables users to succinctly express complex traversals on (or queries of) their application's property graph.&nbsp; In order to provide added-value in forward-engineering, Hackolade provides a graph example in Gremlin syntax for the data model. &nbsp;

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![TinkerPop forward-engineering Gremlin](<lib/TinkerPop forward-engineering Gremlin.png>)

&nbsp;

## Reverse-Engineering

The process to reverse-engineer uses Gremlin functions to query the database, infer the [schema](<https://neo4j.com/docs/developer-manual/current/cypher/schema/> "target=\"\_blank\"") and represent the vertex labels and edge labels with their respective properties and indexes.

&nbsp;

For more details, you may consult the TinkerPop [website](<http://tinkerpop.apache.org/docs/current/reference/#\_tinkerpop\_documentation> "target=\"\_blank\"") and the [Gremlin console](<http://tinkerpop.apache.org/docs/current/tutorials/the-gremlin-console> "target=\"\_blank\"").

