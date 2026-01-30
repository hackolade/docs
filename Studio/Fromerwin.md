# From erwin

## Differences with Erwin

There are many differences between Hackolade Studio and Erwin DM.&nbsp; We do not use or even have a copy of that software.&nbsp; No one in our organization has ever worked with it.&nbsp; Hackolade's ambition is certainly not to copy Erwin, ... to the contrary\!&nbsp; It should be expected, since Hackolade Studio is a different tool than Erwin, that some things would work differently, that we would name some things differently, that features we have don’t exist in Erwin, and vice versa.&nbsp;

&nbsp;

Here are some examples, but there are many, many more…

* Erwin uses the term “Subject Areas”.&nbsp; We have “[Diagram Views](<DiagramViews.md>)”.&nbsp; The purpose may be somewhat similar.&nbsp; Terminology, and how they function may be different

&nbsp;

* Erwin uses the term "domain", a term interpreted differently by different people, for sure to describe something quite different than what we describe as a [re-usable object definition](<Reusableobjectsdefinitions.md>) or user-defined type

&nbsp;

* When creating foreign key relationships in Erwin, the convention is that you drag from the attribute PK in the parent entity towards the child entity.&nbsp; The attribute is automatically created in the child entity and the FK relationship is also created.&nbsp; Hackolade Studio also supports this approach, but it is not the default behavior.&nbsp; To change the default to be like Erwin, simply change the parameter "FK relationships drag-n-drop behavior" in Tools \> Options \> General to become "from parent to child".

&nbsp;

* Erwin seems to have a "complete compare" wizard.&nbsp; With the [architecture of Hackolade Studio](<WhylegacyandSaaSdatamodelingarch.md>), models are in JSON format and are stored in Git repositories where versioning is automatic, and each commit and push results in an immutable version of the model.&nbsp; As a result, a [compare and merge](<Compareandmergemodels.md>) operation in Hackolade Studio always results in a "third" model, instead of an alteration of existing model versions.&nbsp; Note also that it is possible to [compare two arbitrary commits](<https://hackolade.com/help/Explorehistory.html#Compare%20commits>).&nbsp; Whatever the way Erwin compares models, for sure, Hackolade Studio's equivalent feature will work completely differently.

&nbsp;

* Erwin allows to open multiple models in the same application instance.&nbsp; The architecture of Hackolade Studio being different, we allow to start multiple instances of the application, each with a single model.&nbsp; This is actually quite handy, as it allows to alt-tab to toggle between different models.&nbsp; As indicated in our [Tips and Tricks](<Tipsandtricks.md>), you may start multiple instances of Hackolade Studio on the same machine session, so as to work on multiple models simultaneously.&nbsp; You may also merge 2 Hackolade models, or combine elements from another model with copy/paste from one model in one application instance, to the other model in the second application instance.&nbsp; From within the application, this is easily done with the shortcut Ctrl+Shift+I (on Mac Cmd+Shift+I) or with the menu option File \> Start New Application Instance.&nbsp; Or from the operating system, on Windows, right-click on the Hackolade icon in the toolbar then choose Hackolade...

&nbsp;

* Erwin stores logical and physical in the same file. &nbsp; The architecture of our solution is very different from Erwin’s.&nbsp; Our model files are not binary in a proprietary format, but open in JSON format, and each file represents a single model.&nbsp; We purposely avoid Erwin’s approach of logical/physical models in order to provide for a more flexible modular approach, as described [here](<https://hackolade.com/help/PolyglotDataModeling.html#Flexibilty>).&nbsp; With our modular architecture, it is possible for a physical model to be derived from 1 or more (subsets of) polyglot models.&nbsp; It is also possible for any model to reference any part of any model, no matter the target on each side.\
\
Legacy tools have been using the traditional concept of “logical” models, which is too constraining for the needs of non-RDBMS targets supported by Hackolade Studio. &nbsp; Hackolade had to invent the principles of [Polyglot Data Modeling](<https://hackolade.com/polyglot-data-modeling.html>) to support the needs of NoSQL, Avro, Parquet, REST APIs, etc…&nbsp; We name it Polyglot, as opposed to logical, to avoid any semantic confusion or discussion.&nbsp; But our Polyglot models are logical in the sense that they are technology-agnostic, and they can be fully normalized. &nbsp; But they can be much more than strict logical models in the sense that they can optionally support nested objects, polymorphism, and denormalization.&nbsp; \
\
Polyglot models can be purely "logical", in the traditional sense.&nbsp; But they can also be more of a "common physical model", including technical names or views that would be common across different physical targets.&nbsp; No dogma with Hackolade: you can be as rigorous in applying data modeling theory as you wish, or less rigorous in order to adhere to the reality of your organization.\
\
Physical data models can be [derived from](<https://hackolade.com/help/PolyglotDataModel.html>) polyglot models.&nbsp; It is also possible to start from a physical data model (either from scratch or created from the reverse-engineering of an instance) and convert it to a polyglot model.\
\
Once a target model is linked to one or more polyglot models, any change in the polyglot model can be reviewed through an [Impact Analysis](<https://hackolade.com/help/PolyglotDataModel.html#Impact%20Analysis>) screen to decide whether to include the changes, globally or individually.\
\
Polyglot models can be derived from (subsets of) other polyglot model(s), as described [here](<https://hackolade.com/help/PolyglotDataModeling.html#Flexibilty>).&nbsp; In the end, it is possible to create a graph of models.\
&nbsp;
* In Erwin when creating a physical model from a logical model, the physical model is "generated" (or "derived") from the logical model in a "**push**" process.&nbsp; In Hackolade Studio, the process is different, partly due to the fact that Hackolade Studio supports so many targets that are different than RDBMS.&nbsp; And also because in Hackolade Studio, it is possible to build an N-to-N graph of data models, where for example a model draws from more than one polyglot model.&nbsp; As a result in Hackolade Studio, the process follows a "**pull**" mechanism: you would first create a physical model for the target of our choice, then "derive" from the selected polyglot model or models.

&nbsp;

Given the above, it should be expected that there is some learning curve to our tool.&nbsp; You will most likely avoid frustration if you don't assume, because you're a veteran user of Erwin DM, that you can use Hackolade Studio without learning about it.&nbsp; This learning curve can be greatly reduced by investing a little bit of time in reading or searching inside our [online documentation](<WelcometoHackoladeStudio.md>), going through [tutorials](<Tutorial.md>) and [how-to guides](<How-toguides.md>), and by watching some of the videos on our [eLearning platform](<https://community.hackolade.com/slides/all> "target=\"\_blank\"").

&nbsp;

## Export a data model from Erwin

**Note:** recently a customer migrating a large number of Erwin models to Hackolade reported that, in their opinion, an alternate approach leads to better results than through XSD files: use Erwin to export the model to a PowerDesigner format, then import the resulting PDM file using [these instructions](<https://hackolade.com/help/PowerDesigner.html>).&nbsp; This operation does not require a PowerDesigner license.&nbsp; We suggest you test both the PowerDesigner and the XSD routes, and compare the results. &nbsp;

&nbsp;

In any case, you should always validate the imported model, as some customers reported that their Erwin models were not up-to-date with reality anyway...&nbsp; This can be done for example by doing the reverse-engineering from the corresponding production database, then doing a [compare \& merge](<Compareandmergemodels.md>) operation.&nbsp;

&nbsp;

If you have data models in erwin and want to leverage them in Hackolade Studio, you need to fist export them to XSD, following the instructions below.&nbsp; You should first consult [this page](<XSDXMLSchemaDefinition.md>) for an overview of the import functionality in Hackolade Studio.

&nbsp;

By default ERwin does not export primary key and foreign key constraints.&nbsp; If the XSD does not contain this information, this reverse-engineering process cannot import them, but it is still possible to use the functionality to [Infer PKs \& FKs](<InferPrimaryKeysandForeignKeyRel.md>).

&nbsp;

It is suggested to use the parameters below when exporting models to XSD,&nbsp;

\- if from a physical model:

![ERwin XSD export parameters - physical](<lib/ERwin XSD export parameters - physical.png>)

&nbsp;

\- if from a logical model:

![Image](<lib/ERwin XSD export parameters - logical.png>)

&nbsp;

## Import XSD into Hackolade Studio

After the successful export of your model to XSD, use the instructions in [this page](<XSDXMLSchemaDefinition.md>) to import the XSD into a Hackolade Studio model for the target of your choice.

&nbsp;

With logical models exported from erwin, spaces in object names are generally replaced with underscores.&nbsp; When importing those models into a Hackolade Studio polyglot model, it might be desirable to restore object names to a regular business name.&nbsp; To that effect, we provide the option to perform a case conversion upon import.&nbsp; Proper Case or Title Case are likely candidates for this option.

&nbsp;

If your erwin models contains Erwin "domains", it is preferable to "resolve references" so that the properties in the Hackolade Studio model remain editable (while being originally created with the properties of the Erwin domains.)

![Erwin reverse-engineer resolved references](<lib/Erwin reverse-engineer resolved references.png>)

&nbsp;

If you want to keep the Erwin domains as Hackolade Studio User-Defined Types/Model Definitions for future use, then you should do a double import:

&#49;) first you reverse-engineer the XSD without resolving the references

&#50;) then you reverse-engineer the XSD immediately again, this time with resolution of the references, and when presented with the conflict resolution screen, make sure to use the Replace option:

![Erwin model import conflict resolution](<lib/Erwin model import conflict resolution.png>)

&nbsp;

&nbsp;

## Export subject areas from erwin

For a given data model exported to XSD and imported into Hackolade Studio, you may also transfer the erwin subject areas to easily create the corresponding ERD Views (ERDVs) in the imported Hackolade Studio model.

&nbsp;

The first step is to create in erwin a Subject Area report in CSV format, following the erwin [Report Designer](<https://bookshelf.erwin.com/bookshelf/public\_html/2019R1/Content/Installation/Implementation/create\_rep\_report\_designer.html> "target=\"\_blank\"") instructions.&nbsp; For [Subject Area Reports](<https://bookshelf.erwin.com/bookshelf/public\_html/2020R1/Content/Installation/Implementation/Subject%20Area%20Reports.html> "target=\"\_blank\""),&nbsp; you should not include the \<model\> subject area which is the main ERD and was already imported via the XSD step. &nbsp;

&nbsp;

**Important:** since the model name is not included when you generate a Subject Area report, you must be careful and possibly use corresponding naming of the CSV file.

&nbsp;

## Import subject areas into Hackolade Studio

Like for all bulk operations in Hackolade Studio, this operation is performed via the [Excel export](<Excelfile.md>) and [import](<Exceltemplate.md>) capability.

&nbsp;

The steps are as follows:

&#49;) open in Hackolade Studio the data model previously imported from the XSD file

&#50;) go to Tools \> Forward-Engineer \> Excel file... and choose the location for storing your Excel file

&#51;) open in Excel the Subject Area Report.csv file.&nbsp; It contains 2 columns and several rows, for example:

![ERwin - Subject Area Report CSV](<lib/ERwin - Subject Area Report CSV.png>)

&nbsp;

&#52;) go to the ER Diagram Views tab of the Excel file for the model exported in step 2) and paste the 2 columns from the Subject Area report with the following mapping:

\- "Subject Area Name" column of the Subject Area Report must copied and pasted into the "ERDV Name" column of the model Excel

\- "Entity Name" column of the Subject Area Report must be copied and pasted into the "Entity Name" of the model Excel

![ERwin - Subject Area Report pasted in Excel](<lib/ERwin - Subject Area Report pasted in Excel.png>)

&nbsp;

&#53;) save the Excel file

&#54;) back in Hackolade Studio with the model file open, go to Tools \> Reverse-Engineer \> Excel Template... and select the model Excel saved in the previous step

&nbsp;

Assuming that the Subject Area report matched the model file, the name matching of entities should work as expected and ERDVs will be created in the model:

![Image](<lib/ERwin - Subject Areas created as ERDVs.png>)

&nbsp;

&nbsp;

&nbsp;

## Export User-Defined Properties

In Erwin, you can define custom properties and assign them to the different classes of model objects. These user-defined properties (UDPs) are properties that you create to document and notate the logical and physical object classes.&nbsp; This is equivalent to our own Hackolade Studio [custom properties](<Userdefinedcustomproperties.md>).&nbsp; When migrating your library of Erwin models to Hackolade Studio, it is of course critical to keep those UDP's accumulated with our models.

&nbsp;

![Erwin User-Defined Properties](<lib/Erwin User-Defined Properties.png>)

&nbsp;

Unfortunately, the proprietary format of Erwin files complicates matters, plus the export to XSD does not include UDPs.&nbsp; It is therefore necessary to proceed with some additional steps outlined below:

&nbsp;

One-time setup in Hackolade Studio:

&#49;) Create custom properties for the target or targets, following instructions in this [how-to guide](<https://hackolade.com/help/Configurecustomproperties.html>) and [video](<https://community.hackolade.com/slides/slide/user-defined-custom-properties-8>).&nbsp; This should be done at the entity/table level and attribute/column/field level.&nbsp; If you have many UDPs for each level, it may be useful to create a custom tab for your custom properties.

&nbsp;

In Erwin:&nbsp;

&#50;) From the model file, generate the XSD according to the instructions above in this page.

&#51;) Use the Report Designer to create a report including UDPs at the entity/table level and attribute/column level, then create the export for your model.&nbsp;

&nbsp;

In Hackolade Studio

&#52;) Import the XSD into a Hackolade Studio data model.&nbsp; Save it.

&#53;) Generate the Excel export for your Hackolade data model, using [these instructions](<Excelfile.md>).

&nbsp;

In Excel:

&#54;) The export will include empty Excel columns for each of the custom properties defined in step 1):

![Erwin UDPs - HCK model export headings](<lib/Erwin UDPs - HCK model export headings.png>)

&nbsp;

&#55;) For each cell of the custom props columns that you wish to populate, you can create an [XLOOKUP](<https://support.microsoft.com/en-us/office/xlookup-function-b7fd680e-6d10-43e6-84f9-88eae8bf5929> "target=\"\_blank\"") Excel function to find the appropriate cell value in the Excel generated from the Erwin model, for example:

&nbsp;

> \=IF(XLOOKUP($B2,'\[User Defined Property values.xlsx\]Table Level UDP'\!$C$3:$C$6,'\[User Defined Property values.xlsx\]Table Level UDP'\!$K$3:$K$6)=0,"",XLOOKUP($B2,'\[User Defined Property values.xlsx\]Table Level UDP'\!$C$3:$C$6,'\[User Defined Property values.xlsx\]Table Level UDP'\!$K$3:$K$6))

&nbsp;

Great care must be applied to ensure that the proper values are set in the right places.&nbsp; The above can be customized and enhanced with additional logic.

&nbsp;

&#56;) Save the Excel file.

&nbsp;

Back in Hackolade Studio:

&#57;) Import the Excel file into the Hackolade Studio model, using [these instructions](<Exceltemplate.md>).

&#49;0) Double-check that the result corresponds to your expectations.

&nbsp;

