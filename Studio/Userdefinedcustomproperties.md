# User-defined custom properties

For each object in Hackolade Studio, we've defined a set of standard properties that appear in the properties pane.&nbsp; But it is possible that your organization wants to define and track its own metadata properties for models, containers, entities, and attributes.&nbsp; This could be for data governance reasons, and/or to leverage properties in code generation, etc...&nbsp;

&nbsp;

Hackolade Studio provides a no-code approach: you can create and maintain custom properties simply by editing JSON configuration files. If desired, you can version those files in a version control system and share them across your organization. We recommend the use of Git as it is a lever for enabling [team collaboration](<Teamcollaboration.md>) using the Workgroup edition of Hackolade Studio.

&nbsp;

The values you record in custom properties are stored in the model file and are naturally exposed in documentation, JSON Schema (in full and extended compliance), Excel exports.

&nbsp;

The location of the JSON configuration files depends on your environment:

\- If you use the browser application, you can download template files from *Tools \> Options \> Custom Properties*. You can then edit those files and (re-)load them into the application.

\- If you use the desktop application on Windows, you can find the JSON files in C:\\Users\\%username%\\.hackolade\\options. You can edit those files in-place.

\- If you use the desktop application on MacOS, you can find the JSON files in /Users/$USER/.hackolade/options. You can edit those files in-place.

&nbsp;

**Warning:** whatever your environment, you need to restart / reload the application for configuration changes to take effect\!

Note that native targets (aka JSON, Couchbase, DynamoDB, MongoDB, and Polyglot) can be customized without downloading additional plugins. &nbsp;

&nbsp;

## Access the target customization directory

### Desktop deployment

To create and maintain custom properties for a given target, you access the folder structure from Help \> Plugin Manager

&nbsp;

![Plugin Manager menu new](<lib/Plugin%20Manager%20menu%20new.png>)

&nbsp;

&nbsp;

&nbsp;

and choose the Installed tab:

![Plugin Manager Installed tab](<lib/Plugin%20Manager%20Installed%20tab.png>)

&nbsp;

then click on the Show plugin customization directory link for the chosen target.&nbsp; This link opens up a Windows Explorer or Mac Finder session in the corresponding folder.&nbsp; If the folder does not yet exist, it will be automatically created, along with all the necessary configuration files.

&nbsp;

For each custom properties plugin, you will find a directory structure similar to this one:

&nbsp;

![Plugin - Custom Prop - directory struc new](<lib/Plugin%20-%20Custom%20Prop%20-%20directory%20struc%20new.png>)

&nbsp;

**Notes:**&nbsp;

i)&nbsp; it is always necessary to restart the application after having saved changes, and before you can see these changes reflected in the properties pane.

ii) for field-level definitions, since data types have different property lists, it may be necessary to define custom properties for multiple data types.

&nbsp;

When you open a *xLevelConfig.json* file, it starts with a section showing examples of how different controls are structured.&nbsp; Then at the end, you find the section where changes are made:

![Custom properties - empty config](<lib/Custom%20properties%20-%20empty%20config.png>)

&nbsp;

It is an array of objects, themselves containing and array of control objects.

&nbsp;

Adding control objects inside the structure array of Details would add custom properties at the bottom the of the Details tab in the Properties Pane.&nbsp; If you want to define a custom tab, it would be by adding an object in the array:

![Custom properties - custom tab](<lib/Custom%20properties%20-%20custom%20tab.png>)

&nbsp;

To add a control object, copy from one of the examples at the top of the file, and paste it in the right place, for example:

![Custom properties - custom tab custom control](<lib/Custom%20properties%20-%20custom%20tab%20custom%20control.png>)

&nbsp;

If you need to add a custom property to a data type, but not to all data types, you must do it under the data type specific to the technology target:

![Custom properties - field level control](<lib/Custom%20properties%20-%20field%20level%20control.png>)

&nbsp;

### Browser deployment

Given the security requirements browsers, the user experience is quite different.&nbsp; In the browser application, go to *Tools \> Options \> Custom Properties*.

&nbsp;

&nbsp;

![Plugin - Custom Prop - template files](<lib/Plugin%20-%20Custom%20Prop%20-%20template%20files.png>)

&nbsp;

#### You run both the Desktop and the Browser deployments of Hackolade Studio

No need to download any template file if you want to share the same setup of custom properties with the Desktop application (recommended.)

&nbsp;

For each target technology, you must select the folder previously created with the Desktop application.&nbsp; This will typically be:

\- on Windows: C:\\Users\\%username%\\.hackolade\\options\\\<target\>\\customProperties

\- on Mac: /Users/$USER/.hackolade/options/\<target\>/customProperties (note: use Cmd+. to display hidden folders)

&nbsp;

Each time you make changes to the custom properties config files, you must reload the browser page.

&nbsp;

#### You only run Hackolade Studio in the browser

Download the template file (zip file) by clicking the link provided.&nbsp; For each target, you must create a folder structure based on the zip file containing structure and templates.&nbsp; You must unzip the archive, and we suggest to store it all under:

\- on Windows: C:\\Users\\%username%\\.hackolade\\options\\\<target\>\\customProperties

\- on Mac: /Users/$USER/.hackolade/options/\<target\>/customProperties (note: use Cmd+. to display hidden folders)

&nbsp;

You may then edit the files according the instructions below.&nbsp; Once you are done editing those files, you need to load them in the application using the directory picker. Note that your configuration remains local to your machine: the JSON files are persisted in your browser and restored across sessions but they are never sent to a remote server.

&nbsp;

&nbsp;

![Image](<lib/Plugin%20-%20Custom%20Prop%20-%20folder%20loaded.png>)

## Levels

As a reminder, terminology differs between the targets supported by Hackolade:

\- container means: dbs in MongoDB, region in DynamoDB, and bucket in Couchbase, namespace in Avro, keyspace in Cassandra, schema in RDBMS, etc...

\- entity means: collection in MongoDB, table in DynamoDB and Cassandra and RDBMS, and document type in Couchbase,e tc...

\- field means: field in MongoDB and Couchbase, and attribute in DynamoDB, column in Cassandra and RDBMS, etc...

&nbsp;

You need to edit the corresponding \<object\>LevelConfig.json file to add custom properties.

&nbsp;

## Tabs

**Note:** tabs in Properties Panes were originally placed at the bottom.&nbsp; To make them more visible, they were subsequently moved to the top. &nbsp;

&nbsp;

For each level, the Hackolade properties pane may have one or more lower tab:

\- MongoDB model tab:

![MongoDB model lower tab](<lib/MongoDB%20model%20lower%20tab.png>)

\- MongoDB dbs tab:

![MongoDB dbs lower tab](<lib/MongoDB%20dbs%20lower%20tab.png>)

\- MongoDB collection tab:

![MongoDB collection lower tab](<lib/MongoDB%20collection%20lower%20tab.png>)

\- MongoDB field&nbsp; tab:

![MongoDB field lower tab](<lib/MongoDB%20field%20lower%20tab.png>)

&nbsp;

If the level allows multiple tabs, you need to choose to which tab you want to add properties.

&nbsp;

## Property types

The following controls are possible for user-defined properties:

&nbsp;

![Plugin - possible property types](<lib/Custom%20Props%20controls.png>)

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

## Property definition

Examples are provided in the comments section of each config file.&nbsp; Here's an overview of the schema:

![Plugin - property schema](<lib/Plugin%20-%20property%20schema.png>)

Here's another view, consolidated:

![Plugin - custom props consolidated schema](<lib/Plugin%20-%20custom%20props%20consolidated%20schema.png>)

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

## Share customization with team members

it is recommended that you share customization using Git.&nbsp; Store your changes in a Git remote repository, and have your team members clone it locally in C:\\Users\\%username%\\.hackolade\\options (on Mac in Users/$USER/.Hackolade/options)&nbsp; That way, all that teams members need to do is to pull regularly, and they will get your latest changes.

&nbsp;

For the changes to take effect on each computer, it is required to exit Hackolade and restart it.

&nbsp;

## Models with custom properties lacking configuration

It is possible that you might be opening a model in which some custom properties were recorded, and and for which you don't have the configuration.&nbsp; In such case, we display a custom tab with a warning badge to alert you of this situation.

![Image](<lib/Custom%20props%20lacking%20configuration.png>)

&nbsp;

You may have to synchronize or pull the latest version of the custom configuration, or adjust your configuration to match the custom properties in the model.

