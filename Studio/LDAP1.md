# LDAP

## LDAP Authentication

Hackolade can connect via LDAP authentication through either “binary” or "http" transport mode. The following properties should be set up:

&nbsp;

```xml
<property>
  <name>hive.server2.authentication</name>
  <value>ldap</value>
</property>
<property>
  <name>hive.server2.authentication.ldap.url</name>
  <value>LDAP_URL</value>
</property>
<property>
  <name>hive.server2.authentication.ldap.baseDN</name>
  <value>LDAP_BASE_DN</value>
</property>
<property>
  <name>hive.server2.authentication.ldap.userDNPattern</name>
  <value>LDAP_DN_PATTERN</value>
</property>
```

&nbsp;

Where:

- ***LDAP_URL*** *-* URL of LDAP server (e.g. ldap://localhost:389)
- ***LDAP_BASE_DN*** - base distinguish name of users (e.g. dc=hackolade,dc=com)
- ***LDAP_DN_PATTERN*** *-* pattern for matching users (e.g. CN=%s,DC=hackolade,DC=com). By default users are matched by uid.

&nbsp;

In Hackolade set “User Name” and “Password”:\
![Hive - LDAP Connection Settings](<lib/Hive - LDAP Connection Settings.png>)
