# Common to dbt models and sources

## Data tests

dbt [data tests](<https://docs.getdbt.com/docs/build/data-tests> "target=\"\_blank\"") are validation rules that run against your data to check quality and integrity. They are declared in the property file alongside the model or source and executed with the dbt test command.

&nbsp;

Hackolade Studio generates data tests in two ways: automatically from constraints already defined in your model, and manually via free-text entries in the dbt tab at column level. Both approaches work for models and sources.

&nbsp;

### Auto-generated tests from constraints

When forward-engineering, check the **Generate data tests** from constraints option in the dialog to let Studio produce dbt data tests automatically from the constraints defined in your model. No extra configuration is needed in the properties pane, Studio reads what is already there.

&nbsp;

The following mapping is applied:

| **Hackolade constraint** | **Generated dbt data test** |
| --- | --- |
| Primary key | not\_null + unique |
| Not null / required | not\_null |
| Unique (non primary key) | unique |
| Enum values | accepted\_values with the list of allowed values |
| Foreign key | relationships with the referenced model and column |


&nbsp;

Tests are placed at column level in the generated YAML, which is the [recommended style](<https://docs.getdbt.com/docs/build/data-tests#column-level-data-tests> "target=\"\_blank\"") in dbt. Studio uses the data\_tests: syntax introduced in dbt v1.8 and the arguments: syntax for tests with parameters (dbt v1.10.5+).

&nbsp;

> models:\
&nbsp; - name: orders\
&nbsp; &nbsp; columns:\
&nbsp;   &nbsp; - name: order\_id\
&nbsp;     &nbsp; data\_tests:\
&nbsp;       &nbsp; - not\_null\
&nbsp;       &nbsp; - unique\
&nbsp;   &nbsp; - name: status\
&nbsp;     &nbsp; data\_tests:\
&nbsp;       &nbsp; - accepted\_values:\
&nbsp;           &nbsp; arguments:\
&nbsp;             &nbsp; values: \[placed, shipped, completed, returned\]\
&nbsp;   &nbsp; - name: customer\_id\
&nbsp;     &nbsp; data\_tests:\
&nbsp;       &nbsp; - relationships:\
&nbsp;           &nbsp; arguments:\
&nbsp;             &nbsp; to: ref('customers')\
&nbsp;             &nbsp; field: customer\_id

&nbsp;

### Global test options

When Generate data tests from constraints is enabled, 3 optional settings appear in the forward-engineering dialog and applied uniformly to all generated tests:

* Severity (warn or error): Controls whether a test failure blocks the run or only raises a warning.
* Store failures: when enabled, dbt stores the rows that failed the test in a table for inspection.
* Limit: limits the number of failing rows stored (only relevant when store failures is enabled).

&nbsp;

&nbsp;

> columns:\
&nbsp; - name: order\_id\
&nbsp; &nbsp; data\_tests:\
&nbsp;   &nbsp; - not\_null:\
&nbsp;       &nbsp; severity: warn\
&nbsp;       &nbsp; store\_failures: true\
&nbsp;       &nbsp; limit: 50

&nbsp;

### Additional tests

For tests that go beyond the 4 built-in dbt tests, such as tests from packages like [dbt-utils](<https://hub.getdbt.com/dbt-labs/dbt\_utils/latest/> "target=\"\_blank\"") or custom macros, you can add free-text YAML fragments directly in the dbt tab at column level.

&nbsp;

Each additional test is added via the + button in the dbt tab. Studio validates that each entry is well-formed YAML, but does not verify that it is a valid dbt test.&nbsp;

&nbsp;

Ensuring the fragment makes sense in context remains your responsibility. Entries are appended to the column's data\_tests: list after any auto-generated tests.

&nbsp;

**Note**: make sure any referenced tests or packages are available in your dbt project.

&nbsp;

![Image](<lib/dbt tests.png>)

​

> columns:\
&nbsp; - name: email\
&nbsp; &nbsp; data\_tests:\
&nbsp;   &nbsp; - not\_null\
&nbsp;   &nbsp; - dbt\_utils.expression\_is\_true:\
&nbsp;       &nbsp; expression: "email like '%@%'"

**Note:** there is no distinction between package tests and custom macros at this stage: both are entered as free-text in the same field.

## Custom headers and footers

For cases where the generated YAML is not enough on its own, Hackolade Studio lets you inject free-text YAML content before and after the generated output, at container level and at entity level.

&nbsp;

This is useful for adding dbt configuration blocks, comments, or any valid YAML that Studio does not generate natively.

&nbsp;

**Note:** Hackolade Studio validates that the injected content is well-formed YAML. However, it does not verify that the content is semantically valid for dbt. Ensuring the injected YAML makes sense in context remains your responsibility.

&nbsp;

### Where to define them

Headers and footers are defined in the dbt tab of the properties pane:

* Container level: available for all containers, whether they are source groups or dbt-model containers
* Entity level: available for entities that belong to a model container (not source groups)

&nbsp;

### Output order

When forward-engineering, content is assembled in the following order:

> container header\
&nbsp; entity header\
&nbsp; generated content&nbsp; entity footer\
container footer

**Note;** Entity-level headers and footers are ignored when generating one file per schema rather than one file per entity.

&nbsp;

### Example

The most common use case for a container-level header is adding additional dbt resource declarations, such as exposures: or metrics: , in the same file as the generated models or sources. A models.yml file can contain multiple dbt resource types alongside the generated content.

&nbsp;

> exposures:\
&nbsp; - name: weekly\_finance\_report\
&nbsp; &nbsp; type: dashboard\
&nbsp; &nbsp; owner:\
&nbsp;   &nbsp; email: finance@company.com\
&nbsp; &nbsp; depends\_on:\
&nbsp;   &nbsp; - ref('orders')\
\
\
version: 2\
models:\
&nbsp; - name: orders\
&nbsp; &nbsp; description: One record per order\
&nbsp; &nbsp; columns:\
&nbsp;   &nbsp; ...

&nbsp;

For an entity-level header (only applicable in one-file-per-entity mode), a typical use case is adding a YAML comment block for documentation or governance purposes, before the entity definition:

&nbsp;

> \# Owner: finance-team\
\# Refresh: nightly\
\# SLA: data available by 06:00 UTC\
version: 2\
models:\
&nbsp; - name: orders\
&nbsp; &nbsp; description: One record per order\
&nbsp; &nbsp; columns:\
&nbsp;   &nbsp; ...

&nbsp;

&nbsp;

