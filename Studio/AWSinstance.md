# AWS instance

To access a DynamoDB instance, you should obtain the proper credentials from your administrator.&nbsp; In particular you'll need to know your Access Key, Secret Access Key, and the Region for the instance.

&nbsp;

Give a meaningful name to the connection and make sure that the option 'use local DynamoDB' is unchecked.

![Reverse-Engineering - DynamoDB connect AWS1](<lib/Rev-Engineering - DynamoDB connect AWS1.png>)

&nbsp;

Then go to the Authentication tab, and paste the Access Key ID received from your administrator, and Secret Access Key for your IAM.&nbsp; Finally, select the appropriate region where your DynamoDB instance is located.

![Reverse-Engineering - DynamoDB connect AWS2](<lib/Rev-Engineering - DynamoDB connect AWS2.png>)

&nbsp;

You may test the connection prior to saving the connection parameters for future use.

&nbsp;

If you wish to handle AWS authentication through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\""), you may leave blank the Access Key ID and Secret Access Key fields, knowing that Hackolade supplies credentials following the recommendations described [here](<https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html> "target=\"\_blank\"") or use a temporary [session token](<https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_temp\_use-resources.html> "target=\"\_blank\"").

