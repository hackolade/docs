# Azure instance

To access a Cosmos DB instance, you should obtain the proper credentials from your administrator.&nbsp; At a minimum, you'll need to know the URI and Access Key. &nbsp;

&nbsp;

When performing reverse-engineering of Cosmos DB, most of the information can be retrieved through the Data Plane account key.&nbsp; If provided additional Control Plane parameters, Hackolade is able to also retrieve additional metadata, such as: tags, location and region replication, automatic failover, virtual network filter and rules, and IP-range filter.&nbsp;

&nbsp;

## Data plane

Give a meaningful name to the connection to identify it for later, and provide proper connection string parameters:

![Cosmos DB connection settings dialog](<lib/Cosmos DB connection settings dialog.png>)

&nbsp;

&nbsp;

Go to the [Azure portal](<https://portal.azure.com/> "target=\"\_blank\"") to retrieve your URL, port number, and Primary Key.&nbsp; In the Azure portal, navigate to your Azure Cosmos DB account, and click on **Keys**. &nbsp; Copy the URI from the portal and paste it into \<Address\> (without the port number), then enter the port number into \<Port\>, and finally copy the PRIMARY or SECONDARY key, either Read-Write or Read-Only, and paste it into \<Account Key\>.

&nbsp;

![Azure Portal - DocDB connection](<lib/Azure Portal - DocDB connection.png>)

&nbsp;

&nbsp;

## Control Plane

The REST API connection must be enabled and all the proper parameters provided if you wish for Hackolade to retrieve additional Azure metadata such as: tags, location and region replication, automatic failover, virtual network filter and rules, and IP-range filter.&nbsp;

&nbsp;

![CosmosDB Data Plane dialog](<lib/CosmosDB Data Plane dialog.png>)

&nbsp;

&nbsp;

First, you must provide the **Resource Group Name** and **Subscription ID** of Cosmos DB instance, as found in the Overview screen of the Cosmos DB instance. More information [here](<https://docs.microsoft.com/en-us/azure/cosmos-db/how-to-manage-database-account#create-an-account> "target=\"\_blank\"").

![CosmosDB - Azure instance overview screen](<lib/CosmosDB - Azure instance overview screen.png>)

&nbsp;

Next, the Hackolade application must be registered so Azure accepts the REST API calls, as per these [instructions](<https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal> "target=\"\_blank\"").&nbsp; The **Application (client) ID** and the **Directory (tenant) ID** are retrieved are retrieved from the App registration Overview screen:

![CosmosDB - Azure App registration overview](<lib/CosmosDB - Azure App registration overview.png>)

&nbsp;

**Note:** it is critical to assign the proper role to the application just registered.&nbsp; This is done following the steps outlined [here](<https://docs.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal> "target=\"\_blank\"").&nbsp;

![CosmosDB - Azure IAM role assignment](<lib/CosmosDB - Azure IAM role assignment.png>)

&nbsp;

Finally, the **Application secret** is obtained from the Certificates \& secrets screen of the App registration:&nbsp;

![CosmosDB - Azure App registration secrets scr](<lib/CosmosDB - Azure App registration secrets scr.png>)

&nbsp;

If you don't know how to generate some of the above values, you may want to consult this [document](<https://github.com/Azure/azure-libraries-for-net/blob/master/AUTH.md> "target=\"\_blank\"").

&nbsp;

