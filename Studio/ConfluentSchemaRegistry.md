# Confluent Schema Registry

The [Confluent Schema Registry](<https://docs.confluent.io/platform/current/schema-registry/index.html> "target=\"_blank\"") is a central repository with a RESTful interface for developers to define standard schemas and register applications to enable compatibility. Schema Registry is available as a software component of Confluent Platform or as a managed component of Confluent Cloud. Confluent Schema Validation provides a direct interface between the Kafka broker and Schema Registry to validate and enforce schemas programmatically. Schema Validation can be configured at the Kafka topic level.

&nbsp;

A key component of event streaming is to enable broad compatibility between applications connecting to Kafka. In a large organizations, trying to ensure data compatibility can be difficult and ultimately ineffective, so schemas should be handled as “contracts” between producers and consumers. Kafka cannot prevent unformatted data from being published. As a Kafka deployment scales and the number of connected systems and apps increases, so does the amount of risk and uncertainty regarding data quality.

&nbsp;

Hackolade supports Avro schema and JSON Schema maintenance in Confluent Schema Registry. Unlike many other Hackolade targets, this does not require a special plugin. It is done respectively through the Avro, Parquet or ProtoBuf plugins, or the JSON native target.

&nbsp;

In effect, Hackolade provides a graphical interface for the design and maintenance of Avro and JSON schemas stored in Confluent Schema Registry.\
![confluent Schema Registry workspace](<lib/Avro workspace.png>)

&nbsp;

For the details on how to define Avro schema definitions in Hackolade, you should consult this [Avro schema page](Avroschema.md).

&nbsp;

## Terminology

### Message

A data item that is made of a key (optional) and a value (the Kafka data payload.) Messages are not handled or managed by Hackolade. A schema type suffix, key or value, may be specified in the subject name.

&nbsp;

### Topic

A collection of of messages, where ordering is maintained for messages with the same key. Topics are not handled or managed by Hackolade, but can be referred to in some of the subject name strategies (see below.)

&nbsp;

### Schema

A description of how data should be structured. Each schema in Confluent Schema Registry is saved (registered) under a subject.

&nbsp;

### Subject

A named ordered history of schema versions. A subject can be seen as a scope in which a schema can evolve and is versioned.

&nbsp;

## Subject Name Strategy

Hackolade supports the 3 strategies offered by the Confluent Schema Registry:

&nbsp;

<table style="width:90%">
<colgroup><col style="width:21%"><col style="width:42%"><col style="width:37%"></colgroup>
<thead>
<tr>
<th>Strategy</th>
<th>Description</th>
<th>Format</th>
</tr>
</thead>
<tbody>
<tr>
<td>TopicNameStrategy</td>
<td>Derives subject name from topic name (default)</td>
<td>&lt;topic name&gt;-&lt;schema type suffix (optional)&gt;</td>
</tr>
<tr>
<td>RecordNameStrategy</td>
<td>Derives subject name from the record name, and provides a way to group logically related events that may have different data structures under a subject.</td>
<td>&lt;avro namespace&gt;-&lt;avro record name&gt;-&lt;schema type suffix (optional)&gt;</td>
</tr>
<tr>
<td>TopicRecordNameStrategy</td>
<td>Derives the subject name from topic and record name, as a way to group logically related events that may have different structures under a subject.</td>
<td>&lt;topic name&gt;-&lt;avro namespace&gt;-&lt;avro record name&gt;-&lt;schema type suffix (optional)&gt;</td>
</tr>
</tbody>
</table>

&nbsp;

The TopicNameStrategy is the default strategy, and implicitly requires that all messages in the same topic conform to the same schema to enforce the subject-topic constraints.

&nbsp;

The other 2 strategies can be used when a single topic can have records that use multiple schemas. This is useful when data represents a time-ordered sequence of events, with messages having different data structures. They use respectively the record name, and the topic plus the record name, to determine the subject to be used for schema lookups.

&nbsp;

Before the availability of these 2 new strategies, it was common to use Avro unions, with the caveats that it was difficult to independently evolve event types within the Avro union, plus the fact the resulting Avro union could become unwieldy: "By using either `RecordNameStrategy` or `TopicRecordNameStrategy`, you retain subject-schema constraints, eliminate the need for an Avro union, and gain the ability to evolve types independently. However, you lose subject-topic constraints, as now there is no constraint on the event types that can be stored in the topic, which means the set of event types in the topic can grow unbounded."

&nbsp;

You should look at [this table](<https://docs.confluent.io/platform/current/schema-registry/serdes-develop/index.html#how-the-naming-strategies-work> "target=\"_blank\"") comparing how strategies work, as part of [this page](<https://docs.confluent.io/platform/current/schema-registry/serdes-develop/index.html#subject-name-strategy> "target=\"_blank\"").

&nbsp;

## Avro unions with schema references

Confluent Platform (versions 5.5.0 and later) provides full support for the notion of *schema references*, the ability of a schema to refer to other schemas

&nbsp;

Introduced with Confluent 5.5, a schema reference is comprised of a reference name, and a subject/version for that reference. The Avro union is just a list of event types that could be sent to a topic. And each event type can evolve independently, as they would have with either `RecordNameStrategy` or `TopicRecordNameStrategy`, except that you can now use `TopicNameStrategy` and retain subject-topic constraints,

&nbsp;

You will find more details in [this blog](<https://www.confluent.io/blog/multiple-event-types-in-the-same-kafka-topic/> "target=\"_blank\"") and this [documentation page](<https://docs.confluent.io/platform/current/schema-registry/fundamentals/serdes-develop/serdes-avro.html#schema-references-in-avro> "target=\"_blank\""). Hackolade supports Avro unions with schema references.

&nbsp;

A schema reference consists of the following:

- A name for the reference. (For Avro, the reference name is the fully qualified schema name, for JSON Schema it is a URL, and for Protobuf, it is the name of another Protobuf file.)
- A subject, representing the subject under which the referenced schema is registered.
- A version, representing the exact version of the schema under the registered subject.

&nbsp;

In Hackolade Studio, you can create a reference to another Avro record in the same model through a model reference. Let's say you have 2 records in your Avro model: customer and address. Now you'd like to reference the address record from the customer record. Choose Append field > Reference > Model Definition > Open definitions...\
![Confluent Schema Rgistry - add reference](<lib/Confluent Schema Rgistry - add reference.png>)

&nbsp;

Then choose the address record in the dialog:\
![Confluent Schema Rgistry - pick definition](<lib/Confluent Schema Rgistry - pick definition.png>)\
This will result in a reference inside the customer record:\
![Confluent Schema Rgistry - union schema](<lib/Confluent Schema Rgistry - union schema.png>)

&nbsp;

This will result in a references section in the customer schema for the Confluent Schema Registry:\
![Confluent Schema Rgistry - union schema outpu](<lib/Confluent Schema Rgistry - union schema outpu.png>)

&nbsp;

## Forward-Engineering

Schemas for Avro or JSON defined in Hackolade can be added to subjects in the Schema Registry through an Apply button appearing at the bottom of the Avro Schema tab.

&nbsp;

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

&nbsp;

![Confluent Schema Registry forward-engineering](<lib/Confluent Schema Registry forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create a new version of the schema, if different from the latest one.

&nbsp;

## Reverse-Engineering

The reverse-engineering function lets you connect to the Confluent Schema Registry, either on-prem or in the Cloud.

&nbsp;

For more information, make sure to consult the Confluent Schema Registry [overview](<https://docs.confluent.io/platform/current/schema-registry/index.html> "target=\"_blank\"").

&nbsp;

## Configure CORS to access Confluent Schema Registries from Hackolade Studio in the browser

When interacting (forward- or reverse-engineering) with Confluent Schema Registries (CSR) from [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"_blank\""), a specific [Cross Origin Resource Sharing](<https://itnext.io/understanding-cors-4157bf640e11> "target=\"_blank\"") (CORS) configuration must be set up on the CSR instance(s).

&nbsp;

The CORS configuration Allow-Access-Origin header must allow for the '''studio.hackolade.com''' origin to interact with the instance, otherwise the browser blocks any interaction of Hackolade Studio in the browser with the schema registry.

&nbsp;

### Confluent Cloud

The Confluent Cloud platform doesn't allows custom configuration of the CORS Access-Control-Allow-Origin header when accessing the schema registry on their "confluent.cloud" domain.

&nbsp;

To make it accept transactions from [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"_blank\""), you (or your IT department) must first set up a CORS [Reverse Proxy](<https://en.wikipedia.org/wiki/Reverse_proxy> "target=\"_blank\"") that serves the Confluent-provided schema registry while overriding response headers when the response is sent back to studio.hackolade.com.

&nbsp;

We give you an example of how to deploy such a reverse proxy and use this endpoint as the host URL to execute forward- or reverse-engineering operations from [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"_blank\"").

&nbsp;

For example with an Nginx reverse proxy served on https://cors-proxy-for-confluent-cloud.mydomain.com, after you picked up the public URL for your Confluent Schema registry (something like https://\<schema registry instance>.confluent.cloud):

&nbsp;

*server {*\
*listen 443;*

&nbsp;

```text
    server_name  confluent-proxy;
    location  / {
        add_header Access-Control-Allow-Origin 'https://studio.hackolade.com' always;
        add_header Access-Control-Allow-Headers '*';
        add_header Access-Control-Allow-Methods '*';
        add_header Access-Control-Allow-Credentials 'true';
        if ($request_method = 'OPTIONS') {
            return 204;
        }
        proxy_pass  https://<schema registry instance>.confluent.cloud;
    }
}
```

&nbsp;

### On premises custom instance

Please refer to the Confluent Schema Registry [configuration reference](<https://docs.confluent.io/platform/current/schema-registry/installation/config.html#access-control-allow-origin> "target=\"_blank\"") to properly configure your custom instance. You need to add (at least) the property "access.control.allow.origin" to your "schema-registry.properties" file. It is often useful too to set "access.control.allow.methods" to "\*".

&nbsp;

*access.control.allow.origin=https://studio.hackolade.com*\
*access.control.allow.methods=\**
