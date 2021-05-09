# Old user-defined custom properties

For each object in Hackolade, we've defined a set of standard properties that appear in the properties pane.&nbsp; But it is possible that your company wants to define and track additional properties for models, containers, entities, and attributes.&nbsp; Hackolade lets you do just that, by leveraging our plugin architecture (used also to integrate our modeling engine with all kinds of NoSQL document databases.)

&nbsp;

## &#49;) Download and enable plugin ##

To enable the custom properties capability, you first need to download a plugin for each database target for which you wish to add properties.&nbsp; To do so, go to Help \> Plugin Manager

![Image](<lib/Plugin%20Manager%20menu.png>)

&nbsp;

You may choose which plugin to install on your computer.

![Image](<lib/Plugin%20-%20manager%20available%20custom%20props.png>)

&nbsp;

This will result in the plugin appearing in the Installed tab of the plugin manager.

![Image](<lib/Plugin%20-%20Manager%20installed%20custom%20props.png>)

&nbsp;

## &#50;) Access plugin configuration files ##

You are now ready to add custom properties via editing of configuration files.&nbsp; The plugin configurations files can be found by going to Help \> Show plugin directory:

![Image](<lib/Plugin%20-%20Show%20plugin%20directory.png>)

&nbsp;

&nbsp;

For each custom properties plugin, you will find the a directory structure similar to this one:

![Image](<lib/Plugin%20-%20Custom%20Prop%20-%20directory%20structure.png>)

**Notes:**&nbsp;

i) do NOT make any changes to the package.json file\!&nbsp; Only the \<object\>LevelConfig.json files should be edited according to the specifications below.

ii) it is advised to keep a backup of the files before making changes, so you can revert back in case of errors.

iii) it is always necessary to restart the application after having saved changes before you can see these changes relected in the properties pane.

iv) for field-level definitions, since field types have different property lists, it may be necessary to define custom properties for multiple field types.

## &#51;) Levels ##

As a reminder, terminology differs between NoSQL database:

\- container means: dbs in MongoDB, region in DynamoDB, and bucket in Couchbase

\- entity means: collection in MongoDB, table in DynamoDB, and document kind in Couchbase

\- field means: field in MongoDB and Couchbase, and attribute in DynamoDB

&nbsp;

You need to edit the corresponding \<object\>LevelConfig.json file to add custom properties.

&nbsp;

## &#52;) Lower tabs ##

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

## &#53;) Property types ##

The following controls are possible for user-defined properties:

![Image](<lib/Plugin%20-%20possible%20property%20types.png>)

* simple text: one line of text
* text area: popup for multi-line text entry
* dropdown selection from a deined list of options
* numeric-only field
* checkbox: for true/false entry
* group: addition of a set of properties of given control type
* field list: selection from list of fields
* field list with attributes: selection from list of fields with attributes

&nbsp;

More information [here](<https://github.com/hackolade/plugins#26-property-controls> "target=\"\_blank\"").

&nbsp;

## &#54;) Property definition ##

Examples are provided in the comments section of each config file.&nbsp; Here's an overview of the schema:

![Image](<lib/Plugin%20-%20property%20schema.png>)

Here's another view, consolidated:

![Image](<lib/Plugin%20-%20custom%20props%20consolidated%20schema.png>)

\- propertyName: mandatory, this is the property label that will appear in the Property Pane

\- propertyKeyword: mandatory, this is the unique key for the property

\- shouldValidate: optional, boolean true/false to define whether to validate the regular expression of the text input \[default: false\]

\- propertyTooltip: optional, in the case of input types textarea and select, it is possible to display a tooltip&nbsp; defined here

\- propertyType: mandatory, this is the control definition, with possible values: text, details, select (i.e. dropdown), checkbox&nbsp;

\- options: optional, this is the array of possible checkbox options

\- template: optional, this is needed in the case of propertyType = details, to define a popup multi-line text.&nbsp; Possible value: textarea

\- valueType: optional, this is needed in to specify that a property is numberic only.&nbsp; Possible values: numeric

&nbsp;

## &#55;) Share customization with team members ##

After making, saving, and testing your changes, you should share them with everyone on your team to insure consistency. This is a 3-step process:

\- return to the plugin directory via Help \> Show plugin directory, and zip up the **whole** plugin directory where you made your changes;

\- transfer this zip file to each team member using Hackolade;

\- on each team member's computer, start Hackolade, go to Help \> DB target plugin manager, then click the button 'Install from zip file', and choose the zip file file. &nbsp;

&nbsp;

&nbsp;

For the changes to take effect on each computer, it is required to exit Hackolade and restart it.


***
_Created with the Personal Edition of HelpNDoc: [Easy CHM and documentation editor](<https://www.helpndoc.com>)_
