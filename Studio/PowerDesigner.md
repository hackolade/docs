# PowerDesigner

SAP PowerDesigner has been around for several decades and used to be a quite popular data modeling.&nbsp; Many companies have recognized the large breadth of targets supported by Hackolade Studio and its modernization of the data modeling processes and techniques. &nbsp;

&nbsp;

Hackolade Studio facilitates the migration of PowerDesigner models by letting you read directly PowerDesigner files instead of the more cumbersome previous method which required to first export into an XSD format before importing into Hackolade Studio.

&nbsp;

## Differences with PowerDesigner

There are many differences between Hackolade Studio and PowerDesigner.&nbsp; We do not use or even have a copy of that software.&nbsp; Hackolade's ambition is certainly not to copy PowerDesigner, ... to the contrary\!&nbsp; It should be expected, since Hackolade Studio is a different tool than PowerDesigner, that some things would work differently, that we would name some things differently, that features we have don’t exist in PowerDesigner, and vice versa.&nbsp;

&nbsp;

Here are some examples, but there are many, many more…

* PowerDesigner has 3 core types of data models: conceptual (CDM), logical (LDM), and physical (PDM).&nbsp; Actually, it has more model types: business process models (BPM), object-oriented models (OOM), requirement models (ROM), XML models (XSM), free-form diagrams (FEM), etc...Hackolade Studio only supports conceptual, logical, and physical models.&nbsp; In Hackolade Studio, the Polyglot target supports both conceptual and/or logical models.&nbsp; Given that it is possible to derive a polyglot model from another polyglot model, you may have a polyglot model for conceptual, and another one for logical. So it is possible to map PowerDesigner models 1-to-1 with Hackolade Studio models. It is is also possible to have a polyglot model that covers both conceptual and logical.\
\
![PowerDesigner model migration to Hackolade](<lib/PowerDesigner model migration to Hackolade.png>)\
&nbsp;
* PowerDesigner uses the term "**subject area**" to divide model diagrams into logical sections and “package” to act as containers for objects.&nbsp; We have “[Diagram Views](<DiagramViews.md>)”.&nbsp; The purpose may be somewhat similar.&nbsp; Terminology, and how they function may be different

&nbsp;

* PowerDesigner uses the term "**domain**", a term interpreted differently by different people, for sure to describe something quite different than what we describe as a [re-usable object definition](<Reusableobjectsdefinitions.md>) or user-defined type

&nbsp;

* PowerDesigner has the concept called "**stereotypes**".&nbsp; A stereotype is a semantic classification mechanism, that is used to tag modeling objects (entities, tables, attributes, columns, etc.) in order to express meaning, role, or methodology-specific intent. It does not define data types or physical properties.\
\
In Hackolade Studio, the same semantic classification use case can be covered by our [user-defined custom properties](<Userdefinedcustomproperties.md>)&nbsp; also described in this [how-to guide](<Configurecustomproperties.md>), and [video](<https://community.hackolade.com/slides/slide/user-defined-custom-properties-8> "target=\"\_blank\"").&nbsp;

  * you can define your own custom properties.
  * these properties can represent classifications, categories, or tags.
  * they can be applied consistently to any modeling object.

\
This provides a flexible and explicit way to model stereotype-like semantics.

&nbsp;

* In PowerDesigner,"**shortcuts**" maintain synchronization with their target objects, so changes to the original propagate to all shortcuts. They differ from replicas, which create independent copies.&nbsp; In Hackolade Studio, we call those [references](<Reusableobjectsdefinitions.md>) to existing objects (like entities or tables) in the same model, or a different saved data model, allowing reuse without duplication.&nbsp; When migrating PowerDesigner models to Hackolade Studio, the references must be recreated according to instructions detailed in [this page](<Migrateexternalshortcuts.md>).\
&nbsp;
* When creating foreign key relationships in PowerDesigner, the convention is that you drag from the attribute PK in the parent entity towards the child entity.&nbsp; The attribute is automatically created in the child entity and the FK relationship is also created.&nbsp; Hackolade Studio also supports this approach, but it is not the default behavior.&nbsp; To change the default to be like PowerDesigner, simply change the parameter "FK relationships drag-n-drop behavior" in Tools \> Options \> General to become "from parent to child".\
&nbsp;
* PowerDesigner allows arrows in relational ERDs [pointing to the parent entity](<https://infocenter-archive.sybase.com/help/index.jsp?topic=/com.sybase.stf.powerdesigner.docs\_12.0.0/html/daug/daugp156.htm> "target=\"\_blank\"").&nbsp; Hackolade Studio uses IE (Information Engineering) notation in ER diagrams, wherer cardinality symbols are used on both sides of relationships.&nbsp; In Graph Diagrams of Hackolade Studio, the arrow represents the semantic orientation of the of relationship, typically of the verb of the relationship.&nbsp; In conceptual modeling in Hackolade Studio, the arrow represents the direction of the active verb, and assumes a parent to child direction.\
&nbsp;
* PowerDesigner has a complex **model comparison** approach.&nbsp; With the [architecture of Hackolade Studio](<WhylegacyandSaaSdatamodelingarch.md>), models are in JSON format and are stored in Git repositories where versioning is automatic, and each commit and push results in an immutable version of the model.&nbsp; As a result, a [compare and merge](<Compareandmergemodels.md>) operation in Hackolade Studio always results in a "third" model, instead of an alteration of existing model versions.&nbsp; Note also that it is possible to [compare two arbitrary commits](<https://hackolade.com/help/Explorehistory.html#Compare%20commits>).&nbsp; Whatever the way PowerDesigner compares models, for sure, Hackolade Studio's equivalent feature will work completely differently.

&nbsp;

* PowerDesigner allows to open multiple models in the same application instance.&nbsp; The architecture of Hackolade Studio being different, we allow to start **multiple instances of the application**, each with a single model.&nbsp; This is actually quite handy, as it allows to alt-tab to toggle between different models.&nbsp; As indicated in our [Tips and Tricks](<Tipsandtricks.md>), you may start multiple instances of Hackolade Studio on the same machine session, so as to work on multiple models simultaneously.&nbsp; You may also merge 2 Hackolade models, or combine elements from another model with copy/paste from one model in one application instance, to the other model in the second application instance.&nbsp; From within the application, this is easily done with the shortcut Ctrl+Shift+I (on Mac Cmd+Shift+I) or with the menu option File \> Start New Application Instance.&nbsp; Or from the operating system, on Windows, right-click on the Hackolade icon in the toolbar then choose Hackolade...

&nbsp;

* PowerDesigner has a fairly rigid storage structure in its **central repository** structure. &nbsp; The architecture of our solution is very different from PowerDesigner’s.&nbsp; While PowerDesigner model files in XML format, they are stored in the repository in a structured database.&nbsp; Our files are open in JSON format, and each file represents a single model.&nbsp; Models can be stored in one or more Git repositories, possibly even across multiple repository providers.&nbsp; Models can be organized in a more flexible modular approach, as described [here](<https://hackolade.com/help/PolyglotDataModeling.html#Flexibilty>).&nbsp; With our modular architecture, it is possible for a physical model to be derived from 1 or more (subsets of) polyglot models.&nbsp; It is also possible for any model to reference any part of any model, no matter the target on each side.\
\
Legacy tools have been using the traditional concept of “**logical**” models, which is too constraining for the needs of non-RDBMS targets supported by Hackolade Studio. &nbsp; Hackolade had to invent the principles of [Polyglot Data Modeling](<https://hackolade.com/polyglot-data-modeling.html>) to support the needs of NoSQL, Avro, Parquet, REST APIs, etc…&nbsp; We name it Polyglot, as opposed to logical, to avoid any semantic confusion or discussion.&nbsp; But our Polyglot models are logical in the sense that they are technology-agnostic, and they can be fully normalized. &nbsp; But they can be much more than strict logical models in the sense that they can optionally support nested objects, polymorphism, and denormalization.&nbsp; \
\
Polyglot models can be purely "logical", in the traditional sense.&nbsp; But they can also be more of a "common physical model", including technical names or views that would be common across different physical targets.&nbsp; No dogma with Hackolade: you can be as rigorous in applying data modeling theory as you wish, or less rigorous in order to adhere to the reality of your organization.\
\
Physical data models can be [derived from](<https://hackolade.com/help/PolyglotDataModel.html>) polyglot models.&nbsp; It is also possible to start from a physical data model (either from scratch or created from the reverse-engineering of an instance) and convert it to a polyglot model.\
\
Once a target model is linked to one or more polyglot models, any change in the polyglot model can be reviewed through an [Impact Analysis](<https://hackolade.com/help/PolyglotDataModel.html#Impact%20Analysis>) screen to decide whether to include the changes, globally or individually.\
\
Polyglot models can be derived from (subsets of) other polyglot model(s), as described [here](<https://hackolade.com/help/PolyglotDataModeling.html#Flexibilty>).&nbsp; In the end, it is possible to create a graph of models.\
&nbsp;
* In PowerDesigner when **creating a physical model** from a logical model, the physical model is "generated" (or "derived") from the logical model in a "**push**" process.&nbsp; In Hackolade Studio, the process is different, partly due to the fact that Hackolade Studio supports so many targets that are different than RDBMS.&nbsp; And also because in Hackolade Studio, it is possible to build an N-to-N graph of data models, where for example a model draws from more than one polyglot model.&nbsp; As a result in Hackolade Studio, the process follows a "**pull**" mechanism: you would first create a physical model for the target of our choice, then "derive" from the selected polyglot model or models.

&nbsp;

Given the above, it should be expected that there is some learning curve to our tool.&nbsp; You will most likely avoid frustration if you don't assume, because you're a veteran user of PowerDesigner, that you can use Hackolade Studio without learning about it.&nbsp; This learning curve can be greatly reduced by investing a little bit of time in reading or searching inside our [online documentation](<WelcometoHackoladeStudio.md>), going through [tutorials](<Tutorial.md>) and [how-to guides](<How-toguides.md>), and by watching some of the videos on our [eLearning platform](<https://community.hackolade.com/slides/all> "target=\"\_blank\"").

&nbsp;

### Respective terminology

| **Term in PowerDesigner** | **Term in Hackolade Studio** |
| --- | --- |
| Abstract data types (Physical only) | User-Defined Types |
| Annotation | Annotation |
| Area (Conceptual \& Logical only) | Container |
| Code | Technical name |
| Column (Physical only) | Target specific name (Column, Field, Attribute...) |
| Comment | Description in non-RDBMS target / Comment in RDBMS target |
| Conceptual, Logical model | Polyglot model |
| Data Item (Conceptual only) | Attribute |
| Data type | Type |
| Default value | Default value or Default option for numeric attributes |
| Description | Comment in non-RDBMS target / Remark in RDBMS target |
| (Conceptual/Logical/Physical) Diagram | Entity-Relationship Diagram View (ERDV) |
| Domain | User-Defined Types/Model Definitions |
| Entity (Conceptual \& Logical only) | Entity |
| Entity Attribute (Logical only) | Attribute |
| Extension/Extended attribute | Custom properties |
| High value | Max |
| Identifier | Primary key |
| Index | Index |
| Inheritance | Supertypes / Subtypes |
| Length (character attributes) | Length |
| Length (numeric attributes) | Precision |
| List of values | Enumeration |
| Low value | Min |
| Mandatory | Required |
| Object ID | GUID |
| Package | A PowerDesigner package is used to group modeling objects and the diagrams associated with them. Hackolade Studio takes a different approach: all modeling objects live at the model’s root level, without folder-like packages.&nbsp; Organization is achieved through Entity Relationship Diagram Views (ERDVs), which let users create focused sub-views of the same unified model. In PowerDesigner, packages and diagrams are separate concepts; in Studio, ERDVs provide a simpler way to isolate or zoom in on specific parts of the model without duplicating structure |
| Precision | Scale |
| Relationship | Relationship |
| Shortcut | Reference |
| Symbol | Symbol |
| Table (Physical only) | Target specific name (Table, Collection, Entity...) |
| User (Physical only) | Target specific name (Database, Schema, Container...) |
| View | View |


&nbsp;

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

Starting with v7.9.10 for import into a polyglot model.&nbsp; Starting from v8.0.0 for import into a target model

&nbsp;

Depending on the language used with PowerDesigner, the file extension could also be .pdb, .mpd, mpb, etc.&nbsp; The extension is not really important as long as the content is a PowerDesigner-generated XML file including

\- tags starting with "o:" refer to an "object"

\- tags starting with "a:" refer to an attribute/properties of the object "o:"

\- tags starting with "c:" refer to a list of "objects" linked to the object "o:"

&nbsp;

PowerDesigner physical models typically should be imported in into a Hackolade Studio of the corresponding target.&nbsp; However, Hackolade Studio is also able to convert to another target while converting data types, on a best effort basis, provided that the targets are fairly compatible. If the process encounters an unrecognized data type, it is mapped to the default data type, and a list of concerned attributes is made available in the log.&nbsp; If you think that we are not handling those correctly, please report it to [support@hackolade.com](<mailto:support@hackolade.com>) so we can enhance the standard application, for the benefit of all users.

&nbsp;

Inside PowerDesigner files, the different objects are mapped to equivalent objects in a Hackolade Studio models, mainly:&nbsp;

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

\- Indexes, as long as there is a match between the source technology and the Hackolade Studio target model,

\- database views,

\- domains and [Abstract Data Types](<https://help.sap.com/docs/SAP\_POWERDESIGNER/1f914d86319d43b7b2402532666583c0/b3e01e20f33f45699fe21f6e9fec9e21.html> "target=\"\_blank\""),

\- ExtendedAttributes, mapped them to our custom properties.

&nbsp;

To import a PowerDesigner physical model from the GUI application, you must first create a data model for the target of your choice.&nbsp; Ideally the target model should be empty.&nbsp; But it does not have to be if, for example, you are merging 2 or more PowerDesigner files into a single Hackolade Studio model.

&nbsp;

Then go to Tools \> Reverse-Engineer \> PowerDesigner, and select the PowerDesigner file you wish to import:

![Reverse-engineer or Import PowerDesigner model](<lib/Reverse-engineer or Import PowerDesigner mode.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

## Known limitations

Currently, the following PowerDesigner features are not supported:

\- links [between models](<https://help.sap.com/docs/SAP\_POWERDESIGNER/abd3434b4987485c92057ab9392aadbe/c7e25fae6e1b1014a7948b49b3cdd8fa.html> "target=\"\_blank\"")

\- [XEM extension files](<https://help.sap.com/docs/SAP\_POWERDESIGNER/31c48596e34446a68956e0aa7e700a2e/c7d31d216e1b1014ab88822700700793.html> "target=\"\_blank\"")

\- extended compositions

\- [business rules](<https://help.sap.com/docs/SAP\_POWERDESIGNER/abd3434b4987485c92057ab9392aadbe/c7dd23a26e1b1014a4afd4132cef9ef8.html?\&version=16.6.5> "target=\"\_blank\"")

\- reports

\- support for BPMN, UML, export of XML, etc...

&nbsp;

## Migrate PowerDesigner external shortcuts to Hackolade Studio external references

Please refer to these [step-by-step instructions](<Migrateexternalshortcuts.md>).

&nbsp;

## Bulk import

Using the [Command-Line Interface](<CommandLineInterface.md>), it is easy to orchestrate a batch import of selected PowerDesigner files into Hackolade Studio models, using the command revEngDiagram with its required and options arguments.&nbsp; If you need to import multiple PowerDesigner files, you must repeat the command.

