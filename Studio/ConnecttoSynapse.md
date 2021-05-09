# Connect to Synapse

&nbsp;

&#49;) Data Plane

In the Hackolade connection settings dialog for Synapse, give a meaningful name to the connection, choose the source (on-prem/cloud or Azure SQL Database), then set the database name, the host and port:

&nbsp;

![Image](<lib/Synapse%20connection%20settings.png>)

&nbsp;

then enter your username/password:

![Image](<lib/Synapse%20connection%20authentication.png>)

&nbsp;

Alternatively, you may choose to provide a connection string which includes: host, port, username and password:

![Image](<lib/Synapse%20Connection%20String.png>)

&nbsp;

## &#50;) Control Plane ##

The REST API connection should be enabled and all the proper parameters provided if you wish for Hackolade to retrieve additional Azure metadata such as: tags, location and region replication, automatic failover, virtual network filter and rules, and IP-range filter.&nbsp;

&nbsp;

![Image](<lib/CosmosDB%20Data%20Plane%20dialog.png>)

&nbsp;

&nbsp;

First, you must provide the **Resource Group Name** and **Subscription ID** of Cosmos DB instance, as found in the Overview screen of the Comos DB instance. More information [here](<https://docs.microsoft.com/en-us/azure/cosmos-db/how-to-manage-database-account#create-an-account> "target=\"\_blank\"").

![Image](<lib/CosmosDB%20-%20Azure%20instance%20overview%20screen.png>)

&nbsp;

Next, the Hackolade application must be registered so Azure accepts the REST API calls, as per these [instructions](<https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal> "target=\"\_blank\"").&nbsp; The **Application (client) ID** and the **Directory (tenant) ID** are retrieved are retrieved from the App registration Overview screen:

![Image](<lib/CosmosDB%20-%20Azure%20App%20registration%20overview.png>)

&nbsp;

**Note:** it is critical to assign the proper role to the application just registered.&nbsp; This is done following the steps outlined [here](<https://docs.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal> "target=\"\_blank\"").&nbsp;

![Image](<lib/CosmosDB%20-%20Azure%20IAM%20role%20assignment.png>)

&nbsp;

Finally, the **Application secret** is obtained from the Certificates \& secrets screen of the App registration:&nbsp;

![Image](<lib/CosmosDB%20-%20Azure%20App%20registration%20secrets%20scr.png>)

&nbsp;

If you don't know how to generate some of the above values, you may want to consult this [document](<https://github.com/Azure/azure-libraries-for-net/blob/master/AUTH.md> "target=\"\_blank\"").

&nbsp;

&nbsp;


***
_Created with the Personal Edition of HelpNDoc: [Create iPhone web-based documentation](<https://www.helpndoc.com/feature-tour/iphone-website-generation>)_
