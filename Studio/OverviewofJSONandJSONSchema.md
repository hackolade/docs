# Overview of JSON and JSON Schema

## JSON

**JSON** stands for JavaScript Object Notation.&nbsp; It is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate.

&nbsp;

According to [json.org](<https://www.json.org/json-en.html> "target=\"\_blank\""), JSON is built on two structures:

* A collection of name/value pairs.&nbsp; In various languages, this is realized as an *object*, record, struct, dictionary, hash table, keyed list, or associative array.
* An ordered list of values.&nbsp; In most languages, this is realized as an *array*, vector, list, or sequence.

&nbsp;

An *object* is an unordered set of name/value pairs.&nbsp; An *object* begins with a **{**&#8202;*left brace* and end with a **}**&#8202;*right brace*.&nbsp; Each name is followed by a **:**&#8202;*colon* and the name/value pairs are separated by a **,**&#8202;*comma*.

![JSON object syntax](<lib/JSON%20object%20syntax.png>)

&nbsp;

An *array* is an ordered collection of values.&nbsp; An *array* begins with a **\[**&#8202;*left bracket* and end with a **\]**&#8202;*right bracket*.&nbsp; Values are separate by a ,*comma*.

&nbsp;

![JSON array syntax](<lib/JSON%20array%20syntax.png>)

&nbsp;

A *value* can be a *string* in double quotes, or a *number*, or **true** or **false** or **null**, or an *object* or an *array*. These structures can be nested.

![JSON array syntax](<lib/JSON%20value%20syntax.png>)

&nbsp;

&nbsp;

Keys must be strings (text) and values must be valid JSON data types: string, number, another JSON object, array, boolean or null.

![JSON key-value pairs](<lib/JSON%20key-value%20pairs.png>)

&nbsp;

&nbsp;

&nbsp;

There are infinite ways to organize JSON objects, depending on your needs. It can be as simple as a list or attributes (keys) and values, or it can become very complex with nested JSON objects, arrays of JSON objects, arrays inside attributes, etc...

![JSON document object](<lib/JSON%20document%20object.png>)

&nbsp;

&nbsp;

&nbsp;

## JSON in databases

One of the big advantages of document databases such as MongoDB, Couchbase, DocumentDB, Elasticsearch, etc., besides their distributed horizontal scalability, is that you can leverage the flexibility and easy evolution of JSON documents. &nbsp;

* you can embed information using objects, arrays or a combination thereof to capture relationships between data into a single document structure, thereby denormalizing the data and avoiding expensive joins while maintaining integrity of the transactions
* collections of documents do not require that all the documents have the same schema: some may have more fields than others, plus the data type of some fields may differ across documents of the same collection.&nbsp; Be careful however about this point...&nbsp; While the flexibility is wonderful, it should be carefully managed to not lead to chaos.&nbsp;

&nbsp;

The benefits of a single document atomicity with embedded objects is best illustrated with a shopping cart or an invoice.&nbsp; With relational databases, the storage of this information would require multiple tables with foreign keys, implying that data is split between all these tables when storing the data. &nbsp;

![JSON order normalized structure](<lib/JSON%20order%20normalized%20structure.png>)

&nbsp;

&nbsp;

Then, when comes the time to display the information on screen or print the invoice, the information needs to be gathered again, using lengthy and CPU-intensive joins.&nbsp; Besides the performance impact of these joins, developers encounter difficulties known as [impedance mismatch](<https://en.wikipedia.org/wiki/Object–relational\_impedance\_mismatch> "target=\"\_blank\"").

&nbsp;

With a JSON, it make a lot of sense to gather all this information in a single atomic document, including all the information needed to produce the screen or invoice.&nbsp; Besides, only a single access to storage is required to get all this information, instead of one for each part of the join.

&nbsp;

![JSON order denormalized structure](<lib/JSON%20order%20denormalized%20structure.png>)

&nbsp;

## JSON Schema

JSON Schema is a vocabulary to annotate and validate JSON documents. It defines how a JSON should be structured, making it easy to ensure that a JSON is formatted correctly, and it is useful for automated testing and validating. In addition, JSON Schema provides clear human- and machine-readable documentation.&nbsp;

&nbsp;

Schemas in general are used to validate files before use to prevent (or at least lower the risk of) software failing in unexpected ways. If there’s an error in the data being validated, the schema fails immediately. Schemas can serve as an extra quality filter for data.

&nbsp;

Furthermore, when used in the context of the [MongoDB validator](<https://docs.mongodb.com/manual/core/schema-validation/> "target=\"\_blank\""), you can enforce the specified schema on insert and update operations in MongoDB for higher consistency and data quality.

&nbsp;

JSON Schema is a [standard](<https://json-schema.org/> "target=\"\_blank\"") providing a format for what JSON data is required for a given application and how to interact with it.&nbsp; Understanding JSON Schema involves a learning curve, so we suggest reading [this guide](<https://json-schema.org/understanding-json-schema/index.html> "target=\"\_blank\"") for more information.&nbsp; But Hackolade makes is super simple for users as it dynamically generates JSON Schema for structures created with the tool.&nbsp; While a basic understanding of JSON Schema helps leverage the power of the tool, it is not necessary to know the JSON Schema syntax.&nbsp; Also, the tool onboards a validator so you can be sure that all quotes, braces, brackets, and commas are in the right places.

&nbsp;

The design of a JSON document depend largely on its intended use within an application, so there’s no right or wrong way to design a document.. However, when an application a document, it is important to know exactly how that document should be organized. the application needs to know what fields are expected, and how the values are represented. That’s where JSON Schema comes in.

&nbsp;

Note that JSON Schema itself is written in JSON. It is data itself, not a computer program. It’s just a declarative format for “describing the structure of other data”.

&nbsp;

Hackolade Studio was built on top of JSON Schema, with extensions, and using it as an internal notation to represent all kinds of hierarchical structures, whether related to JSON or not.&nbsp; For a long time also, before the introduction of the [Polyglot data modeling](<PolyglotDataModel.md>) capability, JSON Schema was used also to convert models from one target technology to another.&nbsp; Hackolade supports the latest JSON Schema specifications :

\- [draft-04](<https://json-schema.org/specification-links.html#draft-4> "target=\"\_blank\"")

\- [draft-06](<https://json-schema.org/specification-links.html#draft-6> "target=\"\_blank\"")

\- [draft-07](<https://json-schema.org/specification-links.html#draft-7> "target=\"\_blank\"")

\- [2019-09](<https://json-schema.org/specification-links.html#2019-09-formerly-known-as-draft-8> "target=\"\_blank\"")

\- [2020-12](<https://json-schema.org/specification-links.html#2020-12> "target=\"\_blank\"")

## Representation of nested structures in Entity Relationship Diagrams

The novel added-value provided by Hackolade Studio is its ability to represent nested structures inside an Entity-Relationship Diagram.&nbsp; In a way, we have bent and stretched the theory of ERDs to accommodate a user-friendly view of JSON document structures in ERDs.

&nbsp;

If you use a traditional ERD tool to represent the above order document, it can only create a separate for each nested object, something like this:

![JSON order normalized ERD](<lib/JSON%20order%20normalized%20ERD.png>)

&nbsp;

We think that this is a fundamentally flawed approach.&nbsp; One that is neither user-friendly nor scalable, particularly in the context of document databases with many different databases.&nbsp; We prefer to present the schema of the JSON in a single atomic unit which respects the structure, the sequence, and the indentation of the document:

![JSON order ERD](<lib/JSON%20order%20ERD.png>)

&nbsp;

We supplement this view with a hierarchical schema view which is sometimes preferred by users to manipulated nested objects:

![Image](<lib/JSON%20order%20hierarchical%20schema%20view.png>)

&nbsp;

And finally, we facilitate the linking of multiple documents in an Entity-Relationship Diagram:

![Image](<lib/JSON%20multiple%20entity%20ERD.png>)

&nbsp;

While foreign key relationships are not enforced by the document database, it is important for a better understanding, to document implicit relationships in the data.

