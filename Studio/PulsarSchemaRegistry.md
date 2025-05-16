# Pulsar Schema Registry

The [Pulsar Schema Registry](<https://pulsar.apache.org/docs/en/concepts-schema-registry/> "target=\"\_blank\"") is a central repository to enable message producers and consumers on Pulsar topics to coordinate on the structure of topics for your message bus. The structure of the data, or its *schema*, may either be specified and uploaded through a [REST interface](<http://pulsar.apache.org/admin-rest-api/?version=2.4.2#tag/schemas>) or by the message producer itself. Each piece of data that is passed through the system is in turn stamped with the name and version of the schema it represents. With schemas for Avro and JSON, every single piece of data traveling through the system is completely discoverable, enabling to build systems that can easily adapt as the data changes.

&nbsp;

Furthermore, the schema registry keeps track of data compatibility between versions of the schema. As new schemas are uploaded the registry ensures that new schema versions are able to be read by old consumers. This ensures that Producers are not able to break Consumers. 

&nbsp;

Hackolade supports Avro schema and JSON Schema maintenance in the Pulsar Schema Registry.&nbsp; Unlike many other Hackolade targets, this does not require a special plugin.&nbsp; It is done respectively through the Avro, Parquet or ProtoBuf plugins, or the JSON native target.

&nbsp;

In effect, Hackolade provides a graphical interface for the design and maintenance of Avro and JSON schemas stored in Pulsar Schema Registry.

![Pulsar workspace](<lib/Avro workspace.png>)

&nbsp;

For the details on how to define Avro schema definitions in Hackolade, you should consult this [Avro schema page](<Avroschema.md>).

&nbsp;

## Forward-Engineering

Schemas for Avro or JSON defined in Hackolade can be added to subjects in the Schema Registry through an Apply button appearing at the bottom of the Avro Schema tab.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Pulsar Schema Registry forward-engineering](<lib/Pulsar Schema Registry forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create a new version of the schema, if different from the latest one.

&nbsp;

## Reverse-Engineering

The reverse-engineering function lets you connect to the Pulsar Schema Registry, either on-prem or in the Cloud. &nbsp;

&nbsp;

For more information, make sure to consult the Pulsar Schema Registry [documentation](<https://pulsar.apache.org/docs/en/schema-get-started/> "target=\"\_blank\"").

&nbsp;

