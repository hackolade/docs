# LDAP

MongoDB Enterprise provides support for proxy authentication of users. This allows administrators to configure a MongoDB cluster to authenticate users by proxying authentication requests to a specified Lightweight Directory Access Protocol (LDAP) service.

&nbsp;

LDAP support for user authentication requires proper configuration of the saslauthd daemon process as well as the MongoDB server.&nbsp; For more info, consult this [link](<https://docs.mongodb.com/manual/tutorial/configure-ldap-sasl-openldap/> "target=\"\_blank\"").

&nbsp;

In Hackolade, the address of the LDAP server and port number need to be specified in the Connection tab:

&nbsp;

![Image](<lib/MongoDB%20connection%20LDAP%201.png>)

&nbsp;

Then select LDAP in the authentication dropdown box, before specifying the username and password:

&nbsp;

![Image](<lib/MongoDB%20connection%20LDAP%202.png>)

