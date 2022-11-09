# From PowerDesigner

If you have data models in PowerDesigner and want to leverage them in Hackolade Studio, you need to fist export them to XSD, following the instructions below.&nbsp; You should first consult [this page](<XSDXMLSchemaDefinition.md>) for an overview of the import functionality in Hackolade Studio.

&nbsp;

If the XSD does not contain primary key and foreign key constraints, this reverse-engineering process cannot import them, but it is still possible to use the functionality to [Infer PKs \& FKs](<InferPrimaryKeysandForeignKeyRel.md>).

&nbsp;

From PowerDesigner, the process is as follows:

&nbsp;

&#49;. go to Tools \> Generate \> XML Models or  Ctrl + Shift + M

&nbsp;

![PowerDesigner - Export to XML General](<lib/PowerDesigner%20-%20Export%20to%20XML%20General.png>)

&nbsp;

&nbsp;

&#50;. In the Details tab, select the following options:

&nbsp;

![Image](<lib/PowerDesigner%20-%20Export%20to%20XML%20Details.png>)

&nbsp;

&#51;. \[optional\] Click the **Target Models** tab and specify the target models for any generated shortcuts.

&nbsp;

&#52;. \[optional\] Click the **Selection** tab and select objects to generate.

&nbsp;

&#53;. Click **OK** to begin generation.

&nbsp;

&#54;. Go to Hackolade: Tools \> Reverse-Engineer \> XSD Schema and select previously generated file

&nbsp;

&nbsp;

You may refer to the following pages for more information:

[https://help.sap.com/viewer/856348b84a7c479489d5172a630f014d/16.7.00/en-US/c7c994ac6e1b1014a7cee7aac852831e.html](<https://help.sap.com/viewer/856348b84a7c479489d5172a630f014d/16.7.00/en-US/c7c994ac6e1b1014a7cee7aac852831e.html>).

[https://help.sap.com/viewer/1c741f9f80fb4ee4b189535407dd0686/16.7.00/en-US/c802dc9b6e1b1014a826b72f71f0bc04.html](<https://help.sap.com/viewer/1c741f9f80fb4ee4b189535407dd0686/16.7.00/en-US/c802dc9b6e1b1014a826b72f71f0bc04.html>)&nbsp;

&nbsp;

To generate the XML model with configuration so primary keys and foreign key relationships: &nbsp;  [https://help.sap.com/viewer/856348b84a7c479489d5172a630f014d/16.7.00/en-US/c81551706e1b1014b477f70e345cba01.html](<https://help.sap.com/viewer/856348b84a7c479489d5172a630f014d/16.7.00/en-US/c81551706e1b1014b477f70e345cba01.html>)

&nbsp;

&nbsp;

After the successful export of your model to XSD, use the instructions in [this page](<XSDXMLSchemaDefinition.md>) to import the XSD into a Hackolade Studio model for the target of your choice.

