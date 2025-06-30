# Download additional target plugins

The latest version of each plugin is always available for download from the Plugin Manager?&nbsp; Just go to Help \>&nbsp; Plugin Manager

&nbsp;

![Plugin Manager menu new](<lib/Plugin Manager menu new.png>)

&nbsp;

&nbsp;

You may choose which plugin to install on your computer.

![Plugin - manager available custom props](<lib/Plugin - manager available custom props.png>)

&nbsp;

This will result in the plugin appearing in the Installed tab of the plugin manager.

![Plugin - Manager installed custom props](<lib/Plugin - Manager installed custom props.png>)

&nbsp;

&nbsp;

&nbsp;

## Are you experiencing issues with plugin download?

Do you have your network proxy set correctly?&nbsp; See more details [here](<Networkproxy.md>).

&nbsp;

Does&nbsp; your organization prevent access to GitHub?&nbsp; You may need to have [https://github.com/hackolade](<https://github.com/hackolade> "target=\"\_blank\"") whitelisted.

&nbsp;

There is an alternative: you may download the plugin from [our GitHub repo](<https://github.com/hackolade> "target=\"\_blank\""), then go to the plugin of your choice, and click on link in the About section on the right-hand side of the page:

&nbsp;

&nbsp;

&nbsp;

![GitHub Plugin Download](<lib/GitHub Plugin Download.png>)

&nbsp;

This link leads you to a page with the latest release, where you can click on the link **\<plugin\>-\<version\>.zip** link to download the zip file:

&nbsp;

&nbsp;

![GitHub Plugin Download step 2](<lib/GitHub Plugin Download step 2.png>)

&nbsp;

&nbsp;

​

&nbsp;

Then to install the plugin, go to Help \> Plugin Manager and click the button Install from Zip.

&nbsp;

![Plugin Manager - Install from zip](<lib/Plugin Manager - Install from zip.png>)

&nbsp;

&nbsp;

## You get the message "Hackolade Studio doesn't have enough rights to install a plugin..."

While you, as a user may have the rights to the folder where plugins are installed, it is possible that some environments limit the rights of our application.&nbsp; It can be a virtualization or sandboxing setup or most likely an anti-virus software. &nbsp;

![Plugins - Virus Threat Protection error](<lib/Plugins - Virus Threat Protection error.png>)

&nbsp;

If your anti-virus is Windows Defender, you, or your IT department, can create an exclusion in Windows Defender. Follow these steps:

**Open Windows Security:**

\- Press the **Windows key + I** to open Settings.

\- Select "Privacy \& Security."

\- Click on "Windows Security" in the left sidebar.

&nbsp;

**Access Virus \& Threat Protection Settings:**

\- In the Windows Security window, click on "Virus \& threat protection."

![Image](<lib/Plugins - Virus Threat Protection.png>)

&nbsp;

&nbsp;

**Manage Settings:**

\- Under the "Virus \& threat protection settings" section, click on "Manage settings."

&nbsp;

![Plugins Windows Defender Manage settings](<lib/Plugins Windows Defender Manage settings.png>)

&nbsp;

&nbsp;

**Add or Remove Exclusions:**

\- Scroll down to the bottom, to the "Exclusions" section.

\- Click on "Add or remove exclusions."

&nbsp;

![Plugins Windows Defender add exclusion](<lib/Plugins Windows Defender add exclusion.png>)

&nbsp;

**Add a Folder Exclusion:**

\- Click on "Add an exclusion."

\- Choose "Folder" from the drop-down menu.

&nbsp;

If you get the message that you don't have the permission to create this exclusion, you will need for your IT Security team to access your machine and allow this operation.&nbsp; Or ask them to perform it for you.

&nbsp;

![Image](<lib/Plugins - Windows Defender no permission.png>)

&nbsp;

&nbsp;

**Specify the Folder Path:**

\- Navigate to the folder **C:\\Users\\%username%\\.hackolade** and select it.

![Plugins Windows Defender add folder path](<lib/Plugins Windows Defender add folder path.png>)

&nbsp;

**Save Changes:**

\- Save your changes.

This exclusion tells Windows Defender not to scan or interfere with files and processes within the specified folder. Hackolade Studio should now have the necessary WRITE or EXECUTE permissions in the specified directory.\
\
Remember to replace **%username%** in the folder path with the actual username. After making these changes, the application should be able to operate in the specified directory without being blocked by Windows Defender.

&nbsp;

## Plugin Manager options for an installed plugin

In the Installed tab of the Plugin Manager, you may see multiple buttons:

![Plugin Manager Installed tab - buttons](<lib/Plugin Manager Installed tab - buttons.png>)

&nbsp;

**Remove:** this button deletes the plugin from your machine

**Disable:** this button keeps the plugin on your machine but turns it OFF, so it no longer appears in the targets available to create models.

**Migrate:**  this has to do with customizations you may have made to this plugin.  The whole thing is documented in [this page](<Migrationtoenhancedcustompropert.md>). If you don't have customizations dating prior to v3.6.2, you may probably ignore.  But it is safer to first migrate just in case, then update to the latest version of the plugin.

&nbsp;

