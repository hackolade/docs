# Connect to an AWS RDS or Aurora PostgreSQL instance

Amazon RDS offers two options to run PostgreSQL database engines in the Cloud, the usual RDS PostgreSQL instance or an Aurora PostgreSQL instance.  Hackolade can perform modeling for these two AWS databases using the PostgreSQL plugin while connecting in a specific manner as AWS enforces SSL/TLS (full-verify ssl mode) and such instances are usually only accessible using ssh over a EC2 instance (ssh tunneling).

Before being able to connect to an AWS RDS instance, you'll need to gather a bunch of information and files.

- Access to an EC2 instance server, you'll need an ssh key pair and identify the ssh user to use with that key to connect on the server and open an ssh tunnel to the RDS instance. In general to identify which user to use you need to know the type of platform that is running your EC2 instance (Amazon Linux, Ubuntu, ...).  You can find this information in the ![Instance Details tab](<lib/RDS%20SSH%20EC2%20Instance%20Details%20Tab.png>).  In general when your instance runs Ubuntu the user will be '''ubuntu''' but otherwise it's most of the time '''ec2-user'''.
- The database endpoint to use as the host (and port, usually 5432 like any PostgreSQL).
- The SSL certificate authority bundle used by AWS to encrypt/decrypt all communications.

&nbsp;

In the Hackolade connection settings dialog, give a meaningful name to the connection, then set the the host and port, and an optional database name if you wish to limit the scope of the discovery.

&nbsp;

![PostgreSQL connection settings](<lib/PostgreSQL%20connection%20settings.png>)

&nbsp;

Also enter the username and password to access the database.

&nbsp;

![Image](<lib/MariaDB%20connection%20settings%20auth.png>)

&nbsp;

Then setup SSL/TLS that must be enabled with full-verify mode for both RDS PostgreSQL and Aurora PostgreSQL.  You can find the AWS global certificate bundle ![here](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.SSL.html#UsingWithRDS.SSL.CertificatesDownload).
Note that only the certificate authority field needs to be field in order to setup SSL properly for full-verify mode.

&nbsp;

![Image](<lib/RDS%20SSL%20connection%20settings%20auth.png>)

&nbsp;

Then finally setup the SSH tunneling using your EC2 instance connection details and Key pair (.pem or .ppk).

&nbsp;

![Image](<lib/RDS%20SSH%20connection%20settings%20auth.png>)

You should be able to Test the connection.

Note:  It might be that your RDS instance can be directly accessible without using an SSH tunnel through an EC2 instance (in that case just disable the SSH option in your connection), 
