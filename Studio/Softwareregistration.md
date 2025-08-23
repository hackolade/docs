# Software registration

*If you're using a an older version of Hackolade Studio (up to v6.11.9), consult [*this page](<OldSoftwareValidationdialog.md>) *for the older screenshots and process.*

&nbsp;

After downloading Hackolade Studio Desktop, you need to obtain and validate an activation key before you can use the application, except for the Community Edition.

&nbsp;

You can initiate the process of getting an activation key either from the website, or from inside the application.&nbsp; Once you have an activation key, it needs to be validated from the application.

&nbsp;

**IMPORTANT NOTE:** Your license key is a valuable asset and should be treated with care.&nbsp; Just like you would reclaim a laptop when someone leaves, you should do the same for our license keys.&nbsp; If you change computers or a user leaves the organization, take a moment to release the license key on the old PC before retiring it, so your license key can be validated again on a new machine.  Many customers add to the exit checklist of team members the action of releasing the license key.&nbsp; All details can be found [here](<Transferalicensetoanewcomputer.md> "Transfer license to a new computer"). &nbsp;

&nbsp;

**Important:** the following domains must be whitelisted: [https://hackolade.com](<https://hackolade.com> "target=\"\_blank\""),&nbsp; [https://quicklicensemanager.com](<https://quicklicensemanager.com/> "target=\"\_blank\""), [https://qlmdr.com](<https://qlmdr.com> "target=\"\_blank\""), and [https://github.com/hackolade](<https://github.com/hackolade> "target=\"\_blank\"")

&nbsp;

**Warning:** if you have an HTTP proxy server on your network, you may have to manually set in the application the proxy parameters.&nbsp; You will find more information on the [Network Proxy page](<Networkproxy.md>).&nbsp; In particular, in environments with proxies using SSL inspection (Zscaler, BlueCoat, etc.) it is critical that Hackolade Studio be whitelisted to connect properly with SSL/TLS protocols.

&nbsp;

**Useful info when managing licenses for multiple users:** read [this article](<https://hackolade.zendesk.com/hc/en-us/articles/360002719839-Managing-multiple-license-keys-and-seats> "target=\"\_blank\"") if you're a license administrator and want to track who's using Hackolade licenses.

&nbsp;

&nbsp;

## Get a software license key

Starting with v7.0.0, the Community Edition no longer requires a license key.&nbsp; For the Community Edition, the experience is 100% friction-less: no license key, no sign up, no login.&nbsp; Just download the software and start to use use it.&nbsp; If you want to avoid seeing the License Status screen each time you start the application.&nbsp; Just click on the Continue for Free button in the Community Edition card.

&nbsp;

For obvious reasons, it is not possible to accumulate multiple 14-day free trial keys.&nbsp; Once your key has expired, you may take a subscription for the Edition of your choice, or choose to use the Community Edition for free.&nbsp; If you need more time, you may send an email to support@hackolade.com, explaining the evaluation plans and timeline for your organization.

### from the website

Go to the [pricing page](<http://hackolade.com/pricing.html> "target=\"\_blank\"") and choose the version you prefer (see [here](<Editions.md>) for more info).&nbsp; You will be directed to the Hackolade Store where you'll be guided through the checkout process.&nbsp; A license key will be generated and provided on screen and via email. &nbsp; You will need this key to access the application.&nbsp; Go to the validation step below for instructions.

### from the application

When you start Hackolade Studio, if there is no valid license key present, you are presented with this License Status screen, also available by clicking the key icon at the bottom of the context bar in the lower left-hand corner, or by going to Help \> License Status:

&nbsp;

![License Status - request license key](<lib/License Status - request license key.png>)

&nbsp;

Choose your Edition and subscription plan.&nbsp; You will be directed to the Hackolade Store in your browser where you'll be guided through the checkout process.&nbsp; A license key will be generated and sent to you via email. &nbsp; You will need this license key to access the application. &nbsp;

&nbsp;

## Validate your license key

If you have not downloaded Hackolade yet, please do so from the [download page](<http://hackolade.com/download.html> "target=\"\_blank\"").

&nbsp;

![License Status - validate license key](<lib/License Status - validate license key.png>)

&nbsp;

Paste the license key received by email, or provided by your administrator.&nbsp; The license key has a format of multiple 5-character segment like XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX.&nbsp; Note that the dashes ("-") are cosmetic and optional.&nbsp; A proper license key with no dashes validates equally well.

&nbsp;

The Identifier field is pre-populated with information fetched from your Operating System.&nbsp; This Identifier is important in the management of license keys.

&nbsp;

Click the Validate button.

&nbsp;

You must be connected to the Internet for the validation of your license key with Hackolade's license server.&nbsp; In some rare cases when your machine must be isolated from the Internet, you may use the offline validation process described below.

&nbsp;

If the license key is successfully validated, the following message will briefly appear at the top of your screen.

![License Status - license key validated](<lib/License Status - license key validated.png>)

&nbsp;

&nbsp;

The License Status screen can be accessed at any time by clicking the key icon at the bottom of the context bar in the lower left-hand corner, or by going to Help \> License Status:

&nbsp;

![License Status - status screen](<lib/License Status - status screen.png>)

&nbsp;

&nbsp;

&nbsp;

## Release the license key from one computer to move to another

If you need to move your license key to another computer, you first need to release it on the machine where it is currently validated.

&nbsp;

To release it, go to the option Help \> License Status then click the Release key button.

&nbsp;

As of this moment, you can no longer use Hackolade Studio on the original computer, unless you you re-register it, or switch back to the Community Edition.

&nbsp;

Go to the other computer where you want to use Hackolade Studio and validate your license key using the instructions above 'Validate your license key'

&nbsp;

## Offline validation

**Important note:** offline validation will NOT work for subscriptions or perpetual concurrent licenses.&nbsp; This section is only for 14-day trial, and perpetual individual workstation licenses.

&nbsp;

If the application cannot reach the Internet, the following dialog is displayed:

&nbsp;

![Offline license activation - connection failu](<lib/Offline license activation - connection failu.png>)

&nbsp;

If the machine does have access to the Internet, it is possible that a proxy setting is preventing the application from properly connecting, and you should follow the steps described [here](<Networkproxy.md>).

&nbsp;

There are legitimate reasons for the machine to be disconnected from the Internet, in which case you should follow the steps below.

&nbsp;

By clicking on the link or the Send button, you will be directed in your browser to this page (or you should copy the URL so it could be used on a different computer with Internet access), with the fields pre-filled:

![Offline license activation - web screen](<lib/Offline license activation - web screen.png>)

&nbsp;

To manually access the above, you may also use [this link](<https://quicklicensemanager.com/hackolade/QlmCustomerSite/qlmwebactivation.aspx> "target=\"\_blank\"").&nbsp;

&nbsp;

When you click the activate button, an XML file will be downloaded to your PC.&nbsp; With the application, choose the path and filename of the downloaded file:

&nbsp;

![Offline license activation - choose file](<lib/Offline license activation - choose file.png>)

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

As long as you validate and use Hackolade Studio with the same combination of host machine, remote machine, and login, there should be no issue.&nbsp; If any of these 3 parameters is different, access is blocked.&nbsp; In a VM environment, it is critical that the VM instance is persistent to ensure the stability of the 3-parameter combination.

&nbsp;

**Important note:** installing Hackolade on a central computer (whether on a PC or a server, whether the machine is virtual or physical, and whether on premises or in the Cloud) does **not** change the terms of our [License Agreement](<Licenseagreement.md>).&nbsp; Specifically, that license metric is per "per seat", and that a license must be obtained for each device on or from which the Product is used or accessed. When the Product is accessed remotely across using Terminal Server, Remote Desktop, Windows App, virtual machine, Citrix, or an equivalent method, a separate Product license is required to be assigned to each device from which the application is accessed, i.e. not the virtual machine on which the Product is installed.

&nbsp;

**Important:** before you delete a user login on a VM, or delete an entire VM, make sure to release the Hackolade key(s) via Help \> Software Key Validation \> Release.  This is the only way for you to free up the seats of that user, and make it available for another one.

&nbsp;

**Reminder:** when installing Hackolade on a VM to share among multiple users, it is important to realize that licensing is not attached to just the machine, but to the combination of the machine where Hackolade is installed, a client workstation identification for the PC accessing the application, and the user login.&nbsp; As per the [EULA](<Licenseagreement.md>): "A license must be obtained for each device on or from which the Product is used or accessed." &nbsp;

&nbsp;

Example: having 4 Hackolade users on a single VM is the equivalent of having 4 individual PCs running Hackolade from a licensing point of view: you need 4 license seats to be validated.

&nbsp;

### VM configuration

**Note:** it is critical that the VM setup is such that you access a **persistent** VM instance of the application.&nbsp; Non-persistent instances will cause license issues.&nbsp; See [this article](<https://www.parallels.com/blogs/ras/persistent-vdi-vs-non-persistent/> "target=\"\_blank\"") for a good discussion of persistent vs non-persistent (or stateless) VDI.

&nbsp;

![Persistent vs non-persistent VDI](<lib/Persistent vs non-persistent VDI.png>)

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

&nbsp;

&nbsp;

## Reuse in the Browser your license key already validated in the Desktop

Remember that the Desktop deployment of Hackolade Studio remains the flagship product that includes all the features, depending on the license key.&nbsp; The Browser deployment is provided for convenience, particularly useful for read-only viewers, but, as explained [here](<Security-firstbrowserdeployment.md>) and [here](<Editions.md>), not all the features are possible from the browser.

&nbsp;

If you use both the browser and desktop deployments of Hackolade Studio on the same machine, it would be annoying if 2 license seats were necessary...&nbsp; Same user on the same machine, it seems logical that only a single license seat would be required.&nbsp; We recognize that, but finding a solution was technically quite challenging.&nbsp; This mutualization of the license key validation is possible starting with v8.3.2 and allows to reuse in the Browser the license key already validated in the Desktop for the same machine plus user combination (don't try it on virtual machines across different users ;-)...).&nbsp; This synchronization is NOT possible if your Desktop version is lower than v8.3.2.

&nbsp;

**Important note:** the synchronization of the license validation must be performed in a specific sequence. The license must be validated first in the Desktop, then synchronized from the Browser.&nbsp; If you originally validated the license in the Browser, and you decide that you now want to use the Desktop, then you must first release the license in the browser, then validate it in the Desktop, then synchronize from the Browser.

&nbsp;

For security purposes, browsers are not allowed easy access to local drive resources without repeatedly asking for permission.&nbsp; This constraint prevents us from accessing the license information, originally created with the Desktop,&nbsp; directly from the Browser.&nbsp; A special process is therefore required.

&nbsp;

**Important note:** the synchronization only works for the default browser of your operation system.&nbsp; If you have multiple browsers on your machine, the synchronization will fail if started from another browser than your default browser.&nbsp; It also cannot be started from an incognito instance of your browser, or the license information will be lost as soon as you close the tab.

&nbsp;

### License key reuse process

Assuming that you validated your license key with the Desktop, go to [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"\_blank\"") to access the browser deployment of Hackolade Studio.&nbsp; Then go to Help \> License Status, or click&nbsp; on the key icon in the lower left-hand corner of the screen.

&nbsp;

The license screen should look similar to this image:

&nbsp;

![Browser - 1 - License key reuse](<lib/Browser - 1 - License key reuse.png>)

&nbsp;

&nbsp;

Click the radio button "Yes" to the question "Do you already have a validated license key in Hackolade Studio Desktop?"&nbsp; Of course, we assume that you do indeed have Hackolade Studio Desktop installed on your machine, in version v8.3.2 or above, and with a validated license key.

&nbsp;

The dialog changes to this screen, so you can click the button "Reuse license key from desktop app":

&nbsp;

![Browser - 2 - License key reuse](<lib/Browser - 2 - License key reuse.png>)

&nbsp;

&nbsp;

When you click the button, a new browser tab opens with the following message:

![Browser - 3 - License key reuse](<lib/Browser - 3 - License key reuse.png>)

&nbsp;

Click the button "Open Hackolade", and the system starts Hackolade Studio Desktop to fetch the license key information.

&nbsp;

If all goes well, the additional tab should flash this message before disappearing:

![Browser - 4 - License key reuse](<lib/Browser - 4 - License key reuse.png>)

&nbsp;

then return to the Welcome screen of the application.&nbsp; If you access again the License Status screen, you should see something like this, where the license key and license metadata is identical to that in your Desktop application:

![Browser - 5 - License key reuse](<lib/Browser - 5 - License key reuse.png>)

&nbsp;

&nbsp;

&nbsp;

### Troubleshooting

If no license key was validated in the Desktop, you will get this message:

![Browser - 6 - License key reuse](<lib/Browser - 6 - License key reuse.png>)

&nbsp;

If you get the message below, it is probably because the Desktop application could not be found on your machine, or that your Desktop version is not at least v8.3.2:

![Browser - 7 - License key reuse](<lib/Browser - 7 - License key reuse.png>)

&nbsp;

If you get this message, it is probably because you did not start the process from your default browser:

&nbsp;

![Image](<lib/Browser - 8 - License key reuse.png>)

&nbsp;

&nbsp;

