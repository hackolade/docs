# MarkLogic

MarkLogic is a database designed from the ground up to make massive quantities of heterogeneous data easily accessible through search.&nbsp; MarkLogic is a leading 'multi-model' database, supporting traditional relational tables, XML and JSON documents, and RDF triples, all with ACID transactions capabilities.&nbsp; While Hackolade does not yet support the XML part, all other models are part of the solution.

&nbsp;

To perform data modeling for MarkLogic with Hackolade, you must first download the MarkLogic [plugin](<DownloadadditionalDBtargetplugin.md>). &nbsp;

&nbsp;

Hackolade was specially adapted to support the data modeling of MarkLogic, including the JSON definition of model descriptors, geospatial structures, triples and quads, and sub-collections.&nbsp; The application closely follows the terminology of the database. &nbsp;

&nbsp;

The data model in the picture below results from the reverse-engineering of a sample ordering&nbsp; application imported in MarkLogic.

![Image](<lib/MarkLogic%20workspace.png>)

&nbsp;

## Database

The design of MarkLogic allows a database to hold millions of collections without difficulty.

&nbsp;

## Collections / Directories

Collections are groups of documents that enable queries to efficiently target subsets of content within a MarkLogic database.&nbsp; Directories can also be used to organize documents.&nbsp; Collections do not require members to conform to any URI patterns.&nbsp; They are not hierarchical whereas directories are.&nbsp; Also, any document can belong to any collection, and any document can also belong to multiple collections.&nbsp; Properties can only be set for a directory, but not for collections.

&nbsp;

Collections are named using URIs.&nbsp; The URI needs to be unique within the set of collections.&nbsp; Collections can be protected or unprotected.

&nbsp;

## Attributes data types

MarkLogic, when storing JSON documents, supports standard JSON [data types](<https://www.tutorialspoint.com/documentdb/documentdb\_data\_types.htm> "target=\"\_blank\""), including arrays and objects.&nbsp; The Hackolade menu items, contextual menus, toolbar icon tooltips, and documentation are adapted to MarkLogic terminology and feature set. &nbsp;

&nbsp;

GeoSpatial structure templates:

Given the complex geospatial searches capability of MarkLogic, Hackolade facilitates the creation of geoJSON types (point, box, circle, polygon, linestring) with pre-defined templates:

![Image](<lib/MarkLogic%20geospatial.png>)

&nbsp;

Triple structure template:

Semantics enables the discovery of facts and relationships in data, and provides context for these facts.&nbsp; MarkLogic allows the natively store, search, and manage RDF triples, queried with SPARQL.&nbsp; Hackolade facilitates the creatio of triple structures with a predefined template:

![Image](<lib/MarkLogic%20triple.png>)

Quad structure template:

A quad is a representation of subject, predicate, and object, plus an additional resource for the context of the triple.

![Image](<lib/MarkLogic%20quad.png>)

&nbsp;

&nbsp;

## URIs

A JSON document is uniquely identified within a database with a Uniform Resource Identifier (URI). The URI for a document is analogous to the primary key in a relational table and may consist of a human-readable title or just a unique value.

## Indexing

MarkLogic makes use of multiple types of indexes to resolve queries.&nbsp; This is known as the Universal Index.&nbsp; The universal index indexes JSON properties in the loaded documents.&nbsp; By default, MarkLogic Server builds a set of indexes that is designed to yield the fast query performance in general usage scenarios.&nbsp; It does not have to be told what schema to expect &nbsp; More details can be found [here](<https://docs.marklogic.com/guide/concepts/indexing> "target=\"\_blank\""). &nbsp;

&nbsp;

Hackolade helps manage [range indexing](<https://docs.marklogic.com/guide/concepts/indexing#id\_51573> "target=\"\_blank\"").&nbsp; In some cases, documents can incorporate numeric, date or other typed information.&nbsp; Queries against these documents may include search conditions based on inequalities. Specifying [range indexes](<https://docs.marklogic.com/guide/admin/range\_index> "target=\"\_blank\"") for these elements and/or attributes will substantially accelerate the evaluation of these queries.

## Forward-Engineering

Forward-engineering of JSON Schema is available for use by [https://docs.marklogic.com/xdmp.jsonValidate](<https://docs.marklogic.com/xdmp.jsonValidate> "target=\"\_blank\"").

![Image](<lib/MarkLogic%20Forward-Engineering.png>)

## Reverse-Engineering

The connection is established using a connection string including (IP) address and port (typically 8000), and authentication using username/password if applicable.&nbsp; Details on how to connect Hackolade to a MarkLogic instance can be found on [this page](<ConnecttoaMarkLogicinstance.md>).

&nbsp;

The Hackolade process for reverse-engineering of MarkLogic databases includes the statistical sampling of documents followed by probabilistic inference of the JSON document schema.

&nbsp;

&nbsp;

For more information on MarkLogic in general, please consult the MarkLogic [website](<https://www.marklogic.com/> "target=\"\_blank\"").

