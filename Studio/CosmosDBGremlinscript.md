---
description: Hackolade Studio generates the Gremlin script for vertex and edge labels of a Cosmos DB Gremlin model, to export or apply to an instance.
seoTitle: Generate Cosmos DB Gremlin scripts
image: lib/CosmosDB Gremlin script forward-engineering.png
---
# Cosmos DB Gremlin script

As you develop the model for your Cosmos DB Gremlin graph database, with vertex labels and edge labels, Hackolade dynamically generates the corresponding Gremlin script.

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

The information can be viewed in the Gremlin script tab:\
![CosmosDB Gremlin script forward-engineering](<lib/CosmosDB Gremlin script forward-engineering.png>)

A button lets the user apply to a selected Azure instance the script to create graphs, nodes and edges, indexes, UDFs, stored procedures, and triggers

Or you may apply these scripts to a Gremlin directly to the selected instance with the menu option Tools > Forward-Engineering > Gremlin script:\
![Cosmos DB Gremlin forward-engineering menu](<lib/Cosmos DB Gremlin forward-engineering menu.png>)
