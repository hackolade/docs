# Kerberos

## Authentication

&nbsp;

Hackolade also supports the Kerberos authentication mechanism. For more info on how to setup Kerberos in HBase, please consult this [link](<http://hbase.apache.org/0.94/book/security.html#hbase.secure.configuration> "target=\"\_blank\"") and this useful [article](<https://blog.cloudera.com/blog/2012/09/understanding-user-authentication-and-authorization-in-apache-hbase/> "target=\"\_blank\"").

&nbsp;

The Kerberos parameters for HBase are maintained in Hackolade as follows:

![Image](<lib/HBase%20connection%20Kerberos.png>)

&nbsp;

&nbsp;

A Kerberos principal is a unique identity to which Kerberos can assign tickets.

&nbsp;

Principals can have an arbitrary number of components. Each component is separated by a component separator, generally /. The last component is the realm, separated from the rest of the principal by the realm separator, generally @.

&nbsp;

An example for a Kerberos Principal is: primary/instance@REALM.

&nbsp;

A Kerberos Service Name is the name by which a client uniquely identifies an instance of a service.Typically, the service name for an instance is named hbase. Provide another name here if your HBase instance was set up with a different service name.

&nbsp;

The **service principal** must be in the form: service@\<hostname\>. (Otherwise, if you only pass the hostname (also called fqdn - fully qualified domain name), it would default to HTTP@fqdn. And it would be resolved to the corresponding principal service/\<hostname\>@REALM by the GSS-API, which is not desirable, cfr this [page](<https://developer.ibm.com/hadoop/2016/05/12/hbase-rest-gateway-security/> "target=\"\_blank\"").)

&nbsp;

The minimum requirements to be able to connect with the Kerberos protocol are:

* Name of a host must always be the same as a computer host (hostname -f)
* Add to the "hbase-site.xml" the following parameters:\
\<property\>

   &nbsp; &nbsp; &nbsp; \<name\>hadoop.proxyuser.HTTP.groups\</name\>

   &nbsp; &nbsp; &nbsp; \<value\>\*\</value\>

\</property\>

\<property\>

&nbsp;   \<name\>hadoop.proxyuser.HTTP.hosts\</name\>

&nbsp;   \<value\>\*\</value\>

\</property\>

* All layers of Hadoop must be set up with Kerberos auth
* Yarn must be set up with SSL certificates
* Kerberos or Kerberos packages *“krb5-admin-server”* and *“krb5-kdc”* must be installed and run
* HBase REST service must be running&nbsp; REST should have administrative access. One can provide it by running HBASE command: *grant 'rest\_server', 'RWCA' *\
[https://hbase.apache.org/book.html#\_client\_side\_configuration\_for\_secure\_operation\_rest\_gateway](<https://hbase.apache.org/book.html#\_client\_side\_configuration\_for\_secure\_operation\_rest\_gateway> "target=\"\_blank\"")

&nbsp;

Instructions:

1. Start Kerberos services:
   1. service krb5-admin-server start
   1. service krb5-kdc start
1. Start HBase with Kerberos:
   1. Hadoop (dfs.sh, yarn.sh)
   1. Zookeeper (zkServer.sh)
   1. HBase (start-hbase.sh)
   1. HBase Rest (hbase rest start)
1. Obtains and caches an initial ticket-granting ticket for principal:
   1. kinit hbase@EXAMPLE.COM (pass:\<password\>)
   1. klist - (check if ticket received)
1. Check by curl request:
   1. curl -i --negotiate -u : http://\<host\>:\<port\>/version/cluster
   1. curl -i --negotiate -u : http://\<host\>:\<port\>/namespaces

&nbsp;

For more information with Hortonworks installations, click [here](<https://community.hortonworks.com/articles/91425/howto-start-and-test-hbase-rest-server-in-a-kerber.html> "target=\"\_blank\"").

