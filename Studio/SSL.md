# SSL

MongoDB supports SSL certificate authentication for client authentication and internal authentication of the members of replica sets and sharded clusters.&nbsp; x.509 certificate authentication requires a secure TLS/SSL connection.&nbsp; For more info, please consult [https://docs.mongodb.com/manual/tutorial/configure-ssl/](<https://docs.mongodb.com/manual/tutorial/configure-ssl/> "target=\"\_blank\"")

&nbsp;

![MongoDB connection SSL](<lib/MongoDB connection SSL.png>)

&nbsp;

Depending on the setup, one or more of the following fields will need to reference the appropriate file:

## Certificate Authority

For production use, your MongoDB deployment should use valid certificates generated and signed by a single certificate authority. You or your organization can generate and maintain an independent certificate authority, or use certificates generated by a third-party SSL vendor.

&nbsp;

To verify the identity of the MongoDB deployment you connect to, provide one or more certificates of trusted Certificate Authorities.

&nbsp;

## Client Certificate

If the server is configured to perform certificate validation, you need to provide a certificate here to identify yourself to the server.

&nbsp;

Typical file extensions for the certificate are .crt or .pem.

&nbsp;

## Client Private Key

If the server is configured to perform certificate validation, you need to provide the private key here to identify yourself to the server.

&nbsp;

Typical file extensions for the private key are .key or .pem.

&nbsp;

## Private Key Password

A private key can optionally be encrypted with a password.

&nbsp;

If your private key is password protected, enter the password here. If not, leave the field blank.

