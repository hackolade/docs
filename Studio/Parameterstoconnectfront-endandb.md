# Parameters to connect front-end and back-end

Once your OCI setup is completed, an action is required by Hackolade to link the front-end application, served from our [Azure Front Door CDN](<https://azure.microsoft.com/en-us/blog/introducing-the-new-azure-front-door-reimagined-for-modern-apps-and-content/> "target=\"\_blank\"") (Content Delivery Network), with the database and OCI stack you created in [the previous step](<OCIstackdeployment.md>).

&nbsp;

For this step, you must communicate in a ticket to the Hackolade helpdesk [support@hackolade.com](<mailto:support@hackolade.com?subject=Please%20create%20DNS%20for%20our%20Model%20Hub>) just 4 pieces of information from 2 OCI screens, described below.&nbsp; Please provide the information both in **text format** and with the **2 screenshots** (making sure that the information is displayed and legible.)

&nbsp;

From OCI Resource Manager \> Stacks \> Stack \> Job \> Variables

* the hub\_db\_schema\_username
* the hub\_domain\_name, in a format \<yourOrgName\>.hackolade.com

&nbsp;

&nbsp;

![OCI Resources Manager Variables](<lib/OCI Resources Manager Variables.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

From OCI Resource Manager \> Stacks \> Stack \> Job \> Outputs&nbsp;

* the ORDS endpoint&nbsp;
* the ApiGatewayEndpoint

&nbsp;

![Image](<lib/OCI Resources Manager Job Outputs.png>)

&nbsp;

&nbsp;

Once Hackolade Helpdesk responds that the setup has been successfully performed, you should be able to go to your personal domain \<yourOrgName\>.hackolade.com in a browser and access this page prompting for your username and password:

&nbsp;

![Hackolade Model Hub login](<lib/Hackolade Model Hub login.png>)

&nbsp;

&nbsp;

Currently, as no Hub users have been created, no username/password combination will work here.&nbsp; The OCI administrator must first create one or more users, following [these instructions](<ModelHubusermanagement.md>).

&nbsp;

With the proper credentials, you can access the Hub.

&nbsp;

As the database is currently empty, the first screen of the Hub shows this screen with zeros everywhere...

&nbsp;

![Hackolade Model Hub empty database screen](<lib/Hackolade Model Hub empty database screen.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

