# JSON Schema Editor

Wikipedia definition: **JSON** (**JavaScript Object Notation**, pronounced [/](<https://en.wikipedia.org/wiki/Help:IPA/English>)ˈdʒeɪsən[/](<https://en.wikipedia.org/wiki/Help:IPA/English>); also [/](<https://en.wikipedia.org/wiki/Help:IPA/English>)ˈdʒeɪˌsɒn/) is an [open standard](<https://en.wikipedia.org/wiki/Open\_standard>) [file format](<https://en.wikipedia.org/wiki/File\_format>) and data interchange format that uses human-readable text to store and transmit data objects consisting of attribute–value pairs and arrays (or other serializable values). It is a very common data format, with a diverse range of applications, one example being web applications that communicate with a server.&nbsp; JSON is a language-independent data format. It was derived from JavaScript, but many modern programming languages include code to generate and [parse](<https://en.wikipedia.org/wiki/Parsing>) JSON-format data. JSON filenames use the extension .json.

Douglas Crockford originally specified the JSON format in the early 2000s. &nbsp; Here is a 2019 video of Doug Crockford retracing the [History of JSON](<https://youtu.be/TjVcVWB0oFk> "target=\"\_blank\"").&nbsp;

When using JSON documents, whether for document databases or data exchanges, it is useful to ensure the integrity and validity of the JSON document being exchanged or stored.&nbsp; In a similar way to how XSD provides a schema definition for XML, the [JSON Schema](<http://json-schema.org/> "target=\"\_blank\"") standard provides a clear human- and machine-readable documentation of of JSON documents that allow their annotation and validation.

## Graphical JSON Schema editor

Hackolade provides graphical JSON Schema editing of the latest versions including [draft-04](<https://json-schema.org/specification-links.html#draft-4> "target=\"\_blank\""), [draft-06](<https://json-schema.org/specification-links.html#draft-6> "target=\"\_blank\""), [draft-07](<https://json-schema.org/specification-links.html#draft-7> "target=\"\_blank\""), [2019-09](<https://json-schema.org/specification-links.html#2019-09-formerly-known-as-draft-8> "target=\"\_blank\""), [2020-12](<https://json-schema.org/specification-links.html#2020-12> "target=\"\_blank\"").&nbsp; It lets you generate JSON Schema without needing to know JSON Schema syntax, and makes it easy to understand and edit your schema.

&nbsp;

Hackolade provides the unique ability to integrate the structure for multiple documents into an Entity-Relationship Diagram, optionally allowing the creation of implicit Foreign Key Relationships for documentation purposes, while rendering each document as a single atomic unit, even when deeply nested sub-objects and arrays are present.

&nbsp;

![JSON Schema workspace](<lib/JSON Schema workspace.png>)

&nbsp;

Hackolade allows an undefined data type called "any".&nbsp; This allows you to have no restriction on the data type.&nbsp; While the declaration of the "any" data type is explicit in the UI, the result in JSON Schema is the absence of a data type declaration.&nbsp; In other words, the selection of the "any" data type:

![JSON Schema undefined data type any](<lib/JSON Schema undefined data type any.png>)

results in the following JSON Schema declaration:

![Image](<lib/JSON Schema undefined data type any result.png>)

&nbsp;

&nbsp;

## Convert DDLs and XSD into JSON Schema

Hackolade works great to convert structures from [XSD](<XSDXMLSchemaDefinition.md>) (XML Schema) except for import and include, from [DDL](<SQLDDL.md>) (Data Definition Language) for SQL relational databases (RDBMS) as well as all the targets Hackolade supports, whether for data-at-rest or data-in-motion.&nbsp; Hackolade shines at inferring the JSON Schema for any JSON document, and can also generate a sample JSON document for any JSON Schema.&nbsp; Hackolade on-boards a JSON Schema validator, and also allows for user-defined custom properties as well as extensions to allow the specific data types of the different database and protocol targets supported by the tool.&nbsp; A [command-line interface](<CommandLineInterface.md>) makes it easy to automate these functions and integrate them into a CI/CD pipeline.

&nbsp;

![JSON Schema preview](<lib/JSON Schema preview.png>)

&nbsp;

Hackolade handles the polymorphic nature of JSON documents with the support of multiple data types and allOf, anyOf, oneOf choices for [schema combination](<https://json-schema.org/understanding-json-schema/reference/combining.html#combining-schemas> "target=\"\_blank\"").

![JSON Schema choices](<lib/JSON Schema choices.png>)

&nbsp;

Hackolade also supports [conditional application of subschemas](<https://json-schema.org/understanding-json-schema/reference/conditionals.html> "target=\"\_blank\"") whereby the if, then and else keywords allow the application of a subschema based on the outcome of another schema:

![JSON Schema conditional](<lib/JSON Schema conditional.png>)

&nbsp;

Hackolade supports the [reuse](<https://json-schema.org/understanding-json-schema/structuring.html#reuse> "target=\"\_blank\"") of objects structures through references to internal and external [definitions](<Reusableobjectsdefinitions.md>).&nbsp; It is easy to add [user-defined custom properties](<Userdefinedcustomproperties.md>) to the application.

&nbsp;

Hackolade provides a powerful and unique [side-by-side comparison of models](<Compareandmergemodels.md>) handling the synchronized scrolling of hierarchical structures for easy merging of additions, deletions, modifications and moves.

&nbsp;

You may also [generate documentation](<Generatedocumentation.md>) in HTML, Markdown or PDF. &nbsp;

