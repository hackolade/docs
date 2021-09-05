# JSON Schema Tree view

JSON Schema specifies a JSON-based format to define the structure of JSON data for validation, documentation, and interaction control. A JSON Schema provides a contract for the JSON data required by a given application, and how that data can be modified.

&nbsp;

JSON Schema is based on the concepts from XML Schema (XSD), but it is JSON-based. The JSON data schema can be used to validate JSON data. The schema is self-describing.

&nbsp;

More information can be found on [http://json-schema.org/](<http://json-schema.org/> "target=\"\_blank\"")

&nbsp;

JSON Schema holds a central place in the strategy to model NoSQL document schemas with Hackolade.&nbsp; But Hackolade needs to take some liberties with the JSON Schema specification.&nbsp; One of them, is to expand the list of field types to include additional BSON types (see [BSON Spec](<http://bsonspec.org/> "target=\"\_blank\"")) for the specific needs of MongoDB.&nbsp; Additional fields in the JSON Schema syntax have been added so as to support the persistence of Hackolade data in a JSON repository. Finally, some concepts supported by MongoDB are not supported by JSON Schema, but had to be taken into account.&nbsp; As a result, JSON Schema validation has been extended for the specific needs of Hackolade.&nbsp; But you may still produce standard JSON Schema which will comply with standard validators, or extended JSON Schema (which will not validate with standard validators.)

&nbsp;

![Image](<lib/Couchbase%20DTD.png>)

&nbsp;

&nbsp;

There are many ways to access this screen:

\- double click on the entity title\
\- click once on the middle-right icon in the entity title\
\- right-click on the entity title and choose Open in new tab\
\- right-click on the entity name in the Object Browser on the left, and choose Open in new tab

&nbsp;

![Image](<lib/JSON%20Tree%20in%20new%20tab.png>)

