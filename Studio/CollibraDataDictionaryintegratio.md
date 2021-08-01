# Collibra Data Dictionary integration

**Note:** You may wish to view the [how-to video](<https://hackolade.com/videos.html#collibra> "target=\"\_blank\"") on this subject.

&nbsp;

[Collibra](<https://www.collibra.com/> "target=\"\_blank\"") is one of the leaders in the space of data governance and metadata management solutions.&nbsp; Metadata management is a core aspect of an organization’s ability to manage its data and information assets. The term “metadata” describes the various facets of an information asset that can improve its usability throughout its life cycle. Metadata is used as a reference for business-oriented and technical projects, and lays the foundations for describing, inventorying and understanding data for multiple use cases.

Hackolade has partnered with Collibra to provide an officially supported integration with Collibra's Data Dictionary, using its [Core and Import APIs](<https://developer.collibra.com/rest/#apis> "target=\"\_blank\"").&nbsp; With this integration, users can easily publish into Collibra domains their Hackolade data models for any of the many targets supported by Hackolade.&nbsp; Even the schema definitions of REST APIs documented in Swagger or OpenAPI.

The process automatically:

* checks the configuration in Collibra
* creates the necessary custom scopes, attributeTypes and assignments to support the granularity of Hackolade features
* then creates and keeps in sync assets for schemas, tables, views, columns, and foreign key relationships.

The integration specifically handles complex data types, hierarchical structures, and polymorphism found in modern databases, JSON, Avro, Parquet, ProtoBuf, etc...

&nbsp;

**Important note:** the Collibra integration is an add-on feature which requires a specific license key which can be purchased from us [here](<mailto:support@hackolade.com?subject=Collibra%20integration%20license>).

## Integration process flow

To forward a Hackolade data model to you Collibra Data Dictionary, you choose Tools \> Forward-Engineering \> Collibra Dictionary. &nbsp;

The diagram below describes the integration flow:

![Image](<lib/Collibra%20integration%20flow.png>)

&nbsp;

### Connect to your Collibra instance

In order to feed data model information to the Collibra instance, it is assumed that you have sufficient credentials to do so.&nbsp; If not, please contact your Collibra administrator.

&nbsp;

To connect to the Collibra instance, you must first specify connection settings:

![Image](<lib/Collibra%20connection%20settings.png>)

as well as authentication credentials:

![Image](<lib/Collibra%20authentication.png>)

&nbsp;

### Check for the proper configuration

To ensure successful processing of the Hackolade model information, the system uses the [Core API](<https://developer.collibra.com/rest/rest-core-api/> "target=\"\_blank\"") to check that the Collibra setup is OK, and if not, asks the user for permission to create the necessary setup.

&nbsp;

The system will:

&#49;) confirm that the [out-of-the-box assetTypes](<https://productresources.collibra.com/docs/user/5.7/#Assets/AssetTypes/ref\_ootb-asset-types.htm> "target=\"\_blank\"") exist: schema, table, database view, column, foreign key, mapping specification

&#50;) confirm that the [out-of-the-box relationTypes](<https://productresources.collibra.com/docs/user/5.7/#Assets/Characteristics/Attributes/AttributeTypes/ref\_attribute-types.htm> "target=\"\_blank\"") exist: schema contains table, and table contains column

&#51;) confirm that the Hackolade setup exists:

\- custom attribute scope

\- custom attributeTypes to handle Hackolade-specific information

\- custom assignments of attributeTypes to out-of-the-box assetTypes: schema, tables, database views, columns

\- custom characteristics for schema, table, columns, and database views

\- custom relationType "Column contains Column" to allow hierarchical view of nested objects, arrays, and polymorphism

&nbsp;

If the expected configuration cannot be found in Collibra, the user is prompted for confirmation that the setup should be automatically carried out in the Collibra instance.

### Fetch existing Communities and Domains

If the configuration is correct, the application uses the Core API to retrieve the existing Communities and Domains and display them so the user can select where the Hackolade Data Model should be loaded.&nbsp; If the domain does not exist, it should be created first.&nbsp; It is recommended to create a new domain with type "Physical Data Dictionary".

![Image](<lib/Collibra%20create%20domain.png>)

### Select the target domain

All communities and domains are displayed in the box below so the user can select the one where the Hackolade data model should be loaded:

![Image](<lib/Collibra%20resource%20selection.png>)

&nbsp;

### Select the data model objects to be loaded

The user then selects the entities to be loaded to the selected Collibra domains:

![Image](<lib/Collibra%20object%20selection.png>)

&nbsp;

### Publish data model information to Collibra

The application uses the [Import API](<https://developer.collibra.com/rest/rest-import-api/> "target=\"\_blank\"") to bulk load the selected objects metadata and Entity-Relationship picture into the selected Collibra domain.&nbsp; The system leverages the [Synchronization API](<https://collibra-developer-portal.s3-eu-west-1.amazonaws.com/docs/import/Default.htm#API/ImportAPIv2/co\_synchronization-api.htm> "target=\"\_blank\"") to keep data in Collibra up-to-date with model evolutions when invoking the integration repeatedly.&nbsp; The synchronization is based on the internal model UUID.

**Important note:** the master for the data catalog information is the Hackolade data model.&nbsp; According the Collibra [documentation](<https://collibra-developer-portal.s3-eu-west-1.amazonaws.com/docs/import/Default.htm#API/ImportAPIv2/to\_import-commands.htm#Resource> "target=\"\_blank\""), depending on the resource type, the Import API performs one of two operations: SET/REPLACE or MERGE.&nbsp; For attributes, the operation is SET/REPLACE.&nbsp; As a result, "if the resource exists with properties other than the ones defined in the input (i.e.; the Hackolade data model), the resource is replaced with the one provided in the input."&nbsp; Meaning that edits made in Collibra risk disappearing with subsequent publications. &nbsp;

## View data model in Collibra console

The data model information can immediately be viewed inside Collibra:

&nbsp;

![Image](<lib/Collibra%20view%20data%20models.png>)

&nbsp;

In order to view nested objects in the above screen, it is suggested to enable multipath hierarchy for the relation types: schema contains table, table contains column, and column contains column:

![Image](<lib/Collibra%20configure%20hierarchy.png>)

&nbsp;

You may also display the Full Name field to view the nesting path in dot.notation, as well as the hackolade Data Type:

![Image](<lib/Collibra%20fields%20config.png>)

&nbsp;

Users will notice that the data types of the specific target technology:

![Image](<lib/Collibra%20data%20type%20view.png>)

&nbsp;

The Entity-Relationship Diagram image can also be viewed as a PNG file:

![Image](<lib/Collibra%20view%20ERD%20file.png>)

&nbsp;

&nbsp;

