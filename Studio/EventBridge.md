# EventBridge

Amazon EventBridge is a serverless event bus that makes it easy to connect applications together using data from applications, integrated Software-as-a-Service (SaaS) applications, and AWS services. &nbsp; EventBridge delivers a stream of real-time data from event sources, and routes that data to targets like AWS Lambda.&nbsp; EventBridge makes it easy to build event-driven applications because it takes care of event ingestion and delivery, security, authorization, and error handling for you.

&nbsp;

The Amazon EventBridge Schema Registry (EBSR) stores event structure - or schema - in a shared central location and maps those schemas to code for Java, Python, and Typescript so it’s easy to use events as objects in code. It is possible to connect to and interact with the schema registry from the AWS Management Console, or REST APIs.&nbsp; The EBSR stores a collection of easy-to-find event schemas and enables to download code bindings for those schemas in IDEs to represent the event as a strongly-typed object in code. Schema from the event bus can also be automatically added to the registry through the schema discovery feature.

&nbsp;

The EventBridge Schema Registry stores schemas in OpenAPI 3.0.0 format.&nbsp; OpenAPI is a [formal specification](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md> "target=\"\_blank\"") surrounded by a large ecosystem of tools, which includes everything from front-end user interfaces, low-level code libraries and commercial API management solutions.

&nbsp;

To perform the design of an EBSR schemas using OpenAPI 3 with Hackolade, you must first download the EventBridge [plugin](<DownloadadditionalDBtargetplugin.md>).&nbsp; This plugin is strictly compliant with version 3.0.0 of the OpenAPI specification and is based on the Hackolade [plugin for OpenAPI](<OpenAPI.md>) but independent of it so it can closely match the AWS requirements for the EBSR schema.

&nbsp;

Hackolade was specially adapted to support the design of EventBridge schemas, including all the necessary AWS metadata for the schema. &nbsp;

&nbsp;

The application closely follows the terminology of the specification.&nbsp; The visual tool puts the focus on what really matters in an API: the schema of the information being exchanged between systems.&nbsp; At the same time, it provides assistance to modelers and does not require perfect mastery of the OpenAPI 3 syntax.&nbsp; It generates validated files that are syntactically correct and compatible with the specification thereby greatly improving productivity and quality. The software also allows retrieval (reverse-engineering) of existing schemas in the Amazon EventBridge Schema Registry, as well publishing (forward-engineering) of new schemas (or new versions of a schema).

&nbsp;

The diagram below results from the reverse-engineering of AWS event aws.glue@GlueDataCatalogTableStateChange

![EventBridge workspace](<lib/EventBridge%20workspace.png>)

&nbsp;

&nbsp;

## Structure

The EBSR for any AWS account in a region is made of:

* an AWS event schema registry
* one or more custom schema registries

Each EBSR schema corresponds to a single Hackolade model file.&nbsp; While the structure of the event schema is maintained in the Components tab, the schema metadata is visible in the Schema properties tab.

&nbsp;

![EBSR lower tab](<lib/EBSR%20lower%20tab.png>)

&nbsp;

## Data Types

The OpenAPI specification used by EBSR describes primitives (or scalar) data types which can have an optional property modifier, *format*, plus a file primitive type.&nbsp; Complex types such as arrays and sub-objects, plus combinations thereof, are also allowed.

&nbsp;

![EventBridge Schema Registry data types](<lib/Swagger%20data%20types.png>)&nbsp; ![EventBridge Schema Registry data types - string](<lib/Swagger%20data%20types%20-%20string.png>)&nbsp; ![EventBridge Schema Registry data types - number](<lib/Swagger%20data%20types%20-%20number.png>)&nbsp; ![EventBridge Schema Registry data types - integer](<lib/Swagger%20data%20types%20-%20integer.png>) &nbsp;

&nbsp;

## Event metadata

A number of properties describing the registry and each schema can be reverse-engineered and maintained in the model:

&nbsp; ![EventBridge Schema Registry metadata](<lib/EBSR%20metadata.png>)

&nbsp;

## Components

[Component objects](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#components-object> "target=\"\_blank\"") hold a set of reusable objects that can be used across multiple endpoints in the same API: schema, parameter, request body, response, example, header, security scheme, link, or callback. All objects defined within the components object will have no effect on the API unless they are explicitly referenced from properties outside the components object by using a $ref reference in any path item.

&nbsp;

As you expose more resources and operations against your API, your API may repeat a lot of existing parameters or response descriptions in many different paths and operations.&nbsp; By creating reusable component objects, you avoid time-consuming rewriting as well as the risk of inconsistencies.

&nbsp;

Data types can be objects, but also primitives and arrays. This object is based on the [JSON Schema Specification Wright Draft 00 (a.k.a. Draft-05)](<http://json-schema.org/> "target=\"\_blank\"") and uses a predefined subset of it. On top of this subset, there are extensions provided by this specification to allow for more complete documentation.

&nbsp;

![EventBridge Schema Registry - Components](<lib/OpenAPI%20-%20Components.png>)

&nbsp;

Consult [this page](<Reusableobjectsdefinitions.md>) or more information on how to use definitions.&nbsp; For OpenAPI, you should limit yourself to Hackolade model definitions.

&nbsp;

## Forward-Engineering

The files describing the RESTful API in accordance with the [OpenAPI specification](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md> "target=\"\_blank\"") OAS are represented as JSON objects and conform to the JSON standards.&nbsp; Hackolade generates OpenAPI documentation in JSON format or YAML format.&nbsp; The schema exposes two types of fields. Fixed fields, which have a declared name, and patterned fields, which declare a regex pattern for the field name. Patterned fields can have multiple occurrences as long as each has a unique name.&nbsp; The OpenAPI representation of the API is made of a single file. However, parts of the definitions can be split into separate files, at the discretion of the user. This is applicable for $ref fields in the specification as follows from the [JSON Schema ](<http://json-schema.org/> "target=\"\_blank\"")definitions.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![EventBridge script forward-engineering](<lib/EventBridge%20script%20forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically create a new version of the schema, if different from the latest one.

## Reverse-Engineering

The connection is established using a connection using AWS IAM credentials:

![Event Bridge Schema Registry connection settings](<lib/Glue%20connection%20settings.png>)

&nbsp;

or through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\"") of the AWSCLI.

&nbsp;

The reverse-engineering function lets you take a schema from either the AWS even schema registry, or any custom schema registry file in JSON or YAML format and generate Hackolade components.&nbsp; Then, you may enrich the model with comments, generate standard Hackolade documentation, and make the schema evolve to apply to the EventBridge Schema Registry through the AWS Command Line Interface.

&nbsp;

