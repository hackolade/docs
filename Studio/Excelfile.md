# Excel file

The feature to exchange data with Excel provides the ability to export a data model, or parts of it, to Microsoft Excel so properties could be easily edited in a tabular format, to be re-imported back into the application.&nbsp; It facilitates productive bulk actions for the maintenance of properties.&nbsp; It also allows creation of a new model - or additions to an existing model - by team members that might not have access to the application.

&nbsp;

It includes the following capabilities:&nbsp;

(i) editing containers, entities, and attributes of an existing model;&nbsp;

(ii) selecting which properties of an attribute are exported in the Excel file, and hence which ones are filtered out and not exported; and&nbsp;

(iii) selecting custom attributes to be added in the various data types of the plugin.

&nbsp;

When doing a roundtrip from Hackolade to Excel and back, it is important to maintain integrity of the model and avoid any corruption.&nbsp; Microsoft Excel does not allow all the controls and validations of the Hackolade applications.&nbsp; Additionally, the application supports a large number of different targets with differing terminology, structure, and characteristics. &nbsp;

&nbsp;

**Important note:** let's not misunderstand what is meant with "bulk editing"...&nbsp; the purpose of this function is to facilitate the enrichment of existing models, thanks to the flexibility and power of Excel, including the ability to xlookup, copy/paste information, etc. &nbsp; The purpose is NOT to find a creative way to leverage Excel's lack of integrity rules to circumvent the logic and checks built in the application.&nbsp; We suggest to be extra careful in particular when performing operations that touch the object GUIDs.&nbsp; Copying or changing GUIDs create risks of corrupting the model upon import.

&nbsp;

**Important note:** it is critical that the template used to import is of the same target and plugin version issued by the export process.

&nbsp;

**Important note:** deleting a line in Excel will NOT result in a delete operation in the model when reverse-engineering the Excel back into the Hackolade model. &nbsp;

&nbsp;

To import CSV files into Hackolade, it is advised to first export an Excel template, then import the CSV file into the Excel template, before importing back into Hackolade.

&nbsp;

## Export model

To start your export for a model, simply go to Tools \> Forward-Engineer \> Excel file...&nbsp; In the Object selection dialog, you may deselect objects that you do not wish to export. &nbsp;

&nbsp;

![Tools Options - FE Excel Export Objet Select](<lib/Tools Options - FE Excel Export Objet Select.png>)

&nbsp;

&nbsp;

With the Options button, you may also access a dialog to select object properties that you do not wish to export:

![Tools Options - FE Excel Properties Selection](<lib/Tools Options - FE Excel Properties Selection.png>)

&nbsp;

The properties for each object are listed in the corresponding sections.&nbsp; If you need to filter out a property, simply uncheck the corresponding box.

&nbsp;

Instructions for the import of an Excel file can be found in [Excel reverse-engineering](<Exceltemplate.md>).

&nbsp;

## Maintain configuration

This configuration can also be maintained in Tools \> Options \> Forward-Engineering, and there's one configuration per target.&nbsp; The configuration itself can be exported to a JSON file so it can be distributed in the organization, and imported on other instances of the application.

&nbsp;

&nbsp;

![Tools Options - FE Excel Export](<lib/Tools Options - FE Excel Export.png>)

&nbsp;

**Note:** depending on the purpose of your export, you may want to resolve referenced definitions, or not.&nbsp; When the purpose is to do bulk editing, then import the Excel back into your model, then in order to maintain integrity, when a reference to a definition is exported Excel, it must NOT&nbsp; be resolved.&nbsp; In other words, the sub-structure of the object is not exported. &nbsp;

If on the other hand, the purpose is to publish a catalog of the objects in the model, it may be desirable to resolve the references.&nbsp; Choose this option wisely.

&nbsp;

&nbsp;

## Known limitations

Microsoft Excel (as well as LibreOffice) encounters memory limitations in the handling of validation lists, used to control in Excel boolean checkbox properties and for dropdown properties, and leading to this type of error message:

&nbsp;

![Excel - Validation list limit](<lib/Excel - Validation list limit.png>)

&nbsp;

If you click Yes, you should be aware that values are no longer validated against validation lists, which could lead to undesired inconsistencies.&nbsp; It is suggested instead to:

\- increase RAM on the workstation,

\- reduce the number of validated properties exported (checkbox or dropdown)

\- reduce the number of entities (and hence attributes) exported

&nbsp;

&nbsp;

