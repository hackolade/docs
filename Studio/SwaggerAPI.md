# Swagger API

The goal of Swagger is to define a standard, language-agnostic interface to REST APIs which allows both humans and computers to discover and understand the capabilities of the service without access to source code, documentation, or through network traffic inspection.&nbsp; When properly defined via Swagger, a consumer can understand and interact with the remote service with a minimal amount of implementation logic.&nbsp; Similar to what interfaces have done for lower-level programming, Swagger removes the guesswork in calling the service.

&nbsp;

Technically speaking - Swagger is a [formal specification](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md> "target=\"\_blank\"") surrounded by a large ecosystem of tools, which includes everything from front-end user interfaces, low-level code libraries and commercial API management solutions.

&nbsp;

To perform model-first design of a REST API using Swagger with Hackolade, you must first download the Swagger [plugin](<DownloadadditionalDBtargetplugin.md>).&nbsp; This plugin is strictly compliant with version 2.0 of the OpenAPI specification.&nbsp; Another plugin is required to support the OpenAPI 3.0 specification.

&nbsp;

Creating APIs is not easy\! And writing Swagger documentation in a design-first approach can be tedious at best, generally error-prone and frustrating...&nbsp; Hackolade takes a **visual schema-centric** approach so you can focus on the content of requests and responses. The application also assists with all the metadata to produce validated Swagger files and test the transactions.&nbsp; You can also reverse-engineer existing Swagger files in JSON or YAML to produce a graphical representation of your APIs.

Hackolade was specially adapted to support the API design of Swagger, including all the necessary metadata for the API, the requests and responses.&nbsp; The application closely follows the terminology of the specification.&nbsp; The visual tool puts the focus on what really matters in an API: the schema of the information being exchanged between systems.&nbsp; At the same time, it provides assistance to modelers and does not require perfect mastery of the Swagger syntax.&nbsp; It generates validated files that are syntactically correct and compatible with the specification thereby greatly improving productivity and quality. &nbsp; A step-by-step tutorial is available in a [YouTube video](<https://hackolade.com/videos.html#swagger> "target=\"\_blank\"").

&nbsp;

The diagram below results from the reverse-engineering of the [Pet Store](<https://mermade.org.uk/examples/swagger.json> "target=\"\_blank\"") sample API.

![Swagger - Workspace](<lib/Swagger%20-%20Workspace.png>)

&nbsp;

## Data Types

The Swagger specification describes primitives (or scalar) data types which can have an optional property modifier, *format*, plus a file primitive type.&nbsp; Complex types such as arrays and sub-objects, plus combinations thereof, are also allowed.

&nbsp;

![Swagger data types](<lib/Swagger%20data%20types.png>)&nbsp; ![Swagger data types - string](<lib/Swagger%20data%20types%20-%20string.png>)&nbsp; ![Swagger data types - number](<lib/Swagger%20data%20types%20-%20number.png>)&nbsp; ![Swagger data types - integer](<lib/Swagger%20data%20types%20-%20integer.png>) &nbsp;

&nbsp;

&nbsp;

## API metadata

The info object, as well as the host, basePath, schemes, consumes, produces, the securityDefinitions object, the security object, the tags object, and externalDocs object are fixed fields treated as metadata and maintained at model-level in Hackolade.

&nbsp;![Swagger - Info object 1](<lib/Swagger%20-%20Info%20object%201.png>)&nbsp; ![Swagger - Info object 2](<lib/Swagger%20-%20Info%20object%202.png>)&nbsp; ![Swagger - Info object 3](<lib/Swagger%20-%20Info%20object%203.png>)

&nbsp;

## Definitions

An object of [schema objects](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#schema-object> "target=\"\_blank\"") with definitions of inputs and outputs to be produced and consumed by operations.&nbsp; Data types can be objects, but also primitives and arrays. This object is based on the [JSON Schema Specification Draft 4](<http://json-schema.org/> "target=\"\_blank\"") and uses a predefined subset of it. On top of this subset, there are extensions provided by this specification to allow for more complete documentation.

&nbsp;

![Swagger - Definitions](<lib/Swagger%20-%20Definitions.png>)

&nbsp;

Consult [this page](<Reusableobjectsdefinitions.md>) or more information on how to use definitions.&nbsp; For Swagger, you should limit yourself to Hackolade model definitions.

## Resource

The resource path object is a container representing the relative path to an individual endpoint.&nbsp; The field name must start with a slash ("/").&nbsp; The path is appended to the basePath in order to construct the full URL.&nbsp; Path templating (usage of curly braces ("{}") to mark a section of a URL path as replaceable using path parameters) is allowed.

&nbsp;

Each resource contains one or more "[path item objects](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#path-item-object> "target=\"\_blank\"")" made of a request and one or more responses:

![Swagger - Resource container](<lib/Swagger%20-%20Resource%20container.png>)

&nbsp;

You may create a new resource via right-click anywhere in the ERD view and choosing the contextual menu option:

![Swagger - Add resource contextual menu](<lib/Swagger%20-%20Add%20resource%20contextual%20menu.png>)

&nbsp;

or via the menu:

![Swagger - Add resource action menu](<lib/Swagger%20-%20Add%20resource%20action%20menu.png>)

&nbsp;

or the toolbar:

![Swagger - Add resource toolbar button](<lib/Swagger%20-%20Add%20resource%20toolbar%20button.png>)

&nbsp;

&nbsp;

## Requests

A request is an object with a type, associated data, relationships to other resources, and a set of methods that operate on it.&nbsp; Only a few standard methods are defined for the resource (corresponding to the standard HTTP GET, POST, PUT and DELETE methods.)

&nbsp;

The [Parameter Object](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#parameter-object> "target=\"\_blank\"") describes a single operation parameter defined by a combination of a name and location.&nbsp; Hackolade provides a handy template of parameter types allowing the description of the payload either by adding adding individual fields or by referencing an existing definition.

&nbsp;

![Swagger - Request parameter 1](<lib/Swagger%20-%20Request%20parameter%201.png>) &nbsp; ![Swagger - Request parameter 2](<lib/Swagger%20-%20Request%20parameter%202.png>)

&nbsp;

To create a request within a resource container, you may:

\- right-click inside the container area of the ERD pane, and choose the contextual menu option:

![Swagger - Add request contextual menu](<lib/Swagger%20-%20Add%20request%20contextual%20menu.png>)

\- choose the Action menu:

![Swagger - Add request action menu](<lib/Swagger%20-%20Add%20request%20action%20menu.png>)

\- choose the toolbar button:

![Swagger - Add request toolbar button](<lib/Swagger%20-%20Add%20request%20toolbar%20button.png>)

&nbsp;

It is easy to maintain the metadata for a request in the properties pane:

![Swagger - Request properties](<lib/Swagger%20-%20Request%20properties.png>)

&nbsp;

## Responses

[Response definitions](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#response-object> "target=\"\_blank\"") describe responses from API operations.&nbsp; For each request, you may create one or more responses.&nbsp;

&nbsp;

![Swagger - Request-Responses](<lib/Swagger%20-%20Request-Responses.png>)

&nbsp;

A response may have a schema that is defined as individual fields or references a definition:

![Swagger - Response schema](<lib/Swagger%20-%20Response%20schema.png>)

&nbsp;

To create a response for a given request, you may:

\- right-click on the request in the ERD and choose the contextual menu option:

![Swagger - Add response contextual menu](<lib/Swagger%20-%20Add%20response%20contextual%20menu.png>)

\- or choose the Action menu:

![Swagger - Add response action menu](<lib/Swagger%20-%20Add%20response%20action%20menu.png>)

\- or choose the toolbar button:

![Swagger - Add response toolbar button](<lib/Swagger%20-%20Add%20response%20toolbar%20button.png>)

&nbsp;

It is easy to maintain the metadata for a response in the properties pane:

![Swagger - Response properties](<lib/Swagger%20-%20Response%20properties.png>)

## Forward-Engineering

The files describing the RESTful API in accordance with the [Swagger specification](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md> "target=\"\_blank\"") are represented as JSON objects and conform to the JSON standards.&nbsp; Hackolade generates Swagger documentation in JSON format or YAML format.&nbsp; The schema exposes two types of fields. Fixed fields, which have a declared name, and patterned fields, which declare a regex pattern for the field name. Patterned fields can have multiple occurrences as long as each has a unique name.&nbsp; The Swagger representation of the API is made of a single file. However, parts of the definitions can be split into separate files, at the discretion of the user. This is applicable for $ref fields in the specification as follows from the [JSON Schema ](<http://json-schema.org/> "target=\"\_blank\"")definitions.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

&nbsp;

![Swagger - Forward-Engineering](<lib/Swagger%20-%20Forward-Engineering.png>)

&nbsp;

An internal Swagger syntax validator ensures that the generated file is valid, and the right-hand pane allows interactions with the API and testing.&nbsp;

&nbsp;

## Reverse-Engineering

This function lets you take a Swagger file in JSON or YAML format and generate a Hackolade model.&nbsp; Then, you may enrich the model with comments, generate standard Hackolade documentation, and make the API evolve to generate a new Swagger file through forward-engineering.

&nbsp;

## External references

It is possible to reference a variety of definitions created elsewhere:

\- another Hackolade model

\- a JSON Schema file

\- an internet link url to a JSON Schema

\- a Swagger API file (YAML or JSON)

\- a Swagger domain export file (YAML or JSON)

\- a SwaggerHub API url

\- a SwaggerHub domain url

\- a Polyglot data model

