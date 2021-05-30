# Connect to a Delta Lake instance

Connecting a Databricks instance on one of the cloud providers requires to declare the connections settings and a personal access token.

&nbsp;

![Image](<lib/Delta%20Lake%20connection%20settings.png>)

&nbsp;

&nbsp;

You should consult this [page](<https://docs.databricks.com/workspace/workspace-details.html> "target=\"\_blank\"") for more information on finding Databricks workspace details.

&nbsp;

To get the cluster ID, click the **Clusters** tab in sidebar and then select a cluster name. The cluster ID is the number after the /clusters/ component in the URL of this page:

https://\<databricks-instance\>/#/setting/clusters/\<cluster-id\>

&nbsp;

In the following screenshot, the cluster ID is 1115-164516-often242:

![Image](<lib/Delta%20Lake%20connection%20settings%20input.png>)

&nbsp;

&nbsp;

Hackolade uses the Databricks REST API, and requires that an access token be issued in the Databricks console under User Settings \> Generate New Token.&nbsp; For more information, please consult [this page](<https://docs.databricks.com/sql/user/security/personal-access-tokens.html> "target=\"\_blank\""). The access token must be pasted in the field below.&nbsp; Access token management is described [here](<https://docs.databricks.com/administration-guide/access-control/tokens.html> "target=\"\_blank\"").

&nbsp;

![Image](<lib/Delta%20Lake%20connections%20settings%20auth.png>)

&nbsp;

