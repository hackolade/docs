# Connect to Amazon Redshift

To access an Amazon Redshift database, you should obtain the proper credentials from your administrator.&nbsp; In particular you'll need to know your Access Key, Secret Access Key, and the Region for the instance.

&nbsp;

## Cluster instance

Give a meaningful name to the connection:

![Redshift connection settings](<lib/Redshift%20connection%20settings.png>)

You also must specify the cluster identifier and database name.

&nbsp;

&nbsp;

Then go to the Authentication tab, and paste the Access Key ID received from your administrator, and Secret Access Key for your IAM.&nbsp; Finally, select the appropriate region where your Redshift cluster is located.

&nbsp;

![Redshift authentication](<lib/Redshift%20authentication.png>)

&nbsp;

If you wish to handle AWS authentication through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\""), you may leave blank the Access Key ID and Secret Access Key fields, knowing that Hackolade supplies credentials following the recommendations described [here](<https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html> "target=\"\_blank\""). Or use a temporary [session token](<https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_temp\_use-resources.html> "target=\"\_blank\"").

&nbsp;

&nbsp;

## Serverless

With serverless Redshift; you must specify the workgroup as well as the database name:

![Redshift - serverless connection settings](<lib/Redshift%20-%20serverless%20connection%20settings.png>)

&nbsp;

Authentication is similar to the cluster instance above.

