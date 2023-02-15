# Connect to a Teradata instance

**Important:** when forward-engineering a Teradata instance, the (Teradata) user used to connect to the target instance should have access to read **SYSUDTLIB** system database to retrieve DDL scripts for UDT, UDM etc...

More information is available [here](<https://docs.teradata.com/r/Enterprise_IntelliFlex_VMware/Teradata-VantageTM-SQL-Data-Definition-Language-Syntax-and-Examples-17.20/Table-Statements/CREATE-TABLE-and-CREATE-TABLE-AS> "target=\"\_blank\"").

&nbsp;

The Teradata instance can be hosted on-premises, or on virtualized machines in a private or public cloud. &nbsp;

&nbsp;

In the Hackolade connection settings dialog, give a meaningful name to the connection, then set the the host and port, and an optional database name if you wish to limit the scope of the discovery.

&nbsp;

![Teradata connection settings](<lib/Teradata%20connection%20settings.png>)

&nbsp;

If required, you may enter your username and password

&nbsp;

![Image](<lib/Teradata%20connection%20settings%20auth.png>)
