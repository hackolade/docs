# dbt schema models

[dbt](<https://www.getdbt.com/> "target=\"\_blank\"") is a SQL-first transformation workflow that lets teams quickly and collaboratively deploy analytics code following software engineering best practices like modularity, portability, CI/CD, and documentation. It helps teams work directly within the warehouse to produce trusted datasets for reporting, ML modeling, and operational workflows.&nbsp;

&nbsp;

dbt performs the T (Transform) of ETL (actually ELT) but it doesn’t offer support for Extraction and Load operations. It allows companies to write transformations as queries and orchestrate them in a more efficient way.&nbsp;

&nbsp;

Multiple SQL-like [databases](<https://docs.getdbt.com/docs/trusted-adapters> "target=\"\_blank\"") are supported currently, including: BigQuery, Databricks, Hive, MySQL, Oracle, PostgreSQL, Redshift, Snowflake, SQL Server, Synapse, and Teradata.

&nbsp;

For selected targets, Hackolade Studio facilitates the transformation of data in your warehouse with dbt, by letting you generate the model properties schema.yml for tables in your source and target models.&nbsp; The feature is available in Tools \> Forward-Engineering \> dbt models

&nbsp;

## dbt models

**Warning:** the term "model" in dbt terminology is different than for Hackolade.&nbsp; In dbt \<model name\> is the technical name of an entity/table/collection/record in Hackolade Studio.

&nbsp;

[Model properties](<https://docs.getdbt.com/reference/model-properties> "target=\"\_blank\"") are declared in .yml files generally in a models/ directory (or possibly elsewhere.)&nbsp; These files can be named whatever\_you\_want.yml (for us, it will be either the schema's technical name or the entity's technical name, depending on the option chosen.)

&nbsp;

Example:

> version: 2\
models:\
&nbsp; &nbsp; - name: \<model name\>\
&nbsp; &nbsp; &nbsp; description: \<markdown\_string\>\
&nbsp; &nbsp; &nbsp; columns:\
&nbsp; &nbsp; &nbsp; &nbsp; - name: \<column\_name\> # required\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; data\_type: \<string\>\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; description: \<markdown\_string\>\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; constraints:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; - \<constraint\>\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; tags: \[\<string\>\]\
&nbsp; &nbsp; &nbsp; &nbsp; - name: ... # declare properties of additional columns\
&nbsp; &nbsp; constraints:\
&nbsp; &nbsp; &nbsp; &nbsp; - \<constraint\>\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; config:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \<model\_config\>: \<config\_value\>

&nbsp;

Users are able to choose to have one file per entity or one file per schema, in which case, multiple entities are listed inside the same model file.

&nbsp;

## dbt keywords

There are many keywords in dbt, called properties and configs.&nbsp; Below is a list of the relevant keywords in the context of Hackolade Studio.&nbsp; See also this [styling guide](<https://docs.getdbt.com/best-practices/how-we-style/1-how-we-style-our-dbt-models> "target=\"\_blank\"") for dbt models.

&nbsp;

### Name

[Name](<https://docs.getdbt.com/reference/project-configs/name> "target=\"\_blank\""): must be letters, digits and underscores only, and cannot start with a digit

&nbsp;

> name: string

&nbsp;

We use the technical name if present, otherwise the business name for the object.

&nbsp;

### Description

[Description](<https://docs.getdbt.com/reference/resource-properties/description> "target=\"\_blank\""): a user-defined description. Can be used to document a model, and model columns

&nbsp;

> version: 2\
models:\
&nbsp; &nbsp; - name: dim\_customers\
&nbsp; &nbsp; &nbsp; description: One record per customer\
&nbsp; &nbsp; &nbsp; columns:\
&nbsp; &nbsp; &nbsp; &nbsp; - name: customer\_id\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; description: Primary key

&nbsp;

For multi-line description: we use YAML [block notation](<https://yaml-multiline.info/> "target=\"\_blank\"") to split a longer description over multiple lines

&nbsp;

> \
version: 2\
models:\
&nbsp; - name: dim\_customers\
&nbsp; &nbsp; description: \>\
&nbsp; &nbsp; &nbsp; One record per customer. Note that a customer must have made a purchase to\
&nbsp; &nbsp; &nbsp; be included in this \<Term id="table" /\> — customer accounts that were created but never\
&nbsp; &nbsp; &nbsp; used have been filtered out.\
&nbsp; &nbsp; columns:\
&nbsp; &nbsp; &nbsp; - name: customer\_id\
&nbsp; &nbsp; &nbsp; &nbsp; description: Primary key

&nbsp;

Markdown in description is possible too, but requires to quote description to ensure that the YAML parser doesn't get confused by special characters.

&nbsp;

> version: 2\
models:\
&nbsp; &nbsp; - name: dim\_customers\
&nbsp; &nbsp; &nbsp; description: "\*\*\[Read more\](https://www.google.com/)\*\*"\
&nbsp; &nbsp; &nbsp; columns:\
&nbsp; &nbsp; &nbsp; &nbsp; - name: customer\_id\
&nbsp; &nbsp; &nbsp; &nbsp; description: Primary key.

&nbsp;

### Columns

[Columns](<https://docs.getdbt.com/reference/resource-properties/columns> "target=\"\_blank\""): can define sub-properties, including name, description, data\_type, constraints.

&nbsp;

&nbsp;

### Data type

[data\_type](<https://docs.getdbt.com/sql-reference/data-types> "target=\"\_blank\""): dbt supports scalar and complex semi-structured data types:

&nbsp;

\- numeric: integer, decimal, float

\- string: string, char, varchar, text, character

\- date: date, datetime, time, timestamp

\- Boolean

\- semi-structured: JSON, and array

&nbsp;

> models:\
&nbsp; &nbsp; - name: dim\_customers\
&nbsp; &nbsp; &nbsp; columns:\
&nbsp; &nbsp; &nbsp; &nbsp; - name: customer\_id\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; data\_type: int\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; constraints:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; - type: not\_null\
&nbsp; &nbsp; &nbsp; &nbsp; - name: customer\_name\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; data\_type: string\
&nbsp; &nbsp; &nbsp; &nbsp; - name: non\_integer\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; data\_type: numeric(38,3)

&nbsp;

### Constraints

[Constraints](<https://docs.getdbt.com/reference/resource-properties/constraints> "target=\"\_blank\""): Constraints may be defined for a single column, or at the model level for one or more columns.

If you are defining multiple primary\_key constraints for a single model (entity), those *must* be defined at the model level. Defining multiple primary\_key constraints at the column level is not supported. &nbsp;

&nbsp;

The structure of a constraint is:

\- type (required): one of not\_null, unique, primary\_key, foreign\_key, check, custom

\- expression: Free text input to qualify the constraint. Required for certain constraint types, and optional for others.

\- name (optional): Human-friendly name for this constraint. Supported by some data platforms.

\- columns (model-level only): List of column names to apply the constraint over

&nbsp;

> models:\
&nbsp; &nbsp; - name: \<model\_name\> \
&nbsp; &nbsp; &nbsp; # required\
&nbsp; &nbsp; &nbsp; config\
&nbsp; &nbsp; &nbsp; &nbsp; contract:\
&nbsp; &nbsp; &nbsp; &nbsp; enforced: true\
\
&nbsp; &nbsp; &nbsp; columns:\
&nbsp; &nbsp; &nbsp; &nbsp; - name: FIRST\_COLUMN\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; data\_type: DATA\_TYPE\
\
&nbsp; &nbsp; # column-level constraints\
&nbsp; &nbsp; constraints:\
&nbsp; &nbsp; &nbsp; &nbsp; - type: not\_null\
&nbsp; &nbsp; &nbsp; &nbsp; - type: unique\
&nbsp; &nbsp; &nbsp; &nbsp; - type: foreign\_key\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; expression: OTHER\_MODEL\_SCHEMA.OTHER\_MODEL\_NAME (OTHER\_MODEL\_COLUMN)\
&nbsp; &nbsp; &nbsp; &nbsp; - type\
\
&nbsp; &nbsp; &nbsp; # model-level constraints\
&nbsp; &nbsp; &nbsp; constraints:\
&nbsp; &nbsp; &nbsp; &nbsp; - type: primary\_key\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; columns: \[FIRST\_COLUMN, SECOND\_COLUMN, ...\]\
&nbsp; &nbsp; &nbsp; &nbsp; - type: FOREIGN\_KEY # multi\_column\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; columns: \[FIRST\_COLUMN, SECOND\_COLUMN, ...\]\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; expression: "OTHER\_MODEL\_SCHEMA.OTHER\_MODEL\_NAME (OTHER\_MODEL\_FIRST\_COLUMN,OTHER\_MODEL\_SECOND\_COLUMN, ...)"\
&nbsp; &nbsp; &nbsp; &nbsp; - type: check\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; columns: \[FIRST\_COLUMN, SECOND\_COLUMN, ...\]\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; expression: "FIRST\_COLUMN \!= SECOND\_COLUMN"\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; name: HUMAN\_FRIENDLY\_NAME\
&nbsp; &nbsp; &nbsp; &nbsp; - type: ...\
: ...

&nbsp;

### Config (TBA)

[config](<https://docs.getdbt.com/reference/resource-properties/config> "target=\"\_blank\""): allows to configure resources at the same time as properties in YAML files.

&nbsp;

> version: 2\
models:\
&nbsp; &nbsp; - name: \<model\_name\>\
&nbsp; &nbsp; &nbsp; config:\
&nbsp; &nbsp; &nbsp; &nbsp; \<model\_config\>: \<config\_value\>\
&nbsp; &nbsp; &nbsp; &nbsp; ...

&nbsp;

where

> version: 2\
models:\
&nbsp; &nbsp; - name: \[\<model-name\>\]\
&nbsp; &nbsp; config:\
&nbsp; &nbsp; &nbsp; &nbsp; database: \<string\>\
&nbsp; &nbsp; &nbsp; &nbsp; schema: \<string\>\
&nbsp; &nbsp; &nbsp; &nbsp; contract: {\<dictionary\>}

&nbsp;

There are platform-specific configs for [BigQuery](<https://docs.getdbt.com/reference/resource-configs/bigquery-configs> "target=\"\_blank\""), [Databricks](<https://docs.getdbt.com/reference/resource-configs/databricks-configs> "target=\"\_blank\""), [Oracle](<https://docs.getdbt.com/reference/resource-configs/oracle-configs> "target=\"\_blank\""), [PostgreSQL](<https://docs.getdbt.com/reference/resource-configs/postgres-configs> "target=\"\_blank\""), [Redshift](<https://docs.getdbt.com/reference/resource-configs/redshift-configs> "target=\"\_blank\""), [Snowflake](<https://docs.getdbt.com/reference/resource-configs/snowflake-configs> "target=\"\_blank\""), [SQL Server](<https://docs.getdbt.com/reference/resource-configs/mssql-configs> "target=\"\_blank\""), [Synapse](<https://docs.getdbt.com/reference/resource-configs/azuresynapse-configs> "target=\"\_blank\""),&nbsp; and [Teradata](<https://docs.getdbt.com/reference/resource-configs/teradata-configs> "target=\"\_blank\"").&nbsp; Currently, Hackolade Studio does not generate platform-specific configs.

&nbsp;

### Contract (TBA)

[Contract](<https://docs.getdbt.com/reference/resource-configs/contract> "target=\"\_blank\""): when the contract configuration is enforced, dbt will ensure that your model's returned dataset exactly matches the attributes you have defined in yaml:

&nbsp;

\- name and data\_type for every column

\- additional [constraints](<https://docs.getdbt.com/reference/resource-properties/constraints> "target=\"\_blank\""), as supported for this materialization and data platform

&nbsp;

This is to ensure that the people querying your model downstream -- both inside and outside dbt -- have a predictable and consistent set of columns to use in their analyses. dbt uses built-in type aliasing for the data\_type defined in your YAML. For example, you can specify string in your contract, and on Postgres/Redshift, dbt will convert it to text. If dbt doesn't recognize the data\_type name among its known aliases, it will pass it through as-is. This is enabled by default, but you can opt-out by setting alias\_types to false.

&nbsp;

> models:\
&nbsp; &nbsp; - name: dim\_customers\
&nbsp; &nbsp; &nbsp; config:\
&nbsp; &nbsp; &nbsp; &nbsp; materialized: table\
&nbsp; &nbsp; &nbsp; contract:\
&nbsp; &nbsp; &nbsp; &nbsp; enforced: true\
&nbsp; &nbsp; &nbsp; &nbsp; alias\_types: false # true by default\
&nbsp; &nbsp; &nbsp; columns:\
&nbsp; &nbsp; &nbsp; &nbsp; - name: customer\_id\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; data\_type: int\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; constraints:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; - type: not\_null\
&nbsp; &nbsp; &nbsp; &nbsp; - name: customer\_name\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; data\_type: string\
&nbsp; &nbsp; &nbsp; &nbsp; - name: non\_integer\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; data\_type: numeric(38,3)

&nbsp;

&nbsp;

&nbsp;

