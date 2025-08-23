# Connect to a Neptune instance

As per this [Amazon page](<https://docs.aws.amazon.com/neptune/latest/userguide/graph-notebooks.html#graph-notebooks-local-with-neptune> "target=\"\_blank\""), "The most convenient way for most people, however, is to connect to set up an Amazon EC2 proxy server within the VPC and then use [SSH tunneling](<https://www.ssh.com/ssh/tunneling/> "target=\"\_blank\"") (also called port forwarding), to connect to it."&nbsp; And on [this page](<https://docs.aws.amazon.com/neptune/latest/userguide/get-started-access-graph.html> "target=\"\_blank\""), "For information about connecting to an EC2 instance using SSH, see [Connect to Your Linux Instance](<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstances.html> "target=\"\_blank\"") in the *Amazon EC2 User Guide for Linux Instances*."

&nbsp;

Below are step-by-step instructions in the context of Hackolade.

## Create a Neptune cluster

### Go to Neptune in AWS console and create database

### ![Neptune connect 1](<lib/Neptune connect 1.png>)

&nbsp;

![Neptune connect 2](<lib/Neptune connect 2.png>)

&nbsp;

&nbsp;

### Create security group and subnet group

Make sure to select "Create new VPC", then open up "Additional connectivity configuration", then "Create new DB Subnet Group", and make a note of the new VPC security group name:

&nbsp;

![Neptune connect 3](<lib/Neptune connect 3.png>)

&nbsp;

Then, press the Create data base button.

&nbsp;

## Create an EC2 instance

### Go to EC2 -\> Network \& Security -\> Security Groups in AWS console

Select the VPC security group created above:

![Neptune connect 4](<lib/Neptune connect 4.png>)

&nbsp;

&nbsp;

### Edit the inbound rules

Add SSH port with CIDR 0.0.0.0/0 and to port 8182 add CIDR 0.0.0.0/0.&nbsp; Or restrict to the IP addresses of your Hackolade installation.

![Neptune connect 5](<lib/Neptune connect 5.png>)

&nbsp;

&nbsp;

### Go to EC2 instances in AWS console

Create an instance in the same region as your Neptune cluster, e.g. “Ubuntu Server 20.04 LTS”

&nbsp;

![Neptune connect 6](<lib/Neptune connect 6.png>)

&nbsp;

In the configuration section select the same VPC as for Neptune, choose one of the Subnets and assign public IP:

![Neptune connect 7](<lib/Neptune connect 7.png>)

&nbsp;

&nbsp;

&nbsp;

In the security group section select existing security group (neptune-security-group)

![Neptune connect 8](<lib/Neptune connect 8.png>)

&nbsp;

Press “review and launch”, then in the dialog, create and download key pair:

![Neptune connect 9](<lib/Neptune connect 9.png>)

&nbsp;

### &nbsp;

### Ensure you have the proper IAM access rights to Neptune infrastructure

To be able to access your Neptune cluster from Hackolade you need to have the right to run the action rds:DescribeDBClusters.

&nbsp;

## In Hackolade

Fill in the connection settings, from either the forward- or reverse-engineering functions:

![Neptune connect 10](<lib/Neptune connect 10.png>)

&nbsp;

where:

**Name** is friendly name you assign to the connection

**Cluster identifier** corresponds to the cluster name you assigned to the Neptune cluster:

![Neptune connect 11](<lib/Neptune connect 11.png>)

&nbsp;

**Region** is the the region where both your Neptune cluster and EC2 instance are located

**EC2 Public Address** is the IP address of the EC2 instance created above

**SSH Port** is 22

**User Name** is ubuntu, unless you chose a different type of EC2 instance.&nbsp; To check, select your instance and click Connect

&nbsp;

![Neptune connect 12](<lib/Neptune connect 12.png>)

&nbsp;

**Private key** is the path and file name to the .pem file downloaded during the previous step.

&nbsp;

Finally, in the Authentication tab of the Hackolade connection dialog:

&nbsp;

![Neptune connect 13](<lib/Neptune connect 13.png>)

&nbsp;

You may leave the information blank if you already have an AWSCLI setup.&nbsp; Otherwise, enter either a [session token](<https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_temp\_use-resources.html> "target=\"\_blank\""), or the Access Key ID and Secret Access Key combination.

&nbsp;

