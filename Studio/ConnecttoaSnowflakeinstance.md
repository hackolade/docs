# Connect to a Snowflake instance

A Snowflake account can be hosted on any of the following cloud platforms: Amazon Web Services, Google Cloud Platform, or Microsoft Azure.&nbsp; Each platform provides one or more [regions](<https://docs.snowflake.com/en/user-guide/intro-regions.html>) where the account is provisioned.&nbsp;

&nbsp;

Access to Snowflake by Hackolade and permission to perform reverse-engineering are contingent upon the following minimum setup in Snowflake:

* “USAGE” privilege for warehouse/database/schema, according to [https://docs.snowflake.com/en/user-guide/security-access-control-privileges.html#virtual-warehouse-privileges](<https://docs.snowflake.com/en/user-guide/security-access-control-privileges.html#virtual-warehouse-privileges>)

&nbsp; For example: *grant usage on warehouse compute\_wh to role public;*

\- “SELECT” privilege for tables

&nbsp;

Your Snowflake administrator might have to create a read-only user for you.&nbsp; Here's a [good example](<https://gist.github.com/vdparikh/7931f0c22e55f98d491a1df737260a53> "target=\"\_blank\"").

&nbsp;

In the Hackolade connection settings dialog, give a meaningful name to the connection, choose the cloud platform, then set the host prefix.

&nbsp;

![Snowflake Connection Settings](<lib/Snowflake%20Connection%20Settings.png>)

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
