# Choices

JSON Schema includes keywords to allow [schema composition](<https://json-schema.org/understanding-json-schema/reference/combining> "target=\"\_blank\"") or the combination of schemas and corresponding to the boolean algebra concepts AND, OR, XOR, and NOT.

&nbsp;

The keywords used to combine schemas are:

* [allOf](<https://json-schema.org/understanding-json-schema/reference/combining.html#allof> "target=\"\_blank\""): (AND) Must be valid against *all* of the sub-schemas
* [anyOf](<https://json-schema.org/understanding-json-schema/reference/combining.html#anyof> "target=\"\_blank\""): (OR) Must be valid against *any* of the sub-schemas
* [oneOf](<https://json-schema.org/understanding-json-schema/reference/combining.html#oneof> "target=\"\_blank\""): (XOR) Must be valid against *exactly one* of the sub-schemas

All of these keywords must be set to an array, where each item is a schema.

In addition, there is:

* [not](<https://json-schema.org/understanding-json-schema/reference/combining.html#not> "target=\"\_blank\""): (NOT) Must *not* be valid against the given schema

&nbsp;

Hackolade was build from scratch on top of JSON Schema, and we fully support the concept of choices, provided that the model target supports it.&nbsp; For example, RDBMS targets do not, so the functions is disabled.

&nbsp;

You may add choices to your model either from the ERD pane, or from the hierarchical tree view, the latter being often chosen as simpler to understand and visualize.

&nbsp;

Instead of adding a simple attribute, choose

![oneOf choice create](<lib/oneOf choice create.png>)

&nbsp;

This action automatically creates 2 sub-schema objects.

![Image](<lib/oneOf choice subschemas.png>)

&nbsp;

Then you can define each sub-schema:

![oneOf choice subschemas structure](<lib/oneOf choice subschemas structure.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

You will find more information on [this page](<https://json-schema.org/understanding-json-schema/reference/combining.html> "target=\"\_blank\"").&nbsp;

