# dbt sources

In addition to model properties files, Studio can generate dbt [sources](<https://docs.getdbt.com/docs/build/sources> "target=\"\_blank\"") files. Sources are the raw tables in your warehouse that your dbt models build on top of. Declaring them in a sources.yml file lets dbt track freshness, document lineage, and reference source tables using the {{ source() }} function.

&nbsp;

To declare a container as a dbt source group, check the **dbt source group** property in the dbt tab of the container's properties pane. All entities inside that container are then treated as source tables, and forward-engineering produces a sources.yml file instead of a models.yml file.

&nbsp;

Entities in a source group do not expose the model-level dbt configuration properties (materialized, access, contract, etc.); only source-specific properties are available. All entities of a source group produce a single sources.yml file.

&nbsp;

Example:

&nbsp;

> version: 2\
sources:\
&nbsp; - name: \<source\_name\>\
&nbsp; &nbsp; description: \<markdown\_string\>\
&nbsp; &nbsp; database: \<database\>\
&nbsp; &nbsp; schema: \<schema\>\
&nbsp; &nbsp; loaded\_at\_field: \<column\_name\>\
&nbsp; &nbsp; freshness:\
&nbsp;   &nbsp; warn\_after: {count: 12, period: hour}\
&nbsp;   &nbsp; error\_after: {count: 24, period: hour}\
&nbsp; &nbsp; tables:\
&nbsp;   &nbsp; - name: \<table\_name\>\
&nbsp;     &nbsp; description: \<markdown\_string\>\
&nbsp;     &nbsp; identifier: \<identifier\>\
&nbsp;     &nbsp; tags: \[\<string\>\]

## Source group properties (at Studio container level)

## name

The logical identifier for this source group in the dbt project, used as the first argument in {{ source('group\_name', 'table\_name') }} references. This is not a physical database name; database: and schema: carry the physical location.

&nbsp;

Studio uses the container's (business) name for this field.

&nbsp;

### description

Taken directly from the container description in Studio. Not configurable in the dbt tab.

&nbsp;

### database

The database in which the source tables live. Leave this empty to let Studio fall back to the database defined at the container level in the model. Only set this explicitly if it needs to differ from the container's defined database.

schema

&nbsp;

The schema in which the source tables live. Leave this empty to let Studio fall back to the schema defined at the container level in the model. Only set this explicitly if it needs to differ from the container's defined schema.

&nbsp;

### loader

[loader](<https://docs.getdbt.com/reference/resource-properties/loader> "target=\"\_blank\""): a free text description of the tool or process that loads data into this source (e.g. Fivetran, Stitch). Used for documentation purposes only: dbt does not use this value during runs.

&nbsp;

### loaded\_at\_field

[loaded\_at\_field](<https://docs.getdbt.com/reference/resource-properties/freshness#loaded\_at\_field> "target=\"\_blank\""): the column used by dbt to determine when the source was last loaded, required for freshness checks. Defined at source group level and inherited by all tables unless overridden at table level.

&nbsp;

### freshness

[freshness](<https://docs.getdbt.com/reference/resource-properties/freshness>): defines thresholds for how old source data is allowed to be before dbt raises a warning or an error. Defined at source group level and inherited by all tables unless overridden at table level.

&nbsp;

> sources:\
&nbsp; - name: jaffle\_shop\
&nbsp; &nbsp; loaded\_at\_field: \_etl\_loaded\_at\
&nbsp; &nbsp; freshness:\
&nbsp;   &nbsp; warn\_after: {count: 12, period: hour}\
&nbsp;   &nbsp; error\_after: {count: 24, period: hour}

### quoting

[quoting](<https://docs.getdbt.com/reference/resource-properties/quoting> "target=\"\_blank\""): controls whether dbt quotes the database, schema, and identifier when generating SQL for source references. Each sub-property accepts true, false, or empty (the dbt default, not exported).&nbsp;

&nbsp;

> sources:\
&nbsp; - name: jaffle\_shop\
&nbsp; &nbsp; quoting:\
&nbsp;   &nbsp; database: false\
&nbsp;   &nbsp; schema: false\
&nbsp;   &nbsp; identifier: true

&nbsp;

### tags

[tags](<https://docs.getdbt.com/reference/resource-configs/tags> "target=\"\_blank\""): one or more tags to apply to all tables in this source group. Accepts multiple values. Tags defined at source group level are inherited by all tables in the group.

Source table properties (at Studio entity level)

&nbsp;

### name

The name of the source table, taken from the entity name in Hackolade Studio. Used as the second argument in {{ source() }} references.

Note: if a technical name is defined on the entity, see identifier.

&nbsp;

### description

Taken directly from the entity description in Studio. Not configurable in the dbt tab.

&nbsp;

### identifier

[identifier](<https://docs.getdbt.com/reference/resource-properties/identifier>): the actual name of the table in the database. This property is not configurable in the dbt tab: Studio takes it automatically from the model. When a technical name is defined in Studio and differs from the (business) name, the (business) name is used as name: (how you reference the source in dbt) and the technical name is exported as identifier: (the physical table name in the database). If only one name is defined, identifier: is omitted and dbt assumes it matches name:.

&nbsp;

> sources:\
&nbsp; - name: jaffle\_shop\
&nbsp; &nbsp; tables:\
&nbsp;   &nbsp; - name: transaction\_records     # business name\
&nbsp;     &nbsp; identifier: tr\_records\_raw    # technical name

&nbsp;

### tags

[tags](<https://docs.getdbt.com/reference/resource-configs/tags> "target=\"\_blank\""): one or more tags to apply to the source table. Accepts multiple values.

&nbsp;

> sources:\
&nbsp; - name: jaffle\_shop\
&nbsp; &nbsp; tables:\
&nbsp;   &nbsp; - name: orders\
&nbsp;     &nbsp; tags:\
&nbsp;       &nbsp; - nightly\
&nbsp;       &nbsp; - finance

&nbsp;

### loaded\_at\_field (override)

When set at table level, overrides the source group's loaded\_at\_field for this specific table. If left empty, dbt inherits the value from the source group.

&nbsp;

### freshness (override)

When set at table level, overrides the source group's freshness thresholds for this specific table. If left empty, dbt inherits the thresholds from the source group.

&nbsp;

> sources:\
&nbsp; - name: jaffle\_shop\
&nbsp; &nbsp; loaded\_at\_field: \_etl\_loaded\_at\
&nbsp; &nbsp; freshness:\
&nbsp;   &nbsp; warn\_after: {count: 12, period: hour}\
&nbsp;   &nbsp; error\_after: {count: 24, period: hour}\
&nbsp; &nbsp; tables:

> &nbsp;   &nbsp; - name: orders\
&nbsp;     &nbsp; description: One record per order\
&nbsp;     &nbsp; tags:\
&nbsp;       &nbsp; - nightly\
&nbsp;   &nbsp; - name: customers\
&nbsp;     &nbsp; description: One record per customer\
&nbsp;     &nbsp; identifier: raw\_customers\
&nbsp;     &nbsp; loaded\_at\_field: updated\_at\
&nbsp;     &nbsp; freshness:\
&nbsp;       &nbsp; warn\_after: {count: 6, period: hour}\
&nbsp;       &nbsp; error\_after: {count: 12, period: hour}

&nbsp;

## Column names in source tables

Column name: in dbt is simply the physical name of the column. There is no equivalent of identifier: at column level in dbt (this is a *known limitation of dbt-core*, not a Hackolade choice).&nbsp;

&nbsp;

As a result, there is no way to maintain separate business and technical names for columns in the dbt output. Studio exports the technical name if one is defined, otherwise falls back to the (business) name.

&nbsp;

If your columns have both a business name and a technical name in Studio, be aware that only the technical name will appear in the generated sources.yml.

