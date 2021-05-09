# Kerberos

## Kerberos Authentication ##

&nbsp;

**Important note:** our Kerberos support uses a 3rd-party library to provide cross-platform kerberos authentication using GSSAPI on Linux/Mac, and SSPI on Windows. &nbsp; For Linux and Mac, there are pre-requisites, respectively,&nbsp;

for **Linux:**

* python v2.7
* make
* A proper C/C++ compiler toolchain, like [GCC](<https://gcc.gnu.org/> "target=\"\_blank\"")
* Distribution-specific kerberos packages (e.g. krb5-dev on Ubuntu)

and for **Mac:**

* Xcode Command Line Tools: Can be installed with xcode-select --install
* Distribution-specific kerberos packages (e.g. [krb5 on Homebrew](<https://formulae.brew.sh/formula/krb5> "target=\"\_blank\""))

&nbsp;

If issues are encountered, it is generally a good idea to validate first that the whole environment has been set up correctly by connecting with [Beeline](<https://cwiki.apache.org/confluence/display/Hive/HiveServer2%20Clients> "target=\"\_blank\"").&nbsp; It may be required to obtain a valid Kerberos ticket before you attempt a connection to HiveServer2.&nbsp; This step can be done by running *kinit* from a terminal (Linux/mac) or a command line (Windows):&nbsp;

\[example\_user@host ~\] $ $BIGINSIGHTS\_HOME/jdk/jre/bin/kinit -k -t /home/example\_user/example\_user.keytab example\_user@YOUR-REALM.COM

&nbsp;

Hackolade can connect via Kerberos authentication only through “binary” transport mode and with Quality of Protection (QOP) values: “auth”, "auth-int", or "auth-conf", as per [RFC 1964](<https://tools.ietf.org/html/rfc1964> "target=\"\_blank\"") section 4.2.&nbsp;

&nbsp;

The Kerberos configuration in hive-site.xml must include these properties:

\<property\>

  \<name\>hive.metastore.sasl.enabled\</name\>

  \<value\>**true**\</value\>

  \<description\>If true, the metastore Thrift interface will be secured with SASL. Clients must authenticate with Kerberos.\</description\>

\</property\>

\<property\>

\<name\>hive.server2.authentication\</name\>

\<value\>***KERBEROS***\</value\>

\</property\>

\<property\>

\<name\>hive.server2.thrift.sasl.qop\</name\>

\<value\>**auth**\</value\>

\<description\>value could be also **auth-int** or **auth-conf**\</description\>

\</property\>

\<property\>

\<name\>hive.server2.authentication.kerberos.principal\</name\>

\<value\>***KERBEROS\_SERVICE\_PRINCIPAL***\</value\>

\<description\>the format of the service [principal](<https://web.mit.edu/kerberos/krb5-1.5/krb5-1.5.4/doc/krb5-user/What-is-a-Kerberos-Principal\_003f.html> "target=\"\_blank\"") is *service*/*\<fully qualified domain name of instance\>*@\<REALM\>\</description\>

\</property\>

\<property\>

\<name\>hive.server2.authentication.kerberos.keytab\</name\>

\<value\>***KERBEROS\_KEYTAB***\</value\>

\<description\>[keytab](<https://web.mit.edu/kerberos/krb5-1.5/krb5-1.5.4/doc/krb5-install/The-Keytab-File.html> "target=\"\_blank\"") looks like */etc/hive/conf/hive.keytab*\</description\>

\</property\>

&nbsp;

Where:

***\- KERBEROS\_SERVICE\_NAME*** is the kerberos service principal of the Hive instance (format. \<service\>/\<instance\>@REALM)&nbsp;

***\- KERBEROS\_KEYTAB*** - is the keytab file for kerberos principal

&nbsp;

The corresponding settings in Hackolade would be:

&nbsp;

![Image](<lib/Hive%20-%20Kerberos%20Authentication%20settings.png>)

&nbsp;

**User name**: don't forget to to put the username in UPPERCASE, and to reference the REALM.&nbsp; IN Windows, the username might be your Windows login.

**Service name**: enter the service name as provided by the administrator. &nbsp;

**Kerberos host**: enter the FQDN or "fully qualified domain name"

&nbsp;

&nbsp;

The krb5 library uses [MIT Kerberos](<https://web.mit.edu/kerberos/dist/> "target=\"\_blank\"") software. To make it work you should setup kerberos client, to do this create [krb5.conf](<https://web.mit.edu/kerberos/krb5-devel/doc/admin/conf\_files/krb5\_conf.html#sample-krb5-conf-file> "target=\"\_blank\"") and create environment variable **KRB5\_CONFIG** with path to the krb5.conf. After this, restart the PC. If MIT Kerberos is able to retrieve a ticket, then Hackolade should as well.

&nbsp;

Currently, krb5 library with keytab is used only in HTTP mode to retrieve SPNEGO token.


***
_Created with the Personal Edition of HelpNDoc: [Easily create EBooks](<https://www.helpndoc.com/feature-tour>)_
