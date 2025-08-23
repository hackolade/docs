# Print a diagram

You may wish to print just the Entity Relationship diagram or hierarchical schema views, possibly on A3 or Tabloid format.&nbsp; Note that the application does not actually interact with your printer.&nbsp; Instead it generates files (PDF, Hi-Res PDF, PNG, or SVG) which can then be opened with the corresponding application of your choice for viewing or actual printing with the print options provided by that application.&nbsp; Or the image can be posted on&nbsp;

&nbsp;

And if you want to tailor what appears in these files, you may create [Diagram Views (ERDVs)](<DiagramViews.md>) with your choice of entities and display options, which is very useful for data modeling "story telling".

&nbsp;

In terms of image quality, PDF is well known for it poor resolution when zooming in on large images.  The technical solution we provide to work around this limitation is the option to select the vector format SVG.  In between these 2 format qualities, there us the PNG format which is better than PDF, but not scalable like SVG format.   

Starting with v8.3.4, it is possible to create Hi-Resolution PDF image which is drawn from the SVG.&nbsp; Because of the high resolution, the generation of the image takes quite a bit longer than the default PDF image.

&nbsp;

The difference between PNG and SVG is that PNG is a raster format with compression, whereas SVG  is a vector format.  Both have their pros and cons: PNG being compressed has a smaller footprint, but as a result, with larger images, you lose in resolution.  SVG on the other hand takes much more space, but can scale infinitely.

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

