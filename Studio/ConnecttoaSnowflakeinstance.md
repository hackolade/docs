# Connect to a Snowflake instance

A Snowflake account can be hosted on any of the following cloud platforms: Amazon Web Services, Google Cloud Platform, or Microsoft Azure.&nbsp; Each platform provides one or more [regions](<https://docs.snowflake.com/en/user-guide/intro-regions.html>) where the account is provisioned.&nbsp;

&nbsp;

Access to Snowflake by Hackolade and permission to perform reverse-engineering are contingent upon the following minimum setup in Snowflake:

* “USAGE” privilege for warehouse/database/schema, according to [https://docs.snowflake.com/en/user-guide/security-access-control-privileges.html#virtual-warehouse-privileges](<https://docs.snowflake.com/en/user-guide/security-access-control-privileges.html#virtual-warehouse-privileges>)

&nbsp; For example: *grant usage on warehouse compute\_wh to role public;*

\- “SELECT” privilege for tables

\- rights to run the utility function [GET\_DDL](<https://docs.snowflake.com/en/sql-reference/functions/get\_ddl>) and get the information returned. Here is a [link](<https://docs.snowflake.com/en/user-guide/views-secure#interacting-with-secure-views:~:text=The%20definition%20of%20a%20secure%20view%20is%20only%20exposed%20to%20authorized%20users%20(i.e.%20users%20who%20have%20been%20granted%20the%20role%20that%20owns%20the%20view).%20If%20an%20unauthorized%20user%20uses%20any%20of%20the%20following%20commands%20or%20interfaces>) for additional explanation. Note that DESC VIEW does not provide sufficient information in the API for our reverse-engineering needs.&nbsp; For Secure Views, it is necessary to access the structure stored in the **VIEW\_DEFINITION** column of **INFORMATION\_SCHEMA**.**VIEWS.**  If access to **VIEW\_DEFINITION** is restricted based on privileges, an unauthorized user cannot apparently retrieve the required metadata for reverse engineering.   This is the same as for **GET\_DDL**.

&nbsp;

&nbsp;

Your Snowflake administrator might have to create a read-only user for you.&nbsp; Here's a [good example](<https://gist.github.com/vdparikh/7931f0c22e55f98d491a1df737260a53> "target=\"\_blank\"").

&nbsp;

In the Hackolade connection settings dialog, give a meaningful name to the connection, choose the cloud platform, then set the host prefix.

&nbsp;

![Snowflake Connection Settings](<lib/Snowflake Connection Settings.png>)

&nbsp;

Host prefixes differ may depend on the platform:

\- AWS: \<account\>.\<region\> for URL https://\<account\>.\<region\>.snowflakecomputing.com/

[&nbsp;except for US West accounts where the URL follows the format ](<https://\<account\>.snowflakecomputing.com/>)https://\<account\>.snowflakecomputing.com/

[\- Google Cloud: ](<https://os70966.europe-west4.gcp.snowflakecomputing.com/>)\<account\>.\<region\>.gcp for URL[ ](<https://os70966.europe-west4.gcp.snowflakecomputing.com/>)https://\<account\>.\<region\>.gcp.snowflakecomputing.com/

[\- Azure: ](<https://ah42164.west-europe.azure.snowflakecomputing.com/>)\<account\>.\<region\>.azure for URL [https://\<account\>.\<region\>.azure.snowflakecomputing.com/](<https://ah42164.west-europe.azure.snowflakecomputing.com/>)

or the account name provided by Snowflake, where the URL follows the format https://*account\_name*.snowflakecomputing.com

&nbsp;

Optionally specify the active/current warehouse for the session.

&nbsp;

Different options are possible for authentication:

\- [Snowflake authentication](<Snowflakeauthentication.md>)

\- [Native SSO (Okta only)](<NativeSSOOktaonly.md>)

\- [Single Sign-On via external browser](<IdentityProviderSSOexternalbrows.md>)
