# Excel template

Reverse-Engineering of an Excel file pre-supposes that you have first performed forward-engineering of your existing model, as described [here](<Excelfile.md>).&nbsp; If you plan to import a new model, you at least need to export an empty model for the same target.

&nbsp;

**WARNINGS**:

\- Do not change the titles or order of the columns\!&nbsp;

\- Referential integrity is not enforced by this template.&nbsp; You need to ensure the coherence of the references from one tab to the other\!

&nbsp;

To import CSV files into Hackolade, it is advised to go first export an Excel template, then link it to the CSV file, before importing back into Hackolade.

&nbsp;

To import the content of this Excel, use the Hackolade function Tools \> Reverse-Engineering \> Excel template

&nbsp;

![Image](<lib/Tools%20-%20Reverse-Engineer%20-%20Excel%20Template.png>)

&nbsp;

&nbsp;

Assuming that the user has not altered the integrity of the exported Excel file (i.e. GUIDs or column names), the following behavior occurs:

* when applied to an open model, and provided that the target and GUID of the model match, the information in the imported Excel file is processed as an update/insert to the existing model.&nbsp; If applied to a new model, the entire imported Excel is processed as an insert;
* based on a given GUID, the property values imported write over the existing ones.&nbsp; This includes writing over empty values, or non-empty values.&nbsp; It also includes deleting values when the value imported has been nulled.&nbsp; Properties not imported leave untouched their existing value;
* an object (model, container, entity, or attribute) with no GUID will be created, ideally inserted in the proper order;
* the creation of complex structures is supported, as long as dot notation is used in the imported Excel file.&nbsp; Multiple data types are supported as well, as long as the \| separator is used and the data types correspond to the acceptable values.&nbsp; This can be a bit tricky though, e.g. {"id":"c973c0a0-7e84-11e9-9a55-eba2b9bb390e","type":"string","enum":\["user","owner","tester"\]} \| {"id":"d7cd4e50-7e84-11e9-9a55-eba2b9bb390e","type":"null"} \| {"id":"cbd7a140-7e84-11e9-9a55-eba2b9bb390e","type":"numeric","minimum":"","exclusiveMinimum":false,"maximum":"", "exclusiveMaximum":false,"multipleOf":"","unit":""}
* a new GUID is generated for each new object, or for an object for which the GUID is not recognized.

&nbsp;

So as to not create instability or any kind of model corruption at time of import of the Excel, it is first scanned for the following validations:

* the import is rejected if the target of the Excel file does not match the target of the open or new model;
* there can be only one line (other than the title line) in the model tab;
* for each target, we can only import if the tab names match the acceptable values;
* a column name (property) does not have to be marked for export in the config to be usable in the Excel import, as long as it is a valid “propertyName”;
* an attribute line referencing an entity not present in the entities tab cannot be imported.&nbsp; Similarly, an entity referencing a container not present in the containers tab cannot be imported.&nbsp; And a container referencing a model not present in the model tab cannot be imported;
* unknown property value: we can only accept valid values as previously exported and visible in the last tab "Lists".

&nbsp;

If validation is successful, the following message is displayed:

![Image](<lib/Excel%20RE%20validation%20-%20Success.png>)

&nbsp;

But if things don't validate properly, you may get a message such as this one:

![Image](<lib/Excel%20RE%20validation%20-%20error.png>)

&nbsp;

## For advanced users ##

Most users will use this Excel export/import feature for a productive manner to edit bulk data for a model, but without changing the structure of the model itself.&nbsp; The feature allows much more:

### &#49;) Add an scalar attribute to an existing entity ###

This is the simplest use case.&nbsp; In the "entity attributes" tab (which could be named "Collection fields", or "Table columns, etc... depending on the target), simply insert a blank line where you want the attribute to appear in the model.&nbsp; You should note the following:

\- the GUID of an attribute is the unique number used internally by Hackolade.&nbsp; For an existing attribute being modified, this MUST NOT change, as it is the key used for matching upon import.&nbsp; For a new attribute, the cell should be left blank.

\- the Name column uses "dot notation", starting with the name of the entity (table, collection,...) If you want to add an attribute "firstName" to an entity "users", you would enter *users.firstName* in the Name cell.&nbsp; Spaces are allowed and do not require quotes or encoding.

\- the Entity ID represents the GUID of the entity.&nbsp; It is required to add the attribute to the correct entity.&nbsp; Note that if there is an incoherence between the entity name in the Name cell and the Entity ID, it is the latter that is being used during reverse-engineering.

\- make sure to choose the data Type from the dropdown box

### &#50;) Add a complex attribute (object) to an existing entity ###

To add a nested object, itself made of attributes, you can extent the dot notation in the Name cells.&nbsp; For example to add an address object to a user entity, you would create/insert:

\- one line for the object, for example *user.address* with a data type *object* (or document or map, depending on the target)

![Image](<lib/Excel%20-%20object.png>)

\- a line per attribute of the object, for example:

![Image](<lib/Excel%20-%20Object%20attributes.png>)

while following the guidelines in 1) above.&nbsp; Nesting can go several levels deep, within the limits of each target.

&nbsp;

### &#51;) Add a complex attribute (array) to an existing entity ###

For arrays, the same dot notation is supported.&nbsp; For example to add an array of friends to a user entity, you would create/insert:

\- one line for the array, for example *user.friends* with a data type *array* (or list of set, depending on the target)

\- one line for the array item, with the data type of the item&nbsp; Array items don't have names.

![Image](<lib/Excel%20-%20Array.png>)

&nbsp;

Note that you can combine objects and arrays, for example *users.addresses.\[0\].address.street*

### &#52;) Add an attribute with multiple data types ###

If this form of polymorphism is allowed by the target, you may do so from the Excel template.&nbsp; The easiest way to understand how to do it might be to first create a multiple type attribute in Hackolade, then export to Excel.&nbsp; Then you can mimic the syntax.&nbsp; The separator between types is a pipe ("\|").&nbsp; The GUID is repeated:

&nbsp;

{

&nbsp; &nbsp; "id": "c973c0a0-7e84-11e9-9a55-eba2b9bb390e",

&nbsp; &nbsp; "type": "string",

&nbsp; &nbsp; "enum": \["user", "owner", "tester"\]

}

&nbsp; &nbsp; \|&nbsp;

{

&nbsp; &nbsp; "id": "d7cd4e50-7e84-11e9-9a55-eba2b9bb390e",

&nbsp; &nbsp; "type": "null"

}

&nbsp; &nbsp; \|&nbsp;

{

&nbsp; &nbsp; "id": "cbd7a140-7e84-11e9-9a55-eba2b9bb390e",

&nbsp; &nbsp; "type": "numeric",

&nbsp; &nbsp; "minimum": "",

&nbsp; &nbsp; "exclusiveMaximum": false,

&nbsp; &nbsp; "maximum": "",

&nbsp; &nbsp; "exclusiveMinimum": false,

&nbsp; &nbsp; "mode": "",

&nbsp; &nbsp; "multipleOf": "",

&nbsp; &nbsp; "sample": "",

&nbsp; &nbsp; "unit": ""

}

&nbsp;

### &#53;) Add a new entity ###

In the Entities tab (which could be names "Collections", "Tables", etc... depending on the target), simply insert a blank line for the entity.&nbsp; You should note the following:

\- the GUID of an entity is the unique number used internally by Hackolade.&nbsp; For an existing entity being modified, this MUST NOT change, as it is the key used for matching upon import.&nbsp; For a new entity, the cell should be left blank.

\- the Entity ID represents the GUID of the Container (database/bucket/keyspace/workspace/...) to which this entity belongs.&nbsp; This is required in order to link the entity to the correct container. &nbsp;

&nbsp;

### &#54;) Add a definition ###

Only internal and model definitions can be edited in an Excel having been exported.&nbsp; If you need to make modifications to an external definition, it is required to export that model separately.

&nbsp;

Internal and model definitions are exported in a separate tab, generally called Definitions (for Cassandra it is User-Defined Types, etc...) attributes can be edited or inserted just like any other attribute (cfr points 1 thru 4 above.)

&nbsp;

### &#55;) Add a reference to a definition ###

To create a reference to a definition requires an entry in the $ref cell:

\- model reference: #model/definitions/\<definitionName\>

\- internal reference: #/definitions/\<defintionName\>

\- external reference: \<drive\>:\<path\>/\<modelFileName\>.json#/\<attributeName\>

### &#56;) Add a relationship ###

Relationships go into their own tab.&nbsp; They have their own GUID as well.&nbsp; If adding a new one, leave the GUID cell blank.&nbsp; Each relationship needs the GUID of:

\- parent entity

\- parent attribute

\- child entity

\- child attribute

&nbsp;

They also have a relationship type: foreign key, or foreign master.


***
_Created with the Personal Edition of HelpNDoc: [Free Qt Help documentation generator](<https://www.helpndoc.com>)_
