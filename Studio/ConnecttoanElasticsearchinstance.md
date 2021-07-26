# Connect to an Elasticsearch instance

From version 5.0 onward, Shield is part of X-Pack.&nbsp; For more information, see Securing Elasticsearch in the [X-Pack Reference](<https://www.elastic.co/guide/en/x-pack/current/xpack-security.html> "target=\"\_blank\"").&nbsp; Hackolade currently supports basic authentication (username/password) and SSL.&nbsp; Other authentication methods, such as LDAP, PKI, and User Directory Authentication are not supported yet.

&nbsp;

The Connection Settings dialog lets define the parameters in different tabs, as needed:

![Image](<lib/Elasticsearch%20-%20connection%20settings.png>)

These parameters are assembled by Hackolade to create the full connection string when establishing the connection during the Reverse-Engineering process.

&nbsp;

Enter the required username and password:

![Image](<lib/Elasticsearch%20-%20authentication.png>)

&nbsp;

## Authority Certificate

For production use, your Elasticsearch deployment should use valid certificates generated and signed by a single certificate authority. You or your organization can generate and maintain an independent certificate authority, or use certificates generated by a third-party SSL vendor.

&nbsp;

To verify the identity of the Elasticsearch deployment you connect to, provide one or more certificates of trusted Certificate Authorities.

&nbsp;

Typical file extensions for the certificate are .crt or .pem.

![Image](<lib/Elasticsearch%20-%20SSL.png>)
