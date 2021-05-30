# Print a diagram

You may wish to print just the Entity Relationship diagram or hierarchical schema views, possibly on A3 or Tabloid format.

&nbsp;

To do so, choose the menu option File \> Print Diagram

![Image](<lib/File%20menu%20-%20Print%20Diagram.png>)

&nbsp;

Users may wish to create pictures for different diagrams created with the application.&nbsp; They can be generated in either PDF or PNG format, and for different paper layouts.

![Image](<lib/File%20-%20Print%20Daigram.png>)

With the controls just below the picture, the user may zoom in, zoom out, or fit the diagram to the page.

&nbsp;

&nbsp;

## Known issue on Linux Debian when generating the images in PDF format

If you get a "write EPIPE" error:

>  "stack": "Error: write EPIPE\\n    at WriteWrap.onWriteComplete \[as oncomplete\] (internal/stream\_base\_commons.js:83:16)",

> &nbsp;

It may be due to an open issue documented [here](<https://github.com/wch/webshot/issues/90> "target=\"\_blank\"") and [here](<https://github.com/marcbachmann/node-html-pdf/issues/531> "target=\"\_blank\"").

&nbsp;

As a workaround, you should execute the following command:

> export OPENSSL\_CONF=/etc/ssl/

&nbsp;

which will allow the generation of images in PDF format.

&nbsp;

