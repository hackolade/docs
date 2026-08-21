# Integrating with Okta

On this page, you will find a step-by-step guide to integrating Okta with the Model HUB portal.

&nbsp;

## Pre-requisites

In order to perform the operations in this guide, you will need the following:

* Access to the administration panel on Okta with the ability to create an app integration and authorization server
* Be able to create groups and assign them to users

&nbsp;

## &#49;. Create an app integration

IIn Okta, select Applications -\> Applications, then click on Create App integration

&nbsp;

In the modal, select OIDC - OpenID Connect and Single-Page Application as the Application, then click Next

&nbsp;

Give a name to your app, then add the following options

* For Grant type, make sure the Authorization Code is checked
* As a Sign-in redirect URIs, put both the domain of the Model Hub portal and the admin portal (eg, https://hck.example.com/hub and https://hck.example.com/admin)
* As sign-out redirect URIs put the domain name of the Model Hub portal (eg, https://hck.example.com)
* Feel free to give access to the right users in the Assignments section

&nbsp;

## &#50;. Create a new groups

In order to give users administrative access to the Model HUB portal, you should create a new group

&nbsp;

In Okta, select Directory -\> Groups, then click on Add group

&nbsp;

Fill the form with the following:

* Name: Hub.Admin
* Description: A group that gives access to the admin UI of the Model Hub portal

&nbsp;

Once the group is created, you can start assigning users to these groups. &nbsp;

&nbsp;

* In the Model Hub policy, click on Add rule
* This allows you to configure different token lifespans for different users. Give it a name like "Model Hub default rule".\&#x20;

  * You can leave the rest as is and click on "Create rule" when you are done.

&nbsp;

&nbsp;

## &#51;. Configure the authorization server

To retrieve the groups a user belongs to in the Model HUB, you will need to configure the authorization server to include them in the access token.

&nbsp;

In Okta, select Security -\> API, then select the authorization server you want to use (or the default one)

&nbsp;

Go to Claims, then click on Add Claim

&nbsp;

Fill the model with the following information:

* Name: roles
* Include in token type: Select Access Token
* Value type: Groups
* Filter: Select Starts with and fill in "Hub"
* Include in: Select any scope

&nbsp;

Make sure you have an Access Policy configured by going to the Access Policies tab:

* Click on Add Policy
* Give it a name like "Model Hub"
* Description: "Model Hub access policy"
* Assign to: The following clients then chose the application you created in step 1

&nbsp;

&nbsp;

## &#52;. Assign the groups to the application

To give access to the people in the groups created above to Model Hub, you need to assign them

* In Okta, select Applications -\> Applications, then click on the application you created
* Click on the Assignments tab
* Click on the Assign button, then Assign to Groups
* Make sure to add the groups "Hub.Admin" and "Hub.User"

&nbsp;

## &#53;. Configure the application in the admin portal

Finally, to configure the application to use Okta as an authentication server, you will need to go to the admin portal -\> Authentication, click on the *Authentication enabled* toggle, then fill the form with the following

&nbsp;

* Identity provider: Okta
* Domain: The domain name of your Okta deployment
* Client ID: Go to Okta, select Applications -\> Applications then click on the app you just created and copy the Client ID in the client credentials section
* Authorization server ID (optional): Specify the authorization server configured in step 3. Uses *default* by default

&nbsp;

