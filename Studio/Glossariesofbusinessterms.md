# Glossaries of business terms

A glossary is a curated set of business terms that establishes the official vocabulary used across an organization. It ensures that data models rely on consistent, shared terminology, enabling both business and technical stakeholders to interpret them accurately and uniformly.

&nbsp;

In Hackolade Studio, glossaries can be referenced directly within data models. Model objects can be linked to one or more terms from one or multiple glossaries, anchoring each element in an explicit business definition. This linkage clarifies meaning, enforces alignment with business semantics, and promotes consistency across models.

&nbsp;

Downstream, this foundation enables a shared understanding of the semantics, meaning, and context of data structures—both for human stakeholders and for AI systems.

&nbsp;

## Overview

Using glossaries in Hackolade Studio requires an initial step to assign one or more glossaries to your data model to establish which ones are relevant and authoritative for the model -- this step is only required once per model.&nbsp; The glossary assignment is model-specific, as you might assign different glossaries to different models.

&nbsp;

After that initial step, you may bind model objects to one or more business terms from one or more glossary terms from these assigned glossaries to modeling objects.&nbsp; This step should be done once per model object.

&nbsp;

## Assign glossaries to a data model

Before using glossary terms in a data model, you first assign one or several glossaries to that model.

&nbsp;

This assignment defines which glossaries are relevant for the model. As your organization may have multiple glossaries, it is possible that only one or selected glossaries are relevant to a given data model.&nbsp; Once assigned, the glossary terms become available for binding with modeling objects, or for creating new modeling objects based on those terms.

&nbsp;

You can assign multiple glossaries to the same data model. This allows you to work with terms coming from different domains or sources when needed.

&nbsp;

### Glossary file format

A glossary file to be used by Hackolade Studio can be the result of an export from any source.&nbsp; The glossary is an external resource provided as a CSV file. &nbsp;

&nbsp;

A glossary file should contain at least the following columns:

&nbsp;

Term\_ID \| Term \| Description \| Domain

&nbsp;

The column names do not matter (as long as they are unique), nor the order, as a mapping configuration is available for each glossary. &nbsp;

&nbsp;

**Important:**&nbsp; ensure that each glossary term has a unique identifier. This is required for traceability, for maintaining stable references over time, and to close the loop when publishing models back to a metadata management tool from which the glossaries terms originated in the first place.

&nbsp;

The glossary file can reside on your local drive, shared network folder, or preferably in a Git repository so it can be shared across users, so it can be automatically versioned, and so changes can be tracked.&nbsp;

&nbsp;

In the current version, glossaries are expected to be provided as CSV files. Future versions may support direct integrations with external glossary providers.

&nbsp;

### How to assign a glossary

You can assign glossaries from 2 entry points:

* from the menu \_Actions \> Assign Glossary
* from the model-level Properties Pane: click the + button to add a glossary to the model.

&nbsp;

Assigning a glossary is done in 2 steps: select the source file, then define the mapping.

&nbsp;

#### Select source file

Use the dialog to choose a glossary file from your local machine or network drive, or from a Git repository.

&nbsp;

![Business terms glossaries - select source](<lib/Business terms glossaries - select source.png>)

&nbsp;

&nbsp;

Both options are supported, but the choice depends on how your models and glossaries are managed:

* use a **local file** only when you are working on a local clone and the glossary is part of the same repository
* use a **remote repository** when the glossary is stored in another repository or when you are not working on a local clone

&nbsp;

In general, avoid pointing to standalone local files, as they are not reusable by colleagues.&nbsp; Prefer remote sources for shared glossaries, and local files only when they are part of the same cloned repository.

&nbsp;

#### Define the mapping

This step ensures that Studio correctly interprets the file, understanding which columns correspond to identifiers, terms, descriptions, and other attributes.

&nbsp;

Three fields are mandatory and must be mapped:

* identifier (must be unique)
* term
* description

&nbsp;

For each of these, you select the corresponding column from the CSV file. A preview is displayed to help you validate that the correct column has been selected.

&nbsp;

![Business terms glossaries - mapping](<lib/Business terms glossaries - mapping.png>)

&nbsp;

&nbsp;

You can also specify whether the CSV file contains headers. If not, the first row is treated as data, and columns are referenced by their position.

&nbsp;

You can also define additional mappings for other columns. For each additional field, you can:

* specify a field name
* select the corresponding column
* define the value type (single value or multiple values). For multiple values, you must define a separator (for example \`;\`). This is typically used for fields such as synonyms which can contain a list.

&nbsp;

&nbsp;

You can also define how the value is displayed in Studio:

* text
* tag (for example for status fields such as validated or deprecated)

&nbsp;

The preview adapts based on your configuration so you can see how values will be rendered.

&nbsp;

![Business terms glossaries - mapping extended](<lib/Business terms glossaries - mapping extended.png>)

&nbsp;

&nbsp;

Mapping is optional for non-mandatory fields. All columns remain available in Studio even without mapping. In that case, the field name defaults to the CSV column name.

&nbsp;

You can optionally give a name to the glossary, independent from the file name, to make it easier to identify within the model.

&nbsp;

During assignment, validations are performed. In particular, the identifier must be unique across all terms. This is required to ensure traceability and to reliably track terms even if their names change over time.

&nbsp;

Once a glossary is assigned, it is visible in the Properties Pane of the model. From there, you can unassign the glossary using the cross icon, or open it to consult its source. If the glossary is stored in a remote repository, it opens from that remote location. If it is a local CSV file, it opens using the default application associated with CSV files on your system.

&nbsp;

![Business terms glossaries - assignment list](<lib/Business terms glossaries - assignment list.png>)

&nbsp;

&nbsp;

## Use glossary terms in a data model

After assigning glossaries, you can use glossary terms in 2 ways:

* bind an existing modeling object to a glossary term
* create a new modeling object from a glossary term

&nbsp;

### Bind term to existing modeling object

You can bind glossary terms to any existing modeling object, including containers, entities, views, relationships, and attributes.

&nbsp;

Binding is done from the Properties pane, using the \_Glossary terms\_ property. This property supports multiple values, meaning a modeling object can be bound to several glossary terms.

&nbsp;

Click the + button to open the glossary browser.

&nbsp;

![Business terms glossaries - bind term](<lib/Business terms glossaries - bind term.png>)

&nbsp;

&nbsp;

#### Browse and select terms

The glossary browser displays all terms from the glossaries assigned to the model.

* on the left, you can filter by glossary. By default, \_All\_ is selected.
* in the center, glossary terms are displayed in a configurable grid.

&nbsp;

Each time the glossary browser is opened, the glossary sources are accessed to reflect the most recent available data, whether from a local file or a remote repository.

&nbsp;

&nbsp;

![Business terms glossaries - select term](<lib/Business terms glossaries - select term.png>)

&nbsp;

&nbsp;

The grid is customizable:

* reorder columns using drag and drop
* sort by any column
* hide or show columns

&nbsp;

A filter bar allows you to filter terms as you type, dynamically updating the grid.

* by default, search is applied to the \_term\_ field
* you can extend the search scope to other fields if needed

&nbsp;

Each column also provides its own filter, accessible from the column header.

&nbsp;

![Business terms glossaries - term list filters](<lib/Business terms glossaries - term list filters.png>)

&nbsp;

The grid is a master-detail view:

* the main grid shows the columns you configured
* select a row to open a panel on the right displaying all available information for the selected term

&nbsp;

![Business terms glossaries - term details](<lib/Business terms glossaries - term details.png>)

&nbsp;

#### Bind terms

Select one or more terms using checkboxes, then click \_Apply\_ to bind them to the modeling object.\&#x20;

&nbsp;

![Business terms glossaries - term selected](<lib/Business terms glossaries - term selected.png>)

&nbsp;

&nbsp;

The selected terms appear in the \_Glossary terms\_ property in the Properties pane, where you can unbind terms one by one using the cross icon next to each term, add more terms by clicking the \*\*+\*\* button again, or access full details for a term using the three-dot icon.

&nbsp;

![Business terms glossaries - bound term](<lib/Business terms glossaries - bound term.png>)

&nbsp;

Press the 3 dots ... next to the term to display the term details

&nbsp;

![Business terms glossaries - consult term](<lib/Business terms glossaries - consult term.png>)

&nbsp;

### Create modeling objects from glossary terms

You can also create new modeling objects directly from glossary terms.

&nbsp;

From the context menu, each creation action (such as adding a container, entity, relationship, view, or attribute) provides a **Pick from glossary** option.

&nbsp;

![Business terms glossaries - pick term](<lib/Business terms glossaries - pick term.png>)

&nbsp;

Select this option to open the same glossary browser described earlier, allowing you to browse, filter, and select one or more terms.

&nbsp;

After you click the **Apply** button, the modeling object is created and automatically bound to the selected glossary term(s). The business name of the object is initialized using the selected glossary term instead of a default name such as "New entity" or "New attribute".

&nbsp;

If multiple terms are selected, a single modeling object is created, and the business name is constructed by concatenating the selected terms in the order of selection.

&nbsp;

![Business terms glossaries - multi-term select](<lib/Business terms glossaries - multi-term select.png>)

&nbsp;

&nbsp;

![Business terms glossaries - multi-term list](<lib/Business terms glossaries - multi-term list.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

