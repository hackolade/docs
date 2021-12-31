# MongoDB Atlas

To connect Hackolade to MongoDB Atlas, you will need:

* Whitelist in Atlas the IP address for your PC
* MongoDB User and Password. The connection details use the MongoDB administration user and password set up for the group. To connect with a different MongoDB user, replace the user name and password in the connection details.
* The MongoDB URI for the hosts and ports for a replica set or the hostname for the mongos for a sharded cluster.

&nbsp;

Even if the user is set up for two-factor authentication (2FA), the connection to your MongoDB Atlas instance with Hackolade does not require 2FA.

&nbsp;

![MongoDB Atlas Cluster overview](<lib/Atlas%20Cluster%20overview.png>)

&nbsp;

Click Connect, then Connect with MongoDB Compass:

![MongoDB Atlas connect with Compass](<lib/Atlas%20connect%20with%20Compass.png>)

&nbsp;

Then click the Copy button:

![Atlas MongoDB connection string copy](<lib/Atlas%20MongoDB%20connection%20string%20copy.png>)

&nbsp;

so it can be pasted in Hackolade:

&nbsp;

In Hackolade Connection Settings, click on **From URI or SRV** and paste the URI info copied to the clipboard:

&nbsp;

![MongoDB Reverse-Engineering - Atlas connectio](<lib/MongoDB%20Reverse-Engineering%20-%20Atlas%20connectio.png>)

You may choose the Read Preference from the list:

![MongoDB Atlas read preference](<lib/Atlas%20read%20preference.png>)

&nbsp;

&nbsp;

Don't forget, in the Authentication tab, to replace \<password\> with your real Atlas user password.

&nbsp;

In the SSL tab, make sure thatthe option System CA / Atlas Deployment was selected:

![MongoDB reverse-engineering - Atlas deployment](<lib/MongoDB%20Rev%20Eng%20-%20Atlas%20deployment.png>)

&nbsp;

You may test if you wish, then save and connect.

&nbsp;

**Important note:** don't forget to whitelist in Atlas the IP address of your PC where Hackolade is installed

With your MongoDB Atlas login credentials, open to your account and find the cluster. &nbsp;

Next, click on Network Access under the Security tab on the left-hand sidebar. This will take you to the IP Whitelist tab.

Click on Add IP Address in the top-right corner. This will open the Add IP Whitelist Entry dialog.

![Image](<lib/MongoDB%20IP%20address%20whitelist%201.png>)

&nbsp;

&nbsp;

Click on Add current IP address. MongoDB will automatically detect your current address, then click Confirm.

![Image](<lib/MongoDB%20IP%20address%20whitelist%202.png>)

&nbsp;

MongoDB Atlas will take a few minutes to deploy the changes, after which you should be good to go. The IP address that will appear should be the same that appears when you search for it manually, using tools like [whatsmyip.org](<https://www.whatsmyip.org/> "target=\"\_blank\"").

