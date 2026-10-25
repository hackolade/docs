# DocumentDB script

DocumentDB does not provide an abstraction for schemas. In order to provide added-value in forward-engineering, Hackolade provides a JSON document by example for each collection in the model. The script also includes the creation of collection and indexes, and it can be applied to the DocumentDB instance.

&nbsp;

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

&nbsp;

![DocumentDB forward-engineering](<lib/DocumentDB forward-engineering.png>)

&nbsp;

A button lets the user apply to a selected instance the script to create databases, collections with indexes as well as sample data if desired.
