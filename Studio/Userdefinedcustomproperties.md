# User-defined custom properties

For each object in Hackolade Studio, we've defined a set of standard properties that appear in the properties pane.&nbsp; But it is possible that your organization wants to define and track its own metadata properties for models, containers, entities, and attributes.&nbsp; This could be for data governance reasons, and/or to leverage properties in code generation, etc...&nbsp;

&nbsp;

Hackolade Studio exposes the different controls of Properties panes to provides a no-code approach: you can create and maintain custom properties, even custom tabs, simply by editing JSON configuration files.&nbsp; If desired, you can version those files in a version control system and share them across your organization. We recommend the use of Git as it is a lever for enabling [team collaboration](<Teamcollaboration.md>) using the Workgroup edition of Hackolade Studio.

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

![Plugin Manager menu new](<lib/Plugin Manager menu new.png>)

&nbsp;

&nbsp;

&nbsp;

and choose the Installed tab:

![Plugin Manager Installed tab](<lib/Plugin Manager Installed tab.png>)

&nbsp;

then click on the Show plugin customization directory link for the chosen target.&nbsp; This link opens up a Windows Explorer or Mac Finder session in the corresponding folder.&nbsp; If the folder does not yet exist, it will be automatically created, along with all the necessary configuration files.

&nbsp;

For each custom properties plugin, you will find a directory structure similar to this one:

&nbsp;

![Plugin - Custom Prop - directory struc new](<lib/Plugin - Custom Prop - directory struc new.png>)

&nbsp;

**Notes:**&nbsp;

i)&nbsp; it is always necessary to restart the application after having saved changes, and before you can see these changes reflected in the properties pane.

ii) for field-level definitions, since data types have different property lists, it may be necessary to define custom properties for multiple data types.

&nbsp;

When you open a *xLevelConfig.json* file, it starts with a section showing examples of how different controls are structured.&nbsp; Then at the end, you find the section where changes are made:

![Custom properties - empty config](<lib/Custom properties - empty config.png>)

&nbsp;

It is an array of objects, themselves containing and array of control objects.

&nbsp;

Adding control objects inside the structure array of Details would add custom properties at the bottom the of the Details tab in the Properties Pane.&nbsp; If you want to define a custom tab, it would be by adding an object in the array:

![Custom properties - custom tab](<lib/Custom properties - custom tab.png>)

&nbsp;

To add a control object, copy from one of the examples at the top of the file, and paste it in the right place, for example:

![Custom properties - custom tab custom control](<lib/Custom properties - custom tab custom control.png>)

&nbsp;

If you need to add a custom property to a data type, but not to all data types, you must do it under the data type specific to the technology target:

![Custom properties - field level control](<lib/Custom properties - field level control.png>)

&nbsp;

### Browser deployment

Given the security requirements browsers, the user experience is quite different.&nbsp; In the browser application, go to *Tools \> Options \> Custom Properties*.

&nbsp;

&nbsp;

![Plugin - Custom Prop - template files](<lib/Plugin - Custom Prop - template files.png>)

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

![Image](<lib/Plugin - Custom Prop - folder loaded.png>)

## Levels

As a reminder, terminology differs between the targets supported by Hackolade:

\- container means: dbs in MongoDB, region in DynamoDB, and bucket in Couchbase, namespace in Avro, keyspace in Cassandra, schema in RDBMS, etc...

\- entity means: collection in MongoDB, table in DynamoDB and Cassandra and RDBMS, and document type in Couchbase,etc...

\- field means: field in MongoDB and Couchbase, and attribute in DynamoDB, column in Cassandra and RDBMS, etc...

&nbsp;

You need to edit the corresponding \<object\>LevelConfig.json file to add custom properties.

&nbsp;

## Tabs

**Note:** tabs in Properties Panes were originally placed at the bottom.&nbsp; To make them more visible, they were subsequently moved to the top. &nbsp;

&nbsp;

For each level, the Hackolade properties pane may have one or more lower tab:

\- MongoDB model tab:

![MongoDB model lower tab](<lib/MongoDB model lower tab.png>)

\- MongoDB dbs tab:

![MongoDB dbs lower tab](<lib/MongoDB dbs lower tab.png>)

\- MongoDB collection tab:

![MongoDB collection lower tab](<lib/MongoDB collection lower tab.png>)

\- MongoDB field&nbsp; tab:

![MongoDB field lower tab](<lib/MongoDB field lower tab.png>)

&nbsp;

If the level allows multiple tabs, you need to choose to which tab you want to add properties.

&nbsp;

## Property types

The following controls are possible for user-defined properties:

&nbsp;

![Plugin - possible property types](<lib/Custom Props controls.png>)

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

![Plugin - property schema](<lib/Plugin - property schema.png>)

Here's another view, consolidated:

![Plugin - custom props consolidated schema](<lib/Plugin - custom props consolidated schema.png>)

&nbsp;

\- propertyName: mandatory, this is the property label that will appear in the Property Pane

\- propertyKeyword: mandatory, this is the unique key for the property

\- shouldValidate: optional, boolean true/false to define whether to validate the regular expression of the text input \[default: false\]

\- propertyTooltip: optional, in the case of input types textarea and select, it is possible to display a tooltip&nbsp; defined here

\- propertyType: mandatory, this is the control definition, with possible values: text, details, select (i.e. dropdown), checkbox&nbsp;

\- options: optional, this is the array of possible checkbox options

\- template: optional, this is needed in the case of propertyType = details, to define a popup multi-line text.&nbsp; Possible value: textarea

\- valueType: optional, this is needed in to specify that a property is numeric only.&nbsp; Possible values: numeric

&nbsp;

## Share customization with team members

It is recommended that you share customization using Git.&nbsp; Store your changes in a Git remote repository, and have your team members clone it locally in C:\\Users\\%username%\\.hackolade\\options (on Mac in Users/$USER/.Hackolade/options)&nbsp; That way, all that teams members need to do is to pull regularly, and they will get your latest changes.

&nbsp;

For custom property changes to take effect on each computer, it is required to exit Hackolade Studio and restart it.

&nbsp;

### One-time setup of the Git repository for the organization's custom properties

This step is required once per organization, to be executed by the Hackolade Studio superuser or maintainer.

&nbsp;

The process to git-enable your options folder may vary, depending on your OS and your repo provider.&nbsp; Here is an example using GitHub and Windows:

&nbsp;

&#49;) in Windows Explorer, go to C:\\Users\\%username%\\.hackolade\\options and make sure that the folder is empty. &nbsp;

&#50;) if the folder C:\\Users\\%username%\\.hackolade\\options is not empty, then cut the content and place it in a safe place

&#51;) in GitHub, create a new repository, for example called "hck\_custom\_props" and copy the Git URL, for example in our case "https://github.com/hackolade/hck\_custom\_props.git" (finishing in .git)

![Git-enable custom props - create repo](<lib/Git-enable custom props - create repo.png>)

&nbsp;

&#52;) in Hackolade Studio, go to the repository context (or the menu option "Repository \> Open Repository Context, or keyboard shortcut Ctrl + G)&nbsp;

&#53;) in the top bar, select the Source "URL", then paste the Git URL you had copied in step 3), then click the Clone button

![Git-enable custom props - clone repo](<lib/Git-enable custom props - clone repo.png>)

&#54;) in the OS destination folder dialog, select the folder C:\\Users\\%username%\\.hackolade\\options which must be an empty folder

![Git-enable custom props - select dest folder](<lib/Git-enable custom props - select dest folder.png>)

&#55;) if you had in step 2) to put in a safe place previous content of the options folder, now is the time to copy it back to the C:\\Users\\%username%\\.hackolade\\options folder

&#56;) commit and push to the central remote repository the changes of step 7) and any other changes to custom properties

&nbsp;

### One-time setup of each user's custom properties

When a new user installs the application, it should be part of the organizations documented process, right after license key validation, to clone locally the organization's custom properties repository.

&#49;) in Hackolade Studio, go to the repository context (or the menu option "Repository \> Open Repository Context, or keyboard shortcut Ctrl + G)&nbsp;

&#50;) in the top bar, select the Source "URL", then paste the Git URL you copied in step 3) , then click the Clone button

![Image](<lib/Git-enable custom props - clone repo.png>)

&#51;) in the OS destination folder dialog, select the folder C:\\Users\\%username%\\.hackolade\\options which must be an empty folder

![Image](<lib/Git-enable custom props - select dest folder.png>)

&#52;) select or possibly clone locally the models repository

&nbsp;

&nbsp;

### Share custom properties changes with Hackolade Studio users

When the superuser(s) or maintainer(s) develop, fine-tune and test new or adapted custom properties, it is useful to share them with the rest of the Hackolade Studio community of users in the organization.

&nbsp;

They should:

&#49;) using Hackolade Studio, select the custom props repository

&#50;) go to the Commit screen and click the Push button

&#51;) notify your community of Hackolade users to pull the changes from the remote repo of custom properties

&#52;) go back to your models repository

&nbsp;

Other users should simply:

&#49;) using Hackolade Studio, select the custom props repository

&#50;) go to the Pull screen and click the Pull button

&#51;) close and restart Hackolade Studio

&#52;) go back to your models repository

&nbsp;

## Models with custom properties lacking configuration

It is possible that you might be opening a model in which some custom properties were recorded, and and for which you don't have the configuration.&nbsp; In such case, we display a custom tab with a warning badge to alert you of this situation.

![Image](<lib/Custom props lacking configuration.png>)

&nbsp;

You may have to synchronize or pull the latest version of the custom configuration, or adjust your configuration to match the custom properties in the model.

