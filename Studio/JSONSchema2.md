# JSON Schema

Hackolade is a visual editor for JSON Schema for non-programmers.&nbsp; It is ideal to perform the upfront schema design of any type of JSON document &nbsp; Since v5 of Hackolade, the latest JSON Schema specifications are supported:

\- [draft-04](<https://json-schema.org/specification-links.html#draft-4> "target=\"\_blank\"")

\- [draft-06](<https://json-schema.org/specification-links.html#draft-6> "target=\"\_blank\"")

\- [draft-07](<https://json-schema.org/specification-links.html#draft-7> "target=\"\_blank\"")

\- [2019-09](<https://json-schema.org/specification-links.html#2019-09-formerly-known-as-draft-8> "target=\"\_blank\"")

\- [2020-12](<https://json-schema.org/specification-links.html#2020-12> "target=\"\_blank\"")

&nbsp;

Hackolade was specially adapted to support the data modeling of JSON files.

![JSON workspace](<lib/JSON%20workspace.png>)

&nbsp;

[](<http://www.json.org/> "target=\"\_blank\"")

[JSON](<http://www.json.org/> "target=\"\_blank\"") (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate.&nbsp; It is based on a subset of the JavaScript Programming Language.&nbsp; JSON is a text format that is completely language independent but uses conventions that are familiar to programmers of the C-family of languages.&nbsp; These properties make JSON an ideal data-interchange language.&nbsp; JSON is built on two structures:

* A collection of name/value pairs. In various languages, this is realized as an object, record, struct, dictionary, hash table, keyed list, or associative array.
* An ordered list of values. In most languages, this is realized as an array, vector, list, or sequence.

&nbsp;

&nbsp;

![Image](<lib/JSON%20schema%20tree%20view.png>)

&nbsp;

With version 5 of Hackolade, support was introduced for the [conditional application of subschemas](<https://json-schema.org/understanding-json-schema/reference/conditionals.html> "target=\"\_blank\"").&nbsp; The if, then and else keywords allow the application of a subschema based on the outcome of another schema:

&nbsp;

![JSON Schema conditional](<lib/JSON%20Schema%20conditional.png>)

&nbsp;

&nbsp;

You will find more information about JSON Schema on the [website](<http://json-schema.org/> "target=\"\_blank\""). &nbsp;

&nbsp;

## Forward-engineering

Hackolade dynamically generates JSON Schema for the structure created with the application, and can be pre-viewed with a variety of options, as further described [here](<JSONSchema.md>). The JSON Schema can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Forward-Engineering - JSON Preview](<lib/Forward-Engineering%20-%20JSON%20Preview.png>)

&nbsp;

&nbsp;

The JSON Schema can also be exported to a Confluent or Pulsar Schema Registry instance:

![JSON Schema - forward-engineering to Confluent](<lib/JSON%20Schema%20-%20forward-engineering%20to%20Confluen.png>)

&nbsp;

&nbsp;

## Reverse-Engineering

Hackolade can reverse-engineer of course JSON Schema from different drafts, but also infer the schema from JSON, YAML or NDJSON documents.&nbsp; It can also convert DDLs and XSDs to JSON Schema.

