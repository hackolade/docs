# Connect to a Hive instance

Hive can be configured to provide User Authentication, which ensures that only authorized users can communicate with Hive.

&nbsp;

The Hackolade connection settings must match the [configuration of the hive-site.xml](<https://cwiki.apache.org/confluence/display/Hive/AdminManual+Configuration> "target=\"_blank\"") for the [HiveServer2 setup](<https://cwiki.apache.org/confluence/display/Hive/Setting+Up+HiveServer2> "target=\"_blank\"") where:

- ***HOST*** is a host name of the machine Hive is running on (e.g. *localhost, 0.0.0.0, hive.company.com etc.*).
- According to the mode option, either ***BINARY_PORT*** or ***HTTP_PORT*** is set up (by default they are *10000* and *10001* accordingly).
- The **authentication parameter** must be "none", “*nosasl”, "ldap", or "kerberos"*
- ***MODE*** is the transport mode for Thrift protocol. It can be “http” or “binary”.
- **HTTP_PATH** is the option to define a URI to the hive server (e.g. if *HTTP_PATH* is *hive2* the URI of Hive server will be *http://localhost:10001/hive2*).

&nbsp;

Besides proper connection, the application requires, for proper reverse-engineering, that the credentials have **sufficient rights to execute these queries:**\
describe formatted \<table>\
describe extended \<table>\
select \* from \<table> limit 1

&nbsp;

## 1) Host name and port number

In the connection tab, first give a friendly name to the connection settings. This name is only used in Hackolade to help manage multiple connections.

&nbsp;

![Hive - Connection settings](<lib/Hive - Connection settings.png>)

&nbsp;

> [!TIP]
> If you have instances with a very large number of databases, you may wish to declare a particular database directly in the connection string by providing the database name and restrict the scope of discovery.

&nbsp;

Set the host name of the machine the Hive is running (e.g. *localhost, 0.0.0.0, hive.example.com etc.*) corresponding to:

&nbsp;

```xml
<property>
  <name>hive.server2.thrift.bind.host</name>
  <value>hive.example.com</value>
</property>
```

&nbsp;

If in binary transport mode, the port number must correspond to the port number in:

&nbsp;

```xml
<property>
  <name>hive.server2.thrift.port</name>
  <value>10001</value>
</property>
```

&nbsp;

If in http transport mode, the port number must correspond to the port number in:

&nbsp;

```xml
<property>
  <name>hive.server2.thrift.http.port</name>
  <value>10001</value>
</property>
```

&nbsp;

## 2) Authentication type

You may choose between the following protocols:

- [None (Plain SASL)](NonePlainSASL.md)
- [NoSASL](NoSASL.md)
- [LDAP](LDAP1.md)
- [Kerberos](Kerberos1.md)

&nbsp;

## 3) Transport mode

In the options tab, choose the [transport mode](<https://cwiki.apache.org/confluence/display/Hive/Configuration+Properties#ConfigurationProperties-hive.server2.transport.mode> "target=\"_blank\""), either binary (default) or http.

&nbsp;

```xml
<property>
  <name>hive.server2.transport.mode</name>
  <value>MODE</value>
</property>
```

&nbsp;

![Hive - Connection options](<lib/Hive - Connection options.png>)

&nbsp;

Http transport mode is available for all transport types (Plain SASL, NoSASL, LDAP or Kerberos.) If the chosen transport mode is http, then the [HTTP path](<https://cwiki.apache.org/confluence/display/Hive/HiveServer2+Clients#HiveServer2Clients-ConnectionURLWhenHiveServer2IsRunninginHTTPMode> "target=\"_blank\"") must be specified:

&nbsp;

```xml
<property>
  <name>hive.server2.thrift.http.path</name>
  <value>hive2</value>
</property>
```

&nbsp;

![Hive connection options http](<lib/Hive connection options http.png>)

&nbsp;

## 4) SSL

Hackolade is able to connect to Hive via SSL connection with all of the authentication types: “None (PlainSASL)”, "NoSASL", “LDAP” and “Kerberos”. Hive uses the following configuration in the *`hive-site.xml`* file:

&nbsp;

```xml
<property>
  <name>hive.server2.use.SSL</name>
  <value>true</value>
</property>
<property>
  <name>hive.server2.keystore.path</name>
  <value>PATH_TO_JKS_FILE</value>
</property>
<property>
  <name>hive.server2.keystore.password</name>
  <value>PASSWORD_FOR_JKS_FILE</value>
</property>
```

&nbsp;

### 4a) Using HTTPs

If the certificate is not installed locally, you must get a copy of the certificate(s) and reference them in the Certificate Authority field:\
![Hive connection settings SSL-HTTPs](<lib/Hive connection settings SSL-HTTPs.png>)\
You may declare multiple certificates, separated by a comma.

&nbsp;

Alternatively, you may concatenate the certificates into a single file, and the result should look like this:\
-----BEGIN CERTIFICATE-----\
…\
-----END CERTIFICATE-----\
-----BEGIN CERTIFICATE-----\
…\
-----END CERTIFICATE-----

&nbsp;

### 4b) Accessing the keystore directly

Specify the path and filename to keystore, the access password, and the alias name for the Hive instance.\
![Hive - Connection settings Java Keystore](<lib/Hive - Connection settings Java Keystore.png>)

&nbsp;

### 4c) Convert the keystore into [PEM keys](mailto:https://en.wikipedia.org/wiki/Privacy-Enhanced_Mail).

The following instruction shows how to convert JKS (java key store) certificate to PEM:

1. Install java if you don't have it: [https://www.java.com/en/download/](https://www.java.com/en/download/)
2. Install openssl: [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)
   1. Linux: `sudo apt-get install openssl`
   2. MacOS: `brew install openssl`
   3. Windows: [https://slproweb.com/products/Win32OpenSSL.html](https://slproweb.com/products/Win32OpenSSL.html)
3. Find out alias used by keystore

&nbsp;

Run the following command to find out what alias is used by keystore:\
\> keytool -v -list -keystore keystore.jks\
where `keystore.jks` is the java key store file granting access to the cassandra instance\
alias will be in the section “Alias name”

3. Generate PKS key

&nbsp;

```bash
> keytool -importkeystore -srckeystore keystore.jks -destkeystore myapp.p12 -srcalias myapp-dev -srcstoretype jks -deststoretype pkcs12
```

&nbsp;

`keystore.jks` - the java key store file granting access to the hive instance\
`myapp.p12` - intermediate PKS key\
`myapp-dev` - alias used by keystore and determined in step 3 above

&nbsp;

```bash
      5. Generate CA key
> keytool -importkeystore -srckeystore truststore.jks -destkeystore trust.p12 -srcalias myapp-dev -srcstoretype jks -deststoretype pkcs12
      6. Generate .pem key
> openssl pkcs12 -in myapp.p12 -nokeys -out myapp.pem
> openssl pkcs12 -in trust.p12 -nokeys -out ca.pem
> openssl pkcs12 -in myapp.p12 -nodes -nocerts -out myapp.key

      7. Use generated files in Hackolade:
```

&nbsp;

“Certificate Authority”: *ca.pem*\
“Client Certificate”: *myapp.pem*\
“Client Private Key”: *myapp.key*

&nbsp;

![Hive - Connection settings SSL](<lib/Hive - Connection settings SSL.png>)

&nbsp;

More information can be found [here](<https://cwiki.apache.org/confluence/display/Hive/Setting+Up+HiveServer2#SettingUpHiveServer2-SSLEncryption> "target=\"_blank\"").
