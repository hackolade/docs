# Connect to Synapse

&nbsp;

## Data Plane

In the Hackolade connection settings dialog for Synapse, give a meaningful name to the connection, choose the source (on-prem/cloud or Azure SQL Database), then set the database name, the host and port:

&nbsp;

![Synapse connection settings](<lib/Synapse connection settings.png>)

&nbsp;

then enter your username/password:

![Synapse connection authentication](<lib/Synapse connection authentication.png>)

&nbsp;

&nbsp;

https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/sql-authentication?tabs=serverless

&nbsp;

&nbsp;

Alternatively, you may choose to provide a connection string which includes: host, port, username and password:

![Synapse Connection String](<lib/Synapse Connection String.png>)

&nbsp;

&nbsp;

&nbsp;

If you choose Azure Active Directory, you must also specify your "Tenant ID" ([how-to find your tenant ID?](<https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-how-to-find-tenant> "target=\"\_blank\""))&nbsp;

&nbsp;

![Synapse Azure AD Directory tenant ID](<lib/Synapse Azure AD Directory tenant ID.png>)

please also consult:

https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/active-directory-authentication

&nbsp;

with MFA:

https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/mfa-authentication

https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-mfa-howitworks

&nbsp;

&nbsp;

## Control Plane

The REST API connection should be enabled and all the proper parameters provided if you wish for Hackolade to retrieve additional Azure metadata such as: tags, location and region replication, automatic failover, virtual network filter and rules, and IP-range filter.&nbsp;

&nbsp;

![Synapse Data Plane dialog](<lib/CosmosDB Data Plane dialog.png>)

&nbsp;

&nbsp;

First, you must provide the **Resource Group Name** and **Subscription ID** of Cosmos DB instance, as found in the Overview screen of the Comos DB instance. More information [here](<https://docs.microsoft.com/en-us/azure/cosmos-db/how-to-manage-database-account#create-an-account> "target=\"\_blank\"").

![Synapse - Azure instance overview screen](<lib/CosmosDB - Azure instance overview screen.png>)

&nbsp;

Next, the Hackolade application must be registered so Azure accepts the REST API calls, as per these [instructions](<https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal> "target=\"\_blank\"").&nbsp; The **Application (client) ID** and the **Directory (tenant) ID** are retrieved are retrieved from the App registration Overview screen:

![Synapse - Azure App registration overview](<lib/CosmosDB - Azure App registration overview.png>)

&nbsp;

**Note:** it is critical to assign the proper role to the application just registered.&nbsp; This is done following the steps outlined [here](<https://docs.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal> "target=\"\_blank\"").&nbsp;

![Synapse- Azure IAM role assignment](<lib/CosmosDB - Azure IAM role assignment.png>)

&nbsp;

Finally, the **Application secret** is obtained from the Certificates \& secrets screen of the App registration:&nbsp;

![Synapse - Azure App registration secrets scr](<lib/CosmosDB - Azure App registration secrets scr.png>)

&nbsp;

If you don't know how to generate some of the above values, you may want to consult this [document](<https://github.com/Azure/azure-libraries-for-net/blob/master/AUTH.md> "target=\"\_blank\"").

&nbsp;

&nbsp;

