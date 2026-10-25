# LDAP

If you require LDAP authentication, it is necessary, in order to connect to nodes via a secure connection, to select the SSL type. There are 2 ways to leverage the Java Keystore (JKS): accessing the JKS directly, or using certificates issued from the keystore.

&nbsp;

## Accessing the keystore directly

Specify the path and filename to keystore, the access password, and the alias name for the ScyllaDB instance.

&nbsp;

![ScyllaDB Connection Settings - LDAP JKS](<lib/Cassandra Connection Settings - LDAP JKS.png>)

&nbsp;

## Convert the keystore and truststore into [PEM keys](<https://en.wikipedia.org/wiki/Privacy-Enhanced_Mail> "target=\"_blank\"")

Assuming scyllaDB server config (cassandra.yaml):

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
where `keystore.jks` is the java key store file granting access to the scyllaDB instance\
alias will be in the section “Alias name”

3. Generate PKS key

&nbsp;

```bash
> keytool -importkeystore -srckeystore keystore.jks -destkeystore myapp.p12 -srcalias myapp-dev -srcstoretype jks -deststoretype pkcs12
```

&nbsp;

`keystore.jks` - the java key store file granting access to the scyllaDB instance\
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

![ScyllaDB Connection Settings - LDAP Certific](<lib/Cassandra Connection Settings - LDAP Certific.png>)
