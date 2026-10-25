# LDAP

If you require LDAP authentication, it is necessary, in order to connect to the DSE nodes via a secure connection, to select the SSL type. A keystore contains client certificate and client key. Whereas a truststore contains certificate authority (CA).

&nbsp;

There are different ways to leverage the Java Keystore (JKS):

1. Keystore info only: if the server doesn’t need truststore, the application assumes that client certificate is the certificate authority. The application retrieves the client certificate and key from the keystore, and uses certificate as CA.
2. Truststore info only: if the server doesn’t require a keystore, but requires a truststore, then the application takes only the certificate authority from the truststore, and connects without client certificate and key
3. Both keystore and truststore: if the server requires both a keystore and a truststore, then the application takes the certificate authority from the truststore, plus the client certificate and key from the keystore.

&nbsp;

Alternatively, you may use certificates issued from the keystore.

&nbsp;

## Accessing the keystore

Specify the path and filename to keystore, the access password, and the alias name for the Cassandra instance.

&nbsp;

![Cassandra Connection Settings - LDAP JKS](<lib/Cassandra Connection Settings - LDAP JKS.png>)

&nbsp;

The Alias Name is mandatory. If you don't know it, it can be found out by the following command:

&nbsp;

*keytool -v -list -keystore \<jks file>*

&nbsp;

The alias can be found in the section “Alias name”. If no alias was set, you should use the default "mykey".

&nbsp;

## Accessing the truststore

If necessary, you may also declare truststore parameters:

&nbsp;

![Cassandra Connection Settings - LDAP truststo](<lib/Cassandra Connection Settings - LDAP truststo.png>)

&nbsp;

You may consult [this page](<https://docs.datastax.com/en/security/6.7/security/secSslCertificatesKeystores.html> "target=\"_blank\"") for more info, as well as the full keytool [specification](<https://docs.oracle.com/javase/8/docs/technotes/tools/windows/keytool.html> "target=\"_blank\"").

&nbsp;

## Accessing both the keystore and the truststore

Enter the parameters according to both 1) and 2) above.

&nbsp;

## Convert the keystore and truststore into [PEM keys](<https://en.wikipedia.org/wiki/Privacy-Enhanced_Mail> "target=\"_blank\"")

Assuming cassandra server config (cassandra.yaml):

&nbsp;

```yaml
client_encryption_options:
 enabled: true
 keystore: keystore.jks
 keystore_password: *******
 truststore: truststore.jks
 truststore_password: ******
 require_client_auth: true
```

&nbsp;

1. Install java if you don't have it: [https://www.java.com/en/download/](<https://www.java.com/en/download/> "target=\"_blank\"")
2. Install openssl: [https://wiki.openssl.org/index.php/Binaries](<https://wiki.openssl.org/index.php/Binaries> "target=\"_blank\"")
   1. Linux: `sudo apt-get install openssl`
   2. MacOS: `brew install openssl`
   3. Windows: [https://slproweb.com/products/Win32OpenSSL.html](<https://slproweb.com/products/Win32OpenSSL.html> "target=\"_blank\"")
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

`keystore.jks` - the java key store file granting access to the cassandra instance\
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

![Cassandra Connection Settings - LDAP Certificate](<lib/Cassandra Connection Settings - LDAP Certific.png>)
