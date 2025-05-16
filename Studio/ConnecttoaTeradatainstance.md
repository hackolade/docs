# Connect to a Teradata instance

**Important:** when reverse-engineering or forward-engineering a Teradata instance, the (Teradata) user used to connect to the target instance should have access to read **SYSUDTLIB** system database to retrieve DDL scripts for UDT, UDM etc...

&nbsp;

More information is available [here](<https://docs.teradata.com/r/Enterprise\_IntelliFlex\_VMware/Teradata-VantageTM-SQL-Data-Definition-Language-Syntax-and-Examples-17.20/Table-Statements/CREATE-TABLE-and-CREATE-TABLE-AS> "target=\"\_blank\"").

&nbsp;

The Teradata instance can be hosted on-premises, or on virtualized machines in a private or public cloud.  

 

In the Hackolade connection settings dialog, give a meaningful name to the connection, then set the the host and port if you wish to limit the scope of the discovery.

&nbsp;

![Teradata connection settings](<lib/Teradata connection settings.png>)

&nbsp;

**Important:** when reverse-engineering or forward-engineering a Teradata instance, Hackolade is leveraging the Teradata **Java** client.&nbsp; You will need a working and properly configured Java environment (minimum Java 11).&nbsp; Hackolade tries to autodetect **JAVA\_HOME** on your system but you can still configure it manually if your installation is specific (or if our automatic detection can’t find **JAVA\_HOME**)**.**

![Teradata advanced settings Java binary path](<lib/Teradata advanced settings Java binary path.png>)

&nbsp;

&nbsp;

If required, you may enter your username and password

&nbsp;

![Image](<lib/MariaDB connection settings auth.png>)
