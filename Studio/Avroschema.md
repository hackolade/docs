---
description: "Design Apache Avro schemas visually in Hackolade Studio: records, unions, complex types, annotations and namespaces, with forward- and reverse-engineering."
seoTitle: Avro schema data modeling with Hackolade Studio
image: lib/Avro workspace.png
---
# Avro schema

Apache Avro is a language-neutral data serialization system, developed by Doug Cutting, the father of Hadoop. Avro is a preferred tool to serialize data in Hadoop. It is also the best choice as file format for data streaming with Kafka. Avro serializes the data which has a built-in schema. Avro serializes the data into a compact binary format, which can be deserialized by any application. Avro schemas defined in JSON, facilitate implementation in the languages that already have JSON libraries. Avro creates a self-describing file named Avro Data File, in which it stores data along with its schema in the metadata section.

Hackolade is a visual editor for **Avro schema** for non-programmers. To perform data modeling for Avro schema with Hackolade, you must first download the Avro [plugin](DownloadadditionalDBtargetplugin.md).

Hackolade was specially adapted to support the [schema design of Avro](<https://hackolade.com/nosqldb/avro-schema-editor.html> "target=\"_blank\"") schema. The application closely follows the Avro terminology.

![Avro workspace](<lib/Avro workspace.png>)

## Avro Schema

An Avro schema is created in JSON format and contains 4 attributes: **name**, **namespace**, **type**, and **fields.**

## Data Types

There are 8 primitive types (**null**, **boolean**, **int**, **long**, **float**, **double**, **bytes**, and **string**) and 6 complex types (**record**, **enum**, **array**, **map**, **union**, and **fixed**).

![Avro data types](<lib/Avro data types.png>)

Hackolade also supports [Avro logical types](<https://avro.apache.org/docs/1.11.0/spec.html#Logical+Types> "target=\"_blank\"").

> [!WARNING]
> The data types date/time/timestamp can be a bit of a trap. The label would make the reader think that the content is similar to what is generally understood in other technologies, like references to:

- date: a three-part value (year, month, and day) designating a point in time using the Gregorian calendar, which is assumed to have been in effect from the year 1 A.D.
- time: a three-part value (hour, minute, and second) designating a time of day using a 24-hour clock.
- timestamp: a six-part or seven-part value (year, month, day, hour, minute, second, and optional fractional second) with an optional time zone specification, that represents a date and time.

But careful reading of the Avro specification reveals that they are **stored** in a completely different manner:

- a date logical type annotates an Avro int, where the int stores the number of days from the unix epoch, 1 January 1970 (ISO calendar).
- a time-millis logical type annotates an Avro int, where the int stores the number of milliseconds after midnight, 00:00:00.000.\
  \- a time-micros logical type annotates an Avro long, where the long stores the number of microseconds after midnight, 00:00:00.000000.
- a timestamp-millis logical type annotates an Avro long, where the long stores the number of milliseconds from the unix epoch, 1 January 1970 00:00:00.000 UTC.
- a timestamp-millis logical type annotates an Avro long, where the long stores the number of milliseconds from the unix epoch, 1 January 1970 00:00:00.000 UTC.
- a timestamp-micros logical type annotates an Avro long, where the long stores the number of microseconds from the unix epoch, 1 January 1970 00:00:00.000000 UTC.
- a local-timestamp-millis logical type annotates an Avro long, where the long stores the number of milliseconds, from 1 January 1970 00:00:00.000.
- local-timestamp-micros logical type annotates an Avro long, where the long stores the number of microseconds, from 1 January 1970 00:00:00.000000.

When reverse-engineering from other technology sources, Hackolade Studio maps to the above logical types, but if you transfer data, you must ensure to convert the data accordingly, if your connector does not do it automatically.

**Enum warning:** you may want to read this [excellent article](<https://medium.com/expedia-group-tech/safety-considerations-when-using-enums-in-avro-schemas-82e18baaa081> "target=\"_blank\"").

### Union types

In Avro, [union types](<https://avro.apache.org/docs/++version++/specification/#unions> "target=\"_blank\"") are used to represent alternative data types for a field. They play a key role in [schema evolution and compatibility](<https://docs.confluent.io/platform/current/schema-registry/fundamentals/schema-evolution.html> "target=\"_blank\""), and in modeling logical choices such as *oneOf*. More details can be found in this [How-To guide](UniontypesinAvro.md).

As fields are always technically required in Avro, it is necessary to facilitate forward- and backward-compatibility by allowing fields to have a null type in addition to their natural data type. In Hackolade Studio, when you create a new field, it is created with the required property selected. If you want to make a field logically optional, it must still be present physically, but with a default which must be null. To do this in Hackolade Studio, you would set the data type to null, then deselect the required property, and make the default property = null (without quotes):\
![Avro union types](<lib/Avro union types.png>)

> [!NOTE]
> The position of null in the hierarchy has an influence on the default. Default is based on the first data type listed. For "default": null to appear, the null data type must be first in the multiple data types, and the word null (without quotes) entered in the default property..

**Example:** a sample model can be found [here](<https://hackolade.com/samplemodels.html#avro> "target=\"_blank\"").

But how you treat this in the application differs depending on whether the data type(s) is(are) scalar or complex:\
**Scalar types**\
Combining a null type with a scalar data type (**boolean**, **int**, **long**, **float**, **double**, **bytes**, and **string**) is very simple, you must click on the + sign to the right of the type property to become:\
![Multi-type creation](<lib/Multi-type creation.png>)\
which results in multiple blocks of properties appearing below in the Properties Pane:\
![Multiple-type block](<lib/Multiple-type block.png>)

### Complex types

If at least one data type is complex (**record**, **enum**, **array**, **map**, **union**, or **fixed**), then you must use a oneOf choice, for example:\
![Avro oneOf choice](<lib/Avro oneOf choice.png>)

## Annotations

The Avro schema specifications documents standard keywords. You may add your own annotations for your use cases. This is done by leveraging the Hackolade Studio [custom properties](Userdefinedcustomproperties.md)., making sure to mark the property with the flag `includeInScript.`

This can be done at the record level or field level. For example:

```json
{
    "propertyName": "Tags",
 "propertyKeyword": "tags",
 "propertyTooltip": "Select from list of options",
 "propertyType": "multipleCheckboxSelect",
 "options": [
  "PII",
  "GDPR",
  "Sensitive",
  "Protected"
 ],
 "includeInScript": true
},
```

## Namespace references

This feature is barely officially documented if at all. It is well described in [this article](<https://deeptimittalblogger.medium.com/defining-reusable-schemas-in-avro-991f2e21d1ca> "target=\"_blank\"") with good examples in [this repo](<https://github.com/timtebeek/register-avro-schemas#define-avro-schemas> "target=\"_blank\""). It allows you to reuse records inside other records by creating references instead of importing or copying the structure. This of course allows for easier maintenance of repeated structures and facilitates quality and governance, while allowing independent evolution of record schemas.

Starting from a blank page, this is how to build a namespace reference. The Price record must have been created first. Then as you build the Order record, append a reference model definition:

![Avro namespace reference creation](<lib/Avro namespace reference creation.png>)

Choose the Price record:

![Avro namespace reference pick record](<lib/Avro namespace reference pick record.png>)

And voilà…

![Avro namespace reference model](<lib/Avro namespace reference model.png>)

The forward-engineered script shows as follows:\
![Avro namespace reference avsc script](<lib/Avro namespace reference avsc script.png>)

When reverse-engineering Avro files containing namespace references, the sequence in which they are ingested is important. In order to insert definitions before insert references to such definitions, we have implemented [topological sorting](<https://en.wikipedia.org/wiki/Topological_sorting> "target=\"_blank\"").

## Forward-Engineering

Hackolade dynamically generates Avro schema for the structure created with the application.

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

![Confluent Schema Registry forward-engineering](<lib/Confluent Schema Registry forward-engineering.png>)

This structure can be forward-engineered to a file with .avsc extension or copied/pasted to code. It can also be forward-engineered to a Azure, [Confluent or Pulsar Schema Registry](ConfluentSchemaRegistry.md) instance.

## Reverse-Engineering

Hackolade easily imports the schema from .avsc or .avro files to represent the corresponding Entity Relationship Diagram and schema structure. You may also import and convert from JSON Schema and documents.

## Cloud Object Storage

In the context of large-scale distributed systems like data lakes, data is often stored in object storage solutions like Amazon S3, Azure ADLS, or Google Cloud Storage. Avro can be used to serialize the data into binary format then be stored in the object storage system as a file, making it easily accessible for processing and analysis.

With Hackolade Studio, you can reverse-engineer Avro files located on:

- Amazon S3
- Azure Blob Storage
- Azure Data Lake Storage (ADLS) Gen 1 and Gen 2
- Google Cloud Storage

## Schema Registries

A key component of event streaming is to enable broad compatibility between applications connecting to Kafka. In a large organizations, trying to ensure data compatibility can be difficult and ultimately ineffective, so schemas should be handled as “contracts” between producers and consumers.

The main benefit of using a Schema Registry is that it provides a centralized way to manage and version Avro schemas, which can be critical for maintaining data compatibility and ensuring data quality in a Kafka ecosystem.

Hackolade Studio supports Avro schema maintenance in:

- [Confluent Schema Registry](ConfluentSchemaRegistry.md)
- [Azure EventHubs Schema Registry](EventHubsAzureSchemaRegistry.md)
- [Pulsar Schema Registry](PulsarSchemaRegistry.md)

Schemas can be published to the registry via forward-engineering, or reverse-engineered from these schema registries.
