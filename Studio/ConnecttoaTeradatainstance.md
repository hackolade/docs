# Connect to a Teradata instance

**Important:** when reverse-engineering or forward-engineering a Teradata instance, the (Teradata) user used to connect to the target instance should have access to read **SYSUDTLIB** system database to retrieve DDL scripts for UDT, UDM etc...

&nbsp;

More information is available [here](<https://docs.teradata.com/r/Teradata-VantageCloud-Lake/SQL-Reference/SQL-Data-Definition-Language/Table-Statements/CREATE-TABLE-and-CREATE-TABLE-AS> "target=\"\_blank\"").

&nbsp;

The Teradata instance can be hosted on-premises, or on virtualized machines in a private or public cloud.  

&nbsp;

Teradata supports 2 authentication mechanisms: basic auth, or LDAP.&nbsp; Hackolade Studio does not currently support LDAP -- only basic auth.&nbsp; To be sure of the auth mechanism for your username, and if they are able to connect via "sql connect tool", you can check the mechanism using the following query:

> **SELECT** Username, LDAP, MechanismName\
**FROM** dbc.SessionInfoV\
**WHERE** Username = **USER**;

&nbsp;

In "MechanismName" there should be either:

* **TD2** for basic auth
* **LDAP** (or any other) for LDAP mechanism respectively

&nbsp;

&nbsp;

Our reverse-engineering process requires at least [read-only privileges](<https://docs.teradata.com/r/Enterprise\_IntelliFlex\_VMware/Database-Administration/Working-with-Users-Roles-and-Profiles-Operational-DBAs/Using-Roles-to-Manage-User-Privileges/User-Types-and-Minimum-Required-Privileges> "target=\"\_blank\"") for the following tables:

&nbsp;

* Databases/Schemas: SELECT on DBC.DatabasesV
* Tables/Views: SELECT on DBC.TablesV
* Columns: SELECT on DBC.ColumnsV
* Check Constraints: SELECT on DBC.CheckConstraintsV
* Unique Constraints: SELECT on DBC.UniqueConstraintsV
* Foreign Keys: SELECT on DBC.All\_RI\_ParentsV
* Indexes: SELECT on DBC.IndicesV
* Views: SELECT on DBC.TablesV.ViewText

&nbsp;

The following must be [granted explicitly](<https://docs.teradata.com/r/Enterprise\_IntelliFlex\_VMware/Database-Administration/Working-with-Databases-All-DBAs/Best-Practices-for-Database-Creation/Working-with-Table-Access-Privileges-for-Views> "target=\"\_blank\"") for each table in the instance, or the user must be an owner of the table

&nbsp;

* UDTs: SELECT on SYSUDTLIB
* Table DDL: SHOW TABLE on \<db\>.\<table\>
* For sampling data: SELECT TOP 1 on \<db\>.\<table\>

&nbsp;

For reference:

* Query to check the actual user rights (update the UserName):

> **SELECT** DatabaseName, TableName, AccessRight **FROM** DBC.AllRights **WHERE** UserName='demo\_user' **ORDER** **BY** 2, 1;

&nbsp;

* To grant a privilege please review instructions in [this page](<https://docs.teradata.com/r/Enterprise\_IntelliFlex\_VMware/Database-Administration/Working-with-Users-Roles-and-Profiles-Operational-DBAs/Granting-Privileges-Directly-To-Users/Granting-Privileges-to-a-User> "target=\"\_blank\"")

&nbsp;

If you want to apply to instance, you will of course need write rights for the above.

 

In the Hackolade connection settings dialog, give a meaningful name to the connection, then set the the host and port if you wish to limit the scope of the discovery.

&nbsp;

![Teradata connection settings](<lib/Teradata connection settings.png>)

&nbsp;

**Important:** when reverse-engineering or forward-engineering a Teradata instance, Hackolade is leveraging the Teradata **Java** client.&nbsp; You will need a working and properly configured Java environment (minimum Java 11).&nbsp; Hackolade tries to auto-detect **JAVA\_HOME** on your system but you can still configure it manually if your installation is specific (or if our automatic detection can’t find **JAVA\_HOME**)**.**

![Teradata advanced settings Java binary path](<lib/Teradata advanced settings Java binary path.png>)

&nbsp;

&nbsp;

If required, you may enter your username and password

&nbsp;

![Image](<lib/MariaDB connection settings auth.png>)
