# MarkLogic

MarkLogic is a database designed from the ground up to make massive quantities of heterogeneous data easily accessible through search. MarkLogic is a leading 'multi-model' database, supporting traditional relational tables, XML and JSON documents, and RDF triples, all with ACID transactions capabilities. While Hackolade does not support the XML part, all other models are part of the solution.

&nbsp;

To perform data modeling for MarkLogic with Hackolade, you must first download the MarkLogic [plugin](DownloadadditionalDBtargetplugin.md).

&nbsp;

Hackolade was specially adapted to support the data modeling of MarkLogic, including the JSON definition of model descriptors, geospatial structures, triples and quads, and sub-collections. The application closely follows the terminology of the database.

&nbsp;

The data model in the picture below results from the reverse-engineering of a sample ordering application imported in MarkLogic.\
![MarkLogic workspace](<lib/MarkLogic workspace.png>)

&nbsp;

## Database

The design of MarkLogic allows a database to hold millions of collections without difficulty.

&nbsp;

## Collections / Directories

Collections are groups of documents that enable queries to efficiently target subsets of content within a MarkLogic database. Directories can also be used to organize documents. Collections do not require members to conform to any URI patterns. They are not hierarchical whereas directories are. Also, any document can belong to any collection, and any document can also belong to multiple collections. Properties can only be set for a directory, but not for collections.

&nbsp;

Collections are named using URIs. The URI needs to be unique within the set of collections. Collections can be protected or unprotected.

&nbsp;

## Attributes data types

MarkLogic, when storing JSON documents, supports standard JSON [data types](<https://www.tutorialspoint.com/documentdb/documentdb_data_types.htm> "target=\"_blank\""), including arrays and objects. The Hackolade menu items, contextual menus, toolbar icon tooltips, and documentation are adapted to MarkLogic terminology and feature set.

&nbsp;

GeoSpatial structure templates:\
Given the complex geospatial searches capability of MarkLogic, Hackolade facilitates the creation of geoJSON types (point, box, circle, polygon, linestring) with pre-defined templates:\
![MarkLogic geospatial](<lib/MarkLogic geospatial.png>)

&nbsp;

Triple structure template:\
Semantics enables the discovery of facts and relationships in data, and provides context for these facts. MarkLogic allows the natively store, search, and manage RDF triples, queried with SPARQL. Hackolade facilitates the creation of triple structures with a predefined template:\
![MarkLogic triple](<lib/MarkLogic triple.png>)\
Quad structure template:\
A quad is a representation of subject, predicate, and object, plus an additional resource for the context of the triple.\
![MarkLogic quad](<lib/MarkLogic quad.png>)

&nbsp;

## URIs

A JSON document is uniquely identified within a database with a Uniform Resource Identifier (URI). The URI for a document is analogous to the primary key in a relational table and may consist of a human-readable title or just a unique value.

&nbsp;

## Indexing

MarkLogic makes use of multiple types of indexes to resolve queries. This is known as the Universal Index. The universal index indexes JSON properties in the loaded documents. By default, MarkLogic Server builds a set of indexes that is designed to yield the fast query performance in general usage scenarios. It does not have to be told what schema to expect More details can be found [here](<https://docs.marklogic.com/guide/concepts/indexing> "target=\"_blank\"").

&nbsp;

Hackolade helps manage [range indexing](<https://docs.marklogic.com/guide/concepts/indexing#id_51573> "target=\"_blank\""). In some cases, documents can incorporate numeric, date or other typed information. Queries against these documents may include search conditions based on inequalities. Specifying [range indexes](<https://docs.marklogic.com/guide/admin/range_index> "target=\"_blank\"") for these elements and/or attributes will substantially accelerate the evaluation of these queries.

&nbsp;

## Forward-Engineering

Forward-engineering of JSON Schema is available for use by [https://docs.marklogic.com/xdmp.jsonValidate](<https://docs.marklogic.com/xdmp.jsonValidate> "target=\"_blank\"").

&nbsp;

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).\
![MarkLogic Forward-Engineering](<lib/MarkLogic Forward-Engineering.png>)

&nbsp;

## Reverse-Engineering

The connection is established using a connection string including (IP) address and port (typically 8000), and authentication using username/password if applicable. Details on how to connect Hackolade to a MarkLogic instance can be found on [this page](ConnecttoaMarkLogicinstance.md).

&nbsp;

The Hackolade process for reverse-engineering of MarkLogic databases includes the statistical sampling of documents followed by probabilistic inference of the JSON document schema.

&nbsp;

For more information on MarkLogic in general, please consult the MarkLogic [website](<https://www.marklogic.com/> "target=\"_blank\"").
