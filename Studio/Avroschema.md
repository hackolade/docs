# Avro schema

Apache Avro is a language-neutral data serialization system, developed by Doug Cutting, the father of Hadoop.&nbsp; Avro is a preferred tool to serialize data in Hadoop.&nbsp; It is also the best choice as file format for data streaming with Kafka.&nbsp; Avro serializes the data which has a built-in schema. Avro serializes the data into a compact binary format, which can be deserialized by any application.&nbsp; Avro schemas defined in JSON, facilitate implementation in the languages that already have JSON libraries.&nbsp; Avro creates a self-describing file named Avro Data File, in which it stores data along with its schema in the metadata section.

&nbsp;

Hackolade is a visual editor for Avro schema for non-programmers. To perform data modeling for Avro schema with Hackolade, you must first download the Avro [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  

&nbsp;

Hackolade was specially adapted to support the [schema design of Avro](<https://hackolade.com/nosqldb/avro-schema-editor.html> "target=\"\_blank\"") schema. The application closely follows the Avro terminology.

&nbsp;

![Avro workspace](<lib/Avro%20workspace.png>)

&nbsp;

## Avro Schema

An  Avro schema is created in JSON format and contains 4 attributes: **name**, **namespace**, **type**, and **fields. **

## Data Types

There are 8 primitive types (**null**, **boolean**, **int**, **long**, **float**, **double**, **bytes**, and **string**) and 6 complex types (**record**, **enum**, **array**, **map**, **union**, and **fixed**).

&nbsp;

![Avro data types](<lib/Avro%20data%20types.png>)

&nbsp;

Hackolade also supports [Avro logical types](<https://avro.apache.org/docs/1.8.1/spec.html#Logical%20Types> "target=\"\_blank\"").&nbsp;

&nbsp;

&nbsp;

### [Union types](<https://avro.apache.org/docs/current/spec.html#Unions> "target=\"\_blank\"")

As fields are always technically required in Avro, it is necessary to facilitate forward- and backward-compatibility by allowing fields to have a null type in addition to their natural data type.&nbsp; In Hackolade, when you create a new field, it is created with the required property selected.&nbsp; If you want to make a field logically optional, it must still be present physically, but with a default which must be null.&nbsp; To do this in Hackolade, you would set the data type to null, then de-select the required property, and make the default property = null (without quotes):

![Avro union types](<lib/Avro%20union%20types.png>)

&nbsp;

**Note:** the position of null in the hierarchy has an influence on the default.&nbsp; Default is based on the first data type listed.&nbsp; For "default": null to appear, the null data type must be first in the multiple data types, and the word null (without quotes) entered in the default property..

&nbsp;

But how you treat this in the application differs depending on whether the data type(s) is(are) scalar or complex:

\
**Scalar types**

Combining a null type with a scalar data type (**boolean**, **int**, **long**, **float**, **double**, **bytes**, and **string**) is very simple, you must click on the + sign to the right of the type property to become:

![Multi-type creation](<lib/Multi-type%20creation.png>)

which results in multiple blocks of properties appearing below in the Properties Pane:

![Multiple-type block](<lib/Multiple-type%20block.png>)

&nbsp;

### Complex types

If at least one data type is complex (**record**, **enum**, **array**, **map**, **union**, or **fixed**), then you must use a oneOf choice, for example:

![Avro oneOf choice](<lib/Avro%20oneOf%20choice.png>)

&nbsp;

## Forward-Engineering

Hackolade dynamically generates Avro schema for the structure created with the application.

&nbsp;

![Confluent Schema Registry forward-engineering](<lib/Confluent%20Schema%20Registry%20forward-engineering.png>)

&nbsp;

&nbsp;

This structure can be forward-engineered to a file with .avsc extention or copied/pasted to code.&nbsp; It can also be forward-engineered to a Azure, [Confluent or Pulsar Schema Registry](<ConfluentSchemaRegistry.md>) instance.

## Reverse-Engineering

Hackolade easily imports the schema from .avsc or .avro files to represent the corresponding Entity Relationship Diagram and schema structure.&nbsp; You may also import and convert from JSON Schema and documents.

