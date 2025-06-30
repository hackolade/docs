# Add a choice, conditional, or pattern field

In the previous tutorial, we reviewed how to create more complex structures with objects and arrays.&nbsp; By the end of this tutorial, you will master the creation of other types of JSON Schema attributes: choices, conditionals, and pattern fields.

&nbsp;

You may also [view this tutorial](<https://youtu.be/\_tjZGmn7ilg> "target=\"\_blank\"") on YouTube.&nbsp; Summary slides can be found [here](<https://www.slideshare.net/PascalDesmarets1/hackolade-tutorial-part-6-add-choice-conditional-pattern-fieldspdf> "target=\"\_blank\"").

&nbsp;

**Note:** some of the features in this tutorial are not available in all target technologies supported by Hackolade, in which case the feature is disabled. &nbsp;

## Choices

JSON Schema provides a way to [combine schemas](<https://json-schema.org/understanding-json-schema/reference/combining> "target=\"\_blank\"") with the use of [*choice* keywords](<https://json-schema.org/understanding-json-schema/reference/combining.html> "target=\"\_blank\""):

* allOf: the constraint must be valid against all of the subschemas (AND)
* anyOf: the constraint must be valid against any of the subschemas (OR)
* oneOf: the constraint must be valid against exactly one of the subschemas (XOR)
* not: the constraint must not be valid against the subschema.

&nbsp;

These keywords can be used to combine schemas together so a value can be validated against multiple criteria at the same time.&nbsp; It can also be used in combination with references to assemble schemas from multiple files.

&nbsp;

Put a different way, choices are a great way to implement [polymorphism](<Whatispolymorphism.md>), in particular when complex data types are involved.&nbsp; Hackolade fully supports the JSON Schema choices, making it much easier to visualize and maintain.

&nbsp;

There are many different use cases for choices.&nbsp; One that illustrates the capability is when a given field can be either a string or a complex subschema.&nbsp; For example in e-commerce, a shipping address could be "same as billing", or it's own full address structure:

![JSON Schema choices](<lib/JSON Schema choices.png>)

&nbsp;

To create a choice, simply right-click and choose to add, insert, or append a Choice, followed by the keyword adapted to you subschema validation criteria:

![Tutorila - append a choice](<lib/Tutorila - append a choice.png>)

&nbsp;

The application automatically creates 2 subschemas which can be defined independently by adding child attributes:

![Tutorial - choice subschemas](<lib/Tutorial - choice subschemas.png>)

&nbsp;

Additional subschemas can be added with teh right-click contextual menu.

&nbsp;

&nbsp;

## Conditionals

[Draft-07](<https://json-schema.org/specification-links.html#draft-7> "target=\"\_blank\"") of JSON Schema introduced the concept of [conditional application of subschemas](<https://json-schema.org/understanding-json-schema/reference/conditionals.html> "target=\"\_blank\"").&nbsp; The if, then and else keywords allow the application of a subschema based on the outcome of another schema.

&nbsp;

A misapplication of this feature is for multiple data types.&nbsp; Multiple data types have been supported by earlier drafts of JSON Schema, whether for scalar/primitive data types, or when combining with complex data types through the use of choices.&nbsp; It is also desirable to do so for backward-compatibility.

&nbsp;

A better application of this feature is when having to allow the application of a subschema depending on the outcome of **another** schema:

* &nbsp;If ***if*** is valid, then ***then*** must also be valid (and ***else*** is ignored)&nbsp;
* &nbsp;If ***if*** is invalid, then ***else*** must also be valid (and ***then*** is ignored)
* &nbsp;If ***then*** or ***else*** is not defined, if behaves as if they have a value of true
* &nbsp;If ***then*** and/or ***else*** appear in a schema without ***if***, then ***then*** and ***else*** are ignored

&nbsp;

&nbsp;

Here is an example:

*&nbsp; &nbsp; "if": {*

*&nbsp; &nbsp; &nbsp; &nbsp; "properties": {*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "country": {*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "type": "string",*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "const": "United States"*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }*

*&nbsp; &nbsp; &nbsp; &nbsp; }*

*&nbsp; &nbsp; },*

*&nbsp; &nbsp; "then": {*

*&nbsp; &nbsp; &nbsp; &nbsp; "properties": {*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "postal\_code": {*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "type": "string",*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "pattern": "\[0-9\]{5}(-\[0-9\]{4})?"*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }*

*&nbsp; &nbsp; &nbsp; &nbsp; }*

*&nbsp; &nbsp; },*

*&nbsp; &nbsp; "else": {*

*&nbsp; &nbsp; &nbsp; &nbsp; "properties": {*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "postal\_code": {*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "type": "string",*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "pattern": "\[A-Z\]\[0-9\]\[A-Z\] \[0-9\]\[A-Z\]\[0-9\]"*

*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }*

*&nbsp; &nbsp; &nbsp; &nbsp; }*

*&nbsp; &nbsp; }*

&nbsp;

which is represented in Hackolade:

![JSON Schema conditional](<lib/JSON Schema conditional.png>)

&nbsp;

&nbsp;

To create a conditional structure, simply right-click and choose to add, insert, or append a Conditional. &nbsp;

![Tutorila - append a conditional](<lib/Tutorila - append a conditional.png>)

&nbsp;

The application automatically creates conditional subschemas so you can define the constraints and expected outcomes::

![Conditionals template](<lib/Conditionals template.png>)

&nbsp;

&nbsp;

## Pattern fields

Pattern fields function in exactly the same way as standard fields, with one exception: the name (in the name-value pair) is not a fixed string, but a regex pattern.

For example:

![Pattern property example](<lib/Pattern property example.png>)

This is represented in the Hackolade ERD as:

![Pattern property ERD](<lib/Pattern property ERD.png>)

The name in the name-value pair is not a fixed word, but a variable.  That's what pattern fields are for.  They are typically controlled by a regular expression, hence the name of pattern field.

You should not look at it as a 'field name', but as a key to a sub-document when embedding.  It lets you easily access the right sub-document inside an array or main document, using dot notation.

In Hackolade, the above example is modeled this way:

![Pattern property schema](<lib/Pattern property schema.png>)

To add a pattern field to a document structure, right-click and choose add/insert/append \> Pattern Field then the field data type:

![Pattern property contextual menu](<lib/Pattern property contextual menu.png>)

&nbsp;

In this tutorial, we reviewed the creation of other types of JSON Schema attributes: choices, conditionals, and pattern fields.&nbsp; In the next tutorial, we will cover how to add relationships to your entity-relationship diagram.

