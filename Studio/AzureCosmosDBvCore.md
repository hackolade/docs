# Azure Cosmos DB vCore

You may also leverage the MongoDB target to model [Azure Cosmos DB for MongoDB vCore](<https://devblogs.microsoft.com/cosmosdb/mongovcorega/> "target=\"\_blank\""). &nbsp;

&nbsp;

To connect to your instance of Cosmos DB with MongoDB vCore compatibility, the simplest is to use the mongodb+srv connection string available from the azure portal at&nbsp;

&nbsp;

![Azure CosmosDB vCore - connection string](<lib/Azure CosmosDB vCore - connection string.png>)

&nbsp;

&nbsp;

&nbsp;

where \<user\> and \<password\> are replaced by the appropriate values.

&nbsp;

When you create a connection setting, click on the button "From SRV or URI" button:

![Azure CosmosDB vCore - mongodb srv button](<lib/Azure CosmosDB vCore - mongodb srv button.png>)

&nbsp;

Then paste the mongodb+srv string:

&nbsp;

![Azure CosmosDB vCore - mongodb srv string](<lib/Azure CosmosDB vCore - mongodb srv string.png>)

&nbsp;

This will parse the mongodb+srv string, and populate the necessary fields.&nbsp; Save the entry and you should be able to connect to your instance.

&nbsp;

