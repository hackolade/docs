# Connect to a MarkLogic instance

Hackolade's reverse-engineering functions allows to discover the schema of documents in collections through a statistical sampling process, followed by a probabilistic inference operation, as described in [this page](<Reverseengineeranexistinginstanc.md>).

&nbsp;

MarkLogic uses a username and password for internal authentication.&nbsp; Hackolade currently supports basic authentication (username/password) with support of SSL certificates.

&nbsp;

To connect to a MarkLogic instance, you need to provide:

\- the hosts IP address or DNS name, and port number

\- your choice of document organization

\- optionally, the database to be fetched

![MarkLogi reverse-engineering connection settings](<lib/MarkLogi RE connection settings.png>)

&nbsp;

The credentials must be entered in the Authentication tab:

![Image](<lib/MarkLogic RE authentication tab.png>)

&nbsp;

Optionally, SSL can be enabled and a certificate provided for SSL inspection:

![Image](<lib/MarkLogic RE SSL tab.png>)

