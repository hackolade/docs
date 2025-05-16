# PowerDesigner

SAP PowerDesigner has been around for several decades and used to be a quite popular data modeling.&nbsp; Many companies have recognized the large breadth of targets supported by Hackolade Studio and its modernization of the data modeling processes and techniques. &nbsp;

&nbsp;

Hackolade Studio facilitates the migration of PowerDesigner models by letting you read directly PowerDesigner files instead of the more cumbersome previous method which required to first export into an XSD format before importing into Hackolade Studio.

&nbsp;

## PowerDesigner conceptual models stored in .cdm files

Starting with v8.1.1

&nbsp;

Depending on the language used with PowerDesigner, the file extension could also be .cdb, .mcd, mcb, etc.&nbsp; The extension is not really important as long as the content is a PowerDesigner-generated XML file including

\- tags starting with "o:" refer to an "object"

\- tags starting with "a:" refer to an attribute/properties of the object "o:"

\- tags starting with "c:" refer to a list of "objects" linked to the object "o:"

&nbsp;

It is natural to reverse-engineer or import a PowerDesigner logical model into a Hackolade Studio [polyglot model](<PolyglotDataModel.md>), Hackolade Studio's equivalent of traditional conceptual (with graph view) logical models, only more flexible and powerful.&nbsp;

&nbsp;

Inside PowerDesigner files, the different objects are mapped to equivalent objects in a Hackolade Studio models, mainly:&nbsp;

\- entities;&nbsp;

\- attributes and their data types (with length, precision, and scale where applicable), business and technical names, comments and descriptions;&nbsp;

\- constraints: required or not null, unique keys, (composite) primary keys, and relationships with their cardinality.

&nbsp;

Some transformations occur, and extraneous information is ignored.&nbsp; We also import:&nbsp;

\- ArchitectureAreas, and map them to containers,&nbsp;

\- Inheritance, and map them to our supertypes and subtypes;&nbsp;

\- ConceptualDiagrams, and map them to our Diagram Views; &nbsp;

\- Shortcuts, and map them to references to their respective entities,

\- Packages, and map them to our Diagram Views,

\- ExtendedAttributes, and map them to our custom properties,

\- and DataItems mapped to attributes.

&nbsp;

To import a PowerDesigner logical model from the GUI application, you must first create a Polyglot data model.&nbsp; Ideally the polyglot model should be empty.&nbsp; But it does not have to be if, for example, you are merging 2 or more PowerDesigner files into a single Hackolade Studio model.

&nbsp;

Then go to Tools \> Reverse-Engineer \> PowerDesigner, and select the PowserDesigner file you wish to import:

![Reverse-engineer or Import PowerDesigner model](<lib/Reverse-engineer or Import PowerDesigner mode.png>)

&nbsp;

&nbsp;

## PowerDesigner logical data models stored in .ldm files

Depending on the language used with PowerDesigner, the file extension could also be .ldb, .mld, mlb, etc.&nbsp; The extension is not really important as long as the content is a PowerDesigner-generated XML file including

\- tags starting with "o:" refer to an "object"

\- tags starting with "a:" refer to an attribute/properties of the object "o:"

\- tags starting with "c:" refer to a list of "objects" linked to the object "o:"

&nbsp;

It is natural to reverse-engineer or import a PowerDesigner logical model into a Hackolade Studio [polyglot model](<PolyglotDataModel.md>), Hackolade Studio's equivalent of traditional logical models, only more flexible and powerful.&nbsp;

&nbsp;

Inside PowerDesigner files, the different objects are mapped to equivalent objects in a Hackolade Studio models, mainly:&nbsp;

\- entities;&nbsp;

\- attributes and their data types (with length, precision, and scale where applicable), business and technical names, comments and descriptions;&nbsp;

\- constraints: required or not null, unique keys, (composite) primary keys, foreign key relationships and their cardinality;

\- views.

&nbsp;

Some transformations occur, and extraneous information is ignored.&nbsp; We also import:&nbsp;

\- ArchitectureAreas, and map them to containers,&nbsp;

\- Inheritance, and map them to our supertypes and subtypes;&nbsp;

\- LogicalDiagrams, and map them to our Diagram Views; &nbsp;

\- Shortcuts, and map them to references to their respective entities,

\- Packages, and map them to our Diagram Views,

\- and most importantly we also import ExtendedAttributes, and map them to our custom properties.

&nbsp;

To import a PowerDesigner logical model from the GUI application, you must first create a Polyglot data model.&nbsp; Ideally the polyglot model should be empty.&nbsp; But it does not have to be if, for example, you are merging 2 or more PowerDesigner files into a single Hackolade Studio model.

&nbsp;

Then go to Tools \> Reverse-Engineer \> PowerDesigner, and select the PowserDesigner file you wish to import:

![Reverse-engineer or Import PowerDesigner model](<lib/Reverse-engineer or Import PowerDesigner mode.png>)

&nbsp;

## PowerDesigner physical data models stored in .pdm files

Starting with v7.9.10 for import into a polyglot model.&nbsp; Starting from v8.0.0 for import into a target maodel

&nbsp;

Depending on the language used with PowerDesigner, the file extension could also be .pdb, .mpd, mpb, etc.&nbsp; The extension is not really important as long as the content is a PowerDesigner-generated XML file including

\- tags starting with "o:" refer to an "object"

\- tags starting with "a:" refer to an attribute/properties of the object "o:"

\- tags starting with "c:" refer to a list of "objects" linked to the object "o:"

&nbsp;

PowerDesigner physical models typically should be imported in into a Hackolade Studio of the corresponding target.&nbsp; However, Hackolade Studio is also able to convert to another target while converting data types, on a best effort basis, provided that the targets are fairly compatible. If the process encounters an unrecognized data type, it is mapped to the default data type, and a list of concerned attributes is made available in the log.&nbsp; If you think that we are not handling those correctly, please report it to [support@hackolade.com](<mailto:support@hackolade.com>) so we can enhance the standard application, for the benefit of all users.

&nbsp;

Inside PowerDesigner files, the different objects are mapped to equivalent objects in a Hackolade Studio modesls, mainly:&nbsp;

\- containers (corresponding to the concept of the target: databases, schemas, namespaces, buckets, keyspace, etc...);

\- entities (tables, collections, etc...);&nbsp;

\- attributes (columns of fields) and their data types (with length, precision, and scale where applicable), business and technical names, comments and descriptions;&nbsp;

\- constraints: required or not null, unique keys, (composite) primary keys, foreign key relationships and their cardinality;

\- views.

&nbsp;

Some transformations occur, and extraneous information is ignored.&nbsp; We also import:&nbsp;

\- ArchitectureAreas, and map them to containers,&nbsp;

\- Inheritance, and map them to our supertypes and subtypes;&nbsp;

\- LogicalDiagrams, and map them to our Diagram Views; &nbsp;

\- Shortcuts, and map them to references to their respective entities,

\- Packages, and map them to our Diagram Views,

\- and most importantly we also import ExtendedAttributes, and map them to our custom properties.

&nbsp;

To import a PowerDesigner physical model from the GUI application, you must first create a data model for the target of your choice.&nbsp; Ideally the target model should be empty.&nbsp; But it does not have to be if, for example, you are merging 2 or more PowerDesigner files into a single Hackolade Studio model.

&nbsp;

Then go to Tools \> Reverse-Engineer \> PowerDesigner, and select the PowserDesigner file you wish to import:

![Reverse-engineer or Import PowerDesigner model](<lib/Reverse-engineer or Import PowerDesigner mode.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

### Known limitations

Currently, the following PowerDesigner features are not supported:

\- domains (in progress)

\- views (TBA)

\- [Abstract Data Types](<https://help.sap.com/docs/SAP\_POWERDESIGNER/1f914d86319d43b7b2402532666583c0/b3e01e20f33f45699fe21f6e9fec9e21.html> "target=\"\_blank\"") (TBA)

\- indexes (TBA)

\- [XEM extension files](<https://help.sap.com/docs/SAP\_POWERDESIGNER/31c48596e34446a68956e0aa7e700a2e/c7d31d216e1b1014ab88822700700793.html> "target=\"\_blank\"")

\- links [between models](<https://help.sap.com/docs/SAP\_POWERDESIGNER/abd3434b4987485c92057ab9392aadbe/c7e25fae6e1b1014a7948b49b3cdd8fa.html> "target=\"\_blank\"")

\- [business rules](<https://help.sap.com/docs/SAP\_POWERDESIGNER/abd3434b4987485c92057ab9392aadbe/c7dd23a26e1b1014a4afd4132cef9ef8.html?\&version=16.6.5> "target=\"\_blank\""), etc...

&nbsp;

## Bulk import (TBD)

Using the [Command-Line Interface](<CommandLineInterface.md>), it is easy to orchestrate a batch import of selected PowerDesigner files into Hackolade Studio models, using the command revEngDiagram with its required and options arguments.

&nbsp;

&nbsp;

