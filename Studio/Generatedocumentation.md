# Generate documentation

Model documentation is an important output of data modeling.&nbsp; Models are enriched with descriptions, comments, constraints to be consulted by application stakeholders.

&nbsp;

Hackolade Studio easily produces a customizable report, and allows also to output just the diagrams.

&nbsp;

This feature is also available via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Menu File Generate Documentation](<lib/Menu File Generate Documentation.png>)

Currently the following formats are available:

\- PDF for all editions

\- Markdown for the Pro editions (free 14-trial and paid)

\- HTML for the Pro editions (free 14-trial and paid)

&nbsp;

In general, PDF should only be used for smaller models, as the number of pages can quickly grow beyond a manageable number of pages.&nbsp; For medium-size models, the HTML option is great because it produces one single HTML file including all assets and pictures.&nbsp; The HTML file can easily be sent via email or placed on a corporate portal.&nbsp; For large models, it is advised to use the Markdown option where the images are produced in a sub-folder, and the Markdown file only has text content formatted in Markdown syntax.

&nbsp;

The Markdown format is particularly useful for publishing in Git repositories, but also for customization of layout.&nbsp; There are many free tools available in different languages, for example [Docsify-This](<https://docsify-this.net/#/> "target=\"\_blank\"") or [MKDocs](<https://www.mkdocs.org/> "target=\"\_blank\"").&nbsp; See [this example](<https://docsify-this.net/?basePath=https://raw.githubusercontent.com/hackolade/HCK-docs-markdown/e73d25c0fec59e7e2c21ee906f8a6d34071e03e7/Yelp\&homepage=Yelp%20Challenge%20dataset%20documentation.md\&sidebar=true#/> "target=\"\_blank\"").

&nbsp;

Documentation can be configured using 2 sets of controls:

&nbsp;

## Parameters in Tools \> Options \> Documentation

Users may control the different sections to include in the documentation:

&nbsp;

![Documentation options](<lib/Documentation options.png>)

and select a company logo to appear at the top of the reports.

&nbsp;

As documentation generation can be lengthy, they can set a time limit.&nbsp; A custom logo can also be selected:

![Tools - Options - Doc2](<lib/Tools - Options - Doc2.png>)

&nbsp;

When you generate documentation, it is first saved to the file system, and it will open automatically.&nbsp; The file contains:

&#49;. Model&nbsp;

a. Entity Relationship diagram

b. properties

&#50;. For each container

&nbsp; &nbsp; a. hierarchical schema view

&nbsp; &nbsp; b. properties

&nbsp; &nbsp; c. fields, and for each field:

&nbsp; &nbsp; &nbsp; &nbsp; 1. sub-tree diagram

&nbsp; &nbsp; &nbsp; &nbsp; 2. properties

&#51;. For each relationship

&nbsp; &nbsp; a. relationship diagram

&nbsp; &nbsp; b. properties

&nbsp;

## Object selection in File \> Generate Documentation

Before generation of the documentation, you're given the opportunity to filter objects and select only the desired ones:

&nbsp;

![Documentation - Object selection](<lib/Documentation - Object selection.png>)

&nbsp;

You may generate the diagrams with business names or technical names by choosing the corresponding option in the dropdown box.

&nbsp;

&nbsp;

## Known issue on Linux Debian when generating the documentation as PDF

If you get a "write EPIPE" error:

>  "stack": "Error: write EPIPE\\n    at WriteWrap.onWriteComplete \[as oncomplete\] (internal/stream\_base\_commons.js:83:16)",

&nbsp;

It may be due to an open issue documented [here](<https://github.com/wch/webshot/issues/90> "target=\"\_blank\"") and [here](<https://github.com/marcbachmann/node-html-pdf/issues/531> "target=\"\_blank\"").

&nbsp;

As a workaround, you should execute the following command:

> export OPENSSL\_CONF=/etc/ssl/

&nbsp;

which will allow the generation of documentation as PDF.

