# LDAP

## Authentication

&nbsp;

If you require LDAP authentication, it is necessary, in order to connect to nodes via a secure connection, to select the SSL type.&nbsp; There are 2 ways to leverage the Java Keystore (JKS): accessing the JKS directly, or using certificates issued from the keystore.

&nbsp;

## &#49;) Accessing the keystore directly

Specify the path and filename to keystore, the access password, and the alias name for the ScyllaDB instance.

&nbsp;

![Image](<lib/Cassandra%20Connection%20Settings%20-%20LDAP%20JKS.png>)

&nbsp;

## &#50;) Convert the keystore and truststore into [PEM keys](<https://en.wikipedia.org/wiki/Privacy-Enhanced\_Mail> "target=\"\_blank\"")

&nbsp;

Assuming scyllaDB server config (cassandra.yaml):

&nbsp;

&nbsp;client\_encryption\_options:

  enabled: true

  keystore: keystore.jks

  keystore\_password: \*\*\*\*\*\*\*

  truststore: truststore.jks

  truststore\_password: \*\*\*\*\*\*

  require\_client\_auth: true

&nbsp;

1. Install java if you don't have it: [https://www.java.com/en/download/](<https://www.java.com/en/download/> "target=\"\_blank\"")
1. Install openssl: [https://wiki.openssl.org/index.php/Binaries](<https://wiki.openssl.org/index.php/Binaries> "target=\"\_blank\"")
   1. Linux: sudo apt-get install openssl
   1. MacOS: brew install openssl
   1. Windows: [https://slproweb.com/products/Win32OpenSSL.html](<https://slproweb.com/products/Win32OpenSSL.html> "target=\"\_blank\"")
1. Find out alias used by keystore

Run the following command to find out what alias is used by keystore:

\> keytool -v -list -keystore keystore.jks

where keystore.jks is the java key store file granting access to the scyllaDB instance

alias will be in the section “Alias name”

1. Generate PKS key

\> keytool -importkeystore -srckeystore keystore.jks -destkeystore myapp.p12 -srcalias myapp-dev -srcstoretype jks -deststoretype pkcs12

keystore.jks - the java key store file granting access to the scyllaDB instance

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

![Image](<lib/Cassandra%20Connection%20Settings%20-%20LDAP%20Certific.png>)

