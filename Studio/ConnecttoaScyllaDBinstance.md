# Connect to a ScyllaDB instance

Like many database, ScyllaDB provides user rolenames and passwords for internal authentication.&nbsp; Hackolade currently supports basic authentication (username/password) as well as LDAP.

&nbsp;

To connect to a ScyllaDB instance, whether on-premises or Cloud, you need to provide:

\- the hosts IP address or DNS name, and port number

\- a localDataCenter, if necessary to prevent routing requests to nodes in remote data centers.

&nbsp;

![Image](<lib/ScyllaDB%20connection%20settings.png>)

&nbsp;

In the Advanced tab you may change the default request timeout and specify it in milliseconds.

![Image](<lib/Cassandra%20connection%20advanced%20tab.png>)

&nbsp;

The documentation on [this page](<https://docs.datastax.com/en/developer/nodejs-driver/4.5/api/type.ClientOptions/> "target=\"\_blank\"") indicates:&nbsp; “the timeout settings used on the Cassandra side (\*\_request\_timeout\_in\_ms in cassandra.yaml) should be taken into account when picking a value for this read timeout. You should pick a value a couple of seconds greater than the Cassandra timeout settings.”

