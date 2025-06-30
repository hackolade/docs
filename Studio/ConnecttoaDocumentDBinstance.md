# Connect to a DocumentDB instance

DocumentDB clusters are deployed within an Amazon Virtual Private Cloud (Amazon VPC). They can be accessed directly by Amazon EC2 instances or other AWS services that are deployed in the same Amazon VPC. Additionally, Amazon DocumentDB can be accessed by EC2 instances or other AWS services in different VPCs in the same AWS Region or other Regions via VPC peering.

&nbsp;

Often the situation requires Hackolade to access the DocumentDB resources from outside the cluster's VPC. In that case, you can use SSH tunneling (also known as *port forwarding*) to access your DocumentDB resources through an EC2 instance.

&nbsp;

You must first follow carefully and precisely all the steps described in [this page](<https://docs.aws.amazon.com/documentdb/latest/developerguide/connect-ec2.html> "target=\"\_blank\"").

&nbsp;

Finally, you need to populate the corresponding values in the Hackolade connection settings dialog tabs:

&nbsp;

In the Hackolade connection settings dialog, give a meaningful name to the connection, then set the the host and port.&nbsp; The host entry corresponds to the Cluster endpoint URL that can be found in the Configuration tab of the DocumentDB Cluster information screen.&nbsp; The port number is also indicated and should generally be 27017.

&nbsp;

![DocumentDB connection tab](<lib/DocumentDB connection tab.png>)

&nbsp;

&nbsp;

In the Authentication tab, please enter your username and password:

&nbsp;

![DocumentDB authentication tab](<lib/DocumentDB authentication tab.png>)

&nbsp;

As indicated in Step 6 of the EC2 [instructions,](<https://docs.aws.amazon.com/documentdb/latest/developerguide/connect-ec2.html#connect-ec2.tls> "target=\"\_blank\"") you should have downloaded the CA certificate for Amazon DocumentDB from [https://s3.amazonaws.com/rds-downloads/rds-combined-ca-bundle.pem](<https://s3.amazonaws.com/rds-downloads/rds-combined-ca-bundle.pem> "target=\"\_blank\"") &nbsp; Copy the certificate to a safe location (for example the folder specified in Tools \> Options \> Default Paths \> SSL/SSH Certificates), then reference that path and certificate file in the field Certificate Authority:

&nbsp;

![DocumentDB SSL tab](<lib/DocumentDB SSL tab.png>)

&nbsp;

Next, you need to set up the details for the SSH connection to your EC2 instance.&nbsp; The SSH address is the Public IPv4 DNS found in the instance summary.&nbsp; Post is usually 22, and the SSH username is generally ec2-user. &nbsp;

&nbsp;

The private key for your EC2 instance is created in the left menu of your EC2 instance Network \& Security \> Key Pairs, following these [instructions](<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair> "target=\"\_blank\"").&nbsp; Copy the certificate to a safe location (for example the folder specified in Tools \> Options \> Default Paths \> SSL/SSH Certificates), then reference that path and certificate file in the field Private Key:

&nbsp;

![DocumentDB SSH tab](<lib/DocumentDB SSH tab.png>)

&nbsp;

&nbsp;

Finally, in order to retrieve the cluster metadata, go to the Authentication tab, and paste the Access Key ID received from your administrator, and Secret Access Key for your IAM. &nbsp;

&nbsp;

![DocumentDB AWS access tab](<lib/DocumentDB AWS access tab.png>)

If you wish to handle AWS authentication through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\""), you may leave blank the Access Key ID and Secret Access Key fields, knowing that Hackolade Studio supplies credentials following the recommendations described [here](<https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html> "target=\"\_blank\""). Or use a temporary [session token](<https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_temp\_use-resources.html> "target=\"\_blank\"").

&nbsp;

