# MongoError: Authentication failed

It can be frustrating to initiate a reverse-engineering operation, and get a message like "MongoError: Authentication failed".&nbsp; Particularly, if you have no such issue with MongoDB Compass.&nbsp;

&nbsp;

Some typical issues might be with entries on the Auth tab: are the username and password spelled correctly, with the appropriate upper and lower cases, and is the Auth source correct (in most cases it should be left empty or use the default "admin".)&nbsp;

&nbsp;

But there could be many other details.&nbsp; Compass and Hackolade use the same software libraries to connect to MongoDB instances, whether on-premises or Atlas.

&nbsp;

Just to make sure that the connection string is identical to what you have in Compass, is to copy/paste from Compass into Hackolade.  Here are the steps:\
&#49;) Open Compass, select the connection, and click on the Edit button:

![Compass connection copy 1](<lib/Compass%20connection%20copy%201.png>)​\
\
&#50;) click Confirm:

![Compass connection copy 2](<lib/Compass%20connection%20copy%202.png>)

​\
&#51;) in the edit window, press ctrl+A to select the entire string, then ctrl+C to copy the string to the clipboard:

![Compass connection copy 3](<lib/Compass%20connection%20copy%203.png>)

​\
&#52;) In Hackolade MongoDB model connections settings, add a new one, and press the button "From SRV or URI":

![Compass connection copy 4](<lib/Compass%20connection%20copy%204.png>)\
\
&#53;) then press ctrl+V or right click and choose paste:

![Compass connection copy 5](<lib/Compass%20connection%20copy%205.png>)​\
\
When you save, this should parse the string and fill-in all the entries automatically.\
\
Then try again to connect to the database, using the newly created connection settings.\
\
If it does not work, you should send an email to [support@hackolade.com](<mailto:support@hackolade.com?subject=Cannot%20connect%20to%20MongoDB%20instance>) with the log file HackoladeRE.log from directory&nbsp; C:\\Users\\%username%\\AppData\\Roaming\\HackoladeLogs (Windows) or folder Users/$USER/Documents/HackoladeLogs (Mac/Linux)

&nbsp;

