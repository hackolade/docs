# Connect to a Delta Lake instance

In the premium version of Databricks, it is possible to control [table access](<https://docs.databricks.com/security/access-control/table-acls/index.html#table-access-control> "target=\"\_blank\"").  If that's the case, the user must be granted the following [data object privileges](<https://docs.databricks.com/security/access-control/table-acls/object-privileges.html#data-object-privileges> "target=\"\_blank\""):

1. for reverse-engineering: READ\_METADATA and SELECT  on the tables and views
1. for forward-engineering (apply to instance): rights to CREATE/UPDATE schema, table, and view: CREATE on the CATALOG, and either OWN or both USAGE and CREATE on the schema, tables and views.

&nbsp;

Connecting a Databricks instance on one of the cloud providers requires to declare the connections settings and a personal access token.

&nbsp;

![Delta Lake Databicks connection settings](<lib/Delta%20Lake%20connection%20settings.png>)

&nbsp;

&nbsp;

You should consult this [page](<https://docs.databricks.com/workspace/workspace-details.html> "target=\"\_blank\"") for more information on finding Databricks workspace details.

&nbsp;

**Note:** the connection must be established with compute clusters, i.e. not with the SQL Warehouse which uses a different API which we do not support.

&nbsp;

To get the cluster ID, click the **Clusters** tab in sidebar and then select a cluster name. The cluster ID is the number after the /clusters/ component in the URL of this page:

https://\<databricks-instance\>/#/setting/clusters/\<cluster-id\>

&nbsp;

In the following screenshot, the cluster ID is 1115-164516-often242:

![Delta Lake Databricks connection settings input](<lib/Delta%20Lake%20connection%20settings%20input.png>)

&nbsp;

&nbsp;

Hackolade uses the Databricks REST API, and requires that an access token be issued in the Databricks console under User Settings \> Generate New Token.&nbsp; For more information, please consult [this page](<https://docs.databricks.com/sql/user/security/personal-access-tokens.html> "target=\"\_blank\""). The access token must be pasted in the field below.&nbsp; Access token management is described [here](<https://docs.databricks.com/administration-guide/access-control/tokens.html> "target=\"\_blank\"").

&nbsp;

![Delta Lake Databricks connections settings auth](<lib/Delta%20Lake%20connections%20settings%20auth.png>)

&nbsp;

For Databricks on Azure, you may have tables using Azure Data Lake Storage which requires additional authentication for Databricks to access it.&nbsp; In such case, you may need to declare ADLS credentials passthrough:

![Databricls ADLS passthrough credentials](<lib/Databricls%20ADLS%20passthrough%20credentials.png>)

&nbsp;

You may want to read more about [ADLS credential passthrough](<https://learn.microsoft.com/en-us/azure/databricks/security/credential-passthrough/adls-passthrough> "target=\"\_blank\"").

&nbsp;

