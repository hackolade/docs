# PowerDesigner

SAP PowerDesigner has been around for several decades and used to be a quite popular data modeling. Many companies have recognized the large breadth of targets supported by Hackolade Studio and its modernization of the data modeling processes and techniques.

&nbsp;

Hackolade Studio facilitates the migration of PowerDesigner models by letting you read directly PowerDesigner files instead of the more cumbersome previous method which required to first export into an XSD format before importing into Hackolade Studio.

&nbsp;

## Differences with PowerDesigner

There are many differences between Hackolade Studio and PowerDesigner. We do not use or even have a copy of that software. Hackolade's ambition is certainly not to copy PowerDesigner, ... to the contrary! It should be expected, since Hackolade Studio is a different tool than PowerDesigner, that some things would work differently, that we would name some things differently, that features we have don’t exist in PowerDesigner, and vice versa.

&nbsp;

Here are some examples, but there are many, many more…

- PowerDesigner has 3 core types of data models: conceptual (CDM), logical (LDM), and physical (PDM). Actually, it has more model types: business process models (BPM), object-oriented models (OOM), requirement models (ROM), XML models (XSM), free-form diagrams (FEM), etc...Hackolade Studio only supports conceptual, logical, and physical models. In Hackolade Studio, the Polyglot target supports both conceptual and/or logical models. Given that it is possible to derive a polyglot model from another polyglot model, you may have a polyglot model for conceptual, and another one for logical. So it is possible to map PowerDesigner models 1-to-1 with Hackolade Studio models. It is is also possible to have a polyglot model that covers both conceptual and logical.\
  \
  ![PowerDesigner model migration to Hackolade](<lib/PowerDesigner model migration to Hackolade.png>)
- PowerDesigner uses the term "**subject area**" to divide model diagrams into logical sections and “package” to act as containers for objects. We have “[Diagram Views](DiagramViews.md)”. The purpose may be somewhat similar. Terminology, and how they function may be different
- PowerDesigner uses the term "**domain**", a term interpreted differently by different people, for sure to describe something quite different than what we describe as a [re-usable object definition](Reusableobjectsdefinitions.md) or user-defined type
- PowerDesigner has the concept called "**stereotypes**". A stereotype is a semantic classification mechanism, that is used to tag modeling objects (entities, tables, attributes, columns, etc.) in order to express meaning, role, or methodology-specific intent. It does not define data types or physical properties. Reverse-engineering copies the General Stereotype into the [custom property](Userdefinedcustomproperties.md) whose keyword is `stereotype`. If you want that value in the Details tab, declare the property as described in this [how-to guide](Configurecustomproperties.md), and [video](<https://community.hackolade.com/slides/slide/user-defined-custom-properties-8> "target=\"_blank\"").
- PowerDesigner has 3 object properties that are not built into Hackolade Studio: "**stereotypes**", "**keywords**", and "**annotations**". A stereotype is a semantic classification mechanism, used to tag modeling objects (entities, tables, attributes, columns, etc.) in order to express meaning, role, or methodology-specific intent. It does not define data types or physical properties. Keywords are free tags that loosely group objects. An annotation is a free text in the Notes tab of an object, usually a note about its implementation. You can add all 3 with [custom properties](Userdefinedcustomproperties.md), and adapt them to your own needs. When you reverse-engineer a PowerDesigner file, Hackolade Studio already fills these custom properties with your PowerDesigner values. You only have to declare them to display them in the Properties Pane, with the configuration given in the section Display imported stereotypes, keywords, and annotations further down this page.\
  \
  **Important**: in PowerDesigner, an annotation is a property of an object. In Hackolade Studio, an [annotation](Symbols.md) is a symbol: a box with free text that you place in the diagram, which corresponds to a PowerDesigner Note.
- In PowerDesigner,"**shortcuts**" maintain synchronization with their target objects, so changes to the original propagate to all shortcuts. They differ from replicas, which create independent copies. In Hackolade Studio, we call those [references](Reusableobjectsdefinitions.md) to existing objects (like entities or tables) in the same model, or a different saved data model, allowing reuse without duplication. When migrating PowerDesigner models to Hackolade Studio, the references must be recreated according to instructions detailed in [this page](Migrateexternalshortcuts.md).
- When **creating foreign key relationships** in PowerDesigner, the convention is that you drag from the attribute PK in the parent entity towards the child entity. The attribute is automatically created in the child entity and the FK relationship is also created. Hackolade Studio also supports this approach, but it is not the default behavior. To change the default to be like PowerDesigner, simply change the parameter "FK relationships drag-n-drop behavior" in Tools > Options > General to become "from parent to child".
- PowerDesigner allows arrows in relational ERDs [pointing to the parent entity](<https://infocenter-archive.sybase.com/help/index.jsp?topic=/com.sybase.stf.powerdesigner.docs_12.0.0/html/daug/daugp156.htm> "target=\"_blank\""). Hackolade Studio uses IE (Information Engineering) notation in ER diagrams, where cardinality symbols are used on both sides of relationships. In Graph Diagrams of Hackolade Studio, the arrow represents the semantic orientation of the of relationship, typically of the verb of the relationship. In conceptual modeling in Hackolade Studio, the arrow represents the direction of the active verb, and assumes a parent to child direction.
- PowerDesigner has a complex **model comparison** approach. With the [architecture of Hackolade Studio](WhylegacyandSaaSdatamodelingarch.md), models are in JSON format and are stored in Git repositories where versioning is automatic, and each commit and push results in an immutable version of the model. As a result, a [compare and merge](Compareandmergemodels.md) operation in Hackolade Studio always results in a "third" model, instead of an alteration of existing model versions. Note also that it is possible to [compare two arbitrary commits](<https://hackolade.com/help/Explorehistory.html#Compare%20commits>). Whatever the way PowerDesigner compares models, for sure, Hackolade Studio's equivalent feature will work completely differently.
- PowerDesigner allows to open **multiple models** in the same application instance. The architecture of Hackolade Studio being different, we allow to start **multiple instances of the application**, each with a single model. This is actually quite handy, as it allows to alt-tab to toggle between different models. As indicated in our [Tips and Tricks](Tipsandtricks.md), you may start multiple instances of Hackolade Studio on the same machine session, so as to work on multiple models simultaneously. You may also merge 2 Hackolade models, or combine elements from another model with copy/paste from one model in one application instance, to the other model in the second application instance. From within the application, this is easily done with the shortcut Ctrl+Shift+I (on Mac Cmd+Shift+I) or with the menu option File > Start New Application Instance. Or from the operating system, on Windows, right-click on the Hackolade icon in the toolbar then choose Hackolade...
- The [Generate property](<https://help.sap.com/docs/SAP_POWERDESIGNER/856348b84a7c479489d5172a630f014d/c7c99e6e6e1b1014999fba096ab22a45.html> "target=\"_blank\"") in PowerDesigner as a toggle switch on an object's property sheet to control whether or not that specific component is included when you create a new target model or output script. The equivalent in Hackolade Studio is a boolean property called Activated, and is enabled by default when creating an object. When it is disabled, the object is either commented in the generated script (if the target allows it) or removed from it entirely. During migration of PowerDesigner model into Hackolade Studio, if the Generate property is unchecked in the source file, Studio reverse-engineers that object as deactivated.
- PowerDesigner has a fairly rigid storage structure in its **central repository** structure. The architecture of our solution is very different from PowerDesigner’s. While PowerDesigner model files in XML format, they are stored in the repository in a structured database. Our files are open in JSON format, and each file represents a single model. Models can be stored in one or more Git repositories, possibly even across multiple repository providers. Models can be organized in a more flexible modular approach, as described [here](<https://hackolade.com/help/PolyglotDataModeling.html#Flexibility>). With our modular architecture, it is possible for a physical model to be derived from 1 or more (subsets of) polyglot models. It is also possible for any model to reference any part of any model, no matter the target on each side.

&nbsp;

Legacy tools have been using the traditional concept of “**logical**” models, which is too constraining for the needs of non-RDBMS targets supported by Hackolade Studio. Hackolade had to invent the principles of [Polyglot Data Modeling](https://hackolade.com/polyglot-data-modeling.html) to support the needs of NoSQL, Avro, Parquet, REST APIs, etc… We name it Polyglot, as opposed to logical, to avoid any semantic confusion or discussion. But our Polyglot models are logical in the sense that they are technology-agnostic, and they can be fully normalized. But they can be much more than strict logical models in the sense that they can optionally support nested objects, polymorphism, and denormalization.\
Polyglot models can be purely "logical", in the traditional sense. But they can also be more of a "common physical model", including technical names or views that would be common across different physical targets. No dogma with Hackolade: you can be as rigorous in applying data modeling theory as you wish, or less rigorous in order to adhere to the reality of your organization.

&nbsp;

Physical data models can be [derived from](PolyglotDataModel.md) polyglot models. It is also possible to start from a physical data model (either from scratch or created from the reverse-engineering of an instance) and convert it to a polyglot model.\
Once a target model is linked to one or more polyglot models, any change in the polyglot model can be reviewed through an [Impact Analysis](<https://hackolade.com/help/PolyglotDataModel.html#Impact%20Analysis>) screen to decide whether to include the changes, globally or individually.\
Polyglot models can be derived from (subsets of) other polyglot model(s), as described [here](<https://hackolade.com/help/PolyglotDataModeling.html#Flexibility>). In the end, it is possible to create a graph of models.

- In PowerDesigner when **creating a physical model** from a logical model, the physical model is "generated" (or "derived") from the logical model in a "**push**" process. In Hackolade Studio, the process is different, partly due to the fact that Hackolade Studio supports so many targets that are different than RDBMS. And also because in Hackolade Studio, it is possible to build an N-to-N graph of data models, where for example a model draws from more than one polyglot model. As a result in Hackolade Studio, the process follows a "**pull**" mechanism: you would first create a physical model for the target of our choice, then "derive" from the selected polyglot model or models.

&nbsp;

Given the above, it should be expected that there is some learning curve to our tool. You will most likely avoid frustration if you don't assume, because you're a veteran user of PowerDesigner, that you can use Hackolade Studio without learning about it. This learning curve can be greatly reduced by investing a little bit of time in reading or searching inside our [online documentation](WelcometoHackoladeStudio.md), going through [tutorials](Tutorial.md) and [how-to guides](How-toguides.md), and by watching some of the videos on our [eLearning platform](<https://community.hackolade.com/slides/all> "target=\"_blank\"").

&nbsp;

### Respective terminology

<table style="width:85%">
<colgroup><col style="width:33%"><col style="width:67%"></colgroup>
<thead>
<tr>
<th>Term in PowerDesigner</th>
<th>Term in Hackolade Studio</th>
</tr>
</thead>
<tbody>
<tr>
<td>Abstract data types (Physical only)</td>
<td>User-Defined Types</td>
</tr>
<tr>
<td>Annotation (Notes tab of an object)</td>
<td>Not built in. PowerDesigner Comment and Description map to two free-text properties of Hackolade Studio (see these rows). For a third free text, use a custom property: reverse-engineering already fills it with your PowerDesigner annotations, and you only have to [declare it](#) to display it. Not to be confused with the annotation symbol of Hackolade Studio (see Note).</td>
</tr>
<tr>
<td>Area (Conceptual &amp; Logical only)</td>
<td>Container</td>
</tr>
<tr>
<td>Check / Business rule</td>
<td><p>Check constraint</p><p>A native check on a table or column, and a business rule attached to a table or column that holds a server expression, both become a check constraint. A business rule with no server expression does not get imported.</p></td>
</tr>
<tr>
<td>Code</td>
<td>Technical name</td>
</tr>
<tr>
<td>Column (Physical only)</td>
<td>Target specific name (Column, Field, Attribute...)</td>
</tr>
<tr>
<td>Comment</td>
<td>Description in non-RDBMS target / Comment in RDBMS target</td>
</tr>
<tr>
<td>Conceptual, Logical model</td>
<td>Polyglot model</td>
</tr>
<tr>
<td>Data Item (Conceptual only)</td>
<td>Attribute</td>
</tr>
<tr>
<td>Data type</td>
<td>Type</td>
</tr>
<tr>
<td>Default value</td>
<td>Default value or Default option for numeric attributes</td>
</tr>
<tr>
<td>Description</td>
<td>Comment in non-RDBMS target / Remark in RDBMS target</td>
</tr>
<tr>
<td>(Conceptual/Logical/Physical) Diagram</td>
<td>Entity-Relationship Diagram View (ERDV)</td>
</tr>
<tr>
<td>Domain</td>
<td>User-Defined Types/Model Definitions</td>
</tr>
<tr>
<td>Entity (Conceptual &amp; Logical only)</td>
<td>Entity</td>
</tr>
<tr>
<td>Entity Attribute (Logical only)</td>
<td>Attribute</td>
</tr>
<tr>
<td>Extension/Extended attribute</td>
<td>Custom properties</td>
</tr>
<tr>
<td>Free symbol (Note, Rectangle, Text, etc.)</td>
<td>Symbol (annotation or rectangle)</td>
</tr>
<tr>
<td>High value</td>
<td>Max</td>
</tr>
<tr>
<td>Identifier</td>
<td>Primary key</td>
</tr>
<tr>
<td>Index</td>
<td>Index</td>
</tr>
<tr>
<td>Inheritance</td>
<td>Supertypes / Subtypes</td>
</tr>
<tr>
<td>Keywords</td>
<td>Not built in. You can tag objects with a custom property: reverse-engineering already fills it with your PowerDesigner keywords, and you only have to [declare it](#) to display it.</td>
</tr>
<tr>
<td>Length (character attributes)</td>
<td>Length</td>
</tr>
<tr>
<td>Length (numeric attributes)</td>
<td>Precision</td>
</tr>
<tr>
<td>List of values</td>
<td>Enumeration</td>
</tr>
<tr>
<td>Low value</td>
<td>Min</td>
</tr>
<tr>
<td>Mandatory</td>
<td>Required</td>
</tr>
<tr>
<td>Note (free symbol)</td>
<td>Annotation (symbol)</td>
</tr>
<tr>
<td>Object ID</td>
<td>GUID</td>
</tr>
<tr>
<td>Package</td>
<td><p>A PowerDesigner package is used to group modeling objects and the diagrams associated with them. Hackolade Studio takes a different approach: all modeling objects live at the model’s root level, without folder-like packages.</p><p>Organization is achieved through Entity Relationship Diagram Views (ERDVs), which let users create focused sub-views of the same unified model. In PowerDesigner, packages and diagrams are separate concepts; in Studio, ERDVs provide a simpler way to isolate or zoom in on specific parts of the model without duplicating structure</p></td>
</tr>
<tr>
<td>Precision</td>
<td>Scale</td>
</tr>
<tr>
<td>Relationship</td>
<td>Relationship</td>
</tr>
<tr>
<td>Shortcut</td>
<td>Reference</td>
</tr>
<tr>
<td>Stereotype</td>
<td>Not built in. You can classify objects with a custom property: reverse-engineering already fills it with your PowerDesigner stereotypes, and you only have to [declare it](#) to display it.</td>
</tr>
<tr>
<td>Table (Physical only)</td>
<td>Target specific name (Table, Collection, Entity...)</td>
</tr>
<tr>
<td>User (Physical only)</td>
<td>Target specific name (Database, Schema, Container...)</td>
</tr>
<tr>
<td>View</td>
<td>View</td>
</tr>
</tbody>
</table>

&nbsp;

## PowerDesigner conceptual models stored in .cdm files

Starting with v8.1.1

&nbsp;

Depending on the language used with PowerDesigner, the file extension could also be .cdb, .mcd, mcb, etc. The extension is not really important as long as the content is a PowerDesigner-generated XML file including

- tags starting with "o:" refer to an "object"
- tags starting with "a:" refer to an attribute/properties of the object "o:"
- tags starting with "c:" refer to a list of "objects" linked to the object "o:"

&nbsp;

It is natural to reverse-engineer or import a PowerDesigner logical model into a Hackolade Studio [polyglot model](PolyglotDataModel.md), Hackolade Studio's equivalent of traditional conceptual (with graph view) logical models, only more flexible and powerful.

&nbsp;

Inside PowerDesigner files, the different objects are mapped to equivalent objects in a Hackolade Studio models, mainly:

- entities;
- attributes and their data types (with length, precision, and scale where applicable), business and technical names, comments and descriptions;
- constraints: required or not null, unique keys, (composite) primary keys, and relationships with their cardinality.

&nbsp;

Some transformations occur, and extraneous information is ignored. We also import:

- ArchitectureAreas, and map them to containers,
- Inheritance, and map them to our supertypes and subtypes;
- ConceptualDiagrams, and map them to our Diagram Views;
- Shortcuts, and map them to references to their respective entities,
- Packages, and map them to our Diagram Views,
- ExtendedAttributes, and map them to our custom properties,
- Stereotype, Keywords, and Annotation values, and map them to dedicated custom properties,
- and DataItems mapped to attributes.

&nbsp;

To import a PowerDesigner logical model from the GUI application, you must first create a Polyglot data model. Ideally the polyglot model should be empty. But it does not have to be if, for example, you are merging 2 or more PowerDesigner files into a single Hackolade Studio model.

&nbsp;

Then go to Tools > Reverse-Engineer > PowerDesigner, and select the PowserDesigner file you wish to import:\
![Reverse-engineer or Import PowerDesigner model](<lib/Reverse-engineer or Import PowerDesigner mode.png>)

&nbsp;

## PowerDesigner logical data models stored in .ldm files

Depending on the language used with PowerDesigner, the file extension could also be .ldb, .mld, mlb, etc. The extension is not really important as long as the content is a PowerDesigner-generated XML file including

- tags starting with "o:" refer to an "object"
- tags starting with "a:" refer to an attribute/properties of the object "o:"
- tags starting with "c:" refer to a list of "objects" linked to the object "o:"

&nbsp;

It is natural to reverse-engineer or import a PowerDesigner logical model into a Hackolade Studio [polyglot model](PolyglotDataModel.md), Hackolade Studio's equivalent of traditional logical models, only more flexible and powerful.

&nbsp;

Inside PowerDesigner files, the different objects are mapped to equivalent objects in a Hackolade Studio models, mainly:

- entities;
- attributes and their data types (with length, precision, and scale where applicable), business and technical names, comments and descriptions;
- constraints: required or not null, unique keys, (composite) primary keys, foreign key relationships and their cardinality;
- views.

&nbsp;

Some transformations occur, and extraneous information is ignored. We also import:

- ArchitectureAreas, and map them to containers,
- Inheritance, and map them to our supertypes and subtypes;
- LogicalDiagrams, and map them to our Diagram Views;
- Shortcuts, and map them to references to their respective entities,
- Packages, and map them to our Diagram Views,
- ExtendedAttributes, and map them to our custom properties,
- and Stereotype, Keywords, and Annotation values, and map them to dedicated custom properties.

&nbsp;

To import a PowerDesigner logical model from the GUI application, you must first create a Polyglot data model. Ideally the polyglot model should be empty. But it does not have to be if, for example, you are merging 2 or more PowerDesigner files into a single Hackolade Studio model.

&nbsp;

Then go to Tools > Reverse-Engineer > PowerDesigner, and select the PowserDesigner file you wish to import:\
![Reverse-engineer or Import PowerDesigner model](<lib/Reverse-engineer or Import PowerDesigner mode.png>)

&nbsp;

## PowerDesigner physical data models stored in .pdm files

Starting with v7.9.10 for import into a polyglot model. Starting from v8.0.0 for import into a target model

&nbsp;

Depending on the language used with PowerDesigner, the file extension could also be .pdb, .mpd, mpb, etc. The extension is not really important as long as the content is a PowerDesigner-generated XML file including

- tags starting with "o:" refer to an "object"
- tags starting with "a:" refer to an attribute/properties of the object "o:"
- tags starting with "c:" refer to a list of "objects" linked to the object "o:"

&nbsp;

PowerDesigner physical models typically should be imported in into a Hackolade Studio of the corresponding target. However, Hackolade Studio is also able to convert to another target while converting data types, on a best effort basis, provided that the targets are fairly compatible. If the process encounters an unrecognized data type, it is mapped to the default data type, and a list of concerned attributes is made available in the log. If you think that we are not handling those correctly, please report it to [support@hackolade.com](mailto:support@hackolade.com) so we can enhance the standard application, for the benefit of all users.

&nbsp;

Inside PowerDesigner files, the different objects are mapped to equivalent objects in a Hackolade Studio models, mainly:

- containers (corresponding to the concept of the target: databases, schemas, namespaces, buckets, keyspace, etc...);
- entities (tables, collections, etc...);
- attributes (columns of fields) and their data types (with length, precision, and scale where applicable), business and technical names, comments and descriptions;
- constraints: required or not null, unique keys, (composite) primary keys, foreign key relationships and their cardinality, and check constraints;
- views.

&nbsp;

Some transformations occur, and extraneous information is ignored. We also import:

- ArchitectureAreas, and map them to containers,
- Inheritance, and map them to our supertypes and subtypes;
- LogicalDiagrams, and map them to our Diagram Views;
- Shortcuts, and map them to references to their respective entities,
- Packages, and map them to our Diagram Views,
- Indexes, as long as there is a match between the source technology and the Hackolade Studio target model,
- check constraints, from a native table or column check, and from an attached business rule with a server expression;
- database views,
- domains and [Abstract Data Types](<https://help.sap.com/docs/SAP_POWERDESIGNER/1f914d86319d43b7b2402532666583c0/b3e01e20f33f45699fe21f6e9fec9e21.html> "target=\"_blank\""),
- ExtendedAttributes, and map them to our custom properties,
- Stereotype, Keywords, and Annotation values, and map them to dedicated custom properties.

&nbsp;

If the target has no check property on the column, a column check is stored at the table level.

&nbsp;

To import a PowerDesigner physical model from the GUI application, you must first create a data model for the target of your choice. Ideally the target model should be empty. But it does not have to be if, for example, you are merging 2 or more PowerDesigner files into a single Hackolade Studio model.

&nbsp;

Then go to Tools > Reverse-Engineer > PowerDesigner, and select the PowerDesigner file you wish to import:\
![Reverse-engineer or Import PowerDesigner model](<lib/Reverse-engineer or Import PowerDesigner mode.png>)

&nbsp;

## Display imported stereotypes, keywords, and annotations

Stereotype, Keywords, and Annotation are standard properties of PowerDesigner objects. When you reverse-engineer a .cdm, .ldm, or .pdm file, Hackolade Studio records their values in custom properties of the model, containers, entities, attributes, and views, always with the same keywords:

- **Stereotype** (keyword stereotype): one line of text, from the General tab in PowerDesigner;
- **Keywords** (keyword migratedKeywords): a list with one item per PowerDesigner keyword, from the General tab;
- **Annotation** (keyword migratedAnnotation): a multi-line text, from the Notes tab.

&nbsp;

Extended attributes come from your own PowerDesigner extensions, so their names and types vary from one organization to the next. Stereotype, Keywords, and Annotation exist in every PowerDesigner model, and we provide their configuration below.

&nbsp;

The values are in the model as soon as the reverse-engineering is done. But the Properties Pane only displays a custom property after you declare it in the configuration of the target. Until you do, Hackolade Studio shows a custom tab with a warning badge, as explained in \[User-defined custom properties\](https://hackolade.com/help/Userdefinedcustomproperties.html).

&nbsp;

Declare the properties for the target of the model you imported into: Polyglot, or the physical target (Oracle, for example) if you imported a .pdm file into a model of that target. Go to Help > Plugin Manager > Installed, choose the target, and click the link Show plugin customization directory. In the browser application, use Tools > Options > Custom Properties instead. Our how-to guide \[Configure custom properties\](https://hackolade.com/help/Configurecustomproperties.html) walks through a complete example, also available as a \[video\](https://community.hackolade.com/slides/slide/user-defined-custom-properties-8).

&nbsp;

In modelLevelConfig.json, containerLevelConfig.json, and viewLevelConfig.json, paste this block inside the structure array of the Details tab, separated by a comma from any property already there:

&nbsp;

```json
{
  "propertyName": "Stereotype",
  "propertyKeyword": "stereotype",
  "propertyType": "text"
},
{
  "propertyName": "Annotation",
  "propertyKeyword": "migratedAnnotation",
  "propertyType": "details",
  "template": "textarea"
},
{
  "propertyName": "Keywords",
  "propertyKeyword": "migratedKeywords",
  "propertyType": "group",
  "structure": [
    {
      "propertyName": "Keyword",
      "propertyKeyword": "keyword",
      "propertyType": "text"
    }
  ]
}
```

&nbsp;

In entityLevelConfig.json, paste this block at the same place:

&nbsp;

```json
{
  "propertyName": "Stereotype",
  "propertyKeyword": "stereotype",
  "propertyType": "text",
  "enableForReference": true
},
{
  "propertyName": "Annotation",
  "propertyKeyword": "migratedAnnotation",
  "propertyType": "details",
  "template": "textarea",
  "enableForReference": true
},
{
  "propertyName": "Keywords",
  "propertyKeyword": "migratedKeywords",
  "propertyType": "group",
  "structure": [
    {
      "propertyName": "Keyword",
      "propertyKeyword": "keyword",
      "propertyType": "text"
    }
  ]
}
```

&nbsp;

In fieldLevelConfig.json, paste the same block as for entities, inside a Details tab whose structure is a plain array. Properties declared this way apply to all data types, next to any Details tab that lists properties per data type:

&nbsp;

```json
{
  "lowerTab": "Details",
  "structure": [
    paste the entity block here
  ]
}
```

&nbsp;

Save the files and restart Hackolade Studio, as the configuration is only read at startup. The 3 properties then appear at the bottom of the Details tab in the Properties Pane:

&nbsp;

![PowerDesigner stereotype-keyword-annotations](<lib/PowerDesigner stereotype-keyword-annotations.png>)

&nbsp;

In the entity and field level block, enableForReference is set to true for Stereotype and Annotation. You can then enter a Stereotype or an Annotation directly on a [reference to a definition](Reusableobjectsdefinitions.md), and Hackolade Studio uses that value instead of the value of the referenced definition.

&nbsp;

Currently, Hackolade Studio does not support enableForReference for a group property such as Keywords. On a reference, Hackolade Studio displays the Keywords of the referenced definition, and you cannot edit them there.

&nbsp;

## Known limitations

Currently, the following PowerDesigner features are not supported:

- links [between models](<https://help.sap.com/docs/SAP_POWERDESIGNER/abd3434b4987485c92057ab9392aadbe/c7e25fae6e1b1014a7948b49b3cdd8fa.html> "target=\"_blank\"")
- [XEM extension files](<https://help.sap.com/docs/SAP_POWERDESIGNER/31c48596e34446a68956e0aa7e700a2e/c7d31d216e1b1014ab88822700700793.html> "target=\"_blank\"")
- extended compositions
- [business rules](<https://help.sap.com/docs/SAP_POWERDESIGNER/abd3434b4987485c92057ab9392aadbe/c7dd23a26e1b1014a4afd4132cef9ef8.html?&version=16.6.5> "target=\"_blank\"")
- reports
- support for BPMN, UML, export of XML, etc...

&nbsp;

## Migrate PowerDesigner external shortcuts to Hackolade Studio external references

Please refer to these [step-by-step instructions](Migrateexternalshortcuts.md).

&nbsp;

## Bulk import

Using the [Command-Line Interface](CommandLineInterface.md), it is easy to orchestrate a batch import of selected PowerDesigner files into Hackolade Studio models, using the command revEngDiagram with its required and options arguments. If you need to import multiple PowerDesigner files, you must repeat the command.
