# Neptune Gremlin

Amazon Neptune is a fully managed graph database service engine optimized for storing billions of relationships and querying the graph with milliseconds latency. It supports 2 separate popular graph models: Property Graph and W3C's RDF, and their respective query languages Apache TinkerPop Gremlin and SPARQL.

&nbsp;

This page deals only with the property graph side using the Gremlin query language.

&nbsp;

> [!NOTE]
> There are a few important differences between the Amazon Neptune implementation of Gremlin and the implementation defined by Apache TinkerPop. They are detailed in [this page](<https://docs.aws.amazon.com/neptune/latest/userguide/access-graph-gremlin-differences.html> "target=\"_blank\""). Also, and contrary to JanusGraph for example, Neptune-Gremlin is schemaless.

&nbsp;

To perform data modeling for Neptune-Gremlin with Hackolade, you must first download the Neptune-Gremlin [plugin](DownloadadditionalDBtargetplugin.md). You can find more details on graph-specific controls in [this page](Graphshapes.md).

&nbsp;

Hackolade was specially adapted to support the data modeling of vertex labels and edge labels and their respective properties. The application closely follows the terminology of the database. To be clear, Hackolade is *not* a graph visualization tool, but a tool for **data modeling** of Neptune-Gremlin graph databases.

&nbsp;

The data model in the picture below results from the reverse-engineering of a [sample fraud graph](<https://aws.amazon.com/neptune/fraud-graphs-on-aws/> "target=\"_blank\"") imported in Neptune-Gremlin with a Sagemaker notebook. Two views of the data model are available:

&nbsp;

1\) a graph view, with familiar circular vertex labels:\
![Neptune-Gremlin workspace](<lib/Neptune-Gremlin workspace.png>)

&nbsp;

2\) an Entity-Relationship Diagram (ERD) view, with the advantage of displaying properties for both vertex labels and edge labels:\
![Neptune-Gremlin ERD](<lib/Neptune-Gremlin ERD.png>)

&nbsp;

Note: The Neptune-Gremlin implementation includes a couple of apparent limitations. As noted below, the possible data types are limited. Also, you can only define a single graph per instance. A possible workaround is suggested in [this article](<https://stackoverflow.com/a/64702748/9309385> "target=\"_blank\"").

&nbsp;

## Vertex labels

Vertex labels are a semantic representation of vertices in the graph. Vertex labels are used to represent the role of the vertex in the domain, making it possible to query the graph, to define constraints, and add indexes for properties. Labels can also be used to mark temporary states of a vertex.

&nbsp;

## Property keys

A vertex label usually has attributes, called "property keys" where the name (or key) is a string.\
![Neptune Gremlin vertex label properties](<lib/CosmosDB Gremlin vertex label properties.png>)

&nbsp;

## Property key data types

IDs must be strings. User-supplied IDs are supported provided they are unique Strings. Automatically generated IDs are UUIDs converted to a String. Neptune supports the base types of boolean, byte, date, double, float, integer, long and string. Arrays, lists, maps and meta-properties are not supported.

&nbsp;

It is possible to define the allowed cardinality of the values associated with the key on any given vertex. LIST is not supported.

- SINGLE: Allows at most one value per element for such key. In other words, the key-value mapping is unique for all elements in the graph. The property key birthDate is an example with SINGLE cardinality since each person has exactly one birth date.
- SET: Allows multiple values but no duplicate values per element for such key. In other words, the key is associated with a set of values. The property key name has SET cardinality if we want to capture all names of an individual (including nick name, maiden name, etc).

&nbsp;

The default cardinality setting is SINGLE.

&nbsp;

## Edge labels

Each edge connecting two vertices has a label which defines the semantics of the relationship. Edge labels are a semantic representation of relationships in the graph. Every relationship must have one and only type, and 2 nodes can be linked by several relationship types. Relationship types are used during complex traversals across the graph, when only certain kinds of paths from node to node are necessary for a specific query.

&nbsp;

In Neptune, edge labels are unidirectional, going from one node label to another node label. In Hackolade we also represent edge labels that are implicitly bi-directional. For example, IS_MARRIED_TO should not require 2 edge labels, but instead be considered bi-directional. Since Neptune does not support the bi-directional concept, marking a relationship as bi-directional in Hackolade is for documentation purposes only.

&nbsp;

![Neptune Gremlin edge label](<lib/Neo4j relationship type.png>)

&nbsp;

As Neptune-Gremlin is a type of graph database known as 'property graph', edge labels may have attributes, called property keys, just like vertex labels:\
![Neptune Gremlin edge label property keys](<lib/Neo4j relationship type property keys.png>)

&nbsp;

## Indexes

Neptune does not expose index configuration to the users. Indexes are maintained internally.

&nbsp;

## Forward-Engineering

Neptune-Gremlin does not provide an abstraction for schemas. Gremlin is a functional, data-flow language that enables users to succinctly express complex traversals on (or queries of) their application's property graph. In order to provide added-value in forward-engineering, Hackolade provides a graph example in Gremlin syntax for the data model. The script can be applied to the Neptune instance via the an [EC2 instance](<https://docs.aws.amazon.com/neptune/latest/userguide/get-started-access-graph.html> "target=\"_blank\"") and following instructions on [this page](ConnecttoaNeptuneinstance.md).

&nbsp;

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

&nbsp;

![Neptune-Gremlin script forward-engineering](<lib/Neptune-Gremlin script forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create graph vertices and edges by example.

&nbsp;

## Reverse-Engineering

The connection to a Neptune-Gremlin cluster instance is established using connection parameters further described in [this page](ConnecttoaNeptuneinstance.md).

&nbsp;

For more information on Neptune in general, please consult the [website](<https://aws.amazon.com/neptune/> "target=\"_blank\"").and [documentation](<https://docs.aws.amazon.com/neptune/latest/userguide/intro.html> "target=\"_blank\"").
