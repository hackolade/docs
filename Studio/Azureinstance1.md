# Azure instance

To access a Cosmos DB instance, you should obtain the proper credentials from your administrator.&nbsp; In particular you'll need to know the URI and Access Key.

&nbsp;

Go to the [Azure portal](<https://portal.azure.com/> "target=\"\_blank\"") to retrieve your connection information.&nbsp; More info [here](<https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account> "target=\"\_blank\"").

![Image](<lib/Azure%20portal%20-%20Mongo%20API%20connection.png>)

&nbsp;

Give a meaningful name to the connection to identify it for later, and provide proper connection string parameters:

&nbsp;

&nbsp;

![Image](<lib/Cosmos%20with%20Mongo%20API%20Connection%20settings.png>)

&nbsp;

In the Azure portal, navigate to your Azure Cosmos DB account, and click on **Connection String**. &nbsp; Copy the HOST from the portal and paste it into \<Address\>, then enter the port number 10255 into \<Port\>.&nbsp;

&nbsp;

&nbsp;

![Image](<lib/Cosmos%20with%20Mongo%20API%20Connection%20authent.png>)

Then go to the Authentication tab, and copy the the username and password. &nbsp;

