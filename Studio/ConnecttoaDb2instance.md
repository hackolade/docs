---
description: Connect Hackolade Studio to IBM Db2 on-premises or in the cloud, and the privileges needed for reverse- and forward-engineering.
seoTitle: Connect to an IBM Db2 instance
image: lib/Db2 connection settings.png
---
# Connect to a Db2 instance

The IBM Db2 instance can be hosted on-premises, or on virtualized machines in a private or public cloud.

In the Hackolade connection settings dialog, give a meaningful name to the connection, then set the the host and port if you wish to limit the scope of the discovery.

![Db2 connection settings](<lib/Db2 connection settings.png>)

> [!IMPORTANT]
> When reverse-engineering or forward-engineering a Db2 instance, Hackolade is leveraging the IBM Db2 **Java** client. You will need a working and properly configured Java environment (minimum [JRE 8](<https://www.java.com/en/download/> "target=\"_blank\"")). Hackolade tries to auto-detect **JAVA_HOME** on your system but you can still configure it manually if your installation is specific (or if our automatic detection can’t find **JAVA_HOME**)**.**

![Db2 advanced settings Java binary path](<lib/Db2 advanced settings Java binary path.png>)

If required, you may enter your username and password

![Db2 connection settings auth](<lib/Db2 connection settings auth.png>)
