# Confluent Schema Registry

The [Confluent Schema Registry](<https://docs.confluent.io/platform/current/schema-registry/index.html> "target=\"\_blank\"") is a central repository with a RESTful interface for developers to define standard schemas and register applications to enable compatibility. Schema Registry is available as a software component of Confluent Platform or as a managed component of Confluent Cloud.&nbsp; Confluent Schema Validation provides a direct interface between the Kafka broker and Schema Registry to validate and enforce schemas programmatically. Schema Validation can be configured at the Kafka topic level.

&nbsp;

A key component of event streaming is to enable broad compatibility between applications connecting to Kafka. In a large organizations, trying to ensure data compatibility can be difficult and ultimately ineffective, even when using Schema Registry, because schemas are handled as “agreements” at the application level. Kafka cannot prevent unformatted data from being published. As a Kafka deployment scales and the number of connected systems and apps increases, so does the amount of risk and uncertainty regarding data quality.

&nbsp;

Hackolade supports Avro schema and JSON Schema maintenance in Confluent Schema Registry.&nbsp; Unlike many other Hackolade targets, this does not require a special plugin.&nbsp; It is done respectively through the Avro plugin or the JSON native target.&nbsp; Support for ProtoBuf format is not currently available, but foreseen in the near future.

&nbsp;

In effect, Hackolade provides a graphical interface for the design and maintenance of Avro and JSON schemas stored in Confluent Schema Registry.

![Image](<lib/Avro%20workspace.png>)

&nbsp;

For the details on how to define Avro schema definitions in Hackolade, you should consult this [Avro schema page](<Avroschema.md>).

&nbsp;

## Forward-Engineering

Schemas for Avro or JSON defined in Hackolade can be added to subjects in the Schema Registry through an Apply button appearing at the bottom of the Avro Schema tab.

&nbsp;

![Image](<lib/Confluent%20Schema%20Registry%20forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create a new version of the schema, if different from the latest one.

&nbsp;

## Reverse-Engineering

The reverse-engineering function lets you connect to the Confluent Schema Registry, either on-prem or in the Cloud. &nbsp;

&nbsp;

For more information, make sure to consult the Confluent Schema Registry [overview](<https://docs.confluent.io/platform/current/schema-registry/index.html> "target=\"\_blank\"").

&nbsp;

