# Generate documentation and pictures

In the previous tutorial, we reviewed how to export or forward-engineer artifacts from your data model.&nbsp; By the end of this tutorial, you will have learned how to generate documentation and pictures for your data model.

&nbsp;

You may also [view this tutorial](<https://youtu.be/11hK9WH773c> "target=\"\_blank\"") on YouTube.&nbsp; Summary slides can be found [here](<https://www.slideshare.net/PascalDesmarets1/hackolade-tutorial-part-10-generate-documentation-and-picturespdf> "target=\"\_blank\"").

&nbsp;

Arguably, documentation and pictures of diagrams are also artifacts.&nbsp; The difference is that forward-engineered artifacts are generally "consumable" by machines, whereas documentation and pictures are clearly for humans.&nbsp; Admittedly, the nuance is subtle and non-exclusive, and the separation in the menu is historical...

## Generate documentation

Documentation for your data models can be generated in 3 formats: HTML, Markdown, and PDF.&nbsp; Their content is identical, but the structure differs:

* HTML documentation is packaged in a single file encapsulating all content.&nbsp; This way, it can be easily moved around, emailed, or posted on on corporate portal.&nbsp; It can also be read via scripts and joined with an integration of the raw data model file (as saved on disk) to feed a homegrown data dictionary.
* Markdown documentation is particularly handy if you plan to post it on GitHub or other repository operators.&nbsp; While the main markdown file is unique per documentation generation, a major difference with HTML and PDF, is that pictures are extracted and placed in a subdirectory bearing the same name as the documentation file.&nbsp; Note also, that it is easy to render Markdown documentation with [custom web site generators](<https://jamstack.org/generators/> "target=\"\_blank\"").
* PDF documentation is also a single file, but with less flexibility and navigation capabilities than the HTML file.

&nbsp;

Documentation can quickly grow to a very large size, so it is recommended to use the following controls to adjust it to your needs:

### Parameters&nbsp;

Parameters are maintained in Tools \> Options \> Documentation to select the segments and behavior.&nbsp; .

![Tools - Options - Documentation](<lib/Tools - Options - Documentation.png>)

### Selection

Each time you generate documentation for a data model, you will be prompted to select the the objects of the data models that you wish to be included:

![Generate documentation - object selection](<lib/Generate documentation - object selection.png>)

You may deselect groups of objects or individual objects.

&nbsp;

Documentation generation is accessible either from the GUI application, or from the [Command-Line Interface](<CommandLineInterface.md>), whether directly or running in [Docker containers](<https://github.com/hackolade/docker/tree/main/Studio> "target=\"\_blank\"").

&nbsp;

## Print diagrams

You may want to generate PNG or PDF files for your Entity-Relationship Diagrams or hierarchical schema views.&nbsp; There are many choices for configuration:

\- type of diagram: the entire mdeol ERD, separate ER diagram views, individual entities, or read-only views if any;

\- paper size: either A paper (A0 through A4) or US (letter, tabloid, or ledger)

\- layout: portrait or landscape

\- pages: if the picture spans multiple pages, you may select the page numbers to be included in the output

\- header and footer: you may add text to appear at the top and bottom of the diagrams

\- zoom in or out: using these buttons affects the number of pages

\- fit to page: the output will be automatically zoomed in or out to fit on a single page of the selected size and layout

\- business or technical names: if naming conventions are enabled

&nbsp;

![Tutorial - Print diagram](<lib/Tutorial - Print diagram.png>)

&nbsp;

In this tutorial, we reviewed how to generate documentation and pictures for your data model.&nbsp; In the next tutorial, we will cover how to master data models for property graph databases.

