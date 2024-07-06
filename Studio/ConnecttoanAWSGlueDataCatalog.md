# Connect to an AWS Glue Data Catalog

To access a Glue Data Catalog, you should obtain the proper credentials from your administrator.&nbsp; In particular you'll need to know your Access Key, Secret Access Key, and the Region for the instance.

&nbsp;

Give a meaningful name to the connection:

![Glue data catalog connection name](<lib/Glue%20connection%20name.png>)

&nbsp;

&nbsp;

Then go to the Authentication tab, and paste the Access Key ID received from your administrator, and Secret Access Key for your IAM.&nbsp; Finally, select the appropriate region where your AWS Glue Data Catalog is located.

&nbsp;

![Glue data catalog connection settings](<lib/Glue%20connection%20settings.png>)

&nbsp;

If you wish to handle AWS authentication through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\""), you may leave blank the Access Key ID and Secret Access Key fields, knowing that Hackolade supplies credentials following the recommendations described [here](<https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html> "target=\"\_blank\"").&nbsp; Or use a temporary [session token](<https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_temp\_use-resources.html>).

&nbsp;

