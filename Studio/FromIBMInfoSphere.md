# From IBM InfoSphere

If you have data models in InfoSphere and want to leverage them in Hackolade Studio, you need to fist export them to XSD, following the instructions below.&nbsp; You should first consult [this page](<XSDXMLSchemaDefinition.md>) for an overview of the import functionality in Hackolade Studio.

&nbsp;

If the XSD does not contain primary key and foreign key constraints, this reverse-engineering process cannot import them, but it is still possible to use the functionality to [Infer PKs \& FKs](<InferPrimaryKeysandForeignKeyRel.md>).

&nbsp;

It is suggested to use the parameters below when exporting models to XSD. These [steps](<https://www.ibm.com/support/pages/how-convert-db2-ddl-xml-xsd-format-ibm-infosphere-data-architect> "target=\"\_blank\"") assume that IBM InfoSphere Data Architect version 7.5.x is installed on the system:

## Install the Model Import/Export feature

Install the Model Import/Export feature if it is not already installed. &nbsp; To confirm if the feature is already installed, use the View Installed Packages for the IBM Installation Manager. This is available from the Start menu in the following location:\
\
Start -\> Programs -\> IBM Installation Manager -\> View Installed Packages\
\
If installed, the feature will be listed in the Features section for the IBM InfoSphere Data Architect package.

\
If the feature is not installed, the Installation Manager can be used to install the feature:\
\
&#49;.1.- Open IBM Installation Manager\
&#49;.2.- Select option "Modify"\
&#49;.3.- Highlight the IBM InfoSphere Data Architect product and click Next\
&#49;.4.- From the "Features", under "Model Exchange", select "Model Import/Export" and follow the prompts to add this feature

## Perform the export

Suggested steps:

&nbsp;

&#50;.1.- Open the IBM InfoSphere Data Architect product, then open or create your Data Design Project.\
\
&#50;.2.- If the DB2 DDL file is not yet in the Data Design Project (usually in the SQL Scripts folder), use the *File / Import*... option from the IBM InfoSphere Data Architect product menu to import the file. Select the *File System* option under the *General* category as the import source in the Import wizard and follow the prompts to import the DB2 DDL file into your project.

\
&#50;.3.- Click on *File / Export...* option from the IBM InfoSphere Data Architect menu.\
\
&#50;.4.- Select *Data Model Export Wizard* under the *Data* section as the export destination and click Next

\
&#50;.5.- Select *W3C XML Schema x.y (XSD)* as the Model format, where *x.y* identifies the version (ie. 1.0)\
\
&#50;.6.- Click the *Browse...* button to the side of label *Model:* and select the script corresponding to the DB2 DDL file you want to export

\
&#50;.7.- Click the *Browse...* button to the side of the *Export to:* label and specify a filename for the resulting file\
\
&#50;.8.- Click Next

&nbsp;

After the successful export of your model to XSD, use the instructions in [this page](<XSDXMLSchemaDefinition.md>) to import the XSD into a Hackolade Studio model for the target of your choice.

