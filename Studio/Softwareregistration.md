# Software registration

After downloading Hackolade, you need to obtain and validate an activation key before you can use the application.

&nbsp;

You can initiate the process of getting an activation key either from the website, or from inside the application.&nbsp; Once you have an activation key, it needs to be validated from the application.

&nbsp;

**IMPORTANT NOTE:** Your license key is a valuable asset and should be treated with care.&nbsp; If you change computers or a user leaves the organization, take a moment to release the license key on the old PC before retiring it, so your license key can be validated again on your new machine.  All details can be found [here](<Transferalicensetoanewcomputer.md> "Transfer license to a new computer"). &nbsp;

&nbsp;

**Important:** the following domains must be whitelisted: [https://hackolade.com](<https://hackolade.com> "target=\"\_blank\""),&nbsp; [https://quicklicensemanager.com](<https://quicklicensemanager.com/> "target=\"\_blank\""), [https://qlmdr.com](<https://qlmdr.com> "target=\"\_blank\""), and [https://github.com](<https://github.com> "target=\"\_blank\"")

&nbsp;

**Warning:** if you have an HTTP proxy server on your network, you may have to manually set in the application the proxy parameters.&nbsp; You will find more information on the [Network Proxy page](<Networkproxy.md>).&nbsp; In particular, in environments with proxies using SSL inspection (Zscaler, BlueCoat, etc.) it is critical that Hackolade be whitelisted to connect properly with SSL/TLS protocols.

&nbsp;

**Useful info when managing licenses for multiple users:** read [this article](<https://hackolade.zendesk.com/hc/en-us/articles/360002719839-Managing-multiple-license-keys-and-seats> "target=\"\_blank\"") if you're a license administrator and want to track who's using Hackolade licenses.

&nbsp;

&nbsp;

## Get a software license key

### from the website

Go to the [pricing page](<http://hackolade.com/pricing.html> "target=\"\_blank\"") and choose the version you prefer (see [here](<Editions.md>) for more info).&nbsp; You will be directed to the Hackolade Store where you'll be guided through the checkout process.&nbsp; A license key will be generated and provided on screen and via email. &nbsp; You will need this key to access the application.&nbsp; Go to step 2 below for instructions.

### from the application

When you start Hackolade, if there is no valid license key present, you are presented with this dialog box:

&nbsp;

![Registration -- empty dialog](<lib/Registration%20--%20empty%20dialog.png>)

&nbsp;

This screen can also be reached by going to Help \> Software Key Validation.

&nbsp;

&nbsp;

Choose one of the following options:

&nbsp;

![Registration -- 4 options](<lib/Registration%20--%204%20options.png>)

&nbsp;

then click the Send button.&nbsp; You will be directed to the Hackolade Store where you'll be guided through the checkout process.&nbsp; A license key will be generated and provided on screen and via email. &nbsp; You will need this license key to access the application.&nbsp; Go to step 2 below for instructions.

## Validate your license key

If you have not downloaded Hackolade yet, please do so from the [download page](<http://hackolade.com/download.html> "target=\"\_blank\"").

&nbsp;

&nbsp;

&nbsp;

![Registration -- register activation key](<lib/Registration%20--%20register%20activation%20key.png>)

&nbsp;

&nbsp;

**Step 1:** In the Software Key Validation dialog, please choose the option 'I want to...':

![Registration -- activation](<lib/Registration%20--%20activation.png>)

then **Step 2:** paste your license key, and optionally enter your name or an identifier to help manage multiple licenses

and **Step 3:** click the Send button. &nbsp;

&nbsp;

You need to be connected to the Internet for this step to validate your license key with Hackolade's license server.&nbsp; If your company has many licenses, your administrator may require that you enter your name in the Identifier (optional) field:

![Registration -- license details](<lib/Registration%20--%20license%20details.png>)

&nbsp;

You should be getting this confirmation message:

![Registration -- success message](<lib/Registration%20--%20success%20message.png>)

&nbsp;

and the license details will be filled window will be filled.

&nbsp;

## Release the license key from one computer to move to another

If you need to move your license key to another computer, you first need to release it on the PC where your key is currently validated.

&nbsp;

To do so, go to the option Help \> Software Key Validation, and choose the action 'I want to...':

![Registration -- release license key](<lib/Registration%20--%20release%20license%20key.png>)

and click the Send button.&nbsp; This will free up the key on our license server. &nbsp;

&nbsp;

![Registration -- un-register confirmation](<lib/Registration%20--%20un-register%20confirmation.png>)

Make sure to copy the license key and store it (or find your original license key confirmation email) as you will need it to activate on the other computer where you will want to use Hackolade.

&nbsp;

As of this moment, you can no longer use Hackolade on the original computer, unless you you re-register it.

&nbsp;

Go to the other computer where you want to use Hackolade and validate your license key using the instructions above '2. Validate your license key'

&nbsp;

## Offline validation

**Important note:** offline validation will NOT work for subscriptions or perpetual concurrent licenses.&nbsp; This section is only for Community, Trial, and perpetual individual workstation licenses.

&nbsp;

If the application cannot reach the Internet, the following dialog is displayed:

&nbsp;

![Offline license activation - connection failu](<lib/Offline%20license%20activation%20-%20connection%20failu.png>)

&nbsp;

If the machine does have access to the Internet, it is possible that a proxy setting is preventing the application from properly connecting, and you should follow the steps described [here](<Networkproxy.md>).

&nbsp;

There are legitimate reasons for the machine to be disconnected from the Internet, in which case you should follow the steps below.

&nbsp;

By clicking on the link or the Send button, you will be directed in your browser to this page (or you should copy the URL so it could be used on a different computer with Internet access), with the fields pre-filled:

![Offline license activation - web screen](<lib/Offline%20license%20activation%20-%20web%20screen.png>)

&nbsp;

To manually access the above, you may also use [this link](<https://quicklicensemanager.com/hackolade/QlmCustomerSite/qlmwebactivation.aspx> "target=\"\_blank\"").&nbsp;

&nbsp;

When you click the activate button, an XML file will be downloaded to your PC.&nbsp; With the application, choose the path and filename of the downloaded file:

&nbsp;

![Offline license activation - choose file](<lib/Offline%20license%20activation%20-%20choose%20file.png>)

&nbsp;

And the application should get activated.&nbsp; Do not modify anything in the downloaded file, or the activation will fail.

&nbsp;

## Concurrent licenses

Concurrent licenses (a.k.a. *floating* licenses) work differently than workstation licenses.&nbsp; With concurrent licenses, Hackolade's cloud-based licensing server tracks the number of simultaneous users for a given concurrent license key.&nbsp; If the number of simultaneous users reaches the maximum number of seats for the license key, anyone who subsequently tries to start the software is denied access. &nbsp;

&nbsp;

The application may be installed on a large number of computers, each with the same validated license key, but a maximum number of users are allowed at the same time, according to the number of seats purchased for that concurrent license key.&nbsp; For example, an organization has acquired a single concurrent license key for 20 seats.&nbsp; The application and validated license key are installed on 250 PCs.&nbsp; At any given time, only a maximum of 20 users will be allowed to use the application.&nbsp; If a 21st user attempts to open the application, access will be denied until a previous user exits the application and frees up a seat.

&nbsp;

With ***individual workstation*** licenses, the license key is entered and validated by our Hackolade cloud-based licensing server when the application is first accessed.&nbsp; After that validation, the application no longer needs to access the licensing server.&nbsp; To be complete, each time the maintenance or the subscription expires, the application will again communicate with the licensing server to check if the contract has been renewed.&nbsp;

&nbsp;

For **concurrent** licenses, the licensing server is contacted multiple times: each time the application is started, plus each time the application is exited.&nbsp; Assuming that the license key has been validated once for an application instance, each time the application is started, the licensing server is contacted to verify the availability of a seat.&nbsp; If a seat is available, it gets reserved on the licensing server with the unique UUID of the PC, and access is granted.&nbsp; If no seat is available, access is denied.&nbsp; Any seat granted when opening the application gets released upon exiting the application. &nbsp;

&nbsp;

Offline use of the application is possible but requires to start the application so a seat can be granted **before** going offline, provided that a seat is indeed available. The seat will remain assigned until the application is exited while online.

&nbsp;

**Note:** In particular with concurrent licenses, it is strongly suggested to read and apply [this article](<Managingmultiplelicensekeysandse.md>) so a license administrator can track who's using Hackolade licenses and seats. &nbsp;

&nbsp;

## Licenses on Virtual Machines (or physical computer accessed via RDP or equivalent)

**Important note:** installing Hackolade on a central computer (whether on a PC or a server, whether the machine is virtual or physical, and whether on premises or in the Cloud) does **not** change the terms of our [License Agreement](<Licenseagreement.md>).&nbsp; Specifically, that license metric is per "per seat", and that a license must be obtained for each device on or from which the Product is used or accessed. When the Product is accessed remotely across using Terminal Server, Remote Desktop, Citrix XenDesktop or an equivalent method, a separate Product license is required to be assigned to each device from which the application is accessed, i.e. not the virtual machine on which the Product is installed.

&nbsp;

**Important:** before you delete a user login on a VM, or delete an entire VM, make sure to release the Hackolade key(s) via Help \> Software Key Validation \> Release.  This is the only way for you to free up the seats of that user, and make it available for another one.

&nbsp;

**Reminder:** when installing Hackolade on a VM to share among multiple users, it is important to realize that licensing is not attached to just the machine, but to the combination of the machine where Hackolade is installed, a client workstation identification for the PC accessing the application, and the user login.&nbsp; As per the [EULA](<Licenseagreement.md>): "A license must be obtained for each device on or from which the Product is used or accessed." &nbsp;

&nbsp;

Example: having 4 Hackolade users on a single VM is the equivalent of having 4 individual PCs running Hackolade from a licensing point of view: you need 4 license seats to be validated.

&nbsp;

### VM configuration

**Note:** it is critical that the VM setup is such that you access a **persistent** VM instance of the application.&nbsp; Non-persistent instances will cause license issues.

&nbsp;

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

