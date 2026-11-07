---
description: Generate customizable HTML, PDF or Markdown documentation and diagram pictures for your Hackolade Studio data models.
seoTitle: Generate data model documentation
image: lib/Documentation - Object selection.png
---
# Generate documentation

Model documentation is an important output of data modeling. Models are enriched with descriptions, comments, constraints to be consulted by application stakeholders.

Hackolade Studio easily produces a customizable report, and allows also to output just the diagrams.

This feature is also available via the [Command-Line Interface](CommandLineInterface.md).

![Menu File Generate Documentation](<lib/Menu File Generate Documentation.png>)\
Currently the following formats are available:

- PDF for all editions
- Markdown for the Pro editions (free 14-trial and paid)
- HTML for the Pro editions (free 14-trial and paid)

In general, PDF should only be used for smaller models, as the number of pages can quickly grow beyond a manageable number of pages. For medium-size models, the HTML option is great because it produces one single HTML file including all assets and pictures. The HTML file can easily be sent via email or placed on a corporate portal. For large models, it is advised to use the Markdown option where the images are produced in a sub-folder, and the Markdown file only has text content formatted in Markdown syntax.

The Markdown format is particularly useful for publishing in Git repositories, but also for customization of layout. There are many free tools available in different languages, for example [Docsify-This](<https://docsify-this.net/#/> "target=\"_blank\"") or [MKDocs](<https://www.mkdocs.org/> "target=\"_blank\""). See [this example](<https://docsify-this.net/?basePath=https://raw.githubusercontent.com/hackolade/HCK-docs-markdown/e73d25c0fec59e7e2c21ee906f8a6d34071e03e7/Yelp&homepage=Yelp%20Challenge%20dataset%20documentation.md&sidebar=true#/> "target=\"_blank\"").

Documentation can be configured using 2 sets of controls:

## Parameters in Tools > Options > Documentation

Users may control the different sections to include in the documentation:

![Documentation options](<lib/Documentation options.png>)\
and select a company logo to appear at the top of the reports.

As documentation generation can be lengthy, they can set a time limit. A custom logo can also be selected:\
![Tools - Options - Doc2](<lib/Tools - Options - Doc2.png>)

When you generate documentation, it is first saved to the file system, and it will open automatically. The file contains:\
1\. Model\
a. Entity Relationship diagram\
b. properties\
2\. For each container

```text
a. hierarchical schema view
b. properties
c. fields, and for each field:
```

1\. sub-tree diagram\
2\. properties\
3\. For each relationship

```text
a. relationship diagram
b. properties
```

## Object selection in File > Generate Documentation

Before generation of the documentation, you're given the opportunity to filter objects and select only the desired ones:

![Documentation - Object selection](<lib/Documentation - Object selection.png>)

You may generate the diagrams with business names or technical names by choosing the corresponding option in the dropdown box.

## Known issue on Linux Debian when generating the documentation as PDF

If you get a "write EPIPE" error:

```json
"stack": "Error: write EPIPE\n    at WriteWrap.onWriteComplete [as oncomplete] (internal/stream_base_commons.js:83:16)",
```

It may be due to an open issue documented [here](<https://github.com/wch/webshot/issues/90> "target=\"_blank\"") and [here](<https://github.com/marcbachmann/node-html-pdf/issues/531> "target=\"_blank\"").

As a workaround, you should execute the following command:

```bash
export OPENSSL_CONF=/etc/ssl/
```

which will allow the generation of documentation as PDF.
