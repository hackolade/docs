# AWS IAM

Using Amazon Web Services Identity and Access Management (AWS IAM) reduces the number of authentication mechanisms and number of secrets to manage. The secret key that you use for authentication is not sent over the wire to Atlas and is not persisted by the driver.&nbsp; Hackolade Studio supports this mechanism starting with v8.1.5

&nbsp;

To be able to leverage this capability in Hackolade Studio, you must first set things up according to the MongoDB documentation on [Authentication with AWS IAM](<https://www.mongodb.com/docs/atlas/security/aws-iam-authentication/> "target=\"\_blank\"").

&nbsp;

In the connections settings dialog for MongoDB, in the Auth tab, choose the AWS authentication:

&nbsp;

![Image](<lib/RE - MongoDB - AWS IAM.png>)

&nbsp;

&nbsp;

Then fill in your Access Key ID and Secret Access Key, or your Session Token.

&nbsp;

If you wish to handle AWS authentication through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\""), you may leave blank the Access Key ID and Secret Access Key fields, knowing that Hackolade Studio supplies credentials following the recommendations described [here](<https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html> "target=\"\_blank\"").

&nbsp;

