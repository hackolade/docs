# SSL

In cases where the server and client exist on separate networks or they are in a high-risk network, the lack of encryption does introduce security concerns as a malicious actor could potentially eavesdrop on the traffic as it is sent over the network between them.

To mitigate this concern, SQL Server allows you to encrypt data in transit between the server and clients using the Transport Layer Security (TLS) protocol. TLS was formerly known as Secure Socket Layer (SSL), but strictly speaking the SSL protocol is a predecessor to TLS and, that version of the protocol is now considered insecure. The documentation still uses the term SSL often and for compatibility reasons TLS-related server system

In order to secure connections between the server and client, you need to ensure that your server was compiled with TLS support. &nbsp;

&nbsp;

![SQL Server connection SSL](<lib/MongoDB connection SSL.png>)

&nbsp;

Depending on the setup, one or more of the following fields will need to reference the appropriate file:

## Certificate Authority

For production use, your SQL Server deployment should use valid certificates generated and signed by a single certificate authority. You or your organization can generate and maintain an independent certificate authority, or use certificates generated by a third-party SSL vendor.

&nbsp;

To verify the identity of the SQL Server deployment you connect to, provide one or more certificates of trusted Certificate Authorities.

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

&nbsp;

## Troubleshooting

If you get a message on screen or in the HackoladeRE.log saying "Failed to connect - unable to get local issuer certificate".&nbsp; This is caused by the fact that your organization might be using self-signed certificates (often in the context of dev or test environments -- rarely in prod environments...) and this self-signed certificate is not present in the local certificate storage.&nbsp; This situation and the solution are well described in this [Microsoft link](<https://learn.microsoft.com/en-us/troubleshoot/sql/database-engine/connect/error-message-when-you-connect> "target=\"\_blank\"").

&nbsp;

