# From ER/Studio

If you have data models in ER/Studio and want to leverage them in Hackolade Studio, you need to fist export them to XSD, following the instructions below.&nbsp; You should first consult [this page](<XSDXMLSchemaDefinition.md>) for an overview of the import functionality in Hackolade Studio.

&nbsp;

By default ER/Studio does not export primary key and foreign key constraints.&nbsp; If the XSD does not contain this information, this reverse-engineering process cannot import them, but it is still possible to use the functionality to [Infer PKs \& FKs](<InferPrimaryKeysandForeignKeyRel.md>).

&nbsp;

For ER/Studio, the suggested parameters in the wizard are as follows:

&nbsp;

![ER-Studio Wizard - page 1](<lib/ER-Studio Wizard - page 1.png>)

&nbsp;

![ER-Studio Wizard - page 2](<lib/ER-Studio Wizard - page 2.png>)

&nbsp;

![ER-Studio Wizard - page 3 model](<lib/ER-Studio Wizard - page 3 model.png>)

&nbsp;

![ER-Studio Wizard - page 3 dictionary](<lib/ER-Studio Wizard - page 3 dictionary.png>)

&nbsp;

![ER-Studio Wizard - page 3 general](<lib/ER-Studio Wizard - page 3 general.png>)

&nbsp;

&nbsp;

![ER-Studio Wizard - page 3 datatype](<lib/ER-Studio Wizard - page 3 datatype.png>)

&nbsp;

&nbsp;

![ER-Studio Wizard - page 3 name conversion](<lib/ER-Studio Wizard - page 3 name conversion.png>)

&nbsp;

Knowing that the export function does not work with all version of ER/Studio, another option is to use the MetaWizard export in XSD format:

![ER-Studio Wizard - Meta export](<lib/ER-Studio Wizard - Meta export.png>)

&nbsp;

After the successful export of your model to XSD, use the instructions in [this page](<XSDXMLSchemaDefinition.md>) to import the XSD into a Hackolade Studio model for the target of your choice.
