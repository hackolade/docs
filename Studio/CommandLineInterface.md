# Command Line Interface

With its Command Line Interface (CLI), Hackolade truly supports an agile development approach leveraging the flexibility of NoSQL dynamic schemas. Some customers use this capability nightly in a batch process to identify attributes and structures that may have appeared in the data since the last run. During a nightly run of the reverse-engineering function, a much larger dataset can be queried as a basis for document sampling, hence making schema inference more precise. Such capability can be useful in a data governance context to properly document the semantics and publish a thorough data dictionary for end users.

&nbsp;

The CLI can also be used in the context of compliance with privacy laws to make sure that the company does not store data that it is not supposed to store. There are many more examples of how to use this functionality.

&nbsp;

Another common use case we've seen is to use the CLI to compare the models reverse-engineered from different environments (e.g; dev, test, integration, prod) to ensure their synchronization.

&nbsp;

The Hackolade command line can of course be used on a stand alone machine. It can also be easily combined with a [git repository](Teamcollaboration.md) for the storage of versioned models and schema artifacts, as well as with [Docker containers](<https://github.com/hackolade/docker/tree/main/Studio> "target=\"_blank\""). Customers have been using this combination either in a push mode, triggered by saving or committing model changes, or in a pull mode, when invoked by a DevOps CI/CD pipeline or a scheduled job.

&nbsp;

> [!NOTE]
> The CLI is available in the Professional and Workgroup editions with a dedicated license, as a single-threaded process you run from the command line of your desktop machine. The CLI is not available if you run the Hackolade Studio from the browser. Also, if you want to run the CLI multi-threaded in a Docker container, it must use a [floating license](Floatinglicensekeybehavior.md) seat.

&nbsp;

You may want to watch a playlist of [short videos](<https://www.youtube.com/playlist?list=PLuoumc7VQje0qPX3zHa8SUaDWQg2EAT40> "target=\"_blank\"") on YouTube.\
![CLI Command Line Interface with git](<lib/CLI with git.png>)

&nbsp;

To understand how to set the different CLI arguments, it is often helpful to first run the equivalent function in the GUI application, then to assemble the CLI command piece by piece.

&nbsp;

It is easier to run the CLI from the directory where the Hackolade executable is installed, from a terminal program:

- Windows:
  - cmd command line: all commands below should be preceded by `start /wait hackolade`
  - PowerShell: all commands below should be preceded by `Start-Process -wait hackolade` and the commands and arguments should be wrapped in quotes such as `Start-Process -wait hackolade "forwEng --help"` for more details, please consult [this page](<https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/start-process?view=powershell-7.2#example-7--specifying-arguments-to-the-process> "target=\"_blank\"").
- Mac: start Terminal and execute: all commands below should be preceded by `/Applications/Hackolade.app/Contents/MacOS/Hackolade`
- Linux: terminal emulator or common shell programs: all commands below should be preceded by `./Hackolade`  or `path-to-where-hackolade-was-unzipped/Hackolade`

&nbsp;

To take full advantage of the capability, you may run the CLI from scheduled batch files.

&nbsp;

> [!NOTE]
> A properly licensed copy of Hackolade is required to run the CLI. The CLI functionality is only available in the following editions of Hackolade Studio: Professional, Workgroup, and 14-Day Free Trial.

&nbsp;

Below is the current list of Hackolade CLI commands. Additional commands may be added at a later date.

&nbsp;

<table style="width:90%">
<colgroup><col style="width:19%"><col style="width:81%"></colgroup>
<thead>
<tr>
<th>Command</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>compMod</code></td>
<td>Compare two Hackolade models to detect differences, and optionally merge them</td>
</tr>
<tr>
<td><code>extRefUpdate</code></td>
<td>Update external references</td>
</tr>
<tr>
<td><code>forwEng</code></td>
<td>Forward-engineer structure created with the application to dynamically generate the schema of the selected entities. Or forward-engineer JSON Schema or a sample JSON data document</td>
</tr>
<tr>
<td><code>forwEngAPI</code></td>
<td>Forward-engineer Swagger or OpenAPI model from merge of a source data model and a user-defined template</td>
</tr>
<tr>
<td><code>forwEngDataDictionary</code></td>
<td>Publish Hackolade data model to Data Dictionary instance</td>
</tr>
<tr>
<td><code>forwEngXLSX</code></td>
<td>Export model to Excel file</td>
</tr>
<tr>
<td><code>genDoc</code></td>
<td>Generate documentation for a Hackolade model, in HTML, Markdown, or PDF format</td>
</tr>
<tr>
<td><code>obfusc</code></td>
<td><p>Copy a model, and garble sensitive properties: business name, technical name, description, comments, enumeration.</p><p>Use if you need to send a model for troubleshooting but don't want to disclose sensitive aspects of the model.</p></td>
</tr>
<tr>
<td><code>open</code></td>
<td>Open Hackolade Studio data model</td>
</tr>
<tr>
<td><code>polyglotConvert</code></td>
<td>Convert a model to a Polyglot model</td>
</tr>
<tr>
<td><code>polyglotDerive</code></td>
<td>Derive a model (polyglot or physical target) from a polyglot data model</td>
</tr>
<tr>
<td><code>polyglotUpdate</code></td>
<td>Update polyglot definition</td>
</tr>
<tr>
<td><code>revEng</code></td>
<td>Reverse-engineer a database instance or script file to fetch or infer the schema of the selected collections/tables</td>
</tr>
<tr>
<td><code>revEngDataDictionary</code></td>
<td>Reverse-engineer a data dictionary instance to infer the schema of entities</td>
</tr>
<tr>
<td><code>revEngDiagram</code></td>
<td>Reverse-engineer model from PowerDesigner, MEGA, Mermaid, or DBML file</td>
</tr>
<tr>
<td><code>revEngJSON</code></td>
<td>Reverse-engineer JSON Schema or documents</td>
</tr>
<tr>
<td><code>revEngYAML</code></td>
<td>Reverse-engineer YAML or YAML Schema files</td>
</tr>
<tr>
<td><code>revEngDDL</code></td>
<td>Reverse-engineer RDBMS data definition language files with .sql extensions</td>
</tr>
<tr>
<td><code>revEngXLSX</code></td>
<td>Import Excel template into a data model</td>
</tr>
<tr>
<td><code>revEngXSD</code></td>
<td>Reverse-engineer XSD files with .xsd extensions</td>
</tr>
<tr>
<td><code>help</code></td>
<td>Display commands and their arguments</td>
</tr>
<tr>
<td><code>performance</code></td>
<td>Records timestamps of application startup steps for performance troubleshooting</td>
</tr>
<tr>
<td><code>version</code></td>
<td>Display application version</td>
</tr>
</tbody>
</table>

&nbsp;

Usage: *hackolade command \[--arguments\]*

&nbsp;

## compMod

The *`compMod`* command lets you compare two (2) Hackolade models and derive a delta model file with additions, deletions, and modifications of fields and structures.

&nbsp;

When merging into a targetModel, you should keep in mind that:

- merging is an "all or nothing" proposition
- handling of modifications is impacted by the order in which model1 and model 2 are assigned, with model2 values being kept in the merged model

&nbsp;

Usage: `hackolade compMod [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:24%"><col style="width:10%"><col style="width:66%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--model1=[commit:][path]&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td><p>Full path and file name for baseline Hackolade model with which comparison will be performed. With the Workgroup Edition, you may precede the full path and file name with a reference to the commit of the model file.</p><p>The commit can be any valid Git reference and must be followed by a colon:</p><ul><li>a short hash, e.g. <em>97dd2ae</em></li><li>a long hash, e.g. <em>97dd2ae065771908ee9ae0fa08ccdb58b5a6b18f</em></li><li>a branch, e.g. <em>develop</em></li><li>a tag, e.g. <em>v1.0.0</em></li><li>a pre-defined reference such as <em>HEAD</em>, <em>HEAD^1</em>, <em>HEAD~1</em>, etc.</li></ul><p>Extension .json is optional</p></td>
</tr>
<tr>
<td>--model2=[commit:][path]&lt;file&gt;*</td>
<td>Y</td>
<td>Full path and file name for comparison Hackolade model. Extension .json is optional. With the Workgroup Edition, you may precede the full path and file name with a reference to the commit of the model file. <br>Both models need to be of the same DB target. Extension .json is optional</td>
</tr>
<tr>
<td>--deltaModel=&lt;file&gt;*</td>
<td>Y</td>
<td>Full path and file name for differences in model comparisons. The resulting file is a Hackolade model. Extension .json is optional</td>
</tr>
<tr>
<td>--ignoreGUIDs=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Specify whether to include GUIDs in comparison. [default: true]</td>
</tr>
<tr>
<td><p>--ignoreExtraProperties=</p><p>&lt;<strong>true</strong> | false&gt;</p></td>
<td>N</td>
<td>Specify whether to include in comparison the Hackolade properties that cannot typically be derived from the data, such as descriptions, comments, samples, defaults, and foreign key-related infos. [default: true]</td>
</tr>
<tr>
<td>--ignoreOrder=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Specify whether to detect changes in order of fields [default: true]</td>
</tr>
<tr>
<td>--targetModel=&lt;file&gt;*</td>
<td>N</td>
<td><p>Full path and file name for the Hackolade model resulting from the merge of model1 and model2. If specified, a new Hackolade model is created with a merge of the 2 original models.</p><p>Extension .json is optional</p></td>
</tr>
<tr>
<td>--mergedeletesasdeactivated=<br>&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Specify whether to deactivate deleted objects [default: false]</td>
</tr>
<tr>
<td>--gui=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Specify whether to open Model Compare &amp; Merge in GUI [default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Note: unless GUID’s are used for the comparison, a change in a field name will result in an addition plus a deletion. Same for a change in an entity name.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade compMod --model1=yesterdaysModel --model2=todaysModel --deltaModel=todaysDeltaModel --ignoreGUIDs=true --ignoreExtraProperties=true --ignoreOrder=true
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: *"C:\\Program Files\\Hackolade\\hackolade"* . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command *C:\\PROGRA~1\\Hackolade\\hackolade*, as displayed above.

&nbsp;

Structure of resulting delta model file:\
![CLI compMod delta model structure](<lib/CLI compMod delta model structure.png>)\
A delta model file may contain any combination of multiple additions, deletions, and modifications. Deeply nested fields are referenced through their structure. To merge newly added fields, open your baseline model in Hackolade, then either copy/paste from the delta model, or reference the new field via an external reference to the delta model, then convert the reference into attributes.

&nbsp;

## extRefUpdate

The `extRefUpdate` command lets you update a referrer model for modifications made to the external referenced models.

&nbsp;

Usage: `hackolade extRefUpdate [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:23%"><col style="width:10%"><col style="width:67%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for referrer model. Extension .json is optional</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade extRefUpdate --model=referrerModel
```

&nbsp;

## forwEng

Forward engineer structure created with the application to dynamically generate the schema of the selected entities.

&nbsp;

Usage: `hackolade forwEng [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:25%"><col style="width:10%"><col style="width:65%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for target Hackolade model. Extension .json is optional</td>
</tr>
<tr>
<td>--path=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Specify the directory path and file name where the forward-engineered files will be created.</td>
</tr>
<tr>
<td>--outputType=&lt; <strong>jsonschema</strong> | jsondata | yamldata | script | schemaregistry | dbt | archimatemodel | openexchange &gt;</td>
<td>Y</td>
<td><p>Specify the type of output (JSON Schema, sample JSON data, sample YAML data, script, or schemaregistry, dbt, Archimate model or Archimate OpenExchange) [default: jsonschema]</p><p>This allows output of the script corresponding to the target of the specified model, e.g.: CQL for Cassandra, HQL for Hive, etc...</p><p>It also allows the publication of Avro, ProtoBuf, and JSON schemas to schema registry instances</p></td>
</tr>
<tr>
<td>--jsonSchemaCompliance=&lt; <strong>standard</strong> | full | extended &gt;</td>
<td>N</td>
<td>Specify JSON Schema compliance: standard for only JSON Schema keywords and data types, full for additional custom properties, or extended for target-specific data types and internal properties. [default: standard]</td>
</tr>
<tr>
<td>--jsonschemaversion=&lt; <strong>draft-04</strong> | draft 06 | draft-07 | 2019-09 | 2020-12 &gt;</td>
<td>N</td>
<td>Specify JSON Schema specification version [default: draft-04] [values: draft-04, draft-06, draft-07, 2019-09, 2020-12] [default: "draft-04"]</td>
</tr>
<tr>
<td>--format=&lt; <em>format</em> &gt;</td>
<td>N</td>
<td><p>Output target-specific schema format:</p><p>MongoDB: ["shell", "mongoose","js", $jsonchema"]</p><p>Couchbase: ["ottoman", "n1ql"]</p><p>DynamoDB: ["tableScript", "putItemScript"]</p><p>Avro: ["avroSchema","schemaRegistry", "azureSchemaRegistry","confluentSchemaRegistry","pulsarSchemaRegistry"]</p><p>BigQuery: ["sql", "json"]</p><p>CosmosDB-with-Gremlin-API: ["gremlin", "cosmosdb"]</p><p>CosmosDB-with-SQL-API: ["containerSettingsJson", "azureCliPowerShell","azureCliZsh","azureCliBash"]</p><p>JSON Schema: ["azureSchemaRegistry","confluentSchemaRegistry","pulsarSchemaRegistry"]</p><p>Glue: ["awsCLI", "HiveQL"]</p><p>OpenAPI: ["json", "yaml"]</p><p>Oracle: ["quotedIdentifier", "nonquotedIdentifier"]</p><p>Protobuf: ["azureSchemaRegistry","confluentSchemaRegistry","pulsarSchemaRegistry"]</p><p>Snowflake: ["snowSight", "classicUI"]</p><p>Swagger: ["json", "yaml"]</p></td>
</tr>
<tr>
<td>--connectName=&lt;connection&gt;</td>
<td>Y if to instance</td>
<td><p>Currently only available for schema registries. Name of connection settings saved in the Hackolade instance where CLI is invoked.</p><p>Or use --connectFile instead.</p></td>
</tr>
<tr>
<td>--connectFile=&lt;<em>file</em>&gt;*</td>
<td>N</td>
<td>Currently only available for schema registries. Full file path of connection config file (you don't need to use it when connect name is specified). The simplest way to create a connection file is to create a connection in the GUI application, then export the connection settings to file, encrypted or not.</td>
</tr>
<tr>
<td><p>--selectedObjects=</p><p>"&lt;containerName&gt;: [&lt;<em>entity1&gt;</em>,&lt;<em>entity2&gt;</em>,…]"</p></td>
<td>N</td>
<td><p>Specify array of entities to include to result from model [default: all]</p><p>For multiple containers, separate them with semi-colon (;)</p></td>
</tr>
<tr>
<td>--scriptType=&lt;<strong>create</strong> | update &gt;</td>
<td>N</td>
<td>For Cassandra, if outputType=script, specify type of forward engineering script [default:create]</td>
</tr>
<tr>
<td><p>--defsStrategy=</p><p>&lt;<strong>resolved</strong> | referenced | internal&gt;</p></td>
<td>N</td>
<td>If outputType=jsonschema, specify whether to output resolved, referenced or internal definitions [values: "resolved", "referenced", "internal"] [default: "resolved"]</td>
</tr>
<tr>
<td>--updateExtDefs=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>When reference to external definition, update current model to ensure latest changes are included. [default: false]</td>
</tr>
<tr>
<td>--insertSampleData=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Include sample data to the output if it supports. [default: false]</td>
</tr>
<tr>
<td>--quotingType=&lt;<strong>unquoted</strong> | simple | double&gt;</td>
<td>N</td>
<td>Specify the type of quotes for YAML [values: "unquoted", "single", "double"] [default: "unquoted"]</td>
</tr>
<tr>
<td>--minify=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>For JSON document/schema and Avro Schema, minify output instead of default beautifying format [default=false]</td>
</tr>
<tr>
<td>--batchScriptSeparator=&lt; ; | GO &gt;</td>
<td>N</td>
<td>For SQL Server, Azure SQL, and Synapse, specify if you wish a different separator than the default semi-column ";" or the "GO" separator [choices: ";", "GO"] [default: ";"]</td>
</tr>
<tr>
<td>--validateSchema=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>If output script supports validation (JSON Schema, Avro Schema, Swagger, OpenAPI,...), run respective validator, and generate error message if validation failed. [default: false]</td>
</tr>
<tr>
<td>--ignoredoc=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Ignore description and comment properties which may be too wordy for this purpose [default: false]</td>
</tr>
<tr>
<td>--definitions=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>JSON Schema only, specify whether to generate json schema of model definitions [default: false]</td>
</tr>
<tr>
<td>--level=&lt;entity | container | model&gt;</td>
<td>N</td>
<td>Specify the forward-engineering level [values: "entity", "container", "model"]</td>
</tr>
<tr>
<td>--skipModelFolder=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Skip extraneous root folder named after the model, allowing for direct export of files into the selected location [default: false]</td>
</tr>
<tr>
<td>--skipUndefinedLevel=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>For JSON document/schema, skip extraneous folder level when container is undefined [default: false]</td>
</tr>
<tr>
<td>--apply-drop-statements=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Determines whether DROP statements are active (true) or commented out (false). The user is required to explicitly activate the generation of DROP statements, signifying the understanding of the possible consequences [default: false]</td>
</tr>
<tr>
<td>--excludeContainerAlterStatements= &lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Determines whether containers ALTER statements are excluded (true) or not (false) [default: false]</td>
</tr>
<tr>
<td>--resolveApiExternalRefs=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Specify whether to resolve external references in API targets [default: false]</td>
</tr>
<tr>
<td>--serialization=&lt;<strong>BSON</strong> | JSON&gt;</td>
<td>N</td>
<td>Specify whether JSON Data must be generated with Plain JSON values or BSON values [values: "BSON", "JSON"] [default: "BSON"]</td>
</tr>
<tr>
<td>--pkAtTop=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Place Primary Key at the top of the attribute list [default: true]</td>
</tr>
<tr>
<td>--generateDataTests=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>When outputType=dbt, specify whether to generate dbt data tests from model constraints (primary keys, foreign keys, not null, unique, enum). [default: false]</td>
</tr>
<tr>
<td>--severity=&lt;warn | error&gt;</td>
<td>N</td>
<td>When outputType=dbt and generateDataTests=true, specify the severity level applied to all generated data tests.</td>
</tr>
<tr>
<td>--storeFailures=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>When outputType=dbt and generateDataTests=true, specify whether dbt should store failing rows in a table for inspection. [default: false]</td>
</tr>
<tr>
<td>--limit=&lt;number&gt;</td>
<td>N</td>
<td>When outputType=dbt and storeFailures=true, limit the number of failing rows stored. Accepts a positive integer.</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade forwEng --model=masterdata.json --path=masterdata.cql
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## forwEngAPI

The `forwEngAPI` command lets you generate a Swagger or OpenAPI model from the merging of a source data model and a user-defined template

&nbsp;

Usage: `hackolade forwEngAPI [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:23%"><col style="width:10%"><col style="width:67%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--sourcemodel=&lt;file&gt;*</td>
<td>Y</td>
<td>Full path and file name for the Hackolade model to to serve as a basis for the API generation. Extension .json is optional</td>
</tr>
<tr>
<td><p>--selectedObjects=</p><p>"&lt;containerName&gt;: [&lt;<em>entity1&gt;</em>,&lt;<em>entity2&gt;</em>,…]"</p></td>
<td>N</td>
<td><p>Specify array of entities to include to result from model [default: all]</p><p>For multiple containers, separate them with semi-colon (;)</p></td>
</tr>
<tr>
<td>--APItemplate=&lt;file&gt;*</td>
<td>N</td>
<td>Full path and file name for the template to be used during API generation to create the specified resources for each selected entity of the source model. The template can be a Hackolade model, or a Swagger or OpenAPI documentation file in either JSON or YAML. When no template is provided, the <br>--apiTargetVersion argument must be specified instead.</td>
</tr>
<tr>
<td>--targetModelFormat=&lt; Swagger | <strong>OpenAPI</strong> &gt;</td>
<td>N</td>
<td>Specify the target of the target model. ["Swagger" or "OpenAPI"] [default: OpenAPI]</td>
</tr>
<tr>
<td>--apiTargetVersion</td>
<td>N</td>
<td>Specify the API schema version to be used during API generation when no API template is provided. This argument cannot be used together with the --APItemplate argument. ["3.0.3" or "3.1.0"][default= "3.0.3"]</td>
</tr>
<tr>
<td>--targetmodel=&lt;file&gt;*</td>
<td>Y</td>
<td>Full path and file name for the obfuscated Hackolade model. Extension .json is optional.</td>
</tr>
<tr>
<td>--APIdocFile=&lt;file&gt;*</td>
<td>N</td>
<td>If specified, the corresponding documentation file will be generated in the chose model format. Specify the full path and file name for the generated documentation file.</td>
</tr>
<tr>
<td>--keepexternal=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Keep external references to this data model [default: true]</td>
</tr>
<tr>
<td>--referencepath=&lt;<strong>absolute</strong> | relative&gt;</td>
<td>N</td>
<td>Specify type of external references path [default: absolute]</td>
</tr>
<tr>
<td>--pkAtTop=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Place Primary Key at the top of the attribute list [default: true]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade forwEngAPI --sourcemodel=masterdata --APItemplate=OAS_generation --targetmodel=masterdataAPI  --APIdocFile=masterdata_OpenAPI
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## forwEngDataDictionary

The `forwEngDataDictionary` command lets you publish Hackolade data models to a Data Dictionary instance (currently Collibra only.)

&nbsp;

Usage: `hackolade forwEngDataDictionary [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:24%"><col style="width:10%"><col style="width:66%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--model=&lt;file&gt;*</td>
<td>Y</td>
<td>Full path and file name for the Hackolade model to be published to the Data Dictionary instance. Extension .json is optional.</td>
</tr>
<tr>
<td>--connectName=&lt;connection&gt;</td>
<td>Y if to instance</td>
<td><p>Name of connection settings saved in the Hackolade instance where CLI is invoked.</p><p>Or use --connectFile instead.</p></td>
</tr>
<tr>
<td>--connectFile=&lt;<em>file</em>&gt;*</td>
<td>N</td>
<td>Full file path of connection config file (you don't need to use it when connect name is specified). The simplest way to create a connection file is to create a connection in the GUI application, then export the connection settings to file, encrypted or not.</td>
</tr>
<tr>
<td><p>--selectedObjects=</p><p>"&lt;containerName&gt;: [&lt;<em>entity1&gt;</em>,&lt;<em>entity2&gt;</em>,…]"</p></td>
<td>N</td>
<td><p>Specify array of entities to include to result from model [default: all]</p><p>For multiple containers, separate them with semi-colon (;)</p></td>
</tr>
<tr>
<td>--targetResource=&lt;resource&gt;</td>
<td>Y</td>
<td>Name of a target resource (domain) in Data Dictionary instance.</td>
</tr>
<tr>
<td>--forceconfig=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Specify whether to create necessary config in Data Dictionary instance</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade forwEngDataDictionary --model=yelp --connectName=Collibra_instance --targetResource=Yelp
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## forwEngXLSX

The `forw`*`EngXLSX`* command allows to export a data model into an Excel file.

&nbsp;

> [!WARNING]
> When exporting into an existing Excel file name, the whole file get overwritten.

&nbsp;

Usage: `hackolade forwEngXLSX [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:34%"><col style="width:10%"><col style="width:56%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for target Hackolade model. Extension .json is optional</td>
</tr>
<tr>
<td>--path=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Specify the directory path and file name where the forward-engineered files will be created</td>
</tr>
<tr>
<td><p>--selectedObjects=</p><p>"&lt;containerName&gt;: [&lt;<em>entity1&gt;</em>,&lt;<em>entity2&gt;</em>,…]"</p></td>
<td>N</td>
<td><p>Specify array of entities to include to result from model [default: all]</p><p>For multiple containers, separate them with semi-colon (;)</p></td>
</tr>
<tr>
<td>--relationships=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Specify whether to export relationships [default: true]</td>
</tr>
<tr>
<td>--fullPathTechnicalNames=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Specify whether, for nested complex structures, to include the full path in dot notation for the technical name [default: true]</td>
</tr>
<tr>
<td>--resolvedDefinitions=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Specify whether to resolve referenced definitions [default: false]</td>
</tr>
<tr>
<td>--updateExtDefs=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>When reference to external definition, update current model to ensure latest changes are included. [default: false]</td>
</tr>
<tr>
<td>--pkAtTop=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Place Primary Key at the top of the attribute list [default: true]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

## genDoc

The *`genDoc`* command lets you invoke the generation of a documentation file, either in HTML or PDF format, for a specified existing Hackolade model.

&nbsp;

Usage: `hackolade genDoc [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:22%"><col style="width:10%"><col style="width:68%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--format=&lt;HTML | Markdown | PDF&gt;</td>
<td>Y</td>
<td>Specify format, currently either HTML, MARKDOWN, or PDF</td>
</tr>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for source Hackolade model for which documentation is being generated. Extension .json is optional</td>
</tr>
<tr>
<td>--doc=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for documentation. Extension .html , .md, or .pdf is optional</td>
</tr>
<tr>
<td>--logo=&lt;<em>file</em>&gt;*</td>
<td>N</td>
<td>Full path and file name for custom logo file. If omitted, Hackolade logo is used</td>
</tr>
<tr>
<td>--displayName=&lt;<strong>business</strong> | technical&gt;</td>
<td>N</td>
<td>Define whether to display business or technical names [values: "business", "technical"] [default: business]</td>
</tr>
<tr>
<td>--diagram=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Include model diagram [default: true]</td>
</tr>
<tr>
<td>--diagramViews=["&lt;<em>ERDV1&gt;"</em>,"&lt;<em>ERDV2&gt;"</em>,…]"</td>
<td>N</td>
<td>Specify an array of diagram views to be included. The value is a string surrounded by double quotes ("). ER Diagram View names are represented as an array surrounded by square brackets ([]), and are separated by a comma (,). [default: all]</td>
</tr>
<tr>
<td>--sepContDiag=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Include separate container diagrams (database, region, buckets, keyspaces...) [default: true]</td>
</tr>
<tr>
<td>--entityDiagrams=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Include entity hierarchical schema diagrams [default: false]</td>
</tr>
<tr>
<td>--attribTree=&lt;all | <strong>complex</strong> | none&gt;</td>
<td>N</td>
<td>Include individual hierarchical schema view for all attributes [all], for complex attributes only [complex], or for no attributes [none]. [default: complex]</td>
</tr>
<tr>
<td>--properties=&lt;all | <strong>notNull</strong> | none&gt;</td>
<td>N</td>
<td>Include all field properties [all], only field properties with information [notnull], or no field properties [none]. [default: notNull]</td>
</tr>
<tr>
<td>--relationships=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Include Relationships [default: true]</td>
</tr>
<tr>
<td>--JSONSchema=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Include JSON Schema code [default: true]</td>
</tr>
<tr>
<td>--JSONData=&lt;<strong>true</strong> | false&gt;</td>
<td>N</td>
<td>Include JSON Data sample [default: true]</td>
</tr>
<tr>
<td>--entities="&lt;containerName&gt;: [&lt;<em>entity1&gt;</em>,&lt;<em>entity2&gt;</em>,…]"</td>
<td>N</td>
<td><p>Specify container(s) to include in documentation [default: all] and an array of entities [default: all]</p><ul><li>MongoDB: container = dbs; entity = collection</li><li>DynamoDB: container = <em>not applicable</em>; entity = table</li><li>Couchbase: container = bucket; entity = document kind</li><li>Cosmos DB: container = collection; entity = document type</li><li>plain JSON: container = group; entity = document</li></ul><p>The value is a string surrounded by double quotes ("). Entities are represented as an array surrounded by square brackets ([]), and are separated by a comma (,). The entities array is separated from the container name by a colon (:). Containers are separated by semi-colons (;).</p></td>
</tr>
<tr>
<td>--views="[&lt;view1&gt;, &lt;view2&gt;, ...]"</td>
<td>N</td>
<td><p>In MongoDB only, specify view(s) to include in documentation [default: all]</p><p>The value is a string surrounded by double quotes ("). Views are represented as an array surrounded by square brackets ([]), and are separated by a comma (,).</p></td>
</tr>
<tr>
<td>--openDoc=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Specify whether to open the generated document or not upon completion of generation. [default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Simple example: using all default options:

&nbsp;

```bat
start /wait hackolade genDoc --format=HTML --model=C:\Users\Public\Bitbucket\hackolade\schemas\MongoDB\noaa.json 
--doc=C:\Users\Public\Documents\Hackolade\Documentation\noaa.html
```

&nbsp;

More complex example:

&nbsp;

```bat
start /wait C:\PROGRA~1\Hackolade\hackolade genDoc --format=HTML --model=C:\Users\Public\Bitbucket\hackolade\schemas\Couchbase\travel-sample.json 
--doc=C\Users\Public\Documents\Hackolade\Documentation\travel-sample.html --logo="C\Users\Public\Documents\Hackolade\Documentation\couchbase logo.png"
--attribTree=complex --JSONSchema=false --JSONData=false --properties=notNull --entities="travel-sample: airport, airline, route"
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## open

It is possible to open Hackolade Studio data model from the command line.

&nbsp;

Usage: `hackolade open [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:23%"><col style="width:10%"><col style="width:67%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--model=&lt;<em>file</em>&gt;</td>
<td>Y</td>
<td>Full path and file name for the Hackolade Studio data model to open. Extension .json is optional</td>
</tr>
<tr>
<td>--updateReferences=&lt;true | <strong>false</strong>&gt;</td>
<td>N</td>
<td>Specify whether to update external and polyglot references if present [default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade open --model="/data models/yelp-mongodb.hck.json"
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## obfusc

The <u>obfusc</u> command lets you garble sensitive properties: business name, technical name, description, comments, enumeration. Use if you need to send a model for troubleshooting but don't want to disclose sensitive aspects of the model.

&nbsp;

Usage: `hackolade obfusc [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:24%"><col style="width:7%"><col style="width:69%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--sourcemodel=&lt;file&gt;*</td>
<td>Y</td>
<td>Full path and file name for the Hackolade model to be obfuscated. Extension .json is optional</td>
</tr>
<tr>
<td>--targetmodel=&lt;file&gt;*</td>
<td>Y</td>
<td>Full path and file name for the obfuscated Hackolade model. Extension .json is optional.</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade obfusc --sourcemodel=masterdata --targetmodel=garbeledmasterdata
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## polyglotConvert

The `polyglotConcert` command lets you convert a model (polyglot or physical target) to a polyglot model.

&nbsp;

Usage: `hackolade polyglotConvert [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:23%"><col style="width:10%"><col style="width:67%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--model=&lt;sourceModelFile&gt;</td>
<td>Y</td>
<td>Full path and file name of the target model to convert to Polyglot. Extension .json is optional</td>
</tr>
<tr>
<td>--polyglotModel=&lt;polyglotModelFile&gt;</td>
<td>Y</td>
<td><p>Full path and file name for converted Polyglot model. Extension .json is optional.</p><p>If Polyglot model doesn't exist yet, it will be created. If it does exist, the argument --mergeWithExistingPolyglot can be used to determine whether to merge or replace it.</p></td>
</tr>
<tr>
<td>--polyglotDependence=&lt; independent | dependentRelative | dependentAbsolute &gt;</td>
<td>Y</td>
<td>Specify whether to keep the model to convert dependent on the Polyglot model or to keep them independent If dependent, the path can be relative (recommended) or absolute.</td>
</tr>
<tr>
<td>--mergeWithExistingPolyglot=&lt; true | <strong>false</strong> &gt;</td>
<td>N</td>
<td>f Polyglot model already exists, specify whether to merge the converted Polyglot into the existing one. If false, the existing Polyglot model will be replaced. [Default: false]</td>
</tr>
<tr>
<td>--APIModelDefsHandling=&lt; <strong>resolve</strong> | saveAsDefinitions &gt;</td>
<td>N</td>
<td>Specify how to handle definitions when the model to convert is an API model. Definitions can either be resolved or saved as definitions in the converted Polyglot model. [Default: resolve]</td>
</tr>
<tr>
<td>--convertViews=&lt; true | <strong>false</strong> &gt;</td>
<td>N</td>
<td>Specify whether to convert the views to Polyglot views. [Default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade polyglotConvert --model=yelp-mongodb.hck.json --polyglotmodel=yelp-polyglot.hck.json --polyglotDependence=dependentRelative --mergeWithExistingPolyglot=true --convertViews=true
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## polyglotDerive

The `polyglotDerive` command lets you derive a model (polyglot or physical target) from a polyglot model.

&nbsp;

Usage: `hackolade polyglotDerive [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:23%"><col style="width:10%"><col style="width:67%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--target=&lt;<em>target</em>&gt;</td>
<td>Y</td>
<td>Native target for model: JSON, MONGODB, DYNAMODB, COUCHBASE, or plugin target: Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop, etc..</td>
</tr>
<tr>
<td>--targetVersion=&lt;version&gt;</td>
<td>N</td>
<td>Specify the version number where applicable and necessary.(currently Oracle) [default: latest]</td>
</tr>
<tr>
<td>--polyglotmodels="&lt;file1&gt;;&lt;file2&gt;..."</td>
<td>Y</td>
<td><p>Full path and file name for polyglot model. Extension .json is optional.</p><p>Accepts paths divided by semicolon when deriving from multiple Polyglot models..</p></td>
</tr>
<tr>
<td>--targetmodel=&lt;file&gt;*</td>
<td>Y</td>
<td>Specify the directory path and file name where the derived target model will be created</td>
</tr>
<tr>
<td>--pathType=&lt; <strong>absolute</strong> | relative &gt;</td>
<td>N</td>
<td>Specify the type of path, absolute or relative [default: absolute]</td>
</tr>
<tr>
<td>--normalize=&lt; true | <strong>false</strong> &gt;</td>
<td>N</td>
<td>Where applicable, specify whether or not to normalize complex data types in separate entities [default: false]</td>
</tr>
<tr>
<td>--generateAssociativeEntities=&lt; true | <strong>false</strong> &gt;</td>
<td>N</td>
<td>Generate associative entities for many-to-many relationships [default: false]</td>
</tr>
<tr>
<td>--APItemplate=&lt;file&gt;*</td>
<td>N</td>
<td>When deriving to Swagger/OpenAPI target to generate model-driven API, specify full path and file name for the template to be used during deriving from Polyglot. The template can be a Hackolade model, or a Swagger or OpenAPI documentation file in either JSON or YAML.</td>
</tr>
<tr>
<td>--selectedObjects=<br>"&lt;containerName&gt;: [&lt;<em>entity1&gt;</em>,&lt;<em>entity2&gt;</em>,…]"</td>
<td>N</td>
<td><p>Specify container(s) to reverse-engineer [default: all] and an array of entities [default: all]</p><ul><li>MongoDB: container = dbs; entity = collection</li><li>DynamoDB: container = <em>not applicable</em>; entity = table</li><li>Couchbase: container = bucket; entity = document kind</li><li>Cosmos DB: container = collection; entity = document type</li><li>Elasticsearch: container = index: entity = type</li><li>HBase: container = namespace; entity = table</li></ul><p>The value is a string surrounded by double quotes ("). Entities are represented as an array surrounded by square brackets ([]), and are separated by a comma (,). The entities array is separated from the container name by a colon (:). Containers are separated by semi-colons (;).</p></td>
</tr>
<tr>
<td>--selectedViews=<br>"&lt;containerName&gt;: [&lt;<em>entity1&gt;</em>,&lt;<em>entity2&gt;</em>,…]"</td>
<td>N</td>
<td>Specify container(s) to derive [default: none] and an array of views. The value is a string surrounded by double quotes ("). Views are represented as an array surrounded by square brackets ([]), and are separated by a comma (,). The views array is separated from the container name by a colon (:). Containers are separated by semi-colons (;)</td>
</tr>
<tr>
<td>--applytargetnamingconventions=&lt; true | <strong>false</strong> &gt;</td>
<td>N</td>
<td>Specify whether to apply the target model's naming conventions when deriving names. If set to true, names will be generated using the target's naming rules. If set to false, names defined in the Polyglot model will be preserved. [default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade polyglotDerive --target=mongodb --polyglotmodels=yelp-polyglot.hck.json --targetmodel=yelp-mongodb.hck.json
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## polyglotUpdate

The `polyglotUpdate` command lets you update a target model for modifications made to the referenced polyglot models

&nbsp;

Usage: `hackolade polyglotUpdate [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:23%"><col style="width:10%"><col style="width:67%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--model=&lt;file&gt;*</td>
<td>Y</td>
<td>Full path and file name for target model. Extension .json is optional</td>
</tr>
<tr>
<td>--references= "&lt;<em>name1&gt;</em>,&lt;<em>name2&gt;</em>,…"</td>
<td>N</td>
<td><p>Specify the name of the referenced polyglot models for which the target model must be updated.</p><p>The value is a string surrounded by double quotes ("). The names are separated by a comma (,).</p><p><img src="lib/CLI - Polyglot reference name.png" alt="CLI - Polyglot reference name"></p><p>[default: all]</p></td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade polyglotUpdate --model=yelp-mongodb.hck.json
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## revEng

The *`revEng`* command allows to trigger a reverse-engineering process of a database instance, as described in [this page](Reverseengineeranexistinginstanc.md), or script file.

&nbsp;

Usage: `hackolade revEng [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:23%"><col style="width:10%"><col style="width:67%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--target=&lt;<em>target</em>&gt;</td>
<td>Y</td>
<td>Native target for model: JSON, MONGODB, DYNAMODB, COUCHBASE, or plugin target: Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop, etc..</td>
</tr>
<tr>
<td>--connectName=&lt;connection&gt;</td>
<td>Y if from instance</td>
<td><p>Name of connection settings saved in the Hackolade instance where CLI is invoked.</p><p>Or use --connectFile instead.</p></td>
</tr>
<tr>
<td>--connectFile=&lt;<em>file</em>&gt;*</td>
<td>N</td>
<td>Full file path of connection config file (you don't need to use it when connect name is specified). The simplest way to create a connection file is to create a connection in the GUI application, then export the connection settings to file, encrypted or not.</td>
</tr>
<tr>
<td>--files="&lt;file1&gt;;&lt;file2&gt;..."</td>
<td>Y if from file</td>
<td>List of full file path of target scripts (MongoDB validator, Cassandra CQL, Hive HQL, Avro schema, Neo4j Cypher, Swagger documentation, etc...) from which reverse-engineering process has to be performed. Accepts paths divided by semicolon (schema1.avcs;schema2.avcs) when reverse-engineering from Avro/Parquet with combining schemas into one.</td>
</tr>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for target Hackolade model into which reverse-engineering process has to be converted. Extension .json is optional</td>
</tr>
<tr>
<td>--samplingMethod=&lt; <strong>abs</strong> | re l&gt;</td>
<td>N</td>
<td>Specify sampling method, either absolute number of documents or relative percentage. [default: abs]</td>
</tr>
<tr>
<td>--samplingValue=&lt;<em>x</em>&gt;</td>
<td>N</td>
<td><p>If samplingMethod=abs: positive integer between 1 and 100000 [default: 1000]</p><p>If samplingMethod=rel: positive integer between 1 and 100 [default: 1]</p><blockquote><p>[!WARNING]</p><p>For obvious performance and response time reasons, be reasonable with these parameters when used on large entities! What's the point of sampling 10% of 1B+ identical documents?...</p></blockquote></td>
</tr>
<tr>
<td>--fieldOrder=&lt; <strong>keep</strong> | alpha &gt;</td>
<td>N</td>
<td>Specify whether to preserve order of fields in sampled document or rearrange in alpha order <br>[default: keep]</td>
</tr>
<tr>
<td>--inferRelationships=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>For MongoDB only, optionally specify whether to attempt relationship inference based on ObjectID data type.</td>
</tr>
<tr>
<td>--query="{&lt;aggregation pipeline expression&gt;}"</td>
<td>N</td>
<td>For MongoDB only, specify query criteria for sampling. [string] [default: "{}"]</td>
</tr>
<tr>
<td>--sort="{&lt;aggregation pipeline expression&gt;}"</td>
<td>N</td>
<td>For MongoDB only, specify sort criteria for sampling. [default: "{}"]</td>
</tr>
<tr>
<td>--useIndexInSort=&lt; true | <strong>false</strong> &gt;</td>
<td>N</td>
<td>For MongoDB only, specify whether to use index columns in sort criteria [default= false]</td>
</tr>
<tr>
<td>--update=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>Specify whether to update existing model. If false, existing model will be overwritten [default: false]</td>
</tr>
<tr>
<td>--conflictResolution&lt; <strong>keepBoth</strong> | replace | merge | cancel &gt;</td>
<td>N</td>
<td>Specify conflict resolution strategy for containers and entities [default: keepBoth] [values: "keepBoth", "replace", "merge", "cancel"] [default: "keepBoth"]</td>
</tr>
<tr>
<td>--selectedObjects=<br>"&lt;containerName&gt;: [&lt;<em>entity1&gt;</em>,&lt;<em>entity2&gt;</em>,…]"</td>
<td>N</td>
<td><p>Specify container(s) to reverse-engineer [default: all] and an array of entities [default: all]</p><ul><li>MongoDB: container = dbs; entity = collection</li><li>DynamoDB: container = <em>not applicable</em>; entity = table</li><li>Couchbase: container = bucket; entity = document kind</li><li>Cosmos DB: container = collection; entity = document type</li><li>Elasticsearch: container = index: entity = type</li><li>HBase: container = namespace; entity = table</li></ul><p>The value is a string surrounded by double quotes ("). Entities are represented as an array surrounded by square brackets ([]), and are separated by a comma (,). The entities array is separated from the container name by a colon (:). Containers are separated by semi-colons (;).</p></td>
</tr>
<tr>
<td>--documentKinds=<br>"&lt;bucketName&gt;: &lt;docKindField&gt;"</td>
<td>N</td>
<td>In Couchbase only, for each bucket, you must specify the field used to distinguish the different objects stored in the same bucket.</td>
</tr>
<tr>
<td>--entityVersion=&lt;version number&gt;</td>
<td>N</td>
<td>In EventBridge only, specify schema version [default: latest]</td>
</tr>
<tr>
<td>--includeEmpty=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>In MongoDB only, specify whether to include empty collections [default: false]</td>
</tr>
<tr>
<td>--includeSystem=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>In MongoDB only, specify whether to include system collections [default: false]</td>
</tr>
<tr>
<td>--includeViews=&lt; <strong>true</strong> | false &gt;</td>
<td>N</td>
<td>In MongoDB only, specify whether to include views [default: true]</td>
</tr>
<tr>
<td>--selectedDB=&lt;database name&gt;</td>
<td>N</td>
<td>In Cosmos DB, you must specify the name of the database which should be reverse-engineered. [default: the first database in the list]</td>
</tr>
<tr>
<td>--pagination=&lt; <strong>0</strong> | 1 | ...&gt;</td>
<td>N</td>
<td>In Couchbase, you must specify the number of documents per page for pagination. If value = 0, pagination is disabled [default: 0]</td>
</tr>
<tr>
<td>--detectPattern=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>Specify whether to automatically convert pattern fields [default: false]</td>
</tr>
<tr>
<td>--combineSchemas=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>For Avro and Parquet only. Specify whether to combine the schemas of multiple files, or keep one schema per file reverse-engineered [default: false]</td>
</tr>
<tr>
<td>--namingConventions=&lt; business | technical &gt;</td>
<td>N</td>
<td><p>If application parameters are set to enable Naming Conventions, specify whether to reverse-engineer source attributes as business names or as technical names. Conversions will be applied according to your Naming Conventions parameters.</p><p>[default: <strong>business</strong>, if Naming Conventions are disabled; or</p><p><strong>technical</strong>, if Naming Conventions are enabled in application Tools &gt; Options]</p></td>
</tr>
<tr>
<td>--distribution=&lt; <strong>true</strong> | false &gt;</td>
<td>N</td>
<td>Specify whether to perform orthogonal distribution of model entities on ERD. [default: true]</td>
</tr>
<tr>
<td>--maxErdEntityBoxes=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>Specify whether to fully expand all collections before distribution. [default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

MongoDB example:

&nbsp;

```bat
hackolade revEng --connectName=local --target=MONGODB --samplingMethod=abs --samplingValue=1000 
--model=C:\Users\Public\Bitbucket\hackolade\schemas\MongoDB\yelp.json --includeEmpty=true --selectedObjects="yelp" --fieldOrder=keep
```

&nbsp;

DynamoDB example:

&nbsp;

```bat
"C:\Program Files\Hackolade\hackolade" revEng --connectName=local --target=DYNAMODB --samplingMethod=abs --samplingValue=1000 
--model=C:\Users\Public\Bitbucket\hackolade\schemas\DynamoDB\entertainment.json --includeEmpty=false --selectedObjects="[Movies, Music]" --fieldOrder=alpha
```

&nbsp;

Couchbase example:

&nbsp;

```bat
"C:\Program Files\Hackolade\hackolade" revEng --connectName=local --target=COUCHBASE --samplingMethod=abs --samplingValue=2500 
--model=C:\Users\Public\Bitbucket\hackolade\schemas\Couchbase\travel-sample.json --includeEmpty=false --selectedObjects="travel-sample: [airline, airport]"
--documentKinds="travel-sample: type" --fieldOrder=keep
```

&nbsp;

Cosmos DB example:

&nbsp;

```bat
start /wait hackolade reveng --target=COSMOSDB-DOC --connectName=azure --model=travel.json --selectedObjects="travel" --documentKinds="travel:type"
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## revEngDataDictionary

The `revEngDataDictionary` command lets you synchronize a previously published Hackolade data models from a Data Dictionary instance (currently Collibra only.)

&nbsp;

Usage: `hackolade revEngDataDictionary [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:23%"><col style="width:10%"><col style="width:67%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--target=&lt;<em>target</em>&gt;</td>
<td>Y</td>
<td>Native target for model: JSON, MONGODB, DYNAMODB, COUCHBASE, or plugin target: Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop, etc..</td>
</tr>
<tr>
<td>--connectName=&lt;connection&gt;</td>
<td>Y if from instance</td>
<td><p>Name of connection settings saved in the Hackolade instance where CLI is invoked.</p><p>Or use --connectFile instead.</p></td>
</tr>
<tr>
<td>--connectFile=&lt;<em>file</em>&gt;*</td>
<td>N</td>
<td>Full file path of connection config file (you don't need to use it when connect name is specified). The simplest way to create a connection file is to create a connection in the GUI application, then export the connection settings to file, encrypted or not.</td>
</tr>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for target Hackolade model into which reverse-engineering process has to be converted. Extension .json is optional</td>
</tr>
<tr>
<td>--dataDictionaryResource=&lt;resource name&gt;</td>
<td>Y</td>
<td>Name of the resource (domain) in the Data Dictionary instance being reverse-engineered</td>
</tr>
<tr>
<td>--fieldOrder=&lt; <strong>keep</strong> | alpha &gt;</td>
<td>N</td>
<td>Specify whether to preserve order of fields in sampled document or rearrange in alpha order <br>[default: keep]</td>
</tr>
<tr>
<td>--update=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>Specify whether to update existing model. If false, existing model will be overwritten [default: false]</td>
</tr>
<tr>
<td>--conflictResolution&lt; <strong>keepBoth</strong> | replace | merge | cancel &gt;</td>
<td>N</td>
<td>Specify conflict resolution strategy for containers and entities [default: keepBoth] [values: "keepBoth", "replace", "merge", "cancel"] [default: "keepBoth"]</td>
</tr>
<tr>
<td>--namingConventions=&lt; business | technical &gt;</td>
<td>N</td>
<td><p>If application parameters are set to enable Naming Conventions, specify whether to reverse-engineer source attributes as business names or as technical names. Conversions will be applied according to your Naming Conventions parameters.</p><p>[default: <strong>business</strong>, if Naming Conventions are disabled; or</p><p><strong>technical</strong>, if Naming Conventions are enabled in application Tools &gt; Options]</p></td>
</tr>
<tr>
<td>--distribution=&lt; <strong>true</strong> | false &gt;</td>
<td>N</td>
<td>Specify whether to perform orthogonal distribution of model entities on ERD. [default: true]</td>
</tr>
<tr>
<td>--maxErdEntityBoxes=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>Specify whether to fully expand all collections before distribution. [default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade revEngDataDictionary --target=MONGODB --connectName=Collibra_instance --dataDictionaryResource=Yelp --model=yelp
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## revEngDDL

The *`revEngDDL`* command allows to trigger a reverse-engineering process of a Data Definition Language file from a database instance, as described in [this page](SQLDDL.md).

&nbsp;

Usage: `hackolade revEngDDL [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:33%"><col style="width:8%"><col style="width:59%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--target=&lt;<em>target</em>&gt;</td>
<td>Y</td>
<td>Native target for model: MONGODB, DYNAMODB, COUCHBASE, or plugin target: ArangoDB, Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop</td>
</tr>
<tr>
<td>--file=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Specify the directory path and file name where the schema file to be reverse-engineered is located (file type must be compatible with selected target.)</td>
</tr>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for target Hackolade model into which reverse-engineering process has to be converted. Extension .json is optional</td>
</tr>
<tr>
<td>--entityHandling=&lt; <strong>ERD</strong> | definitions &gt;</td>
<td>N</td>
<td>Specify whether must be reverse-engineered as entities in ERD or as model definitions [default: ERD]</td>
</tr>
<tr>
<td>--container=&lt;containerName&gt;</td>
<td>N</td>
<td>Specify a container name into which reverse-engineered entities will be inserted [default=""]</td>
</tr>
<tr>
<td>--database=&lt; oracle | mysql | mssqlserver | db2 | postgres | informix | snowflake | teradata &gt;</td>
<td>Y</td>
<td>Name of database of DDL script</td>
</tr>
<tr>
<td>--update=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>Specify whether to update existing model. If false, existing model will be overwritten [default: false]</td>
</tr>
<tr>
<td>--conflictResolution=&lt; <strong>keepBoth</strong> | replace | merge | cancel &gt;</td>
<td>N</td>
<td>Specify conflict strategy for containers and entities [default: keepBoth]</td>
</tr>
<tr>
<td>--namingConventions=&lt; business | technical &gt;</td>
<td>N</td>
<td><p>If application parameters are set to enable Naming Conventions, specify whether to reverse-engineer source attributes as business names or as technical names. Conversions will be applied according to your Naming Conventions parameters.</p><p>[default: <strong>business</strong>, if Naming Conventions are disabled; or</p><p><strong>technical</strong>, if Naming Conventions are enabled in application Tools &gt; Options]</p></td>
</tr>
<tr>
<td>--maxErdEntityBoxes=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>Specify whether to fully expand all collections before distribution. [default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

## revEngDiagram

The *`revEngDiagram`* command allows to trigger a reverse-engineering process of a model from a file created with another modeling tool: a [PowerDesigner file](PowerDesigner.md) for conceptual, logical or physical model (typically .cdm, .ldm or .pdm extension), a [MEGA](<https://bizzdesign.com/transformation-suite/hopex> "target=\"_blank\"") exchange file (.xmg extension), or files with [Mermaid ER diagram code](GenAI-createdMermaidERdiagram.md).(.mmd extension), or with [DBML syntax](GenAI-createdDBML.md) (.dbml extension).

&nbsp;

Usage: `hackolade revEngDiagram [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:24%"><col style="width:10%"><col style="width:66%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--source=&lt; powerdesigner | mermaid | dbml | mega &gt;</td>
<td>Y</td>
<td>Specify the modeling tool providing the source file. Currently only powerdesigner, mermaid, dbml, or mega are a possible value</td>
</tr>
<tr>
<td>--file=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Specify the directory path and file name where the file to be reverse-engineered is located (file must be a valid file for the source.) Absolute and relative paths are allowed. Supported extensions: .cdm, .ldm, .pdm (conceptual, logical, and physical models from PowerDesigner), .mmd (Mermaid ER diagrams), .dbml (DBML syntax files), .xmg (MEGA exchange files)</td>
</tr>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for target Hackolade model into which reverse-engineering process has to be converted. Extension .json is optional. If not specified, the target Hackolade model is located in the same directory than the data model file to be reverse-engineered and receives the same name, with the Hackolade extension .hck.json.</td>
</tr>
<tr>
<td>--target=&lt;<em>target</em>&gt;</td>
<td>Y</td>
<td>Specify the target for the Hackolade Studio model to create. For a logical model, the target must be polyglot. For a physical model, the target must be one of the Hackolade Studio physical targets. For a MEGA file, the target must be Polyglot.</td>
</tr>
<tr>
<td>--maxErdEntityBoxes=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>Specify whether to fully expand all collections before distribution. [default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
start /wait hackolade revEngDiagram --source=PowerDesigner --file=MyLogicalDataModel.ldm --target=Polyglot

start /wait hackolade revEngDiagram --source=mega --file=Sales.xmg --target=Polyglot
```

&nbsp;

## revEngJSON

The *`revEngJSON`* command allows to trigger a reverse-engineering process of a JSON document or JSON Schema file, as described in [this page](JSONdocument1.md).

&nbsp;

Usage: `hackolade revEngJSON [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:24%"><col style="width:10%"><col style="width:66%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--target=&lt;<em>target</em>&gt;</td>
<td>Y</td>
<td>Native target for model: JSON, MONGODB, DYNAMODB, COUCHBASE, or plugin target: ArangoDB, Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop</td>
</tr>
<tr>
<td>--files="&lt;file1&gt;;&lt;file2&gt;..."</td>
<td>Y</td>
<td>Specify the directory path and file names to be reverse-engineered</td>
</tr>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for target Hackolade model into which reverse-engineering process has to be converted. Extension .json is optional</td>
</tr>
<tr>
<td>--entityHandling=&lt; <strong>ERD</strong> | definitions &gt;</td>
<td>N</td>
<td>Specify whether must be reverse-engineered as entities in ERD or as model definitions [default: ERD]</td>
</tr>
<tr>
<td>--container=&lt;containerName&gt;</td>
<td>N</td>
<td>Specify a container name into which reverse-engineered entities will be inserted [default=""]</td>
</tr>
<tr>
<td>--normalization=&lt; <strong>true</strong> | false &gt;</td>
<td>N</td>
<td>Only applicable to RDBMS. Specify whether complex data types should be normalized into separate entities [default: true]</td>
</tr>
<tr>
<td>--conflictResolution=&lt; <strong>keepBoth</strong> | replace | merge | cancel &gt;</td>
<td>N</td>
<td>Specify conflict strategy for containers and entities [default: keepBoth]</td>
</tr>
<tr>
<td>--ndjson=&lt; true | <strong>false</strong> &gt;</td>
<td>N</td>
<td>Specify whether the file is contains NDJSON to leverage sampling options [default: false]</td>
</tr>
<tr>
<td>--namingConventions=&lt; business | technical &gt;</td>
<td>N</td>
<td><p>If application parameters are set to enable Naming Conventions, specify whether to reverse-engineer source attributes as business names or as technical names. Conversions will be applied according to your Naming Conventions parameters.</p><p>[default: <strong>business</strong>, if Naming Conventions are disabled; or</p><p><strong>technical</strong>, if Naming Conventions are enabled in application Tools &gt; Options]</p></td>
</tr>
<tr>
<td>--maxErdEntityBoxes=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>Specify whether to fully expand all collections before distribution. [default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

## revEngYAML

The *`revEngYAML`* command allows to trigger a reverse-engineering process of a YAML document file, as described in [this page](JSONdocument1.md).

&nbsp;

Usage: `hackolade revEngJSON [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:24%"><col style="width:10%"><col style="width:66%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--target=&lt;<em>target</em>&gt;</td>
<td>Y</td>
<td>Native target for model: JSON, MONGODB, DYNAMODB, COUCHBASE, or plugin target: ArangoDB, Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop</td>
</tr>
<tr>
<td>--files="&lt;file1&gt;;&lt;file2&gt;..."</td>
<td>Y</td>
<td>Specify the directory path and file names to be reverse-engineered</td>
</tr>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for target Hackolade model into which reverse-engineering process has to be converted. Extension .json is optional</td>
</tr>
<tr>
<td>--entityHandling=&lt; <strong>ERD</strong> | definitions &gt;</td>
<td>N</td>
<td>Specify whether must be reverse-engineered as entities in ERD or as model definitions [default: ERD]</td>
</tr>
<tr>
<td>--container=&lt;containerName&gt;</td>
<td>N</td>
<td>Specify a container name into which reverse-engineered entities will be inserted [default=""]</td>
</tr>
<tr>
<td>--normalization=&lt; <strong>true</strong> | false &gt;</td>
<td>N</td>
<td>Only applicable to RDBMS. Specify whether complex data types should be normalized into separate entities [default: true]</td>
</tr>
<tr>
<td>--conflictResolution=&lt; <strong>keepBoth</strong> | replace | merge | cancel &gt;</td>
<td>N</td>
<td>Specify conflict strategy for containers and entities [default: keepBoth]</td>
</tr>
<tr>
<td>--ndjson=&lt; true | <strong>false</strong> &gt;</td>
<td>N</td>
<td>Specify whether the file is contains NDJSON to leverage sampling options [default: false]</td>
</tr>
<tr>
<td>--namingConventions=&lt; business | technical &gt;</td>
<td>N</td>
<td><p>If application parameters are set to enable Naming Conventions, specify whether to reverse-engineer source attributes as business names or as technical names. Conversions will be applied according to your Naming Conventions parameters.</p><p>[default: <strong>business</strong>, if Naming Conventions are disabled; or</p><p><strong>technical</strong>, if Naming Conventions are enabled in application Tools &gt; Options]</p></td>
</tr>
<tr>
<td>--maxErdEntityBoxes=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>Specify whether to fully expand all collections before distribution. [default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

## revEngXLSX

The *`revEngXLSX`* command allows to import an Excel template into a data model.

&nbsp;

> [!WARNING]
> When importing into an existing model, values will be over written by the values in the Excel file.

&nbsp;

Usage: `hackolade revEngXLSX [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:27%"><col style="width:10%"><col style="width:63%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--file=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Specify the directory path and file name where the Excel template file to be reverse-engineered is located</td>
</tr>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td><p>Full path and file name for target Hackolade model into which reverse-engineering process has to be converted. Extension .json is optional</p><p>If data model is an existing one, target must be compatible with the target of Excel file</p></td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

## revEngXSD

The *`revEngXSD`* command allows to trigger a reverse-engineering process of an XMS schema (XSD).

&nbsp;

Usage: `hackolade revEngXSD [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:27%"><col style="width:10%"><col style="width:63%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--target=&lt;<em>target</em>&gt;</td>
<td>Y</td>
<td>Native target for model: MONGODB, DYNAMODB, COUCHBASE, or plugin target: ArangoDB, Avro, CASSANDRA, COSMOSDB-SQL, COSMOSDB-MONGO, ELASTICSEARCH, EventBridge, Glue, HBase, HIVE, JOI, MSSQLServer; NEO4J, OPENAPI, PARQUET, ScyllaDB, Snowflake, SWAGGER, Synapse, TinkerPop</td>
</tr>
<tr>
<td>--file=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Specify the directory path and file name where the schema file to be reverse-engineered is located (file type must be compatible with selected target.)</td>
</tr>
<tr>
<td>--model=&lt;<em>file</em>&gt;*</td>
<td>Y</td>
<td>Full path and file name for target Hackolade model into which reverse-engineering process has to be converted. Extension .json is optional</td>
</tr>
<tr>
<td>--entityHandling=&lt; <strong>ERD</strong> | definitions &gt;</td>
<td>N</td>
<td>Specify whether must be reverse-engineered as entities in ERD or as model definitions [default: ERD]</td>
</tr>
<tr>
<td>--container=&lt;containerName&gt;</td>
<td>N</td>
<td>Specify a container name into which reverse-engineered entities will be inserted [default=""]</td>
</tr>
<tr>
<td>--conflictResolution=&lt; <strong>keepBoth</strong> | replace | merge | cancel &gt;</td>
<td>N</td>
<td>Specify conflict strategy for containers and entities [default: keepBoth]</td>
</tr>
<tr>
<td>--namingConventions=&lt; business | technical &gt;</td>
<td>N</td>
<td><p>If application parameters are set to enable Naming Conventions, specify whether to reverse-engineer source attributes as business names or as technical names. Conversions will be applied according to your Naming Conventions parameters.</p><p>[default: <strong>business</strong>, if Naming Conventions are disabled; or</p><p><strong>technical</strong>, if Naming Conventions are enabled in application Tools &gt; Options]</p></td>
</tr>
<tr>
<td>--maxErdEntityBoxes=&lt; true | <strong>false </strong>&gt;</td>
<td>N</td>
<td>Specify whether to fully expand all collections before distribution. [default: false]</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

## obfusc

The `obfusc` command lets you garble sensitive properties: business name, technical name, description, comments, enumeration. Use if you need to send a model for troubleshooting but don't want to disclose sensitive aspects of the model.

&nbsp;

Usage: `hackolade obfusc [--arguments]`

&nbsp;

<table style="width:100%">
<colgroup><col style="width:23%"><col style="width:10%"><col style="width:67%"></colgroup>
<thead>
<tr>
<th>Argument</th>
<th>Required</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td>--sourcemodel=&lt;file&gt;*</td>
<td>Y</td>
<td>Full path and file name for the Hackolade model to be obfuscated. Extension .json is optional</td>
</tr>
<tr>
<td>--targetmodel=&lt;file&gt;*</td>
<td>Y</td>
<td>Full path and file name for the obfuscated Hackolade model. Extension .json is optional.</td>
</tr>
<tr>
<td>--logLevel=&lt; 1 | 2 | 3 | <strong>4</strong> &gt;</td>
<td>N</td>
<td><p>1 = no spinner, no info, no error messages</p><p>2 = no spinner, no info</p><p>3 = no spinner</p><p>4 = full output</p><p>[default: 4]</p></td>
</tr>
</tbody>
</table>

&nbsp;

\*: If path and/or file name contains blanks, the value must be surrounded by double quotes (“) Path can be ignored if file is in local directory.

&nbsp;

Example:

&nbsp;

```bat
C:\PROGRA~1\Hackolade\hackolade obfusc --sourcemodel=masterdata --targetmodel=garbeledmasterdata
```

&nbsp;

> [!NOTE]
> If the path contains spaces, Windows generates an error message when running the CLI from another directory than the one where the Hackolade executable was installed, even if using quotes, e.g.: `"C:\Program Files\Hackolade\hackolade"` . The workaround, assuming:

&nbsp;

![Windows Program Files](<lib/Windows Program Files.png>)\
is to to use the 8.3 command `C:\PROGRA~1\Hackolade\hackolade`, as displayed above.

&nbsp;

## help

The `--`*`help`* argument displays the version number of Hackolade being invoked.

&nbsp;

Usage: `start /wait hackolade --help`

&nbsp;

## performance

The *`--performance`* argument records timestamps of application startup steps for performance troubleshooting. Log can be found in file HackoladePerformance.log in directory `C:\Users\%username%\AppData\Roaming\HackoladeLogs` (Windows) or folder `Users/$USER/Documents/HackoladeLogs` (Mac/Linux)

&nbsp;

Usage: `start /wait hackolade --performance`

&nbsp;

## version

The `--`*`version`* argument displays the version number of Hackolade being invoked.

&nbsp;

Usage: `start /wait hackolade --version`

&nbsp;

## CLI error message

You may download an Excel file with CLI error messages [here](<https://hackolade.com/downloads/CLI_Error_Messages_Hackolade.xlsx> "target=\"_blank\"").
