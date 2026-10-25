# From ER/Studio

## Differences with ER/Studio

There are many differences between Hackolade Studio and ER/Studio. We do not use or even have a copy of that software. No one in our organization has ever worked with it. Hackolade's ambition is certainly not to copy ER/Studio, ... to the contrary! It should be expected, since Hackolade Studio is a different tool than ER/Studio, that some things would work differently, that we would name some things differently, that features we have don’t exist in ER/Studio, and vice versa.

&nbsp;

Here are some examples, but there are many, many more…

- ER/Studio uses the term "submodels" to divide model diagrams into logical sections. We have “[Diagram Views](DiagramViews.md)”. The purpose may be somewhat similar. Terminology, and how they function may be different
- ER/Studio uses the term "domain", a term interpreted differently by different people, for sure to describe something quite different than what we describe as a [re-usable object definition](Reusableobjectsdefinitions.md) or user-defined type
- When creating foreign key relationships in ER/Studio, the convention is that you drag from the attribute PK in the parent entity towards the child entity. The attribute is automatically created in the child entity and the FK relationship is also created. Hackolade Studio also supports this approach, but it is not the default behavior. To change the default to be like ER/Studio, simply change the parameter "FK relationships drag-n-drop behavior" in Tools > Options > General to become "from parent to child".
- ER/Studio has a complex model comparison approach. With the [architecture of Hackolade Studio](WhylegacyandSaaSdatamodelingarch.md), models are in JSON format and are stored in Git repositories where versioning is automatic, and each commit and push results in an immutable version of the model. As a result, a [compare and merge](Compareandmergemodels.md) operation in Hackolade Studio always results in a "third" model, instead of an alteration of existing model versions. Note also that it is possible to [compare two arbitrary commits](<https://hackolade.com/help/Explorehistory.html#Compare%20commits>). Whatever the way ER/Studio compares models, for sure, Hackolade Studio's equivalent feature will work completely differently.
- ER/Studio allows to open multiple models in the same application instance. The architecture of Hackolade Studio being different, we allow to start multiple instances of the application, each with a single model. This is actually quite handy, as it allows to alt-tab to toggle between different models. As indicated in our [Tips and Tricks](Tipsandtricks.md), you may start multiple instances of Hackolade Studio on the same machine session, so as to work on multiple models simultaneously. You may also merge 2 Hackolade models, or combine elements from another model with copy/paste from one model in one application instance, to the other model in the second application instance. From within the application, this is easily done with the shortcut Ctrl+Shift+I (on Mac Cmd+Shift+I) or with the menu option File > Start New Application Instance. Or from the operating system, on Windows, right-click on the Hackolade icon in the toolbar then choose Hackolade...
- ER/Studio has a rigid storage structure in its central repository structure. The architecture of our solution is very different from ER/Studio’s. Our model files are not binary in a proprietary format, but open in JSON format, and each file represents a single model. Models can be stored in one or more Git repositories, possibly even across multiple repository providers. Models can be organized in a more flexible modular approach, as described [here](<https://hackolade.com/help/PolyglotDataModeling.html#Flexibility>). With our modular architecture, it is possible for a physical model to be derived from 1 or more (subsets of) polyglot models. It is also possible for any model to reference any part of any model, no matter the target on each side.

&nbsp;

Legacy tools have been using the traditional concept of “logical” models, which is too constraining for the needs of non-RDBMS targets supported by Hackolade Studio. Hackolade had to invent the principles of [Polyglot Data Modeling](https://hackolade.com/polyglot-data-modeling.html) to support the needs of NoSQL, Avro, Parquet, REST APIs, etc… We name it Polyglot, as opposed to logical, to avoid any semantic confusion or discussion. But our Polyglot models are logical in the sense that they are technology-agnostic, and they can be fully normalized. But they can be much more than strict logical models in the sense that they can optionally support nested objects, polymorphism, and denormalization.\
Polyglot models can be purely "logical", in the traditional sense. But they can also be more of a "common physical model", including technical names or views that would be common across different physical targets. No dogma with Hackolade: you can be as rigorous in applying data modeling theory as you wish, or less rigorous in order to adhere to the reality of your organization.

&nbsp;

Physical data models can be [derived from](PolyglotDataModel.md) polyglot models. It is also possible to start from a physical data model (either from scratch or created from the reverse-engineering of an instance) and convert it to a polyglot model.\
Once a target model is linked to one or more polyglot models, any change in the polyglot model can be reviewed through an [Impact Analysis](<https://hackolade.com/help/PolyglotDataModel.html#Impact%20Analysis>) screen to decide whether to include the changes, globally or individually.\
Polyglot models can be derived from (subsets of) other polyglot model(s), as described [here](<https://hackolade.com/help/PolyglotDataModeling.html#Flexibility>). In the end, it is possible to create a graph of models.

- In ER/Studio when creating a physical model from a logical model, the physical model is "generated" (or "derived") from the logical model in a "**push**" process. In Hackolade Studio, the process is different, partly due to the fact that Hackolade Studio supports so many targets that are different than RDBMS. And also because in Hackolade Studio, it is possible to build an N-to-N graph of data models, where for example a model draws from more than one polyglot model. As a result in Hackolade Studio, the process follows a "**pull**" mechanism: you would first create a physical model for the target of our choice, then "derive" from the selected polyglot model or models.

&nbsp;

Given the above, it should be expected that there is some learning curve to our tool. You will most likely avoid frustration if you don't assume, because you're a veteran user of ER/Studio, that you can use Hackolade Studio without learning about it. This learning curve can be greatly reduced by investing a little bit of time in reading or searching inside our [online documentation](WelcometoHackoladeStudio.md), going through [tutorials](Tutorial.md) and [how-to guides](How-toguides.md), and by watching some of the videos on our [eLearning platform](<https://community.hackolade.com/slides/all> "target=\"_blank\"").

&nbsp;

## Export a data model from ER/Studio

If you have data models in ER/Studio and want to leverage them in Hackolade Studio, you need to fist export them to XSD, following the instructions below. You should first consult [this page](XSDXMLSchemaDefinition.md) for an overview of the import functionality in Hackolade Studio.

&nbsp;

By default ER/Studio does not export primary key and foreign key constraints. If the XSD does not contain this information, this reverse-engineering process cannot import them, but it is still possible to use the functionality to [Infer PKs & FKs](InferPrimaryKeysandForeignKeyRel.md).

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

![ER-Studio Wizard - page 3 datatype](<lib/ER-Studio Wizard - page 3 datatype.png>)

&nbsp;

![ER-Studio Wizard - page 3 name conversion](<lib/ER-Studio Wizard - page 3 name conversion.png>)

&nbsp;

Knowing that the export function does not work with all version of ER/Studio, another option is to use the MetaWizard export in XSD format:\
![ER-Studio Wizard - Meta export](<lib/ER-Studio Wizard - Meta export.png>)

&nbsp;

## Import XSD into Hackolade Studio

After the successful export of your model to XSD, use the instructions in [this page](XSDXMLSchemaDefinition.md) to import the XSD into a Hackolade Studio model for the target of your choice.
