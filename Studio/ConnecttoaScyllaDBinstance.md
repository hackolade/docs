---
description: Connect Hackolade Studio to ScyllaDB on-premises or in the cloud with username and password or LDAP, for reverse-engineering.
seoTitle: Connect to a ScyllaDB instance
image: lib/ScyllaDB connection settings.png
---
# Connect to a ScyllaDB instance

Like many database, ScyllaDB provides user rolenames and passwords for internal authentication. Hackolade currently supports basic authentication (username/password) as well as LDAP.

To connect to a ScyllaDB instance, whether on-premises or Cloud, you need to provide:

- the hosts IP address or DNS name, and port number
- a localDataCenter, if necessary to prevent routing requests to nodes in remote data centers.

![ScyllaDB connection settings](<lib/ScyllaDB connection settings.png>)

In the Advanced tab you may change the default request timeout and specify it in milliseconds.\
![Cassandra connection advanced tab](<lib/Cassandra connection advanced tab.png>)

The documentation on [this page](<https://docs.datastax.com/en/developer/nodejs-driver/4.5/api/type.ClientOptions/> "target=\"_blank\"") indicates: “the timeout settings used on the Cassandra side (\*\_request_timeout_in_ms in cassandra.yaml) should be taken into account when picking a value for this read timeout. You should pick a value a couple of seconds greater than the Cassandra timeout settings.”
