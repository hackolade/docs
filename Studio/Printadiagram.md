# Print a diagram

You may wish to print just the Entity Relationship diagram or hierarchical schema views, possibly on A3 or Tabloid format.

&nbsp;

In terms of image quality, PDF is well known for it poor resolution when zooming in on large images.  The technical solution we provide to work around this limitation is the option to select the vector format SVG.  In between these 2 format qualities, we have the PNG format which is better than PDF, but not scalable like SVG format.   

&nbsp;

To print a diagram, choose the menu option File \> Print Diagram

![File menu - Print Diagram](<lib/File menu - Print Diagram.png>)

&nbsp;

Users may wish to create pictures for different diagrams created with the application.&nbsp; They can be generated in either PDF, PNG, or SVG format, and for different paper layouts.

&nbsp;

![File - Print Diagram](<lib/File - Print Diagram.png>)

&nbsp;

With the controls just below the picture, the user may zoom in, zoom out, fit the diagram to the page, or toggle between business names and technical names

&nbsp;

&nbsp;

## Known issue on Linux Debian when generating the images in PDF format

If you get a "write EPIPE" error:

>  "stack": "Error: write EPIPE\\n    at WriteWrap.onWriteComplete \[as oncomplete\] (internal/stream\_base\_commons.js:83:16)",

&nbsp;

It may be due to an open issue documented [here](<https://github.com/wch/webshot/issues/90> "target=\"\_blank\"") and [here](<https://github.com/marcbachmann/node-html-pdf/issues/531> "target=\"\_blank\"").

&nbsp;

As a workaround, you should execute the following command:

> export OPENSSL\_CONF=/etc/ssl/

&nbsp;

which will allow the generation of images in PDF format.

&nbsp;

