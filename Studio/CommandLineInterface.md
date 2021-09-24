# Command Line Interface

With its Command Line Interface (CLI), Hackolade truly supports an agile development approach leveraging the flexibility of NoSQL dynamic schemas.&nbsp; Some Hackolade customers use this capability nightly in a batch process to identify attributes and structures that may have appeared in the data since the last run.&nbsp; During a nightly run of the reverse-engineering function, a much larger dataset can be queried as a basis for document sampling, hence making schema inference more precise. Such capability can be useful in a data governance context to properly document the semantics and publish a thorough data dictionary for end users.&nbsp; It can also be used in the context of compliance with privacy laws to make sure that the company does not store data that it is not supposed to store.&nbsp; There are many more examples of how to use this functionality.

&nbsp;

It is often helpful, in order to understand how to set the different CLI arguments, to first run the equivalent function in the GUI application.

&nbsp;

It is easier to run the CLI from the directory where the Hackolade executable is installed, from a terminal program:

* Windows:&nbsp;
  * cmd command line: all commands below should be preceded by *start /wait hackolade *
  * PowerShell: all commands below should be preceded by *Start-Process -wait hackolade&nbsp; *
* Mac: start Terminal and execute: all commands below should be preceded by */Applications/Hackolade.app/Contents/MacOS/Hackolade *
* Linux: terminal emulator or common shell programs: all commands below should be preceded by *./Hackolade*&nbsp; or *path-to-where-hackolade-was-unzipped/Hackolade *

> &nbsp;

To take full advantage of the capability, you may run the CLI from scheduled batch files. &nbsp;

&nbsp;

**Note:** a properly licensed copy of Hackolade is required to run the CLI.&nbsp; The CLI functionality is only available in the Professional and Trial editions of Hackolade.

&nbsp;

Below is the current list of Hackolade CLI commands.&nbsp; Additional commands may be added at a later date.

&nbsp;

| **Command** | **Purpose** |
| --- | --- |
| genDoc | Generate documentation for a Hackolade model, in HTML, Markdown, or PDF format |
| revEng | Reverse-engineer a database instance or script file to infer the schema of the selected collections/tables |
| revEngJSON | Reverse-engineer JSON Schema or documents |
| revEngYAML | Reverse-engineer YAML or YAML Schema files |
| revEngDDL | Reverse-engineer RDBMS data definition language files with .sql extensions |
| revEngXSD | Reverse-engineer XSD files with .xsd extensions |
| compMod | Compare two Hackolade models to detect differences, and optionally merge them |
| forwEng | Forward-engineer structure created with the application to dynamically generate the schema of the selected entities.&nbsp; Or forward-engineer JSON Schema or a sample JSON data document |
| forwEngAPI | Forward-engineer Swagger or OpenAPI model from merge of a source data model and a user-defined template |
| forwEngDataDictionary | Publish Hackolade data model to Data Dictionary instance |
| obfusc | Copy a model, and garble sensitive properties: business name, technical name, description, comments, enumeration.  Use if you need to send a model for troubleshooting but don't want to disclose sensitive aspects of the model. |
| help | Display commands and their arguments |
| performance | Records timestamps of application startup steps for performance troubleshooting |
| version | Display application version |


&nbsp;

&nbsp;

Usage: &nbsp; &nbsp; *hackolade command \[--arguments\]*

&nbsp;

## genDoc

The *genDoc* command lets you invoke the generation of a documentation file, either in HTML or PDF format, for a specified existing Hackolade model.

&nbsp;

Usage:&nbsp; &nbsp; *hackolade genDoc \[--arguments\]*

&nbsp;

| **Argument** | **Required** | **Purpose** |
| --- | --- | --- |
| \--format=\<HTML \| Markdown&nbsp; \|&nbsp; PDF\> | Y | Specify format, currently either HTML, MARKDOWN, or PDF |
| \--model=\<*file*\>\* | Y | Full path and file name for source Hackolade model for which documentation is being generated.&nbsp; Extension .json is optional |
| \--doc=\<*file*\>\* | Y | Full path and file name for documentation.&nbsp; Extension .html , .md, or .pdf is optional |
| \--logo=\<*file*\>\* | N | Full path and file name for custom logo file.&nbsp; If omitted, Hackolade logo is used |
| \--displayName=\<**business** \| technical\> | N | Define whether to display business or technical names \[values: "business", "technical"\] \[default: business\]&nbsp; |
| \--diagram=\<**true** \| false\> | N | Include model diagram \[default: true\] |
| \--diagramViews=\["\<*ERDV1\>"*,"\<*ERDV2\>"*,…\]" | N | Specify an array of diagram views to be included.&nbsp; The value is a string surrounded by double quotes (").&nbsp; ER Diagram View names are represented as an array surrounded by square brackets (\[\]), and are separated by a comma (,).&nbsp; \[default: all\] |
| \--sepContDiag=\<**true** \| false\> | N | Include separate container diagrams (database, region, buckets, keyspaces...)&nbsp; \[default: true\] |
| \--entityDiagrams=\<**true** \| false\> | N | Include entity hierarchical schema diagrams \[default: true\] |
| \--attribTree=\<**all** \| complex \| none\> | N | Include individual hierarchical schema view for all attributes \[all\], for complex attributes only \[complex\], or for no attributes \[none\]. \[default: all\] |
| \--properties=\<**all** \| notNull \| none\> | N | Include all field properties \[all\], only field properties with information \[notnull\], or no field properties \[none\]. \[default: all\] |
| \--relationships=\<**true** \| false\> | N | Include Relationships \[default: true\] |
| \--JSONSchema=\<**true** \| false\> | N | Include JSON Schema code \[default: true\] |
| \--JSONData=\<**true** \| false\> | N | Include JSON Data sample \[default: true\] |
| \--entities="\<containerName\>: \[\<*entity1\>*,\<*entity2\>*,…\]" | N | Specify container(s) to include in documentation \[default: all\] and an array of entities \[default: all\] - MongoDB: container = dbs; entity = collection - DynamoDB: container = *not applicable*; entity = table - Couchbase: container = bucket; entity = document kind - Cosmos DB: container = collection; entity = document type - plain JSON: container = group; entity = document The value is a string surrounded by double quotes (").&nbsp; Entities are represented as an array surrounded by square brackets (\[\]), and are separated by a comma (,).&nbsp; The entities array is separated from the container name by a colon (:). &nbsp; Containers are separated by semi-colons (;). |
| \--views="\[\<view1\>, \<view2\>, ...\]" | N | In MongoDB only, specify view(s) to include in documentation \[default: all\] The value is a string surrounded by double quotes (").&nbsp; Views are represented as an array surrounded by square brackets (\[\]), and are separated by a comma (,). |
| \--openDoc=\<true \| **false**\> | N | Specify whether to open the generated document or not upon completion of generation. \[default: false\] |
| \--logLevel=\< 1 \| 2 \| 3 \| **4** \> | N | &#49; = no spinner, no info, no error messages 2 = no spinner, no info 3 = no spinner 4 = full output \[default: 4\] |


\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“)&nbsp; Path can be ignored if file is in local directory.

&nbsp;

Simple example: using all default options: &nbsp;

> start /wait hackolade genDoc --format=HTML --model=C:\\Users\\Public\\Bitbucket\\hackolade\\schemas\\MongoDB\\noaa.json \
\--doc=C:\\Users\\Public\\Documents\\Hackolade\\Documentation\\noaa.html

&nbsp;

More complex example:&nbsp;

> start /wait C:\\PROGRA~1\\Hackolade\\hackolade genDoc --format=HTML --model=C:\\Users\\Public\\Bitbucket\\hackolade\\schemas\\Couchbase\\travel-sample.json \
\--doc=C\\Users\\Public\\Documents\\Hackolade\\Documentation\\travel-sample.html --logo="C\\Users\\Public\\Documents\\Hackolade\\Documentation\\couchbase logo.png" \
\--attribTree=complex --JSONSchema=false --JSONData=false --properties=notNull --entities="travel-sample: airport, airline, route"

&nbsp;

**Note:** If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: *"C:\\Program Files\\Hackolade\\hackolade"* .&nbsp; The workaround, assuming:

![Image](<lib/Windows%20Program%20Files.png>)

is to to use the 8.3 command *C:\\PROGRA~1\\Hackolade\\hackolade*, as displayed above.

&nbsp;

## revEng

The *revEng* command allows to trigger a reverse-engineering process of a database instance, as described in [this page](<Reverseengineeranexistinginstanc.md>), or script file.

&nbsp;

Usage:&nbsp; &nbsp; *hackolade revEng \[--arguments\]*

&nbsp;

| **Argument** | **Required** | **Purpose** |
| --- | --- | --- |
| \--target=\<*target*\> | Y | Native target for model: JSON, MONGODB, DYNAMODB, COUCHBASE, or plugin target: Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop, etc.. |
| \--connectName=\<connection\> | Y if from instance | Name of connection settings saved in the Hackolade instance where CLI is invoked. Or use --connectFile instead. |
| \--connectFile=\<*file*\>\* | N | Full file path of connection config file (you don't need to use it when connect name is specified).&nbsp; The simplest way to create a connection file is to create a connection in the GUI application, then export the connection settings to file, encrypted or not. |
| \--files="\<file1\>;\<file2\>..." | Y if from file | List of full file path of target scripts (MongoDB validator, Cassandra CQL, Hive HQL, Avro schema, Neo4j Cypher, Swagger documentation, etc...)&nbsp; from which reverse-engineering process has to be performed. Accepts paths divided by semicolon (schema1.avcs;schema2.avcs) when reverse-engineering from Avro/Parquet with combining schemas into one.&nbsp; |
| \--model=\<*file*\>\* | Y | Full path and file name for target Hackolade model into which reverse-engineering process has to be converted.&nbsp; Extension .json is optional |
| \--samplingMethod=\< **abs** \| re l\> | N | Specify sampling method, either absolute number of documents or relative percentage.&nbsp; \[default: abs\] |
| \--samplingValue=\<*x*\> | N | If samplingMethod=abs: positive integer between 1 and 100000 \[default: 1000\] If samplingMethod=rel: positive integer between 1 and 100 \[default: 1\] **Warning:** for obvious performance and response time reasons, be reasonable with these parameters when used on large entities\!&nbsp; What's the point of sampling 10% of 1B+ identical documents?... |
| \--fieldOrder=\< **keep** \| alpha \> | N | Specify whether to preserve order of fields in sampled document or rearrange in alpha order&nbsp; \[default: keep\] |
| \--inferRelationships=\< true \| **false** \> | N | For MongoDB only, optionally specify whether to attempt relationship inference based on ObjectID data type. &nbsp; |
| \--query="{\<aggregation pipeline expression\>}" | N | For MongoDB only, specify query criteria for sampling.&nbsp; \[string\] \[default: "{}"\] |
| \--sort="{\<aggregation pipeline expression\>}" | N | For MongoDB only, specify sort criteria for sampling.&nbsp; \[default: "{}"\] |
| \--update=\< true \| **false** \> | N | Specify whether to update existing model.  If false, existing model will be overwritten \[default: false\] |
| \--conflictResolution\< **keepBoth** \| replace \| merge \| cancel \> | N | Specify conflict resolution strategy for containers and entities \[default: keepBoth\]&nbsp; \[values: "keepBoth", "replace", "merge", "cancel"\] \[default: "keepBoth"\] |
| \--selectedObjects= "\<containerName\>: \[\<*entity1\>*,\<*entity2\>*,…\]" | N | Specify container(s) to include in documentation \[default: all\] and an array of entities \[default: all\] - MongoDB: container = dbs; entity = collection - DynamoDB: container = *not applicable*; entity = table - Couchbase: container = bucket; entity = document kind - Cosmos DB: container = collection; entity = document type - Elasticsearch: container = index: entity = type - HBase: container =&nbsp; namespace; entity = table The value is a string surrounded by double quotes (").&nbsp; Entities are represented as an array surrounded by square brackets (\[\]), and are separated by a comma (,).&nbsp; The entities array is separated from the container name by a colon (:).&nbsp; Containers are separated by semi-colons (;). |
| \--documentKinds= "\<bucketName\>: \<docKindField\>" | N | In Couchbase only, for each bucket, you must specify the field used to distinguish the different objects stored in the same bucket. |
| \--entityVersion=\<version number\> | N | In EventBridge only, specify schema version \[default: latest\] |
| \--includeEmpty=\< true \| **false** \> | N | In MongoDB only, specify whether to include empty collections \[default: false\] |
| \--includeSystem=\< true \| **false** \> | N | In MongoDB only, specify whether to include system collections \[default: false\]&nbsp; |
| \--includeViews=\< **true** \| false \> | N | In MongoDB only, specify whether to include views \[default: true\] |
| \--selectedDB=\<database name\> | N | In Cosmos DB, you must specify the name of the database which should be reverse-engineered. \[default: the first database in the list\] |
| \--pagination=\< **0** \| 1 \| ...\> | N | In Couchbase, you must specify the number of documents per page for pagination. If value = 0, pagination is disabled&nbsp; \[default: 0\] |
| \--detectPattern=\< true \| **false** \> | N | Specify whether to automatically convert pattern fields \[default: false\] |
| \--combineSchemas=\< true \| **false** \> | N | For Avro and Parquet only.&nbsp; Specify whether to combine the schemas of multiple files, or keep one schema per file reverse-engineered \[default: false\] |
| \--namingConventions=\< business \| technical \> | N | If application parameters are set to enable Naming Conventions, specify whether to reverse-engineer source attributes as business names or as technical names.&nbsp; Conversions will be applied according to your Naming Conventions parameters. &nbsp; \[default: **business**, if Naming Conventions are disabled; or **technical**, if Naming Conventions are enabled in application Tools \> Options\] |
| \--distribution=\< **true** \| false \> | N | Specify whether to perform orthogonal distribution of model entities on ERD. \[default: true\] |
| \--logLevel=\< 1 \| 2 \| 3 \| **4** \> | N | &#49; = no spinner, no info, no error messages 2 = no spinner, no info 3 = no spinner 4 = full output \[default: 4\] |


\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“)&nbsp; Path can be ignored if file is in local directory.

&nbsp;

MongoDB example:&nbsp; &nbsp;

> hackolade revEng --connectName=local --target=MONGODB --samplingMethod=abs --samplingValue=1000 \
\--model=C:\\Users\\Public\\Bitbucket\\hackolade\\schemas\\MongoDB\\yelp.json --includeEmpty=true --selectedObjects="yelp" --fieldOrder=keep&nbsp;

&nbsp;

DynamoDB example:&nbsp; &nbsp;

> "C:\\Program Files\\Hackolade\\hackolade" revEng --connectName=local --target=DYNAMODB --samplingMethod=abs --samplingValue=1000 \
\--model=C:\\Users\\Public\\Bitbucket\\hackolade\\schemas\\DynamoDB\\entertainment.json --includeEmpty=false --selectedObjects="\[Movies, Music\]" --fieldOrder=alpha&nbsp;

&nbsp;

Couchbase example:&nbsp; &nbsp;

> "C:\\Program Files\\Hackolade\\hackolade" revEng --connectName=local --target=COUCHBASE --samplingMethod=abs --samplingValue=2500 \
\--model=C:\\Users\\Public\\Bitbucket\\hackolade\\schemas\\Couchbase\\travel-sample.json --includeEmpty=false --selectedObjects="travel-sample: \[airline, airport\]"&nbsp; \
\--documentKinds="travel-sample: type" --fieldOrder=keep

&nbsp;

Cosmos DB example:

> start /wait hackolade reveng --target=COSMOSDB-DOC --connectName=azure --model=travel.json --selectedObjects="travel" --documentKinds="travel:type"

&nbsp;

**Note:** If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: *"C:\\Program Files\\Hackolade\\hackolade"* .&nbsp; The workaround, assuming:

![Image](<lib/Windows%20Program%20Files.png>)

is to to use the 8.3 command *C:\\PROGRA~1\\Hackolade\\hackolade*, as displayed above.

&nbsp;

## revEngJSON

The *revEngJSON* command allows to trigger a reverse-engineering process of a JSON document or JSON Schema file, as described in [this page](<JSONdocument1.md>).

&nbsp;

Usage:&nbsp; &nbsp; *hackolade revEngJSON \[--arguments\]*

&nbsp;

| **Argument** | **Required** | **Purpose** |
| --- | --- | --- |
| \--target=\<*target*\> | Y | Native target for model: JSON, MONGODB, DYNAMODB, COUCHBASE, or plugin target: ArangoDB, Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop |
| \--files="\<file1\>;\<file2\>..." | Y | Specify the directory path and file names to be reverse-engineered |
| \--model=\<*file*\>\* | Y | Full path and file name for target Hackolade model into which reverse-engineering process has to be converted.&nbsp; Extension .json is optional |
| \--entityHandling=\< **ERD** \| definitions \> | N | Specify whether must be reverse-engineered as entities in ERD or as model definitions \[default: ERD\] |
| \--container=\<containerName\> | N | Specify a container name into which reverse-engineered entities will be inserted \[default=""\] |
| \--normalization=\< **true** \| false \> | N | Only applicable to RDBMS.&nbsp; Specify whether complex data types should be normalized into separate entities \[default: true\] |
| \--conflictResolution=\< **keepBoth** \| replace \| merge \| cancel \> | N | Specify conflict strategy for containers and entities \[default: keepBoth\] |
| \--ndjson=\< true \| **false** \> | N | Specify whether the file is contains NDJSON to leverage sampling options \[default: false\] |
| \--namingConventions=\< business \| technical \> | N | If application parameters are set to enable Naming Conventions, specify whether to reverse-engineer source attributes as business names or as technical names.&nbsp; Conversions will be applied according to your Naming Conventions parameters. &nbsp; \[default: **business**, if Naming Conventions are disabled; or **technical**, if Naming Conventions are enabled in application Tools \> Options\] |
| \--logLevel=\< 1 \| 2 \| 3 \| **4** \> | N | &#49; = no spinner, no info, no error messages 2 = no spinner, no info 3 = no spinner 4 = full output \[default: 4\] |


\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“)&nbsp; Path can be ignored if file is in local directory.

&nbsp;

## revEngYAML

The *revEngYAML* command allows to trigger a reverse-engineering process of a YAML document file, as described in [this page](<JSONdocument1.md>).

&nbsp;

Usage:&nbsp; &nbsp; *hackolade revEngJSON \[--arguments\]*

&nbsp;

| **Argument** | **Required** | **Purpose** |
| --- | --- | --- |
| \--target=\<*target*\> | Y | Native target for model: JSON, MONGODB, DYNAMODB, COUCHBASE, or plugin target: ArangoDB, Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop |
| \--files="\<file1\>;\<file2\>..." | Y | Specify the directory path and file names to be reverse-engineered |
| \--model=\<*file*\>\* | Y | Full path and file name for target Hackolade model into which reverse-engineering process has to be converted.&nbsp; Extension .json is optional |
| \--entityHandling=\< **ERD** \| definitions \> | N | Specify whether must be reverse-engineered as entities in ERD or as model definitions \[default: ERD\] |
| \--container=\<containerName\> | N | Specify a container name into which reverse-engineered entities will be inserted \[default=""\] |
| \--normalization=\< **true** \| false \> | N | Only applicable to RDBMS.&nbsp; Specify whether complex data types should be normalized into separate entities \[default: true\] |
| \--conflictResolution=\< **keepBoth** \| replace \| merge \| cancel \> | N | Specify conflict strategy for containers and entities \[default: keepBoth\] |
| \--ndjson=\< true \| **false** \> | N | Specify whether the file is contains NDJSON to leverage sampling options \[default: false\] |
| \--namingConventions=\< business \| technical \> | N | If application parameters are set to enable Naming Conventions, specify whether to reverse-engineer source attributes as business names or as technical names.&nbsp; Conversions will be applied according to your Naming Conventions parameters. &nbsp; \[default: **business**, if Naming Conventions are disabled; or **technical**, if Naming Conventions are enabled in application Tools \> Options\] |
| \--logLevel=\< 1 \| 2 \| 3 \| **4** \> | N | &#49; = no spinner, no info, no error messages 2 = no spinner, no info 3 = no spinner 4 = full output \[default: 4\] |


\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“)&nbsp; Path can be ignored if file is in local directory.

&nbsp;

## revEngDDL

The *revEngDDL* command allows to trigger a reverse-engineering process of a Data Definition Language file from a database instance, as described in [this page](<SQLDDL.md>).

&nbsp;

Usage:&nbsp; &nbsp; *hackolade revEngDDL \[--arguments\]*

&nbsp;

| **Argument** | **Required** | **Purpose** |
| --- | --- | --- |
| \--target=\<*target*\> | Y | Native target for model: MONGODB, DYNAMODB, COUCHBASE, or plugin target: ArangoDB, Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop |
| \--file=\<*file*\>\* | Y | Specify the directory path and file name where the schema file to be reverse-engineered is located (file type must be compatible with selected target.)&nbsp; |
| \--model=\<*file*\>\* | Y | Full path and file name for target Hackolade model into which reverse-engineering process has to be converted.&nbsp; Extension .json is optional |
| \--entityHandling=\< **ERD** \| definitions \> | N | Specify whether must be reverse-engineered as entities in ERD or as model definitions \[default: ERD\] |
| \--container=\<containerName\> | N | Specify a container name into which reverse-engineered entities will be inserted \[default=""\] |
| \--database=\< oracle \| mysql \| mssqlserver \| db2 \| postgres \| informix \| snowflake \| teradata \> | Y | Name of database of DDL script&nbsp; |
| \--update=\< true \| **false** \> | N | Specify whether to update existing model.  If false, existing model will be overwritten \[default: false\] |
| \--conflictResolution=\< **keepBoth** \| replace \| merge \| cancel \> | N | Specify conflict strategy for containers and entities \[default: keepBoth\] |
| \--namingConventions=\< business \| technical \> | N | If application parameters are set to enable Naming Conventions, specify whether to reverse-engineer source attributes as business names or as technical names.&nbsp; Conversions will be applied according to your Naming Conventions parameters. &nbsp; \[default: **business**, if Naming Conventions are disabled; or **technical**, if Naming Conventions are enabled in application Tools \> Options\] |
| \--logLevel=\< 1 \| 2 \| 3 \| **4** \> | N | &#49; = no spinner, no info, no error messages 2 = no spinner, no info 3 = no spinner 4 = full output \[default: 4\] |


\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“)&nbsp; Path can be ignored if file is in local directory.

&nbsp;

## revEngXSD

The *revEngXSD* command allows to trigger a reverse-engineering process of an XMS schema (XSD).

&nbsp;

Usage:&nbsp; &nbsp; *hackolade revEngXSD \[--arguments\]*

&nbsp;

| **Argument** | **Required** | **Purpose** |
| --- | --- | --- |
| \--target=\<*target*\> | Y | Native target for model: MONGODB, DYNAMODB, COUCHBASE, or plugin target: ArangoDB, Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop |
| \--file=\<*file*\>\* | Y | Specify the directory path and file name where the schema file to be reverse-engineered is located (file type must be compatible with selected target.)&nbsp; |
| \--model=\<*file*\>\* | Y | Full path and file name for target Hackolade model into which reverse-engineering process has to be converted.&nbsp; Extension .json is optional |
| \--entityHandling=\< **ERD** \| definitions \> | N | Specify whether must be reverse-engineered as entities in ERD or as model definitions \[default: ERD\] |
| \--container=\<containerName\> | N | Specify a container name into which reverse-engineered entities will be inserted \[default=""\] |
| \--conflictResolution=\< **keepBoth** \| replace \| merge \| cancel \> | N | Specify conflict strategy for containers and entities \[default: keepBoth\] |
| \--namingConventions=\< business \| technical \> | N | If application parameters are set to enable Naming Conventions, specify whether to reverse-engineer source attributes as business names or as technical names.&nbsp; Conversions will be applied according to your Naming Conventions parameters. &nbsp; \[default: **business**, if Naming Conventions are disabled; or **technical**, if Naming Conventions are enabled in application Tools \> Options\] |
| \--logLevel=\< 1 \| 2 \| 3 \| **4** \> | N | &#49; = no spinner, no info, no error messages 2 = no spinner, no info 3 = no spinner 4 = full output \[default: 4\] |


\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“)&nbsp; Path can be ignored if file is in local directory.

&nbsp;

## compMod

The *compMod* command lets you compare two (2) Hackolade models and derive a delta model file with additions, deletions, and modifications of fields and structures.

&nbsp;

When merging into a targetModel, you should keep in mind that:

\- merging is an "all or nothing" proposition

\- handling of modifications is impacted by the order in which model1 and model 2 are assigned, with model2 values being kept in the merged model

&nbsp;

Usage:&nbsp; &nbsp; *hackolade compMod \[--arguments\]*

&nbsp;

| **Argument** | **Required** | **Purpose** |
| --- | --- | --- |
| \--model1=\<*file*\>\* | Y | Full path and file name for baseline Hackolade model with which comparison will be performed.&nbsp; Extension .json is optional |
| \--model2=\<file\>\* | Y | Full path and file name for comparison Hackolade model.&nbsp; Extension .json is optional.&nbsp; Both models need to be of the same DB target.&nbsp; Extension .json is optional |
| \--deltaModel=\<file\>\* | Y | Full path and file name for differences in model comparisons.&nbsp; The resulting file is a Hackolade model.&nbsp; Extension .json is optional |
| \--ignoreGUIDs=\<**true** \| false\> | N | Specify whether to include GUIDs in comparison.&nbsp; \[default: true\] |
| \--ignoreExtraProperties= \<**true** \| false\> | N | Specify whether to include in comparison the Hackolade properties that cannot typically be derived from the data, such as descriptions, comments, samples, defaults, and foreign key-related infos.&nbsp; \[default: true\] |
| \--ignoreOrder=\<**true** \| false\> | N | Specify whether to detect changes in order of fields \[default: true\] |
| \--targetModel=\<file\>\* | N | Full path and file name for the Hackolade model resulting from the merge of model1 and model2.&nbsp; If specified, a new Hackolade model is created with a merge of the 2 original models.&nbsp; Extension .json is optional |
| \--mergedeletesasdeactivated= \<true \| **false**\> | N | Specify whether to deactivate deleted objects \[default: false\] |
| \--gui=\<true \| **false**\> | N | Specify whether to open Model Compare \& Merge in GUI&nbsp; \[default: false\] |
| \--logLevel=\< 1 \| 2 \| 3 \| **4** \> | N | &#49; = no spinner, no info, no error messages 2 = no spinner, no info 3 = no spinner 4 = full output \[default: 4\] |


\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“)&nbsp; Path can be ignored if file is in local directory.

&nbsp;

Note: unless GUID’s are used for the comparison, a change in a field name will result in an addition plus a deletion.&nbsp; Same for a change in an entity name.

&nbsp;

Example:

*C:\\PROGRA~1\\Hackolade\\hackolade compMod --model1=yesterdaysModel --model2=todaysModel --deltaModel=todaysDeltaModel --ignoreGUIDs=true *\
*\--ignoreExtraProperties=true --ignoreOrder=true *

&nbsp;

**Note:** If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: *"C:\\Program Files\\Hackolade\\hackolade"* .&nbsp; The workaround, assuming:

![Image](<lib/Windows%20Program%20Files.png>)

is to to use the 8.3 command *C:\\PROGRA~1\\Hackolade\\hackolade*, as displayed above.

&nbsp;

Structure of resulting delta model file:

![Image](<lib/CLI%20compMod%20delta%20model%20structure.png>)

A delta model file may contain any combination of multiple additions, deletions, and modifications.&nbsp; Deeply nested fields are referenced through their structure.&nbsp; To merge newly added fields, open your baseline model in Hackolade, then either copy/paste from the delta model, or reference the new field via an external reference to the delta model, then convert the reference into attributes.

&nbsp;

## forwEng

Forward engineer structure created with the application to dynamically generate the schema of the selected entities.

&nbsp;

Usage:&nbsp; &nbsp; *hackolade forwEng \[--arguments\]*

&nbsp;

| **Argument** | **Required** | **Purpose** |
| --- | --- | --- |
| \--model=\<*file*\>\* | Y | Full path and file name for target Hackolade model. Extension .json is optional&nbsp; |
| \--path=\<*file*\>\* | Y | Specify the directory path where the forward-engineered files will be created. |
| \--outputType=\< **jsonschema** \| jsondata yamldata \| script \| schemaregistry \> | Y | Specify the type of output (JSON Schema, sample JSON data, sample YAML data, script, or schemaregistry) \[default: jsonschema\] This allows output of the script corresponding to the target of the specified model, e.g.: CQL for Cassandra, HQL for Hive, etc... It also allows the publication of Avro and JSON schemas to schema registry instances |
| –jsonSchemaCompliance=\< **standard** \| full \| extended \> | N | Specify JSON Schema compliance: standard for only JSON Schema keywords and data types, full for additional custom properties, or extended for target-specific data types and internal properties.  \[default: standard\] |
| \--jsonschemaversion=\< **draft-04** \| draft 06 \| draft-07 \| 2019-09 \| 2020-12 \> | N | Specify JSON Schema specification version \[default: draft-04\] &nbsp; \[values: draft-04, draft-06, draft-07, 2019-09, 2020-12\] \[default: "draft-04"\] |
| \--format=\< *format* \> | N | Output target-specific schema format: MongoDB: \["shell", "mongoose","js", $jsonchema"\] Couchbase: \["ottoman", "n1ql"\] Avro: \["avroSchema", "schemaRegistry"\] Glue: \["awsCLI", "HiveQL"\] OpenAPI: &nbsp; \["json", "yaml"\] Swagger: &nbsp; \["json", "yaml"\] |
| \--connectName=\<connection\> | Y if to instance | Name of connection settings saved in the Hackolade instance where CLI is invoked. Or use --connectFile instead. |
| \--connectFile=\<*file*\>\* | N | Full file path of connection config file (you don't need to use it when connect name is specified).&nbsp; The simplest way to create a connection file is to create a connection in the GUI application, then export the connection settings to file, encrypted or not. |
| \--selectedObjects= "\<containerName\>: \[\<*entity1\>*,\<*entity2\>*,…\]" | N | Specify array of entities to include to result from model \[default: all\] |
| \--scriptType=\<**create** \| update \> | N | For Cassandra, if outputType=script, specify type of forward engineering script \[default:create\] |
| (deprecated) --resolvDefs=\<**true** \| false\> | N | If outputType=jsonschema, specify whether to output resolved definitions (true) or referenced definitions (false) \[default=true\] |
| \--defsStrategy== \<**resolved** \| referenced \| internal\> | N | If outputType=jsonschema, specify whether to output resolved, referenced or internal definitions&nbsp; \[values: "resolved", "referenced", "internal"\] \[default: "resolved"\] |
| \--updateExtDefs=\<true \| **false**\> | N | When reference to external definition, update current model to ensure latest changes are included. \[default: false\] |
| \--insertSampleData=\<true \| **false**\> | N | Include sample data to the output if it supports. \[default: false\] |
| \--minify=\<true \| **false**\> | N | For JSON document/schema and Avro Schema, minify output instead of default beautifying format \[default=false\] |
| \--batchScriptSeparator=\< ; \| GO \> | N | For SQL Server, Azure SQL, and Synapse, specify if you wish a different separator than the default semi-column ";" or the "GO" separator \[choices: ";", "GO"\] \[default: ";"\] |
| \--validateSchema=\<true \| **false**\> | N | If output script supports validation (JSON Schema, Avro Schema, Swagger, OpenAPI,...), run respective validator, and generate error message if validation failed. \[default: false\] |
| \--ignoredoc=\<true \| **false**\> | N | Ignore description and comment properties which may be too wordy for this purpose \[default: false\] |
| \--definitions=\<true \| **false**\> | N | JSON Schema only, specify whether to generate json schema of model definitions \[default: false\] |
| \--level=\<entity \| container \| model\> | N | Specify the forward-engineering level \[values: "entity", "container", "model"\] |
| \--skipUndefinedLevel=\<true \| **false**\> | N | For JSON document/schema, skip extraneous folder level when container is undefined \[default: false\] |
| \--structuredpath=\<**true** \| false\> | N | Use a structured path for naming a model folder \[default: true\] |
| \--logLevel=\< 1 \| 2 \| 3 \| **4** \> | N | &#49; = no spinner, no info, no error messages 2 = no spinner, no info 3 = no spinner 4 = full output \[default: 4\] |


\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“)&nbsp; Path can be ignored if file is in local directory.

&nbsp;

Example:

> C:\\PROGRA~1\\Hackolade\\hackolade forwEng --model=masterdata.json --path=masterdata.cql &nbsp;

&nbsp;

**Note:** If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: *"C:\\Program Files\\Hackolade\\hackolade"* .&nbsp; The workaround, assuming:

![Image](<lib/Windows%20Program%20Files.png>)

is to to use the 8.3 command *C:\\PROGRA~1\\Hackolade\\hackolade*, as displayed above.

&nbsp;

&nbsp;

## forwEngAPI

The forwEngAPI command lets you generate a Swagger or OpenAPI model from the merging of a source data model and a user-defined template

&nbsp;

Usage:&nbsp; &nbsp; *hackolade forwEngAPI \[--arguments\]*

&nbsp;

| **Argument** | **Required** | **Purpose** |
| --- | --- | --- |
| \--sourcemodel=\<file\>\* | Y | Full path and file name for the Hackolade model to to serve as a basis for the API generation.  Extension .json is optional |
| \--selectedObjects= "\<containerName\>: \[\<*entity1\>*,\<*entity2\>*,…\]" | N | Specify array of entities to include to result from model \[default: all\] |
| \--APItemplate=\<file\>\* | Y | Full path and file name for the template to be used during API generation to create the specified resources for each selected entity of the source model.  The template can be a Hackolade model, or a Swagger or OpenAPI documentation file in either JSON or YAML. |
| \--targetModelFormat=\< Swagger \| **OpenAPI** \> | N | Specify the target of the target model.&nbsp; \["Swagger" or "OpenAPI"\] \[default: OpenAPI\] |
| \--targetmodel=\<file\>\* | Y | Full path and file name for the obfuscated Hackolade model.  Extension .json is optional. &nbsp; |
| \--APIdocFile=\<file\>\* | N | If specified, the corresponding documentation file will be generated in the chose model format.&nbsp; Specify the full path and file name for the generated documentation file. |
| \--logLevel=\< 1 \| 2 \| 3 \| **4** \> | N | &#49; = no spinner, no info, no error messages 2 = no spinner, no info 3 = no spinner 4 = full output \[default: 4\] |


\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“)&nbsp; Path can be ignored if file is in local directory.

&nbsp;

Example:

> C:\\PROGRA~1\\Hackolade\\hackolade forwEngAPI --sourcemodel=masterdata --APItemplate=OAS\_generation --targetmodel=masterdataAPI&nbsp; --APIdocFile=masterdata\_OpenAPI&nbsp;

&nbsp;

**Note:** If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: *"C:\\Program Files\\Hackolade\\hackolade"* .&nbsp; The workaround, assuming:

![Image](<lib/Windows%20Program%20Files.png>)

is to to use the 8.3 command *C:\\PROGRA~1\\Hackolade\\hackolade*, as displayed above.

&nbsp;

## forwEngDataDictionary

The forwEngDataDictionary command lets you publish Hackolade data models to a Data Dictionary instance (currently Collibra only.)

&nbsp;

Usage:&nbsp; &nbsp; *hackolade forwEngDataDictionary \[--arguments\]*

&nbsp;

| **Argument** | **Required** | **Purpose** |
| --- | --- | --- |
| \--model=\<file\>\* | Y | Full path and file name for the&nbsp; Hackolade model to be published to the Data Dictionary instance. Extension .json is optional. |
| \--connectName=\<connection\> | Y if to instance | Name of connection settings saved in the Hackolade instance where CLI is invoked. Or use --connectFile instead. |
| \--connectFile=\<*file*\>\* | N | Full file path of connection config file (you don't need to use it when connect name is specified).&nbsp; The simplest way to create a connection file is to create a connection in the GUI application, then export the connection settings to file, encrypted or not. |
| \--selectedObjects= "\<containerName\>: \[\<*entity1\>*,\<*entity2\>*,…\]" | N | Specify array of entities to include to result from model \[default: all\] |
| \--targetResource=\<resource\> | Y | Name of a target resource (domain) in Data Dictionary instance. |
| \--forceconfig=\<true \| **false**\> | N | Specify whether to create necessary config in Data Dictionary instance |
| \--logLevel=\< 1 \| 2 \| 3 \| **4** \> | N | &#49; = no spinner, no info, no error messages 2 = no spinner, no info 3 = no spinner 4 = full output \[default: 4\] |


\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“)&nbsp; Path can be ignored if file is in local directory.

&nbsp;

Example:

> C:\\PROGRA~1\\Hackolade\\hackolade forwEngDataDictionary --model=yel --connectioName=Collibra\_instance --targetResource=Yelp &nbsp;

&nbsp;

**Note:** If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: *"C:\\Program Files\\Hackolade\\hackolade"* .&nbsp; The workaround, assuming:

![Image](<lib/Windows%20Program%20Files.png>)

is to to use the 8.3 command *C:\\PROGRA~1\\Hackolade\\hackolade*, as displayed above.

&nbsp;

## obfusc&nbsp;

The obfusc command lets you garble sensitive properties: business name, technical name, description, comments, enumeration.  Use if you need to send a model for troubleshooting but don't want to disclose sensitive aspects of the model.

&nbsp;

Usage:&nbsp; &nbsp; *hackolade obfusc \[--arguments\]*

&nbsp;

| **Argument** | **Required** | **Purpose** |
| --- | --- | --- |
| \--sourcemodel=\<file\>\* | Y | Full path and file name for the Hackolade model to be obfuscated.  Extension .json is optional |
| \--targetmodel=\<file\>\* | Y | Full path and file name for the obfuscated Hackolade model.  Extension .json is optional. &nbsp; |
| \--logLevel=\< 1 \| 2 \| 3 \| **4** \> | N | &#49; = no spinner, no info, no error messages 2 = no spinner, no info 3 = no spinner 4 = full output \[default: 4\] |


\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“)&nbsp; Path can be ignored if file is in local directory.

&nbsp;

Example:

*C:\\PROGRA~1\\Hackolade\\hackolade obfusc --sourcemodel=masterdata --targetmodel=garbeledmasterdata&nbsp; *

&nbsp;

**Note:** If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: *"C:\\Program Files\\Hackolade\\hackolade"* .&nbsp; The workaround, assuming:

![Image](<lib/Windows%20Program%20Files.png>)

is to to use the 8.3 command *C:\\PROGRA~1\\Hackolade\\hackolade*, as displayed above.

&nbsp;

## help

The --*help* argument displays the version number of Hackolade being invoked.

&nbsp;

Usage:&nbsp; &nbsp; *start /wait hackolade --help*

&nbsp;

## performance

The *--performance* argument records timestamps of application startup steps for performance troubleshooting.&nbsp; Log can be found in file HackoladePerformance.log in directory C:\\Users\\%username%\\AppData\\Roaming\\HackoladeLogs (Windows) or folder Users/$USER/Documents/HackoladeLogs (Mac/Linux)

&nbsp;

Usage:&nbsp; &nbsp; *start /wait hackolade --performance*

&nbsp;

## version

The --*version* argument displays the version number of Hackolade being invoked.

&nbsp;

Usage:&nbsp; &nbsp; *start /wait hackolade --version*

