# Mac

## Standard installation

The application is shipped as a signed (with Hackolade's parent company IntegrIT NV Developer ID) .pkg file with an installation wizard automatically placing the app in the proper folder and displaying the License Agreement and Release Notes.&nbsp; After downloading the application from our [download page](<https://hackolade.com/download.html> "target=\"\_blank\""), double-click on the downloaded .pkg file and the wizard will start.&nbsp; You will be prompted for your Mac username and password.

&nbsp;

Starting with the release of macOS 10.15 Catalina, Apple has introduced a new security feature that ensures that 3rd-party applications are manually granted access to the user's file.&nbsp; Hackolade stores settings and logs in your Documents folder, and it cannot operate without it.&nbsp; So, if prompted with this dialog:

![Mac - access to Documents folder](<lib/Mac%20Catalina%20-%20access%20to%20Documents%20folder.png>)

&nbsp;

you must click OK.&nbsp; You may still manage this grant if needed in Security \& Privacy:

![Mac Security Privacy](<lib/Mac%20Catalina%20Security%20Privacy.png>)

&nbsp;

## To install the application without admin rights

In a corporate environment if you don't have the admin password to perform installation, you should contact your IT department.&nbsp; They can remotely access your computer and install the software for you.&nbsp; You should comply with the IT policy on non-approved software.

![Mac install - admin password](<lib/Mac%20install%20-%20admin%20password.png>)&nbsp; ![Mac install - failed](<lib/Mac%20install%20-%20failed.png>)

&nbsp;

Nevertheless, it is possible to bypass this restriction and install Hackolade without admin rights.&nbsp; You must be aware that the installation of the software is a tacit acceptance of our [Terms and Conditions and End-User License Agreement](<https://hackolade.com/eulas.html> "target=\"\_blank\""), whether you use the installation wizard or follow the instructions below.

&nbsp;

Manual installation steps:

&#49;. download the application from our [download page](<https://hackolade.com/download.html> "target=\"\_blank\"")

&nbsp;

&#50;. copy the downloaded file **Hackolade-mac-setup-signed.pkg** to the Desktop

&nbsp;

&#51;. You may want to minimize and hide all windows by pressing Command+Option+H+M

![Mac install - step 2](<lib/Mac%20install%20-%20step%202.png>)

&nbsp;

&#52;. Open the search bar by pressing Command+Spacebar, search for terminal and press enter

![Mac install - step 4](<lib/Mac%20install%20-%20step%204.png>)

&nbsp;

&#53;. Type: **pkgutil --expand** , then drag-and-drop the .pkg file in the terminal window, followed by the folder path where you want to install the software, for example /Users/\<homeFolderName\>/HackoladeTMP and press enter to extract the package into the destination folder

![Mac install - step 5](<lib/Mac%20install%20-%20step%205.png>)

&nbsp;

&#54;. Open the destination temp folder HackoladeTMP

&nbsp;

&#55;. You should see a package file Hackolade.pkg&nbsp; Press Ctrl+Right-Click on the the Hackolade.pkg file and choose Show Content

![Mac install - step 7](<lib/Mac%20install%20-%20step%207.png>)

&nbsp;

&#56;. You will see a Payload file

![Mac install - step 8](<lib/Mac%20install%20-%20step%208.png>)

&nbsp;

&#57;. In the Terminal window, type the command: **tar -xvf** , then drag-and-drop the Payload file and add the -C argument (with an uppercase C) plus the final destination folder and press enter

![Mac install - step 9](<lib/Mac%20install%20-%20step%209.png>)

&nbsp;

&#49;0.&nbsp; You should see a list of filenames scroll through the window:

![Mac install - step 10](<lib/Mac%20install%20-%20step%2010.png>)

&nbsp;

&#49;1.&nbsp; When the process is finished, if you access the destination folder, you should see the installed app:

![Mac install - step 11](<lib/Mac%20install%20-%20step%2011.png>)

&nbsp;

Double-click on the Hackolade.app icon to start the application.

