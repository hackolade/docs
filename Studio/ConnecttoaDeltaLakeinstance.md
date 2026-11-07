---
description: Connect Hackolade Studio to Databricks Delta Lake, with the table access privileges needed for reverse- and forward-engineering.
seoTitle: Connect to Delta Lake on Databricks
image: lib/Delta Lake connection settings.png
---
# Connect to a Delta Lake instance

In the premium version of Databricks, it is possible to control [table access](<https://docs.databricks.com/security/access-control/table-acls/index.html#table-access-control> "target=\"_blank\""). If that's the case, the user must be granted the following [data object privileges](<https://docs.databricks.com/security/access-control/table-acls/object-privileges.html#data-object-privileges> "target=\"_blank\""):

1. for reverse-engineering: READ_METADATA and SELECT on the tables and views
2. for forward-engineering (apply to instance): rights to CREATE/UPDATE schema, table, and view: CREATE on the CATALOG, and either OWN or both USAGE and CREATE on the schema, tables and views.

Connecting a Databricks instance on one of the cloud providers requires to declare the connections settings and a personal access token.

![Delta Lake connection settings](<lib/Delta Lake connection settings.png>)

You should consult this [page](<https://docs.databricks.com/workspace/workspace-details.html> "target=\"_blank\"") for more information on finding Databricks workspace details.

> [!NOTE]
> The connection must be established with compute clusters, i.e. not with the SQL Warehouse which uses a different API which we do not support. It is not currently possible to connect using only a Serverless compute. The problem, if we don't leverage the compute cluster, is that many functions of our reverse-engineering process are not supported by the API. We will lose at least the reverse-engineering of views and of Bloom filters, plus maybe other things.

To get the cluster ID, click the **Clusters** tab in sidebar and then select a cluster name. The cluster ID is the number after the `/clusters/` component in the URL of this page, and before the `?o=:`

```text
https://<databricks-instance>/#/setting/clusters/<cluster-id>
```

In the following screenshot, the cluster ID is `0522-122550-st68dyc7`

![Delta Lake connection settings input](<lib/Delta Lake connection settings input.png>)

## Authentication

### Personal Access Token

Hackolade Studio can use the Databricks REST API, and requires that an access token be issued in the Databricks console under User Settings > Generate New Token. For more information, please consult [this page](<https://docs.databricks.com/sql/user/security/personal-access-tokens.html> "target=\"_blank\""). The access token must be pasted in the field below. Access token management is described [here](<https://docs.databricks.com/administration-guide/access-control/tokens.html> "target=\"_blank\"").

![Delta Lake Databricks connections settings auth](<lib/Delta Lake connections settings auth.png>)

### OAuth authorization code flow (PCKE)

OAuth sign-in replaces a Databricks personal access token when you reverse-engineer or run a script in a Databricks workspace. If configured for OAuth, Hackolade Studio opens your browser to sign in when you connect. You need Hackolade version `v8.13.8` and above to have this feature.

On the Authentication tab, you choose one of two OAuth methods:

- Microsoft Entra ID via authorization code flow (PKCE), for Azure Databricks only. You sign in with your work account.
- OAuth authorization code flow (PKCE), for any cloud provider. An account admin registers a public application in the Databricks account console, and you paste its client ID in Hackolade Studio.

Both methods use [authorization code with PKCE](<https://docs.databricks.com/aws/en/dev-tools/auth/oauth-u2m.html> "target=\"_blank\""). Personal access token remains available as a legacy option.

<img src="lib/Databricks authentication OAuth flow PKCE.png" alt="Databricks authentication Entra ID or OAuth flow PKCE" width="491">

#### Sign in with Microsoft Entra ID (Azure Databricks)

Use this method when the cloud provider is Azure Databricks.

1. Open `Tools > Reverse-Engineer > Delta Lake tables...`. In Delta Lake Connections, create or edit a connection.
2. On the Connection tab, set Cloud provider to Azure Databricks, then set Workspace URL, Cluster id, and optionally Catalog name and Schema name.
3. On the Authentication tab, set Authentication method to Microsoft Entra ID via authorization code flow (PKCE)
4. Save the connection, then choose Test connection or start the reverse-engineering. Hackolade Studio opens your browser on the Microsoft sign-in page. After you sign in, the browser returns to `http://localhost:30424/oauth` and Studio continues the connection.

> [!IMPORTANT]
> Important: this method is only for Azure Databricks. If the cloud provider is Databricks on AWS, Databricks runtime on GCP, or Databricks runtime, the connection stops before the browser opens. Use OAuth authorization code flow (PCKE) instead, or change the cloud provider.

The first sign-in in a customer Microsoft Entra tenant can stop until an administrator consents to the Hackolade application. When that happens, Hackolade Studio shows a message with an admin consent link. An Azure administrator opens that link, grants consent for the tenant, then you retry the connection.

#### Sign in with a Databricks OAuth application

Use this method when you have a client ID from a public OAuth application in the Databricks account console. It works for Azure Databricks, Databricks on AWS, Databricks on GCP, and Databricks runtime.

##### Register the application in Databricks

An account admin registers a public OAuth application in the Databricks account console. The application has a client ID and no client secret. Hackolade Studio then uses that client ID when a user connects.

1. Open the account console for your cloud, not the workspace:
   - AWS: [`https://accounts.cloud.databricks.com`](<https://accounts.cloud.databricks.com> "target=\"_blank\"")
   - Azure: [`https://accounts.azuredatabricks.net`](<https://accounts.azuredatabricks.net> "target=\"_blank\"")
   - GCP: [`https://accounts.gcp.databricks.com`](<https://accounts.gcp.databricks.com> "target=\"_blank\"")
2. Click the Settings icon in the sidebar.
3. Open the App connections tab, then click on Custom apps.
4. Click Add connection.
5. Enter a name, for example `Hackolade Studio`.
6. In Redirect URLs, enter exactly `http://localhost:30424/oauth`.
7. For Access scopes, select `all-apis` and `offline_access`.
8. Leave the access-token and refresh-token lifetimes at their defaults unless your account requires other values.
9. Leave Generate a client secret cleared. A secret is only for a confidential client. Hackolade Studio signs in with PKCE and does not use one.
10. Click Add.
11. In the Connection created dialog, copy the Client ID.

Databricks documents the same steps under [Enable custom OAuth applications using the Databricks UI](<https://docs.databricks.com/aws/en/integrations/enable-disable-oauth> "target=\"_blank\"").

##### Enter the connection in Hackolade Studio

Open `Tools > Reverse-Engineer > Delta Lake tables...`. In Delta Lake Connections, create or edit a connection.

On the Connection tab, set:

- Cloud provider, for example, Azure Databricks
- Workspace URL (e.g.: `https://<workspace-id>.azuredatabricks.net`)
- Cluster id
- Catalog name and Schema name if you want to limit the scope; both are optional

On the Authentication tab, set Authentication method to OAuth authorization code flow (PCKE), then paste the client ID into Client id.

> [!IMPORTANT]
> Port 30424 must be free on your machine when you connect. If another program is already listening on it, the sign-in fails. The redirect URL does not move to another port.
>
> The error shown in the UI will be the following: Cannot start the local authentication callback server: port 30424 is already in use. Close the application using this port and try again.

## ADLS credentials passthrough

For Databricks on Azure, you may have tables using Azure Data Lake Storage which requires additional authentication for Databricks to access it. In such case, you may need to declare ADLS credentials passthrough:\
![Databricls ADLS passthrough credentials](<lib/Databricls ADLS passthrough credentials.png>)

You may want to read more about [ADLS credential passthrough](<https://learn.microsoft.com/en-us/azure/databricks/security/credential-passthrough/adls-passthrough> "target=\"_blank\"").
