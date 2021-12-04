# Confluent Schema Registry

The [Confluent Schema Registry](<https://docs.confluent.io/platform/current/schema-registry/index.html> "target=\"\_blank\"") is a central repository with a RESTful interface for developers to define standard schemas and register applications to enable compatibility. Schema Registry is available as a software component of Confluent Platform or as a managed component of Confluent Cloud.&nbsp; Confluent Schema Validation provides a direct interface between the Kafka broker and Schema Registry to validate and enforce schemas programmatically. Schema Validation can be configured at the Kafka topic level.

&nbsp;

A key component of event streaming is to enable broad compatibility between applications connecting to Kafka. In a large organizations, trying to ensure data compatibility can be difficult and ultimately ineffective, even when using Schema Registry, because schemas are handled as “agreements” at the application level. Kafka cannot prevent unformatted data from being published. As a Kafka deployment scales and the number of connected systems and apps increases, so does the amount of risk and uncertainty regarding data quality.

&nbsp;

Hackolade supports Avro schema and JSON Schema maintenance in Confluent Schema Registry.&nbsp; Unlike many other Hackolade targets, this does not require a special plugin.&nbsp; It is done respectively through the Avro plugin or the JSON native target.&nbsp; Support for ProtoBuf format is not currently available, but foreseen in the near future.

&nbsp;

In effect, Hackolade provides a graphical interface for the design and maintenance of Avro and JSON schemas stored in Confluent Schema Registry.

![confluent Schema Registry workspace](<lib/Avro%20workspace.png>)

&nbsp;

For the details on how to define Avro schema definitions in Hackolade, you should consult this [Avro schema page](<Avroschema.md>).

&nbsp;

## Terminology

#### Message

A data item that is made of a key (optional) and a value.&nbsp; Messages are not handled or managed by Hackolade.

#### Topic

A collection of of messages, where ordering is maintained for messages with the same key.&nbsp; Topics are not handled or managed by hackolade, but can be referred to in some circumstances.

#### Schema

A description of how data should be structured.

#### Subject

A named ordered history of schema versions.

&nbsp;

## Subject Name Strategy

Hackolade supports the 3 strategies offered by the Confluent Schema Registry:&nbsp;

| **Strategy** | **Description** |
| --- | --- |
| TopicNameStrategy | Derives subject name from topic name (default) |
| RecordNameStrategy | Derives subject name from the record name, and provides a way to group logically related events that may have different data structures under a subject. |
| TopicRecordNameStrategy | Derives the subject name from topic and record name, as a way to group logically related events that may have different structures under a subject. |


&nbsp;

The TopicNameStrategy is the default strategy, and implicitly requires that all messages in the same topic conform to the same schema to enforce the subject-topic constraints. &nbsp;

&nbsp;

The other 2 strategies can be used when a single topic can have records that use multiple schemas.&nbsp; This is useful when data represents a time-ordered sequence of events, with messages having different data structures.&nbsp; They use respectively the record name, and the topic plus the record name, to determine the subject to be used for schema lookups. &nbsp;

&nbsp;

Before the availability of these 2 new strategies, it was common to use Avro unions, with the caveats that it was difficult to independently evolve event types within the Avro union, plus the fact the resulting Avro union could become unwieldy: "By using either RecordNameStrategy or TopicRecordNameStrategy, you retain subject-schema constraints, eliminate the need for an Avro union, and gain the ability to evolve types independently. However, you lose subject-topic constraints, as now there is no constraint on the event types that can be stored in the topic, which means the set of event types in the topic can grow unbounded."

&nbsp;

You should look at [this table](<https://docs.confluent.io/platform/current/schema-registry/serdes-develop/index.html#how-the-naming-strategies-work> "target=\"\_blank\"") comparing how strategies work, as part of [this page](<https://docs.confluent.io/platform/current/schema-registry/serdes-develop/index.html#subject-name-strategy> "target=\"\_blank\"").

&nbsp;

## Avro unions with schema references

Introduced with Confluent 5.5, a schema reference is comprised of a reference name, and a subject/version for that reference.&nbsp; The Avro union is just a list of event types that could be sent to a topic.&nbsp; And each event type can evolve independently, as they would have with either RecordNameStrategy or TopicRecordNameStrategy, except that you can now use TopicNameStrategy and retain subject-topic constraints,&nbsp;

&nbsp;

You will find more details in [this blog](<https://www.confluent.io/blog/multiple-event-types-in-the-same-kafka-topic/> "target=\"\_blank\"").&nbsp; Hackolade does not yet support Avro unions with schema references, but design is under way.

&nbsp;

## Forward-Engineering

Schemas for Avro or JSON defined in Hackolade can be added to subjects in the Schema Registry through an Apply button appearing at the bottom of the Avro Schema tab.

&nbsp;

![Confluent Schema Registry forward-engineering](<lib/Confluent%20Schema%20Registry%20forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create a new version of the schema, if different from the latest one.

&nbsp;

## Reverse-Engineering

The reverse-engineering function lets you connect to the Confluent Schema Registry, either on-prem or in the Cloud. &nbsp;

&nbsp;

For more information, make sure to consult the Confluent Schema Registry [overview](<https://docs.confluent.io/platform/current/schema-registry/index.html> "target=\"\_blank\"").

&nbsp;

