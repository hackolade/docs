# Export or forward-engineer

In the previous tutorial, we reviewed how to export or forward-engineer artifacts from your data model.&nbsp; By the end of this tutorial, you will master exporting or forward-engineering of schemas and order artifacts for your data models.

&nbsp;

Hackolade Studio is a data modeling tool with a purpose.&nbsp; We recognize that it is easier for humans to understand data structures via graphical Entity-Relationship Diagrams.&nbsp; The diagrams make it easy to design, maintain, and discuss with application stakeholders.&nbsp; But data models are not an end in themselves.&nbsp; Data models are useful so we can produce schemas, which we define as "contracts" between producers and consumers of data so they understand each other unambiguously during exchanges.&nbsp; Data models are also useful to feed business-facing data dictionaries so data citizens can understand the meaning and context of data when using it in self-service analytics, machine-learning, artificial intelligence, etc...&nbsp; In other words, a data model is an important mean to an end.

&nbsp;

![Metadata-as-Code](<lib/Metadata-as-Code.png>)

&nbsp;

As the data model is not an end and of itself, we need to use data models as a basis for exports through forward-engineering.

&nbsp;

Hackolade supports the forward-engineering of different types of artifacts:

* a [JSON or YAML sample document](<JSONDocument.md>);
* a [JSON Schema or YAML Schema](<JSONSchema.md>), to be saved on the file system (local or network) or to be applied to schema registries;
* an [Excel file](<Excelfile.md>) to perform bulk updates on a data model and import back into it;
* a [model-driven API file](<APIModel.md>) in Swagger or OpenAPI specification, generated from the underlying data model;
* a publication of the data model to data dictionaries, currently [Collibra](<CollibraDataDictionaryintegratio.md>).

&nbsp;

Additionally, and most importantly, we forward-engineer the respective [schema creation script](<Target-specific.md>) for each target we support: DDL for RDBMS, dbCreateCollection script for MongoDB, CQL for Cassandra/ScyllaDB, Cypher for Neo4j, etc., including constraints, indexing, and other necessary commands.

&nbsp;

For the JSON target, the menu looks as shown below.&nbsp; The menu is dynamically adapted in other targets to reflect the available capabilities of each plugin:

&nbsp;

![Tutorial - forward-engineering menu](<lib/Tutorial%20-%20forward-engineering%20menu.png>)

&nbsp;

&nbsp;

## Exporting file-based artifacts

For file-based exports, you are first prompted to select the entities you wish to forward-engineer, plus various options which differ depending on the type of export:

&nbsp;

![Tutorial - object selection dialog](<lib/Tutorial%20-%20object%20selection%20dialog.png>)

&nbsp;

Then you are prompted with the OS-specific dialog to save in the folder of your choice, for example in Windows:

![Image](<lib/Tutorial%20-%20forward-engineering%20save%20dialog.png>)

&nbsp;

&nbsp;

## Exporting to instances and systems

When applying scripts to database instances, applying schemas to registries, or publishing data models to data dictionaries, whether you forward-engineer to on-prem or cloud instances, you must provide connection parameters and security credentials.&nbsp; This is done via a Connections dialog such as:

&nbsp;

![Tutorial - Connections dialog](<lib/Tutorial%20-%20Connections%20dialog.png>)

&nbsp;

This confidential information stays on your local system with encrypted passwords.&nbsp; With this screen you can connect to previously saved connections, as well as add, edit, copy, import, export, and delete connections. &nbsp;

&nbsp;

The connection settings differ for each target, depending on the respective protocols and authentication mechanisms of each target technology.

&nbsp;

&nbsp;

All forward-engineering functions are accessible either from the GUI application, or from the [Command-Line Interface](<CommandLineInterface.md>), whether directly or running in [Docker containers](<https://github.com/hackolade/docker/tree/main/Studio> "target=\"\_blank\"").

&nbsp;

&nbsp;

In this tutorial, we reviewed how to export or forward-engineer schemas and order artifacts for your data models.&nbsp; In the next tutorial, we will cover how to generate documentation and diagrams for your data model.

