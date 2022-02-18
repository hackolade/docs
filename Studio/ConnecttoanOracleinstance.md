# Connect to an Oracle instance

To interact with Oracle databases (Cloud and private), when applying forward-engineering DDLs reverse-engineering, a user-provided Oracle client is required.&nbsp; Just like major applications, including [Tableau Desktop](<https://kb.tableau.com/articles/howto/Connecting-to-Oracle-in-Tableau-Desktop-using-Oracle-Wallet> "target=\"\_blank\""), we do NOT ship an Oracle Instant Client in our plugin for many reasons, including Oracle's licensing terms.&nbsp; If you don't have an Oracle Client already installed on your machine, its download and installation will be required as part of the process so the connection settings can be pointed at it.

&nbsp;

**Important:** when reverse-engineering an Oracle instance, non-privileged users can see the metadata of only their own objects, so to access others you need to be be granted SELECT\_CATALOG\_ROLE. More information is available [here](<https://docs.oracle.com/cd/B19306\_01/appdev.102/b14258/d\_metada.htm#i1016867> "target=\"\_blank\"").

&nbsp;

**Note:** There are many ways to configure connections to Oracle. Plus firewalls, proxies, and whitelist can be make it hard to access.&nbsp; The easiest way to troubleshoot the connection settings in Hackolade is to make sure first that you have access from the same machine with another client tool.&nbsp; Then it becomes easy to transpose the connection settings from that application to Hackolade.&nbsp; Since [SQL Developer](<https://www.oracle.com/tools/downloads/sqldev-downloads.html> "target=\"\_blank\"") is an Oracle product, it does not require a separate Oracle Instant Client, so having a working connection from SQL Developer is not alone sufficient proof that Hackolade could connect.

&nbsp;

## ORACLE\_HOME vs Instant Client

You may already have a full client installed on your machine.&nbsp; ORACLE\_HOME is a directory in the file system where the Oracle software is installed. The path to this directory is stored in an environment variable. &nbsp;

&nbsp;

To check if ORACLE\_HOME has been set on your machine and available for Hackolade:

&nbsp;

**On Windows:** At a command prompt, type C:\\\>echo %ORACLE\_HOME%. If this gives you the directory path, then that means ORACLE\_HOME is set.

\
If ORACLE\_HOME is not set, the output will simply give back %ORACLE\_HOME%.&nbsp;

&nbsp;

**On Unix/Linux:** type env&nbsp; grep \| ORACLE\_HOME

If ORACLE\_HOME is set, then you may choose this option:\
![Oracle connection ORACLE\_HOME](<lib/Oracle%20connection%20ORACLE\_HOME.png>)

&nbsp;

&nbsp;

If ORACLE\_HOME is not set, you probably need to [download](<https://www.oracle.com/database/technologies/instant-client/downloads.html> "target=\"\_blank\"") and install an Instant Client.&nbsp; You may have to get your IT department to push this to your machine.

&nbsp;

Oracle Instant client is a basic lightweight client which can be unzipped in a location without any installation, it contains only the communication layer to be able to connect to oracle. When using Instant Client, just unzip it to a location of your choice.&nbsp; Keep a note of the path to this folder, as you will have to specify it in the connexion settings to your Oracle instance.&nbsp;

&nbsp;

You may set your ORACLE\_HOME environment variable to this location, or simply specify the location in the Hackolade connection settings.

&nbsp;

![Oracle connection instant client](<lib/Oracle%20connection%20instant%20client.png>)

&nbsp;

### Oracle Instant Client installation on Mac

On MacOS, a trusted signed package is required.&nbsp; When you download from [Oracle](<https://www.oracle.com/database/technologies/instant-client/macos-intel-x86-downloads.html> "target=\"\_blank\""), you must know that the .zip version won't be trusted by MacOS and will cause Hackolade to malfunction.&nbsp; You must download one of the .dmg packages&nbsp;

&nbsp;

![Image](<lib/Oracle%20Instant%20Client%20MacOS.png>)

&nbsp;

Once the package is downloaded, open the \`\<instant-client\>.dmg\` and copy **all the files** to a dedicated folder of your chioce. For example, \`/Users/\<username\>/databases/clients/oracle\`. Keep a note of the path to this folder, as you will have to specify it in the connexion settings to your Oracle instance.&nbsp;

&nbsp;

## Connection method

We support 3 connection methods: basic, with an Oracle wallet, or with a tnsnames.ora configuration file.

&nbsp;

### Basic connection settings

With the basic method, you must specify all the necessary parameters for the clinet to establish the connection.&nbsp; This includes the hostname DNS or IP address, the port number, and either a service name or SID (Oracle system identifier)

&nbsp;

![Oracle basic connection service name](<lib/Oracle%20basic%20connection%20service%20name.png>)

&nbsp;

or&nbsp;

![Image](<lib/Oracle%20basic%20connection%20SID.png>)

&nbsp;

&nbsp;

### Oracle wallet

Oracle Wallet provides an simple and easy method to manage database credentials across multiple domains. It allows you to update database credentials by updating the Wallet instead of having to change individual datasource definitions. This is accomplished by using a database connection string in the datasource definition that is resolved by an entry in the wallet.

&nbsp;

With Oracle Autonomous, you may also generate a wallet using [these instructions](<https://docs.oracle.com/en/cloud/paas/autonomous-database/adbsa/connect-download-wallet.html#GUID-B06202D2-0597-41AA-9481-3B174F75D4B1> "target=\"\_blank\""). Once you have downloaded the Wallet .zip file, you simply need to specify the file path and name, and the service name

&nbsp;

![Oracle connection wallet](<lib/Oracle%20connection%20wallet.png>)

&nbsp;

### TNSnames.ora config file

TNS = Transparent Network Substrate. The tnsnames.ora file is a configuration file that contains network service names mapped to connect descriptors for the local naming method, or net service names mapped to listener protocol addresses. A net service name is an alias mapped to a database network address contained in a connect descriptor.

&nbsp;

You may have a tnsnames.ora file on your machine or on a shared drive.&nbsp; By default, tnsnames.ora is located in the $ORACLE\_HOME/network/admin directory, but it can also be in the directory specified by the TNS\_ADMIN environment variable.&nbsp; On a Windows machine, the system environment variable TNS\_ADMIN, if any, generally indicates the location of your tnsnames.ora file.&nbsp;  At a command prompt, type C:\\\>echo %TNS\_ADMIN% to find out.

&nbsp;

You must specify the folder location of the tnsnames.ora file as well as the service name to be used.

&nbsp;

![Image](<lib/Oracle%20connection%20tnsnames%20ora.png>)

&nbsp;

### Authentication

Hackolade does not yet support OS-based or Kerberos authentication.

&nbsp;

You must provide the username, passwaord, and optionally a role for your connection.

&nbsp;

![Oracle connection authentication](<lib/Oracle%20connection%20authentication.png>)

&nbsp;

&nbsp;

&nbsp;

### Advanced

Oracle instances can be quite large with many user schemas.&nbsp; If you want to limit the scope of the discovery and you know the user schema you wish to access directly, you may enter it in the Advanced tab.&nbsp; You may even create one connection per user schema you access often.

&nbsp;

![Oracle connection advanced limit scope discov](<lib/Oracle%20connection%20advanced%20limit%20scope%20discov.png>)

&nbsp;

## Connecting to Oracle on Amazon RDS

If you're running Oracle on Amazon RDS, the [instructions to connect](<https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER\_ConnectToOracleInstance.html> "target=\"\_blank\"") to SQL Developer can be followed to connect to Hackolade in a similar way.

