# API Model

## Model-driven API generation

Previously, Hackolade allowed the import of different formats (JSON documents, JSON Schema, DDLs, XSDs) into an OpenAPI or Swagger model as schema components (or Swagger definitions.) &nbsp; While already useful, this feature highlighted the possibility to further automate and facilitate the creation of APIs based on existing data models: using an ERD (entity-relationship diagram) to automatically generate the API for CRUD operations of the entities of that data model.&nbsp; For any target for which Hackolade support data modeling: JSON Schema, MongoDB, Cassandra, Avro, Parquet, Hive, Neo4j, Cosmos DB, Couchbase, DynamoDB, Elasticsearch, Snowflake, SQL Server, Azure SQL, Synapse, etc...

&nbsp;

It is no longer necessary to export a Hackolade model to JSON Schema, then import it into an OpenAPI model, before manually going through the repetitive task of creating resources for CRUD operations.&nbsp; With version 4.2.0, Hackolade is introducing this handy new feature at the request of many customers: the ability to directly generate an OpenAPI (or Swagger) model and documentation from any Hackolade model target.&nbsp; This feature will help make your APIs more consistent than those produced by hand, while easily exposing resources for underlying data sources.&nbsp; API maintenance will be greatly facilitated, and Total Cost of Ownership reduced.

&nbsp;

Furthermore, it is now possible to automatically create resources (request and responses) for each entity of the source data model, based on a user-defined template.&nbsp; The template can be defined in different ways: a Hackolade model file for Swagger or OpenAPI, or an actual Swagger/OpenAPI documentation file in either JSON or YAML.

&nbsp;

For this feature to work, it is required to have the OpenAPI (or Swagger if applicable) plugin installed.

&nbsp;

## Process

The process is as follows:

&nbsp;

![Image](<lib/API%20process.png>)

&nbsp;

&#49;) Open or create a Hackolade model with entities: collections for MongoDB, tables for Cassandra/Hive/RDBMS, node labels and relationship types dfor Neo4j, etc...

&#50;) Go to Tools \> Forward-Engineering \> API model and choose a previously defined template to use for the merge operation

&#51;) Hackolade will generate an OpenAPI (or Swagger) model, and optionally the corresponding documentation file.

&nbsp;

## Data model

Any Hackolade data model can serve as a basis for this process.&nbsp; Each entity (collection, table, node label, view, relationship type, etc...) of the model will serve as a basis for the creation of a schema component/definition in the API model, so CRUD operations could be generated for each entity.

&nbsp;

## Template&nbsp;

An API template is typically a Hackolade model itself, but it can also be an OpenAPI or Swagger documentation file in either JSON or YAML&nbsp; The template is user-defined and used by the process to control the creation of the API for the source model.

&nbsp;

You will find on our sample model [page](<https://hackolade.com/samplemodels.html#api> "target=\"\_blank\"") a sample template that can serve as a basis for your own template.&nbsp; You will see the following screen if you open the OpenAPI sample template:

![Image](<lib/API%20template.png>)

&nbsp;

The template contains:

\- API metadata in the properties pane which should be edited to your specific context and standards;

\- a resource named "entities" containing 1 request (a POST operation) with 5 responses (201 (Created), 400 (Bad request), 401 (Unauthorized), 403 (Forbidden), and 500 (Internal server error)

\- a resource named "entities/{id}" with 3 request: PUT, GET, DELETE, each with its own set of responses

\- a components section (definitions for Swagger) with re-usable schema and response components.

&nbsp;

Feel free to adjust the template to the behavior that best suits your operation, knowing that you'll still be able to edit the generate model anyway.&nbsp; You may add or change metadata, resources, requests, and responses.

&nbsp;

**IMPORTANT:** do NOT change the keywords "entities" and "entity" in the template, as the merge process hinges on their presence in the template.

&nbsp;

## API generation

The application will perform the following operations while creating the destination API model:

\- import each entity from the source model and create schema components

\- create responses components from the template

\- perform the cartesian product of each entity of the source model with each resource of the template, including requests and responses

&nbsp;

## Options

The function is accessible through Tools \> Forward-Engineering \> API Model...

![Image](<lib/API%20model%20menu.png>)

&nbsp;

You may choose either OpenAPI 3 or Swagger 2 as a destination version.

&nbsp;

You are presented with the usual dialog for object select; and you may unselect entities you do not wish to include in the API generation:&nbsp;

![Image](<lib/API%20entity%20selection.png>)

You must choose a valid template, either in a Hackolade model format, or in an OpenAPI or Swagger documentation file (either in JSON or YAML.) &nbsp;

&nbsp;

**Important note:** the version of template must be compatible with your output version choice.&nbsp; If you choose to output to an OpenAPI 3 model, you must choose an OpenAPI 3 template, i.e. not a Swagger 2 template.&nbsp; And vice-versa.

&nbsp;

You will be prompted for the destination path where the resulting model should be saved.

&nbsp;

Depending on the size of both your source model and your template, the process may take a few minutes.&nbsp; If you have selected to create an OpenAPI documentation file, you will be prompted for the destination path where the resulting OpenAPI documentation file should be saved.

&nbsp;

![Image](<lib/API%20doc%20generation%20info%20dialog.png>)

At the end of the process, you will be asked if you wish to open the resulting API model to be opened in a separate Hackolade instance:

&nbsp;

![Image](<lib/API%20model%20generation%20success%20dialog.png>)

