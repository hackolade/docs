# From PowerDesigner

If you have data models in PowerDesigner and want to leverage them in Hackolade Studio, you need to first export them to XSD, following the instructions below.&nbsp; Then you should consult [this page](<XSDXMLSchemaDefinition.md>) for an overview of the import functionality in Hackolade Studio.

&nbsp;

You may refer to the following pages for more information:

[https://help.sap.com/viewer/856348b84a7c479489d5172a630f014d/16.7.00/en-US/c7c994ac6e1b1014a7cee7aac852831e.html](<https://help.sap.com/viewer/856348b84a7c479489d5172a630f014d/16.7.00/en-US/c7c994ac6e1b1014a7cee7aac852831e.html> "target=\"\_blank\"").

[https://help.sap.com/viewer/1c741f9f80fb4ee4b189535407dd0686/16.7.00/en-US/c802dc9b6e1b1014a826b72f71f0bc04.html](<https://help.sap.com/viewer/1c741f9f80fb4ee4b189535407dd0686/16.7.00/en-US/c802dc9b6e1b1014a826b72f71f0bc04.html> "target=\"\_blank\"")&nbsp;

&nbsp;

To generate the XML model with configuration so primary keys and foreign key relationships: &nbsp; [https://help.sap.com/viewer/856348b84a7c479489d5172a630f014d/16.7.00/en-US/c81551706e1b1014b477f70e345cba01.html](<https://help.sap.com/viewer/856348b84a7c479489d5172a630f014d/16.7.00/en-US/c81551706e1b1014b477f70e345cba01.html> "target=\"\_blank\"")

&nbsp;

## Generate a PowerDesigner physical model (PDM) from a logical model (LDM)

If you already have a physical model, you may skip this step and go to the next one.

&nbsp;

You may also view this [short video](<https://youtu.be/22OaNFbw2is> "target=\"\_blank\"") on YouTube.

&nbsp;

In PowerDesigner with your logical data model open, go to Tools \> Generate Physical Data Model:

&nbsp;

![PowerDesigner LSM to PDM menu](<lib/PowerDesigner%20LSM%20to%20PDM%20menu.png>)

&nbsp;

&nbsp;

Then choose the DBMS platform for the physical model

![PowerDesigner LSM to PDM general tab](<lib/PowerDesigner%20LSM%20to%20PDM%20general%20tab.png>)

&nbsp;

&nbsp;

And make any changes necessary in the Detail tab for model check and or lineage.

&nbsp;

When you click OK, a physical data model gets created in PowerDesigner. &nbsp;

&nbsp;

## Generate a PowerDesigner XML model (XSM) from a physical model (PDM)

If you already have an XML model, you may skip this step and go to the next one.

&nbsp;

You may also view this [short video](<https://youtu.be/UrBBfDWVdxI> "target=\"\_blank\"") on YouTube.

&nbsp;

In PowerDesigner with your physical data model open, go to Tools \> Generate XML Model:

&nbsp;

![PowerDesigner PDM to XSM menu](<lib/PowerDesigner%20PDM%20to%20XSM%20menu.png>)

&nbsp;

Then give your model a name:

![PowerDesigner - Export to XML General](<lib/PowerDesigner%20-%20Export%20to%20XML%20General.png>)

&nbsp;

&nbsp;

And in the Details tab, select the following options:

![PowerDesigner - Export to XML Details](<lib/PowerDesigner%20-%20Export%20to%20XML%20Details.png>)

&nbsp;

&nbsp;

&nbsp;

\[optional\] Click the **Target Models** tab and specify the target models for any generated shortcuts.

&nbsp;

\[optional\] Click the **Selection** tab and select objects to generate.

&nbsp;

Click **OK** to begin generation.

&nbsp;

You may have to setup the XML extension appropriately:

![PowerDesigner XML extension](<lib/PowerDesigner%20XML%20extension.png>)

&nbsp;

## Generate an XSD file from a PowerDesigner XML model (XSM)

You may also view this [short video](<https://youtu.be/c9MTSw0tT88> "target=\"\_blank\"") on YouTube.

&nbsp;

With your XSM model open, go to Language \> Generate XML Schema Definition File

&nbsp;

![PowerDesigner XSM to XSD menu](<lib/PowerDesigner%20XSM%20to%20XSD%20menu.png>)

&nbsp;

&nbsp;

Choose the destination for your output

![PowerDesigner XSM to XSD destination](<lib/PowerDesigner%20XSM%20to%20XSD%20destination.png>)

&nbsp;

&nbsp;

&nbsp;

More info about XSM: [https://www.powerdesigner.biz/documentations/powerdesigner-16.6-documentation-en/xml\_modeling.pdf](<https://www.powerdesigner.biz/documentations/powerdesigner-16.6-documentation-en/xml\_modeling.pdf> "target=\"\_blank\"")

&nbsp;

## Reverse-Engineer XSD file into a Hackolade model

After the successful export of your model to XSD, use the instructions in [this page](<XSDXMLSchemaDefinition.md>) to import the XSD into a Hackolade Studio model for the target of your choice.

&nbsp;

In Hackolade Studio, go to Tools \> Reverse-Engineer \> XSD Schema and select previously generated file.

&nbsp;

As PowerDesigner represents some Foreign Key relationships with the embedding of the child table in the paretn table, if it advised to select the check box "Normalize complex data types in separate entities".&nbsp; Even if your target model allows complex data types and denormalization, you may want to analyze your access patterns and do the [denormalization](<SuggestdenormalizationofaSQLsche.md>) manually.

&nbsp;

![PowerDesigner XSD to Hackolade dialog](<lib/PowerDesigner%20XSD%20to%20Hackolade%20dialog.png>)

&nbsp;

After import, Hackolade Studio displays the resulting ER diagram.

&nbsp;

If the XSD does not contain primary key and foreign key constraints, this reverse-engineering process cannot import them, but it is still possible to use the functionality to [Infer PKs \& FKs](<InferPrimaryKeysandForeignKeyRel.md>). &nbsp;

&nbsp;

&nbsp;

