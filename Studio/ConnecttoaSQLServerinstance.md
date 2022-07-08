# Connect to a SQL Server instance

The SQL Server engine can hosted on-premises, on virtualized machines in a private or public cloud, or as a managed instance with the Azure SQL Database service. &nbsp;

&nbsp;

Several [authentication methods](<https://docs.microsoft.com/en-us/sql/ssms/f1-help/connect-to-server-database-engine> "target=\"\_blank\"") are available.

&nbsp;

In the Hackolade connection settings dialog, give a meaningful name to the connection, choose the source (on-prem/cloud or Azure SQL Database), then set the database name, the host and port:

&nbsp;

![SQL Server Connection settings](<lib/SQL%20Server%20Connection%20settings.png>)

&nbsp;

&nbsp;

**Important:** the host IP address and the port must correspond exactly to the values in the SQL Server instance.&nbsp; You may want to check using the SQL Server Configuration Manager (SQL Server Network Configuration -\> Protocols for \<instance name\> -\> TCP/IP -\> \[right click\] properties)

![Image](<lib/SQL%20Server%20Configuration%20Manager.png>)

&nbsp;

&nbsp;

If you reference a named instance in the host field, please make sure to leave blank the port.

&nbsp;

Or you may choose to provide a connection string which includes: host, port, username and password:

&nbsp;

![SQL Server Connection String](<lib/SQL%20Server%20Connection%20String.png>)

