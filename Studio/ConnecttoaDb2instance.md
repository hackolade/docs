# Connect to a Db2 instance

The IBM Db2 instance can be hosted on-premises, or on virtualized machines in a private or public cloud.  

 

In the Hackolade connection settings dialog, give a meaningful name to the connection, then set the the host and port if you wish to limit the scope of the discovery.

&nbsp;

![Db2 connection settings](<lib/Db2 connection settings.png>)

&nbsp;

&nbsp;

**Important:** when reverse-engineering or forward-engineering a Db2 instance, Hackolade is leveraging the IBM Db2 **Java** client.&nbsp; You will need a working and properly configured Java environment (minimum [JRE 8](<https://www.java.com/en/download/> "target=\"\_blank\"")).&nbsp; Hackolade tries to autodetect **JAVA\_HOME** on your system but you can still configure it manually if your installation is specific (or if our automatic detection can’t find **JAVA\_HOME**)**.**

&nbsp;

![Db2 advanced settings Java binary path](<lib/Db2 advanced settings Java binary path.png>)

&nbsp;

&nbsp;

If required, you may enter your username and password

&nbsp;

![Db2 connection settings auth](<lib/Db2 connection settings auth.png>)
