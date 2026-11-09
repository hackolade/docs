---
description: Hackolade Studio generates dbt model property files with names, descriptions, columns, data types and constraints.
seoTitle: Generate dbt schema model properties
---
# dbt schema models

> [!WARNING]
> The term "model" in dbt terminology is different than for Hackolade. In dbt \<model name> is the technical name of an entity/table/collection/record in Hackolade Studio.

[Model properties](<https://docs.getdbt.com/reference/model-properties> "target=\"_blank\"") are declared in `.yml` files generally in a `models/` directory (or possibly elsewhere.) These files can be named `whatever_you_want.yml` (for us, it will be either the schema's technical name or the entity's technical name, depending on the option chosen.)

Example:

```yaml
version: 2
models:
    - name: <model name>
      description: <markdown_string>
      columns:
        - name: <column_name> # required
          data_type: <string>
          description: <markdown_string>
          constraints:
            - <constraint>
          tags: [<string>]
        - name: ... # declare properties of additional columns
    constraints:
        - <constraint>
          config:
            <model_config>: <config_value>
```

Users are able to choose to have one file per entity or one file per schema, in which case, multiple entities are listed inside the same model file.

## Auto-generated properties

There are many keywords in dbt, called properties and configs. Below is a list of the relevant keywords in the context of Hackolade Studio. See also this [styling guide](<https://docs.getdbt.com/best-practices/how-we-style/1-how-we-style-our-dbt-models> "target=\"_blank\"") for dbt models.

### name

[name](<https://docs.getdbt.com/reference/project-configs/name> "target=\"_blank\""): must be letters, digits and underscores only, and cannot start with a digit

```text
name: string
```

We use the technical name if present, otherwise the business name for the object.

### description

[description](<https://docs.getdbt.com/reference/resource-properties/description> "target=\"_blank\""): a user-defined description. Can be used to document a model, and model columns

```yaml
version: 2
models:
    - name: dim_customers
      description: One record per customer
      columns:
        - name: customer_id
          description: Primary key
```

For multi-line description: we use YAML [block notation](<https://yaml-multiline.info/> "target=\"_blank\"") to split a longer description over multiple lines\
`version: 2`\
`models:`\
`  - name: dim_customers`\
`    description: >`\
`      One record per customer. Note that a customer must have made a purchase to`

```yaml
be included in this <Term id="table" /> — customer accounts that were created but never
used have been filtered out.
    columns:
      - name: customer_id
        description: Primary key
```

Markdown in description is possible too, but requires to quote description to ensure that the YAML parser doesn't get confused by special characters.

```yaml
version: 2
models:
    - name: dim_customers
      description: "**[Read more](https://www.google.com/)**"
      columns:
        - name: customer_id
        description: Primary key.
```

### columns

[columns](<https://docs.getdbt.com/reference/resource-properties/columns> "target=\"_blank\""): can define sub-properties, including name, description, data_type, constraints.

### data type

[data_type](<https://docs.getdbt.com/sql-reference/data-types> "target=\"_blank\""): dbt supports scalar and complex semi-structured data types:

- numeric: integer, decimal, float
- string: string, char, varchar, text, character
- date: date, datetime, time, timestamp
- Boolean
- semi-structured: JSON, and array

```yaml
models:
    - name: dim_customers
      columns:
        - name: customer_id
          data_type: int
          constraints:
            - type: not_null
        - name: customer_name
          data_type: string
        - name: non_integer
          data_type: numeric(38,3)
```

### constraints

[constraints](<https://docs.getdbt.com/reference/resource-properties/constraints> "target=\"_blank\""): Constraints may be defined for a single column, or at the model level for one or more columns.\
If you are defining multiple `primary_key` constraints for a single model (entity), those *must* be defined at the model level. Defining multiple `primary_key` constraints at the column level is not supported.

The structure of a constraint is:

- `type` (required): one of `not_null`, `unique`, `primary_key`, `foreign_key`, `check`, `custom`
- `expression`: Free text input to qualify the constraint. Required for certain constraint types, and optional for others.
- `name` (optional): Human-friendly name for this constraint. Supported by some data platforms.
- `columns` (model-level only): List of column names to apply the constraint over

`models:`\
`- name: <model_name> `\
`  # required`\
`  config`\
`contract:`\
`enforced: true`\
\
`  columns:`\
`- name: FIRST_COLUMN`\
`  data_type: DATA_TYPE`\
\
`# column-level constraints`\
`constraints:`\
`- type: not_null`\
`- type: unique`\
`- type: foreign_key`\
`  expression: OTHER_MODEL_SCHEMA.OTHER_MODEL_NAME (OTHER_MODEL_COLUMN)`\
`- type`\
\
`  # model-level constraints`\
`  constraints:`\
`- type: primary_key`\
`  columns: [FIRST_COLUMN, SECOND_COLUMN, ...]`\
`- type: FOREIGN_KEY # multi_column`\
`  columns: [FIRST_COLUMN, SECOND_COLUMN, ...]`\
`  expression: "OTHER_MODEL_SCHEMA.OTHER_MODEL_NAME (OTHER_MODEL_FIRST_COLUMN,OTHER_MODEL_SECOND_COLUMN, ...)"`\
`- type: check`\
`  columns: [FIRST_COLUMN, SECOND_COLUMN, ...]`\
`  expression: "FIRST_COLUMN != SECOND_COLUMN"`\
`  name: HUMAN_FRIENDLY_NAME`\
`- type: ...`\
*: ...*

## Model-level dbt configuration properties

The above properties name, description, columns, data types, and constraints are generated automatically from the modeling objects information. No special setup is required.

For teams needing more control, Hackolade Studio provides an advanced dbt configuration mode that exposes additional dbt-specific properties which cannot be inferred from the model alone. This capability is only available in physical targets supported where we support dbt, currently: BigQuery, Databricks, Hive, MySQL, Oracle, PostgreSQL, Redshift, Snowflake, SQL Server, Synapse, and Teradata.

To activate it, check the **dbt model configuration** property in the properties pane of the Model. Doing so reveals a dbt tab at both the entity level and the column level, where dbt-specific settings can be defined. Only non-empty values are included in the generated YAML.

> [!NOTE]
> Jinja expressions, e.g. `{{ env_var('DBT_ENV') }}` are supported in free text fields and exported as-is.

Boolean properties in the dbt tab (such as config.enabled, config.contract.enforced, or config.docs.show ) are represented as a three-state dropdown rather than a simple checkbox. The 3 options are:

- (dbt default - not exported): the property is omitted from the generated YAML entirely
- true: the property is explicitly exported as true
- false: the property is explicitly exported as false

The default selection is (dbt default - not exported). This avoids cluttering the YAML with values that simply mirror dbt's own defaults, and makes the user's intent unambiguous: if a property appears in the output, it is there on purpose.

### access

[access](<https://docs.getdbt.com/reference/resource-properties/access> "target=\"_blank\""): defines which other resources can reference this model. Accepted values: `private, protected, public`. This is a model-level property, independent of config.

```yaml
models:
  - name: dim_customers
    access: public
```

### config

[config](<https://docs.getdbt.com/reference/resource-properties/config> "target=\"_blank\"") allows to configure resources at the same time as properties in YAML files.

```yaml
version: 2
models:
  - name: <model_name>
    config:
      <model_config>: <config_value>
```

### config.contract.enforced

[contract](<https://docs.getdbt.com/reference/resource-configs/contract> "target=\"_blank\"") when enforced, dbt ensures that the model's returned dataset exactly matches the column names and data types defined in the YAML. Enable by checking `config.contract.enforced`.

```yaml
models:
  - name: dim_customers
    config:
      contract:
        enforced: true
```

### config.incremental_strategy

[incremental_strategy](<https://docs.getdbt.com/docs/build/incremental-strategy> "target=\"_blank\"") defines how dbt performs incremental updates. The available strategies depend on the active target (e.g. `merge, append, insert_overwrite, delete+insert`). Only relevant when materialized is set to `incremental`.

### config.on_schema_change

[on_schema_change](<https://docs.getdbt.com/docs/build/incremental-models#what-if-the-columns-of-my-incremental-model-change> "target=\"_blank\"") defines how dbt handles schema changes in incremental models. Accepted values: `ignore, fail, append_new_columns, sync_all_columns`. Only relevant when materialized is set to incremental.

### config.on_configuration_change

[on_configuration_change](https://docs.getdbt.com/reference/resource-configs/on_configuration_change): defines behavior when configuration changes are detected for materialized views. Accepted values: `apply, continue, fail`.

### config.docs.show and config.docs.node_color

[docs](<https://docs.getdbt.com/reference/resource-configs/docs> "target=\"_blank\"") controls how the model appears in dbt documentation. Uncheck config.docs.show to hide the model from the docs site. The config.docs.node_color field accepts a hex color code (e.g. #cd7f32) or a CSS color name, and controls the color of the node in the dbt DAG visualization.

```yaml
models:
  - name: dim_customers
    config:
      docs:
        show: true
        node_color: "#cd7f32"
```

### config.persist_docs

[persist_docs](<https://docs.getdbt.com/reference/resource-configs/persist_docs> "target=\"_blank\"") when enabled, dbt persists descriptions to the underlying database object as column or relation comments. Check config.persist_docs.relation to persist the model description, and config.persist_docs.columns to persist column descriptions.

```yaml
models:
  - name: dim_customers
    config:
      persist_docs:
        relation: true
        columns: true
```

### config.alias

[alias](<https://docs.getdbt.com/reference/resource-configs/alias> "target=\"_blank\"") overrides the name of the database object that dbt will build. By default, dbt uses the model name.

### config.schema

[schema](<https://docs.getdbt.com/reference/resource-configs/schema> "target=\"_blank\"") the schema in which dbt will build the model. Leave this empty to let Studio fall back to the schema defined at the container level in the model. Only set this explicitly if the model needs to target a schema that differs from the one defined in the model structure.

### config.database

[database](<https://docs.getdbt.com/reference/resource-configs/database> "target=\"_blank\"") the database in which dbt will build the model. Leave this empty to let Studio fall back to the database defined at the container level in the model. Only set this explicitly if the model needs to target a database that differs from the one defined in the model structure.

### config.enabled

[enabled](<https://docs.getdbt.com/reference/resource-configs/enabled> "target=\"_blank\"") when unchecked, dbt skips this model entirely during runs. Defaults to true.

### config.materialized

[materialized](<https://docs.getdbt.com/reference/resource-configs/materialized> "target=\"_blank\"") defines how dbt builds the model in the warehouse. Accepted values: `table, view, incremental, ephemeral, materialized_view`.

This value is automatically derived from the object type in your Hackolade model: a table maps to `table`, a view to `view`, a materialized view to `materialized_view`. You only need to set this explicitly if you want to override that default, for example to declare a table as incremental or `ephemeral`.

```yaml
models:
  - name: dim_customers
    config:
      materialized: table
```

### config.full_refresh

[full_refresh](<https://docs.getdbt.com/reference/resource-configs/full_refresh> "target=\"_blank\"") when checked, dbt always rebuilds the model from scratch, ignoring any incremental logic. Only relevant when materialized is set to incremental.

### config.unique_key

[unique_key](<https://docs.getdbt.com/reference/resource-configs/unique_key> "target=\"_blank\"") the column or combination of columns that uniquely identifies a row, used by dbt to determine which records to update or insert during an incremental run. Only relevant when materialized is set to incremental.

This field is not auto-populated from the model. Even when a primary key is defined, Hackolade does not attempt to infer the unique key for incremental runs — there may be multiple candidate keys, and the right choice depends on the transformation logic. The user must specify it explicitly.

Accepts a single column name or a comma-separated list of column names.

```yaml
models:
  - name: dim_customers
    config:
      materialized: incremental
      unique_key: customer_id

models:
  - name: dim_customers
    config:
      materialized: incremental
      unique_key: [customer_id, updated_at]
```

### config.group

[group](<https://docs.getdbt.com/reference/resource-configs/group> "target=\"_blank\"") assigns the model to a dbt group, which can be used together with access controls to manage cross-group model references.

### config.sql_header

[sql_header](<https://docs.getdbt.com/reference/resource-configs/sql_header> "target=\"_blank\"") SQL to inject at the top of the compiled file, before the model query. Useful for session-level settings on platforms like Snowflake or BigQuery.

### deprecation_date

[deprecation_date](<https://docs.getdbt.com/reference/resource-properties/deprecation_date> "target=\"_blank\"") marks the model as deprecated as of a given date. Accepts an ISO 8601 date string (e.g. `2025-12-31`). The model still builds and can still be referenced, but dbt will emit a warning when downstream models use it.

```yaml
models:
  - name: dim_customers
    deprecation_date: "2025-12-31"
```

### tags

[tags](<https://docs.getdbt.com/reference/resource-configs/tags> "target=\"_blank\"") one or more tags to apply to the model. Tags can be used to select or exclude groups of models when running dbt commands. Accepts multiple values.

```yaml
models:
  - name: dim_customers
    tags:
      - nightly
      - finance
```

## Column-level dbt configuration properties

When dbt model configuration property is checked at the model level, a dbt tab also appears at the attribute level in the properties pane. The following properties are available.

### quote

[quote](<https://docs.getdbt.com/reference/resource-properties/quote> "target=\"_blank\"") when checked, dbt quotes the column name in generated SQL. Useful for column names that are reserved words or require case-sensitivity.

```yaml
columns:
  - name: Order
    quote: true
```

### tags

[tags](<https://docs.getdbt.com/reference/resource-configs/tags> "target=\"_blank\"") one or more tags applied at the column level. Accepts multiple values.

### policy_tags

policy_tags: a list of [BigQuery policy tag](<https://cloud.google.com/bigquery/docs/column-level-security-intro> "target=\"_blank\"") identifiers to apply to the column, used for column-level access control and data governance. Accepts multiple values. This property is specific to BigQuery targets.

```yaml
columns:
  - name: customer_email
    policy_tags:
      - "projects/my-project/locations/us/taxonomies/123/policyTags/456"
```

## dbt meta from custom properties

The [meta](<https://docs.getdbt.com/reference/resource-configs/meta> "target=\"_blank\"") field in dbt is a free-form dictionary that accepts any custom key-value pairs, at model- or column-level. It is commonly used to attach governance metadata, ownership information, or any other custom attributes.

Hackolade Studio lets you map your own [custom properties](Userdefinedcustomproperties.md) directly to dbt meta, without any change to the properties pane.

To enable this, add `includeInDbtMeta: true` to the relevant custom property definition in your `entityLevelConfig.json` or `fieldLevelConfig.json`. When forward-engineering to dbt, any property flagged this way is automatically exported under `meta:` in the generated YAML.

Example: a custom property `data_owner` defined at entity level:

```json
{
  "propertyName": "data_owner",
  "propertyKeyword": "data_owner",
  "propertyType": "text",
  "includeInDbtMeta": true
}
```

Example: a custom property `pii` flag defined at field level:

```json
{
  "propertyName": "PII",
  "propertyKeyword": "pii",
  "propertyType": "checkbox",
  "includeInDbtMeta": true
}
```

When forward-engineering to dbt, any property flagged this way is automatically exported under `meta:` in the generated YAML.

Custom property types are mapped to dbt meta types as follows:

<table style="width:25%">
<thead>
<tr>
<th>Hackolade type</th>
<th>dbt meta type</th>
</tr>
</thead>
<tbody>
<tr>
<td>text / textarea</td>
<td>string</td>
</tr>
<tr>
<td>checkbox</td>
<td>boolean</td>
</tr>
<tr>
<td>dropdown</td>
<td>number</td>
</tr>
<tr>
<td>dropdown (single)</td>
<td>string</td>
</tr>
<tr>
<td>multiselect</td>
<td>array of strings</td>
</tr>
</tbody>
</table>

> [!NOTE]
> Complex custom property types (such as property groups or block) are not supported by dbt and will not be exported to meta.

Example output combining model-level and column-level meta:

```yaml
models:
  - name: dim_customers
    meta:
      data_owner: finance-team
    columns:
      - name: customer_id
        description: Primary key
      - name: customer_email
        description: Contact email address
        meta:
          pii: true
```
