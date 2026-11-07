---
description: Connect Hackolade Studio to SQL Server on-premises, in the cloud or on Azure SQL Database, with the available authentication methods.
seoTitle: Connect to SQL Server or Azure SQL Database
image: lib/SQL Server Connection settings.png
---
# Connect to a SQL Server instance

The SQL Server engine can hosted on-premises, on virtualized machines in a private or public cloud, or as a managed instance with the Azure SQL Database service.

Several [authentication methods](<https://docs.microsoft.com/en-us/sql/ssms/f1-help/connect-to-server-database-engine> "target=\"_blank\"") are available.

In the Hackolade connection settings dialog, give a meaningful name to the connection, choose the source (on-prem/cloud or Azure SQL Database), then set the database name, the host and port:

![SQL Server Connection settings](<lib/SQL Server Connection settings.png>)

> [!IMPORTANT]
> The host IP address and the port must correspond exactly to the values in the SQL Server instance. You may want to check using the SQL Server Configuration Manager (SQL Server Network Configuration -> Protocols for \<instance name> -> TCP/IP -> \[right click\] properties)

![SQL Server Configuration Manager](<lib/SQL Server Configuration Manager.png>)

If you reference a named instance in the host field, please make sure to leave blank the port.

Or you may choose to provide a connection string which includes: host, port, username and password:

![SQL Server Connection String](<lib/SQL Server Connection String.png>)
