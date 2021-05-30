# Connect to a Hive instance

Hive can be configured to provide User Authentication, which ensures that only authorized users can communicate with Hive. &nbsp;

&nbsp;

The Hackolade connection settings must match the [configuration of the hive-site.xml](<https://cwiki.apache.org/confluence/display/Hive/AdminManual%20Configuration> "target=\"\_blank\"") for the [HiveServer2 setup](<https://cwiki.apache.org/confluence/display/Hive/Setting%20Up%20HiveServer2> "target=\"\_blank\"") where:

* ***HOST*** is a host name of the machine Hive is running on (e.g. *localhost, 0.0.0.0, hive.company.com etc.*).
* According to the mode option, either ***BINARY\_PORT*** or ***HTTP\_PORT*** is set up (by default they are *10000* and *10001* accordingly).
* The **authentication parameter** must be "none", “*nosasl”, "ldap", or "kerberos"*
* ***MODE*** is the transport mode for Thrift protocol. It can be “http” or “binary”.
* **HTTP\_PATH** is the option to define a URI to the hive server (e.g. if *HTTP\_PATH* is *hive2* the URI of Hive server will be *http://localhost:10001/hive2*).

&nbsp;

Besides proper connection, the application requires, for proper reverse-engineering, that the credentials have **sufficient rights to execute these queries:**

describe formatted \<table\>

describe extended \<table\>

select \* from \<table\> limit 1

&nbsp;

&nbsp;

## &#49;) Host name and port number

In the connection tab, first give a friendly name to the connection settings.&nbsp; This name is only used in Hackolade to help manage multiple connections.

&nbsp;

![Image](<lib/Hive%20-%20Connection%20settings.png>)

&nbsp;

***TIP***: if you have instances with a very large number of databases, you may wish to declare a particular database directly in the connection string by providing the database name and restrict the scope of discovery.

&nbsp;

&nbsp;

Set the host name of the machine the Hive is running (e.g. *localhost, 0.0.0.0, hive.example.com etc.*)&nbsp; corresponding to:

\<property\>

\<name\>hive.server2.thrift.bind.host\</name\>

\<value\>***hive.example.com***\</value\>

\</property\>

&nbsp;

If in binary transport mode, the port number must correspond to the port number in:

\<property\>

\<name\>hive.server2.thrift.port\</name\>

\<value\>***10001***\</value\>

\</property\>

&nbsp;

&nbsp;

If in http transport mode, the port number must correspond to the port number in:

\<property\>

\<name\>hive.server2.thrift.http.port\</name\>

\<value\>***10001***\</value\>

\</property\>

&nbsp;

&nbsp;

## &#50;) Authentication type

You may choose between the following protocols:

\- [None (Plain SASL)](<NonePlainSASL.md>)

\- [NoSASL](<NoSASL.md>)

\- [LDAP](<LDAP1.md>)

\- [Kerberos](<Kerberos1.md>)

&nbsp;

&nbsp;

## &#51;) Transport mode

In the options tab, choose the [transport mode](<https://cwiki.apache.org/confluence/display/Hive/Configuration%20Properties#ConfigurationProperties-hive.server2.transport.mode> "target=\"\_blank\""), either binary (default) or http. &nbsp;

&nbsp;

\<property\>

\<name\>hive.server2.transport.mode\</name\>

\<value\>***MODE***\</value\>

\</property\> &nbsp;

&nbsp;

&nbsp;

![Image](<lib/Hive%20-%20Connection%20options.png>)

&nbsp;

Http transport mode is available for all transport types (Plain SASL, NoSASL, LDAP or Kerberos.)&nbsp; If the chosen transport mode is http, then the [HTTP path](<https://cwiki.apache.org/confluence/display/Hive/HiveServer2%20Clients#HiveServer2Clients-ConnectionURLWhenHiveServer2IsRunninginHTTPMode> "target=\"\_blank\"") must be specified:

\<property\>

\<name\>hive.server2.thrift.http.path\</name\>

\<value\>***hive2***\</value\>

\</property\>

&nbsp;

![Image](<lib/Hive%20connection%20options%20http.png>)

## &#52;) SSL

Hackolade is able to connect to Hive via SSL connection with all of the authentication types: “None (PlainSASL)”, "NoSASL", “LDAP” and “Kerberos”. Hive uses the following configuration in the *hive-site.xml* file:

\<property\>

\<name\>hive.server2.use.SSL\</name\>

\<value\>true\</value\>

\</property\>

\<property\>

\<name\>hive.server2.keystore.path\</name\>

\<value\>*PATH\_TO\_JKS\_FILE*\</value\>

\</property\>

\<property\>

\<name\>hive.server2.keystore.password\</name\>

\<value\>*PASSWORD\_FOR\_JKS\_FILE*\</value\>

\</property\>

&nbsp;

## &#52;a) Using HTTPs

If the certificate is not installed locally, you must get a copy of the certificate(s) and reference them in the Certificate Authority field:&nbsp;

![Image](<lib/Hive%20connection%20settings%20SSL-HTTPs.png>)

You may declare multiple certificates, separated by a comma. &nbsp;

&nbsp;

Alternatively, you may concatenate the certificates into a single file, and the result should look like this:

\-----BEGIN CERTIFICATE-----

…

\-----END CERTIFICATE-----

\-----BEGIN CERTIFICATE-----

…

\-----END CERTIFICATE-----

&nbsp;

&nbsp;

### *&#52;b)* Accessing the keystore directly

Specify the path and filename to keystore, the access password, and the alias name for the Hive instance.

![Image](<lib/Hive%20-%20Connection%20settings%20Java%20Keystore.png>)

&nbsp;

### &#52;c) Convert the keystore into [PEM keys](<mailto:https://en.wikipedia.org/wiki/Privacy-Enhanced\_Mail>).&nbsp;

&nbsp;

The following instruction shows how to convert JKS (java key store) certificate to PEM:

&nbsp;

1. Install java if you don't have it: [https://www.java.com/en/download/](<https://www.java.com/en/download/>)
1. Install openssl: [https://wiki.openssl.org/index.php/Binaries](<https://wiki.openssl.org/index.php/Binaries>)
   1. Linux: sudo apt-get install openssl
   1. MacOS: brew install openssl
   1. Windows: [https://slproweb.com/products/Win32OpenSSL.html](<https://slproweb.com/products/Win32OpenSSL.html>)
1. Find out alias used by keystore

Run the following command to find out what alias is used by keystore:

\> keytool -v -list -keystore keystore.jks

where keystore.jks is the java key store file granting access to the cassandra instance

alias will be in the section “Alias name”

1. Generate PKS key

\> keytool -importkeystore -srckeystore keystore.jks -destkeystore myapp.p12 -srcalias myapp-dev -srcstoretype jks -deststoretype pkcs12

keystore.jks - the java key store file granting access to the hive instance

myapp.p12 - intermediate PKS key

myapp-dev - alias used by keystore and determined in step 3 above

      5. Generate CA key

\> keytool -importkeystore -srckeystore truststore.jks -destkeystore trust.p12 -srcalias myapp-dev -srcstoretype jks -deststoretype pkcs12

      6. Generate .pem key

\> openssl pkcs12 -in myapp.p12 -nokeys -out myapp.pem

\> openssl pkcs12 -in trust.p12 -nokeys -out ca.pem

\> openssl pkcs12 -in myapp.p12 -nodes -nocerts -out myapp.key

&nbsp;

      7. Use generated files in Hackolade:

“Certificate Authority”: *ca.pem*

“Client Certificate”: *myapp.pem*

“Client Private Key”: *myapp.key*

&nbsp;

&nbsp;

![Image](<lib/Hive%20-%20Connection%20settings%20SSL.png>)

&nbsp;

More information can be found [here](<https://cwiki.apache.org/confluence/display/Hive/Setting%20Up%20HiveServer2#SettingUpHiveServer2-SSLEncryption> "target=\"\_blank\"").

