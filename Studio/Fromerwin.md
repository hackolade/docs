# From erwin

If you have data models in erwin and want to leverage them in Hackolade Studio, you need to fist export them to XSD, following the instructions below.&nbsp; You should first consult [this page](<XSDXMLSchemaDefinition.md>) for an overview of the import functionality in Hackolade Studio.

&nbsp;

By default ERwin does not export primary key and foreign key constraints.&nbsp; If the XSD does not contain this information, this reverse-engineering process cannot import them, but it is still possible to use the functionality to [Infer PKs \& FKs](<InferPrimaryKeysandForeignKeyRel.md>).

&nbsp;

It is suggested to use the parameters below when exporting models to XSD,&nbsp;

\- if from a physical model:

![ERwin XSD export parameters - physical](<lib/ERwin%20XSD%20export%20parameters%20-%20physical.png>)

&nbsp;

\- if from a logical model:

![Image](<lib/ERwin%20XSD%20export%20parameters%20-%20logical.png>)

&nbsp;

After the successful export of your model to XSD, use the instructions in [this page](<XSDXMLSchemaDefinition.md>) to import the XSD into a Hackolade Studio model for the target of your choice.

