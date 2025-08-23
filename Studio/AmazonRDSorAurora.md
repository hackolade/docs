# Amazon RDS or Aurora

Amazon RDS (Relational Database Service) offers two options to run the PostgreSQL database engine in the Cloud: the RDS is a managed service that simplifies PostgreSQL database setup and management, offering basic scalability and automated backups. Or Aurora for PostgreSQL, a high-performance, cloud-native version of PostgreSQL built on a distributed storage system, designed to provide better performance and availability with features like faster recovery and automated scaling. RDS is ideal for simpler workloads with moderate scaling needs, while Aurora is suited for high-demand applications requiring faster performance, auto-scaling, and greater fault tolerance.

&nbsp;

Hackolade Studio can perform modeling for both options, using the [PostgreSQL plugin](<PostgreSQL.md>) while connecting securely, using SSL/TLS (full-verify SSL mode.)&nbsp; RDS instances are sometimes set up to be only accessible using SSH over a EC2 instance (SSH tunneling).

&nbsp;

Before you're able to connect to an AWS RDS instance with Hackolade Studio, you'll need to gather relevant information and files, which will then be referenced in the Hackolade Studio connection parameters.

&nbsp;

There are many parameters in the setup of a Postgres instance.&nbsp; The connection setup depends greatly on whether or not access is public or using an EC2 bastion instance.

&nbsp;

![RDS - public access choice](<lib/RDS - public access choice.png>)

&nbsp;

We cover both cases below.

### Public access

With public access, it is much easier to set up the connection.

&nbsp;

### Database endpoint and Port

In the RDS instance screen, the tab "Connectivity \& security" confirms the public accessibility, and shows the Endpoint and Port to be used (by default 5432.)

&nbsp;

![RDS - public connectivity and security](<lib/RDS - public connectivity and security.png>)

&nbsp;

In the Hackolade connection settings dialog, give a meaningful name to the connection, then set the the endpoint host and port, and an optional database name if you wish to limit the scope of the discovery. &nbsp;

![RDS - public connection host and port setting](<lib/RDS - public connection host and port setting.png>)

&nbsp;

### Authentication

In the Authentication tab, you must provide the credentials given by your database administrator, created according to these [instructions](<https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Appendix.PostgreSQL.CommonDBATasks.Access.html> "target=\"\_blank\"").

![Image](<lib/RDS - authentication with username-password.png>)

&nbsp;

&nbsp;

### SSL certificate bundle&nbsp;

Finally, it is now required to [download from AWS](<https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.SSL.html#UsingWithRDS.SSL.CertificatesDownload> "target=\"\_blank\""), then reference an official certificate bundle for RDS.&nbsp; It is possible to get a bundle specific to the region of your instance (smaller file), or to get the global certificate bundle for all AWS regions.&nbsp; You must download the Privacy Enhanced Mail (PEM) bundle, and place it on your local system in a place where Hackolade Studio can access it.&nbsp; Make sure to choose the SSL option "Verify Full":

&nbsp;

![Image](<lib/RDS - SSL Certificate bundle.png>)

&nbsp;

You may now save your entry and connect to the RDS instances.

&nbsp;

&nbsp;

### No public access

The process is [documented](<https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/tutorial-ec2-rds-option1.html> "target=\"\_blank\"") by AWS, and we summarize here the parts that are relevant to connect with Hackolade Studio.

&nbsp;

The architecture, courtesy of Amazon, looks like this:

![Image](<lib/RDS - no publis access architecture EC2.png>)

&nbsp;

&nbsp;

Perform all steps above for the public access, plus this additional and critical last step...

### SSH certificate of the EC2 server&nbsp;

If your RDS instance does not have a public IP address, then access is allowed through a secure EC2 "bastion" server.&nbsp; That EC2 instance must be in the same VPC as the RDS database. This can be either an existing EC2 instance, or one that is created just for this purpose.&nbsp; The Security group must include the following three rules:

\- Allow SSH from your IP address

\- Allow HTTPS traffic from anywhere

\- Allow HTTP traffic from anywhere

&nbsp;

You can find this information in the EC2 details screen&nbsp;

&nbsp;

![RDS - EC2 Bastion instance info](<lib/RDS - EC2 Bastion instance info.png>)

&nbsp;

&nbsp;

&nbsp;

You also need to find out which SSH user name to reference.&nbsp; To that effect, you need to know the type of platform that is running your EC2 instance (Amazon Linux, Ubuntu, ...).&nbsp; In general when your instance runs Ubuntu the user will be '''ubuntu''' but otherwise it's most of the time '''ec2-user'''.

&nbsp;

![RDS - EC2 Bastion instance details](<lib/RDS - EC2 Bastion instance details.png>)

&nbsp;

Finally, you need to get from your administrator the Privacy Enhanced Mail (PEM).&nbsp; **Note** that this is second PEM file specifically for the EC2 bastion server to be used in the context of SSH -- not to be confused with the PEM bundle used for SSL in the previous step.

&nbsp;

During the setup of RDS with private access through the EC2 bastion server, there was a step to create and save the PRM

![RDS - private SSH key pair PEM creation](<lib/RDS - private SSH key pair PEM creation.png>)

&nbsp;

&nbsp;

&nbsp;

Setup the SSH tunneling using your EC2 instance connection details, using the SSH Address, port 22 by default, the SSH user name ("ec2-user" for Amazon Linux, or "ubuntu"), then select the auth method "private key", and reference the path to the key pair (.pem).

&nbsp;

![Image](<lib/RDS - SSH addres port username and PEM.png>)

&nbsp;

You should now be able to connect to your EC2 instance to tunnel to your RDS instance.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

