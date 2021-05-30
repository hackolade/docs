# LDAP

## Authentication

&nbsp;

If you require LDAP authentication, it is necessary, in order to connect to the DSE nodes via a secure connection, to select the SSL type.&nbsp; A keystore contains client certificate and client key.&nbsp; Whereas a truststore contains certificate authority (CA).

&nbsp;

There are different ways to leverage the Java Keystore (JKS):

1. Keystore info only: if the server doesn’t need truststore, the application assumes that client certificate is the certificate authority.&nbsp; The application retrieves the client certificate and key from the keystore, and uses certificate as CA.&nbsp;
1. Truststore info only: if the server doesn’t require a keystore, but requires a truststore, then the application takes only the certificate authority from the truststore, and connects without client certificate and key
1. Both keystore and truststore: if the server requires both a keystore and a truststore, then the application takes the certificate authority from the truststore, plus the client certificate and key from the keystore.

&nbsp;

Alternatively, you may use certificates issued from the keystore.

&nbsp;

The system assumes that users have installed Java JDK from [here](<https://www.oracle.com/be/java/technologies/javase/javase-jdk8-downloads.html> "target=\"\_blank\""), and that the JAVA\_HOME variable points at the folder where java was installed. It is recommended to use Java 8.

\
Our module for decrypting JKS uses the following logic to find java home:

1. check for JAVA\_HOME
1. on Windows, query the Registry
1. If neither of the previous methods worked, then scan the PATH for javac
1. On mac, the parent directory of javac is checked for a java\_home binary. If that binary exists then it is executed and the result is used
1. The grandparent directory of javac is used. This is similar to $(dirname $(dirname $(readlink $(which javac))))

&nbsp;

## &#49;) Accessing the keystore&nbsp;

Specify the path and filename to keystore, the access password, and the alias name for the Cassandra instance.

&nbsp;

![Image](<lib/Cassandra%20Connection%20Settings%20-%20LDAP%20JKS.png>)

&nbsp;

The Alias Name is mandatory.&nbsp; If you don't know it, it can be found out by the following command:

&nbsp;

*keytool -v -list -keystore \<jks file\>*

&nbsp;

The alias can be found in the section “Alias name”.&nbsp; If no alias was set, you should use the default "mykey".

&nbsp;

## &#50;) Accessing the truststore

If necessary, you may also declare truststore parameters:

&nbsp;

![Image](<lib/Cassandra%20Connection%20Settings%20-%20LDAP%20truststo.png>)

&nbsp;

You may consult [this page](<https://docs.datastax.com/en/security/6.7/security/secSslCertificatesKeystores.html> "target=\"\_blank\"") for more info, as well as the full keytool [specification](<https://docs.oracle.com/javase/8/docs/technotes/tools/windows/keytool.html> "target=\"\_blank\"").

&nbsp;

## &#51;) Accessing both the keystore and the truststore

Enter the parameters according to both 1) and 2) above.

&nbsp;

&nbsp;

## &#52;) Convert the keystore and truststore into [PEM keys](<https://en.wikipedia.org/wiki/Privacy-Enhanced\_Mail> "target=\"\_blank\"")

&nbsp;

Assuming cassandra server config (cassandra.yaml):

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

where keystore.jks is the java key store file granting access to the cassandra instance

alias will be in the section “Alias name”

1. Generate PKS key

\> keytool -importkeystore -srckeystore keystore.jks -destkeystore myapp.p12 -srcalias myapp-dev -srcstoretype jks -deststoretype pkcs12

keystore.jks - the java key store file granting access to the cassandra instance

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

