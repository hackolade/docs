# Elasticsearch

Elasticsearch is a RESTful search and analytics engine based on Apache Lucene.&nbsp; It provides a distributed, multi-tenant-capable full-text search engine with an HTTP web interface and schema-free JSON documents.&nbsp; Elasticsearch is developed alongside a data-collection and log-parsing engine called Logstash, and an analytics and visualisation platform called Kibana.&nbsp; The three products are designed for use as an integrated solution, referred to as the "Elastic Stack" (formerly the "ELK stack").

&nbsp;

To perform data modeling for Elasticsearch with Hackolade, you must first download the Elasticsearch [plugin](<DownloadadditionalDBtargetplugin.md>).&nbsp; **Important note:** with v7, a new typeless API has been introduced, and the old APIs that accept types have been deprecated (more details [here](<https://www.elastic.co/blog/moving-from-types-to-typeless-apis-in-elasticsearch-7-0> "target=\"\_blank\"").)&nbsp; As a result a different plugin is required, depending on whether you're running ES v2;0 thu 6.\!, or ES v7.0 and above.&nbsp; Please make sure to use the appropriate plugin.

&nbsp;

Hackolade was specially adapted to support the data modeling of Elasticsearch, including the large choice of data types and parent-child relationships.&nbsp; The application closely follows the terminology of the database.

&nbsp;

The data model in the picture below results from the reverse-engineering of a sample travel application imported in Elasticsearch.

&nbsp;

![Elasticsearch workspace](<lib/Elasticsearch workspace.png>)

## Indices

An index is similar to a database of keyspace.&nbsp; The term index should not be confused a database index.&nbsp; And the word indexing in Elasticsearch means inserting/updating the documents in an Elasticsearch index.&nbsp; An index is a flat collection of independent documents.  A single document should contain all of the information that is required to decide whether it matches a search request.

&nbsp;

## Types

A type is similar to a database table or collection.&nbsp; An index can have one or more types.&nbsp; Type is a logical separation of different kinds of data.&nbsp; You should avoid putting documents that have *totally* different structures into the same index in order to avoid sparsity.&nbsp; It is often better to put these documents into different indices, you could also consider giving fewer shards to these smaller indices since they will contain fewer documents overall.

&nbsp;

When mixing different types of documents into the same index (in ES versions prior to 6.0), it becomes necessary to specify a "type" attribute to differentiate the various documents stored in the index.&nbsp; In Hackolade, each Document Type is modeled as a separate entity or box, so its attributes can be defined separately.&nbsp; A specific attribute name must be identified to differentiate the different document types.&nbsp; The unique key and the document type field are common to all document types in the collection, and displayed at the top of each box in the ERD document:

&nbsp;

![Elasticsearch meta-fields](<lib/Elasticsearch meta-fields.png>)

&nbsp;

**Important:** Indices created in Elasticsearch 6.0.0 or later may only contain a single mapping type.&nbsp; Indices created in 5.x with multiple mapping types will continue to function as before in Elasticsearch 6.x. Mapping types have been completely removed in Elasticsearch 7.0. &nbsp; If you want to mix different document types within the same index, then you should specify a field (typically called "type") within each document to define the logical entity represented.&nbsp;

&nbsp;

&nbsp;

## IDs

IDs in Elasticsearch can be provided by the application or automatically generated by Elasticsearch.&nbsp; Even if the id represents an integer, it is stored as a string.

&nbsp;

## Attributes data types

Elasticsearch supports a number of different datatypes for the fields in a document, including core, complex, geo, and specialized datatypes.&nbsp; Hackolade has been configured to use all the Elasticsearch types, as described [here](<https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-types.html> "target=\"\_blank\"").

&nbsp;

![Elasticsearch data types](<lib/Elasticsearch data types.png>) ![Elasticsearch geo-point sub-types](<lib/Elasticsearch geo-point sub-types.png>)![Elasticsearch geo-shape subtypes](<lib/Elasticsearch geo-shape subtypes.png>)

&nbsp;

![Elasticsearch linestring structure](<lib/Elasticsearch linestring structure.png>)

&nbsp;

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the mapping for the document structure created with the application.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Elasticsearch forward-engineering mappings](<lib/Elasticsearch forward-engineering mappings.png>)

## Reverse-Engineering

You may define the connection parameters to your instance, typically on port 9200.&nbsp; Take a look at [this page](<ConnecttoanElasticsearchinstance.md>) for more information.

&nbsp;

The Hackolade reverse-engineering process of an Elasticsearch instance includes a query for a representative random sample of items, followed by a schema inference based on the sample.

&nbsp;

&nbsp;

For more information on Elasticsearch in general, please consult the [website](<https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started.html> "target=\"\_blank\"").

