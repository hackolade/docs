# Excel file

The feature to exchange data with Excel provides the ability to export a data model, or parts of it, to Microsoft Excel so properties could be easily edited in a tabular format, to be re-imported back into the application.&nbsp; It facilitates productive bulk actions for the maintenance of properties.&nbsp; It also allows creation of a new model - or additions to an existing model - by team members that might not have access to the application.

&nbsp;

It includes the following capabilities:&nbsp;

(i) the basic creation of a new model or the addition of containers, entities, and attributes to an existing model;&nbsp;

(ii) the selection, by the user, of which properties of an attribute are exported in the Excel file, and hence which ones are filtered out and not exported; and&nbsp;

(iii) the choice, by the user, of custom attributes to be added in the various data types of the plugin.

&nbsp;

**Note:** in order to maintain integrity, when a reference to a definition is exported Excel, it is not resolved.&nbsp; In other words, the sub-structure of the object is not exported.&nbsp; Neither are the definitions themselves (currently - to be added soon.)

&nbsp;

When doing a roundtrip from Hackolade to Excel and back, it is important to maintain integrity of the model and avoid any corruption.&nbsp; Microsoft Excel does not allow all the controls and validations of the Hackolade applications.&nbsp; Additionally, the application supports a large number of different targets with differing terminology, structure, and characteristics.&nbsp; To address these concerns, it is critical that the template used for export is the one used for the import process.

&nbsp;

To import CSV files into Hackolade, it is advised to go first export an Excel template, then link it to the CSV file, before importing back into Hackolade.

&nbsp;

The user can configure the exact properties of each object to be exported to Excel.&nbsp; This configuration is maintained in Tools \> Options \> Forward-Engineering, and there's one configuration per target.&nbsp; The configuration itself can be exported to a JSON file so it can be distributed in the organization, and imported on other instances of the application.

&nbsp;

&nbsp;

![Image](<lib/Tools%20Options%20-%20FE%20Excel%20Export.png>)

&nbsp;

The properties for each object are listed in the corresponding sections.&nbsp; If you need to filter out a property, simply uncheck the corresponding box.

&nbsp;

![Image](<lib/Tools%20Options%20-%20FE%20Excel%20Object%20Selection.png>)

&nbsp;

**Limits:** Microsoft Excel (as well as LibreOffice) encounters memory limitations in the handling of validation lists, used to control in Excel boolean checkbox properties and for dropdown properties, and leading to this type of error message:

&nbsp;

![Image](<lib/Excel%20-%20Validation%20list%20limit.png>)

&nbsp;

If you click Yes, you should be aware that values are no longer validated against validation lists, which could lead to undesired inconsistencies.&nbsp; It is suggested instead to:

\- increase RAM on the workstation,

\- reduce the number of validated properties exported (checkbox or dropdown)

\- reduce the number of entities (and hence attributes) exported

&nbsp;

Instructions for the reverse-engineering of an Excel file can be found [here](<Exceltemplate.md>).

