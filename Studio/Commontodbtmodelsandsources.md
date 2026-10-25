# Common to dbt models and sources

## Data tests

dbt [data tests](<https://docs.getdbt.com/docs/build/data-tests> "target=\"_blank\"") are validation rules that run against your data to check quality and integrity. They are declared in the property file alongside the model or source and executed with the dbt test command.

&nbsp;

Hackolade Studio generates data tests in two ways: automatically from constraints already defined in your model, and manually via free-text entries in the dbt tab at column level. Both approaches work for models and sources.

&nbsp;

### Auto-generated tests from constraints

When forward-engineering, check the **Generate data tests** from constraints option in the dialog to let Studio produce dbt data tests automatically from the constraints defined in your model. No extra configuration is needed in the properties pane, Studio reads what is already there.

&nbsp;

The following mapping is applied:

&nbsp;

<table>
<thead>
<tr>
<th>Hackolade constraint</th>
<th>Generated dbt data test</th>
</tr>
</thead>
<tbody>
<tr>
<td>Primary key</td>
<td><code>not_null</code> + <code>unique</code></td>
</tr>
<tr>
<td>Not null / required</td>
<td><pre><code class="language-text">not_null</code></pre></td>
</tr>
<tr>
<td>Unique (non primary key)</td>
<td><pre><code class="language-text">unique</code></pre></td>
</tr>
<tr>
<td>Enum values</td>
<td><code>accepted_values</code> with the list of allowed values</td>
</tr>
<tr>
<td>Foreign key</td>
<td><code>relationships</code> with the referenced model and column</td>
</tr>
</tbody>
</table>

&nbsp;

Tests are placed at column level in the generated YAML, which is the [recommended style](<https://docs.getdbt.com/docs/build/data-tests#column-level-data-tests> "target=\"_blank\"") in dbt. Studio uses the `data_tests:` syntax introduced in dbt v1.8 and the `arguments:` syntax for tests with parameters (dbt v1.10.5+).

&nbsp;

```yaml
models:
  - name: orders
    columns:
      - name: order_id
        data_tests:
          - not_null
          - unique
      - name: status
        data_tests:
          - accepted_values:
              arguments:
                values: [placed, shipped, completed, returned]
      - name: customer_id
        data_tests:
          - relationships:
              arguments:
                to: ref('customers')
                field: customer_id
```

&nbsp;

### Global test options

When Generate data tests from constraints is enabled, 3 optional settings appear in the forward-engineering dialog and applied uniformly to all generated tests:

- Severity (warn or error): Controls whether a test failure blocks the run or only raises a warning.
- Store failures: when enabled, dbt stores the rows that failed the test in a table for inspection.
- Limit: limits the number of failing rows stored (only relevant when store failures is enabled).

&nbsp;

```yaml
columns:
  - name: order_id
    data_tests:
      - not_null:
          severity: warn
          store_failures: true
          limit: 50
```

&nbsp;

### Additional tests

For tests that go beyond the 4 built-in dbt tests, such as tests from packages like [dbt-utils](<https://hub.getdbt.com/dbt-labs/dbt_utils/latest/> "target=\"_blank\"") or custom macros, you can add free-text YAML fragments directly in the dbt tab at column level.

&nbsp;

Each additional test is added via the + button in the dbt tab. Studio validates that each entry is well-formed YAML, but does not verify that it is a valid dbt test.

&nbsp;

Ensuring the fragment makes sense in context remains your responsibility. Entries are appended to the column's data_tests: list after any auto-generated tests.

&nbsp;

> [!NOTE]
> Make sure any referenced tests or packages are available in your dbt project.

&nbsp;

![dbt tests](<lib/dbt tests.png>)\
​

&nbsp;

```yaml
columns:
  - name: email
    data_tests:
      - not_null
      - dbt_utils.expression_is_true:
          expression: "email like '%@%'"
```

&nbsp;

> [!NOTE]
> There is no distinction between package tests and custom macros at this stage: both are entered as free-text in the same field.

&nbsp;

## Custom headers and footers

For cases where the generated YAML is not enough on its own, Hackolade Studio lets you inject free-text YAML content before and after the generated output, at container level and at entity level.

&nbsp;

This is useful for adding dbt configuration blocks, comments, or any valid YAML that Studio does not generate natively.

&nbsp;

> [!NOTE]
> Hackolade Studio validates that the injected content is well-formed YAML. However, it does not verify that the content is semantically valid for dbt. Ensuring the injected YAML makes sense in context remains your responsibility.

&nbsp;

### Where to define them

Headers and footers are defined in the dbt tab of the properties pane:

- Container level: available for all containers, whether they are source groups or dbt-model containers
- Entity level: available for entities that belong to a model container (not source groups)

&nbsp;

### Output order

When forward-engineering, content is assembled in the following order:

&nbsp;

```text
container header
  entity header
  generated content  entity footer
container footer
```

&nbsp;

**Note;** Entity-level headers and footers are ignored when generating one file per schema rather than one file per entity.

&nbsp;

### Example

The most common use case for a container-level header is adding additional dbt resource declarations, such as `exposures:` or metrics: , in the same file as the generated models or sources. A `models.yml` file can contain multiple dbt resource types alongside the generated content.

&nbsp;

```yaml
exposures:
  - name: weekly_finance_report
    type: dashboard
    owner:
      email: finance@company.com
    depends_on:
      - ref('orders')

version: 2
models:
  - name: orders
    description: One record per order
    columns:
      ...
```

&nbsp;

For an entity-level header (only applicable in one-file-per-entity mode), a typical use case is adding a YAML comment block for documentation or governance purposes, before the entity definition:

&nbsp;

```yaml
# Owner: finance-team
# Refresh: nightly
# SLA: data available by 06:00 UTC
version: 2
models:
  - name: orders
    description: One record per order
    columns:
      ...
```
