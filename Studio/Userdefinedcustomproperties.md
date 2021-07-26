# User-defined custom properties

For each object in Hackolade, we've defined a set of standard properties that appear in the properties pane.&nbsp; But it is possible that your organization wants to define and track its own metadata properties for models, containers, entities, and attributes.&nbsp; This could be for data governance reasons, and/or to leverage properties in code generation, etc...

&nbsp;

Hackolade lets create and maintain custom properties by editing JSON configuration files found in folders in C:\\Users\\%username%\\.hackolade\\options (on Mac in Users/$USER/.Hackolade/options) which can be Git-enabled to be shared across an organization if desired.

&nbsp;

**Warning:** For the changes to take effect, it is required to exit Hackolade and restart it.

&nbsp;

Customization for native targets (JSON, Couchbase, DynamoDB, and MongoDB) do not require to download a special plugin. &nbsp;

&nbsp;

## &#49;) Access the target customization directory

To create and maintain custom properties for a given target, you access the folder structure from Help \> Plugin Manager

&nbsp;

![Image](<lib/Plugin%20Manager%20menu%20new.png>)

&nbsp;

and choose the Installed tab:

![Image](<lib/Plugin%20Manager%20Installed%20tab.png>)

&nbsp;

then click on the Show plugin customization directory link for the chosen target.&nbsp; This link opens up a Windows Explorer or Mac Finder session in the corresponding folder.&nbsp; If the folder does not yet exist, it will be automatically created, along with all the necessary configuration files.

&nbsp;

For each custom properties plugin, you will find a directory structure similar to this one:

![Image](<lib/Plugin%20-%20Custom%20Prop%20-%20directory%20struc%20new.png>)

&nbsp;

**Notes:**&nbsp;

i)&nbsp; it is always necessary to restart the application after having saved changes, and before you can see these changes reflected in the properties pane.

ii) for field-level definitions, since data types have different property lists, it may be necessary to define custom properties for multiple data types.

&nbsp;

## &#50;) Levels

As a reminder, terminology differs between NoSQL databases:

\- container means: dbs in MongoDB, region in DynamoDB, and bucket in Couchbase, namespace in Avro, keyspace in Cassandra, etc...

\- entity means: collection in MongoDB, table in DynamoDB and Cassandra, and document kind in Couchbase,e tc...

\- field means: field in MongoDB and Couchbase, and attribute in DynamoDB, column in Cassandra, etc...

&nbsp;

You need to edit the corresponding \<object\>LevelConfig.json file to add custom properties.

&nbsp;

## &#51;) Lower tabs

For each level, the Hackolade properties pane may have one or more lower tab:

\- MongoDB model lower tab:

![Image](<lib/MongoDB%20model%20lower%20tab.png>)

\- MongoDB dbs lower tab:

![Image](<lib/MongoDB%20dbs%20lower%20tab.png>)

\- MongoDB collection lower tab:

![Image](<lib/MongoDB%20collection%20lower%20tab.png>)

\- MongoDB field lower tab:

![Image](<lib/MongoDB%20field%20lower%20tab.png>)

&nbsp;

If the level allows multiple tabs, you need to choose to which lower tab you want to add properties.

&nbsp;

## &#52;) Property types

The following controls are possible for user-defined properties:

![Image](<lib/Plugin%20-%20possible%20property%20types.png>)

![Image](<lib/Plugin%20-%20possible%20property%20types-drpdwn%20multi.png>)

* simple text: one line of text
* text area: popup for multi-line text entry
* dropdown selection (unique) from a defined list of options
* dropdown selection (multiple) from a defined list of options
* numeric-only field
* checkbox: for true/false entry
* group: addition of a set of properties of given control type
* field list: selection from list of fields
* field list with attributes: selection from list of fields with attributes

&nbsp;

More information [here](<https://github.com/hackolade/plugins#26-property-controls> "target=\"\_blank\"").

&nbsp;

## &#53;) Property definition

Examples are provided in the comments section of each config file.&nbsp; Here's an overview of the schema:

![Image](<lib/Plugin%20-%20property%20schema.png>)

Here's another view, consolidated:

![Image](<lib/Plugin%20-%20custom%20props%20consolidated%20schema.png>)

&nbsp;

\- propertyName: mandatory, this is the property label that will appear in the Property Pane

\- propertyKeyword: mandatory, this is the unique key for the property

\- shouldValidate: optional, boolean true/false to define whether to validate the regular expression of the text input \[default: false\]

\- propertyTooltip: optional, in the case of input types textarea and select, it is possible to display a tooltip&nbsp; defined here

\- propertyType: mandatory, this is the control definition, with possible values: text, details, select (i.e. dropdown), checkbox&nbsp;

\- options: optional, this is the array of possible checkbox options

\- template: optional, this is needed in the case of propertyType = details, to define a popup multi-line text.&nbsp; Possible value: textarea

\- valueType: optional, this is needed in to specify that a property is numberic only.&nbsp; Possible values: numeric

&nbsp;

## &#54;) Share customization with team members

it is recommended that you share customization using Git.&nbsp; Store your changes in a Git remote repository, and have your team members clone it locally in C:\\Users\\%username%\\.hackolade\\options (on Mac in Users/$USER/.Hackolade/options)&nbsp; That way, all that teams members need to do is to pull regularly, and they will get your latest changes.

&nbsp;

For the changes to take effect on each computer, it is required to exit Hackolade and restart it.

&nbsp;
