# MongoDB scripts

As you develop the model for your MongoDB collection or views, with field-level constraints and indexes, Hackolade dynamically generates corresponding scripts:

* [db.createCollection()](<https://docs.mongodb.com/manual/reference/method/db.createCollection/> "target=\"\_blank\"") with validator script
* [db.collection.createIndex()](<https://docs.mongodb.com/manual/reference/method/db.collection.createIndex/> "target=\"\_blank\"")
* [db.createView()](<https://docs.mongodb.com/manual/reference/method/db.createView/> "target=\"\_blank\"")
* [sh.shardCollection()](<https://docs.mongodb.com/manual/reference/method/sh.shardCollection/> "target=\"\_blank\"")

&nbsp;

The information can be viewed in the MongoDB Script tab:

![Image](<lib/Forward-Engineering%20-%20MongoDB%20Script.png>)

&nbsp;

&nbsp;

You may toggle between Create and Update views:

![Image](<lib/MongoDB%20script%20toggle.png>)

&nbsp;

A button lets the user apply to a selected instance the script to create databases, collections with optional $jsonschema validator, indexes, and sharding configuration, and sample data if desired.

&nbsp;

For version of MongoDB up to v3.4, the MongoDB script is in [aggregation pipeline syntax](<https://docs.mongodb.com/v3.2/core/document-validation/> "target=\"\_blank\"").&nbsp; From v3.6 up, the script is in [$jsonschema syntax](<https://docs.mongodb.com/manual/core/schema-validation/> "target=\"\_blank\"").

&nbsp;

You may export these scripts to a JavaScript file with the menu option Tools \> Forward-Engineering \> MongoDB Script:

![Image](<lib/Forward-Engineering%20-%20MongoDB%20Script%20file.png>)

&nbsp;

The generation of the script can also be triggered with [Command-Line Interface](<CommandLineInterface.md>).

