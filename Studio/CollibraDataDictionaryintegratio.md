# Collibra Data Dictionary integration

**Important note:** Collibra started to provide its Data Intelligence platform in 3 packages: Standard, Premier, and Ultimate.&nbsp; Our integration with Collibra, was historically developed based on functionality that was previously included by default.&nbsp; Now, a "Federated Operating model" is required but only as part of the "Ultimate" package.&nbsp; The Federated Operating model can be procured for an add-on price, even with the Standard and Premier packages.&nbsp; Please contact your Collibra sales account executive. &nbsp;

&nbsp;

For our standard Collibra integration, we must be able to create [scopes](<https://productresources.collibra.com/docs/collibra/latest/Content/Settings/OperatingModel/Scopes/to\_scopes.htm> "target=\"\_blank\"") and scope assignments which are required in order to support the advanced integration necessary for graph database, REST APIs, nested hierarchies, and polymorphism. &nbsp;

&nbsp;

If you do not have the Ultimate package and did not get the Federated Operating model add-on, then starting with v8.3.6, we provide an integration, albeit with some graceful degradation, some limitations, and some required manual configuration described [in this page](<Non-Ultimateeditionintegration.md>).

&nbsp;

## Ultimate Edition integration

One of the primary challenges severely constraining organizations is to make business sense of technical data structures in applications and databases.&nbsp; This complicates the ability of organizations to identify critical data elements and bring them under governance. &nbsp;

&nbsp;

The integration of data modeling with governance tools and processes enables solving this problem at the source, i.e. where data structures are designed to create schemas and their technical metadata. &nbsp;

&nbsp;

**Note:** You may wish to view the [how-to video](<https://youtu.be/6UA1Ys\_OlMY> "target=\"\_blank\"") on this subject.

&nbsp;

**Important note:** the Collibra integration is an add-on feature which requires a specific license key which can be purchased from us [here](<mailto:support@hackolade.com?subject=Collibra%20integration%20license>).

&nbsp;

[Collibra](<https://www.collibra.com/> "target=\"\_blank\"") is one of the leaders in the space of data governance and metadata management solutions.&nbsp; Metadata management is a core aspect of an organization’s ability to manage its data and information assets. The term “metadata” describes the various facets of an information asset that can improve its usability throughout its life cycle. Metadata is used as a reference for business-oriented and technical projects, and lays the foundations for describing, inventorying and understanding data for multiple use cases.

Hackolade has partnered with Collibra to provide an officially supported integration with Collibra's Data Dictionary, using its [Core, Import, and output module APIs](<https://developer.collibra.com/rest/#apis> "target=\"\_blank\"").&nbsp; With this integration, users can easily publish into Collibra domains, and keep synchronized, their Hackolade data models for any of the many targets supported by Hackolade.&nbsp; Even the schema definitions of REST APIs documented in Swagger or OpenAPI.

The process automatically:

* checks the configuration in Collibra
* creates the necessary custom scopes, attributeTypes and assignments to support the granularity of Hackolade features
* then creates and keeps in sync assets for schemas, tables, views, columns, models, entities, attributes, and foreign key relationships.

The integration specifically handles complex data types, hierarchical structures, and polymorphism found in modern databases, JSON, Avro, Parquet, Protobuf, etc...&nbsp; Custom properties defined for a plugin are also published as custom attributeTypes in Collibra.

Hackolade Studio data models for physical targets are published to Physical Data Dictionaries in the form of schemas/tables/columns assets in Collibra, whereas since v7.3.1 of Hackolade Studio, Polyglot models are published to Logical Data Dictionaries in the form of models/entities/attributes assets in Collibra.

With v7.6.1 of Hackolade Studio, we added publishing of lineage relations between logical Polyglot models and their derived physical targets for all their assets (model/schema, entity/table, attribute/column)

## Publishing process flow

To publish a Hackolade data model to your Collibra Data Dictionary, you choose Tools \> Forward-Engineering \> Collibra Dictionary. &nbsp;

The diagram below describes the integration flow:

![Collibra integration flow](<lib/Collibra integration flow.png>)

&nbsp;

### Connect to your Collibra instance

See mode details in [this page](<Connectionandauthentication.md>).

### Check for the proper configuration

To ensure successful processing of the Hackolade model information, the system uses the [Core API](<https://developer.collibra.com/rest/rest-core-api/> "target=\"\_blank\"") to check that the Collibra setup is OK, and if not, asks the user for permission to create the necessary setup.

&nbsp;

The system will:

&#49;) confirm that the necessary [out-of-the-box assetTypes](<https://productresources.collibra.com/docs/collibra/latest/Content/Assets/AssetTypes/ref\_ootb-asset-types.htm> "target=\"\_blank\"") exist: model, entity, attribute, schema, table, database view, column, foreign key, mapping specification

&#50;) confirm that the necessary [out-of-the-box attributeTypes](<https://productresources.collibra.com/docs/collibra/latest/Content/Assets/Characteristics/Attributes/AttributeTypes/ref\_attribute-types.htm> "target=\"\_blank\"") exist: description, comment, scale, etc...

&#51;) confirm that the necessary [out-of-the-box relationTypes](<https://productresources.collibra.com/docs/collibra/latest/Content/Assets/Characteristics/Relations/RelationTypes/ref\_relation-types.htm> "target=\"\_blank\"") exist: schema contains table, and table contains column

&#52;) confirm that the necessary [out-of-the-box complexRelationTypes](<https://productresources.collibra.com/docs/collibra/latest/Content/Assets/Characteristics/ComplexRelations/ComplexRelationTypes/ref\_complex-relation-types.htm> "target=\"\_blank\"") exist

&#53;) confirm that the necessary Hackolade setup exists:

\- custom attribute scope and scope assignments

\- custom attributeTypes to handle Hackolade-specific information

\- custom assignments of attributeTypes to out-of-the-box assetTypes: model, entity, attribute, schema, tables, database views, columns

\- custom characteristics for schema, table, columns, and database views

\- custom relationType "Column contains Column" to allow hierarchical view of nested objects, arrays, and polymorphism

&nbsp;

If the expected configuration cannot be found in Collibra, the user is prompted for confirmation that the setup should be automatically carried out in the Collibra instance.

![Image](<lib/Collibra missing config warning.png>)

### Fetch existing Communities and Domains

If the configuration is correct, the application uses the Core API to retrieve the existing Communities and Domains and display them so the user can select where the Hackolade Data Model should be loaded.&nbsp; If the domain does not exist, it should be created first.&nbsp; It is recommended to create a new domain with type "Physical Data Dictionary" for physical models of Hackolade Studio, and "Logical Data Dictionary" for polyglot models.

![Collibra create domain](<lib/Collibra create domain.png>)

### Select the target domain

For performance reasons, we do not display all the communities and domains.&nbsp; Instead you must expand the tree and fetch the domains for the relevant community.&nbsp; Once the domains are displayed in the box below, you can select the one where the Hackolade data model should be published:

![Collibra resource selection](<lib/Collibra resource selection.png>)

&nbsp;

### Select the data model objects to be loaded

The user then selects the entities to be loaded to the selected Collibra domains:

![Collibra object selection](<lib/Collibra object selection.png>)

&nbsp;

### Publish data model to Collibra

The application uses the [Import API](<https://developer.collibra.com/rest/rest-import-api/> "target=\"\_blank\"") to bulk load the selected objects metadata and Entity-Relationship picture into the selected Collibra domain.&nbsp; The system leverages the [Synchronization API](<https://collibra-developer-portal.s3-eu-west-1.amazonaws.com/docs/import/Default.htm#API/ImportAPIv2/co\_synchronization-api.htm> "target=\"\_blank\"") to keep data in Collibra up-to-date with model evolutions when invoking the integration repeatedly.&nbsp; The synchronization is based on the internal model UUID.

**Important note:** According the Collibra [documentation](<https://collibra-developer-portal.s3-eu-west-1.amazonaws.com/docs/import/Default.htm#API/ImportAPIv2/to\_import-commands.htm#Resource> "target=\"\_blank\""), depending on the resource type, the Import API performs one of two operations: SET/REPLACE or MERGE.&nbsp; For attributes, the operation is SET/REPLACE.&nbsp; As a result, "if the resource exists with properties other than the ones defined in the input (i.e.; the Hackolade data model), the resource is replaced with the one provided in the input."&nbsp; Meaning that edits made in Collibra risk disappearing with subsequent publications from Hackolade.&nbsp; With the ability to reverse-engineer from Collibra into Hackolade, 2 approaches are possible:

&#49;) reverse-engineer from Collibra into the master Hackolade data model, and let the conflict resolution kick-in, letting the user decide whether to merge the information from Collibra.

![Conflict resolution](<lib/Conflict resolution.png>)

Once the information is merged into the hackolade model, the whole model can be published to Collibra again.

&#50;) a user might want to have more control over the granularity of what gets merged and what does not.  There is the possibility to reverse-engineer into an empty model, save it, then do a [Model Compare \& Merge](<Compareandmergemodels.md>) with the master Hackolade model, followed by the publishing back to Collibra of the merged model.

&nbsp;

## View data model in Collibra console

The data model information can immediately be viewed inside Collibra:

![Collibra view data models](<lib/Collibra view data models.png>)

&nbsp;

In order to view nested objects in the above screen, it is suggested to enable multipath hierarchy for the relation types: schema contains table, table contains column, and column contains column:

![Collibra configure hierarchy](<lib/Collibra configure hierarchy.png>)

&nbsp;

You may also display the Full Name field to view the nesting path in dot.notation, as well as the hackolade Data Type:

![Collibra fields config](<lib/Collibra fields config.png>)

&nbsp;

Users will notice that the data types of the specific target technology:

![Collibra data type view](<lib/Collibra data type view.png>)

&nbsp;

The Entity-Relationship Diagram image can also be viewed as a PNG file:

![Collibra view ERD file](<lib/Collibra view ERD file.png>)

&nbsp;

## Reverse-engineer a Collibra Data Dictionary

With v5.2.1, we introduced the possibility to reverse-engineer a Collibra physical data dictionary into a Hackolade data model for the target of your choice.&nbsp; This operation can be done:

\- either into an empty model you wish to create,

\- or into an existing model, possibly the one used to originally publish to Collibra.&nbsp; This is particularly handy if maintenance occurs in Collibra for models created in Hackolade Studio.&nbsp; Refer to the important note above in the section "Publish data model to Collibra".

&nbsp;

## Publish lineage relations

With v7.6.1 of Hackolade Studio, it is now possible to publish lineage relations between logical Polyglot models and their derived physical targets for all their assets (model/schema, entity/table, attribute/column)

This feature is in support of the [Guided Stewardship operating model](<https://productresources.collibra.com/docs/collibra/latest/Content/Catalog/GuidedStewardship/OperatingModel/to\_catalog-om.htm> "target=\"\_blank\"") of Collibra:&nbsp; But it is only possible Guided Stewardship is enabled on your instance as part of the Ultimate licensing tier of Collibra.

![Collibra Guided Stewardship operating model](<lib/Collibra Guided Stewardship operating model.png>)

&nbsp;

This process requires the orchestration of several successive operations:

\- publish to Collibra the Polyglot model(s) from which physical target models are derived in Hackolade.&nbsp; Each Polyglot model is typically published into a Collibra Logical Data Dictionary with the models/data entity/data attribute structure (possibly specifying the hierarchy "Data Attribute **contains** Data Attribute) ;

\- make sure to save the model(s) in Hackolade Studio, so the Collibra internal IDs are persisted in the Polyglot model(s);

\- open the derived model(s) in Hackolade Studio and make sure to refresh the references to parent Polyglot model(s), which will ensure that the links between objects are persisted in the derived model(s);

\- publish the derived model(s) to Collibra, generally into a Collibra Physical Data Dictionary (unless the derived model is itself a Polyglot model, in which case it would be published to a Logical Data Dictionary.)&nbsp;

In Collibra, it is then possible to display the lineage relations automatically created by Hackolade Studio during publishing.

![Collibra lineage](<lib/Collibra lineage.png>)

&nbsp;

If your instance of your Collibra Data Intelligence Platform is not of the the Ultimate type of subscription, you may receive messages like this below.

&nbsp;

Without Guided Stewardship on the Collibra instance, it is not possible to publish Hackolade Studio's polyglot models:

![Collibra Guided Stewardship missing](<lib/Collibra Guided Stewardship missing.png>)

&nbsp;

And without Guided Stewardship on the Collibra instance, it is not possible to publish lineage from physical models to polyglot models (since polyglot models cannot be published to Collibra...):

![Collibra Guided Stewardship limited lineage](<lib/Collibra Guided Stewardship limited lineage.png>)

