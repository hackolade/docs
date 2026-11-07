---
description: Connect Hackolade Studio to Azure Cosmos DB for MongoDB vCore with the mongodb+srv connection string from the Azure portal.
seoTitle: Connect to Azure Cosmos DB for MongoDB vCore
image: lib/Azure CosmosDB vCore - connection string.png
---
# Azure Cosmos DB vCore

You may also leverage the MongoDB target to model [Azure Cosmos DB for MongoDB vCore](<https://devblogs.microsoft.com/cosmosdb/mongovcorega/> "target=\"_blank\"").

To connect to your instance of Cosmos DB with MongoDB vCore compatibility, the simplest is to use the mongodb+srv connection string available from the azure portal at

![Azure CosmosDB vCore - connection string](<lib/Azure CosmosDB vCore - connection string.png>)

where \<user> and \<password> are replaced by the appropriate values.

When you create a connection setting, click on the button "From SRV or URI" button:\
![Azure CosmosDB vCore - mongodb srv button](<lib/Azure CosmosDB vCore - mongodb srv button.png>)

Then paste the mongodb+srv string:

![Azure CosmosDB vCore - mongodb srv string](<lib/Azure CosmosDB vCore - mongodb srv string.png>)

This will parse the mongodb+srv string, and populate the necessary fields. Save the entry and you should be able to connect to your instance.
