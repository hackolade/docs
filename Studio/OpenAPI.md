# OpenAPI

**OpenAPI Specification** or OAS (formerly known as **Swagger Specification**) is an open-source format for describing and documenting APIs. It has become a de-facto standard, language-agnostic interface for designing and describing RESTful APIs which allow both humans and computers to discover and understand the capabilities of the service without access to source code, documentation, or through network traffic inspection.&nbsp; When properly defined via OpenAPI, a consumer can understand and interact with the remote service with a minimal amount of implementation logic.&nbsp; The latest version of OpenAPI is **3.1.0**. OpenAPI definitions can be written in JSON or YAML.

&nbsp;

OpenAPI is a [formal specification](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.1.0.md> "target=\"\_blank\"") surrounded by a large ecosystem of tools, which includes everything from front-end user interfaces, low-level code libraries and commercial API management solutions.

&nbsp;

To perform model-first design of a REST API using OpenAPI 3 with Hackolade, you must first download the OpenAPI [plugin](<DownloadadditionalDBtargetplugin.md>).&nbsp; This plugin is strictly compliant with both versions 3.0.x and 3.1.x of the OpenAPI specification.&nbsp; Note that there are breaking changes between version 3.0.x and 3.1.x, so you need to choose the right version when you create a new model.&nbsp; If you need support version 2 of the specification (a.k.a. Swagger) you need another plugin described [here](<SwaggerAPI.md>).

&nbsp;

Creating APIs is not easy\! And writing OpenAPI documentation in a design-first approach can be tedious at best, generally error-prone and frustrating...&nbsp; Hackolade takes a **visual schema-centric** approach so you can focus on the content of requests and responses. The application also assists with all the metadata to produce validated OpenAPI files and test the transactions.&nbsp; You can also reverse-engineer existing OpenAPI 3 files in JSON or YAML to produce a graphical representation of your APIs.

Hackolade was specially adapted to support the API design of OAS, including all the necessary metadata for the API, the requests and responses.&nbsp; The application closely follows the terminology of the specification.&nbsp; The visual tool puts the focus on what really matters in an API: the schema of the information being exchanged between systems.&nbsp; At the same time, it provides assistance to modelers and does not require perfect mastery of the OpenAPI 3 syntax.&nbsp; It generates validated files that are syntactically correct and compatible with the specification thereby greatly improving productivity, consistency, and quality.&nbsp; A step-by-step tutorial is available in a [YouTube video](<https://hackolade.com/videos.html#swagger> "target=\"\_blank\"").

&nbsp;

The diagram below results from the reverse-engineering of the [Pet Store](<https://mermade.org.uk/examples/openapi.json> "target=\"\_blank\"") sample API.

![OpenAPI Workspace](<lib/OpenAPI Workspace.png>)

&nbsp;

Note the toolbar button to toogle the level of details displayed in the ER Diagram view. &nbsp;

![OpenAPI - Toggle field details](<lib/OpenAPI - Toggle field details.png>)

&nbsp;

By default Hackolade displays all the various ways an API can be defined in OpenAPI.&nbsp; Once you're done creating your design, you may wish to hide the extraneous structures and adjust the layout to take advantage of the extra real estate on screen.

&nbsp;

## Data Types

The OpenAPI specification describes primitives (or scalar) data types which can have an optional property modifier, *format*, plus a file primitive type.&nbsp; Complex types such as arrays and sub-objects, plus combinations thereof, are also allowed.

&nbsp;

![OpenAPI data types](<lib/Swagger data types.png>)&nbsp; ![OpenAPI data types - string](<lib/Swagger data types - string.png>)&nbsp; ![OpenAPI data types - number](<lib/Swagger data types - number.png>)&nbsp; ![OpenAPI data types - integer](<lib/Swagger data types - integer.png>) &nbsp;

&nbsp;

Note that with OAS version 3.1.0, full compatibility with [JSON Schema draft-2020-12](<https://json-schema.org/specification.html> "target=\"\_blank\"") has been achieved.&nbsp; For example the null data type has now been introduced.&nbsp; You will find more details in [this blog](<https://lornajane.net/posts/2020/whats-new-in-openapi-3-1> "target=\"\_blank\"").

&nbsp;

## API metadata

The info object, as well as the host, basePath, schemes, consumes, produces, the securityDefinitions object, the security object, the tags object, and externalDocs object are fixed fields treated as metadata and maintained at model-level in Hackolade.

&nbsp;

![OpenAPI - Info object 1](<lib/OpenAPI - Info object 1.png>)&nbsp; ![OpenAPI - Info object 2](<lib/OpenAPI - Info object 2.png>)&nbsp; ![OpenAPI - Info object 3](<lib/OpenAPI - Info object 3.png>)

&nbsp;

## Components

[Component objects](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#components-object> "target=\"\_blank\"") hold a set of reusable objects that can be used across multiple endpoints in the same API: schema, parameter, request body, response, example, header, security scheme, link, or callback. All objects defined within the components object will have no effect on the API unless they are explicitly referenced from properties outside the components object by using a $ref reference in any path item.

&nbsp;

As you expose more resources and operations against your API, your API may repeat a lot of existing parameters or response descriptions in many different paths and operations.&nbsp; By creating reusable component objects, you avoid time-consuming rewriting as well as the risk of inconsistencies.

&nbsp;

Data types can be objects, but also primitives and arrays. This object is based on the [JSON Schema Specification Wright Draft 00 (a.k.a. Draft-05)](<http://json-schema.org/> "target=\"\_blank\"") and uses a predefined subset of it. On top of this subset, there are extensions provided by this specification to allow for more complete documentation.

&nbsp;

![OpenAPI - Components](<lib/OpenAPI - Components.png>)

&nbsp;

Consult [this page](<Reusableobjectsdefinitions.md>) or more information on how to use definitions.&nbsp; For OpenAPI, you should limit yourself to Hackolade model definitions.

## Resource

The resource path object is a container representing the relative path to an individual endpoint.&nbsp; The field name must start with a slash ("/").&nbsp; The path is appended to the basePath in order to construct the full URL.&nbsp; Path templating (usage of curly braces ("{}") to mark a section of a URL path as replaceable using path parameters) is allowed.

&nbsp;

Each resource contains one or more "[path item objects](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#pathItemObject> "target=\"\_blank\"")" made of a request and one or more responses:

![OpenAPI - Resource container](<lib/OpenAPI - Resource container.png>)

&nbsp;

You may create a new resource via right-click anywhere in the ERD view and choosing the contextual menu option:

![OpenAPI - Add resource contextual menu](<lib/Swagger - Add resource contextual menu.png>)

&nbsp;

or via the menu:

![OpenAPI - Add resource action menu](<lib/Swagger - Add resource action menu.png>)

&nbsp;

or the toolbar:

![OpenAPI - Add resource toolbar button](<lib/Swagger - Add resource toolbar button.png>)

&nbsp;

## Requests

A request is an object with a type, associated data, relationships to other resources, and a set of methods that operate on it.&nbsp; Only a few standard methods are defined for the resource (corresponding to the standard HTTP GET, POST, PUT and DELETE methods.)

&nbsp;

The [Parameter Object](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#parameterObject> "target=\"\_blank\"") describes a single operation parameter defined by a combination of a name and location.&nbsp; Hackolade provides a handy template of parameter types allowing the description of the payload either by adding adding individual fields or by referencing an existing component:

![OpenAPI - Request Parameter 1](<lib/OpenAPI - Request Parameter 1.png>)

![OpenAPI - Request Parameter 2](<lib/OpenAPI - Request Parameter 2.png>)

&nbsp;

To create a request within a resource container, you may:

\- right-click inside the container area of the ERD pane, and choose the contextual menu option:

![OpenAPI - Add request contextual menu](<lib/Swagger - Add request contextual menu.png>)

\- choose the Action menu:

![OpenAPI - Add request action menu](<lib/Swagger - Add request action menu.png>)

\- choose the toolbar button:

![OpenAPI - Add request toolbar button](<lib/Swagger - Add request toolbar button.png>)

&nbsp;

It is easy to maintain the metadata for a request in the properties pane:

![OpenAPI - Request Properties](<lib/OpenAPI - Request Properties.png>)

&nbsp;

## Responses

[Response objects](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#responses-object> "target=\"\_blank\"") describe responses from API operations.&nbsp; For each request, you may create one or more responses.

![OpenAPI - Responses](<lib/OpenAPI - Responses.png>)

&nbsp;

A response may have a schema that is defined as individual fields or references a component:

![OpenAPI - Response schema](<lib/OpenAPI - Response schema.png>)

&nbsp;

To create a response for a given request, you may:

\- right-click on the request in the ERD and choose the contextual menu option:

![OpenAPI - Add response contextual menu](<lib/Swagger - Add response contextual menu.png>)

\- or choose the Action menu:

![OpenAPI - Add response action menu](<lib/Swagger - Add response action menu.png>)

\- or choose the toolbar button:

![OpenAPI - Add response toolbar button](<lib/Swagger - Add response toolbar button.png>)

&nbsp;

It is easy to maintain the metadata for a response in the properties pane:

![OpenAPI - Response properties](<lib/OpenAPI - Response properties.png>)

&nbsp;

## Forward-Engineering

The files describing the RESTful API in accordance with the [OpenAPI specification](<https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md> "target=\"\_blank\"") OAS are represented as JSON objects and conform to the JSON standards.&nbsp; Hackolade generates OpenAPI documentation in JSON format or YAML format.&nbsp; The schema exposes two types of fields. Fixed fields, which have a declared name, and patterned fields, which declare a regex pattern for the field name. Patterned fields can have multiple occurrences as long as each has a unique name.&nbsp; The OpenAPI representation of the API is made of a single file. However, parts of the definitions can be split into separate files, at the discretion of the user. This is applicable for $ref fields in the specification as follows from the [JSON Schema ](<http://json-schema.org/> "target=\"\_blank\"")definitions.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![OpenAPI - Forward-Engineering](<lib/OpenAPI - Forward-Engineering.png>)

&nbsp;

An internal OpenAPI syntax validator ensures that the generated file is valid, and the right-hand pane allows interactions with the API and testing.&nbsp;

&nbsp;

## Reverse-Engineering

This function lets you take a OpenAPI file in JSON or YAML format and generate a Hackolade model.&nbsp; Then, you may enrich the model with comments, generate standard Hackolade documentation, and make the API evolve to generate a new OpenAPI file through forward-engineering.

&nbsp;

&nbsp;

## External references

It is possible to reference a variety of definitions created elsewhere:

\- another Hackolade model

\- a JSON Schema file

\- an internet link url to a JSON Schema

\- an OAS API file (YAML or JSON)

\- an OpenAPI domain export file (YAML or JSON)

\- a SwaggerHub API url

\- a SwaggerHub domain url

\- a Polyglot data model

&nbsp;

