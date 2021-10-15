# Event Hubs Azure Schema Registry

The Azure Schema Registry is a feature of Event Hubs, providing a central system of record for schemas used in event-driven and messaging-centric applications. It provides the flexibility for producer and consumer applications to exchange data without having to manage and share the schema between them, and so they can evolve under different schedules. The Azure Schema Registry also provides a simple governance framework for reusable schemas and defines the relationship between schemas through a grouping construct (schema groups).

&nbsp;

In many event streaming and messaging use cases, the event or message payload contains structured data that's either being serialized or deserialized using a schema-driven format like Apache Avro. Both senders and receivers may want to validate the integrity of the data with a schema. For schema-driven formats, making the schema available to the message consumer is a prerequisite for the consumer to be able to deserialize the data.&nbsp; It can also help reduce the per-message overhead of type information and field names included with every data set as it's the case with tagged formats such as JSON. Having schemas stored alongside the events and inside the eventing infrastructure ensures that the metadata required for serialization/de-serialization is always in reach and schemas can't be misplaced.

&nbsp;

Hackolade supports Avro schema maintenance in the Azure Schema Registry for Event Hubs.&nbsp; Unlike many other Hackolade targets, this does not require a special plugin.&nbsp; It is done through the Avro plugin. &nbsp;

&nbsp;

In effect, Hackolade provides a graphical interface for the design and maintenance of Avro schemas stored in teh Azure Schema Registry for Event Hubs.

![Event Hubs Schema Registry workspace](<lib/Avro%20workspace.png>)

&nbsp;

For the details on how to define Avro schema definitions in Hackolade, you should consult this [Avro schema page](<Avroschema.md>).

&nbsp;

## Forward-Engineering

Schemas for Avro defined in Hackolade can be added to groups in the Schema Registry through an Apply button appearing at the bottom of the Avro Schema tab.

&nbsp;

![Image](<lib/Event%20Hub%20Schema%20Registry-forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create a new version of the schema, if different from the latest one.

&nbsp;

## Reverse-Engineering

The reverse-engineering function lets you connect to the Azure Schema Registry for Event Hubs. &nbsp;

&nbsp;

For more information, make sure to consult the Azure Schema Registry [overview](<https://docs.microsoft.com/en-us/azure/event-hubs/schema-registry-overview> "target=\"\_blank\"").

&nbsp;

