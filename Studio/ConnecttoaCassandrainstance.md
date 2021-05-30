# Connect to a Cassandra instance

Like many database, Cassandra provides user rolenames and passwords for internal authentication.&nbsp; Hackolade currently supports basic authentication (username/password) as well as LDAP.

&nbsp;

To connect to a Cassandra instance, you need to provide:

\- the hosts IP address or DNS name, and port number

\- your choice of installation: private or Astra on Constellation

\- for Cassandra 4.0 and higher, it is now required to provide a localDataCenter. This is necessary to prevent routing requests to nodes in remote data centers.

&nbsp;

![Image](<lib/Cassandra%20connection%20settings.png>)

&nbsp;

In the Advanced tab you may change the default request timeout and specify it in milliseconds.

![Image](<lib/Cassandra%20connection%20advanced%20tab.png>)

&nbsp;

## Troubleshooting

&nbsp;

The documentation on [this page](<https://docs.datastax.com/en/developer/nodejs-driver/4.5/api/type.ClientOptions/> "target=\"\_blank\"") indicates:&nbsp; “the timeout settings used on the Cassandra side (\*\_request\_timeout\_in\_ms in cassandra.yaml) should be taken into account when picking a value for this read timeout. You should pick a value a couple of seconds greater than the Cassandra timeout settings.”

&nbsp;

If the error says that host is not available, "NoHostAvailableError: All host(s) tried for query failed. First host tried, 172.17.0.2:9042: DriverError: Connection timeout", it means the host 172.17.0.2 is not in the network or port 9042 is not opened.&nbsp; Check availability of host, for example using netcat:

&nbsp;

*nc -z -v 172.17.0.2 9042*

&nbsp;

*Also,* check the firewall settings.&nbsp;

&nbsp;

&nbsp;

If trying to connect to a *Dockerized* Cassandra instance, we can suggest the following actions:

&#49;) Check if port is published by running the command&nbsp;

&nbsp;

*docker ps*

&nbsp;

in PORTS columns the should see *0.0.0.0:9042:9042*

&nbsp;

To publish port they should use parameter **-p**

&nbsp;

*docker run -p 9042:9042 cassandra*

&nbsp;

&#50;) Use localhost (or 127.0.0.1) instead of 172.17.0.2, as it is an internal IP address. Or in case docker-toolbox is used, get ip with this command:

&nbsp;

*docker-machine ip*

&nbsp;

