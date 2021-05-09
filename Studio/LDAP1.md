# LDAP

## LDAP Authentication ##

&nbsp;

Hackolade can connect via LDAP authentication through either “binary” or "http" transport mode. The following properties should be set up:

&nbsp;

\<property\>

\<name\>hive.server2.authentication\</name\>

\<value\>**ldap**\</value\>

\</property\>

\<property\>

\<name\>hive.server2.authentication.ldap.url\</name\>

\<value\>***LDAP\_URL***\</value\>

\</property\>

\<property\>

\<name\>hive.server2.authentication.ldap.baseDN\</name\>

\<value\>***LDAP\_BASE\_DN***\</value\>

\</property\>

\<property\>

\<name\>hive.server2.authentication.ldap.userDNPattern\</name\>

\<value\>***LDAP\_DN\_PATTERN***\</value\>

\</property\>

&nbsp;

Where:

\- ***LDAP\_URL** -* URL of LDAP server (e.g. ldap://localhost:389)

***\- LDAP\_BASE\_DN*** - base distinguish name of users (e.g. dc=hackolade,dc=com)

***\- LDAP\_DN\_PATTERN** -* pattern for matching users (e.g. CN=%s,DC=hackolade,DC=com). By default users are matched by uid.

&nbsp;

In Hackolade set “User Name” and “Password”:

![Image](<lib/Hive%20-%20LDAP%20Connection%20Settings.png>)


***
_Created with the Personal Edition of HelpNDoc: [Write eBooks for the Kindle](<https://www.helpndoc.com/feature-tour/create-ebooks-for-amazon-kindle>)_
