# Configure custom properties

Hackolade Studio is shipped with out-of-the-box properties displayed in the Properties Pane. These properties are specific to each object in a data model. They are specific for each target technology, and can even be different for each data type.

&nbsp;

Many users want to define their own properties, for example to track PII or GDPR characteristics, or to tie with metadata management and governance. Some power users create hooks to be leveraged in DevOps CI/CD pipelines or in code generation routines.

&nbsp;

The user-defined custom properties leverage the controls described in [this page](Propertycontrols.md). This how-to guide takes you through a hands-on exercise to create custom properties.

&nbsp;

You may also view this [short video](<https://youtu.be/eHGhwp03rXo> "target=\"_blank\"") on YouTube.

&nbsp;

There is no UI for the creation and maintenance of custom properties. It is all done through a configuration in JSON files. This may sound a bit scary, but once you see how it works, it is really simple.

&nbsp;

Each target, whether native (shipped with Hackolade Studio: Polyglot, JSON, Couchbase, DynamoDB, MongoDB) or installed via plugin, gets a structure in the folder:

- **Windows:** C:\\Users\\%username%\\.hackolade\\options\\\<target>\\customProperties
- **Mac/Linux:** ~/.hackolade/options/\<target>/customProperties

&nbsp;

This folder can be access via Help > Plugin Manager > Installed and clicking on the ling "Show plugin customization directory" or via the operating system explorer/finder.

&nbsp;

In this guide, we will concentrate on files in these sub-folders of **\\customProperties\\properties_pane:**\
![Custom Props subfolders](<lib/Custom Props subfolders.png>)

&nbsp;

As a reminder, terminology differs between the targets supported by Hackolade:

- container means: dbs in MongoDB, region in DynamoDB, and bucket in Couchbase, namespace in Avro, keyspace in Cassandra, schema in RDBMS, etc...
- entity means: collection in MongoDB, table in DynamoDB and Cassandra and RDBMS, and document type in Couchbase, etc...
- field means: field in MongoDB and Couchbase, and attribute in DynamoDB, column in Cassandra and RDBMS, etc...

&nbsp;

You need to edit the corresponding \<object>LevelConfig.json file to add custom properties.

&nbsp;

The following controls are possible for user-defined properties:

&nbsp;

![Custom Props controls](<lib/Custom Props controls.png>)

- simple text: one line of text
- text area: popup for multi-line text entry
- dropdown selection (unique) from a defined list of options
- dropdown selection (multiple) from a defined list of options
- numeric-only field
- checkbox: for true/false entry
- group: addition of a set of properties of given control type
- field list: selection from list of fields
- field list with attributes: selection from list of fields with attributes

&nbsp;

The syntax for these controls is described in detail on this [page](<https://github.com/hackolade/plugins#26-property-controls> "target=\"_blank\"").

&nbsp;

## If you have never customized the chosen target

The very first step, which needs to be done only once per target, is to tell Hackolade that you wish to create custom properties. The application will create the necessary folders. To do this, you just need to go to Help > Plugin Manager > Installed, choose your target, and click on the link "Show plugin customization directory":\
![Custom props - plugin manager](<lib/Custom props - plugin manager.png>)

&nbsp;

## Entity details tab

Let's add a first custom property to the document entity for the JSON target. It will be a dropdown control for a list of Subject Areas for an insurance company.

&nbsp;

To do so, let's find the folder ***C:\\Users\\%username%\\.hackolade\\options\\****\<target>****\\customProperties\\entity_level*** and edit the file ***entityLevelConfig.json*** with a text editor such as [Notepad++](<https://notepad-plus-plus.org/downloads/> "target=\"_blank\""). The file must be a proper JSON-compliant file (except maybe for the comments which are not accepted by all JSON validators.)

&nbsp;

The first 130-odd lines are commented and provide examples for the different controls. All the changes will take place in the section below the comments, and within the brackets of the "structure":\
![Custom Props entity empty](<lib/Custom Props entity empty.png>)

&nbsp;

To create a control for a dropdown, we'll simply copy from an example further in the file, and paste it in between the brackets:\
![Custom Props entity pasted](<lib/Custom Props entity pasted.png>)

&nbsp;

Then we can edit the properties for our needs. There is just one property value that cannot be changed: "propertyType", as it is used by the application to properly handle the control.\
![Custom Props entity options](<lib/Custom Props entity options.png>)

&nbsp;

If you need to allow multiple options in the dropdown, simply change the type to "propertyType": "multipleCheckboxSelect" instead of "select".

&nbsp;

You may paste additional controls, separated by commas.\
![Custom Props entity options checkbox](<lib/Custom Props entity options checkbox.png>)

&nbsp;

You can now save the file. It is necessary to restart the application before you can see the results of your changes, as configuration is only read at startup time. Your custom properties will appear at the bottom of the Properties Pane:

&nbsp;

![Custom Props entity results](<lib/Custom Props entity results.png>)

&nbsp;

![Custom Props entity options dropdown](<lib/Custom Props entity options dropdown.png>)

&nbsp;

Feel free to download [here](<https://hackolade.com/schemas/custProps/properties_pane/entity_level/entityLevelConfig.json> "target=\"_blank\"") the file just created, save it the proper directory, then edit it for your own configuration.

&nbsp;

## Attribute details tab for a specific data type

When it comes to custom properties in the Details tab of attributes, things are slightly trickier, but not much. It is important to understand that the set of properties is different for each data type. As a result, you can declare a custom property for one or more specific data types, as shown in this section. If a custom property applies to all data types, you do not need to repeat it: declare it once, as described in the next section.

&nbsp;

Creating a custom tab is reviewed in a section further down.

&nbsp;

> [!IMPORTANT]
> As the data types are different from one target to the next, you cannot blindly copy the config file from one target to the next. Also, do NOT mix \<level>LevelConfig.json files, as they are structured differently.

&nbsp;

This time, let's add custom properties at the attribute (aka field) level for the JSON target. It will be a dropdown control for a list of GDPR classifications.

&nbsp;

To do so, let's find the folder ***C:\\Users\\%username%\\.hackolade\\options\\****\<target>****\\customProperties\\field_level*** and edit the file ***fieldLevelConfig.json*** with a text editor such as [Notepad++](<https://notepad-plus-plus.org/downloads/> "target=\"_blank\""). The file must be a proper JSON-compliant file (except maybe for the comments which are not accepted by all JSON validators.)

&nbsp;

The first 130-odd lines are commented and provide examples for the different controls. All the changes will take place in the section below the comments, and within the brackets of the "structure". A hint has been placed, commented with a double slash //:

&nbsp;

![Custom Props attribute empty](<lib/Custom Props attribute empty.png>)

&nbsp;

Let's remove the doubles slash //. Then to create a control for a dropdown, we'll simply copy from an example further in the file, and paste it in between the brackets. Then we can edit the properties for our needs. There is just one property value that cannot be changed: "propertyType", as it is used by the application to properly handle the control.

&nbsp;

![Custom Props attribute options](<lib/Custom Props attribute options.png>)

&nbsp;

If you need to allow multiple options in the dropdown, simply change the type to "propertyType": "multipleCheckboxSelect" instead of "select".

&nbsp;

You may paste additional controls, separated by commas.\
![Custom Props attribute options text](<lib/Custom Props attribute options text.png>)

&nbsp;

You can now save the file. It is necessary to restart the application before you can see the results of your changes, as configuration is only read at startup time. Your custom properties will appear at the bottom of the Properties Pane:

&nbsp;

![Custom Props attribute result](<lib/Custom Props attribute result.png>)

&nbsp;

But, these custom properties are currently only available for the string data type. If they also need to be available in the number data type, a new section must be declared, separated by a comma, and the configuration copied:\
![Custom Props attribute numeric options text](<lib/Custom Props attribute numeric options text.png>)

&nbsp;

And the operation can be repeated for other data types.

&nbsp;

Feel free to download [here](<https://hackolade.com/schemas/custProps/properties_pane/field_level/fieldLevelConfig.json> "target=\"_blank\"") the file just created, save it the proper directory, then edit it for your own configuration.

&nbsp;

## Attribute details tab for all data types

Many custom properties apply to all attributes, whatever their data type, for example a GDPR classification or a data owner. In that case, declare the property once, in a Details tab whose structure is an array, instead of an object with one entry per data type.\
​\
​\
You can combine both forms in the same fieldLevelConfig.json file: one Details tab for the properties common to all data types, and another Details tab for the properties of specific data types:\
​

&nbsp;

```json
[
  {
    "lowerTab": "Details",
    "structure": [
      {
        "propertyName": "Common prop of all data types",
        "propertyKeyword": "commonProp",
        "propertyType": "text"
      }
    ]
  },
  {
    "lowerTab": "Details",
    "structure": {
      "string": [
        {
          "propertyName": "Prop of string only",
          "propertyKeyword": "stringOnlyProp",
          "propertyType": "text"
        }
      ],
      "number": [
        {
          "propertyName": "Prop of number only",
          "propertyKeyword": "numberOnlyProp",
          "propertyType": "text"
        }
      ]
    }
  }
]
```

&nbsp;

​\
​\
With this configuration, "Common prop of all data types" appears in the Details tab of every attribute. "Prop of string only" appears only for attributes of type string, and "Prop of number only" appears only for attributes of type number.\
​\
Like for other configuration files, you must restart Hackolade Studio after saving the file, in order for the changes to be taken into account.

&nbsp;

## Attribute custom tab

> [!NOTE]
> Requires Hackolade v5.4.5 or above

&nbsp;

This time, let's add custom properties at the model level for the JSON target. It will be 3 different types of control: a text field, a checkbox, and a dropdown.

&nbsp;

To do so, let's find the folder ***C:\\Users\\%username%\\.hackolade\\options\\****\<target>****\\customProperties\\model_level*** and edit the file model***LevelConfig.json*** with a text editor such as [Notepad++](<https://notepad-plus-plus.org/downloads/> "target=\"_blank\""). The file must be a proper JSON-compliant file (except maybe for the comments which are not accepted by all JSON validators.)

&nbsp;

![Custom Props tab](<lib/Custom Props tab.png>)

&nbsp;

Note: that we leave alone, the 2 tabs already available, and create a new tab. Don't worry about the "lower" part of the keyword "lowerTab".

&nbsp;

You can now save the file. It is necessary to restart the application before you can see the results of your changes, as configuration is only read at startup time. Your custom properties will appear at the bottom of the Properties Pane:\
![Custom Props tab result](<lib/Custom Props tab result.png>)

&nbsp;

Feel free to download [here](<https://hackolade.com/schemas/custProps/properties_pane/model_level/modelLevelConfig.json> "target=\"_blank\"") the file just created, save it the proper directory, then edit it for your own configuration.

&nbsp;

## Advanced syntax

Many additional keywords are available to fine-tune the behavior of controls, which described in the [plugin documentation](<https://github.com/hackolade/plugins#26-property-controls> "target=\"_blank\""). Among them are 2 popular features: the possibility to mark a property as required, and the possibility to display a property based on the value of another property.

&nbsp;

The *`requiredProperty`* keyword displays a red star (\*) character next to the property label. The validation keyword and structure ensures that the entry is validated. If you set the required flag to false, or do not provide the validation structure, then the red star would be for display only with no enforcement. If the requirement is enforced but not satisfied, a red badge with an explanation point (!) is displayed.

&nbsp;

![Custom Props required keyword](<lib/Custom Props required keyword.png>)

&nbsp;

The keyword *`dependency`* allows sophisticated logic described in the [documentation](https://github.com/hackolade/plugins#26-property-controls). to test according multiple criteria, and including and/or/not operators. Here is the simplest of examples:

&nbsp;

![Custom Props dependecy keyword](<lib/Custom Props dependecy keyword.png>)

&nbsp;

The result of the above keywords are displayed below:\
![Custom Props tab required dependency result](<lib/Custom Props tab required dependency result.png>)

&nbsp;

The keyword *`⁠enableForReference`* is an optional boolean parameter used in the property definition. By default, properties of references to a definition (whether internal, model, or external) are typically disabled. However, by setting this keyword to *`true`*, the custom property becomes editable in the reference, allowing users to specify a value that takes precedence over the same property value from the referenced definition.

&nbsp;

This keyword is applicable not only to references but also to attributes of views (column view), which are references to underlying table attributes. This means that when the reference is resolved, the property values will be taken from the reference (if present) rather than from its original definition.

&nbsp;

Example Usage:\
To define a custom property that can be edited in the reference or view attribute, include the ⁠enableForReference keyword in the property definition as shown below:

&nbsp;

```json
{
    "propertyName": "Count",
    "propertyKeyword": "count",
    "propertyType": "numeric",
    "enableForReference": true
}
```

&nbsp;

## Additional considerations

If you use multiple targets, you probably want to display the same custom properties. You may copy the <strong><em>C:\\Users\\%username%\\.hackolade\\options\\</em></strong><em>\<target></em><strong><em>\\customProperties\\</em></strong><em>\<level></em><strong><em>\_level\\</em></strong><em>\<level></em><strong><em>LevelConfig.json</em></strong> file to other targets for all levels except for the field level. The field level configuration file must have data types that match the data types of the target. If you choose to copy the file from another target, you must adjust it to reflect the right data types.

&nbsp;

You may want to share your custom properties with other team members to ensure consistency. We strongly suggest to leverage Git to synchronize and deploy custom properties. Detailed instructions are available in [this page](<https://hackolade.com/help/Userdefinedcustomproperties.html#Share%20customization%20with%20team%20members>).

&nbsp;

If you need to change the location of customer properties, you may do so Tools > Options > Default Paths.
