# Windows

## Standard installation

The application is shipped as a signed .exe file with an installation wizard automatically placing the app in the proper folder and displaying the License Agreement and Release Notes.&nbsp; Windows installation does not require admin rights *(unless the installation is made to a directory requiring admin rights)* and does not write to the Windows Registry.&nbsp; However, in a corporate environment, you should contact your IT department.&nbsp; They can remotely access your computer and install the software for you.&nbsp; You should comply with the IT policy on non-approved software.

&nbsp;

**Warning:** Do NOT install Hackolade in the AppData directory.  You should select either Program Files, or C:\\Hackolade or some other place where you have Write rights.&nbsp; AppData is for application *data*, not application *programs*.

&nbsp;

**Important:** do NOT install a new version of Hackolade while the application is running.&nbsp; All instances of the application must be closed for the upgrade to proceed properly.&nbsp; Please refer to this page if you get an error such as this one:

![Image](<lib/Installation%20error%20-%20application%20running.png>)

&nbsp;

After downloading the application from our [download page](<https://hackolade.com/download.html>), double-click on the downloaded .exe file and the wizard will start.&nbsp; You will first see the publisher verification dialog letting you check the authenticity of the download signed with Hackolade's parent company NV IntegrIT's extended validation certificate.

&nbsp;

![Image](<lib/Windows%20install%20-%20publisher%20verification.png>)

&nbsp;

The wizard starts with a Welcome page stating the version number about to be installed

![Image](<lib/Windows%20install%20-%20Welcome%20page.png>)

&nbsp;

You need to approve the License Agreement to proceed:

![Image](<lib/Windows%20install%20-%20License%20Agreement.png>)

&nbsp;

&nbsp;

A default installation folder is proposed, which may be changed if you wish:

![Image](<lib/Windows%20install%20-%20destination%20folder.png>)

&nbsp;

**Warning:** Do NOT install Hackolade in the AppData directory.  You should select either Program Files as suggest, or C:\\Hackolade or some other place where you have Write rights.&nbsp; AppData is for application *data*, not application *programs*.

&nbsp;

After a couple of additional prompt, the installation process will start.&nbsp; At the end, you will be able to consult the release note, and automatically start the application.

&nbsp;

The installation program also supports silent mode for command-line installations, with the following arguments:

| **/SILEN**T | Runs the installer in silent mode (The progress window is displayed) |
| --- | --- |
| **/VERYSILENT** | Very silent mode. No windows are displayed. |
| **/SUPPRESSMSGBOXES** | Suppress message boxes. Only has an effect when combined with '/SILENT' and '/VERYSILENT'. |
| **/NOCANCEL** | Disables canceling the installation process. |
| **/DIR="x:\\dirname"** | Overrides the default install directory. |
| &nbsp; | &nbsp; |


*Example:*

Silently install the program, suppress message boxes, and install in a user directory instead of the default.

Hackolade-win64-setup-signed.exe /VERYSILENT /SUPPRESSMSGBOXES /DIR="C:/Users/%username%/Hackolade"

&nbsp;

## Licenses on Virtual Machines (or physical computer accessed via Remote Desktop Installations \[RDP\] or equivalent)

**Important note:** installing Hackolade on a central computer (whether on a PC or a server, whether the machine is virtual or physical, and whether on premises or in the Cloud) does **not** change the terms of our [License Agreement](<Licenseagreement.md>).&nbsp; Specifically, that license metric is per "per seat", and that a license must be obtained for each device on or from which the Product is used or accessed. When the Product is accessed remotely across using Terminal Server, Remote Desktop, Citrix XenDesktop or an equivalent method, a separate Product license is required to be assigned to each device from which the application is accessed, i.e. not the virtual machine on which the Product is installed.

&nbsp;

**Important:** before you delete a user login on a VM, or delete an entire VM, make sure to release the Hackolade key(s) via Help \> Software Key Validation \> Release.  This is the only way for you to free up the seats of that user, and make it available for another one.

&nbsp;

**Reminder:** when installing Hackolade on a VM to share among multiple users, it is important to realize that licensing is not attached to just the machine, but to the combination of the machine where Hackolade is installed, a client workstation identification for the PC accessing the application, and the user login.&nbsp; As per the [EULA](<Licenseagreement.md>): "A license must be obtained for each device on or from which the Product is used or accessed." &nbsp;

&nbsp;

Example: having 4 Hackolade users on a single VM is the equivalent of having 4 individual PCs running Hackolade from a licensing point of view: you need 4 license seats to be validated.

&nbsp;

### VM configuration

Hackolade licensing is enforced through registration on our license server of a combination of unique identifiers, including the UUID of the computer where Hackolade is installed, a client workstation identification for the PC accessing the application, and the user login.  Each unknown combination reserves one seat on our license server, until you reach the total number of seats purchased for the submitted license key.

&nbsp;

While typically Windows installation does not require admin rights, if the directory where the software is to be installed requires admin rights, you may need the intervention of an administrator with elevated rights to execute the installation.&nbsp; The Hackolade installation should be made for "all users" of the central computer, if given the choice.&nbsp; Please refer to the section above for instructions on the installation process.

&nbsp;

Once the software is installed centrally, each user login should be able to access its own instance of the application.&nbsp; Each user login on the central computer will be required to go through software key validation, following the steps outlined [here](<Softwareregistration.md>).

&nbsp;

Given the way license seats are counted, it is important that identifiers remain stable.&nbsp; If your IT department configured VM infrastructure differently, it may be required for your IT department to adjust parameters in order to achieve stability.

&nbsp;

#### Citrix

ENABLE\_DYNAMIC\_CLIENT\_NAME should be left to YES\
Allows client name to be the same as the computer name. When you change the computer name, the client name changes too. 

• Yes (default) – Allows the client name to be the same as the computer name. Example, CitrixWorkspaceApp.exe ENABLE\_DYNAMIC\_CLIENT\_NAME=Yes. 

• No - Does not allow the client name to be the same as the computer name. You must specify a value for the CLIENT\_NAME property. Example, CitrixWorkspaceApp.exe ENABLE\_DYNAMIC\_CLIENT\_NAME=No

&nbsp;

Additional resources:

[https://docs.citrix.com/en-us/receiver/windows/4-9/install/cfg-command-line.html#identify-a-user-device](<https://docs.citrix.com/en-us/receiver/windows/4-9/install/cfg-command-line.html#identify-a-user-device> "target=\"\_blank\"")

[https://docs.citrix.com/en-us/receiver/windows/4-9/install/cfg-command-line.html#dynamic-client-name](<https://docs.citrix.com/en-us/receiver/windows/4-9/install/cfg-command-line.html#dynamic-client-name> "target=\"\_blank\"")

&nbsp;

&nbsp;

#### VMWare

As per this VMWare [article, setup should generally be OK](<https://pubs.vmware.com/workstation-9/index.jsp?topic=/com.vmware.ws.using.doc/GUID-533B2C4F-7BD5-41EB-8392-2B9FE687AE50.html> "target=\"\_blank\""):  "Each virtual machine has a universal unique identifier (UUID). The UUID is generated when you initially power on the virtual machine...  Suspending and resuming a virtual machine does not trigger the process that generates a UUID...  If you do not move or copy the virtual machine to another location, the UUID remains constant." &nbsp;

&nbsp;

If it is not the case, maybe instructions in [this article](<https://docs.vmware.com/en/VMware-Horizon/2012/virtual-desktops/GUID-E12713D5-3530-422F-B265-B0F3FDD2041E.html> "target=\"\_blank\"") will help your IT department configure appropriately

