---
description: Hackolade Studio generates the Protobuf schema of your model, to export to files or apply to a schema registry.
seoTitle: Generate Protobuf schemas
image: lib/Protobuf schema forward-engineering.png
---
# Protobuf schema

Hackolade dynamically generates Protobuf schema for the structure created with the application.

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

![Protobuf schema forward-engineering](<lib/Protobuf schema forward-engineering.png>)

This structure can be forward-engineered to a file with .proto extension or copied/pasted to code. It can also be forward-engineered to a [Confluent or Pulsar Schema Registry](ConfluentSchemaRegistry.md) instance.
