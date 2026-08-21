# Pre-populate properties with default values

Hackolade Studio allows to define default values for specific properties such as view names, index names, or constraint names through a configuration file.&nbsp; This equates to what other tools often accomplish with macros or scripting.

&nbsp;

These defaults are defined in the defaultData.json configuration file in each plugin, at .hackolade/OPTIONS/\<target\>/customProperties/properties\_pane.&nbsp; You can easily access that location via Help \> Plugin Manager and then "Show plugin customization directory.":

&nbsp;

When configured, the default value is automatically applied at the time of object creation.&nbsp; For example, when creating a new index or constraint, Hackolade Studio assigns the configured default value to the corresponding property.

&nbsp;

This mechanism is intentionally static and non-dynamic:

* the default value is applied only once, during creation.
* if the property is manually modified afterward, Studio does not override it.

&nbsp;

This behavior is designed to prevent unintended overwrites and avoid conflicts with user customizations.

&nbsp;

## Example of defaultData.json

THes list below is comprehensive.&nbsp; Not all options may be relevant in your case.&nbsp; You may select a subset of the example below, and configure for your specific needs.

&nbsp;

For example, with the configuration below:

* for each level (model, container/schema, entity/table/collection, attribute/column/filed, relationships, and view), generate as default:

  * a business name
  * a technical name with the respective prefix MODEL\_, S\_, T\_, F\_, V\_, FK\_

* an index gets \_IDX as its default name
* a check constraint gets \_CC as its default constraint name
* a composite primary key gets \_PK as its default constraint name
* a composite unique key gets \_UK as its default constraint name
* a NOT NULL constraint on a field gets \_NN as its default name
* a single unique key gets \_SUK as its default constraint name
* a single primary key gets \_SPK as its default constraint name

&nbsp;

These values are fixed prefixes or suffixes defined in advance. They are not dynamically derived from contextual properties such as entity name or attribute name.&nbsp;

&nbsp;

For example, a NOT NULL constraint created on a field with types value customer\_id will receive \_NN, not customer\_id\_NN.

&nbsp;

For foreign key relationships, the value shown here (FK\_) corresponds to the static default defined in defaultData.json when a foreign key relationship is not created by drag-and-drop. A more advanced, pattern-based configuration is available and described in the dedicated section below.

​

> {\
&nbsp; &nbsp; "model": {\
&nbsp; &nbsp; &nbsp; &nbsp; "modelName": "My model",\
&nbsp; &nbsp; &nbsp; &nbsp; "code": "MODEL\_"\
&nbsp; &nbsp; },\
&nbsp; &nbsp; "container": {\
&nbsp; &nbsp; &nbsp; &nbsp; "name": "My schema",\
&nbsp; &nbsp; &nbsp; &nbsp; "code": "S\_",\
&nbsp; &nbsp; &nbsp; &nbsp; "synonyms": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "synonymName": "\_SYN"\
&nbsp; &nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; &nbsp; "sequences": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "sequenceName": "\_SEQ"\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; },\
&nbsp; &nbsp; "collection": {\
&nbsp; &nbsp; &nbsp; &nbsp; "collectionName": "My table",\
&nbsp; &nbsp; &nbsp; &nbsp; "code": "T\_",\
&nbsp; &nbsp; &nbsp; &nbsp; "Indxs": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "indxName": "\_IDX"\
&nbsp; &nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; &nbsp; "chkConstr": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "chkConstrName": "\_CC"\
&nbsp; &nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; &nbsp; "primaryKey":{\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "constraintName": "\_PK"\
&nbsp; &nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; &nbsp; "uniqueKey":{\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "constraintName": "\_UK"\
&nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; },\
&nbsp; &nbsp; "view": {\
&nbsp; &nbsp; &nbsp; &nbsp; "name": "My view",\
&nbsp; &nbsp; &nbsp; &nbsp; "code": "V\_"\
&nbsp; &nbsp; },\
&nbsp; &nbsp; "relationship": {\
&nbsp; &nbsp; &nbsp; &nbsp; "name": "My relationship",\
&nbsp; &nbsp; &nbsp; &nbsp; "code": "FK\_"\
&nbsp; &nbsp; },\
&nbsp; &nbsp; "field": {\
&nbsp; &nbsp; &nbsp; &nbsp; "name": "My column",\
&nbsp; &nbsp; &nbsp; &nbsp; "code": "F\_",\
&nbsp; &nbsp; &nbsp; &nbsp; "notNullConstraintName": "\_NN",\
&nbsp; &nbsp; &nbsp; &nbsp; "uniqueKeyOptions": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "constraintName": "\_SUK"\
&nbsp; &nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; &nbsp; "primaryKeyOptions": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "constraintName": "\_SPK"\
&nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; }\
}

&nbsp;

**Note** that this static approach may not be ideal if you have Naming Conventions enabled.

## Advanced naming for foreign key relationships created by drag-and-drop

In addition to the static default value defined in defaultdata.json, foreign key relationships support a advanced flexible naming mechanism when created via drag and drop.

&nbsp;

In Tools \> Options, a naming pattern can be defined using predefined keywords. The following variables are supported:

* \<parentEntity\>
* \<parentAttribute\>
* \<childEntity\>
* \<childAttribute\>

&nbsp;

These keywords allow composing a relationship name dynamically based on the actual modeling context. For example, a pattern such as:&nbsp;

&nbsp;

> FK\_\<childEntity\>\_\<parentEntity\>

&nbsp;

would generate a name derived from the involved entities at creation time.

&nbsp;

This dynamic naming mechanism applies only when the relationship is created via drag and drop, and only at initialization time. After creation, the name behaves like any other property and is not automatically updated if the model changes.

&nbsp;

![Tools - Options - General - FK relationship name](<lib/Tools - Options - General - FK rel name.png>)

&nbsp;

