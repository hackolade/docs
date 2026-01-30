# Model Hub user management

In the near future, the Hackolade Model Hub will allow to integrate with Single Sign On such as Microsoft Entra ID.&nbsp; In the meantime, or if you don't have such system, it is necessary to manually create users, following the instructions below.

&nbsp;

All actions take place in the OCI console.

## Manual creation of authorized users

Use the navigation menu to go to [Identity \& Security \> Identity \> Domains](<https://cloud.oracle.com/identity/domains> "target=\"\_blank\"") and first make sure that your applied filters specify the correct compartment created in for the [OCI stack](<OCIstackdeployment.md>) of your Model Hub.

&nbsp;

### Create user

Select the domain and choose the tab User management, and click the Create button

&nbsp;

![OCI Identity and Security users screen](<lib/OCI Identity and Security users screen.png>)

&nbsp;

&nbsp;

Enter First name, Last name, and username/email.&nbsp; If the user will need to access the Hub Admin page, for example to create links to your Git repository (or repositories.)&nbsp;

&nbsp;

![OCI Identity and Security create user](<lib/OCI Identity and Security create user.png>)

&nbsp;

&nbsp;

### Link user to integrated application

After successful creation, select the user and choose the tab Integrated applications, and click the button Assign applications:

![OCI Identity and Security user integrated app](<lib/OCI Identity and Security user integrated app.png>)

&nbsp;

&nbsp;

For the application, click the 3-dot ... button and choose Assign:

&nbsp;

![OCI Identity and Security link user to app](<lib/OCI Identity and Security link user to app.png>)

&nbsp;

You should receive a Success message:

![OCI Identity and Security user app success](<lib/OCI Identity and Security user app success.png>)

&nbsp;

&nbsp;

The user will receive an email to activate the account and choose a password:

![OCI Identity and Security user creation email](<lib/OCI Identity and Security user creation email.png>)

&nbsp;

&nbsp;

## Reset password or delete user

If needed, it is possible reset the password or delete the account:

![OCI Identity and Security user reset pwd](<lib/OCI Identity and Security user reset pwd.png>)

&nbsp;

&nbsp;

