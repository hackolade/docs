# dbt schema models

[](<https://www.getdbt.com/> "target=\"\_blank\"")

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

## Auto-generated properties

There are many keywords in dbt, called properties and configs.&nbsp; Below is a list of the relevant keywords in the context of Hackolade Studio.&nbsp; See also this [styling guide](<https://docs.getdbt.com/best-practices/how-we-style/1-how-we-style-our-dbt-models> "target=\"\_blank\"") for dbt models.

&nbsp;

### name

[name](<https://docs.getdbt.com/reference/project-configs/name> "target=\"\_blank\""): must be letters, digits and underscores only, and cannot start with a digit

> name: string

&nbsp;

We use the technical name if present, otherwise the business name for the object.

&nbsp;

### description

[description](<https://docs.getdbt.com/reference/resource-properties/description> "target=\"\_blank\""): a user-defined description. Can be used to document a model, and model columns

> version: 2\
models:\
&nbsp; &nbsp; - name: dim\_customers\
&nbsp; &nbsp; &nbsp; description: One record per customer\
&nbsp; &nbsp; &nbsp; columns:\
&nbsp; &nbsp; &nbsp; &nbsp; - name: customer\_id\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; description: Primary key

&nbsp;

For multi-line description: we use YAML [block notation](<https://yaml-multiline.info/> "target=\"\_blank\"") to split a longer description over multiple lines\
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

> version: 2\
models:\
&nbsp; &nbsp; - name: dim\_customers\
&nbsp; &nbsp; &nbsp; description: "\*\*\[Read more\](https://www.google.com/)\*\*"\
&nbsp; &nbsp; &nbsp; columns:\
&nbsp; &nbsp; &nbsp; &nbsp; - name: customer\_id\
&nbsp; &nbsp; &nbsp; &nbsp; description: Primary key.

&nbsp;

### columns

[columns](<https://docs.getdbt.com/reference/resource-properties/columns> "target=\"\_blank\""): can define sub-properties, including name, description, data\_type, constraints.

&nbsp;

&nbsp;

### data type

[data\_type](<https://docs.getdbt.com/sql-reference/data-types> "target=\"\_blank\""): dbt supports scalar and complex semi-structured data types:

&nbsp;

\- numeric: integer, decimal, float

\- string: string, char, varchar, text, character

\- date: date, datetime, time, timestamp

\- Boolean

\- semi-structured: JSON, and array

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

### constraints

[constraints](<https://docs.getdbt.com/reference/resource-properties/constraints> "target=\"\_blank\""): Constraints may be defined for a single column, or at the model level for one or more columns.

If you are defining multiple primary\_key constraints for a single model (entity), those *must* be defined at the model level. Defining multiple primary\_key constraints at the column level is not supported. &nbsp;

&nbsp;

The structure of a constraint is:

\- type (required): one of not\_null, unique, primary\_key, foreign\_key, check, custom

\- expression: Free text input to qualify the constraint. Required for certain constraint types, and optional for others.

\- name (optional): Human-friendly name for this constraint. Supported by some data platforms.

\- columns (model-level only): List of column names to apply the constraint over

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

## Model-level dbt configuration properties

The above properties name, description, columns, data types, and constraints are generated automatically from the modeling objects information. No special setup is required.

&nbsp;

For teams needing more control, Hackolade Studio provides an advanced dbt configuration mode that exposes additional dbt-specific properties which cannot be inferred from the model alone.&nbsp; This capability is only available in physical targets supported where we support dbt, currently: BigQuery, Databricks, Hive, MySQL, Oracle, PostgreSQL, Redshift, Snowflake, SQL Server, Synapse, and Teradata.

&nbsp;

To activate it, check the **dbt model configuration** property in the properties pane of the Model.&nbsp; Doing so reveals a dbt tab at both the entity level and the column level, where dbt-specific settings can be defined.&nbsp; Only non-empty values are included in the generated YAML.

&nbsp;

**Note:** Jinja expressions, e.g. {{ env\_var('DBT\_ENV') }}&nbsp; are supported in free text fields and exported as-is.

&nbsp;

Boolean properties in the dbt tab (such as config.enabled, config.contract.enforced, or config.docs.show ) are represented as a three-state dropdown rather than a simple checkbox. The 3 options are:

* (dbt default - not exported): the property is omitted from the generated YAML entirely
* true: the property is explicitly exported as true
* false: the property is explicitly exported as false

&nbsp;

The default selection is (dbt default - not exported). This avoids cluttering the YAML with values that simply mirror dbt's own defaults, and makes the user's intent unambiguous: if a property appears in the output, it is there on purpose.

&nbsp;

### access

[access](<https://docs.getdbt.com/reference/resource-properties/access> "target=\"\_blank\""): defines which other resources can reference this model. Accepted values: private, protected, public. This is a model-level property, independent of config.

> models:\
&nbsp; - name: dim\_customers\
&nbsp; &nbsp; access: public

&nbsp;

### config

[config](<https://docs.getdbt.com/reference/resource-properties/config> "target=\"\_blank\"") allows to configure resources at the same time as properties in YAML files.

> version: 2\
models:\
&nbsp; - name: \<model\_name\>\
&nbsp; &nbsp; config:\
&nbsp;   &nbsp; \<model\_config\>: \<config\_value\>

&nbsp;

### config.contract.enforced

[contract](<https://docs.getdbt.com/reference/resource-configs/contract> "target=\"\_blank\"") when enforced, dbt ensures that the model's returned dataset exactly matches the column names and data types defined in the YAML. Enable by checking config.contract.enforced.

> models:\
&nbsp; - name: dim\_customers\
&nbsp; &nbsp; config:\
&nbsp;   &nbsp; contract:\
&nbsp;     &nbsp; enforced: true

&nbsp;

### config.incremental\_strategy

[incremental\_strategy](<https://docs.getdbt.com/docs/build/incremental-strategy> "target=\"\_blank\"") defines how dbt performs incremental updates. The available strategies depend on the active target (e.g. merge, append, insert\_overwrite, delete+insert). Only relevant when materialized is set to incremental.

&nbsp;

### config.on\_schema\_change

[on\_schema\_change](<https://docs.getdbt.com/reference/resource-configs/on\_schema\_change> "target=\"\_blank\"") defines how dbt handles schema changes in incremental models. Accepted values: ignore, fail, append\_new\_columns, sync\_all\_columns. Only relevant when materialized is set to incremental.

&nbsp;

### config.on\_configuration\_change

[on\_configuration\_change](<https://docs.getdbt.com/reference/resource-configs/on\_configuration\_change>): defines behavior when configuration changes are detected for materialized views. Accepted values: apply, continue, fail.

&nbsp;

### config.docs.show and config.docs.node\_color

[docs](<https://docs.getdbt.com/reference/resource-configs/docs> "target=\"\_blank\"") controls how the model appears in dbt documentation. Uncheck config.docs.show to hide the model from the docs site. The config.docs.node\_color field accepts a hex color code (e.g. #cd7f32) or a CSS color name, and controls the color of the node in the dbt DAG visualization.

> models:\
&nbsp; - name: dim\_customers\
&nbsp; &nbsp; config:\
&nbsp;   &nbsp; docs:\
&nbsp;     &nbsp; show: true\
&nbsp;     &nbsp; node\_color: "#cd7f32"

&nbsp;

### config.persist\_docs

[persist\_docs](<https://docs.getdbt.com/reference/resource-configs/persist\_docs> "target=\"\_blank\"") when enabled, dbt persists descriptions to the underlying database object as column or relation comments. Check config.persist\_docs.relation to persist the model description, and config.persist\_docs.columns to persist column descriptions.

> models:\
&nbsp; - name: dim\_customers\
&nbsp; &nbsp; config:\
&nbsp;   &nbsp; persist\_docs:\
&nbsp;     &nbsp; relation: true\
&nbsp;     &nbsp; columns: true

&nbsp;

### config.alias

[alias](<https://docs.getdbt.com/reference/resource-configs/alias> "target=\"\_blank\"") overrides the name of the database object that dbt will build. By default, dbt uses the model name.

&nbsp;

### config.schema

[schema](<https://docs.getdbt.com/reference/resource-configs/schema> "target=\"\_blank\"") the schema in which dbt will build the model. Leave this empty to let Studio fall back to the schema defined at the container level in the model. Only set this explicitly if the model needs to target a schema that differs from the one defined in the model structure.

&nbsp;

### config.database

[database](<https://docs.getdbt.com/reference/resource-configs/database> "target=\"\_blank\"") the database in which dbt will build the model. Leave this empty to let Studio fall back to the database defined at the container level in the model. Only set this explicitly if the model needs to target a database that differs from the one defined in the model structure.

&nbsp;

### config.enabled

[enabled](<https://docs.getdbt.com/reference/resource-configs/enabled> "target=\"\_blank\"") when unchecked, dbt skips this model entirely during runs. Defaults to true.

&nbsp;

### config.materialized

[materialized](<https://docs.getdbt.com/reference/resource-configs/materialized> "target=\"\_blank\"") defines how dbt builds the model in the warehouse. Accepted values: table, view, incremental, ephemeral, materialized\_view.

&nbsp;

This value is automatically derived from the object type in your Hackolade model: a table maps to table, a view to view, a materialized view to materialized\_view. You only need to set this explicitly if you want to override that default, for example to declare a table as incremental or ephemeral.

> models:\
&nbsp; - name: dim\_customers\
&nbsp; &nbsp; config:\
&nbsp;   &nbsp; materialized: table

&nbsp;

### config.full\_refresh

[full\_refresh](<https://docs.getdbt.com/reference/resource-configs/full\_refresh> "target=\"\_blank\"") when checked, dbt always rebuilds the model from scratch, ignoring any incremental logic. Only relevant when materialized is set to incremental.

&nbsp;

### config.unique\_key

[unique\_key](<https://docs.getdbt.com/reference/resource-configs/unique\_key> "target=\"\_blank\"") the column or combination of columns that uniquely identifies a row, used by dbt to determine which records to update or insert during an incremental run. Only relevant when materialized is set to incremental.

&nbsp;

This field is not auto-populated from the model. Even when a primary key is defined, Hackolade does not attempt to infer the unique key for incremental runs — there may be multiple candidate keys, and the right choice depends on the transformation logic. The user must specify it explicitly.

&nbsp;

Accepts a single column name or a comma-separated list of column names.

> models:\
&nbsp; - name: dim\_customers\
&nbsp; &nbsp; config:\
&nbsp;   &nbsp; materialized: incremental\
&nbsp;   &nbsp; unique\_key: customer\_id

&nbsp;

> models:\
&nbsp; - name: dim\_customers\
&nbsp; &nbsp; config:\
&nbsp;   &nbsp; materialized: incremental\
&nbsp;   &nbsp; unique\_key: \[customer\_id, updated\_at\]

&nbsp;

### config.group

[group](<https://docs.getdbt.com/reference/resource-configs/group> "target=\"\_blank\"") assigns the model to a dbt group, which can be used together with access controls to manage cross-group model references.

&nbsp;

### config.sql\_header

[sql\_header](<https://docs.getdbt.com/reference/resource-configs/sql\_header> "target=\"\_blank\"") SQL to inject at the top of the compiled file, before the model query. Useful for session-level settings on platforms like Snowflake or BigQuery.

&nbsp;

### deprecation\_date

[deprecation\_date](<https://docs.getdbt.com/reference/resource-properties/deprecation\_date> "target=\"\_blank\"") marks the model as deprecated as of a given date. Accepts an ISO 8601 date string (e.g. 2025-12-31). The model still builds and can still be referenced, but dbt will emit a warning when downstream models use it.

> models:\
&nbsp; - name: dim\_customers\
&nbsp; &nbsp; deprecation\_date: "2025-12-31"

&nbsp;

### tags

[tags](<https://docs.getdbt.com/reference/resource-configs/tags> "target=\"\_blank\"") one or more tags to apply to the model. Tags can be used to select or exclude groups of models when running dbt commands. Accepts multiple values.

> models:\
&nbsp; - name: dim\_customers\
&nbsp; &nbsp; tags:\
&nbsp;   &nbsp; - nightly\
&nbsp;   &nbsp; - finance

&nbsp;

## Column-level dbt configuration properties

When dbt model configuration property is checked at the model level, a dbt tab also appears at the attribute level in the properties pane. The following properties are available.

&nbsp;

### quote

[quote](<https://docs.getdbt.com/reference/resource-properties/quote> "target=\"\_blank\"") when checked, dbt quotes the column name in generated SQL. Useful for column names that are reserved words or require case-sensitivity.

> columns:\
&nbsp; - name: Order\
&nbsp; &nbsp; quote: true

&nbsp;

### tags

[tags](<https://docs.getdbt.com/reference/resource-configs/tags> "target=\"\_blank\"") one or more tags applied at the column level. Accepts multiple values.

&nbsp;

### policy\_tags

policy\_tags: a list of [BigQuery policy tag](<https://cloud.google.com/bigquery/docs/column-level-security-intro> "target=\"\_blank\"") identifiers to apply to the column, used for column-level access control and data governance. Accepts multiple values. This property is specific to BigQuery targets.

> columns:\
&nbsp; - name: customer\_email\
&nbsp; &nbsp; policy\_tags:\
&nbsp;   &nbsp; - "projects/my-project/locations/us/taxonomies/123/policyTags/456"

&nbsp;

&nbsp;

&nbsp;

## dbt meta from custom properties

The [meta](<https://docs.getdbt.com/reference/resource-configs/meta> "target=\"\_blank\"") field in dbt is a free-form dictionary that accepts any custom key-value pairs, at model- or column-level. It is commonly used to attach governance metadata, ownership information, or any other custom attributes.

&nbsp;

Hackolade Studio lets you map your own [custom properties](<Userdefinedcustomproperties.md>) directly to dbt meta, without any change to the properties pane.

&nbsp;

To enable this, add includeInDbtMeta: true to the relevant custom property definition in your entityLevelConfig.json or fieldLevelConfig.json. When forward-engineering to dbt, any property flagged this way is automatically exported under meta: in the generated YAML.

&nbsp;

Example: a custom property data\_owner defined at entity level:

> {\
&nbsp; "propertyName": "data\_owner",\
&nbsp; "propertyKeyword": "data\_owner",\
&nbsp; "propertyType": "text",\
&nbsp; "includeInDbtMeta": true\
}

&nbsp;

Example: a custom property pii flag defined at field level:

> {\
&nbsp; "propertyName": "PII",\
&nbsp; "propertyKeyword": "pii",\
&nbsp; "propertyType": "checkbox",\
&nbsp; "includeInDbtMeta": true\
}

&nbsp;

When forward-engineering to dbt, any property flagged this way is automatically exported under meta: in the generated YAML.

&nbsp;

Custom property types are mapped to dbt meta types as follows:

&nbsp;

| **Hackolade type** | **dbt meta type** |
| --- | --- |
| text / textarea | string |
| checkbox | boolean |
| dropdown | number |
| dropdown (single) | string |
| multiselect | array of strings |


&nbsp;

&nbsp;

**Note:** complex custom property types (such as property groups or block) are not supported by dbt and will not be exported to meta.

&nbsp;

Example output combining model-level and column-level meta:

> models:\
&nbsp; - name: dim\_customers\
&nbsp; &nbsp; meta:\
&nbsp; &nbsp; &nbsp; data\_owner: finance-team\
&nbsp; &nbsp; columns:\
&nbsp; &nbsp; &nbsp; - name: customer\_id\
&nbsp; &nbsp; &nbsp; &nbsp; description: Primary key\
&nbsp; &nbsp; &nbsp; - name: customer\_email\
&nbsp; &nbsp; &nbsp; &nbsp; description: Contact email address\
&nbsp; &nbsp; &nbsp; &nbsp; meta:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pii: true

&nbsp;

&nbsp;

&nbsp;

## 