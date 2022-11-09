# From Sparx Enterprise Architect

If you have data models in Sparx Enterprise Architect and want to leverage them in Hackolade Studio, you need to fist export them to XSD, following the instructions below.&nbsp; You should first consult [this page](<XSDXMLSchemaDefinition.md>) for an overview of the import functionality in Hackolade Studio.

&nbsp;

By default Enterprise Architect does not export primary key and foreign key constraints.&nbsp; If the XSD does not contain this information, this reverse-engineering process cannot import them, but it is still possible to use the functionality to [Infer PKs \& FKs](<InferPrimaryKeysandForeignKeyRel.md>).

&nbsp;

The XSD generation is a package-level operation in EA. &nbsp;

&nbsp;

***Getting Started***\
To use the schema generation facility you will require the following:

* EA Professional or Corporate edition
* [XSDDataTypes](<https://sparxsystems.com/downloads/profiles/XSDDataTypes.xml>) Package: This package contains classes representing XSD primitive data types. This package is available as an XMI file. To import the file as a UML Package, use EA's XMI import facility which is available from the menu item: Project \| Import/Export \| Import Package from XMI.
* [UML Profile for XML](<https://sparxsystems.com/downloads/profiles/XSDProfile.xml>): This resource file contains the stereotyped classes which allow the schema generation to be customized. The UML Profile for XML can be imported into a model using the Resource View (see [Importing Profiles](<https://sparxsystems.com/resources/developers/uml\_profiles.html>) for details on importing UML profiles into EA).

## Steps to Generate XSD

1. Select the package to be converted to XSD by right-clicking on the package in the Project Browser.
1. Select Project \| Generate XML Schema from the main menu.
1. Set the desired output file using the Filename field.
1. Set the desired xml encoding using the Encoding field.
1. Click on the Generate button to generate the schema.
1. The progress of the schema generator will be shown in the Progress edit box.

&nbsp;

More information can be found [here](<https://sparxsystems.com/resources/xml\_schema\_generation.html> "target=\"\_blank\"").

&nbsp;

After the successful export of your model to XSD, use the instructions in [this page](<XSDXMLSchemaDefinition.md>) to import the XSD into a Hackolade Studio model for the target of your choice.
