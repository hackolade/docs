# Connect to an Oracle instance

To interact with Oracle databases (Cloud and private), when applying forward-engineering DDLs reverse-engineering, a user-provided Oracle client is required.&nbsp; Just like major applications, including [Tableau Desktop](<https://kb.tableau.com/articles/howto/Connecting-to-Oracle-in-Tableau-Desktop-using-Oracle-Wallet> "target=\"\_blank\""), we do NOT ship an Oracle Instant Client in our plugin for many reasons, including Oracle's licensing terms.&nbsp; If you don't have an Oracle Client already installed on your machine, its download and installation will be required as part of the process so the connection settings can be pointed at it.

&nbsp;

**Important:** when reverse-engineering an Oracle instance, non-privileged users can see the metadata of only their own objects, so to access others you need to be be granted SELECT\_CATALOG\_ROLE. More information is available [here](<https://docs.oracle.com/cd/B19306\_01/appdev.102/b14258/d\_metada.htm#i1016867> "target=\"\_blank\"") and [here](<https://docs.oracle.com/en/database/oracle/oracle-database/23/arpls/DBMS\_METADATA.html#GUID-005EEF26-0254-4996-A43A-C5236ADA8829> "target=\"\_blank\"").

&nbsp;

If you encounter an error *ORA-16000: database or pluggable database open for read-only access,* it has been confirmed by Oracle that pluggable and stand-by instances of Oracle are read-only which prevents the operation of the DBMS\_METADATA.GET\_DDL PL/SQL function which we need to perform reverse-engineering of the instance.&nbsp; Hackolade Studio will not perform the reverse-engineering operation correctly if connected to a pluggable or stand-by instance. &nbsp;

&nbsp;

&nbsp;

**Note:** There are many ways to configure connections to Oracle. Plus firewalls, proxies, and whitelist can be make it hard to access.&nbsp; The easiest way to troubleshoot the connection settings in Hackolade is to make sure first that you have access from the same machine with another client tool.&nbsp; Then it becomes easy to transpose the connection settings from that application to Hackolade.&nbsp; Since [SQL Developer](<https://www.oracle.com/tools/downloads/sqldev-downloads.html> "target=\"\_blank\"") is an Oracle product, it does not require a separate Oracle Instant Client, so having a working connection from SQL Developer is not alone sufficient proof that Hackolade could connect.

&nbsp;

&nbsp;

## Thin vs Thick mode

The Hackolade Studio plugin for Oracle includes a thin client to facilitate connections to an Oracle instance, whether on-premises or in the cloud. &nbsp;

![Oracle Thin mode client](<lib/Oracle Thin mode client.png>)

&nbsp;

You just need to give your connection a meaningful name, choose a connection method (basic, Cloud Wallet, or TNS), and complete the fields shown for that method.&nbsp; Then move to the Authentication tab to enter your credentials.&nbsp; **Thin mode** (the default) does not require a separate Oracle Instant Client install on your machine.

&nbsp;

For **Thick mode**, you must also specify **Client type** (Oracle Home or Instant Client) and **Client location** as described in the ORACLE\_HOME vs Instant Client section below.

&nbsp;

If running on Oracle Cloud Infrastructure, things are even simpler if you fetch a Wallet, as described below.

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

If ORACLE\_HOME is set, then you may choose this option:![Oracle connection ORACLE\_HOME](<lib/Oracle connection ORACLE\_HOME.png>)

&nbsp;

&nbsp;

If ORACLE\_HOME is not set, you probably need to [download](<https://www.oracle.com/database/technologies/instant-client/downloads.html> "target=\"\_blank\"") and install an Instant Client.&nbsp; You may have to get your IT department to push this to your machine.

&nbsp;

Oracle Instant client is a basic lightweight client which can be unzipped in a location without any installation, it contains only the communication layer to be able to connect to oracle. When using Instant Client, just unzip it to a location of your choice.&nbsp; Keep a note of the path to this folder, as you will have to specify it in the connection settings to your Oracle instance.&nbsp;

&nbsp;

You may set your ORACLE\_HOME environment variable to this location, or simply specify the location in the Hackolade connection settings.

&nbsp;

![Oracle connection instant client](<lib/Oracle connection instant client.png>)

&nbsp;

&nbsp;

### Oracle Instant Client installation on Mac

On MacOS, a trusted signed package is required.&nbsp; When you download from [Oracle](<https://www.oracle.com/database/technologies/instant-client/macos-intel-x86-downloads.html> "target=\"\_blank\""), you must know that the .zip version won't be trusted by MacOS and will cause Hackolade to malfunction.&nbsp; You must download one of the .dmg packages&nbsp;

&nbsp;

![Image](<lib/Oracle Instant Client MacOS.png>)

&nbsp;

Once the package is downloaded, open the \`\<instant-client\>.dmg\` and copy **all the files** to a dedicated folder of your choice. For example, \`/Users/\<username\>/databases/clients/oracle\`. Keep a note of the path to this folder, as you will have to specify it in the connection settings to your Oracle instance.&nbsp;

&nbsp;

## Connection method

We support 3 connection methods: basic, with an Oracle Cloud Wallet, or with a tnsnames.ora configuration file.

&nbsp;

### Basic connection settings

With the basic method, you must specify all the necessary parameters for the clinet to establish the connection.&nbsp; This includes the hostname DNS or IP address, the port number, and either a service name or SID (Oracle system identifier)

&nbsp;

![Oracle basic connection service name](<lib/Oracle basic connection service name.png>)

&nbsp;

or&nbsp;

![Image](<lib/Oracle basic connection SID.png>)

&nbsp;

&nbsp;

### Oracle wallet

Oracle Wallet provides an simple and easy method to manage database credentials across multiple domains. It allows you to update database credentials by updating the Wallet instead of having to change individual datasource definitions. This is accomplished by using a database connection string in the datasource definition that is resolved by an entry in the wallet.

&nbsp;

With Oracle Autonomous, you may also generate a wallet using [these instructions](<https://docs.oracle.com/en/cloud/paas/autonomous-database/adbsa/connect-download-wallet.html#GUID-B06202D2-0597-41AA-9481-3B174F75D4B1> "target=\"\_blank\""). Once you have downloaded the Wallet .zip file, you simply need to specify the file path and name.&nbsp; In **Thin mode**, you must also enter the **Wallet password** (the password you set when downloading the wallet from OCI — not your database user password).&nbsp; Then use the Authentication tab for your database user name and password.

&nbsp;

![Oracle connection wallet](<lib/Oracle connection wallet.png>)

&nbsp;

### TNSnames.ora config file

TNS = Transparent Network Substrate. The tnsnames.ora file is a configuration file that contains network service names mapped to connect descriptors for the local naming method, or net service names mapped to listener protocol addresses. A net service name is an alias mapped to a database network address contained in a connect descriptor.

&nbsp;

You may have a tnsnames.ora file on your machine or on a shared drive.&nbsp; By default, tnsnames.ora is located in the $ORACLE\_HOME/network/admin directory, but it can also be in the directory specified by the TNS\_ADMIN environment variable.&nbsp; On a Windows machine, the system environment variable TNS\_ADMIN, if any, generally indicates the location of your tnsnames.ora file.&nbsp;  At a command prompt, type C:\\\>echo %TNS\_ADMIN% to find out.

&nbsp;

You must specify the folder location of the tnsnames.ora file (or select the tnsnames.ora file itself — Hackolade uses its parent folder) as well as the TNS alias to be used, or leave the alias empty to use the first entry in the file.

&nbsp;

For Oracle Autonomous Database, entries on port **1522** typically require mutual TLS (mTLS): the client must present wallet files from your OCI download and the wallet password.&nbsp; Enable **Mutual TLS (mTLS)** on the Connection tab when your folder contains the full wallet.&nbsp; When mTLS is enabled in **Thin mode**, enter the wallet password on the Connection tab; the password on the Authentication tab remains your Oracle database user password.

&nbsp;

With the **TNS** connection method and a `tnsnames.ora` file only (mTLS unchecked, no client wallet in the folder), Hackolade can use simpler one-way TLS, which is often more performant than mTLS because the client does not send a wallet certificate.&nbsp; That mode is possible only if your database administrator has configured the instance accordingly — for example Oracle Cloud access control lists (ACLs) that allow your client IP and policies that do not enforce mTLS for the service you use.&nbsp; If mTLS is still required by the database, leave **Mutual TLS (mTLS)** enabled and provide the full wallet directory and wallet password.&nbsp; Do not assume that a `tnsnames.ora` file alone is sufficient unless your DBA has confirmed that mTLS enforcement is disabled for your access path.

&nbsp;

![Image](<lib/Oracle connection tnsnames ora.png>)

&nbsp;

### Authentication

Hackolade does not yet support OS-based or Kerberos authentication.

&nbsp;

You must provide the username, password, and optionally a role for your connection.

&nbsp;

![Oracle connection authentication](<lib/Oracle connection authentication.png>)

&nbsp;

&nbsp;

&nbsp;

### Advanced

Oracle instances can be quite large with many user schemas.&nbsp; If you want to limit the scope of the discovery and you know the user schema you wish to access directly, you may enter it in the Advanced tab.&nbsp; You may even create one connection per user schema you access often.

&nbsp;

![Oracle connection advanced limit scope discov](<lib/Oracle connection advanced limit scope discov.png>)

&nbsp;

## Connecting to Oracle on Amazon RDS

If you're running Oracle on Amazon RDS , the [instructions to connect](<https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER\_ConnectToOracleInstance.html> "target=\"\_blank\"") to SQL Developer can be followed to connect to Hackolade Studio in a similar way.&nbsp; More details can also be found [here](<AmazonRDSorAurora.md>).

&nbsp;
