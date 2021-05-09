# Generate documentation

Model documentation is an important output of data modeling.&nbsp; Models are enriched with descriptions, comments, constraints to be consulted by application stakeholders.

&nbsp;

Hackolade easily produces a customizable report, and allows also to output just the diagrams.

&nbsp;

This feature is also available via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Image](<lib/Menu%20File%20Generate%20Documentation.png>)

Currently the following formats are available:

\- PDF for all editions

\- Markdown for the Pro editions (free 14-trial and paid)

\- HTML for the Pro editions (free 14-trial and paid)

&nbsp;

Documentation can be configured using 2 sets of controls:

&nbsp;

### &#49;) Parameters in Tools \> Options \> Documentation ###

Users may control the different sections to include in the documentation:

&nbsp;

![Image](<lib/Documentation%20options.png>)

and select a company logo to appear at the top of the reports.

&nbsp;

As documentation generation can be lengthy, they can set a time limit.&nbsp; A custom logo can also be selected:

![Image](<lib/Tools%20-%20Options%20-%20Doc2.png>)

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

### &#50;) Object selection in File \> Generate Documentation ###

Before generation of the documentation, you're given the opportunity to filter objects and select only the desired ones:

![Image](<lib/Documentation%20-%20Object%20selection.png>)

&nbsp;

&nbsp;

## Known issue on Linux Debian when generating the documentation as PDF ##

If you get a "write EPIPE" error:

>  "stack": "Error: write EPIPE\\n    at WriteWrap.onWriteComplete \[as oncomplete\] (internal/stream\_base\_commons.js:83:16)",

> &nbsp;

It may be due to an open issue documented [here](<https://github.com/wch/webshot/issues/90> "target=\"\_blank\"") and [here](<https://github.com/marcbachmann/node-html-pdf/issues/531> "target=\"\_blank\"").

&nbsp;

As a workaround, you should execute the following command:

> export OPENSSL\_CONF=/etc/ssl/

&nbsp;

which will allow the generation of documentation as PDF.


***
_Created with the Personal Edition of HelpNDoc: [Easy CHM and documentation editor](<https://www.helpndoc.com>)_
