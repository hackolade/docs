# Attributes

The terms 'attribute' and 'field', while containing nuances, are sometimes used interchangeably. &nbsp; An attribute is a generic word to describe the different types described below. &nbsp;

&nbsp;

A collection defined in JSON Schema for the purpose of document modeling may contain these different types of attributes:&nbsp;

* a root attribute, which in the case of NoSQL is always a document (whereas JSON Schema allows the root to be other types)
* a field
* a pattern field
* a choice
* an array item
* a subschema
* a reference to a previously defined attribute

All the details of how to introduce an attribute in the hierarchical schema view can be found in the page about the manipulation of [Attribute boxes in Tree diagram](<Attributeboxesinhierarchicalsche.md>).

### Root

There is only one root possible per document.&nbsp; For the purpose of a NoSQL document schema, the root attribute can only be of type: document. &nbsp;

Properties can be filled for the root attribute.&nbsp; They are essentially the properties of the collection.

One or more attributes (child field, pattern field, or choice) can be created, as seen below.

&nbsp;

### Field

This is the most common attribute in a schema.&nbsp; It defines the name-value pair that will be found in the JSON document.&nbsp; The properties define the details and constraints of both the name and the value in the pair.&nbsp; As defined by the JSON Schema specification, the available data types for a field value are: string, numeric, boolean, object (document), array, and null.&nbsp; For the purpose of MongoDB, additional BSON types are available: objectID, binary, date, timestamp, regex, JavaScript, JavaScript with scope, symbol, minKey, and maxKey. &nbsp;

&nbsp;

The nominal case is for an attribute to have only one type.&nbsp; The JSON specification however allows a field to be of multiple types.&nbsp; The application UI is able to define and maintain multiple types for a field.&nbsp; If the data types in the multiple set are all scalar types (string, number, boolean, null), then you just press the + sign to the right of the data type property:

![Data types multiple](<lib/Data%20types%20multiple.png>)

As a result, the data type in the ERD appears as "multi":

![Data types multiple ERD](<lib/Data%20types%20multiple%20ERD.png>)

&nbsp;

The Properties Pane displays an array of properties for each of the data types:

![Data types multiple Properties Pane](<lib/Data%20types%20multiple%20Properties%20Pane.png>)

&nbsp;

To expand the list&nbsp; of properties for a given data type, press the + sign on the left.&nbsp; To suppress a data type, click the X on the right.

&nbsp;

If one of the data types is complex (array or object, and also list, map, struct, etc. in other targets), then you must use a choice, cfr below.&nbsp; With v6.2.2, and only for JSON Schema and MongoDB, it is also possible to specify multiple data type with at least one complex data type, using the simpler method already used with scalar data types:

![Data types multiple complex object and array](<lib/Data%20types%20multiple%20complex%20object%20and%20array.png>)

&nbsp;

The nature of attributes is different for document, array, or others.&nbsp; Documents are allowed to have one or more Fields, Pattern Fields, and/or Choices as attributes.&nbsp; Arrays are allowed to have one or more Array Items and/or Choices as attributes.&nbsp; As for all other types of fields, the only possible attribute is ‘Choice’.

&nbsp;

With version 5.3.0, Hackolade introduced the possibility, in the JSON target only, to have an undefined data type called "any".&nbsp; This allows you to have no restriction on the data type.&nbsp; While the declaration of the "any" data type is explicit in the UI, the result in JSON Schema is the absence of a data type declaration.&nbsp; In other words, the selection of the "any" data type:

![JSON Schema undefined data type any](<lib/JSON%20Schema%20undefined%20data%20type%20any.png>)

results in the following JSON Schema declaration:

![Image](<lib/JSON%20Schema%20undefined%20data%20type%20any%20result.png>)

&nbsp;

&nbsp;

### Pattern field

Pattern fields (or [pattern properties](<http://json-schema.org/latest/json-schema-validation.html#rfc.section.6.5.5> "target=\"\_blank\"")) function in exactly the same way as standard fields, with only one exception: the name (in the name-value pair) is not a fixed string, but a regex pattern.&nbsp; This can be particularly useful in MongoDB in combination with ‘dot notation’.&nbsp; It is also the basis for storage in Firebase and Firestore.

&nbsp;

For example:

![patternExample and ERD](<lib/patternExample%20and%20ERD.png>)

&nbsp;

The sub-document key in the key-value pair is not a fixed word, but a variable.&nbsp; These keys are typically controlled by a regular expression pattern, hence the name of 'pattern field'.&nbsp; You should not look at it as a 'field name', but as a key to a sub-document when embedding.  It lets you easily access the right sub-document inside an array or main document, using dot notation. &nbsp;

&nbsp;

In Hackolade, the above example is modeled this way:

![pattern field property example tree](<lib/patternExample%20tree.png>)

&nbsp;

&nbsp;

### Choice

In JSON Schema, there are 4 possible choices: “allOf”, “anyOf”, “oneOf”, and “noneOf”.&nbsp; Each of these attributes contains an array, with each attribute of the array representing content that will be matched against.&nbsp; The choice of “allOf”, “anyOf”, “oneOf”, or “not” determines how the validation processor will treat the results of the matches:&nbsp;

* allOf requires that all attributes in the suschema are matched successfully.
* anyOf requires one or more of the attributes in the subschema to be matched successfully.
* oneOf requires one, and only one, of the attributes in the subschema to match successfully.
* noneOf requires that no attribute in the subschema is matched successfully.

Schema definitions can use “allOf”, “anyOf”, “oneOf”, and “noneOf” individually or in combination, providing significant flexibility for defining attributes that have complex definitions or contextual relationships.&nbsp; These choices apply both to fields and to field properties.&nbsp; In both cases, the only possible attribute of Choice is a Subschema.

&nbsp;

![JSON Schema choices](<lib/JSON%20Schema%20choices.png>)

&nbsp;

### if-then-else conditional subschemas

With version 5 of Hackolade, support was introduced for the [conditional application of subschemas](<https://json-schema.org/understanding-json-schema/reference/conditionals.html> "target=\"\_blank\"").&nbsp; The if, then and else keywords allow the application of a subschema based on the outcome of another schema.

&nbsp;

A misapplication of this feature introduced with JSON Schema [draft-07](<https://json-schema.org/specification-links.html#draft-7> "target=\"\_blank\""), is for multiple data types.&nbsp; Multiple data types have been supported by earlier drafts of JSON Schema, whether for scalar/primitive data types, or when combining with complex data types through the use of choices.&nbsp; It is also desirable to do so for backward-compatibility.

&nbsp;

A better application of this feature is when having to allow the application of a subschema depending on the outcome of another schema:

* &nbsp;If ***if*** is valid, then ***then*** must also be valid (and ***else*** is ignored)&nbsp;
* &nbsp;If ***if*** is invalid, then ***else*** must also be valid (and ***then*** is ignored)
* &nbsp;If ***then*** or ***else*** is not defined, if behaves as if they have a value of true
* &nbsp;If ***then*** and/or ***else*** appear in a schema without ***if***, then ***then*** and ***else*** are ignored

&nbsp;

&nbsp;

![JSON Schema conditional](<lib/JSON%20Schema%20conditional.png>)

&nbsp;

&nbsp;

### Array item

This is the only possible attribute type of an Array field.&nbsp; Different types of array items are possible for a same parent attribute.&nbsp; Each can have from 0 to n occurences, but can be limited by the minItems and maxItems properties of the Array.

&nbsp;

### Subschema

This is the only possible attribute type of a Choice field.&nbsp; The subschema is a document with all the schema possibilities of a JSON object. &nbsp;

&nbsp;

### Reference

Definitions, maintained at 3 distinct levels (collection, model, and external) can be re-used as an attribute.&nbsp; More details [here](<Reusableobjectsdefinitions.md>).

&nbsp;

### Pick from list

Any field previously created in the same collection can be repeated without having to be typed again.&nbsp; Note that they are not linked to each other, so a change in one will not be synched.

